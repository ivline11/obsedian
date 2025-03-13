 
BAY dapp team

정답 단어에 대한 verification key생성 + 입력 단어에 대한 proof 생성
proof - verification key 의 zk 계산으로 입증 

1. ai 가 단어를 random select / 선택된 단어에 대한 유사한 단어들을 1위부터 1000위까지 유사도와 함께 반환.
2. 그리고 선택된 단어의 verifiction key를 zk circuit을 통해 계산. 여기서 나온 verification key를 반환 후 contract로 올림.
3. frontend에서 player가 guess를 할 때마다 backend로 단어를 보냄. 거기서 guess에 해당하는 proof를 생성. 
4. backend에서 contract에 올라가 있는 verification key를 불러오고, backend에서 guess에 해당하는 proof 두개의 parameter를 이용해 zk 계산을 하여 참거짓 여부를 판단.
5. 참여할 시에 0.001 ether 

