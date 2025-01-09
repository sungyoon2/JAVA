#Ch23.API Class
---
API Class
---
> API의 정의<br>
- "Application Programming Interface"의 약자
- 소프트웨어 어플리케이션 간에 상호 작용하는데 사용되는 일련의 규칙과 도구를 제공하는 인터페이스
		=> 쉽게 말해 개발자가 다른 소프트웨어의 기능을 활용하도록 하는 중요한 개념
- 두 소프트웨어 시스템 간의 상호 작용을 위한 정의된 규약이나 프로토콜을 제공
EX)	데이터의 교환, 서비스의 호출, 라이브러리 함수의 사용 등

> API Class<br>
- 자바 플랫폼에서 제공하는 다양한 라이브러리 및 클래스들을 의미
- 이러한 클래스들은 java API의 일부로 제공됨.
- 따라서 JAVA 언어를 사용하여 소프트웨어를 개발하는 데 도움을 주는 다양한 기능을 제공
> API Class의 종류<br>
```
1. java.lang 패키지	: 기본 데이터 유형, 예외 처리 등의 핵심 클래스 등
2. java.util 패키지	: 컬렉션 프레임워크, 날짜 및 시간 관련 클래스 등
3. java.io 패키지	: 입출력 작업을 위한 클래스
4. java.net 패키지 	: 네트워크 프로그래밍을 위한 클래스
5. javax.swing 패키지 	: GUI (그래픽 사용자 인터페이스)를 개발하기 위한 클래스
```
> Object 클래스<br>
- 패키지 : java.lang
- 모든 자바 클래스의 최상위 부모 클래스로, java.lang 패키지에 속해있음.
- 모든 클래스는 기본적으로 Object 클래스를 암시적으로 상속받음.
```
<종류>
1. toString() 메서드
- 객체를 문자열로 표현하는데 사용.
- System.out.println(obj)와 같은 코드에서 객체를 출력할 때 자동으로 호출

2. equals(Object obj) 메서드
- 두 객체가 동등한지 여부를 비교하는데 사용.
- 기본 구현은 객체의 참조(주소)를 비교하므로, 실제 동등성 비교를 위해 이 메서드를 재정의할 수 있습니다.
- Object 클래스에서 제공되는 equals 메서드는 == 연산자와 동일하게 동작하며, 객체의 래퍼런스(메모리 주고)를 비교
    but, 객체의 내용을 비교하도록 재정의될 뿐임 ==> 예를 들면 String Class나 Integer Class에서!!

3. hashCode() 메서드
- 객체의 해시코드 값을 반환.
- HashMap, HashSet 등과 같은 해시 기반 컬렉션에서 객체를 저장하고 검색하는 데 사용.

4. getClass() 메서드
- 객체의 클래스 정보를 반환
- 리플렉션(Reflection)과 같은 고급 프로그래밍 기술에서 주로 사용.

==> Object 클래스의 메서드들은 모든 자바 클래스에 공통적으로 적용되며, 필요에 따라 이러한 메서드들을 오버라이딩하여 클래스에 특화된 동작을 정의할 수 있음.
```

> Wrapper 클래스 (예: Integer, Double, Boolean 등)<br>
- 패키지: java.lang
- Wrapper 클래스들은 기본적으로 java.lang 패키지에 속해있음.
  -> 따라서 추가적인 import문 없이 사용할 수 있음
```
<사용 예시>
public class C03Wrapper {
	public static void main(String[] args) {
	// Boxing (자료 -> Integer 정수형 객체로 변환)
	Integer obj1 = new Integer(100);
	//The constructor Integer(int) has been deprecated since version 9 and marked for removal
		
	Integer obj2 = new Integer("200");
		
	Integer obj3 = new Integer.valueOf("300");
	Integer obj4 = new Integer.valueOf(100);
		
	// UnBoxing(객체 -> 자료)
		
	int value1 = obj1.intValue(); 			// 100
	System.out.println(value1);
		
	// 자동 Boxing과 자동 unBoxing
		
	Integer obj = 100;				// Auto Boxing
	int num = obj + 100;				// Auto UnBoxing
		System.out.println("결과 : " + num);
```

> 문자열 클래스 (String 클래스)<br>
- 패키지 : java.lang
- 마찬가지로 java.lang 패키지에 속해 있음
  -> 따라서 추가적인 import 문 없이 사용할 수 있음.

> Random 클래스<br>
- 패키지: java.util
- Random 클래스는 난수 생성과 관련된 기능을 제공하며, java.util 패키지에 속해 있음
  -> 따라서 추가적인 import문 없이 사용할 수 있음.

> StringBuffer Class <br>
- 문자열을 나타내는 클래스
- 문자열을 동적으로 변경할 수 있도록 설계되었으며, String 클래스와 달리 내용을 직접 수정할 수 있음.
```
1. append(String str)
 append(Object obj) : 문자열을 뒤에 추가.
2. insert(int offset, String str)
 insert(int offset, Object obj) : 지정된 위치에 문자열을 삽입.
3. delete(int start, int end) : 지징된 범위의 문자를 삭제.
4. reverse() : 문자열을 뒤집음.
5. length() : 현재 문자열의 길이를 반환.
```

> Date  Class<br>
- JAVA에서 날짜와 시간을 나타내기 위한 클래스임
- java 8부터는 새로운 날짜 및 시간 API인 "java.time" 패키지의 LocalDate, LocalTime, LocalDateTime 등으로 대체됨.
```
<사용법>
Date d1 = new Date();			        // 현재 날짜와 시간으로 Date 객체를 설정
System.out.println(d1);											* get ~로 각각 원하는 해당 값을 들고오는 과정 *
System.out.println(d1.getYear() + 1900 +  "년");// getYear은 현년도-1900인 년도가 출력되므로 +1900을 해주어야 현재 연도가 출력됨
System.out.println(d1.getMonth() + 1 + "월");	// getMonth는 0 - 11 까지의 값을 반환하므로 +1을 해주어야됨
System.out.println(d1.getDay() + "일");		// getDay로 일만 ,  0 - 6까지의 값을 반환, 0 : 일요일
System.out.println(d1.getHours() + "시간");						
System.out.println(d1.getMinutes() + "분");		
System.out.println(d1.getSeconds() + "초");
```
> Calendar Class<br>
- 날짜와 시간을 다루기 위한 추상 클래스
- 날짜 계산 및 조작을 위해서 자바에서 제공되는 클래스
- JAVA 8부터는 "java.time" 패키지의 날짜 및 시간 API로 대체됨.
   ==> 하지만 Date 클래스는 여전히 많이 사용되고 있음.
```
<사용법>
Calendar c1 = Calendar.getInstance();		// 현재의 날짜로됨 이를 가져오기 위해 import java.util.Calendar;가 선행
int yy = c1.get(Calendar.YEAR);			// Calender는 하나하나 변수를 지정해야됨
int mm = c1.get(Calendar.MONTH) + 1;
int dd = c1.get(Calendar.DAY_OF_MONTH);
int hh = c1.get(Calendar.HOUR_OF_DAY);
int mi = c1.get(Calendar.MINUTE);
int ss = c1.get(Calendar.SECOND);
int ampm = c1.get(Calendar.AM_PM);		// 12시간제로 이용할시 추가
String[] apName = {"오전", "오후"};		// 오전 = 0, 오후 = 1 => 배열로 한글로 나오게 하기위해 설정
*추가*
- ~일 후의 날짜를 알아보기위해선 get대신 add(Calendar.YEAR, 10)이런식으로 하면됨
- 특정 날짜로 지정하기 위해선, set을 이용하는 방법과, 그냥 c1.set(년, 월, 일, 시) 넣어도됨
```
> 기타<br>
- 일반적으로 java.lang 패키지에 속한 클래스들은 추가적인 import 없이 사용할 수 있음.
- 그 외의 클래스들은 필요에 따라 import 문을 사용하여 해당 패키지를 명시해주어야 함.
