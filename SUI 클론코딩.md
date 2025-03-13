
https://docs.sui.io/guides/developer/getting-started
맥/리눅스 brew install sui
윈도우 choco install sui
CMD 에서 설치 가능 

sui --version

https://docs.sui.io/guides/developer/getting-started/connect
![[Pasted image 20250221142329.png]]
SUI client / 주소와 비밀복구구문 생성
sui genesis -f 
sui client -envs
![[Pasted image 20250221142912.png]]

이런식으로 테스트넷 연결 가능
sui wallet 크롬 익스텐션으로 설치 
sui move new my_first_package
https://docs.sui.io/guides/developer/first-app/write-package


[examples/move/first_package/sources/example.move](https://github.com/MystenLabs/sui/tree/main/examples/move/first_package/sources/example.move)

수이에서는 모듈이 기본 단위이다. Move에서의 스마트 컨트랙트라고 보면 됨.
모듈은 Move에서 코드를 담고 실행하는 컨테이너(=스마트 컨트랙트) 역할
part1 모듈
use sui::object::{Self, UID};  
use sui::transfer;  
use sui::tx_context::{Self, TxContext};

part2 구조체 struct 
Sword / Forge object 
UID(address말하는듯) / u64(숫자)
key ? store ?

part3 module initializer
여기 나오는 init 함수는 모듈이 *처음 블록체인에 배포될 때 한 번 실행됨*
part4 accessor functions
struct fields 읽는거

//building and testing

**중요**
윈도우의 경우 오류가 남 **경로 길이 제한(260자)** 때문에 git checkout이 안되는 오류가 발생
cmd 에서 git config --global core.longpaths true 작성시
긴 파일 경로 허용이 되면서 
빌드 성공


NFT 

On Sui, everything is an object. Moreover, everything is a non-fungible token (NFT) as its objects are unique, non-fungible, and owned.

Creating NFTs on Sui differs from other blockchains that are not object based. Those blockchains require a dedicated standard to handle the properties that define NFTs because they are based on a mapping between smart contracts and the token's ID. For instance, the ERC-721 standard on Ethereum was necessary to pair a globally unique ID with the relevant smart contract address to create a unique token instance on the network.

On Sui, every object already has a unique ID, so whether you're dealing with a million fungible tokens, like coins, or thousands of NFTs with individual characteristics, like SuiFrens, your smart contracts on Sui always interact with individual objects.

Imagine you create an Excitable Chimp NFT collection on Sui and another blockchain that isn't object based. To get an attribute like the Chimp's name on the other blockchain, you would need to interact with the smart contract that created the NFT to get that information (typically from off-chain storage) using the NFT ID. On Sui, the name attribute can be a field on the object that defines the NFT itself. This construct provides a much more straightforward process for accessing metadata for the NFT as the smart contract that wants the information can just return the name from the object itself.

=> sui 에서는 모든게 객체다. 더 나아가서 모든게 nft이다. ERC-721에서 nft를 정의해서 유니크한 id를 가지는 유니크한 토큰을 정의하는데 성공했다. sui에서는 모든 객체가 이미 고유한 id를 가진다. 그러므로 sui에서의 스마트 컨트랙트는 무조건 개별 객체와 상호작용한다. 

=> 이말인 즉슨, 이더리움에서 ERC-721 표준을 통해 NFT를 정의하는 것은 "스마트 컨트랙트와 토큰 아이디와의 상호작용" 을 통해 정의하는 것인데, 그렇다면 NFT에 접근하려면, 스마트 컨트랙트를 통해 off-chain에 저장된 정보를 요청해야한다.

Kiosk Apps standard  -> ERC-4907 표준?

```
public struct TestnetNFT has key, store {
    id: UID,
    name: string::String,
    description: string::String,
    url: Url,
}
```

기본 nft 구조체인데, sui 에서 어쩌고 ~ has key, store 하면 블록체인 상에 영구 저장되는 구조체를 선언하는 것.

```
public struct NFTMinted has copy, drop {
    object_id: ID,
    creator: address,
    name: string::String,
}
```
이건 has copy, drop으로 바뀌어서 복사 및 삭제가 가능한 구조체임. 리소스로 블록체인 상에 저장되는 것이 아니라 이벤트 기록용이다.(먼솔?) copy는 복사 drop 은 삭제

# move 문법
move.toml 파일은 package manifest 라고 불리며 definition 과 configuration setting을 포함하고 있다. move compiler가 package의 메타데이터를 관리하기 위해 사용된다.  

public struct Rentables has drop {} => drop ability만 있으므로 kiosk Rentables extension 의 key로만 작용한다.
public struct Rented has store, copy, drop { id: ID } => 

- **copy**: value can be copied (or cloned by value) 복사될 수 있다. 
- **drop**: value can be dropped by the end of the scope 삭제될 수 있다.
- **key**: value can be used as a key for global storage operations 전역 저장소에 저장되는 key로 사용될 수 있다. key가 있으면 무조건 ID 필드가 필요하다.
- **store**: value can be held inside a struct in global storage  전역 저장소에 저장될 수 있다. 

함수 public fun addition (a: u8, b: u8): u8 {
	a+b
}
앞에 두 개는 a랑 b의 type을 말하는거고 뒤에는 return 의 type을 말하는 것.

```
/// An object that contains an arbitrary string
	public struct HelloWorldObject has key, store {
	  	id: UID,
	  	/// A string contained in the object
	  	text: string::String
	}

    public fun mint(ctx: &mut TxContext) {
        let object = HelloWorldObject {
            id: object::new(ctx),
            text: string::utf8(b"Hello World!")
        };
        transfer::public_transfer(object, tx_context::sender(ctx));
    }
```
여기서 ctx는 transaction context를 나타낸다. sui 블록체인에서는 객체를 생성하거나 전송할 때 TxContext가 필요하다. 
ctx: &mut TxContext 트랜잭션 컨텍스트를 가변 참조로 전달
&는 참조, mut 가 가변, TxContext가 트랜잭션 실행에 필요한 정보를 포함하는 구조체.
- Owned
    - Owned by an address
    - Owned by another object
- Shared
    - Shared immutable
    - Shared mutable


# 순서

## 1. 환경설정
-> vscode 나 뭐 사용하는 코드 에디터 이용. 터미널 open 혹은 cmd
맥/리눅스 brew install sui
윈도우 choco install sui 이용하면 sui install 가능
vscode 사용시 버전 1.91 사용
***윈도우의 경우  git config --global core.longpaths true***

sui move new nft_rental
cd nft_rental 
nft_rental 폴더 열기

## 2. NFT 설명
https://docs.sui.io/guides/developer/nft/nft-rental
수이에서 소유권 개념 설명하기

이더리움과 sui에서의 객체와 소유권 개념 차이는 무엇인가?
우선 이더리움은 account-based 즉 계정 기반 모델이다. 이더리움에서 객체는 기본적으로 contract로 표현이 된다. 이더리움의 state는 global 하게 저장이 되며 모든 account의 state들의 집합이 전체 이더리움의 state가 된다. contract를 통해 account의 상태를 바꿀 수 있으며, transaction 을 통해 account의 상태가 바뀌면 이더리움의 전체 상태가 바뀌는 것이다. 이더리움의 계정에는 EOA와 CA가 있는데, 이런 account들이 토큰이나 nft같은 자산의 정보를 기록한다. **토큰 소유권은 스마트컨트랙트의 mapping(address => uint256) 같은 구조를 통해 관리된다.** 그러니까 이더리움에서는 토큰이나 nft같은 자산들이 직접 이동하는 것이 아니라 매핑을 통해 contract (계약서) 로 관리되는 것이다. 소유권을 변경하거나 다른 상태 변화가 일어날 때에는 트랜잭션이 일어난다. 이때 contract 호출도 필요하고 가스비도 지불해야한다. 이더리움에서는 자산을 erc-20/erc-721/erc-1155등 의 규칙을 기반으로 정의하고 스마트 컨트랙트가 관리한다.
반면에 Sui는 객체 기반 모델을 사용하며, move 프로그래밍 언어를 기반으로 소유권을 관리한다. sui에서는 move에서 조금 더 sui에 맞게 변환시킨 sui move 언어를 사용한다. sui에서는 모든게 객체이며 모든게 nft이다. 모든 객체가 고유한 ID를 가진다. 특정한 소유권 유형을 가진다. (총 4가지.) 객체는 독립적인 state를 가지며, 이더리움처럼 state가 바뀐다고 해서 전체 상태를 바꿔야하는 것은 아니다. 따로 논다. sui 의 소유권 개념에는 4가지가 있는데, owned by an address(개인 소유), shared ownership(공유 소유), owned by an object(객체 소유), no ownership(없음) 이렇게 나뉜다. sui에서는 객체가 객체를 소유할 수 있다. 그리고 sui에서는 스마트 컨트랙트의 호출 없이, transaction 없이 로컬상태(sui 네트워크)에서 객체 이동이 가능하다. 여기서 글로벌 업데이트가 아닌, 객체 단위 병렬 처리를 사용하므로 tps가 높은 것이다. 속도가 빠른것.

그래서 nft 할거다
## 3. NFT rental

nft rental은 nft를 구매하고 전송하는 것을 넘어 nft를 잠시동안 대여할 수 있도록 한다. nft를 소유한 사람이 그 nft를 소유함으로서 권한이나 자격같은 것을 가질 때, 구매할 필요 없이 대여함으로서 권한을 소유하도록 할 수 있다. 그러한 nft rental dapp 을 만들 것.

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