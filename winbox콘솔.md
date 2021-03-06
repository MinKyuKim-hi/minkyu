## console
콘솔은 텍스트 터미널을 사용하거나 winbox내에서 원격으로 직렬 포트, 텔넷, SSH 또는 콘솔 화면을 사용하거나 모니터 및 키보드를 사용하여 Mikrotik 라우터
의 구성 및 관리 기능에 액세스 하는데 사용됩니다. 콘솔은 스크립트 작성에도 사용됩니다. 콘솔의 작동 원리에 대해 알아보겠습니다. <br>
**계층** <br>
콘솔에서는 텍스트 명령을 사용하여 라우터 설정을 구성할 수 있습니다. 사용 가능한 명령이 많으므로 계층적 메뉴 레벨 방식으로 구성된 그룹으로 분할됩니다.
메뉴 레벨의 이름은 관련 섹션에서 액세스 할 수 있는 구성 정보를 반영합니다. <br>
*예시* `/ip route print`명령을 실행할 수 있습니다. <br>
각 명령 앞에 `ip route path` 를 입력하는 대신 메뉴 계층의 특정 분기로 이동하기 위해 경로를 한번만 입력할 수 있습니다. 따라서 위의 예제는 다음과 같
이 실행 할수도 있습니다. <br>
`ip route> print` <br>
현재 메뉴 계층 구조의 위치를 반영하기 위해 프롬프트가 변경됩니다. 최상위 레벨로 다시 이동하려면 '/'를 입력합니다. <br>
`ip route` <br>
`ip route> /` 입력시 /로 다시 변경됩니다. <br> 
한 명령 레벨 위로 이동하려면 '..'을 입력합니다. <br>
`ip route> ..` <br>
`ip>` <br>
/ 및 .. 을 사용하여 현재 레벨을 변경하지 않고 다른 메뉴 레벨에서 명령을 실행 할 수 있습니다. <br>
*예시* <br>
`ip route> / ping 10.0.0.1` <br>
`ip firewall nat> .. service-port print` <br>

-----
**품목 이름과 번호** <br>
많은 명령 레벨은 인터페이스, 경로, 사용자 등의 항목 배열로 작동합니다. 이러한 배열은 비슷한 목록으로 표시됩니다. 목록의 모든 항목에는 항목 번호와 매개
변수 값이 있습니다. 항목의 속성을 변경하려면 `set` 명령을 사용하고 항목의 이름 또는 번호를 지정해야 합니다. <br>
- 품목 이름 <br>
일부 목록에는 특정 이름이 지정된 항목이 있습니다. 인터페이스 또는 사용자 수준이 그 예 입니다. 거기에서 품목 번호 대신 품목 이름을 사용할 수 있습니
다. 번호와 달리 이름으로 항목에 액세스하기 전에 print 명령을 사용할 필요는 없습니다. 번호와 달리 콘솔에서 내부적으로 지정되지 않지만 항목의 특성입
니다. 따라서 그들은 스스로 변하지 않을 것입니다. 그러나 여러 사용자가 동시에 라우터 구성을 변경하는 경우 가능한 모든 종류의 모호한 상황이 있습니다.
일반적으로 항목 이름은 숫자보다 안정적이며 더 유익하기 때문에 콘솔 스크립트를 작성할 때 숫자보다 선호합니다. <br>
- 품목 번호 <br>
품목 번호는 print 명령에 의해 지정되며 일정하지 않습니다. 두개의 연속 print 명령이 항목을 다르게 주문할 수 있습니다. 그러나 마지막 print 명령의 결
과 가 기억되므로 일단 할당 되면 add, remove 및 move 작업 후에도 항목 번호를 사용할 수 있습니다.(버전 3부터 move 작업이 항목 번호를 지정하지 않
음.) 항목번호는 세션 별로 할당되며 콘솔을 종료하거나 다음 print 명령이 실행될 때까지 동일하게 유지됩니다. 또한 모든 항목 목록에 대해 번호가 별도로 
지정되므로 ip address print는 인터페이스 목록의 번호를 변경하지 않습니다. <br>
버전 3부터는 print 명령을 실행하지 않고도 항목 번호를 사용할 수 있습니다. print명령이 실행된 것처럼 번호가 할당됩니다. <br>
여러 명령을 대상으로 여러 항목을 지정할 수 있습니다. 항목 수를 쓸 수 있는 거의 모든 곳에서 숫자 목록을 작성할 수도 있습니다. <br>
*예시* <br>
`interface print` <br>
`interface set 0, 1, 2 mtu+1460` <br>

-----
**빠른 타이핑(Quick Typing)**
콘솔에는 명령을 훨씬 빠르고 쉽게 입력할 수 있는 두가지 기능, 즉 [Tab]키 완성과 명령 이름 약어가 있습니다. 완료는 UNIX의 bash 쉘과 유사하게 작동합
니다. 단어의 일부 다음에 [Tab] 키를 누르면 콘솔은 이 단어로 시작하는 현재 컨텍스트 내에서 명령을 찾습니다. 일치하는 항목이 하나만 있으면 자동으로 
추가되고 그 뒤에 공백이 옵니다. `/inte[Tab]_는 /interface_` 가 됩니다. <br>
일치하는 항목이 두개 이상 있지만 모두 공통 시작부분이 있는데 입력한 것보다 길면 단어가 이 공통부분에 완성되고 공백이 추가되지 않습니다. <br>
`/interface set e[Tab]_ becomes /interface set ether_` <br>
공통 부분만 입력한 경우 tab키를 한번 눌러도 아무런 효과가 없습니다. 그러나 두번째로 누르면 가능한 모든 완료가 가능한 단어가 표시됩니다. <br>
`interface set e[Tab]_` <br>
`interface set ether[Tab]_` <br>
`interface set ether[Tab]_` <br>
`ether1 ether2 ether3` <br>
`interface set ether_` <br>
[Tab] 명령 이름, 인수 이름, 방화벽 프로토콜의 일부 목록에 있는 항목의 이름이나 이름처럼( 단지 몇가지 가능한 값이 인수 - 콘솔이 가능한 값에 대한 단
서가 있을 경우 키를 어떤 맥락에서 거의 사용할 수 있습니다. 그리고 NAT 규칙) 숫자, ip주소 및 유사한 값을 완성할 수 없습니다. <br>
입력하는 동안 더 적은 키를 누르는 또 다른 방법은 명령 및 인수 이름을 축약하는 것입니다. 명령 이름의 시작 부분만 입력할 수 있으며, 모호하지 않은 경
우 콘솔은 해당 이름을 전체 이름으로 허용합니다. <br>
`pi 10.1 c 3 si 100` = `ping 10.0.0.1 count 3 size 100` <br>
이름의 시작 부분 뿐만 아니라 고유한 부분 문자열도 완성할 수 있습니다. 정확히 일치하는 것이 없으면 콘솔은 문자열이 여러 단어 이름의 첫 문자로 완성되
거나 단순히 단어의 문자를 포함하는 단어를 찾기 시작합니다. 이 문자열은 같은 순서로 이러한 단어가 있으면 커서 위치에서 완료됩니다.
*예시* <br>
`interface x[Tab]_` <br>
`interface export_` <br>
`interface mt[Tab]_` <br>
`interface monitor-traffic_` <br>

-----
**일반 명령(General Commands)**
print, set, remove, add, find, get, export, enable, disable, comment, move 등 거의 모든 메뉴 수준에 공통적인 명령이 있습니다. 이러한 명령은 
다른 메뉴 수준에서 비슷한 동작을 합니다. <br>
- add : 이 명령은 일반적으로 항목 번호 인수를 제외하고 set과 동일한 인수를 갖습니다. 일반적으로 항목 순서와 관련이 있는 곳에 일반적으로 항목 목록
의 끝에 지정한 값으로 새 항목을 추가합니다. 새 주소에 대한 인터페이스와 같이 제공해야하는 일부 필수 속성이 있지만 명시적으로 지정하지 않으면 다른 
속성이 기본값으로 설정됩니다. <br>
- 공통 파라미터
- copy-from : 기존 항목을 복사합니다. 다른 항목에서 새 항목 속성의 기본값을 사용합니다. 정확한 복사를 원하지 않으면 일부 속성에 새 값을 지정할 수 
있습니다. 이름이 있는 항목을 복사할 때는 일반적으로 사본에 새 이름을 지정해야 합니다. <br>
- place-before : 위치가 지정된 기존 항목 앞에 새 항목을 배치합니다. 따라서 목록에 항목을 추가한후 이동명령을 사용할 필요가 없습니다.
- disabled : 새로 추가된 항목의 비활성화 / 활성화 상태를 제어합니다
- comment : 새로 작성된 항목에 대한 설명을 보유합니다.
- return value
- add 명령은 추가한 항목의 내부 번호를 반환합니다.
- edit : 이 명령은 set 명령과 관련 있습니다. 스크립트와 같이 많은 양의 텍스트가 포함된 속성 값을 편집하는데 사용할 수 있지만 편집 가능한 모든 속성
에서 작동합니다. 터미널의 기능에 따라 지정된 속성 값을 편집하기 위해 전체 화면 편집기 또는 한 줄 편 편집기가 시작됩니다.
- find : 이 명령은 set과 동일한 인수와 함께 각 플래그의 값에 따라 yes 또는 no 값을 갖는 disabled 또는 active 와 같은 플래그 인수가 있습니다. 모
든 플래그와 해당 이름을 보려면 print 명령 출력의 상단을 봐야합니다. find 명령은 지정된 인수와 동일한 값을 갖는 모든 항목의 내부 번호를 반환합니다.
- move : 목록의 항목 순서를 변경합니다.
매개 변수(parameters) <br>
- 첫번째 인수는 이동할 항목 (-s)을 지정합니다.
- 두번째 인수는 이동 될 모든 항목을 배치할 항목을 지정합니다.(두번째 인수가 생략된 경우 목록의 끝에 배치됨)
- print : 특정 명령 레벨에서 액세스 할 수있는 모든 정보를 표시합니다. 따라서 /system clock print 는 시스템 날짜 및 시간을 표시하고, /ip route 
print 는 모든 경로 등을 표시합니다. 현재 레벨의 항목 목록이 있고 읽기 전용이 아닌 경우, 즉 변경 / 제거 할 수있는 경우 (예 : 읽기-항목 목록 만 
/system history 이며 실행된 작업의 기록을 보여줍니다.) print 명령은 이 목록의 항목과 함께 작동하는 모든 명령에 사용되는 번호도 지정합니다. <br>
- 공통 파라미터
- from : 그들 만이 제공하는 동일한 순서로 항목을 지정했습니다.
- where : 지정된 조건과 일치하는 항목만 보여줍니다. where 속성의 구문은 find 명령과 유사합니다.
- brief : 인쇄 명령이 테이블 형식 출력 양식을 사용하도록 합니다.
- detail : 인쇄 명령이 property = value 출력 약식을 사용하도록 합니다.
- count-only : 항목 수를 표시합니다.
- file : 특정 하위 메뉴의 내용을 라우터의 파일로 인쇄합니다.
- interval : 간격 초마다 인쇄 명령의 출력을 업데이트 합니다.
- oid : SNMP에서 액세스 할 수있는 특성의 OID값을 인쇄합니다.
- without-paging : 각 화면 처리 후 중지하지 않고 출력을 인쇄합니다.
- remove : 지정된 항목을 (-s) 목록에서 제거합니다.
- set : 일반 매개 변수 또는 항목 매개 변수의 값을 변경할 수 있습니다. set 명령에는 변경할 수있는 값에 해당하는 이름을 가진 인수가 있습니다. 사용하
다 ? 또는 모든 인수 목록을 보려면 [Tab]을 두번 누르면 됩니다. 이 명령 레벨에 항목 목록이 있는 경우 set에는  설정하려는 항목 수 (또는 숫자 목록)를
허용하는 하나의 조치 인수가 있습니다. 이 명령은 아무것도 반환하지 않습니다.

-----
**mode** <br>
콘솔 라인 편집기는 다중 라인 모드 또는 단일 라인 모드에서 작동합니다. 멀티 라인 모드에서 편집기는 단일 터미널 라인보다 길더라도 완전한 입력 라인을 
표시합니다. 또한 스크립트와 같은 큰 텍스트 값을 편집하기 위해 전체 화면 편집기를 사용합니다. 단일 라인 모드에서는 단 하나의 터미널 라인만 라인 편집
에 사용되며 긴 라인은 커서 주위에서 잘립니다. 이 모드에서는 전체 화면 편집기가 사용되지 않습니다. 모드 선택은 감지된 터미널 기능에 따라 다릅니다.

-----
**키 목록** <br>
- Control-C : 키보드 인터럽트
- Control-D : 로그 아웃 (입력 라인이 비어있는 경우)
- Control-K : 커서에서 줄 끝까지 지움
- Control-X : 안전 모드 토글
- Control-V : 핫록 모드 모드 토글
- F6 : 지하실 토글
- F1 or ? : 상황에 맞는 도움말을 표시합니다. 이전 문자가 \이면 literal ?를 삽입합니다.
- Tap : 라인 완성을 수행해야 합니다. 두번 누르면 가능한 완료를 표시합니다.
- Delete : 커서에서 문자 제거
- Control-H or Backspace : 커서 앞의 문자를 제거하고 커서를 한 위치 뒤로 이동해야 합니다.
- Control-\ : 커서에서 분할 선. 커서 위치에 줄 바꿈을 삽입해야 합니다. 두개의 결과 행 중 두번째를 표시해야 합니다.
- Control-B or Left : 커서를 한 문자 뒤로 이동
- Control-F or Right : 커서를 한 문자 앞으로 이동
- Control-P or Up : 이전 줄로 이동해야 합니다. 이것이 첫번째 입력 행인 경우 history에서 이전 입력을 호출해야 합니다.
- Control-N or Down : 다음 줄로 이동해야 합니다. 이것이 마지막 입력 행인 경우 history 에서 다음 입력을 호출해야 합니다.
- Control-A or Home : 커서를 줄의 시작 부분으로 이동해야 합니다. 커서가 이미 줄의 시작 부분에 있으면 현재 입력의 첫번째 줄의 시작으로 이동
- Control-E or end : 커서를 줄의 끝으로 이동해야 합니다. 커서가 이미 줄의 끝에 있다면 ,현재 입력의 마지막 줄으로 끝으로 커서를 이동해야 합니다.
- Control-L or F5 : 터미널을 재설정하고 화면을 다시 칠해야 합니다.
- up, down 및 split 키는 줄 끝에서 커서를 둡니다.
*내장 도움말* : 콘솔에는 ?가 입력되어 액세스 할 수있는 내장된 도움말이 있습니다. 일반적인 규칙은 도움말에서 ? ([Tap]키를 두번 누르는 것과 유사하지
만 자세한 설명과 함께)

-----
**안전모드** <br>
라우터에 액세스 할 수없는 방식으로 로컬 콘솔을 제외하고 라우터 구성을 변경하는 것이 때때로 가능합니다. 일반적으로 이것은 실수로 수행되지만 라우터에
대한 연결이 이미 끊어진 경우 마지막 변경을 취소 할 수있는 방법이 없습니다. 이러한 위험을 최소화 하기위해 안전모드를 사용할 수 있습니다. <br>
[CTRL] + [X] 를 눌러 안전 모드로 들어갑니다. 변경 사항을 저장하고 안전 모드를 종료하려면 [CTRL] + [X] 를 다시 눌러야 합니다. 변경 사항을 저장하지
않고 종료하려면 [CTRL] + [D] 를 눌러야 합니다. <br>
`ip route> [CTRL] + [X]` <br>
`ip route <SAFE>` <br>
![2009-04-06_1317](https://user-images.githubusercontent.com/63625609/82620979-c7960c80-9c14-11ea-8346-c7a75f367a28.png) <br>
사용된 메세지 안전 모드가 표시되고 세션이 이제 안전 모드에 있음을 나타 내기 위해 프롬프트가 변경됩니다. 라우터가 안전 모드에 있는 동안 (다른 로그인
세션에서도) 이루어진 모든 구성 변경은 안전 모드 세션이 비정상적으로 종료되면 자동으로 취소됩니다. 시스템 히스토리에서 F 플래그로 자동 태그 취소되는
모든 변경 사항을 볼 수 있습니다. <br>
`[admin@MikroTik] ip route>` <br>
`[Safe Mode taken]` <br>
`[admin@MikroTik] ip route<SAFE> add` <br>
`[admin@MikroTik] ip route<SAFE> /system history print` <br>
이제 텔넷 연결 (또는 winbox 터미널)이 끊어지면 잠시후 (TCP 시간 초과는 9분) 안전 모드에서 이루어진 모든 변경 사항이 취소됩니다. [Ctrl] + [D] 로 
세션을 종료 하면 모든 안전 모드 변경이 취소되지만 /quit 는 그렇지 않습니다. 다른 사용자가 안전 모드로 들어가려고 하면 아래 메세지가 출력됩니다. 
`[admin@MikroTik] > <br>
Hijacking Safe Mode from someone - unroll/release/don't take it [u/r/d]:` <br>
[u] : 모든 안전 모드 변경을 취소하고 현재 세션을 안전 모드로 설정합니다. <br>
[r] : 모든 현재 안전 모드 변경 사항을 유지하고 현재 세션을 안전 모드로 설정합니다. 안전 모드의 이전 소유자에게 다음에 대한 알림이 표시됩니다.
     `[admin@MikroTik] ip firewall rule input <br> 
     [Safe mode released by another user]` <br>
[d] : 모든 것을 그대로 둡니다. <br>
안전 모드에 있는 동안 너무 많은 변경이 수행되고 모든 기록을 수용할 공간이 없는 경우 (현재 기록은 최대 100개의 최신 작업을 유지함) 세션이 자동으로 
안전 모드에서 해제되고 변경 사항이 자동으로 취소되지 않습니다. 따라서 안전 모드에서 작은 단계로 구성을 변경하는 것이 가장 좋습니다. [Ctrl] + [X] 
를 두번 누르면 안전 모드 작업 목록을 비울 수 있습니다. 

-----
**핫락 모드** <br>
HotLock mode가 활성화되면 명령이 자동으로 완료됩니다. <br>
HotLock mode를 시작 / 종료 하려면 [CTRL] + [V]를 눌러야 합니다. <br>
`[admin@MikroTik] /ip address> [CTRL]+[V] <br>
[admin@MikroTik] /ip address>>` <br>
이중에 >> 은 HotLock 모드가 활성화 되었음을 나타냅니다. 예를 들어 /in e 를 입력하면 다음과 같이 자동완성 됩니다. <br>
`[admin@MikroTik] /ip address>> /interface ethernet` <br>
Quick Help Menu(빠른 도움말 메뉴) <br>
F6 키는 터미널 하단에 메뉴를 활성화하여 공통 키 조합과 사용법을 보여줍니다. <br>
`[admin@RB493G] >  <br>
tab compl ? F1 help ^V hotlk ^X safe ^C brk ^D quit`

