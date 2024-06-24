# 닷넷 프레임워크
> 2002년 마이크로소프트에서 발표한 응용 프로그램개발 환경으로서 프로세스 가상 머신에 속한다.
- 닷넷 프레임워크를 기반으로 만들어진 응용 프로그램은 반드시 닷넷 프레임워크가 미리 설치된 환경에서만 실행된다.
- 닷넷 프로그램은 외형상 EXE/DLL로 기존 프로그램과 동일한 구조다.

### CLR (Common Language Runtime) : 가상 머신 역할
<img src="./Images/1_1.png" width="500"/>

    프로그램 시작 => CLR 로드 => 소스코드를 기계어가 아닌 중간 언어(IL)로 생성 => 프로그램 실행

### 닷넷 호환 언어 (.NET-Compliant Language) : 중간 언어로 번역되는 언어
- C#, Visual Basic,  .NET, F#, C++/CLI
- COBOL, Lisp, Python, Ruby 등의 언어도 중간 언어로 산출할 수 있는 버전 존재

### 공통 중간 언어 (CIL : Common Intermediate Language) : 

