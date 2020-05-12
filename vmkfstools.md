## vmkfstools 명령 구문 

--------
`vmkfstools optins target` <br>
대상은 명령 옵션을 적용할 파티션, 디바이스 또는 경로를 지정합니다. <br>
`vmkfstools 명령인수`

-------
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

-------
## vmkfstools 명령 옵션
------
1. -v 하위 옵션 <br>
-v 하위 옵션은 명령 출력의 자세한 정도를 나타냅니다. `-v --verbose number` <br>
number 값은 1부터 10까지의 정수로 지정합니다. <br>
-v 하위 옵션은 다른 vmkfstools 옵션과 함께 지정할 수 있습니다. 옵션의 출력이 -v 하위 옵션과 함께 사용하기에 적합하지 않으면 vmkfstools에서는
-v 를 무시합니다.
모든 vmkfstools 명령줄에 -v하위 옵션을 포함할 수 있기 때문에 -v 는 옵션 설명에 하위 옵션으로 포함되지 않습니다.

------
2. 파일 시스템 옵션 <br>
- VMFS 데이터스토어의 특성 나열 <br>
VMFS 데이터스토어의 특성을 나열하려면 vmkfstools 명령을 사용합니다. <br>
`-P|--queryfs` <br>
       `-h|--humanreadable` <br>
VMFS 데이터스토어에 있는 파일 또는 디렉토리에 이 옵션을 사용하면 지정된 데이터스토어의 특성이 나열됩니다. 나열되는 특성에는 일반적으로 파일 시스템
레이블, 데이터스토어의 익스텐트 개수, UUID 및 각 익스텐트가 있는 디바이스의 목록이 포함됩니다. <br>
VMFS 파일 시스템을 지원하는 디바이스가 오프라인이 되면 그에 따라 익스텐트 개수 및 사용 가능한 공간이 변경됩니다. <br>
-p 옵션에 -h|--humanreadable 하위 옵션을 지정할 수 있습니다. 이렇게 하면 vmkfstools가 보다 읽기 쉬운 형식으로 볼륨의 용량을 나열합니다. <br>

-------------
- VMFS데이터 스토어 또는 스크래치 파티션 생성 <br>
vmkfstools 명령을 사용하여 VMFS 데이터스토어 또는 스크래치 파티션을 생성합니다. <br>
-C|--createfs [vmfs5|vmfs6|vfat] <br>
이 옵션은 disk_ID:P 와 같은 지정된 SCSI파티션에 VMFS 데이터스토어를 생성합니다. 이 파티션은 데이터스토어의 헤드 파티션이 됩니다. <br>
VMFS5 및 VMFS6의 경우 1MB블록 크기만 사용할 수 있습니다. <br>
-C옵션에 다음과 같은 하위 옵션을 지정할 수 있습니다. <br>
`-S|--setfsname` 생성하는 VMFS 데이터스토어의 볼륨 레이블을 정의합니다. 이 하위 옵션은 -C 옵션과 함께만 사용해야 합니다. 레이블은 128자까지 
지정할 수 있으며 선행 또는 후행 공백을 포함할 수 없습니다. <br>
vCenter Server에서는 모든 엔티티에 대해 80자 제한을 지원합니다. 데이터스토어 이름이 제한을 초과할 경우 이 데이터스토어를 vCenter Server를 추가할
 때 이름이 단축됩니다. <br>
볼륨 레이블을 정의한 후에는 vmkfstools 명령에 VMFS 데이터스토어를 지정할 때마다 이 레이블을 사용할 수 있습니다. 볼륨 레이블은 ls -l 명령으로 생성
되는 목록에 표시되며 `/vmfs/volumes` 디렉토리에 있는 VMFS 볼륨에 대한 심볼 링크로 표시됩니다. <br>
VMFS볼륨 레이블을 변경하려면 ln -sf 명령을 사용합니다. 아래 예시처럼  사용할 수 있습니다. <br>
`ln -sf /vmfs/volumes/UUID /vmfs/volumes/datastore` <br>
datastore는 UUID VMFS에 사용할 새 볼륨 레이블 입니다. <br>

-------
- VMFS 데이터스토어에 익스텐트 추가 <br>
VMFS 데이터스토어에 익스텐트를 추가하려면 vmkfstools 명령을 사용합니다. <br>
익스텐트를 추가하면 VMFS 데이터스토어가 헤드 파티션에서 span_partition으로 지정된 파티션으로 확장됩니다. <br>
`-Z|--spanfs span_partitionhead_partition` <br>
헤드 및 확장 파티션의 전체 경로 이름을 지정해야 합니다. (예시 : /vmfs/devices/disks/disk_ID:1) 이 옵션을 사용할 때마다 VMFS 데이터스토어에 
익스텐트가 추가되어 데이터스토어가 여러 파티션으로 확장됩니다. <br>
경고 : 이 옵션을 실행하면 span_partition 에 지정한 SCSI 디바이스에 있던 기존의 모든 데이터가 손실됩니다. <br>
VMFS 데이터스토어 확장 예제 <br>
이 예제에서는 VMFS 데이터스토어의 기존 헤드 파티션을 새 파티션까지 확장합니다. <br>
`~ vmkfstools -Z /vmfs/devices/disks/naa.disk_ID_2:1 /vmfs/devices/disks/naa.disk_ID_1:1` <br>
확장된 데이터스토어는 두개의 파티션 (naa.disk_ID_1:1 및 naa.disk_ID_2:1) 으로 확장됩니다. 이 예제에서 `naa.disk_ID_*:1` 은 헤드 파티션의 이름입니다. <br>

--------
- VMFS 데이터스토어 확장 <br>
VMFS 데이터스토어에 익스텐트를 추가하는 대신 기존 데이터스토어의 크기를 늘릴 수 있습니다. vmkfstools -G 명령을 사용합니다. <br>
기존 스토리지의 용량이 증가된 후 데이터스토어의 크기를 늘릴 수 있습니다. 이 명령은 다음 옵션을 사용합니다. <br>
`-G|--growfs devicedevice` <br>
이 옵션은 VMFS 데이터스토어 또는 해당 익스텐트를 확장합니다. 예를 들면 다음과 같습니다. <br>
`vmkfstools --growfs /vmfs/devices/disks/disk_ID:1 /vmfs/devices/disks/disk_ID:1` <br>
- VMFS 데이터스토어 업그레이드 <br>
VMFS 데이터스토어를 사용하는 경우 VMFS5로 업그레이드 해야합니다. <br>
데이터스토어를 업그레이드할 때는 다음 옵션을 사용합니다. <br>
`-T|--upgradevmfs /vmfs/volumes/UUID` <br>
업그레이드는 단방향 프로세스 입니다. VMFS3 데이터스토어를 VMFS5로 변환한 후에는 VMFS3으로 되돌릴 수 없습니다. 또한 데이터스토어를 액세스하는 모든 호스트가 VMFS5를 지원해야 합니다.

---------

