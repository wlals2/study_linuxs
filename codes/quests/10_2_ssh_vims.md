# 🧪 vim 편집 실습 문제 (난이도 순으로 정렬, CRUD Mode 한정)
## 💻 실습 목표
### vim 편집기를 활용하여 텍스트 파일에서 Create / Read / Update / Delete 작업을 정확하게 수행

#### 📁 실습 사전 환경 준비 (모든 컴퓨터 공통)
```bash
#!/bin/bash
mkdir -p ~/vim_crud_practice/{comp1,comp2,comp3}
cd ~/vim_crud_practice/comp1
echo -e "Apple\nBanana\nCherry" > fruits.txt

cd ../comp2
echo -e "1. Clean the house\n2. Buy groceries\n3. Call Mom" > todo.txt

cd ../comp3
echo -e "Name,Email\nJohn Doe,john@example.com\nJane Doe,jane@example.com" > users.csv

chmod +x setup_env.sh && ./setup_env.sh
```

### 🧭 실습 시나리오
```bash
각 실습은 서로 다른 SSH 대상에서 수행
ssh user@192.168.0.101  # 컴퓨터1 (comp1 디렉토리 실습)
ssh user@192.168.0.102  # 컴퓨터2 (comp2 디렉토리 실습)
ssh user@192.168.0.103  # 컴퓨터3 (comp3 디렉토리 실습)
```

## 🔧 실습 문제 (난이도 순)

### 🔹 실습 1. (기초: Read & Search) – comp2/todo.txt
### 🔧 목표: 복사, 붙여넣기 숙달
### 작업 경로: ~/vim_crud_practice/comp2/todo.txt
```bash
vim으로 파일 열기


Buy groceries 줄을 복사한 뒤, 맨 아래에 두 번 붙여넣기


저장 후 종료
✅ 명령어 힌트: /검색, yy, p, :wq
```
### 답변
```bash
~/vim_crud_practice/comp2/todo.txt
yy
p
:wq
1. Clean the house
2. Buy groceries
3. Call Mom
2. Buy groceries
2. Buy groceries

```



# 🔹 실습 2. (기초+: Create & Append) – comp1/fruits.txt
```bash
🔧 목표: 입력 모드와 줄 추가 숙련
작업 경로: ~/vim_crud_practice/comp1/fruits.txt

마지막 줄 아래에 다음 과일 추가

 Durian  
Elderberry
저장 후 종료
```
### 답변

```bash
Apple
Banana
Cherry
Durian
Elderberry

```

### ✅ 명령어 힌트: G, o, i, ESC, :wq

### 🔹 실습 3. (중간: Update + 반복 붙여넣기) – comp3/users.csv
### 🔧 목표: 문자열 수정, 줄 삽입 반복
```bash
작업 경로: ~/vim_crud_practice/comp3/users.csv
john@example.com → john.doe@gmail.com으로 수정


수정한 라인을 복사한 후 아래 줄에 3번 반복 붙여넣기


저장 후 종료

```
### 답변
```bash
Name,Email
john.doe@gmail.com
Jane Doe,jane@example.com
john.doe@gmail.com
john.doe@gmail.com
john.doe@gmail.com
```
### ✅ 명령어 힌트: :%s///, yy, p, :wq

## 🔹 실습 4. (중상: Delete & Navigation) – comp1/fruits.txt
### 🔧 목표: 줄 삭제 후 조작
```bash
작업 경로: ~/vim_crud_practice/comp1/fruits.txt
Cherry 해당 줄을 삭제


저장 후 종료
```
### 답변
```bash
Apple
Banana
Durian
Elderberry

```

✅ 명령어 힌트: /Cherry, dd, :wq

## 🔹 실습 5. (심화: 다중 치환 + 복구) – comp3/users.csv
### 🔧 목표: 반복 치환, 삭제 복구
```bash
작업 경로: ~/vim_crud_practice/comp3/users.csv
모든 Doe → Smith로 전체 치환


실수로 한 줄을 삭제한 뒤, 삭제된 줄 복구


저장 후 종료

```

✅ 명령어 힌트: :%s/Doe/Smith/g, u, :wq

## 🎓 선택 학습 질문 (보조 학습)
```bash
vim에서 실수로 삭제한 줄을 복구하려면?
 → u (undo), U (줄 단위 undo), Ctrl+r (redo)


여러 줄을 복사하고 여러 위치에 붙여넣으려면?
 → V (비쥬얼 모드로 여러 줄 선택) → y → 원하는 위치로 이동 후 p


vim에서 반복 치환 명령은?
 → :%s/기존문자열/변경문자열/g
```
### 답변
```bash
:%s/Doe/Smith/g
Name,Email
john.doe@gmail.com
Jane Smith,jane@example.com
john.doe@gmail.com
john.doe@gmail.com
john.doe@gmail.com

```


# 📝 평가 기준
```bash
항목
평가 포인트
파일 수정 정확성
요구된 작업 정확히 수행 여부
명령어 숙련도
vim 기본 명령어 활용 정확성
SSH 이동 숙련도
3개 컴퓨터에 정확히 접속 및 작업 수행
저장/종료 정확성
:w, :q, :wq 숙지 여부
오류 복구 능력
u, Ctrl+r 등으로 복구 가능 여부 (심화 문제 포함 시)
```

### 📎 복습 명령어 요약
```bash
명령어
기능
i, o
입력 모드 진입 / 아래 줄 입력
ESC
명령 모드 전환
:w, :q, :wq, :q!
저장 / 종료 / 강제 종료
dd, yy, p
줄 삭제 / 복사 / 붙여넣기
/문자열
검색
:%s/a/b/g
전체 치환
u, Ctrl+r
undo / redo


필요 시, 실습별 타이머 또는 모범 답안 설명용 데모 영상도 연계 가능합니다.
```

