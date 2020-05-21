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



