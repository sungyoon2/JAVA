#Ch27. Writer & Reader
---
- Writer 및 Reader는 문자 단위로 데이터를 처리
- 이는 주로 텍스트 파일을 다룰 때 사용
- 문자 데이터의 경우 텍스트를 읽거나 쓸 떄 인코딩을 고려해야 하며, 문자 스트림을 사용하여 문자 데이터를 더 효과적으로 처리 할 수 있음.
---
> Writer의 실행<br>
```
import java.io.FileWriter;

public class C01Writer {
	public static void main(String[] args) {
		// 파일 경로 설정
		String filepath = "C:\\testFolder\\test.txt";
		try {
			// FileWriter를 사용하여 파일에 텍스트를 추가 (true : 기존 내용 유지, 파일 끝에 데이터(내용) 추가)
			Writer out = new FileWriter(filepath, true);
			
			// 추가할 텍스트 작성
			out.write("안녕하세요\n");
			out.write("파일 테스트 중입니다\n");
			out.write("파일을 생성하고 있습니다.\n");
			
			// 버퍼비우기 & 스트림 닫기
			out.flush();
			out.close();
			System.out.println("텍스트 파일이 추가되었습니다. 확인해보세요 !!!");
		} catch (Exception e) {
			e.printStackTrace();
		}
	}

}
```
> Reader의 실행<br>
```
import java.io.FileReader;

public class C02Reader {
	public static void main(String[] args) {
		// 파일 경로 설정
		String filepath = "c:\\testFolder\\test.txt";
		try {
			// File Reader를 사용하여 파일에서 텍스트 읽기
			Reader in = new FileReader(filepath);
			// 파일에서 한 글자씩 읽어오기
			while(true) {
				int data = in.read();
				if (data == -1) {
					break;
				}
				System.out.print((char) data);
			}
			// 스트림 닫기
			in.close();
		} catch (Exception e) {
			e.printStackTrace();
		}
	}

}
```
