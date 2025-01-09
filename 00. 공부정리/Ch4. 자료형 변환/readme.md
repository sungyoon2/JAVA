# Ch4. 자료형 변환
---
자료형 변환의 종류
---
> 종류 및 정의<br>
```
1. 자동형변환 ( 암시적 형 변환 ) : 컴파일러가 자동으로 형 변환해주는 경우
2. 강제형변환 ( 명시적 형 변환 ) : 개발자(프로그래머)가 인위적으로 강제로 형 변환하는 경우.
```
--- 
자동형변환
---
> 자동형변환하는 이유<br>
```
- 범위가 넓은 자료형에 범위가 좁은 자료형이 대입되는 경우
- 컴파일러가 알아서 형 변환을 해준다는건 데이터 손실 가능성이 낮거나 없을 때라는 것임.
- byte < short < int < float < double - 데이터 손실을 최소화
```
> 예시<br>
```
byte bytevar = 100;						// 변수초기화
int intvar = bytevar;						// 자동 형 변환
System.out.println("intvar : " + intvar);					
		
long longvar = intvar;						// 자동 형 변환
System.out.println("longvar :" + longvar);					
		
float floatvar = longvar;					// 자동 형 변환
System.out.println("floatvar :" + floatvar);				
		
double doublevar = floatvar;					// 자동 형 변환(주의), 정수형 자료형 --> 실수형 자료형
System.out.println("doublevar :" + doublevar);
```
---
강제형변환
---
> 강제형변환하는 이유<br>
```
int : 약 -21억 ~ +21억 까지
short : 약 -32768 ~ +35767
char  : 0 ~ 65535
		
프로그래머(개발자)가 특정 자료형을 강제로 형 변환하는 경우
데이터 손실의 가능성 O
좁은 범위의 자료형에다가 큰 값을 넣으려는 경우 발생
```
> 예시<br>
```
1. 데이터 손실의 예시
int num = 128;					// 00000000 00000000 00000000 10000000
byte ch = (byte) num; 				// 10000000  	-> 음수를 지원하는 1 byte에서는 앞에 비트가 부호비트
                                                // -128	== 데이터 손실(128을 넣었는데. -128이 담겨있음)

2. 데어터 손실 X의 예
int num1 = 127;					// 00000000 00000000 00000000 01111111
byte ch1 = (byte) num;				// 01111111
						// 127 == 데이터 손실이 X (127을 넣었는데, 127이 담겨있음)
		
3. 소수점 이하 데이터 소실 !!
double number2 = 3.14;
int num3 = (int) number2;			// 3.14  X ==> 3
						// 데이터 손실!!
```



