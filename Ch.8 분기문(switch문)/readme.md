# Ch.8 분기문(switch문)
---
switch문 (다중 분기)
---
> 정의<br>
- 조건문 중 하나
- 조건문이 여러개일때 각 조건에 따른 코드를 실행할 수 있음.

> 실행 문법<br>
```
switch (변수) {
  case 값1:				// case는 여러개일 수 있다.
					// case == if문이면서 else if문이기도 함.
  실행할 코드1:
  break;				// 위 코드를 실행 후 break;를 만나면 stop역할
  case 값2:				// 얘는 else if
  실행할 코드2;
  break;				// break만나서 stop
  default;				// else문(case의 조건에 부합하지 않을 시 나머지 처리)
  break;
 }
```
