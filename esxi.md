# esxi 설치
![esx11](https://user-images.githubusercontent.com/63625609/80325068-b0ab0700-886e-11ea-84fc-77492fdb7cbe.png)
esxi 뒤에 숫자는 버전마다 다름. 
![esx12](https://user-images.githubusercontent.com/63625609/80325149-efd95800-886e-11ea-90f4-0a3c9f8e4639.png)
인스톨러 로딩화면입니다. 
![esx13](https://user-images.githubusercontent.com/63625609/80325200-29aa5e80-886f-11ea-8936-5a2cd4c42cf4.png)
설치를 위한 하드웨어 로딩화면입니다
![esx14](https://user-images.githubusercontent.com/63625609/80325262-59596680-886f-11ea-8eb4-52067e1eab2a.png)
설치를 진행하려면 `Enter` 취소하려면 `Esc` 를 누르면 됩니다.
![esx15](https://user-images.githubusercontent.com/63625609/80325302-8c9bf580-886f-11ea-940c-7d51f38acb26.png)
최종 사용자 동의문입니다. `F11` 을 눌러 동의하면 진행됩니다.
![esx16](https://user-images.githubusercontent.com/63625609/80325344-c40aa200-886f-11ea-9d88-32712f8e0b89.png)
디바이스를 찾는 동안 기다려 주시면 됩니다.
![esx17](https://user-images.githubusercontent.com/63625609/80325383-e8667e80-886f-11ea-97c3-542d30e9a17e.png)
설치할 장치를 선택하면 됩니다. HDD나 SSD에 설치 해도 되고 USB에도 설치할 수 있습니다.
![esx18](https://user-images.githubusercontent.com/63625609/80325453-2499df00-8870-11ea-916d-396fa65041dc.png)
키보드 레이아웃 선택화면입니다. `US Default` 를 선택합니다.
![다운로드](https://user-images.githubusercontent.com/63625609/80325537-8e19ed80-8870-11ea-9b9a-ba804af22274.png) <br>
서버 접속 root계정 비밀번호 설정화면입니다. 위아래 같은 비밀번호를 적은후 `Enter` 를 눌러 진행합니다. <br>
![다운로드 (1)](https://user-images.githubusercontent.com/63625609/80325605-d20cf280-8870-11ea-82b0-34218a4e899c.png) <br>
`F11` 을 눌러 설치를 진행합니다.
![esx-22](https://user-images.githubusercontent.com/63625609/80325654-fcf74680-8870-11ea-8eea-24f4d772dde3.png) <br>
설치가 진행됩니다. 100% 완료가 될때까지 시간이 조금 걸리니 기다려주시면 됩니다.
![esx-24](https://user-images.githubusercontent.com/63625609/80325687-2021f600-8871-11ea-831b-0296c94bdeef.png) <br>
`Enter` 를 눌러 Reboot하면 esxi 설치 완료. <br>

-------
1. esxi web 접속 <br>
접속하기 위해서는 esxi가 설치된 서버의 ip주소를 알아야 합니다. esxi서버 설치가 완료되면 `F2` 를 눌러 root 계정을 로그인하고 ip주소를 설정 및 <br>
확인합니다. ex) 192.168.0.238 접속주소는 https://192.168.0.238/ui 입니다. https를 사용하기에 보안 오류가 있을 수 있습니다.
![esxi-vm2](https://user-images.githubusercontent.com/63625609/80325927-1e0c6700-8872-11ea-8d71-652cbbad6483.png)
중간 부분에 `고급` 을 클릭합니다.
![esxi-vm3-1](https://user-images.githubusercontent.com/63625609/80325970-4005e980-8872-11ea-8252-a162ddba982a.png)
밑에 `192.168.0.238(안전하지 않음)` 을 클릭하여 웹페이지를 이동합니다.
