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
