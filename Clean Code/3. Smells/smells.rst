Code smells
이상 징후

클린 코드에서 코드 스멜이란, 코드에 잠재적인 문제가 있음을 나타내는 특정 패턴이나 구조를 의미한다.
코드 스멜은 반드시 버그를 포함하고 있지는 않지만, 코드의 가독성, 유지보수성, 확장성에 부정적인 영향을 미칠 가능성이 높은 코드의 특성을 가리킨다.
이는 나쁜 코딩 습관이나 잘못된 설계로 인해 발생하며, 장기적으로 소프퉤어 개발과 유지보수를 어렵게 만든다.




Rigidity(경직성)

the software is difficult to change. 
변경하기 어려운 소프트웨어

A small change causes a cascade of subsequent changes
작은 변경이 연쇄적 변경을 초래한다.


Fragility(취약성)
The software breaks in many places due to a single change.
하나의 변경으로도 많은 부분에서 고장나는 소프트웨어.


Immobility(비유동성)
You cannot reuse parts of the code in other projects because of involved
risks and high effort.
다른 프로젝트에서, 리스크와 높은 코스트 때문에, 코드의 일부를 재사용할 수 없는 소프트웨어.

Viscoity of design(끈적한 디자인(디자인을 따르는 것이 얼마나 어려운가))
Taking a shortcut and introducing technical debt requires less effort than
doing it right.
지름길을 택하고, 기술적 부채를 유발하는것이 올바른 디자인을 택하는 것보다 훨씬 쉬운 경우

Viscoity of Environtment(끈적한 환경)
Building, testing and other tasks take a long time. 
Therefore, these activities are not executed properly by everyone and technical debt is introduced.
구축이나, 테스트등에 긴 시간이 걸리기 때문에, 
아무도 올바르게 이런 행동들을 하지 않고 기술적 부채가 유발된다.

Needless Complexity(불필요한 복잡성)
The design contains elements that are currently not useful. 
설계가 현재 쓸모없는 엘리먼트들을 포함되어 있다.
The added complexity makes the code harder to comprehend. 
쓸모 없는 엘리먼트로인해 추가된 복잡성은 코드를 이해하기 어렵게 만든다.
Therefore, extending and changing the code results in higher effort than necessary.
그러므로 코드를 확장하고 변경하는데 필요한 노력도 증가한다.

Needless Repetition(불필요한 중복)
Code contains exact code duplications or design duplicates (doing the same
thing in a different way).
똑같은 코드가 중복되어 있거나, 설계(다른 방식으로 동일한 작업을 수행)에 똑같은 중복이 포함되어 있다.
Making a change to a duplicated piece of code is
more expensive and more error-prone because the change has to be made
in several places with the risk that one place is not changed accordingly.
중복된 코드를 수정하는 것은 더 비용이 들고, 에러가 발생하기 쉬운일인데, 중복된 모든 부분에서 수정이 이뤄져야 하기 떄문이다.

Opacity(불투명성)
이해하기 어려운 코드로, 어떤 변경이든 먼저 코드를 다시 분석하는 데 추가 시간이 필요하며,
부작용을 이해하지 못해 결함이 발생할 가능성이 더 높다.