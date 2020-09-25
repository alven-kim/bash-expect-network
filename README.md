network config using bash expect
================================

## Concept
 - 네트워크 장비들의 설정과 output에 대한 log 저장
 - SSH Terminal 접근 시, Timeout Feedback output
 - bash expect install

## Dependency
 - bash user 환경변수 영향이 있으므로 필요한 경우 스크립트 환경변수 변경하여 사용.
 - openssh 설치

## 참고사항
 - 모든 장비의 ID/PW 동일해야 함
 - 10초 이상 미응답 시, timeout
 - 필요시에는 stdout redirection 설정하여 표준 출력 제거. ( 1>/dev/null )

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
 - 로그파일 : 현재 경로에 hostname.log로 기록되며, append하지 않음.
 - filename : 여기선 switch_list.txt 파일을 사용하였으며, 필요한 장비의 Hostname(or IP) 입력.
 - 객체형 설정의 경우 적용되지 않음. (one-line commands만 적용됨)

## TODO
 - timeout과 ID/PW 오입력에 대한 stderr를 구현 가능한지 리서치

## See Also
 - man bash
