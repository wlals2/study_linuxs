# Linux 파일 관리 명령어 와일드카드 실습 문제
## 실습 디렉터리 생성
``` bash
mkdir wildcard_file_practice
cd wildcard_file_practice
```
## 테스트 파일들 생성
```bash

touch report1.txt report2.txt report3.txt \
&& touch data1.csv data2.csv data3.csv data_old.csv \
&& touch image1.jpg image2.jpg image3.png photo.gif \
&& touch backup_2023.tar backup_2024.tar config.conf \
&& touch log_error.txt log_access.txt log_system.txt \
&& touch temp1.tmp temp2.tmp temp3.tmp \
&& touch file_001.dat file_002.dat file_010.dat \
&& touch script1.sh script2.sh test_script.sh \
&& touch document.pdf presentation.ppt spreadsheet.xls \
&& touch readme.md changelog.md license.txt \
&& touch old_report.txt new_report.txt final_report.txt
```
## 기본 디렉토리 생성
``` bash
mkdir archives backup logs images documents scripts
```
## 2020년 부터 2024까지 백업 디렉터리 한번에 생성
``` bash
mkdir backup_{2020,2021,2022,2023,2024}
```

##  logs 디렉터리 안에 01월 부터 12월 까지 디렉터리 생성
```bash
mkdir -p ./logs/log_{01,02,03,04,05,06,07,08,09,10,11,12}
```
## project_A, project_B, project_C 디렉터리를 한번에 생성하세요
```bash
mkdir project_{A,B,C}
```
## data/2024/{01,02,03} 구조로 디렉터리 생성
```bash
mkdir -p ./data/2024/{01,02,03}
```
## 모든 .txt 파일을 backup 디렉터리로 복사
``` bash
cp *.txt ./backup/
```
## report로 시작하는 모든 파일을 documents 디렉터리 복사하세요
``` bash
cp report* ./documents/
```
## 파일 명에 숫자가 포함된 모든 이미지 파일 .jpg .png을 images 디렉터리로 복사
``` bash
cp image?.* ./images
```
## data1.csv data2.csv data3.csv 파일만 backup 디렉터리로 복사하세요
``` bash
cp data?.csv ./backup/
```
## logs_ 로 시작하는 .txt 파일들을 logs 디렉터리로 복사하세요
``` bash
cp logs_*.txt ./logs/
```
## 모든 .tmp 파일을 temp 디렉터리로 이동하세요
``` bash
mkdir temp
mv *.tmp ./temp/
```
## backup_로 시작하는 모든 파일을 archives 디렉터리로 이동하세요
```bash
mv backup_* ./archives
```
## 모든 .sh 파일을 scripts 디렉터리로 이동하세요
```bash
mv *.sh ./scripts/
```
## file_로 시작하고 3자리 숫자가 포함된 .data 파일들을 data디렉터리로 이동
``` bash
mv file_???.data ./data/
```
## old_ 또는 new_로 시작하는 모든 파일을 archives 디렉터리로 이동
``` bash
mv {old_,new_}*.txt ./archives/
```
## 모든 .tmp 파일을 삭제하세요
``` bash
rm *.tmp
```
## temp로 시작하는 모든 파일을 삭제하세요
``` bash
rm temp*.tmp
```
## 2023년 백업 파일만 삭제하세요
``` bash
rm backup_2023.tar
```
## 확장자가 3글자가 아닌 파일들을 삭제한다.
``` bash
rm *.??
```
## 모든 이미지파일 .jpg .png .gif
``` bash
mv *.{jpg,png,gif} ./images/
```
## 모든 문서 파일 .pdf .ppt .xls .md
``` bash
mv *.{pdf,ppt,xls,md} ./documents/
```
## 모든 데이터 파일 .csv .dat 을 data 디렉터리로 이동
```bash
mkdir data
mv *.{csv,data} ./data/
```
## 모든 .txt 파일을 backup/txt_files 디렉터리로 복사
```bash
cp *.txt ./backup/txt_files/
```
## 모든 설정 파일을 backup/config 디렉터리로 복사
```bash
cp *.conf ./backup/config/
```
## 원본 설정 파일 삭제 
```bash
rm *.conf 
```
## logs 디렉터리에 error,access,system 하위 디렉터리 생성
``` bash
mkdir ./logs/{error,access,system}
```
## log_error.txt를 logs/error/로 이동
``` bash
mv log_error.txt ./logs/error
```
## log_access.txt 를 logs/access로 이동
```bash
mv log_access.txt ./logs/access
```
## log_system.txt 를 logs/system로 이동
```bash
mv log_system.txt ./logs/system
```
## report , data로 시작하고 숫자가 포함된 모든 파일을 찾아 processed 디렉터리 복사
``` bash
cp {report,data}?.* ./processed
```
## 모든 파일 중에서 final_로 시작하지 않는 .txt 파일들록 draft 디렉터리로 이동하세요
``` bash
mv {report,license}.txt ./draft
```
## 파일명에 001 부터 009까지 숫자가 포함된 파일들을 single_digit디렉터리로 복사하세요
```bash
cp file_{001,002}.dat ./single_digit
```
## 완료된 리포트 파일들 (report*.txt) 을 completed 디렉터리로 이동
``` bash
mv report*.txt ./completed/
```
## 작업중인 파일들 (temp*,*_draft)을 ongoing 디렉터리로 이동
```bash
mkdir ./onging
mv temp* ./ongoing/
```
## 백업 파일들 (backup_*)을 archive 디렉터리로 이동
``` bash
mv backup_* ./archive/
```
## 불필요한 임시파일들 *.tmp 을 삭제
``` bash
rm *.tmp
```
## 2024년 로그 파일들을 logs/2024디렉터리로 이동
```bash
mv backup_2024.tar ./logs/2024/
```

## 에러 로그들을 logs/errors 디렉터리로 복사
```bash
mv logs_error.txt ./logs/errors
```
## 2023년 로그 파일들을 삭제 
```bash
rm backup_2023.tar
```
## 시스템 로그들을 logs/system 디렉터리로 이동
```bash
mv log_system.txt ./logs/system
```
## 모든 스크립트 파일(*.sh)을 scripts 디렉터리로 이동
```bash
mv *.sh ./scripts/
```
## 설정 파일들 (*.conf,*.config)을 config 디렉터리로 이동
```bash
cp *.{conf,config} ./config/
```
## 문서 파일들 (*.md,*.txt)을 docs 디렉터리로 이동
``` bash
mv *.{md.txt} ./docs/
```
## 데이터파일들 (*.csv,*.dat)을 data디렉터리로 이동
```bash
mv *.{csv,dat} ./data/
```
# 모든 이미지 파일들을 images 디렉터리로 이동하고 모든 문서파일 들을 docs 로 디렉터리로 이동 작업 한줄의 명령어로 사용 실행  세미콜론 &&사용
```bash
mv *.{jpg,png,gif} ./images/ && mv *.{docs,md,txt,ppt,sh} ./docs
```
# images 디렉터리가 존재하면 모든 .jpg 파일을 이동하고 존재하지 않으면 디렉터리 생성한 이후 이동하는 명령어를 작성

```bash
mkdir images && mv *.jpg ./images
```
# txt 파일이 5개 이상이면 backup 디렉터리로 복사하고  그렇지 않으면 파일이 부족합니다 . 명령어를 출력
```bash
[ $(ls -1 *.txt 2>/dev/null | wc -l) -gt 5 ] && mkdir -p backup || echo "파일이 부족합니다"
```

## 디렉터리 구조 확인
```bash
ls -al

drwxr-xr-x. 18 ohjimin ohjimin 4096 Jul 18 09:45 .
drwx------. 28 ohjimin ohjimin 4096 Jul 18 09:37 ..
drwxr-xr-x.  7 ohjimin ohjimin  191 Jul 18 09:45 archives
drwxr-xr-x.  2 ohjimin ohjimin 4096 Jul 18 09:45 backup
drwxr-xr-x.  3 ohjimin ohjimin  149 Jul 18 09:45 data
drwxr-xr-x.  2 ohjimin ohjimin  130 Jul 18 09:45 documents
drwxr-xr-x.  2 ohjimin ohjimin   25 Jul 18 09:45 draft
-rw-r--r--.  1 ohjimin ohjimin    0 Jul 18 09:45 final_report.txt
drwxr-xr-x.  2 ohjimin ohjimin   77 Jul 18 09:45 images
drwxr-xr-x. 17 ohjimin ohjimin 4096 Jul 18 09:45 logs
drwxr-xr-x.  2 ohjimin ohjimin    6 Jul 18 09:45 onging
drwxr-xr-x.  2 ohjimin ohjimin   57 Jul 18 09:45 ongoing
drwxr-xr-x.  2 ohjimin ohjimin  114 Jul 17 18:26 processed
drwxr-xr-x.  2 ohjimin ohjimin    6 Jul 18 09:45 project_A
drwxr-xr-x.  2 ohjimin ohjimin    6 Jul 18 09:45 project_B
drwxr-xr-x.  2 ohjimin ohjimin    6 Jul 18 09:45 project_C
-rw-r--r--.  1 ohjimin ohjimin    0 Jul 18 09:45 report1.txt
-rw-r--r--.  1 ohjimin ohjimin    0 Jul 18 09:45 report2.txt
-rw-r--r--.  1 ohjimin ohjimin    0 Jul 18 09:45 report3.txt
drwxr-xr-x.  2 ohjimin ohjimin   64 Jul 18 09:45 scripts
drwxr-xr-x.  2 ohjimin ohjimin   46 Jul 17 18:41 single_digit
drwxr-xr-x.  8 ohjimin ohjimin  129 Jul 17 17:46 test
```
## 특정 디렉터리 내용 확인
```bash
ls -al backip/
ls -al images/
ls -al documents/

[ohjimin@localhost wildcard_file_practice]$ ls -al backup && ls -al images/ && ls -al documents/ 
total 8
drwxr-xr-x.  2 ohjimin ohjimin 4096 Jul 18 09:45 .
drwxr-xr-x. 18 ohjimin ohjimin 4096 Jul 18 09:45 ..
-rw-r--r--.  1 ohjimin ohjimin    0 Jul 18 09:45 data1.csv
-rw-r--r--.  1 ohjimin ohjimin    0 Jul 18 09:45 data2.csv
-rw-r--r--.  1 ohjimin ohjimin    0 Jul 18 09:45 data3.csv
-rw-r--r--.  1 ohjimin ohjimin    0 Jul 18 09:45 final_report.txt
-rw-r--r--.  1 ohjimin ohjimin    0 Jul 18 09:45 license.txt
-rw-r--r--.  1 ohjimin ohjimin    0 Jul 18 09:45 log_access.txt
-rw-r--r--.  1 ohjimin ohjimin    0 Jul 18 09:45 log_error.txt
-rw-r--r--.  1 ohjimin ohjimin    0 Jul 18 09:45 log_system.txt
-rw-r--r--.  1 ohjimin ohjimin    0 Jul 18 09:45 new_report.txt
-rw-r--r--.  1 ohjimin ohjimin    0 Jul 18 09:45 old_report.txt
-rw-r--r--.  1 ohjimin ohjimin    0 Jul 18 09:45 report1.txt
-rw-r--r--.  1 ohjimin ohjimin    0 Jul 18 09:45 report2.txt
-rw-r--r--.  1 ohjimin ohjimin    0 Jul 18 09:45 report3.txt
total 4
drwxr-xr-x.  2 ohjimin ohjimin   77 Jul 18 09:45 .
drwxr-xr-x. 18 ohjimin ohjimin 4096 Jul 18 09:45 ..
-rw-r--r--.  1 ohjimin ohjimin    0 Jul 18 09:45 image1.jpg
-rw-r--r--.  1 ohjimin ohjimin    0 Jul 18 09:45 image2.jpg
-rw-r--r--.  1 ohjimin ohjimin    0 Jul 18 09:45 image3.png
-rw-r--r--.  1 ohjimin ohjimin    0 Jul 18 09:45 photo.gif
total 4
drwxr-xr-x.  2 ohjimin ohjimin  130 Jul 18 09:45 .
drwxr-xr-x. 18 ohjimin ohjimin 4096 Jul 18 09:45 ..
-rw-r--r--.  1 ohjimin ohjimin    0 Jul 18 09:45 document.pdf
-rw-r--r--.  1 ohjimin ohjimin    0 Jul 18 09:45 presentation.ppt
-rw-r--r--.  1 ohjimin ohjimin    0 Jul 18 09:45 report1.txt
-rw-r--r--.  1 ohjimin ohjimin    0 Jul 18 09:45 report2.txt
-rw-r--r--.  1 ohjimin ohjimin    0 Jul 18 09:45 report3.txt
-rw-r--r--.  1 ohjimin ohjimin    0 Jul 18 09:45 spreadsheet.xls
```
## 파일 개수 확인 ls *.txt | wc -l / ls *.jpg | wc -l
```bash
[ohjimin@localhost wildcard_file_practice]$ ls *.txt | wc -l
4
[ohjimin@localhost wildcard_file_practice]$ ls *.jpg | wc -l
ls: cannot access '*.jpg': No such file or directory
0
```
## 전체 파일 목록 확인
``` bash
[ohjimin@localhost wildcard_file_practice]$ find . -type f | sort
./archives/backup_2023.tar
./archives/backup_2024.tar
./archives/new_report.txt
./archives/old_report.txt
./backup/data1.csv
./backup/data2.csv
./backup/data3.csv
./backup/final_report.txt
./backup/license.txt
./backup/log_access.txt
./backup/log_error.txt
./backup/log_system.txt
./backup/new_report.txt
./backup/old_report.txt
./backup/report1.txt
./backup/report2.txt
./backup/report3.txt
./data/data1.csv
./data/data2.csv
./data/data3.csv
./data/data_old.csv
./data/file_001.dat
./data/file_002.dat
./data/file_010.dat
./documents/document.pdf
./documents/presentation.ppt
./documents/report1.txt
./documents/report2.txt
./documents/report3.txt
./documents/spreadsheet.xls
./draft/license.txt
./final_report.txt
./images/image1.jpg
./images/image2.jpg
./images/image3.png
./images/photo.gif
./logs/access/log_access.txt
./logs/error/log_error.txt
./logs/system/log_system.txt
./ongoing/temp1.tmp
./ongoing/temp2.tmp
./ongoing/temp3.tmp
./processed/data1.csv
./processed/data2.csv
./processed/data3.csv
./processed/report1.txt
./processed/report2.txt
./processed/report3.txt
./report1.txt
./report2.txt
./report3.txt
./scripts/script1.sh
./scripts/script2.sh
./scripts/test_script.sh
./single_digit/file_001.dat
./single_digit/file_002.dat
./test/backup/test1.txt
./test/backup/test2.txt
./test/test1.txt
./test/test2.txt
```
## 실제 명령 실행 전에 패턴이 올바른지 확인
```
echo cp *.txt backup/    # 실제로는 실행되지 않고 명령어만 출력

ls *.txt                 # 선택될 파일들 미리 확인

힌트
{} 중괄호 확장 활용: mkdir {dir1,dir2,dir3}
[] 문자 범위 활용: [1-3], [a-z]

- 와일드카드 활용: file*, *.txt
? 단일 문자 활용: file?.txt
복합 패턴 활용: *[0-9]*, file[1-3].txt
디렉터리 생성 시 -p 옵션 활용: mkdir -p path/to/directory
```
## 전체 명령어 정리
``` bash
touch report1.txt report2.txt report3.txt \
&& touch data1.csv data2.csv data3.csv data_old.csv \
&& touch image1.jpg image2.jpg image3.png photo.gif \
&& touch backup_2023.tar backup_2024.tar config.conf \
&& touch log_error.txt log_access.txt log_system.txt \
&& touch temp1.tmp temp2.tmp temp3.tmp \
&& touch file_001.dat file_002.dat file_010.dat \
&& touch script1.sh script2.sh test_script.sh \
&& touch document.pdf presentation.ppt spreadsheet.xls \
&& touch readme.md changelog.md license.txt \
&& touch old_report.txt new_report.txt final_report.txt

mkdir archives backup logs images documents scripts

mkdir backup_{2020,2021,2022,2023,2024}

mkdir -p ./logs/log_{01,02,03,04,05,06,07,08,09,10,11,12}

mkdir project_{A,B,C}

mkdir -p ./data/2024/{01,02,03}

cp *.txt ./backup/

cp report* ./documents/

cp image?.* ./images

cp data?.csv ./backup/

cp logs_*.txt ./logs/

mkdir temp
mv *.tmp ./temp/

mv backup_* ./archives

mv *.sh ./scripts/

mv file_???.data ./data/

mv {old_,new_}*.txt ./archives/

rm *.tmp

rm temp*.tmp

rm backup_2023.tar

rm *.??

mv *.{jpg,png,gif} ./images/

mv *.{pdf,ppt,xls,md} ./documents/

mkdir data
mv *.{csv,data} ./data/

cp *.txt ./backup/txt_files/

cp *.conf ./backup/config/

rm *.conf 

mkdir ./logs/{error,access,system}

mv log_error.txt ./logs/error

mv log_access.txt ./logs/access

mv log_system.txt ./logs/system

cp {report,data}?.* ./processed

mv {report,license}.txt ./draft

cp file_{001,002}.dat ./single_digit

mv report*.txt ./completed/

mkdir ./onging
mv temp* ./ongoing/

mv backup_* ./archive/

rm *.tmp

mv backup_2024.tar ./logs/2024/

mv logs_error.txt ./logs/errors

rm backup_2023.tar

mv log_system.txt ./logs/system

mv *.sh ./scripts/

cp *.{conf,config} ./config/

mv *.{md.txt} ./docs/

mv *.{csv,dat} ./data/

mv *.{jpg,png,gif} ./images/ && mv *.{docs,md,txt,ppt,sh} ./docs

mkdir images && mv *.jpg ./images

[ $(ls -1 *.txt 2>/dev/null | wc -l) -gt 5 ] && mkdir -p backup || echo "파일이 부족합니다"

ls -al
```