# Ch24. 예외처리
---
예외 처리
---
> 예외 처리<br>
- 프로그램 실행 중에 예외가 발생할 수 있는 상황에 대비하여 적절한 조치를 취하는 것을 의미

> 예외<br>
- 프로그램의 정상적인 흐름을 방해하거나 중간시킬 수 있는 상황을 나타냄

> 예외처리 형태<br>
- try-catch문은 예외 처리를 위한 JAVA의 기본적인 구문임.
- JAVA 프로그램에서 예외가 발생할 수 있는 코드 블록을 try 블록내에 배치하고,
- 예외가 발생할 경우에 대한 처리를 catch 클록에서 수행함.

> 예외처리의 구성요소<br>
```
1. try 블록 			: 예외가 발생할 수 있는 코드를 포함하는 블록임.
2. catch 블록		: try 블록에서 발생한 예외를 처리하는 블록임.
								: 여러 개의 catch블록을 사용하여 다양한 종류의 예외를 처리할 수 있음.
3. final 블록		: try블록이나 catch 블록에서 리턴되더라도 항상 실행되어야 하는 블록임.
```

> 예외 종류<br>
```
1. 컴파일 타임 예외 (Checked Exception) 	: 발행 시점 -- 컴파일 시에 발생하는 예외로, 프로그램이 컴파일될 때 확인됨.
  												              : 처리 여부 -- 반드시 예외를 처리해야함. 예외를 처리하지 않으면 컴파일이 되지 않음.
- IOException								: 입출력 작업도중 발생하는 예외
- SQLException							: 데이터베이스와 관련된 예외.
- ClassNotFoundException		: 클래스를 찾을 수 없는 경우 발생하는 예외
- InterruptedException			: 스레드가 중단될 때 발생하는 예외 등


2. 런타임 예외 (Unchecked Exception)	     : 발생 시점 -- 런타임 시에 발생하는 예외로, 프로그램 실행중에 확인됨
												                 : 처리 여부 -- 명시적인 예외 처리가 필요하지 않음. 개발자가 필요하다고 판단하면 예외를 처리할 수 있지만, 강제적으로 처리할 필요는 없음.
- NullPointerException						: null 객체에 접근할 때 발생하는 예외
- ArrayIndexOutOfBounsException		: 배열의 범위를 벗어난 인덱스에 접근할 때 발생하는 예외
- ArithmeticException							: 산술 연산 중 발생하는 예외
- IllegalArgumentException				: 잘못된 인수가 전달될 때 발생하는 예외
- IllegalStateException						: 잭체의 상태가 메소드 호출에 부적절한 경우 발생하는 예외
```
> 예외처리 과정<br>
```
public class EX {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int test = sc.nextInt();
		int test1 = sc.nextInt();

(1) 고전적인 예외 처리
		if(test1 != 0) {
			int num = test / test1;
			System.out.println(num);
		} else {
			System.out.println("0으로 나눌수 없습니다.");
		}
		
(2) 현대적인 예외 처리
		while(true) {
			try {	
				Scanner sc = new Scanner(System.in);
				int test = sc.nextInt();
				int test1 = sc.nextInt();
				
				int num = test = test / test1;
				System.out.println(num);
				
			} catch (Exception e) {								// 정수가 아닌 수가 나올시에 예외 발생, 즉 에러가 발생하므로 이때 catch로 잡아서 Undefined가 출력되도록 설정
				System.out.println("Undefined");
			}
		}
	
