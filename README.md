# Uniswap v2 로 배우는 Defi ( AMM DEX )
Uniswap v2 code 를 가지고 실전 solidity programming 과, evm 의 기능과 한계를 알아본다.

## 목차
- Background
- Why ?
- What
  

## Background
수많은 dex 설명 문서와, solidity 강좌들이 있지만, 정작 개발자들, 특히 solidity developer 가 체감( code 를 눈으로 봐야 이해)할 수 있는 자료는 드물다.

특히, 한글 자료는 더더욱 희귀(?)한 실정이어서, dex 를 이해하고, 새로이 만들어 보려는 solidity developer 에게 도움이 되고자 만들었다.

## Why?
Uniswap 은 Ethereum 의 대표 DEX(Decentralize EXchange) 이다. 특히 v2 는 아직도 현역이라고 볼 수 있을 만큼 사용이 되고 있으며, 수많은 fork ( pancakeswap 같은)의 원천이어서, 대표성을 가진다.

또한, code 내부를 보면, [실전]에서의 필요한 사항과 최적화, EVM 에 대한 최소한의 이해가 필요하다. 그래서 실전 DEX 를 이해하는 데에 좋은 참고자료라 생각했다.

그리고 v3 버전이 최신 버전인데, v2 를 선택한 이유는, v2 버전은 v3 에 비해, 상대적(?)으로 code 가 간결하다. v3 는 license 문제로 인해, fork 가 쉽지 않아서, 이를 기반으로한 DEX 를 만들어서 서비스하기가 힘들다.

v3 를 이용하여 dApp 을 만드는 건, v2 와 동일한 interface 이므로, v2 를 배우는 것만으로도 충분하다.


## What ( 무엇을 배우는가 )
- Uniswap 의 근원 원리 CFMM 에 대한 설명( 필요한 핵심만 )
- Uniswap contract 소스들의 구조(관계)
- CFMM 원리에 해당하는 code 가 어디인지( 어떻게 동작하는 지 )
- Flash swap 은 어떻게 동작하는 지
- 실전에서 soldity optimize( gas 최적화, EVM 한계 우회하기)는 어떻게 했는지  
- Uniswap v2 를 이용해서 또 다른 dApp Contract 을 만드는 방법

모든 설명은 가능한, 이해하는 데 필수적인 내용만 추려서 설명하고자 한다.

## 준비물
- Uniswap v2 사용 경험/이해
  - [Uniswap v2 공식 문서](https://docs.uniswap.org/contracts/v2/overview)
- Solidity 기본 학습( 이 문서는 solidity tutorial 이 아니다 )
- Uniswap v2 contract sources


| Repository                                                            | Description                                                                                                                | url                      |
| --------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- | ------------------------ |
| [v2 core](https://github.com/Uniswap/v2-core)                         | Uniswap v2 의 핵심 contracts. 상장(listing), 핵심 거래 logic(LP, Swap)                                                       |https://github.com/Uniswap/v2-core |
| [v2 periphery](https://github.com/Uniswap/v2-periphery)               | Uniswap v2 core 를 엮어 서비스로 연계하기 위한 contracts.                                      | https://github.com/Uniswap/v2-core                   |


[ 시작(LFG) ! ](./CFMM/README.md)
