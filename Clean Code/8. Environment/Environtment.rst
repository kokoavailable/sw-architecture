Environtment(환경)

Project Build Requires Only One Step +
프로젝트 빌드는 하나의 명령으로 수행돼야 한다.
Check out and then build with a single command.
빌드 프로세스가 간단하고 자동화 돼야 하며, 빌드 절차가 복잡하지 않아야 한다.
단일 명령으로 전체 프로젝트를 빌드 할 수 있어야 한다.

Executing Tests Requires Only One Step +
Run all unit tests with a single command.
모든 단위 테스트를 하나의 명령으로 실행할 수 있어야 한다.
단일 명령으로 전체 테스트 스위트를 실행할 수 있어야 한다.

Source Control System +
Always use a source control system.
항상 소스 제어 시스템을 사용해야 한다.

항상 git등을 사용하여 코드 변경 내용을 추적하고 협업을 용이하게 해야한다.

Continuous Integration +
Assure integrity with Continuous Integration
지속적 통합을 통해 시스템의 무결성을 보장해야 한다.

CI 서버를 사용해 코드 변경시마다 자동으로 빌드 및 테스트를 수행해 코드의 무결성을 유지해야한다.
jenkins, github actions. 등..

Overridden Safeties –
Do not override warnings, errors, exception handling – they will catch you.
경고, 오류, 예외처리를 무시한다면 이러한 것들은 결국 잡아내게 될것이다.

이러한 안전 장치는 잠재적 버그와 문제를 잡아내는데 중요하다.
즉 컴파일러의 경고를 억제하기 위해 @SuppressWarnings  등의 어노테이션을 남용하는 것보다는 경고와 오류를 해결하고
예외 처리를 적절히 구현해 잡재적 문제를 미리 방지한다.