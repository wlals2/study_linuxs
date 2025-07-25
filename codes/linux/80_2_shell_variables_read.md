# shell_variables_read
## shell script 코드
```bash
#변수 지정
argument_first="$1"

read -p "변수를 입력하세요: " read_first
echo "$argument_first (이)는 $read_first"
```
### 입력확인
```bash
$ sh shell_read.sh 지민
변수를 입력하세요: 바보
지민 (이)는 바보
```