## iis에 웹페이지 연결 내부/외부 접속 연결
1. 홈페이지 디렉토리 생성
![주석 2020-05-22 163316](https://user-images.githubusercontent.com/63625609/82643249-27f37100-9c4a-11ea-9d4a-bfa7e71a6d6b.png) <br>
웹 페이지가 소스가 저장될 디렉토리를 생성합니다. <br>

-----
2. 메모장에서 테스트 페이지 파일 생성 html파일로 <br>
<html>
<title>minkyu</title>
<body>
test입니다. </br>
홈페이지 www.minkyu.com </br>
이 페이지는 테스트페이지 입니다. </br>
</body>
</html>
메모장을 이용해 테스트 페이지 html 파일을 작성합니다. <br>

-----
3. iis관리자 열기
![주석 2020-05-22 164257](https://user-images.githubusercontent.com/63625609/82643900-5291f980-9c4b-11ea-8a22-402160f28063.png) <br>
'서버관리자' -> '도구' -> 'iis관리자'를 실행합니다.

-----
4. 웹사이트 추가 및 설정
![image](https://user-images.githubusercontent.com/63625609/82644040-a43a8400-9c4b-11ea-82a0-f49241939cff.png) <br>
'사이트'에서 마우스 오른쪽 버튼 클릭 후 '웹 사이트 추가' 선택 <br>
![주석 2020-05-22 164804](https://user-images.githubusercontent.com/63625609/82644307-11e6b000-9c4c-11ea-9f7d-dd1e06a11166.png) <br>
사이트 이름 / 홈페이지 경로 / 호스트 이름을 입력합니다. <br>
- '사이트 이름'은 iis관리자 페이지의 '사이트' 항목에 보여질 이름입니다. 
- '실제 경로'는 홈페이지가 서비스될 디렉토리 위치입니다. 1번 항목에서 생성한 디렉토리 경로를 입력합니다.
- 특정 계정과 연결하기 위해서는 '연결 계정'에서 계정을 선택해 줍니다.
- '바인딩'은 서버에 여러 개의 ip주소가 있을 경우, 특정 ip주소 하나로만 서비스를 원할 때, 선택합니다. '지정하지 않은 모든 ip'로 선택되어 있는 경우
서버가 사용중인 모든 ip로 웹서비스를 할 수 있습니다. <br>
- '호스트 이름'은 서비스할 도메인 주소를 입력합니다.

-----
5. 기본 문서 지정
![주석 2020-05-22 165229](https://user-images.githubusercontent.com/63625609/82644694-b36e0180-9c4c-11ea-8365-ad76c019a0af.png) <br>
홈페이지 접속시에 기본으로 보여질 문서를 설정합니다. 마우스 오른쪽 버튼 클릭 -> '추가'
![주석 2020-05-22 165247](https://user-images.githubusercontent.com/63625609/82644700-b537c500-9c4c-11ea-9bba-dbd04e75b772.png) <br>
test.html을 기본문서 항목에 추가합니다. <br>
![주석 2020-05-22 165500](https://user-images.githubusercontent.com/63625609/82644888-00ea6e80-9c4d-11ea-8368-b5507405932c.png) <br>
생성된 기본문서 항목입니다. 맨 위에 위치하도록 해줍니다.

-----
6. 웹 페이지 열기
![주석 2020-05-22 165801](https://user-images.githubusercontent.com/63625609/82645173-6dfe0400-9c4d-11ea-97fa-a121b2404c8e.png) <br>
기본 경로인 "C:\inetpub\wwwroot" 에 test html파일을 복사해서 옮겨놓고 기본경로 설정을 바꿔줍니다. <br>
![주석 2020-05-22 165648](https://user-images.githubusercontent.com/63625609/82645303-a00f6600-9c4d-11ea-9e12-d5460d98fa29.png) <br>
웹 페이지 접속 테스트를 한 화면 입니다. 

-----
7. 외부에서 웹페이지 접속
win box 프로그램을 활용해서 Firewall에 접속하고 +버튼 클릭후 다음과 같이 포트포워딩을 설정합니다. <br>
![주석 2020-05-22 170222](https://user-images.githubusercontent.com/63625609/82645658-317ed800-9c4e-11ea-9168-d7b7fa35ab77.png) <br>
![주석 2020-05-22 170238](https://user-images.githubusercontent.com/63625609/82645662-33489b80-9c4e-11ea-811c-3d5499a3b6eb.png) <br>
dstnat 설정 입니다. <br>
![주석 2020-05-22 170458](https://user-images.githubusercontent.com/63625609/82645790-6c810b80-9c4e-11ea-876a-00161979fec2.png) <br>
![주석 2020-05-22 170513](https://user-images.githubusercontent.com/63625609/82645795-6e4acf00-9c4e-11ea-88e3-f9681a91209b.png) <br>
srcnat 설정 입니다.  <br>
dnszi.com 에 접속해서 웹 포워딩을 설정해줍니다. <br>
![주석 2020-05-22 170150](https://user-images.githubusercontent.com/63625609/82645980-bc5fd280-9c4e-11ea-955f-a005d2dc207b.png) <br>
test.go20.co.kr로 접속하면 다음과 같이 접속되는 것을 확인할 수 있습니다. <br>
![주석 2020-05-22 170918](https://user-images.githubusercontent.com/63625609/82646134-01840480-9c4f-11ea-8814-899c818a57cb.png) 
