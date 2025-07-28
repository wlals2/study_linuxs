# ✅ 문제 : 간단한 서버 관리 스크립트 작성
## 🔧 요구사항
### start: 포트 8000에서 http.server를 백그라운드로 
```bash
실행 (nohup, 로그는 server.log)


stop: 실행 중인 프로세스를 찾아 종료


status: 프로세스가 실행 중인지 확인하여 출력


restart: 중지 후 다시 실행
```
```bash
# 쉘 스크립트
#!/bin/bash

logfile=./http_server.log
stopnum=$(ps -aux | grep "http.server" | grep -v grep | tr -s " " | cut -d " " -f2)
echo "Stop number: $stopnum"
state="$1"
if [ $state = "start" ]; then
        if [ -n "$stopnum" ]; then
                echo "이미 서버가 실행중입니다"
        else
                nohup python3 -m http.server $PORT --bind 0.0.0.0 > "$logfile" 2>&1 &
                echo " 서버가 백그라운드에서 시작되었습니다"
        fi
elif [ "$state" = "status" ]; then
        if [ -n "$stopnum" ]; then
                echo "서버가 실행 중입니다 PID: $stopnum"
        else
                echo "서버가 실행 중이지 않습니다."
        fi

elif [ "$state" = "stop" ]; then
        kill -9 $stopnum

        echo "서버가 종료되었습니다."

elif [ "$state" = "tail_log" ]; then
        tail -f "$logfile"

fi

# start 실행중
sh shell_script_process.sh start
Stop number: 5414
이미 서버가 실행중입니다

# start 실행 하고 있지 않음
 sh shell_script_process.sh start
Stop number:
 서버가 백그라운드에서 시작되었습니다

#stop
sh shell_script_process.sh stop
Stop number: 5414
서버가 종료되었습니다.

#status
sh shell_script_process.sh status
Stop number: 5563
서버가 실행 중입니다 PID: 5563

# tail_log / curl localhost:8000
sh shell_script_process.sh tail_log
Stop number: 5563
127.0.0.1 - - [28/Jul/2025 15:44:59] "GET / HTTP/1.1" 200 -

```
### 🎯 실행 예시
```bash
$ ./webserver.sh start
서버가 백그라운드에서 시작되었습니다.

$ ./webserver.sh status
서버 실행 중입니다. PID: 13579

$ ./webserver.sh stop
서버가 종료되었습니다.

$ ./webserver.sh tail_log / curl localhot:8000

… log message 확인

문제 모두 조건에 따라:
if [ "$1" == "start" ] 식으로 흐름 제어


변수 PORT, PID, LOGFILE 등을 정의해 구성 가능
````