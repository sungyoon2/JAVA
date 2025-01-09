# Ch25. JDBC
---
JDBD
---
JDBC를 사용하기 위해선 import java.sql.Connection; 이 선행 필수
> Connect하기<br>
```
public class Connect {
	public static void main(String[] args) {
		// 연결관련 정보 저장용 변수
		String id = "root";					// DB연결 ID
		String pwd = "1234";					// DB연결 PWD
		String url = "jdbc:mysql://localhost:3306/testdb";	// 연결 URL
		
		// DB연결 객체 관련 참조 변수
		Connection conn = null;					// DB연결객체용 참조변수
		PreparedStatement pstmt = null;			        // SQL쿼리 전송객체용 참조변수
		ResultSet rs = null;					// 쿼리결과(Select결과) 수신용 참조변수
		// 연결하기
		try {
			class.forName("com.mysql.cj.jdbc.Driver");	// DB 드라이버 로드
			System.out.println("Driver loading Success!!!");
			conn = DriverManager.getConnection(url, id, pwd);// DB Connection 객체 받기
			System.out.println("DB Connected ---");
		} catch(Exception e) {
			e.printStackTrace();
		} finally {
			try {conn.close();} catch(Exception e) {e.printStackTrace();}
		}
	}
}
```
> Insert하기<br>
```
public class INSERT {
	public static void main(String[] args) {
		// 연결관련 정보 저장용 변수
		String id = "root";					// DB연결 ID
		String pwd = "1234";					// DB연결 PWD
		String url = "jdbc:mysql://localhost:3306/testdb";	// 연결 URL
		// DB연결 객체 관련 참조 변수
		Connection conn = null;					// DB연결객체용 참조변수
		PreparedStatement pstmt = null;				// SQL쿼리 전송객체용 참조변수
		ResultSet rs = null;					// 쿼리결과(Select결과) 수신용 참조변수		
	<데이터베이스 구문>
    	1. 데이터베이스 생성
		CREATE SCHEMA testdb;
    	2. 테이블 생성
		CREATE TABLE testdb.tbl_customer (
				idx INT UNSIGNED PRIMARY KEY AUTO_INCREMENT,
				name VARCHAR(30) NOT NULL,
				age TINYINT UNSINGED NOT NULL,
				address VARCHAR(30) NOT NULL
				);
		
   	 3. 연결하기 및 데이터 삽입
		try {
			Class.forName("com.mysql.cj.jdbc.Driver");			// DB 드라이버 로드
			System.out.println("Driver Loading Success!!!")
			conn = DriverManager.getConnection(url, id, pwd);		// DB Connection 객체 받기
			System.out.println("DB Connected - - -");
			pstmt = conn.prepareStatement("INSERT INTO testdb.tbl_customer VALUES(?, ?, ?, ?)");
			pstmt.setInt(1, 3);
			pstmt.setString(2, "곰돌이");
			pstmt.setInt(3, 2);
			pstmt.setString(4, "대구광역시");
			
			int result = pstmt.executeUpdate();
			if (result > 0) {
				System.out.println("INSERT 성공");
			} else {
				System.out.println("INSERT 실패");
			}
	4. 데이터 조회
			SELECT * FROM testdb.tbl_customer;
			
		} catch(Exception e) {
			e.printStackTrace();
		} finally {
			try {pstmt.close();}catch(Exception e) {e.printStackTrace();}
			try {conn.close();} catch(Exception e) {e.printStackTrace();}
		}
		
	}

}
```
> Delete하기<br>
```
public class DELETE {
	public static void main(String[] args) {
		// 연결관련 정보 저장용 변수
		String id = "root";					// DB연결 ID
		String pwd = "1234";					// DB연결 PWD
		String url = "jdbc:mysql://localhost:3306/testdb";	// 연결 URL
		
		// DB연결 객체 관련 참조 변수
		Connection conn = null;					// DB연결객체용 참조변수
		PreparedStatement pstmt = null;				// SQL쿼리 전송객체용 참조변수
		ResultSet rs = null;					// 쿼리결과(Select결과) 수신용 참조변수
	1. 연결하기 및 데이터 삭제
		try {
			class.forName("com.mysql.cj.jdbc.Driver");	// DB 드라이버 로드
			System.out.println("Driver loading Success!!!");
			conn = DriverManager.getConnection(url, id, pwd);// DB Connection 객체 받기
			System.out.println("DB Connected ---");
			
			pstmt = conn.prepareStatement("DELETE FROM testdb.tbl_customer WHERE idx=?");
			pstmt.setInt(1, 1);
			int result = pstmt.executeUpdate();
			if (result != 0) {
				System.out.println("DELETE 성공");
			} else {
				System.out.println("DELETE 실패");
			}
	2. 데이터 조회
			SELECT * FROM testdb.tbl_customer;
		} catch(Exception e) {
			e.printStackTrace();
		} finally {
			try {pstmt.close();}catch(Exception e) {e.printStackTrace();}
			try {conn.close();} catch(Exception e) {e.printStackTrace();}
		}
	}

}
```
> Update하기<br>
```
public class UPDATE {
	public static void main(String[] args) {
		// 연결관련 정보 저장용 변수
		String id = "root";					// DB연결 ID
		String pwd = "1234";					// DB연결 PWD
		String url = "jdbc:mysql://localhost:3306/testdb";	// 연결 URL
		
		// DB연결 객체 관련 참조 변수
		Connection conn = null;					// DB연결객체용 참조변수
		PreparedStatement pstmt = null;				// SQL쿼리 전송객체용 참조변수
		ResultSet rs = null;					// 쿼리결과(Select결과) 수신용 참조변수
	1. 연결하기 및 데이터 업데이트
		try {
			class.forName("com.mysql.cj.jdbc.Driver");	// DB 드라이버 로드
			System.out.println("Driver loading Success!!!");
			conn = DriverManager.getConnection(url, id, pwd);// DB Connection 객체 받기
			System.out.println("DB Connected ---");
			
			pstmt = conn.prepareStatement("UPDATE FROM testdb.tbl_customer set address =? WHERE idx=?");
			pstmt.setString(1, "고양이 집");
			pstmt.setInt(2, 2);
			
			int result = pstmt.executeUpdate();
			
			if (result != 0) {
				System.out.println("UPDATE 성공");
			} else {
				System.out.println("UPDATE 실패");
			}
	2. 데이터 조회
			SELECT * FROM testdb.tbl_customer;
		} catch(Exception e) {
			e.printStackTrace();
		} finally {
			try {pstmt.close();}catch(Exception e) {e.printStackTrace();}
			try {conn.close();} catch(Exception e) {e.printStackTrace();}
		}
	}

}
```
> Select하기<br>
```
public class C05SELECT {
	public static void main(String[] args) {
		// 연결관련 정보 저장용 변수
		String id = "root";					// DB연결 ID
		String pwd = "1234";					// DB연결 PWD
		String url = "jdbc:mysql://localhost:3306/testdb";	// 연결 URL
		
		// DB연결 객체 관련 참조 변수
		Connection conn = null;					// DB연결객체용 참조변수
		PreparedStatement pstmt = null;				// SQL쿼리 전송객체용 참조변수
		ResultSet rs = null;					// 쿼리결과(Select결과) 수신용 참조변수
	1. 연결하기 및 데이터 조회
		try {
			class.forName("com.mysql.cj.jdbc.Driver");	// DB 드라이버 로드
			System.out.println("Driver loading Success!!!");
			conn = DriverManager.getConnection(url, id, pwd);// DB Connection 객체 받기
			System.out.println("DB Connected ---");
			
			pstmt = conn.prepareStatement("SELECT * FROM testdb.tbl_customer");
			
			rs = pstmt.executeQuery();
			if (rs != null) {
			** 조회한 결과값이 있다면 **
				 while(rs.next()) {
					System.out.println(rs.getString("idx") + " "); 
					System.out.println(rs.getString("name") + " "); 
					System.out.println(rs.getString("age") + " "); 
					System.out.println(rs.getString("address") + " "); 
				 }
			} else {
				System.out.println("UPDATE 실패");
			}
	2. 데이터 조회
			SELECT * FROM testdb.tbl_customer;
		} catch(Exception e) {
			e.printStackTrace();
		} finally {
			try {rs.close();}catch(Exception e) {e.printStackTrace();}
			try {pstmt.close();}catch(Exception e) {e.printStackTrace();}
			try {conn.close();} catch(Exception e) {e.printStackTrace();}
		}
	}

}






