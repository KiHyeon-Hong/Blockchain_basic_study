## 블록체인 기술 기초 공부 참고문헌

- https://arxiv.org/abs/1906.11078

## 블록체인이란?

- 블록체인은 일반적으로 중앙의 기관 없이 구현되는 분산 방식의 변조 방지 디지털 원장이다. 기본적으로 사용자가 블록체인 네트워크에 트랜잭션을 기록할 수 있으며, 이는 네트워크의 정상적인 작동 하에서 트랜잭션이 게시되면 이는 변경할 수 없다.
- 블록체인은 블록으로 그룹화되어 암호화, 서명화 된 트랜잭션의 분산 디지털 원장이다. 각 블록은 유효성 검사, 합의에 따라 이전 블록과 암호화된 방식으로 연결되며, 새로운 블록은 네트워크 내의 원장 사본에 복사되고, 충돌이 발생한다면 미리 설정한 규칙에 따라 자동적으로 문제를 해결한다.

## 블록체인의 분류 (Permissionless VS Permissioned)

### Permissionless

- 어떠한 기관의 허가 없이 블록을 게시하는 모든 사람에게 개방된 탈중앙화 원장 플랫폼이다.
- 대부분이 오픈 소스 소프트웨어이며, 다운로드하려는 모든 사람이 무료로 사용할 수 있다. 누구나 블록을 게시할 수 있는 권리가 있으므로 일부 악의적인 사용자는 시스템을 전복시키기 위한 목적으로 블록을 게시하려고 시도할 수 있다. 이를 방지하기 위해 합의 시스템(예를 들어, Pos, Pow 등)을 활용한다.
- 합의 시스템은 일반적으로 프로토콜을 준수하는 블록 게시자(Miner, 채굴자)에게 암호화폐를 보상하여 악의적이지 않는 행동을 하도록 한다.

### Permissioned

- 사용자, 또는 노드가 일부 권한을 승인 받아야 하는 블록체인 네트워크이다. (권한의 승인을 중앙 집중형에서 받든, 분산형에서 받든)
- 승인된 개인만이 트랜잭션을 제출할 수 있다. 따라서 무허가 블록체인 네트워크와 같은 리소스를 과하게 소비하는 합의 방식은 필요로 하지 않는다. (이미 승인되어 신뢰할 수 있는 사용자로 보기 때문에)
- 참여하기 위해 본인의 신원 확인이 필요하며, 사로간의 신뢰로 네트워크가 유지된다.

## 블록체인의 구성 요소

### 암호화를 위한 해시 함수

- 블록체인 네트워크에서 해시 함수(SHA-256 등)는 다양한 작업에 사용된다.

#### 사용 예시

- Address derivation.
- Creating unique identifiers.
- Securing the block data: a publishing node will hash the block data, creating a digest that will be stored within the block header.
- Securing the block header: a publishing node will hash the block header. If the blockchain network utilizes a proof of work consensus model, the publishing node will need to hash the block header with different nonce values until the puzzle requirements have been fulfilled. The current block header’s hash digest will be included within the next block’s header, where it will secure the current block header data.

### 암호화 nonce

- nonce는 한번만 사용되는 임의의 숫자이다.
- 데이터와 결합하여 nonce마다 다른 해시를 생성한다.

```
hash(data + nonce) = digest
```

- 즉, nonce 값만 변경하면 동일한 데이터에 대해 다른 다이제스트(digest) 값을 얻을 수 있으며, 이는 작업 증명 합의 모델에서 사용한다.

### 거래

- 블록체인 네트워크의 각 블록에는 0개 이상의 트랜잭션이 포함될 수 있다. 블록체인 네트워크의 보안을 유지하기 위해 새로운 블록의 지속적인 공급은 매우 중요하다. 이를 위해 트랜잭션이 발생하지 않더라도 지속해서 블록을 생성하여야 한다.
- 새로운 블록을 지속적으로 공급함으로써 악의적인 사용자가 더 길고 위조된 블록체인을 제조하는 것을 방지한다.
- 또한, 거래의 유효성과 신뢰성을 결정하는 것은 매우 중요하다. 트랜잭션의 유효성은 프로토콜 요구 사항 및 블록체인 네트워크의 구현과 관련된 모든 형식화된 데이터 형식, 또는 스마트 계약 요구 사항을 충족하는 지 확인한다. 거래의 진위 여부는 디지털 자산의 발신자가 해당 디지털 자산에 엑세스할 수 있는지 여부를 결정하므로, 매우 중요하다.
- 트랜잭션은 일반적으로 발신자의 개인 키로 디지털 서명되며, 매칭되는 공개 키를 이용하여 언제든지 확인할 수 있다.

![Feature 5](https://kihyeon-hong.github.io/Collection_of_repository_images/Blockchain_basic_study/figure1.JPG)

### 비대칭키 암호화 (공개키 암호화)

-
