General Principles (일반 원칙)

Follow Standard Conventions(표준 규칙 준수)
ing-, architecture-, design guidelines (check them with tools)
코딩, 아키텍처, 디자인 가이드라인을 따르고, 이를 도구로 확인 한다.

표준화 된 규칙을 따라 코드의 일관성을 유지할 수 있다.
이를 통해 유지보수와 협업이 용이 해진다.
이를 자동으로 확인 해주는 도구들 도 있다.



Keep it Simple, Stupid (KISS)

Simpler is alwyas better, Reduce complexity as much as possible
더 단순한 것이 항상 더 좋다. 가능한 한 복잡성을 줄여라.

복잡한 설계나 코드를 이해하고 유지하는 것은 어렵기 떄문에,
함수를 하나의 기능단위로 작게 유지하고, 복잡한 알고리즘을 사용하기 보다는 간단한 방법을 선택한다.


Boy Scout Rule 보이스카웃 규칙
Leave the campground cleaner than you found it
캠프를 세울때보다 떠날때 더 꺠끗하게 한다.
코드를 수정할때는 기존 코드보다 더 나은 상태로 남겨둬야 한다.
작은 개선이라도 코드를 더 좋게 만드는데 도움이 된다.

Root Cause Analysis 근본 원인 분석
Always look for the root cause of a problem. Otherwise, it will get you again.
항상 문제의 근본원인을 찾아야 한다. 그렇지 않으면 같은 문제가 다시 발생하게된다.

Multiple Langauges in One Source File
c#, java, javascript등 여러 랭기지와 언어를 한 소스 파일에 혼합하여 사용하지 마라.
여러 언어를 한 파일에 사용하면 코드의 가독성과 유지보수성이 크게 저하된다.

