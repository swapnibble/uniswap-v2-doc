# CFMM ( Constant Function Market Maker )
CFMM 이란 말이 흔히 듣는 용어는 아니어서 처음에 거창하지만, 별거 아닌, 그냥 수식으로 거래( 가격과 수량이 정해짐 )한다는 말이다.

이미 다른 문서를 보았다면 잘 알겠지만, 거래를 하기 위한 구성요소는,
- LP( 유동성 공급자, Liquidity Provider )
  - 거래 대상물(token) 을 공급(제공)하고 거래 수수료 수익을 가져가는 주체
- 거래소
  - 거래 logic 을 통해, 거래를 성사시키는 주체
- 거래자(trader)
  - 거래소를 통해, 거래 대상물을 거래(swap) 하는 주체

가 있다. 

![Eocsystem Participants](https://docs.uniswap.org/assets/images/participants-a3e150f3c98a0b402c2063de3e160f2e.jpg)
[이미지 출처: Uniswap Docs]


Uniswap v2 는 이러한 요소중 [ 거래소 ] 를 Smart Contract 으로 구현한 것이고, LP 와 trader 를 중개한다.
이 때 trader 가 거래(swap)를 요청했을 때의 [ 가격, 수량 ] 을 orderbook 이 아닌, 수식으로 결정하는 것이다.

Uniswap 이 사용하는 함수는 
$$x*y=k$$
이다.

여기서, $x$ 와 $y$ 는 거래 대상물(token) 의 '수량(개수)'를 말한다. $k$ 는 단순히 $x$ 와 $y$ 의 곱(multiply)으로 계산되는 값이며, 이 값이 거래(swap)를 할 때는, 항상 상수값(constant, 변하지 않음) 을 가지게 되어서, Constant Function 이라 부른다.

아래의 2가지 원칙을 잊지 말자. 이게 CFMM 의 전부다.
- 유동성 공급/제거일 때만 $k$ 값이 변화한다.
  - token 을 거래소에 넣고, 수수료 수익을 받기를 원하는 주체(LP 행위)
- 거래(swap) 을 할 때엔 $x*y=k$ 에서 $k$ 값이 변하지 않도록 하면 된다.
  


예) ETH-USDT pair 를 거래하는 contract 가정하고,
 - 현재 ETH 100 개, USDT 100,000 개 가 있다고 하면,
 -  $x$ 는 100, $y$ 는 100,000 이며, $k$ 는 10,000,000 이 된다.


이 때, Vitalik(👽) 이 ETH 10 개를 넣으면 몇 개의 USDT 를 받을 수 있을까?
- 거래전: $100(x)*100,000(y)=10,000,000(k)$ 이고,
- 그 미지의 USDT 를 $b$ 라고 표현하면( "10 개 넣고, b 개를 받는다" ),
- $(100 + 10)*(100,000 - b)=10,000,000$ 이므로
- 방정식 계산: $110 * (100,000 - b) = 10,000,000$ 이 된다. $b$ 를 계산하면 받을 수 있는 USDT 수량이 나온다!


이것이 Uniswap v2 의 핵심이고, 이게 전부다. 다른 것은 여기에 flash loan 등의 기능과, gas optimize, LP token 관리가 전부이다.