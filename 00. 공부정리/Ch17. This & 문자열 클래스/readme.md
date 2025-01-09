# Ch17. This & 문자열 클래스
---
This()
---
- OverLoading(오버로딩)된 다른 생성자 호출 가능.
> 사용 예시<br>
```
class C01Simple {
	int x;
	int y;
	
(1) public C01Simple() {
		
  this(10,20);            -> 변수에 X와 Y에 각각 10,20을 대입해서 (3)의 생성자를 호출해 실행 가능하도록 함
  System.out.println("Default Constructor END");
	}

(2) public C01Simple(int x) {
		
  this(x,20);              -> 원래는 변수 X의 값만 주어지지만 Y값까지 부여되어 (3)을 호출하여 실행
  System.out.println("Parameter(int x) Constructor END");
	}
(3) public C01Simple(int x, int y) {
		System.out.println("Parameter(int x, int y) Constructor START");
		this.x = x;
		this.y = y;
		System.out.println("Parameter(int x, int y) Constructor END");
	}
}

public class C01This {
	public static void main(String[] args) {
		C01Simple obj = new C01Simple();
		C01Simple obj1 = new C01Simple(10);
		C01Simple obj2 = new C01Simple(10,20);
	}
}

< 실행 결과>
Parameter(int x, int y) Constructor START
Parameter(int x, int y) Constructor END
Default Constructor END
Parameter(int x, int y) Constructor START
Parameter(int x, int y) Constructor END
Parameter(int x) Constructor END
Parameter(int x, int y) Constructor START
Parameter(int x, int y) Constructor END
```
---
문자열 클래스 (== String Class)에서의 다양한 메서드
---
> 종류<br>
```
length()         : 문자열의 길이
charAt(X)        : X번째의 문자	
toUpperCase()    : 대문자로 변환
toLowerCase()    : 소문자로 변환
replace('X','Y') : X를 Y로 변환
trim()   	 : 반복실행
Substring()      : 문자열 자르기
		   (2)	 -> 앞에서 두 문자 자르고 출력
                   (0,2) -> 앞에서 두 문자외에 다 짤라내고 출력
indexof("문자열") : 문자열의 index번호 확인
                    해당문자열 X시 '-1' return    // 0부터 시작해서 0,1,2순으로 index번호가 매겨짐
lastIndexOf("문자열") : 문자열의 index번호 확인
			* 뒤에서부터 앞으로 검색
contains("문자열") : 문자열 포함여부
```
		
