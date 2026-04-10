# Error
```c
#include <stdio.h>

int main() {
	int a = 1, b = 2, c = 3;
	int max;

	if (a > b)
		max = a;

	else if (b > c)
		max = b;

	else if (a > c)
		max = a;

	printf("max: %d", max);

	return 0;
}
------------------------
int main() {
	int a = 1, b = 2, c = 3;
	int max;

	if (a > b)
		max = a;

	else if (b > c)
		max = b;

	else if (a > c)
		max = a;

	printf("max: %d", max);

	return 0;
}
```
