## vmkfstools 명령 구문

`vmkfstools optins target` <br>
대상은 명령 옵션을 적용할 파티션, 디바이스 또는 경로를 지정합니다. <br>
`vmkfstools 명령인수`
------------------------
옵션 : vmkfstools가 수행할 작업을 지정하기 위해 사용하는 하나 이상의 명령줄 옵션 및 연결된 인수입니다. 새 가상 디스크를 생성할 때 디스크 형식을
선택하는 경우를 예로 들수 있습니다. 옵션을 입력한 후 작업을 수행할 대상을 지정합니다. 대상은 파티션, 디바이스 또는 경로를 나타낼 수 있습니다.

-----
파티션 : 디스크 파티션을 지정합니다. 이 인수의 형식은 disk_ID:P이며, 여기서 disk_ID는 스토리지 어레이에서 반환한 디바이스 ID이고 P는 파티션의 번호를
나타내는 정수입니다. 파티션 숫자는 0보다 커야 하며 유효한 VMFS 파티션에 해당해야 합니다.

-----
디바이스 : 디바이스 또는 논리적 볼륨을 지정합니다. 이 인수는 ESXI 디바이스 파일 시스템의 경로 이름을 사용합니다. 경로 이름은 디바이스 파일 시스템의 
마운트 지점인 `/vmfs/device` 로 시작합니다. <br>
다른 유형의 디바이스를 지정할 때는 다음 형식을 사용합니다. <br>
 - 로컬 또는 SAN 기반 디스크 : `/vmfs/devices/disks`
 - ESXI 논리적 볼륨 : `/vmfs/devices/lvm`
 - 일반 SCSI 디바이스 : `/vmfs/devices/generic`

-----
경로 : VMFS파일 시스템 또는 파일을 지정합니다. 이 인수는 디렉토리 심볼 링크, 원시 디바이스 매핑 또는 `/vmfs`의 파일을 명명하는 절대경로 또는 
상대 경로 입니다. <br>
 - VMFS파일 시스템을 지정하려면 다음 형식을 사용합니다. <br>
`/vmfs/volumes/file_system_UUID` 또는 `/vmfs/volumes/file_system_label`
 - VMFS 데이터스토어에 있는 파일을 지정하려면 다음 형식을 사용합니다. <br>
 `/vmfs/volumes/file_system_label|file_system_UUID/[dir]/myDisk.vmdk` <br>
 현재 작업 디렉토리가 myDisk.vmdk의 상위 디렉토리인 경우에는 전체 경로를 입력하지 않아야 합니다.
