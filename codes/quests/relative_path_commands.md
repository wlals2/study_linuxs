# 리눅스 상대주소 실습 문제
## 사전 준비 : 실습 환경 설정
```
mkdir -p ~/practice/project/{src,docs,tests,config}
mkdir -p ~/practice/project/src/{main,utils}
mkdir -p ~/practice/project/docs/{user,dev}
mkdir -p ~/practice/project/tests/unit
touch ~/practice/project/README.md
touch ~/practice/project/src/main/app.py
touch ~/practice/project/src/utils/helper.py
touch ~/practice/project/docs/user/manual.txt
touch ~/practice/project/docs/dev/api.md
touch ~/practice/project/tests/test_main.py
touch ~/practice/project/config/settings.conf
```
<b>완성된 디렉터리 구조: </b>
~/practice/project/
<br><b>
├── README.md
<br>
├── src/
<br>
│   ├── main/
<br>
│   │   └── app.py
<br>
│   └── utils/
<br>
│       └── helper.py
<br>
├── docs/
<br>
│   ├── user/
<br>
│   │   └── manual.txt
<br>
│   └── dev/
<br>
│       └── api.md
<br>
├── tests/
<br>
│   ├── unit/
<br>
│   └── test_main.py
<br>
└── config/
<br>
    └── settings.conf
<br>
</b>

## 연습문제 1: 기본 상대 주소 이해
<h3><b>1-1·2. 현재 위치에서 상대 주소 확인 및 파일 검증 <br></h3></b>

<b> 0. 현재 위치 확인 </b><br>
```
[ohjimin@localhost ~]$ cd ~/practice/project/src/main/
[ohjimin@localhost main]$ pwd
/home/ohjimin/practice/project/src/main
[ohjimin@localhost main]$ 
```

<b> 1. helper.py:</b>
```
[ohjimin@localhost main]$ touch ../utils/helper.py
[ohjimin@localhost main]$ ls -al ../utils/
total 0
drwxr-xr-x. 2 ohjimin ohjimin 23 Jul 16 16:21 .
drwxr-xr-x. 4 ohjimin ohjimin 31 Jul 16 16:21 ..
-rw-r--r--. 1 ohjimin ohjimin  0 Jul 16 16:35 helper.py
```
<b>2. README.md</b>
```
[ohjimin@localhost main]$ touch ../../README.md
[ohjimin@localhost main]$ ls -al ../../
total 0
drwxr-xr-x. 6 ohjimin ohjimin 73 Jul 16 16:21 .
drwxr-xr-x. 3 ohjimin ohjimin 21 Jul 16 16:21 ..
drwxr-xr-x. 2 ohjimin ohjimin 27 Jul 16 16:21 config
drwxr-xr-x. 4 ohjimin ohjimin 29 Jul 16 16:21 docs
-rw-r--r--. 1 ohjimin ohjimin  0 Jul 16 16:37 README.md
drwxr-xr-x. 4 ohjimin ohjimin 31 Jul 16 16:21 src
drwxr-xr-x. 3 ohjimin ohjimin 38 Jul 16 16:21 tests
```
<b>3. manual.txt</b>
```
[ohjimin@localhost main]$ touch ../../docs/user/manual.txt
[ohjimin@localhost main]$ ls -al ../../docs/user/
total 0
drwxr-xr-x. 2 ohjimin ohjimin 24 Jul 16 16:21 .
drwxr-xr-x. 4 ohjimin ohjimin 29 Jul 16 16:21 ..
-rw-r--r--. 1 ohjimin ohjimin  0 Jul 16 16:38 manual.txt
```
<b>4. settings.conf</b>
```
[ohjimin@localhost main]$ touch ../../config/settings.conf 
[ohjimin@localhost main]$ ls -al ../../config
total 0
drwxr-xr-x. 2 ohjimin ohjimin 27 Jul 16 16:21 .
drwxr-xr-x. 6 ohjimin ohjimin 73 Jul 16 16:21 ..
-rw-r--r--. 1 ohjimin ohjimin  0 Jul 16 16:40 settings.conf
```



## 연습 문제2: 다양한 시작점에서의 상대주소
<h3><b> 2-1. 시작점 변경 실습 </h3></b>
<b>1. app.py 파일로 이동하는 상대 주소를 작성하시오</b>

```
[ohjimin@localhost main]$ cd ~/practice/project/docs/user/
[ohjimin@localhost user]$ cd ../../
config/ docs/   src/    tests/  
[ohjimin@localhost user]$ cd ../../src/main
[ohjimin@localhost main]$ ls
app.py
[ohjimin@localhost main]$ ls -al
total 0
drwxr-xr-x. 2 ohjimin ohjimin 20 Jul 16 16:21 .
drwxr-xr-x. 4 ohjimin ohjimin 31 Jul 16 16:21 ..
-rw-r--r--. 1 ohjimin ohjimin  0 Jul 16 16:21 app.py
```
<b>2. test_main.py 파일로 이동하는 상대 주소를 작성하시오.</b>
```
[ohjimin@localhost tests]$ ls -al
total 0
drwxr-xr-x. 3 ohjimin ohjimin 38 Jul 16 16:21 .
drwxr-xr-x. 6 ohjimin ohjimin 73 Jul 16 16:21 ..
-rw-r--r--. 1 ohjimin ohjimin  0 Jul 16 16:21 test_main.py
drwxr-xr-x. 2 ohjimin ohjimin  6 Jul 16 16:21 unit
```
<b>3. src/utils/ 디렉토리로 이동하는 상대 주소를 작성하시오.</b>
```
[ohjimin@localhost tests]$ cd ../src/utils/
[ohjimin@localhost utils]$ ls -al
total 0
drwxr-xr-x. 2 ohjimin ohjimin 23 Jul 16 16:21 .
drwxr-xr-x. 4 ohjimin ohjimin 31 Jul 16 16:21 ..
-rw-r--r--. 1 ohjimin ohjimin  0 Jul 16 16:35 helper.py
[ohjimin@localhost utils]$ pwd
/home/ohjimin/practice/project/src/utils
```
<h3><b>2-2. 역방향 상대 주소</h3></b>
<b>1. 프로젝트 루트(~/practice/project/)로 이동하는 상대 주소를 작성하시오.</b>

```
[ohjimin@localhost unit]$ cd ../../../../practice/project/
[ohjimin@localhost project]$ pwd
/home/ohjimin/practice/project
```
<b>2.api.md 파일로 이동하는 상대 주소를 작성하시오.</b>
```
[ohjimin@localhost unit]$ cd ../../docs/dev/
[ohjimin@localhost dev]$ ls -al
total 0
drwxr-xr-x. 2 ohjimin ohjimin 20 Jul 16 16:21 .
drwxr-xr-x. 4 ohjimin ohjimin 29 Jul 16 16:21 ..
-rw-r--r--. 1 ohjimin ohjimin  0 Jul 16 16:21 api.md
[ohjimin@localhost dev]$ pwd
/home/ohjimin/practice/project/docs/dev
```
<b>3.helper.py 파일로 이동하는 상대 주소를 작성하시오.</b>
```
[ohjimin@localhost unit]$ pwd
/home/ohjimin/practice/project/tests/unit
[ohjimin@localhost unit]$ cd ../../src/utils/
[ohjimin@localhost utils]$ ls -al
total 0
drwxr-xr-x. 2 ohjimin ohjimin 23 Jul 16 16:21 .
drwxr-xr-x. 4 ohjimin ohjimin 31 Jul 16 16:21 ..
-rw-r--r--. 1 ohjimin ohjimin  0 Jul 16 16:35 helper.py
```

## 연습문제 3: 파일 내용 확인 및 조작
<h3><b>3-1. 상대 주소를 이용한 파일 내용 출력</h3></b>
<b>1. 프로젝트 루트의 README.md 파일 내용을 출력하시오.</b>

```
[ohjimin@localhost utils]$ cat ../../../project/README.md
```
<b>2. docs/user/manual.txt 파일 내용을 출력하시오.</b>
```
[ohjimin@localhost utils]$ pwd
/home/ohjimin/practice/project/src/utils
[ohjimin@localhost utils]$ cat ../../docs/user/manual.txt 
[ohjimin@localhost utils]$ 
```
<b>3. config/settings.conf 파일 내용을 출력하시오.</b>
```
[ohjimin@localhost utils]$ cat ../../config/settings.conf 
[ohjimin@localhost utils]$ pwd
/home/ohjimin/practice/project/src/utils

```

<h3><b>3-2. 상대주소를 이용한 파일 생성</h3></b>
<b>1. 현재 디렉토리에 config.py 파일을 생성하고 "# Configuration module"이라는 내용을 작성하시오.</b><br>

```
[ohjimin@localhost main]$ echo "# Configuration module" > config.py
[ohjimin@localhost main]$ cat config.py 
# Configuration module
[ohjimin@localhost main]$ pwd
/home/ohjimin/practice/project/src/main
```
<b>2. tests/ 디렉토리에 test_app.py 파일을 생성하고 "# App test file"이라는 내용을 작성하시오.</b>

```
[ohjimin@localhost main]$ echo "# App test file" >  ../../tests/test_main.py 
[ohjimin@localhost main]$ cat  ../../tests/test_main.py 
# App test file
[ohjimin@localhost main]$ pwd
/home/ohjimin/practice/project/src/main
```
## 연습문제 4: 파일 복사 및 이동 
<h3><b>4-1. 상대주소를 이용한 파일 이동</h3></b>
<b>1. api.md 파일을 docs/user/ 디렉토리에 api_copy.md로 복사하시오.</b>

```
[ohjimin@localhost main]$ pwd
/home/ohjimin/practice/project/src/main
[ohjimin@localhost main]$ cd ~/practice/project/docs/dev/
[ohjimin@localhost dev]$ cp ../../docs/dev/api.md ../../docs/user/
[ohjimin@localhost dev]$ ls -al ../../docs/user/
total 0
drwxr-xr-x. 2 ohjimin ohjimin 38 Jul 16 17:10 .
drwxr-xr-x. 4 ohjimin ohjimin 29 Jul 16 16:21 ..
-rw-r--r--. 1 ohjimin ohjimin  0 Jul 16 17:10 api.md
-rw-r--r--. 1 ohjimin ohjimin  0 Jul 16 16:38 manual.txt
```
<b>2. src/utils/helper.py 파일을 현재 디렉토리에 복사하시오.</b>
```
[ohjimin@localhost dev]$ cp ../../src/utils/helper.py .
[ohjimin@localhost dev]$ ls -al
total 0
drwxr-xr-x. 2 ohjimin ohjimin 37 Jul 16 17:11 .
drwxr-xr-x. 4 ohjimin ohjimin 29 Jul 16 16:21 ..
-rw-r--r--. 1 ohjimin ohjimin  0 Jul 16 16:21 api.md
-rw-r--r--. 1 ohjimin ohjimin  0 Jul 16 17:11 helper.py
[ohjimin@localhost dev]$ pwd
/home/ohjimin/practice/project/docs/dev
```
<b>3. config/settings.conf 파일을 tests/unit/ 디렉토리에 복사하시오. </b>
```
[ohjimin@localhost dev]$ cp ../../config/settings.conf ../../tests/unit/
[ohjimin@localhost dev]$ ls -al ../../tests/unit/
total 0
drwxr-xr-x. 2 ohjimin ohjimin 27 Jul 16 17:12 .
drwxr-xr-x. 3 ohjimin ohjimin 38 Jul 16 16:21 ..
-rw-r--r--. 1 ohjimin ohjimin  0 Jul 16 17:12 settings.conf
[ohjimin@localhost dev]$ pwd
/home/ohjimin/practice/project/docs/dev
```
<h3><b>4-2. 상대 주소를 이용한 파일 이동</h3></b>
<b>1. test_main.py 파일을 tests/unit/ 디렉토리로 이동하시오.</b>

```
[ohjimin@localhost tests]$ pwd
/home/ohjimin/practice/project/tests
[ohjimin@localhost tests]$ mv test_main.py ./unit/
[ohjimin@localhost tests]$ ls -al ./unit/
total 4
drwxr-xr-x. 2 ohjimin ohjimin 47 Jul 16 17:14 .
drwxr-xr-x. 3 ohjimin ohjimin 18 Jul 16 17:14 ..
-rw-r--r--. 1 ohjimin ohjimin  0 Jul 16 17:12 settings.conf
-rw-r--r--. 1 ohjimin ohjimin 16 Jul 16 17:07 test_main.py
```
<b>2. src/main/config.py 파일을 config/ 디렉토리로 이동하시오.</b>
```
[ohjimin@localhost tests]$ mv ../src/main/config.py ../config/
[ohjimin@localhost tests]$ ls -al ../config/
total 4
drwxr-xr-x. 2 ohjimin ohjimin 44 Jul 16 17:15 .
drwxr-xr-x. 6 ohjimin ohjimin 73 Jul 16 16:21 ..
-rw-r--r--. 1 ohjimin ohjimin 23 Jul 16 17:04 config.py
-rw-r--r--. 1 ohjimin ohjimin  0 Jul 16 16:40 settings.conf
[ohjimin@localhost tests]$ pwd
/home/ohjimin/practice/project/tests
```
## 연습문제5: 복합 상대 주소 활용
<h3><b>5-1. 다중 파일 조작</h3></b>
<b>1. src/main/ 디렉토리의 모든 파일을 docs/dev/ 디렉토리에 복사하시오.</b>

```
[ohjimin@localhost project]$ cp -r src/main/ docs/dev/
[ohjimin@localhost project]$ ls -al docs/dev/
total 0
drwxr-xr-x. 3 ohjimin ohjimin 49 Jul 16 17:18 .
drwxr-xr-x. 4 ohjimin ohjimin 29 Jul 16 16:21 ..
-rw-r--r--. 1 ohjimin ohjimin  0 Jul 16 16:21 api.md
-rw-r--r--. 1 ohjimin ohjimin  0 Jul 16 17:11 helper.py
drwxr-xr-x. 2 ohjimin ohjimin 20 Jul 16 17:18 main
[ohjimin@localhost project]$ pwd
/home/ohjimin/practice/project

```

<b>2. docs/user/ 디렉토리의 모든 파일을 tests/unit/ 디렉토리로 이동하시오.</b>

```
[ohjimin@localhost project]$ mv  docs/user/ tests/unit/
[ohjimin@localhost project]$ ls -al tests/unit/
total 4
drwxr-xr-x. 3 ohjimin ohjimin 59 Jul 16 17:19 .
drwxr-xr-x. 3 ohjimin ohjimin 18 Jul 16 17:14 ..
-rw-r--r--. 1 ohjimin ohjimin  0 Jul 16 17:12 settings.conf
-rw-r--r--. 1 ohjimin ohjimin 16 Jul 16 17:07 test_main.py
drwxr-xr-x. 2 ohjimin ohjimin 38 Jul 16 17:10 user
[ohjimin@localhost project]$ ls -al docs/user
ls: cannot access 'docs/user': No such file or directory
[ohjimin@localhost project]$ pwd
/home/ohjimin/practice/project
```
<b>3. config/ 디렉토리 전체를 backup_config/로 복사하시오.</b>
```
[ohjimin@localhost project]$ cp -r config/ backup_config/
[ohjimin@localhost project]$ ls -al backup_config/
total 4
drwxr-xr-x. 2 ohjimin ohjimin 44 Jul 16 17:21 .
drwxr-xr-x. 7 ohjimin ohjimin 94 Jul 16 17:21 ..
-rw-r--r--. 1 ohjimin ohjimin 23 Jul 16 17:21 config.py
-rw-r--r--. 1 ohjimin ohjimin  0 Jul 16 17:21 settings.conf
[ohjimin@localhost project]$ pwd
/home/ohjimin/practice/project
```
<h3><b>5-2. 조건부 파일 검색</h3></b>
<b>1. 프로젝트 전체에서 .py 확장자를 가진 파일을 모두 찾으시오.</b>

```
[ohjimin@localhost utils]$ find ~/practice/project/ -name *.py
/home/ohjimin/practice/project/src/utils/helper.py
/home/ohjimin/practice/project/docs/dev/helper.py
```

<b>2. docs/ 디렉토리에서 .md 확장자를 가진 파일을 모두 찾으시오. </b>
```
[ohjimin@localhost utils]$ find ~/practice/project/docs/ -name *.md
/home/ohjimin/practice/project/docs/dev/api.md
```
<b>3. 현재 디렉토리에서 상위 2단계 디렉토리까지 .txt 파일을 모두 찾으시오. </b>
```
[ohjimin@localhost utils]$ find ../../ -name *.txt
../../tests/unit/user/manual.txt
```
## 연습문제 6: 에러 찾기 및 수정
<h3><b> 6.1 잘못된 상대 주소 찾기 </h3></b>

<b>A. ls ../../../project/src/main/</b><br>
: ls ../../src/utils/helper.py

<b>B. cat ../../src/utils/helper.py</b><br>
: OK

<b>C. cd ../dev/../../config/ </b><br>
:cd ../dev/../../config/

<b>D. cp manual.txt ../../tests/unit/backup.txt</b><br>
:OK

<b>E. mv api_copy.md ../../../src/main/ </b><br>
:mv api_copy.md ../../src/main
<h3><b> 6.2 경로최적화 </h3></b>
<b> 1. mv api_copy.md ../../../src/main/</b><br>
<b> 2. mv api_copy.md ../../../src/main/ </b><br>
<b> 3. cat ../../README.md </b>

## 연습문제 7: 종합 실습
<h3><b> 7-1. 프로젝트 구조 재정리</h3></b>
<b>1. src/main/ 디렉토리에 models/ 하위 디렉토리를 생성하시오 </b>

```
docs/ 디렉토리에 README.md 파일을 생성하고 "# Project Documentation"이라는 내용을 작성하시오.
```


<b>2. docs/ 디렉토리에 README.md 파일을 생성하고 "# Project Documentation"이라는 내용을 작성하시오.</b>
```
[ohjimin@localhost project]$ echo "# Project Documentation" > ./docs/README.md
[ohjimin@localhost project]$ cat ./docs/README.md 
# Project Documentation
[ohjimin@localhost project]$ pwd
/home/ohjimin/practice/project

```

<b>3.tests/unit/ 디렉토리의 모든 파일을 tests/ 디렉토리로 이동하시오.</b>
```
[ohjimin@localhost main]$ mv ../../tests/unit/* ../../tests/
[ohjimin@localhost main]$ ls -al ../../tests/
total 4
drwxr-xr-x. 3 ohjimin ohjimin  77 Jul 16 18:04 .
drwxr-xr-x. 7 ohjimin ohjimin 102 Jul 16 17:54 ..
-rw-r--r--. 1 ohjimin ohjimin   0 Jul 16 17:42 backip.txt
-rw-r--r--. 1 ohjimin ohjimin   0 Jul 16 17:12 settings.conf
-rw-r--r--. 1 ohjimin ohjimin  16 Jul 16 17:07 test_main.py
drwxr-xr-x. 2 ohjimin ohjimin   6 Jul 16 18:04 unit

```
<b>4. config/ 디렉토리의 모든 파일을 src/ 디렉토리에 복사하시오. </b>
```
[ohjimin@localhost project]$ mv ./config/ ./src/
[ohjimin@localhost project]$ ls ./src/
config  main  utils
[ohjimin@localhost project]$ 

```
<h3><b> 7-1 백업 및 정리 </h3></b>
<b>1. 전체 프로젝트를 ../../project_backup/으로 복사하시오. </b>

```
[ohjimin@localhost main]$ cp -r . ../../project_backup/
```
<b>2. utils/ 디렉토리의 모든 .py 파일을 현재 디렉토리의 models/ 디렉토리로 복사하시오 </b>
```
[ohjimin@localhost main]$ cp -r ../../src/utils/*.py ./models/
[ohjimin@localhost main]$ ls -al ./models/
total 0
drwxr-xr-x. 2 ohjimin ohjimin 23 Jul 16 18:01 .
drwxr-xr-x. 3 ohjimin ohjimin 34 Jul 16 17:48 ..
-rw-r--r--. 1 ohjimin ohjimin  0 Jul 16 18:01 helper.py

```
<b>3. 프로젝트 루트의 README.md 파일을 현재 디렉토리에 PROJECT_INFO.md로 복사하시오.</b>
```
[ohjimin@localhost main]$ cp ../../README.md ./PROJECT_INFO.md
[ohjimin@localhost main]$ ls -al ./
total 0
drwxr-xr-x. 3 ohjimin ohjimin 57 Jul 16 18:03 .
drwxr-xr-x. 5 ohjimin ohjimin 45 Jul 16 17:52 ..
-rw-r--r--. 1 ohjimin ohjimin  0 Jul 16 16:21 app.py
drwxr-xr-x. 2 ohjimin ohjimin 23 Jul 16 18:01 models
-rw-r--r--. 1 ohjimin ohjimin  0 Jul 16 18:03 PROJECT_INFO.md

```


