# esxi 설치
1. 홈페이지 접속하기 <br>
다운로드 전에 알아야 할 것으로 esxi는 `무료 vSphere Hypervisor` 나 `유료 vSphere`로 제공됩니다. <br>
우리는 무료인 vSphere Hypervisor에 대해서 알아보겠습니다. <br>
VMware를 검색해서 홈페이지에 접속해 줍니다. https://www.vmware.com/kr.html 클릭 또는 검색해서 접속해줍니다. <br>
![esxi1](https://user-images.githubusercontent.com/63625609/80326477-e2729c80-8873-11ea-824b-cfb90c358414.png)
왼쪽에 메뉴의 `다운로드` 를 클릭합니다.
![esxi2](https://user-images.githubusercontent.com/63625609/80326523-06ce7900-8874-11ea-9c25-9e5d4556c2bd.png)
무료 제품다운로드 항목중 `vSphere Hypervisor` 를 클릭합니다.
![esxi3](https://user-images.githubusercontent.com/63625609/80326579-3e3d2580-8874-11ea-8d72-0d349700161c.png)
가운데 메뉴의 `License & Download` 를 클릭합니다. 무료이긴 하지만 로그인을 해야 다운로드가 가능하며 무료 License가 발행 됩니다.

-----
2. 설치 USB만들기 <br>
다운로드 받은 파일을 Rufus 프로그램을 사용해서 USB에 설치합니다. <br>
![RUFUS-1](https://user-images.githubusercontent.com/63625609/80326713-a25fe980-8874-11ea-900b-44c7e3ed1a21.png)
* 장치 : os를 설치할 usb를 선택합니다. <br>
* 디스크 형식과 부팅 시스템 유형 : MBR파티션 형식의 BIOS 또는 UEFI(BIOS호환)을 선택합니다. <br>
 *MBR(MASTER BOOT RECORD) : 가장 보편화된 디스크 파티션 기술로 디스크의 첫번재 센터를 말한다. <br>
 *GPT(GUID PARTION TABLE) : MBR의 기술적 제한의 해결하기 위해 나온 디스크 파티션 기술을 말합니다. <br>
 *BIOS(BASIC INPUT/OUTPUT SYSTEM) : 메이보드에 내장된 펌웨어로 CUI 기반입니다. <br>
 *UEFI(UNIFIED EXTENSIBLE FIRMWARE INTERFACE) : BIOS의 발전형이며 GUI 기반의 펌웨어입니다. <br>
* 파일시스템 : FAT32(기본) 선택 합니다.
* 할당 단위 크기 : 4096 bytes(기본) 선택합니다.
* 새 볼륨 레이블 : USB 이름을 정합니다. 그냥 놔두면 알아서 됩니다.
* 빠른 포멧 : USB포멧 방식입니다. 체크합니다.
* 배드섹터 검사 : 이미지가 제대로 설치 되었는지 무결성을 검사합니다. 체크 해제합니다.
* 확장 레이블 및 아이콘 파일 만들기 : 필요시 체크합니다.

-----
3. Rufus 실행하기 <br>
USB에 설치할 `ISO 파일` 을 선택합니다. 시작을 클릭하면 ISO이미지를 USB에 설치하는 작업이 진행됩니다. 시스템 사양에 따라 시간이 다르지만 <br>
되도록이면 USB 3.0이상을 사용하는걸 추천 합니다. 설치 진행시 USB안의 파일들은 못쓰게 되니 비어있는 USB를 사용하거나 필요없는 파일이 있는 USB 사용을 권장합니다.

-----
4. esxi 설치하기 <br>
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
5. esxi web UI 접속 <br>
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
6. 데이터 스토어 `datastore` 설정 <br>
![esxi-datastore-1 (1)](https://user-images.githubusercontent.com/63625609/80327313-a260e900-8876-11ea-9c05-84ffdcf9f74b.png)
* Web UI에 접속후 왼쪽메뉴에서 `스토리지`를 선택합니다.
* 상단 메뉴중 `데이터스토어`를 선택합니다.
* 바로 아래 `새 데이터스토어`를 클릭합니다.
* 가운데 메세지 창이 뜨면 3개의 메뉴중 `새 VMFS데이터 스토어 생성`을 클릭합니다.
![esxi-datastore-2](https://user-images.githubusercontent.com/63625609/80327409-f7046400-8876-11ea-99c6-e28df839c893.png)
* 이름에 데이터 스토어 이름을 영문으로 적어줍니다 대소문자 구별 가능.
* 데이터 스토어로 사용할 HDD 및 SSD를 선택합니다.
