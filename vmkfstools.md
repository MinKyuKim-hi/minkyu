## vmkfstools 명령 구문 

--------
`vmkfstools optins target` <br>
대상은 명령 옵션을 적용할 파티션, 디바이스 또는 경로를 지정합니다. <br>
`vmkfstools 명령인수`

-------
옵션 : vmkfstools가 수행할 작업을 지정하기 위해 사용하는 하나 이상의 명령줄 옵션 및 연결된 인수입니다. 새 가상 디스크를 생성할 때 디스크 형식을
선택하는 경우를 예로 들수 있습니다. 옵션을 입력한 후 작업을 수행할 대상을 지정합니다. 대상은 파티션, 디바이스 또는 경로를 나타낼 수 있습니다.

-----
파티션 : 디스크 파티션을 지정합니다. 이 인수의 형식은 disk_ID:P이며, 여기서 disk_ID는 스토리지 어레이에서 반환한 디바이스 ID이고 P는 파티션의 번호
를 나타내는 정수입니다. 파티션 숫자는 0보다 커야 하며 유효한 VMFS 파티션에 해당해야 합니다.

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
*VMFS 파일 시스템 생성 예제* <br>
이 예제에서는 naa.<ID>:1 파티션에 my_vmfs라는 새 VMFS 데이터스토어를 만드는 방법을 보여주며 파일 블록 크기는 1MB입니다. <br>
`vmkfstools -C vmfs5 -b 1m -S my_vmfs /vmfs/devices/disks/naa.<ID>:1`

-------
- VMFS 데이터스토어에 익스텐트 추가 <br>
VMFS 데이터스토어에 익스텐트를 추가하려면 vmkfstools 명령을 사용합니다. <br>
익스텐트를 추가하면 VMFS 데이터스토어가 헤드 파티션에서 span_partition으로 지정된 파티션으로 확장됩니다. <br>
`-Z|--spanfs span_partitionhead_partition` <br>
헤드 및 확장 파티션의 전체 경로 이름을 지정해야 합니다. (예시 : /vmfs/devices/disks/disk_ID:1) 이 옵션을 사용할 때마다 VMFS 데이터스토어에 
익스텐트가 추가되어 데이터스토어가 여러 파티션으로 확장됩니다. <br>
경고 : 이 옵션을 실행하면 span_partition 에 지정한 SCSI 디바이스에 있던 기존의 모든 데이터가 손실됩니다. <br>
*VMFS 데이터스토어 확장 예제* <br>
이 예제에서는 VMFS 데이터스토어의 기존 헤드 파티션을 새 파티션까지 확장합니다. <br>
`~ vmkfstools -Z /vmfs/devices/disks/naa.<disk_ID_2>:1 /vmfs/devices/disks/naa.<disk_ID_1>:1` <br>
확장된 데이터스토어는 두개의 파티션 (naa.disk_ID_1:1 및 naa.disk_ID_2:1) 으로 확장됩니다. 이 예제에서 `naa.disk_ID_*:1` 은 헤드 파티션의 이름입니다. <br>

--------
- VMFS 데이터스토어 확장 <br>
VMFS 데이터스토어에 익스텐트를 추가하는 대신 기존 데이터스토어의 크기를 늘릴 수 있습니다. vmkfstools -G 명령을 사용합니다. <br>
기존 스토리지의 용량이 증가된 후 데이터스토어의 크기를 늘릴 수 있습니다. 이 명령은 다음 옵션을 사용합니다. <br>
`-G|--growfs devicedevice` <br>
*이 옵션은 VMFS 데이터스토어 또는 해당 익스텐트를 확장합니다. 예를 들면 다음과 같습니다.* <br>
`vmkfstools --growfs /vmfs/devices/disks/disk_ID:1 /vmfs/devices/disks/disk_ID:1` <br>

---------
- VMFS 데이터스토어 업그레이드 <br>
VMFS 데이터스토어를 사용하는 경우 VMFS5로 업그레이드 해야합니다. <br>
데이터스토어를 업그레이드할 때는 다음 옵션을 사용합니다. <br>
`-T|--upgradevmfs /vmfs/volumes/UUID` <br>
업그레이드는 단방향 프로세스 입니다. VMFS3 데이터스토어를 VMFS5로 변환한 후에는 VMFS3으로 되돌릴 수 없습니다. 또한 데이터스토어를 액세스하는 모든 호스트가 VMFS5를 지원해야 합니다.

---------
3. 가상 디스크 옵션 <br>
- 지원되는 디스크 형식 <br>
가상 디스크를 생성하거나 복제할 때 -d|--diskformat 하위 옵션을 사용하여 디스크 형식을 지정할 수 있습니다. <br>
다음 형식 중에서 선택합니다. <br>
`zeroedthick` (기본값) : 가상 디스크에 필요한 공간은 생성 시 할당됩니다. 물리적 디바이스에 남아 있는 모든 데이터는 생성시 지워지지 않지만, 가상 
시스템에서 처음 쓸 때 필요시 비워집니다. 가상 시스템은 디스크에서 오래된 데이터를 읽지 않습니다. <br>
`eagerzeroedthick` : 가상 디스크에 필요한 공간은 생성시 할당됩니다. zeroedthick 형식과 달리 물리적 디바이스에 남아 있는 데이터는 생성시 비워집니다. 
다른 유형의 디스크를 만드는 것보다 이 포맷의 디스크를 만드는 것이 더 오래 걸릴 수 있습니다. <br>
`thin` : 씬 프로비저닝된 가상 디스크입니다. thick 형식과 달리 가상디스크에 필요한 공간은 생성시 할당되지 않고, 필요 시 제공되고 비워집니다. <br>
`rdm` : device 가상호환성 모드 원시 디스크 매핑입니다. <br>
`rdmp` : device 물리적 호환성 모드(패스스루) 원시 디스크 매핑입니다. <br>
`2gbsparse` : 최대 익스텐트 크기가 2GB인 스파스 디스크입니다. VMware Fusion 같이 호스팅된 VMware제품에서 이 디스크 형식을 사용할 수 있습니다.
하지만 ESXI호스트에서 스파스 디스크의 전원을 켜려면 먼저 vmkfstools를 사용하여 디스크를 thick 또는 thin 같이 호환되는 형식으로 다시 가져와야 합니다.
`NFS 데이터스토어의 디스크 형식` <br>
NFS에서는 thin, thick, zeroedthick 및 2gbsparse 디스크 형식만 사용할 수 있습니다.
ESXI 호스트가 아니라 NFS서버가 할당 정책을 결정하므로 일반적으로 Thick,zeroedthick 및 thin 형식은 동일하게 작동합니다. 대부분의 NFS서버에서 
기본 할당 정책은 thin입니다. 그러나 Storage APIs - Array Integration을 지원하는 NFS 서버에서는 zeroedthick 형식으로 가상 디스크를 생성할 수 
있습니다. NFS서버는 공간 예약 작업을 통해 공간을 할당하고 확보할 수 있습니다.

-----
- 가상 디스크 생성 <br>
이 옵션은 데이터스토어의 지정한 경로에 가상 디스크를 생성합니다. 가상 디스크의 크기를 지정합니다. size에 값을 입력할 때 k(킬로바이트),m(메가바이트)
 또는 g(기가바이트)를 접미사로 추가하여 단위 유형을 나타낼 수 있습니다. 단위 유형은 대/소문자를 구분하지 않습니다. vmkfstools는 k 또는 K 모두 
 킬로바이트로 해석합니다. 단위 유형을 지정하지 않으면 vmkfstools는 바이트를 기본값으로 사용합니다. <br>
 `-c|--createvirtualdisk size[bB|sS|kK|mM|gG]` <br>
 `-d|--diskformat [thin|zeroedthick|eagerzeroedthick]` <br>
 `-w|--objecttype [file|vsan|vvol]` <br>
 `--policyFile fileName` <br>
 -c 옵션에 다음과 같은 하위 옵션을 지정할 수 있습니다. <br>
 -d|--diskformat 은 디스크 형식을 지정합니다. <br>
 -w|--objecttype 은 가상 디스크가 VMFS나 NFS 데이터스토어에 있는 파일인지 아니면 vSAN 또는 Virtual Volumes 데이터스토어에 있는 개체인지 지정합니다. <br>
 --policyFile fileName 은 디스크의 VM 스토리지 정책을 지정합니다. <br>
 *가상디스크 생성 예제* <br>
 이 예제에서는 disk.vmdk 라는 이름의 2GB 가상 디스크 파일을 생성하는 방법을 보여줍니다. 이름이 myVMFS인 VMFS 데이터스토어에 디스크를 생성합니다.
 디스크 파일은 가상 시스템에서 액세스할 수 있는 빈 가상 디스크를 나타냅니다. <br>
 `vmkfstools -c 2048m /vmfs/volumes/myVMFS/disk.vmdk` <br>
 
-----
 - 가상 디스크 초기화 <br>
 `-w|--writezeros` <br>
 이 옵션은 모든 데이터를 0으로 덮어써서 가상 디스크를 지웁니다. 가상 디스크의 크기와 가상 디스크를 호스팅하는 디바이스에 대한 I/O 대역폭에 따라
 서는 이 명령을 완료하는데 오래 걸릴 수 있습니다. <br>
 *경고 : 이 명령을 사용하면 가상 디스크의 모든 기존 데이터가 손실됩니다.* <br>

-----
- 씬 가상 디스크 확장 <br>
`-j|--inflatedisk` <br>
이 옵션은 기존 데이터를 모두 보존하면서 thin 가상 디스크를 eagerzeroedthick 으로 변환하고, 아직 할당되지 않은 모든 블록을 할당하고 비웁니다.

-----
- zeroedthick 가상 디스크를 eagerzeroedthick 디스크로 변환 <br>
`-k|--eagerzero` <br>
이 옵션을 사용하면 변환을 수행하는 동안 가상 디스크의 모든 데이터가 보존됩니다. 아래의 예제를 참고 <br>
`vmkfstools --eagerzero /vmfs/volumes/myVMFS/VMName/disk.vmdk` <br>

-------
- 비워진 블록 제거 <br>
`-K|--punchzero` <br>
이 옵션은 비워진 모든 블록을 할당 취소하고 이전에 할당된 블록 중에서 유효한 데이터가 포함된 블록만 남겨 둡니다. 그 결과 가상 디스크는 씬 형식입니다. <br>

-----
- 가상 디스크 삭제 <br>
VMFS 볼륨의 지정된 경로에 있는 가상 디스크 파일을 삭제하려면 vmkfstools 명령을 사용합니다.
`-U|--deletevirtualdisk` <br>

-----
- 가상 디스크 이름 변경 <br>
`-E|--renamevirtualdisk oldNamenewName` <br>
원래 파일 이름 또는 파일 경로 oldName 과 새 파일 이름 또는 파일 경로 newName 을 지정해야 합니다. <br>

-----
- 가상 디스크나 RDM 복제 또는 변환 <br>
루트 사용자가 아니면 가상 디스크나 RDM을 복제할 수 없습니다. 원래 파일 이름 또는 파일 경로 oldName과 새 파일 이름 또는 파일경로 newName을 지정해야 합니다. <br>
`-i|--clonevirtualdisk oldNamenewName` <br>
`-d|--diskformat [thin|zeroedthick|eagerzeroedthick|rdm:device|2gbsparse]` <br>
`-w|--objecttype [file|vsan|vvol]` <br>
`--policyFile fileName` <br>
`-N|--avoidnativeclone` <br>
생성하는 복사본의 매개 변수를 변경하려면 다음 하위 옵션을 사용합니다. <br>
-d|--diskformat 은 디스크 형식을 지정합니다. <br>
-w|--objecttype 은 가상 디스크가 VMFS나 NFS 데이터스토어에 있는 파일인지 ㅇ ㅏ니면 vsan또는 Virtual Volumes 데이터스토어에 있는 개체인지 지정합니다. <br>
--policyFile fileName 은 디스크의 VM 스토리지 정책을 지정합니다. <br>
기본적으로 ESXI는 네이티브 매서드를 사용하여 복제 작업을 수행합니다. 어레이에서 복제 기술을 지원하는 경우에는 작업을 어레이에 오프로드할 수 있습니다. ESXI 네이티브 복제를 방지하려면 -N|--avoidnativeclone 옵션을 지정합니다. <br>
아래의 예제는 templates 저장소의 마스터 가상 디스크 컨텐츠를 myVMFS파일 시스템에 있는 myOS.vmdk 라는 가상 디스크 파일로 복제하는 방법을 보여줍니다. <br>
`vmkfstools -i /vmfs/volumes/myVMFS/templates/gold-master.vmdk /vmfs/volumes/myVMFS/myOS.vmdk` <br>
다음 예제와 같이 가상 시스템 구성 파일에 줄을 추가하여 이 가상 디스크를 사용하도록 가상 시스템을 구성할 수 있습니다. <br>
`scsi0:0.present = TRUE <br>
scsi0:0.fileName = /vmfs/volumes/myVMFS/myOS.vmdk` <br>
디스크 형식을 변환하려면 -d|--diskformat 하위 옵션을 사용합니다. 이 하위 옵션은 ESXI와 호환되지 않는 형식(예:2gbsparse 형식)으로 가상 디스크를 
가져오는 경우에 유용합니다. 디스크를 변환한 후에는 ESXI에 생성한 새 가상 시스템에 이 디스크를 연결할 수 있습니다. <br>
`vmkfstools -i /vmfs/volumes/myVMFS/templates/gold-master.vmdk /vmfs/volumes/myVMFS/myOS.vmdk -d thin` <br>

-----
- 가상 디스크 확장 <br>
가상 시스템을 생성한 후에는 vmkfstools 명령을 사용하여 가상 시스템에 할당된 디스크의 크기를 확장할 수 있습니다. <br>
`-X|--extendvirtualdisk newSize[bBsSkKmMgGtT]` <br>
newSize 매개 변수를 지정하고 적절한 단위 접미사를 추가합니다. 단위 유형은 대/소문자를 구분하지 않습니다. vmkfstools 는 k 또는 K 모두 킬로바이트로
해석합니다. 단위 유형을 지정하지 않으면 vmkfstools는 킬로바이트를 기본값으로 사용합니다. <br>
newSize 매개 변수는 디스크에 추가할 추가분만이 아니라 새 크기 전체를 정의합니다. <br> 
예를 들어 4g 가상 디스크를 1g 더 확장하려면 vmkfstools -X 5g disk name 을 입력합니다. <br>
-d eagerzeroedthick 옵션을 사용하여 가상 디스크를 eagerzeroedthick 형식으로 확장할 수 있습니다. <br>
-X 옵션을 사용할 때 다음 사항을 고려해야 합니다. <br>
스냅샷이 연관되어 있는 가상 시스템의 기본 디스크는 확장하면 안됩니다. 확장할 경우 더이상 스냅샷을 커밋하거나 기본 디스크를 원래 크기로 되돌릴 수 없습니다. <br>
디스크를 확장한 후에는 디스크의 파일 시스템을 업데이트해야 할 수 있습니다. 따라서 게스트 운영 체제가 디스크의 새 크기를 인식하고 사용할 수 있습니다. <br>

-----
- 가상 디스크 업그레이드 <br>
이 옵션은 지정된 가상 디스크 파일을 ESX Server 2 형식에서 ESXI 형식으로 변환합니다. <br>
LEGACYSPARSE, LEGACYPLAIN, LEGACYVMFS, LEGACYVMFS_SPARSE 및 LEGACYVMFS_RDM 유형의 가상 디스크를 변환하려면 이 옵션을 사용합니다. <br>
`-M|--migratevirtualdisk` <br>

-----
- 가상 호환성 모드 원시 디바이스 매핑 생성
VMFS 볼륨에 RDM(원시 디바이스 매핑) 파일을 생성하고 이 파일에 원시 LUN을 매핑하려면 vmkfstools 명령을 사용합니다. 이 매핑을 설정한 후에는 일반
VMFS 가상 디스크에 액세스 하는 것처럼 LUN에 액세스할 수 있습니다. 매핑의 파일 길이는 해당 매핑이 가리키는 원시 LUN 의 크기와 같습니다. <br>
`-r|--createrdm device` <br>
device 매개 변수를 지정할 때는 다음 형식을 사용합니다. <br>
`/vmfs/devices/disks/disk_ID:P` <br>
*RDM 생성 예제* <br>
이 예제에서는 my_rdm.vmdk 라는 RDM을 생성하고 해당 파일에 disk_ID 원시 디스크를 매핑합니다. <br>
`vmkfstools -r /vmfs/devices/disks/disk_ID my_rdm.vmdk` <br>
가상 시스템 구성 파일에 다음 줄을 추가하여 my_rdm.vmdk 매핑 파일을 사용하도록 가상 시스템을 구성할 수 있습니다. <br>
`scsi0:0.present = TRUE <br>
scsi0:0.fileName = /vmfs/volumes/myVMFS/my_rdm.vmdk` <br>

-----
- 물리적 호환성 모드 원시 디바이스 매핑 생성 <br>
패스스루 원시 디바이스를 VMFS 볼륨에 있는 파일에 매핑하려면 vmkfstools 명령을 사용합니다. 이 매핑을 사용하면 가상 시스템이 해당 가상 디스크에 액세
스할 때 ESXI SCSI 명령 필터링을 생략할 수 있습니다. 이 매핑 유형은 SAN 인식 소프트웨어가 가상 시스템에서 실행되는 경우와 같이, 가상 시스템이 독점
SCSI 명령을 보내야 하는 경우에 유용합니다. <br>
`-z|--createrdmpassthru deviceexample.vmdk` <br>
이와 같은 매핑 유형을 설정한 후에는 다른 VMFS 가상 디스크를 액세스하는 것처럼 이 매핑을 사용하여 원시 디스크를 액세스할 수 있습니다. device 경로
를 지정할 때는 다음 형식을 사용합니다. <br>
`/vmfs/devices/disks/device_ID` <br>
.vmdk 이름에는 다음 형식을 사용합니다. 명령을 사용하기 전에 데이터스토어를 생성해야 합니다.
`/vmfs/volumes/datastore_name/example.vmdk` <br>
*예를 들면 아래와 같습니다.* <br>
`vmkfstools -z /vmfs/devices/disks/naa.600a0000... /vmfs/volumes/datastore1/mydisk.vmdk`

-----
- RDM 의 특성 나열 <br>
이러한 특성은 RDM 파일이 매핑되는 스토리지 디바이스를 식별하는 데 도움을 줍니다. <br>
`-q|--queryrdm my_rdm.vmdk` <br>
이 옵션은 원시 디스크 RDM의 이름을 인쇄합니다. 또한 디스크 ID와 같이 원시 디스크에 대한 다른 식별 정보도 인쇄합니다. <br>
*RDM 특성 나열 예제* <br>
`# vmkfstools -q /vmfs/volumes/VMFS/my_vm/my_rdm.vmdk` <br>
`Disk /vmfs/volumes/VMFS/my_vm/my_rdm.vmdk is a Passthrough Raw Device Mapping` <br>
`maps to : vml.0200000005464503453450000003453405435345 ` <br>

-----
- 가상 디스크 기하 도형 표시 <br>
`-g|--geometry` <br>
출력은 Geometry information C/H/S 형식이며, 여기서 C,H 및 S 는 각각 실린더 수, 헤드 수 및 섹터 수 를 나타냅니다. <br>
*참고 : 호스팅된 VMware 제품의 가상 디스크를 ESXI호스트로 가져오면 디스크 기하 도형 불일치 오류 메세지가 표시될 수 있습니다. 디스크 기하 도형 불일
치로 인해 게스트 운영체제를 로드하거나 새로 생성한 가상 시스템을 실행하는 데돋 문제가 발생할 수 있습니다.* <br>

-----
- 가상 디스크 검사 및 복구 <br>
`-x|--fix [check|repair]` <br>
예를 들면 다음과 같습니다. <br>
`vmkfstools -x check /vmfs/volumes/my_datastore/my_disk.vmdk` <br>

-----
- 디스크 체인에서 일관성 검사 <br>
전체 스냅샷 체인을 검사하려면 vmkfstools 명령을 사용합니다. 체인에 손상된 링크가 있는지 또는 잘못된 상위-하위관계가 있는지 확인할 수 있습니다. 
`-e|--chainConsistent` <br>

-----
4. 스토리지 디바이스 옵션 <br>
- LUN의 SCSI 예약관리
다른 호스트가 LUN에 액세스할 수 있도록 예약을 해제하고, 예약을 재설정하여 대상에서 모든 예약을 강제로 해제할 수 있습니다. <br>
`-L|--lock [reserve|release|lunreset|targetreset|busreset|readkeys|readresv] device` <br>
*경고 : -L 옵션을 사용하면 SAN에 있는 다른 서버의 작업이 중단될 수 있습니다. -L 옵션은 클러스터링 설정 문제를 해결할 때만 사용해야 합니다. <br>
VMware에서 권고한 경우가 아니라면 VMFS 볼륨을 호스팅하는 LUN에서 이 옵션을 사용하면 안됩니다.* <br>
-L 옵션은 여러가지 방법으로 지정할 수 있습니다. <br> 
`-L reserve` 지정된 LUN을 예약합니다. 예약한 후에는 해당 LUN을 예약한 서버만 LUN 에 액세스할 수 있습니다. 다른 서버가 해당 LUN 을 액세스하려고 
하면 예약 오류가 발생합니다. <br>
`-L release` 지정된 LUN의 예약을 해제합니다. 다른 서버가 LUN에 다시 액세스할 수 있습니다. <br>
`-L lunreset` 지정된 LUN에 대한 모든 예약을 지우고 모든 서버가 다시 LUN을 사용할 수 있도록 하여 지정된 LUN을 재설정합니다. 재설정은 디바이스의
다른 LUN에 영향을 주지 않습니다. 디바이스에 있는 다른 LUN이 예약되어 있는 경우 해당 예약은 유지됩니다. <br>
`-L targetreset` 전체 대상을 재설정합니다. 재설정은 해당 대상과 연결된 모든 LUN에 대한 예약을 지우고 모든 서버가 다시 LUN을 사용할 수 있도록 
만듭니다. <br>
`-L busreset` 버스에서 액세스 가능한 모든 대상을 재설정합니다. 재설정은 버스를 통해 액세스할 수 있는 모든 LUN에서 모든 예약을 지우고 모든 서버가
다시 LUN을 사용할 수 있도록 만듭니다. <br>
`-L readkeys` LUN에 등록된 예약 키를 읽습니다. SCSI-III 영구 그룹 예약 기능에 적용됩니다. <br>
`-L readresv` LUN에서 예약 상태를 읽습니다. SCSI-III 영구 그룹 예약 기능에 적용됩니다. <br>
device 매개 변수는 다음 형식에 따라 입력합니다. <br>
`/vmfs/devices/disks/disk_ID:P`

-----
- 디바이스 잠금 해제 <br>
특정 파티션에서 디바이스 잠금을 해제하려면 vmkfstools 명령을 사용합니다. <br>
`-B|--breaklock device` <br>
device 매개 변수는 다음 형식에 따라 입력합니다. <br>
`/vmfs/devices/disks/disk_ID:P` <br>
*이 명령은 데이터스토어를 확장, 익스텐트 추가 또는 재서명과 같은 데이터스토어 작업을 수행하는 중에 호스트에서 장애가 발생했을 때 사용할 수 있습니다. 
이 명령을 실행할 때는 잠금을 사용하는 다른 호스트가 없어야 합니다.* 
