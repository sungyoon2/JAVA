# Ch9. 분기문-반복문(While문)
---
반복문
---
- 반복적인 실행이 필요할 때 반복문을 사용함.
		
> while문의 구조<br>
```
	조건식이 참인 경우 반복적으로 코드를 실행한다.
		while(조건) {
			 반복 실행 코드; 					// 조건이 참이면 코드 실행
																	조건이 거짓이면 반복문 종료
		}
```
> while문의 필수 3요소<br>
```
1. 탈출용 변수
	int i = 0;
2. 탈출용 조건식
	while(i <= 10) {
			System.out.println("Hello world");
3. 탈출을 위한 연산식
			i++;		       // 1씩증가함
		}
```
> do - while문의 구조<br>
- while문은 조건식이 거짓이면 실행 X
- do - while문은 무조건 한번 실행 후 조건식 판별
```		
do {																					// 일단 해라
	조건식 판별 전 실행할 코드;																// 조건식에 상관없이 실행
	반복적으로 실행될 코드;																	// 조건식에 상관없이 실행
	} while (조건);																			// 위 코드 실행 후 조건식 판별
																									// true라면 다시 위 코드 반복 실행
																									// false라면 위 코드 반복 실행 X
```
> while - 무한 루프 이용하기<br>
- 값을 사용자로부터 입력받아 모두 더하는 프로크램을 만들기
- 값이 -1이면 프로그램 종료
```		
Scanner sc = new Scanner(System.in);
	
int sum = 0;							// 값 누적용
int num;								// 값 입력받기용
	
while (true) {
	System.out.println("정수 입력 (종료 : -1) >>> ");
	num = sc.nextInt();
	if (num == -1) {								// num가 -1이 입력되면 실행이 종료 즉, break걸림 -> 코드 밖으로 나가 출력 문장이 실행됨
			break;
			}
   		sum = sum + num;								// while 반복문에 의하여 입력된 수를 계속 더함
  		}
System.out.println("누적된 총 합 : " + sum);
```
> continue 예약어<br>
```
1부터 10까지의 수 중에 3의 배수를 제외하고 출력
int i = 1;
while (i <= 10) {
      if (i % 3 == 0) {
				i++;
				continue;								// 근접한 반복문의 조건식으로 돌아감
			}
  System.out.println("i = " + i);
  i++;			
}
```
