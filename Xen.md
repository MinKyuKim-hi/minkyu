**1. XenServer 설치** <br>
- 부팅 화면 <br>
- Enter키를 눌러 설치를 진행합니다
![XenServer1](https://user-images.githubusercontent.com/63625609/80553884-5e045300-8a06-11ea-9865-e9abc4e53658.png)
- keymap은 us로 선택합니다.
![XenServer2](https://user-images.githubusercontent.com/63625609/80553934-96a42c80-8a06-11ea-8701-e0cc274245cd.png)
- Enter키를 눌러 진행합니다.
![XenServer3](https://user-images.githubusercontent.com/63625609/80554017-cb17e880-8a06-11ea-84d6-5854fcee8be6.png)
- 라이선스 동의 화면 입니다. Enter를 눌러 동의하고 진행합니다.
![XenServer4](https://user-images.githubusercontent.com/63625609/80554064-ee429800-8a06-11ea-92d5-6a833480d9bc.png)
- 현재 하드웨어로 XenServer설치 이후 사용에 문제가 있을수 있다는 메세지 입니다.
![XenServer5](https://user-images.githubusercontent.com/63625609/80554150-277b0800-8a07-11ea-82e0-6dbbb91511f6.png)
- XenDesktop을 사용하시는분들은 아래 provisioning을 사용하려면 체크합니다.
![XenServer6](https://user-images.githubusercontent.com/63625609/80554223-68731c80-8a07-11ea-9f8e-d7c53b4b782f.png)
- 로컬미디어 선택후 넘어갑니다.
![XenServer7](https://user-images.githubusercontent.com/63625609/80554292-9d7f6f00-8a07-11ea-97b7-fcb5774adad1.png)
- Supplemental Packs(보조팩) 설치여부 선택입니다.
![XenServer8](https://user-images.githubusercontent.com/63625609/80554323-bee05b00-8a07-11ea-9530-bff1551b2683.png)
- 설치 원본 소스를 확인하는 작업의 진행여부입니다. 필요없으면 Skip verification 선택후 진행합니다.
![XenServer9](https://user-images.githubusercontent.com/63625609/80554382-e800eb80-8a07-11ea-8be6-1c653016e4bb.png)
- XenServer에 사용할 비밀번호 설정화면 입니다.
![XenServer10](https://user-images.githubusercontent.com/63625609/80554427-154d9980-8a08-11ea-8681-e3821302972b.png)
- 네트워크 설정 부분입니다. 고정 ip를 사용하시려면 직접 설정해주어야 하고 자동ip를 사용하려면 DHCP선택후 넘어갑니다.
![XenServer11](https://user-images.githubusercontent.com/63625609/80554462-3910df80-8a08-11ea-9a67-c54cdf014840.png)
- DNS설정 부분입니다. 적절하게 작성하면 됩니다.
![XenServer12](https://user-images.githubusercontent.com/63625609/80554515-6cec0500-8a08-11ea-96dd-769c2efab6a2.png)
- 타임 존 설정입니다. Asia,Seoul선택후 넘어갑니다.
![XenServer13](https://user-images.githubusercontent.com/63625609/80554561-8c832d80-8a08-11ea-958d-7567937704dd.png)
![XenServer14](https://user-images.githubusercontent.com/63625609/80554609-b3d9fa80-8a08-11ea-954b-7b4f77ad2e67.png)
- 시스템 시간 설정입니다.
![XenServer15](https://user-images.githubusercontent.com/63625609/80554652-d0763280-8a08-11ea-81b5-b3e79bd6bfde.png)
- 설정이 끝났으면 설치를 진행합니다.
![XenServer17](https://user-images.githubusercontent.com/63625609/80554706-f7346900-8a08-11ea-82ba-d755455b9e14.png)
- 기다리면 설치가 진행됩니다.
![XenServer18](https://user-images.githubusercontent.com/63625609/80554744-13d0a100-8a09-11ea-80bc-21a25a7bfb77.png)
- 리부팅 하면 설치 완료
![XenServer20](https://user-images.githubusercontent.com/63625609/80554775-28ad3480-8a09-11ea-9815-bd1d133b9db7.png)
- 설치 완료화면 입니다. IP,DNS 등등 설정을 변경 및 확인할 수 있습니다.
![XenServer22](https://user-images.githubusercontent.com/63625609/80554818-4aa6b700-8a09-11ea-8a88-3f633154e748.png)

------------
2. XenCenter <br>
- Add New Server를 눌러 ip주소,id,비밀번호 등을 입력하고 XenServer를 추가합니다.
![XenCenter](https://user-images.githubusercontent.com/63625609/80555030-f9e38e00-8a09-11ea-958b-10d676ae05c6.png)
![주석 2020-04-29 114019](https://user-images.githubusercontent.com/63625609/80556348-429d4600-8a0e-11ea-892f-d41a473b4f44.png)
- XenServer가 XenCenter 서버목록에 추가되었습니다.
![XenCenter3](https://user-images.githubusercontent.com/63625609/80555066-1da6d400-8a0a-11ea-82bd-b89049fe3150.png)
- SSH로 XenServer에 접속하고 /dev/mapper 라고 써있는 부분의 뒤에 /run/sr-mount~~ 경로를 복사해서 mkdir로 iso_storage를 만들어 줍니다.
![주석 2020-04-29 111707](https://user-images.githubusercontent.com/63625609/80555366-0caa9280-8a0b-11ea-9801-52e835dabe0c.png)
- FileZilla Client 프로그램을 사용해서 iso_storage에 이미지 파일 iso 업로드
![주석 2020-04-29 112125](https://user-images.githubusercontent.com/63625609/80555570-99555080-8a0b-11ea-941a-a43145b1d903.png)
- XenCenter에서 iso_storage 에 이미지 파일이 추가 된것을 확인할 수 있다.
![주석 2020-04-29 112314](https://user-images.githubusercontent.com/63625609/80555647-dd485580-8a0b-11ea-98a9-2c73d0a44ef5.png)
- 화면의 New VM 클릭후 설치할 VM의 OS 선택.
![주석 2020-04-29 112519](https://user-images.githubusercontent.com/63625609/80555750-239db480-8a0c-11ea-8e94-4c166370aea8.png)
- 설치할 VM의 이름 설정화면입니다.
![주석 2020-04-29 112659](https://user-images.githubusercontent.com/63625609/80555821-5e9fe800-8a0c-11ea-8eba-62486b1143f1.png)
- 설치할 OS의 DVD drive. iso이미지 파일 선택.
![주석 2020-04-29 112816](https://user-images.githubusercontent.com/63625609/80555874-90b14a00-8a0c-11ea-8859-ca9ce223c825.png)
- 설치할 서버를 확인합니다.
![주석 2020-04-29 113006](https://user-images.githubusercontent.com/63625609/80555925-c9e9ba00-8a0c-11ea-8823-7cfca8d18816.png)
- 설치할 VM의 CPU,Memory등을 설정합니다.
![주석 2020-04-29 113055](https://user-images.githubusercontent.com/63625609/80555965-edad0000-8a0c-11ea-9ad5-481d46782ec7.png)
- storage 확인 화면입니다.
![주석 2020-04-29 113206](https://user-images.githubusercontent.com/63625609/80556003-159c6380-8a0d-11ea-9095-a5b09a72ba16.png)
- Networking 설정 화면 입니다.
![주석 2020-04-29 113256](https://user-images.githubusercontent.com/63625609/80556089-614f0d00-8a0d-11ea-99a1-a79686e6877d.png)
- VM설치 최종확인. Create Now버튼을 눌러 VM생성. Start the new VM automatically 체크박스는 설치후 자동실행 여부를 묻는것 입니다.
![주석 2020-04-29 113506](https://user-images.githubusercontent.com/63625609/80556151-a410e500-8a0d-11ea-878a-859c2defb408.png)
- VM 생성후 실행, 설치완료된 Windows 화면 입니다.
![주석 2020-04-29 113829](https://user-images.githubusercontent.com/63625609/80556253-f9e58d00-8a0d-11ea-800a-d3b5251d8194.png)
