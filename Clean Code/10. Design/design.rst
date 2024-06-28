Design


Keep Configurable Data at High Levels
설정 데이터가 있다면 하이 레벨에 둬라.



If you have a constant such as default or configuration value that is known
and expected at a high level of abstraction, do not bury it in a low-level
function. 
기본값이나 설정 값과 같은 상수를 고수준의 추상화 단계에서 이미 알고 있다면, 
이를 저수준 함수에 묻어두지 마라.

Expose it as an argument to the low-level function called from the
high-level function.
고 수준 함수에서 변수를 만들고 인수로 저수준 함수에 전달하게 하라.



=========

Don’t Be Arbitrary +
임의적인 사람이 되지 마라.


Have a reason for the way you structure your code, and make sure that
reason is communicated by the structure of the code. 
코드의 구조를 짜는데는 이유가 있어야 하며, 그 이유가 코드 구조에 의해 명확히 전달되도록 해야한다.

If a structure appears
arbitrary, others will feel empowered to change it.
만약 구조가 그냥 임의로 짜진 것처럼 보인다면, 누군가는 코드를 아무렇게나 바꾸고 싶어할 것이다.

=====


Be Precise +
정확하고 명확하게 할 것.
When you make a decision in your code, make sure you make it precisely.
코드짜는 중 무언가를 결심한다면, 정확하게 내려야한다.

Know why you have made it and how you will deal with any exceptions.
왜 그렇게 결정했는지, 예외들은 어떻게 처리할 것인지 알고 있어야 한다.



Structure over Convention +
컨벤션보다는 구조를 우선시 할 것.
Enforce design decisions with structure over convention. 
설계(코드나 시스템의 배치, 모듈화, 클래스)자체를 컨벤션보다 우선시 하라.
Naming conventions are good, but they are inferior to structures that force
compliance.
네이밍 규칙도 좋다, 하지만 구조적 강제보다는 부족하다.(인터 페이스 등..)

Prefer Polymorphism To If/Else or Switch/Case +
if/else, switch/case 등의 조건문보다는 다형성을 활용해라.

“ONE SWITCH”: There may be no more than one switch statement for a
given type of selection. The cases in that switch statement must create
polymorphic objects that take the place of other such switch statements in
the rest of the system.
Symmetry / Analogy +
Favour symmetric designs (e.g. Load – Save) and designs that follow
analogies (e.g. same design as found in .NET framework).
Separate Multi-Threading Code +
Do not mix code that handles multi-threading aspects with the rest of the
code. Separate them into different classes.