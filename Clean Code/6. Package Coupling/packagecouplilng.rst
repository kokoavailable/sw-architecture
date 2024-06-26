Package coupling
패키지 결합도.

Acyclic Dependencies Principle (ADP)
비순환 의존성 원칙
The dependency graph of packages must have no cycles.
패키지들의 의존성 그래프는 사이클이 없어야 한다.

순환 의존성은 시스템의 복잡성을 크게 증가 시킨다. 
클래스나 모듈이 서로를 참조하며 의존성이 얽히게 되면, 시스템 전체를 이해하고 유지보수하는 것이 매우 어려워진다.
또한 하나의 클래스를 변경할때 순환구조내의 모든 클래스가 그 변경에 영향을 받을 수 있어 매우 어려워지고
독립적인 테스트가 어려워지며, 멀티스레드 환경에서 데드락 발생 가능성이 올라간다.



Stable Dependencies Principle (SDP)
안정 의존성 원칙
Depend in the direction of stability.
안정된 방향으로 의존해야 한다.

안정적인 패키지는 변경될 가능성이 낮다.
불안정한 패키지는 변경될 가능성이 높다.
이러한 상황에선 , 불안정한 패키지가 안정적인 패키지에 의존해야 한다.

com.example.project
│
├── core
│   ├── CoreUtils.java  // 안정적인 패키지
│
├── service
│   ├── DataService.java  // 덜 안정적인 패키지
│
└── app
    ├── MainApp.java  // 자주 변경되는 패키지

Stable Abstractions Principle (SAP)
안정 추상화 원칙
Abstractness increases with stability
추상화 정도는 안정성과 함께 증가해야 한다.

즉 구체적인 구현만 있는 불안정한 패키지의 단계에서 안정적인 패키지일 수록 interface등 추상화의 정도를 높여야 한다.