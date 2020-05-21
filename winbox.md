##winbox <br>

1. 로더 화면의 버튼 및 필드 설명 <br>
**Simple mode(단순 모드)** <br>
*버튼 / 체크박스* <br>
- Connect(연결) : 라우터에 연결
- Connect To Romon(Romon에 연결) : Romon Agent에 연결
- Add/set(추가/설정) : 관리 탭에서 저장된 라우터 항목을 저장 / 편집합니다.
- Open In New Window(새 창에서 열기) : 로더를 백그라운드에서 열린 상태로 두고 연결되는 각 장치에 대한 새 창을 엽니다.

-----
*필드* <br>
- Connect To(연결) : 라우터의 대상 IP 또는 MAC주소
- Login(로그인) : 인증에 사용된 사용자 이름
- Password(비밀번호) : 인증에 사용된 비밀번호
- Keep Password(비밀번호 유지) : 이 확인란을 선택하지 않으면 비밀번호가 목록에 저장되지 않습니다.

-----
**Advanced mode(고급 모드)** <br>
*버튼 / 체크박스* <br>
- Browse(찾아보기) : 특정 세션에 대한 파일 디렉토리 찾아보기
- Keep Password(비밀번호 유지) : 이 확인란을 선택하지 않으면 비밀번호가 목록에 저장되지 않습니다.
- Secure mode(보안 모드) : 이 옵션을 선택하면 winbox는 DH-1984를 키 교환에 사용하고 수정 및 강화된 Rc4-drop3072 암호화를 사용하여 세션을 보호합니다.
- Autosave session(자동 저장 세션) : 연결이 되는 장치의 세션을 자동으로 저장합니다.

-----
*필드* <br>
- Session : 저장된 라우터 세션
- Note : 라우터 항목을 저장하도록 지정되어 있습니다.
- Group : 저장된 라우터 항목이 할당된 그룹입니다.
- Romon Agent : 사용 가능한 장치 목록에서 Romon에이전트를 선택하십시오.

-----
2. 로더 화면의 메뉴 항목 설명 <br>
*파일* <br>
- New(새로) : 작성-지정된 위치에 새 관리 라우터 목록 작성
- Open : 관리 라우터 목록 파일 열기
- Save As : 현재 관리되는 라우터 목록을 파일로 저장
- Exit : winbox 로더 종료

-----
*도구* <br>
- Advanced Mode(고급 모드) : 고급 모드보기를 활성화 / 비활성화 합니다.
- Import(가져 오기) : 저장된 세션 파일을 가져 옵니다.
- export(내보내기) : 저장된 세션 파일을 내보냅니다.
- Move Session Folder(세션 폴더 이동) : 세션 파일이 저장된 경로 변경
- Clear cache(캐시 지우기) : winbox 캐시 지우기
- Check For Updates(업데이트 확인) :winbox 로더의 업데이트 확인

-----
3.명령행
명령 행을 사용하여 connect,user 및 password 매개 변수를 자동으로 전달할 수 있습니다. <br>
`winbox.exe [<연결대상> [<유저> [<암호>]]]` <br>
*예시* <br>
`winbox.exe 10.5.101.1 관리자 비밀번호` <br>
명령 행을 사용하여 연결,사용자 및 비밀번호 매개 변수를 자동으로 전달하여 Romon을 통해 라우터에 연결할 수 있습니다. 이 경우 winbox가 이 장치의 사용
자와 암호를 알 수 있도록 Romon 에이전트를 관리되는 라우터 목록에 저장해야 합니다. <br>
`winbox.exe --romon [<romon-agent> [<connect-to> [<login> [<password>]]]]` <br>
*예시* <br>
`winbox.exe --romon 10.5.101.1 D4 : CA : 6D : E1 : B5 : 7D 관리자 비밀번호` <br>

-----
winbox는 IPv6 연결을 지원합니다. 라우터 IPv6 주소에 연결하려면 IPv6서버에 연결할 때 웹 브라우저와 동일하게 대괄호로 묶어야 합니다. <br>
*예시* <br>
![Wb-man-3](https://user-images.githubusercontent.com/63625609/82514563-0bbfd900-9b51-11ea-9216-566a3eb3defd.png) <br>
winbox 네이버 감지는 이제 IPv6 사용 라우터를 감지 할 수 있습니다. 아래 이미지에서 볼 수 있듯이 각 IPv6 사용 라우터에는 두개의 항목이 있습니다. 
하나는 IPv4 주소를 사용하고 다른 하나는 IPv6 링크 로컬 주소를 사용합니다. 연결하려는 대상을 쉽게 선택할 수 있습니다. <br>
![Wb-man-2](https://user-images.githubusercontent.com/63625609/82514826-ab7d6700-9b51-11ea-9872-4120e5f498a7.png) <br>

-----
4.인터페이스 <br>
winbox 인터페이스는 대부분의 사용자에게 직관적으로 설계되었습니다. 인터페이스는 다음으로 구성됩니다. <br>
- 사용자가 CPU 및 메모리 사용량과 같은 다양한 정보 필드를 추가할 수 있는 상단의 기본 도구 모음. 
- 왼쪽의 메뉴 모음 : 사용 가능한 모든 메뉴 및 하위 메뉴 목록. 이 목록은 설치된 패키지에 따라 변경됩니다. 예를 들어, IPv6 패키지가 비활성화되어 있으면 IPv6 메뉴와 모든 하위 메뉴가 표시되지 않습니다. <br>
- 작업 영역 : 모든 메뉴 창이 열리는 영역.
![Wb-man-4](https://user-images.githubusercontent.com/63625609/82515115-660d6980-9b52-11ea-91f7-b05e10aec783.png) <br>
제목 표시 줄에는 어떤 라우터 winbox 세션이 열려 있는지 식별하는 정보가 표시 됩니다. 정보는 다음 형식으로 표시됩니다. <br>
`[사용자 이름] @ [라우터의 IP 또는 MAC] ([라우터 ID])-[RB 모델]의 Winbox [ROS 버전] ([플랫폼])` <br>
위의 스크린 샷에서 사용자 krisjanis 가 IPv4 / IPv6 주소 [fe80 :: 4e5e : cff : fef6 : c0ab % 3] 로 라우터에 로그인 되어 있음을 알 수 있습니다.
라우터의 ID는 3C18-Krisjanis_GW 이고, 현재 설치된 RouterOS 버전은 v6.36rc6 이고, 라우터 보드는 CCR1036-12G-4S 이고 플랫폼은 타일 입니다. <br>
기본 도구 모음의 왼쪽에는 실행 취소 및 다시 실행 버튼이 있으며 구성 변경 사항을 신속하게 취소합니다. 오른쪽에는 다음이 있습니다. <br>
- winbox 트래픽 표시기가 녹색 막대로 표시됩니다.
- winbox 세션이 암호화를 사용하는지 여부를 나타내는 표시기

-----
5.작업 공간 및 자식 창 <br>
winbox에는 MDI 인터페이스가 있어서 모든 메뉴 구성 (하위) 미망인이 주 (부모) winbox 창에 연결되어 작업 영역에 표시됩니다. <br>
![Wb-man-5](https://user-images.githubusercontent.com/63625609/82516424-a4f0ee80-9b55-11ea-82bd-dfcdb992e82a.png) <br>
자식 창을 영역 밖으로 끌 수는 없습니다. 위의 스크린 샷에서 인터페이스 창이 보이는 작업영역 밖으로 끌려 가고 하단에 가로 스크롤 막대가 나타납니다.
보이는 작업 영역 경계를 벗어난 창이 있으면 세로 또는 가로 스크롤 막대가 나타납니다.

-----
6.자식 창 메뉴 바
각 자식 창에는 자체 도구 모음이 있습니다. 대부분의 창에는 동일한 도구 모음 단추 세트가 있습니다. <br>
![Win-add](https://user-images.githubusercontent.com/63625609/82516550-0e70fd00-9b56-11ea-8a4d-40c6bff372f4.png)
Add : 목록에 새 항목 추가 <br>
![Win-remove](https://user-images.githubusercontent.com/63625609/82516635-4415e600-9b56-11ea-96c2-d5cdf0c5d3ec.png)
Remove : 목록에서 선택한 항목을 제거 <br>
![Win-enable](https://user-images.githubusercontent.com/63625609/82516708-6b6cb300-9b56-11ea-8d2f-2dd2fcd41c04.png)
Enable : 선택한 항목을 활성화 합니다. ( 콘솔의 enable 명령과 동일) <br>
![Win-disable](https://user-images.githubusercontent.com/63625609/82516785-9eaf4200-9b56-11ea-8873-1979493b8cd7.png)
Disable : 선택한 항목을 비활성화 합니다. ( 콘솔의 disable 명령과 동일) <br>
![Win-comment](https://user-images.githubusercontent.com/63625609/82516890-cf8f7700-9b56-11ea-97b1-9c677434bc97.png)
Comment : 댓글 추가 또는 수정. <br>
![Win-sort](https://user-images.githubusercontent.com/63625609/82516942-ee8e0900-9b56-11ea-837b-86bf11b65df7.png)
Sort : 다양한 매개 변수에 따라 항목을 정렬할 수 있습니다.

-----
거의 모든 창의 도구 모음 오른쪽에 빠른 검색 입력 필드가 있습니다. 이 필드에 입력된 모든 텍스트는 모든 항목을 통해 검색되며 아래 스크린샷 같이 강조 
표시 됩니다. <br>





