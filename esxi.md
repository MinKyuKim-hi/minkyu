# esxi 설치
1. 홈페이지 접속
다운로드 전에 알아야 할 것으로 esxi는 `무료 vSphere Hypervisor` 나 `유료 vSphere`로 제공됩니다. <br>
우리는 무료인 vSphere Hypervisor에 대해서 알아보겠습니다. <br>
VMware를 검색해서 홈페이지에 접속해 줍니다. https://www.vmware.com/kr.html 클릭 또는 검색해서 접속해줍니다. <br>
![esxi1](https://user-images.githubusercontent.com/63625609/80326477-e2729c80-8873-11ea-824b-cfb90c358414.png)
왼쪽에 메뉴의 `다운로드` 를 클릭합니다.
![esxi2](https://user-images.githubusercontent.com/63625609/80326523-06ce7900-8874-11ea-9c25-9e5d4556c2bd.png)
무료 제품다운로드 항목중 `vSphere Hypervisor` 를 클릭합니다.

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
![esxi-vm2](https://user-images.githubusercontent.com/63625609/80325927-1e0c6700-8872-11ea-8d71-652cbbad6483.png) <br>
중간 부분에 `고급` 을 클릭합니다.
![esxi-vm3-1](https://user-images.githubusercontent.com/63625609/80325970-4005e980-8872-11ea-8252-a162ddba982a.png) <br>
밑에 `192.168.0.238(안전하지 않음)` 을 클릭하여 웹페이지를 이동합니다.
![esxi-vm1-1](https://user-images.githubusercontent.com/63625609/80326034-780d2c80-8872-11ea-9dc1-94378c0c0c98.png) <br>
로그인 화면이 나오면 ID는 `root` 를 입력 암호는 설치시 적었던 비밀번호를 입력후 로그인을 클릭하시면 됩니다.
![esxi-vm4-1](https://user-images.githubusercontent.com/63625609/80326128-b86caa80-8872-11ea-941a-fcf4bcc0295d.png) <br>
로그인후 esxi서버 웹페이지 화면입니다. server사양 및 esxi 버전 등 대략적인 것들을 한눈에 볼 수 있습니다. <br>
저는 이미 몇가지를 사용중 이기에 왼쪽에 가상시스템 및 네트워크, 스토리지에 숫자가 표기 됩니다. esxi의 모든 설정을 하는 화면입니다.

-----
