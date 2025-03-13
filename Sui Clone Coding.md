
https://docs.sui.io/guides/developer/nft/nft-rental

## 1. 기본 setting
-> vscode 나 뭐 사용하는 코드 에디터 이용. 터미널 open 혹은 cmd

**sui wallet extension 사용 시**
sui wallet chrome extension 설치, 설정 - network -testnet
*아마 package 배포는 cli로 하고 프론트 만든다면 extension에 있는 sui wallet 사용할 것으로 예상 되긴하는데,, 좀 비효율적이지않나,,*

**front 있다면**
- nodejs 설치(개별 설치)

Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('[https://community.chocolatey.org/install.ps1')](https://community.chocolatey.org/install.ps1'\) "https://community.chocolatey.org/install.ps1')"))

Remove-Item C:\ProgramData\chocolatey -Recurse -Force


**installing sui and settings**
맥/리눅스 brew install sui
윈도우 choco install sui 이용하면 sui install 가능
vscode 사용시 버전 1.91 사용 (1.9.8 됨)
vscode 상단 -> Help -> About
***윈도우의 경우  git config --global core.longpaths true***

관리자 권한으로 진행.

git 이 없는 사람도 있음
 

**배포한다면 cli에서 sui client를 통해 배포 하는 것이 좋아보임**
sui client //지갑 생성

sui client addresses //전체 주소 확인
sui client active-address //active 주소 확인

sui client new-env --alias testnet --rpc https://fullnode.testnet.sui.io:443 //테스트넷 추가

sui client switch --env testnet //테스트넷으로 변경
sui client envs //현재 어떤 네트워크(devnet,testnet 등)에 연결되어있는지 확인

sui client faucet //이 방법도 있지만 discord랑 전송을 이용해 할 수 있음. 웬만하면 여기서 address 받고 전송 이용해서 할 수 있는데, 사람이 많으면 한명 한명 전송 힘듦
https://discord.com/invite/sui

sui client balance //잔액 조회 

ls ~/.sui/sui_config

**여기까지 환경설정 완료 + 테스트넷 토큰 받기**

sui move new nft_rental
cd nft_rental 
nft_rental 폴더 열기
https://github.com/ivline11/nft_rental_skeleton/blob/main/sources/nft_rental_skeleton.move
스켈레톤 코드 nft_rental 에 복붙
	move.toml 파일에 kiosk dependency 추가

sui move build 
sui move test
sui client publish --json --gas-budget 1000000000

**프론트**
git clone https://github.com/keem-hyun/nft-rental-dapp.git
npm install -g pnpm
pnpm -v
cd nft-rental-dapp
pnpm install
pnpm dev
localhost -> ctrl + click
1. 지갑 연결
2. kiosk 설정 -> kiosk 생성 -> rentables 확장 설치
3. nft 생성 -> nft 이름, 설명, 이미지 url 입력 -> 생성 완료
4. nft kiosk에 추가
5. nft 대여 등록(renter) -> nft 선택 -> 대여 기간 및 가격 설정 -> 등록 완료
6. nft 대여(borrower) -> 대여가능한 nft목록확인 -> nft 선택 -> 디여 완료
7. nft 반환(borrower) -> nft 반환 -> 대여한 nft 목록 확인 -> nft 선택 -> 반환 완료 



## 2. NFT 설명
수이에서 소유권 개념 설명하기
이더리움과 sui에서의 객체와 소유권 개념 차이는 무엇인가?
우선 이더리움은 account-based 즉 계정 기반 모델이다. 이더리움에서 객체는 기본적으로 contract로 표현이 된다. 이더리움의 state는 global 하게 저장이 되며 모든 account의 state들의 집합이 전체 이더리움의 state가 된다. contract를 통해 account의 상태를 바꿀 수 있으며, transaction 을 통해 account의 상태가 바뀌면 이더리움의 전체 상태가 바뀌는 것이다. 이더리움의 계정에는 EOA와 CA가 있는데, 이런 account들이 토큰이나 nft같은 자산의 정보를 기록한다. **토큰 소유권은 스마트컨트랙트의 mapping(address => uint256) 같은 구조를 통해 관리된다.** 그러니까 이더리움에서는 토큰이나 nft같은 자산들이 직접 이동하는 것이 아니라 매핑을 통해 contract (계약서) 로 관리되는 것이다. 소유권을 변경하거나 다른 상태 변화가 일어날 때에는 트랜잭션이 일어난다. 이때 contract 호출도 필요하고 가스비도 지불해야한다. 이더리움에서는 자산을 erc-20/erc-721/erc-1155등 의 규칙을 기반으로 정의하고 스마트 컨트랙트가 관리한다.
반면에 Sui는 객체 기반 모델을 사용하며, move 프로그래밍 언어를 기반으로 소유권을 관리한다. sui에서는 move에서 조금 더 sui에 맞게 변환시킨 sui move 언어를 사용한다. sui에서는 모든게 객체이며 모든게 nft이다. 모든 객체가 고유한 ID를 가진다. 특정한 소유권 유형을 가진다. (총 4가지.) 객체는 독립적인 state를 가지며, 이더리움처럼 state가 바뀐다고 해서 전체 상태를 바꿔야하는 것은 아니다. 따로 논다. sui 의 소유권 개념에는 4가지가 있는데, owned by an address(개인 소유), shared ownership(공유 소유), owned by an object(객체 소유), no ownership(없음) 이렇게 나뉜다. sui에서는 객체가 객체를 소유할 수 있다. 그리고 sui에서는 스마트 컨트랙트의 호출 없이, transaction 없이 로컬상태(sui 네트워크)에서 객체 이동이 가능하다. 여기서 글로벌 업데이트가 아닌, 객체 단위 병렬 처리를 사용하므로 tps가 높은 것이다. 속도가 빠른것.

그래서 nft 할거다
## 3. NFT rental

nft rental은 nft를 구매하고 전송하는 것을 넘어 nft를 잠시동안 대여할 수 있도록 한다. nft를 소유한 사람이 그 nft를 소유함으로서 권한이나 자격같은 것을 가질 때, 구매할 필요 없이 대여함으로서 권한을 소유하도록 할 수 있다. 그러한 nft rental dapp 을 만들 것.

**코드 맨 위에 모듈부터 설명 + 아래는 상수들 + 코드 자세한 설명은 깃헙에** 

해당 Dapp에서 사용하는 큰 모듈은 총 세 개. 
만들어야하는 "nft_rental" 모듈, "kiosk_lock_rule" 모듈, "tranfer_policy" 모듈. 
use kiosk:: ~ use sui:: ~ 등 안에 들어있는 것들이 모두 모듈이기는 하지만 대표적으로 이 세 개를 사용한다. 
kiosk 모듈은 sui에서 nft를 편하게 거래할 수 있도록 하는 ... 말그대로 키오스크 같은 역할을 한다. nft 마켓 플레이스 역할이다. kiosk는 특이하게 lender과 borrower 둘 다 kiosk extension 을 install 해야한다.

이는 Sui에 있는 Kiosk apps 표준을 사용하며, ERC-4907 표준과 비슷하다. NFT_rental 에서 이뤄야할 목표는 다음과 같다.
1. lender(임차인)이 특정 기간 동안 그들의 자산을 임대 가능하도록 허용한다.
2. lender가 '임대 기간'을 정할 수 있어야 한다. borrower(임대인)은 해당 임대 기간을 따라야 한다.
3. borrower는 nft에 대한 mutable 혹은 immutable 권한을 얻을 수 있다. immutable은 읽기 전용이고, mutable은 읽기 전용은 아니지만 lender가 해당 경우에는 renting fee를 올릴지 내릴지에 대하여 고려해야한다.
4. 대여 기간이 끝나면, 객체는 원래대로 판매될 수 있다.
5. creator가 정의한 royalty 정책은 transfer policy rule을 통해 존중된다(? 먼소리)

transfer policy rule은 무엇이냐, sui 에서 nft를 전송하기 위한 기본 rule이다. 
모든 sui 객체는 반드시 key abillity를 가져야만 한다. 반면에 store ability는 선택적이다. store ability를 가진 객체는 자유롭게 전송이 가능하다. transfer::public_transfer 함수를 이용하면 누구나 어디로든 자유롭게 전송 가능하다. store ability가 없다면 사용자 정의 전송 함수를 만들어서 다른 방법으로 전송해야한다. 사용자 정의 전송 함수(custom transfer function) 을 만들면 transfer에 key와 store아니더라도 제약 조건을 걸 수 있다. 

//여기까지가 코딩 전에 설명
코딩 들어가기에 앞서서, 기본 Kiosk 모듈에는 임대 기능은 없고,  transfer policy(전송 정책)을 이용해서 sui에서 nft및 자산을 관리하고 거래하도록 하는 시스템이다. Kiosk 자체에는 nft를 임대(rental)하는 기능이 없기 때문에, 특별한 extension 을 설치해야한다. 그래서 가장 먼저 해야하는 것은, Kiosk에 **Rentables Extension**을 설치하는 일이다. 이 extension 을 설치하면, kiosk에 nft를 대여하는 기능, 대여료를 설정하는 기능 등 nft 렌탈을 위한 기능을 추가할 수 있게 된다. 

initialization시에, 우선 NFT(혹은 object)를 제공해주는 'creator' 가 있다. creator는 nft를 대여해주기 위해서 nft_rental 모듈에 parameter로 (publisher와 amountBP) 를 넣고 renting을 setup 한다. 그리고 transfer_policy 모듈에 publisher를 input으로 사용하여 creator만의 transfer policy를 만든다. 그러면 transfer policy 모듈에서 creator에게 TransferPolicyCap을 준다. (정책의 주인을 인정해주는 증명같은 것)

코드에 나오는 setup_renting 은 구멍 뚫어두고 클론코딩 진행. setup_renting에서는 protectedTP 와 RentalPolicy를 결정한다. RentalPolicy는 모든 creator가 민팅(발행)해야한다. 렌탈 규칙이므로 이 구조체는 창작자가 각 임대 요청마다 받을 royalty를 정의한다. (amount_bp가 수수료 비율 / balance는 수수로로 받은 토큰 보관, move에서는 float를 지원하지 않기 때문에 10000은 100%를 의미하고 100은 1%를 의미한다.) ProtectedTP는 창작자가 nft를 임대 가능하게 하기 위해 발행한다. 여기서 둘 다<Phantom T> 를 활용하여 제너릭 타입 T만 가져가고 불필요한 데이터는 제외한다(**좀만 더 고민). 

=> 여기서 문법 + 코드 설명 + 클론코딩은 깃헙에 올린 주석 보고 진행.
https://github.com/ivline11/nft_rental/blob/main/sources/nft_rental.move
이건 스켈레톤 코드 아님. 주석 참고하기


toml파일 sui dependency에다가
override = true  추가

chrome 으로 하기...
