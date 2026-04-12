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
<img width="682" height="795" alt="image" src="https://github.com/user-attachments/assets/b6a0b70e-702e-4141-afe1-c4bd2df8b407" />




























