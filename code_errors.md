# Error
## 최대값 구하기 
```c
// 오답
int main() {
	int a = 3, b = 2, c = 1;
	int max = a;

	if (b > a) // 현재 max와 비교해야 함
		max = b;

	if (b > c)
		max = b;

	if (c > a)
		max = c;
	printf("max: %d", max);

	return 0;
}
// 오답
int main() {
	int a = 1, b = 2, c = 3;
	int max;

	if (a > b) // 모두 참이 아니기에 max에는 쓰레기 값이 들어있음 
		max = a;

	else if (b > c)
		max = b;

	else if (a > c)
		max = a;

	printf("max: %d", max);

	return 0;
}
// 정답
int main() {
	int a = 2, b = 1, c = 3;
	int max = a;

	if (b > max)
		max = b;

	if (c > max)
		max = c;

	printf("max: %d", max);

	return 0;
}
```
## 가변인자 출력 함수
```c
void my_printf(void *format, char *input) {
	// void *는 정체를 모르는 주소, 바로 *format으로 사용 불가
	// *format 하려면 컴파일러가 알아야 하는 게 있어
	// 1바이트씩 읽을지
	// 4바이트씩 읽을지
	// 문자로 볼지
	// 정수로 볼지
	// 그런데 void *는 타입 정보가 없음.
	if (*format == '%') {

	}
```
## Day 28
- <img width="682" height="795" alt="image" src="https://github.com/user-attachments/assets/b6a0b70e-702e-4141-afe1-c4bd2df8b407" />
- ```c
  putchar(*s++);
  putchar(*s);
  s++;
  ```
## A~E for문
```c
int main(void)
{
    char i = 'A';
    char j = 'A';

    for (i = 'A'; i <= 'E'; i++) {
        for (j = 'A'; j <= i; j++) {
            printf("%c", j);
        }
        printf("\n");
    }
        

    return 0;
}
```
## 배열에서 max 값 찾기
```c
int main(void)
{
    int array[5] = { 3, 8, 2, 10, 4 };
    int max = array[0]; // 초기화를 해야 비교 기준이 생김 
    

    for (int i = 1; i < 5; i++) {
        //max = array[i]; // 비교 없이 계속 덮어쓰기만 해서 마지막 원소가 max가 됨

        if (array[i] > max)
            max = array[i];
    }
    printf("max: %d", max);

    return 0;
}
```
## 배열 거꾸로 출력
```c
 int array[5] = { 1,2,3,4,5 };

 for (int i = 4; i < 5; i--) {
     printf("%d ", array[i]);
     if (i == 0)
         break;
 }
```
```c
#include <stdio.h>

int main(void)
{
    int array[5] = { 1, 2, 3, 4, 5 };

    for (int i = 4; i >= 0; i--) {
        printf("%d ", array[i]);
    }

    return 0;
}
```
## 문자열 입력 받아 출력
```c
//char buffer[] = { 0 };  // 배열 크기가 1인 문자 배열 (x)
char buffer[100] = { 0 }; // 바이트 저장, 마지막은 '\0'

printf("문자열 입력: ");
fgets(buffer, sizeof(buffer), stdin);

printf("입력한 문자열: %s", buffer);
```
## 온도 출력
```c
static uint32_t temp_read_period = 0;
void cliTemp(uint8_t argc, char** argv)
{
    if (argc == 1)
    {
        float t = tempRead();
        cliPrintf("temp: %.2f\r\n", t);
    }
    else if (argc == 2)
    {
        if (strcmp(argv[1], "stop") == 0){
            temp_read_period = 0;
            cliPrintf("Temperature Auto Read Stopped!\r\n");
            return NULL;
        }
																
        temp_read_period = atoi(argv[1]); // else추가 안할 시 stop되고 옆의 두 줄 코드 실행
        cliPrintf("Temperature Auto Read Start!\r\n");
        
    }
    else
    {
        cliPrintf("Usage: temp\r\n");
        cliPrintf("       temp read\r\n");
        cliPrintf("       temp stop\r\n");
    }
}
```
## 가드문 활용
```c
// 가드문x
bool thermalReadFrame(uint16_t *frame_buf)
{
    uint16_t i;
    uint16_t data;
    uint16_t addr = MLX90640_RAM_START_ADDR; // 수정 필요?

    for (i=0; i<16; i++)
    {
        if (thermalReadRegister(addr, &data) == true)
        {
            addr++;
            frame_buf[i] = data; 
        }
    }
    return true;
}
```
```c
if (thermalReadRegister(addr, &data) == false)
{
    return false;
}

frame_buf[i] = data;
addr++;
================
if (!thermalReadRegister(addr, &data))
{
    return false;
}

frame_buf[i] = data;
addr++;
```
