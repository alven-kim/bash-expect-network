bash expect - running-config
============================

## Concept
 - 네트워크 장비의 running-config & output log 저장
 - SSH Terminal 접근 시, Timeout Feedback output
 - bash expect install

## Dependency
 - bash user 환경변수 영향이 있으므로 필요한 경우 스크립트 환경변수 변경하여 사용.
 - openssh 설치

## 참고사항
 - 모든 장비의 ID/PW 동일해야 함
 - 10초 이상 미응답 시, timeout되며, timeout은 stdout으로 구현하였으므로 로그파일을 통해 확인 가능
 - 필요시에는 stdout 제거하여 표준 출력 확인. ( 1>/dev/null )

## 사용방법

### Case1) network-running-config-argv-v2.sh
 - ./script.sh [hostname1] [hostname2] ..... 
```bash
Example ./network-running-config-argv-v2.sh 1.1.1.1 2.2.2.2 .....
```
 - 로그파일 : 현재 경로에 hostname.log로 기록되며, append하지 않음.

### Case2) network-any-config-file.sh
 - 사용예제 : ./script.sh [filename] ['commands']
```bash
Example1) ./network-any-config.sh switch_list.txt 'show system'
Example2) ./network-any-config.sh switch_list.txt 'show running-config'
Example3) ./network-any-config.sh switch_list.txt 'show arp'
```
 - filename : 여기선 switch_list.txt 파일을 사용하였으며, 필요한 장비의 IP 입력.
 - 로그파일 : 현재 경로에 hostname.log로 기록되며, append하지 않음.
 - 객체형 설정의 경우 적용되지 않음. (one-line commands만 적용됨)

## TODO
 - timeout과 ID/PW 오입력에 대한 stderr를 구현 예정(현재는 stdout으로 모두 redirection되므로 로그 파일을 통해 확인 가능)

## See Also
 - man bash
