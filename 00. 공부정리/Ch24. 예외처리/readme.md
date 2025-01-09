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
1. try 블록 		: 예외가 발생할 수 있는 코드를 포함하는 블록임.
2. catch 블록		: try 블록에서 발생한 예외를 처리하는 블록임.
                        : 여러 개의 catch블록을 사용하여 다양한 종류의 예외를 처리할 수 있음.
3. final 블록		: try블록이나 catch 블록에서 리턴되더라도 항상 실행되어야 하는 블록임.
```

> 예외 종류<br>
```
1. 컴파일 타임 예외 (Checked Exception) 	: 발행 시점 -- 컴파일 시에 발생하는 예외로, 프로그램이 컴파일될 때 확인됨.
                                        : 처리 여부 -- 반드시 예외를 처리해야함. 예외를 처리하지 않으면 컴파일이 되지 않음.
- IOException				: 입출력 작업도중 발생하는 예외
- SQLException				: 데이터베이스와 관련된 예외.
- ClassNotFoundException		: 클래스를 찾을 수 없는 경우 발생하는 예외
- InterruptedException			: 스레드가 중단될 때 발생하는 예외 등


2. 런타임 예외 (Unchecked Exception)	 : 발생 시점 -- 런타임 시에 발생하는 예외로, 프로그램 실행중에 확인됨
                                         : 처리 여부 -- 명시적인 예외 처리가 필요하지 않음. 개발자가 필요하다고 판단하면 예외를 처리할 수 있지만, 강제적으로 처리할 필요는 없음.
- NullPointerException			: null 객체에 접근할 때 발생하는 예외
- ArrayIndexOutOfBounsException		: 배열의 범위를 벗어난 인덱스에 접근할 때 발생하는 예외
- ArithmeticException			: 산술 연산 중 발생하는 예외
- IllegalArgumentException		: 잘못된 인수가 전달될 때 발생하는 예외
- IllegalStateException			: 잭체의 상태가 메소드 호출에 부적절한 경우 발생하는 예외
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
```
> 예외 처리시 사용 명령어<br>
```
1. getCause() : 원인 가져오기
2. toString() : 예외객체 정보
3. getStackTrace() : 예외객체 식별주소
4. printStackTrace() : 예외발생정보 출력
5. getMessage() : 예외 메세지 내용 출력
```
> 예외처리 예시(NullPointerException)<br>
```
try {
	String str = null;	
	System.out.println(str.toString());	// 없는 문자열을 toString()으로 출력시도 ==> 예외 발생
} catch(Exception e) {
// e == 참조변수
// 에외 객체가 생성되고 주소번지가 100이라면 try에서 예외가 발생한 후 catch의 참조변수 e가 그 주소번지를 받음
	System.out.println("포인터(참조변수)가 null 참조하고 있습니다.");
	System.out.println(e.getCause());			// getCause() : 원인 가져오기
	System.out.println(e.toString());			// toString() : 예외객체 정보
	System.out.println(e.getStackTrace());			// getStackTrace() : 예외객체 식별주소
	e.printStackTrace();					// printStackTrace() : 예외발생정보 출력
	System.out.println(e.getMessage());			// getMessage() : 예외 메세지 내용 출력
}
```
> Exception 클래스<br>
- 자바에서 예외처리를 위한 기본 클래스 중 하나
- 모든 예외의 부모 클래스로서 다양한 예외들이 Exception을 상속하고 있음, java.lang 패키지에 속해 있음
```
< 상속 관계 >
- Exception 클래스는 Throwable 클래스를 상속하고 있음.
- Throwable은 자바에서 예외 처리의 기본 클래스이며, Error와 Exception 클래스의 부모 클래스임.

< Checked Exception과 Unchecked Exception >
- Exception 클래스의 하위 클래스 중에서 RuntimeException(런타임 예외)을 제외한 예외들은 Checked Exception(컴파일 타임 예외)으로 분류됨
- Checked Exception(컴파일 타임 예외)은 반드시 예외 처리를 해주어야하는 것이 특징임.
```

>  ### throw keyword <br>
- 자바에서 예외를 명시적으로 발생시키기 위한 키워드
- throw 키워드를 사용하여 특정 예외를 강제로 발생시킬 수 있음
```
< 기본 구문 >
throw 예외객체;
throw new ArrayIndexOutOfBoundsException();
// "예외 객체"는 특정 예외 클래스의 인스턴스임.

< 예외 처리는 주로 두 가지 방식으로 나눌 수 있음 >
1. 예외의 직접적인 던지기 (Direct throwing) : 메소드 내에서 예외 조건을 발견했을 때, 해당 예외를 직접 던지는 방식
2. 메소드에게 예외를 떠 넘기기 (rethrowing) : 메소드에서 예외를 처리하지 않고, 해당 예외를 다시 호출한 메소드로 떠넘기는 방식
-> 이는 주로 예외를 발생한 메소드가 예외를 해결할 수 없는 경우에 사용

< 예제 >
1. 직접 던지기 Example
public static void main(String[] args) {
	try {
		Scanner sc = new Scanner(System.in);
		System.out.println("양수를 하나 입력하세요>>>");
		int value = sc.nextInt(); 			// value라는 변수에 입력값을 저장
		if (value < 0) {
		*여기에서 throw문을 사용하여 IllegalArgumentException을 명시적으로 던짐(예외 발생)*
			throw new IllegalArgumentException("음수는 허용되지 않습니다.");   
			}
			System.out.println("값 : " + value);
	} catch (Exception e) {
		e.printStackTrace();
	}

2. 메소드에게 예외를 떠넘기기
public static void someMethod() throws CustomException {
try {
	// 예외 발생 가능성 있는 코드
	int result = 10 / 0;			// ArithmeticException 발생				} catch (ArithmeticException e) {
	* ArithmeticException 예외에 해당하는 예외가 발생했을 때 실행되는 코드 *
	System.out.println("Exception caught in someMethod : " + e.getMessage());
	* 예외를 다시 던짐. (CustomException 예외 발생) *
	throw new CustomException("CustomException ", e);
}
public static void main(String[] args) throws CustomException {
		someMethod();
* 예외를 떠넘기는 메소드가 throws를 사용하여 예외를 선언했다고 해도, 해당 메소드를 호출한 곳에서 반드시 예외를 처리할 필요는 없음.
* 메소드를 호출한 속에서 예외를 처리하지 않으면, 예외는 호출 스택을 따라 더 상위의 메소드로 전파됨.
* 최종적으로는 예외가 처리되지 않은 채로 프로그램이 종료될 수 있음.
* 예외를 상위로 떠넘기다 == 예외가 발생한 메소드에서 예외를 처리하지 않고, 호출한 상위 메소드로 예외를 전파시키는 것
* 호출 스택(call stack)을 따라서 예외가 전파되어 나가게 됨.
}
```
