# Ch.5 입력문
---
불러오기
---
> import java.util.*;<br>
```
- *은 java utill의 모든 기능을 사용한다는 의미
- import : 불러오겠다.
- java하는 폴더 .(안에) 있는 모든것(*)을 추가하겠다.
```
---
입력문
---
> 기본<br>
```
1. System.out 					: 표준 출력 스트림 생성 - 모니터
2. System.in					: 표준 입력 스트림 생성 - 키보드
```
> 실수<br>
```
1. nextDouble()
2. nextFloat()
```	
> 정수<br>
```
1. nextInt()
2. nextLong()
3. nextByte()
4. nextShort()
```		
> 논리<br>
```
- nextBoolean()
```		
> 한 단어(String)<br>
```
next()
```		
> 한 줄(String)<br>
```
nextLine()
```	
> Scanner sc = new Scanner(System.in);<br>
```
 - Scanner 장치를 생성해 사용할 수 있도록 참조변수 sc 생성 및 연결

 <입력된 변수 받기>  
String s = sc.next(); 		// next() : 한 문자열(단어), 띄워쓰기 기준으로 한 문자열 만 가능
													// nextLint() : 한 줄
													// nextInt()  : 숫자로 나옴. 대신 변수 앞에 String이 아니라 int로 바꿔야함
```
		
> Scanner 버퍼비우기<br>
```
System.out.print("문자열 입력 : ");
String str = sc.nextLine();	
System.out.print("수 입력 : ");
int num = sc.nextInt();
		
sc.nextLine(); 											// 버퍼공간에 남아 있는 데이터값을 초기화함으로써 str에 문자열을 다시 받을수 있도록 함
		
System.out.print("문자열 입력 (띄워쓰기 포함 문자열) : ");
String str = sc.nextLine();
System.out.println("입력된 문자열 :" + str);
```
		
