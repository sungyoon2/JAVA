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
