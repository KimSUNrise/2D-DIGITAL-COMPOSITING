# Merge Operations

#### plus
: A+B
이미지 A와 이미지 B의 합. 결과적으로 보통은 픽셀 값이 1보다 높게 나온다. 레이저 빔을 합하기에 유용하나 매트를 합할 때는 사용하지 않는 것이 좋음.

#### divide
: A/B if A<0 and B<0
-값을 나누지만 두 개의 음수 값이 양수 값이 되는 것을 막는다. divide는 어떤 사진적 operation과도 어울리지 않지만, multiply를 취소하는데 사용할 수 있음.

#### average
: (A+B)/2
-두 이미지의 평균. 원래의 이미지보다 결과물이 어두워짐.

#### over
: A+B(1-a)
-가장 기본적이고 자주 쓰이는 공식. 알파가 없을 경우에는 plus와 over가 같다. 이미지 A가 알파를 유지한채 B 위에 얹혀짐. 배경 plate 위에 전경의 요소들을 레이어링 할 때 쓰임.

#### atop
: Ab+B(1-a)
-이미지 B와 B를 덥고 있는 만큼의 이미지 A만 보여줌.

#### color-burn
: darken B towards A
-A의 빛에 기초하여 B를 어둡게 만든다.

#### color-dodge
: Brighten B towards A
-A의 빛에 기초하여 이미지 B를 밝게 만든다.

#### conjoint-over
: A+B(1-a/b)
-over와 비슷함. A와 B의 알파가 이중으로 겹칠 때 사용하며, A가 B를 숨기면서 결합한다. 예를 들어 A와 B의 모서리가 공유하는 두 개의 알패 채널에서 A가 B를 완전히 덮는다. 평범한 over는 이 곳을 약간 투명하게 만들어낸다. 

#### Disjoint-over
: A+B(1-a)/b, A+B if a+b<1
-over와 비슷하지만, 픽셀이 부분적으로 A와 B에 의해 덮힐 때, 두 이미지가 겹쳐지지 않으면서 결합함. 보통 A와 B의 모서리가 공유하는 두 개의 다각형에서 그렇다. 평범한 over는 이 곳을 약간 투명하게 만들어낸다. a가 b의 요소를 없에지 않고 지속시키면서, a의 요소와 b의 요소를 합성하고 싶을 때 유용할 수 있음. 예를 들어 머리, 피부, 옷이 따로 렌더된 CG캐릭터에서는 각 요소가 모두 살아있다. 이 경우에, over를 사용하면 합성된 요소들 주위에 어두운 선이 생길 수 있음. 왜냐하면 over는 이미 배경이 있는 상태에서 또 배경을 지속시키기 때문임. 즉 배경이 두 개나 살아있게 됨.

![conjoint/disjoint-over](https://i2.wp.com/benmcewan.com/blog/wp-content/uploads/2020/09/conjoint-2.gif?resize=781%2C461&ssl=1)

<con/dis-joint 이해를 위한 page : https://benmcewan.com/blog/2020/09/28/disjoint-over-and-conjoint-over-explained/>

#### copy
: A
-그냥 A만 보여준다. 이미지 B의 일부가 여전히 보일 수 있도록 mix나 mack컨트롤을 설정하는 경우에도 유용하다.

#### difference
: abs(A-B)
-픽셀이 얼마만큼 다른지 보여줌. 매우 유사한 두 이미지를 비교하는데 유용하다. 이 모드는 dirrerence keyer로도 사용할 수 있음.

#### Exclusion
: A+B-2AB
-difference의 더 사진적인 형태.

####
From : B-A
-이미지A가 B로 부터 제외됨.

#### Geometric
: 2AB/(A+B)
-두 이미지의 평균을 내는 다른 방법.

#### Hard-light
: multiply if A<0.5, screen if A>0.5
-A의 형태 내의 굉장히 밝고 날카로운 빛에 의해 이미지B가 잔뜩 꾸며짐.

#### Hypot
: sqrt(A*A+B*B)
-plus와 screen과 유사함. 결과물의 밝기가 plus보다는 어둡고, screen보다는 밝음. hypot은 값이 1을 초과하는 것으로 작업한다. screen의 대안으로 반사를 추가하는데 유용함.

#### In
: Ab
이미지A의 영역 중에서 이미지B의 알파와 겹치는 부분만 보여줌. 매트를 결합하는데 유용함.

#### Mask
: Ba
in과 반대되는 것. 이미지B의 영역 중에서 이미지A의 알파와 겹치는 영역만 보여줌.

#### Matte
: Aa+B(1-a)
-합성되지 않은 이미지를 이용하여, 합쳐지기 이전에 완료하는 것.

#### Max
: max (A,B)
-두 이미지의 값을 최대한 챙긴다. 매트를 합치는데 좋은 방법이며 밝은 머리카락의 디테일 같은 양상을 투과시키기에 좋음.

#### Min
: min (A,B)
-두 이미지의 값을 최소한만 챙긴다.

#### Minus
: A-B
-이미지A에 의해 B가 짤림.

#### Multiply
: AB, A if A<0 and B<0
-곱하기 연삽을 하지만 A와 B의 값이 모두 음수일 경우 A의 값만 취해서, 두 개의 음수가 양수가 되는 것을 막음. 이미지A의 더 어두운 값을 B와 합성하는데 쓰임. 또한 grain plate를 추가하는데도 유용함.

#### Out
: A(1-b)
-이미지A의 영역 중에서 이미지B의 알파와 겹치지 않은 부분만 보여줌. 매트를 합치는데 유용함.

#### Overlay
: multiply if B<0.5, screen if B>0.5
-이미지A가 이미지B를 밝게 함.

#### Screen
: A or B < or = 1? A+B-AB: max(A,B)
-screen은 plus와 거의 유사함. A 또는 B ≤1이면 A+B-AB이고, 그렇지 않으면 max(A,B). 즉, A 또는 B가 1보다 작거나 같으면 screen이 사용되며, 그렇지 않으면 max가 선택됨. 매트를 결합하고 레이저 빔을 추가하는 데 유용할 수 있음.

#### Soft-light
: B(2A+(B(1-AB))) if AB<1, 2AB otherwise
-이미지B가 밝아지지만 hard-light만큼 극적이지는 않음.

#### Stencil
: B(1-a)
-out의 반대. 이미지B의 영역 중에서 이미지A의 알파와 겹치지 않은 부분만 보여줌.

#### Under
: A(1-b)+B
-over의 반대. 이미지B의 매트에 따라 B가 A를 덮는다.

#### Xor
: A(1-b)+B(1-a)
-이미지A와 B가 겹치지 않는 부분만 보여줌.

(written based on : https://learn.foundry.com/nuke/content/comp_environment/merging/merge_operations.html)
 
