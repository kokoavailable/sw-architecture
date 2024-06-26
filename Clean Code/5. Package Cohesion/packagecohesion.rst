Package Cohesion

패키지 응집도



Release Reuse Equivalency Principle (RREP)
재사용-릴리즈 등가 원칙

The granule of reuse is the granule of release.
재사용의 단위는 릴리즈의 단위와 같다.

특정 기능을 담당하는 클래스 그룹이 있다면, 이 그룹을 하나의 독립적은 패키지로 릴리즈 하여,
다른 프로젝트에서 사용할 수 있을 정도가 돼야한다. 즉 독립적으로 관리되고 배포될 수 있어야한다.




Common Closure Principle (CCP)
공통 폐쇄 원칙

Classes that change together are packaged together
변경이 발생할때 함께 변경되는 클래스들은 하나의 패키지로 묶여있어야 한다.
즉 함께 변경될 가능성이 높은 클래스들은 논리적으로 같은 패키지(또는 모듈)로 그룹화 해야 한다.


Common Reuse Principle (CRP)
공통 재사용 원칙
classes that are used together are packaged together
함께 사용되는 클래스들은 하나의 패키지로 묶여야 한다.

crp 구조의 적용 

com.example.project
│
├── user
│   ├── User.java
│   ├── UserService.java
│   ├── UserController.java
│   ├── UserRepository.java
│
├── order
│   ├── Order.java
│   ├── OrderService.java
│   ├── OrderController.java
│   ├── OrderRepository.java
│
└── payment
    ├── Payment.java
    ├── PaymentService.java
    ├── PaymentController.java
    ├── PaymentRepository.java