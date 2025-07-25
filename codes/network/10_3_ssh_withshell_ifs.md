# Shell 조건문 및 텍스트 처리 실습 문제
## 실습 환경 설정
### 1. 실습 디렉토리 생성 및 이동
```bash
mkdir ~/shell_practice
cd ~/shell_practice
```
### 2. 실습용 데이터 파일 생성
```bash
students.txt 파일 생성
cat > students.txt << EOF
김철수:수학:85:영어:92:과학:78
이영희:수학:95:영어:88:과학:91
박민수:수학:76:영어:79:과학:82
최지원:수학:88:영어:95:과학:89
정우진:수학:92:영어:76:과학:94
김지현:수학:83:영어:91:과학:87
이준호:수학:79:영어:84:과학:76
박서연:수학:97:영어:93:과학:96
한도윤:수학:81:영어:77:과학:83
송민재:수학:86:영어:89:과학:91
EOF
```
### server_logs.txt 파일 생성
```bash
cat > server_logs.txt << EOF
2024-01-15 10:30:15 INFO User login successful: user001
2024-01-15 10:31:22 ERROR Database connection failed
2024-01-15 10:32:05 INFO User login successful: user002
2024-01-15 10:33:18 WARNING Memory usage high: 85%
2024-01-15 10:34:25 ERROR Authentication failed: user003
2024-01-15 10:35:10 INFO User logout: user001
2024-01-15 10:36:33 ERROR Network timeout occurred
2024-01-15 10:37:45 INFO System backup started
2024-01-15 10:38:52 WARNING Disk space low: 90%
2024-01-15 10:39:15 ERROR Database connection failed
2024-01-15 10:40:28 INFO User login successful: user004
2024-01-15 10:41:35 ERROR Authentication failed: user005
EOF
```


### sales_data.txt 파일 생성
```bash
cat > sales_data.txt << EOF
2024-01,서울,노트북,1500000
2024-01,부산,스마트폰,800000
2024-01,대구,태블릿,600000
2024-01,서울,스마트폰,850000
2024-02,부산,노트북,1450000
2024-02,서울,태블릿,620000
2024-02,대구,스마트폰,780000
2024-02,서울,노트북,1520000
2024-03,부산,태블릿,590000
2024-03,대구,노트북,1480000
2024-03,서울,스마트폰,820000
2024-03,부산,스마트폰,790000
EOF
```

### words.txt 파일 생성
```bash
cat > words.txt << EOF
apple
banana
Apple
cherry
BANANA
date
Cherry
elderberry
Apple
fig
banana
CHERRY
EOF
```

# 실습 문제
## 문제 1: 학생 성적 분석기 
### 파일: grade_analyzer.sh
### 요구사항:
```bash
students.txt 파일을 분석하여 다음 기능을 수행하는 스크립트 작성
사용자로부터 과목명을 입력받아 해당 과목의 통계 정보 출력
조건문을 사용하여 입력 검증 및 등급 분류 수행
구현해야 할 기능:
사용자가 입력한 과목이 유효한지 검사 (수학, 영어, 과학)
해당 과목의 모든 점수를 추출하여 정렬된 목록 출력
최고점, 최저점, 평균점수 계산
90점 이상(A), 80점 이상(B), 70점 이상(C), 그 외(D) 등급별 학생 수 출력
평균이 85점 이상이면 "우수", 75점 이상이면 "양호", 그 외는 "보통" 출력
힌트:
cut, grep, sort, wc 명령어 활용
파이프라인으로 명령어 연결
조건문으로 점수 범위 검사
```
```bash
[im@192.168.0.31 ~/Downloads/test1]$ cat student_test.sh
#!/bin/bash

file=students.txt
read -p "과목을 입력해주세요: " class

if [[ "$class" != "수학" && "$class" != "영어" && "$class" != "과학" ]]; then
    echo "[오류] 지원하지 않는 과목입니다."
    echo "가능한 과목: 수학, 영어, 과학"
    exit 1
fi

#  과목별 필드 번호 세팅
if [ "$class" == "수학" ]; then
    field=3
elif [ "$class" == "영어" ]; then
    field=5
else
    field=7
fi
sc=$(cut -d: -f$field "$file")
echo "============="$class"================"
echo "$sc"
scores=$(cut -d: -f$field "$file" | tr '\n' ' ')

# 초기값 세팅
sum=0
count=0
min=9999
max=0
a_cnt=0
b_cnt=0
c_cnt=0
d_cnt=0

# for문 순회
for score in $scores; do
    sum=$((sum + score))
    count=$((count + 1))

    # 최대/최소
    if [ "$score" -gt "$max" ]; then
        max=$score
    fi
    if [ "$score" -lt "$min" ]; then
        min=$score
    fi

    # 등급별 분류
    if [ "$score" -ge 90 ]; then
        a_cnt=$((a_cnt + 1))
    elif [ "$score" -ge 80 ]; then
        b_cnt=$((b_cnt + 1))
    elif [ "$score" -ge 70 ]; then
        c_cnt=$((c_cnt + 1))
    else
        d_cnt=$((d_cnt + 1))
    fi
done

# 평균(소수점까지), 평가 등급
avg=$(echo "scale=2; $sum / $count" | bc)

echo "===============$class 점수================"
echo "정렬된 점수:"
# sort로 정렬된 점수 출력(정수 오름차순)
echo $scores | tr ' ' '\n' | sort -n | xargs

echo "최고점: $max"
echo "최저점: $min"
echo "평균점: $avg"

echo "A(90점 이상): $a_cnt 명"
echo "B(80점 이상): $b_cnt 명"
echo "C(70점 이상): $c_cnt 명"
echo "D(70점 미만): $d_cnt 명"

if (( $(echo "$avg >= 85" | bc -l) )); then
    echo "평가: 우수"
elif (( $(echo "$avg >= 75" | bc -l) )); then
    echo "평가: 양호"
else
    echo "평가: 보통"
fi

```










