# 기억 사항
## 작은수 % 큰수 = 작은수
```c
1 % 10 = 1
5 % 10 = 5
8 % 10 = 8
```
## 변수 a를 사용
```c
int a = 123;
int min = 123 / 60;
int sec = 123 - 60 * min;
```
## if vs if-else
### if-else
- 위에서부터 차례대로 검사, 처음 참이 되는 조건문만 실행하고 아래는 검사x
- 여러 조건 중 하나만 해당되는 경우 
- 학점 구하기, 메뉴 선택, 숫자가 양수 or 음수 or 0인지 판별
- ```c
  	int a;
  // if 여러 개를 써도 동작하지만 조건을 모두 검사하는 불필요한 연산수행
	printf("정수 입력: ");
	scanf_s("%d", &a);

	if (a > 0)
		printf("양수");
	else if (a < 0)
		printf("음수");
	else
		printf("0");
  ```
### if
- 위의 조건이 참이어도 아래 조건도 계속 검사
- 여러 조건이 모두 의미 있을 때 적합
- 최댓값 갱신, 여러 조건 체크, 옵션 여러 개 동시 적용
## 컴파일
- C 컴파일은 전처리, 컴파일, 어셈블, 링크 단계로 이루어지며, GCC/Clang/MSVC 같은 컴파일러를 사용해 실행 파일 또는 임베디드용 바이너리를 생성
```
gcc main.c -o main // 실행 파일
gcc -E main.c -o main.i // 전처리만
gcc -S main.c -o main.s // 컴파일만 (C -> Assembly)
gcc -c main.c -o main.o // 어셈블만
gcc main.o -o main      // 링크 (오브젝트 파일을 실행 파일로 연결)

// 각각 컴파일
gcc -c main.c -o main.o
gcc -c led.c -o led.o
gcc -c uart.c -o uart.o
gcc main.o led.o uart.o -o app // 링크
```
## 컴파일러 종류
### GCC
- Linux에서 많이 사용
- Windows에서도 MinGW, MSYS2로 사용 가능
- 임베디드용 크로스 컴파일러도 많음
### MSVC
- 마소의 C/C++ 컴파일러
- Visual Studio에서 주로 사용
- ```
  cl main.c
  ```
### 임베디드용 크로스 컴파일러
- 크로스 컴파일: PC에서 AVR, STM32용 바이너리 생성 
- AVR: avr-gcc
- ARM Cortex-M: arm-none-eabi-gcc
- ```
  arm-none-eabi-gcc main.c -o main.elf // STM32 
  ```
### 디버그 빌드/ 릴리즈 빌드
- ```
  gcc -g main.c -o main // 디버그 빌드 (디버그 정보 포함, GDB 같은 디버거 사용 가능)
  ```
### 결과 파일 종류
- .i: 전처리 결과 파일
- .s: 어셈블리 파일
- .o: 오브젝트 파일
- .elf: 임베디드용 실행/디버그용 파일
- .hex: MCU 플래시에 올리기 좋은 텍스트 형식 바이너리 (데이터, 메모리 주소, 체크섬)
- .bin: 순수 바이너리 파일
- .exe: Windows 실행 파일
### PC 개발과 임베디드 개발의 차이
```
./main // PC 실행파일
```
```
arm-none-eabi-gcc main.c -o main.elf // 임베디드 C개발
```
- .elf 생성
- 필요하면 .bin, .hex 변환
- 보드에 다운로드
- 디버거(ST-LINK, J-LINK 등)로 실행
-임베디드는 컴파일 후 바로 PC에서 실행하는 게 아니라 보드에 올림

## Makefile 
- 파일이 많아지면 명령어를 매번 치기 어려움
### 실행
```
make // 자동 빌드, 변경된 것만 다시 빌드, 대형 프로젝트에 적합
```
## CLI (Command Line Interface)
- 글자로 명령어를 입력해서 프로그램이나 시스템을 조작하는 방식
- GUI는 마우스로 폴더, 버튼 등 선택 
- ```
  cd project
  gcc main.c -o main
  ./main
  ```
### 임베디드에서의 CLI
1. PC의 명령어 창 (터미널에서 빌드, flash 다운로드, git 사용)
2. 보드 안의 CLI 기능은 UART로 연결하여 사용 (led on, help, status)
3. 장치 내부에 만든 명령어 인터페이스, 즉 MCU 프로그램 안에 간단한 셸을 만든 

  makefile, cmake 차이, 터미널, 쉘 차이, cl, 빌드, make 차이 























