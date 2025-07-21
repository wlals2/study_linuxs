# **Linux 권한 관리 실습 문제**

## **실습 환경 설정**

**먼저 다음 명령어들을 실행하여 실습 환경을 구성하세요:**

- # 실습 디렉터리 생성(/root 사용)
- mkdir permission_practice
- cd permission_practice
- 
- # 사용자 및 그룹 생성 (관리자 권한 필요)
- sudo useradd -m -s /bin/bash alice
- sudo useradd -m -s /bin/bash bob
- sudo useradd -m -s /bin/bash charlie
- sudo useradd -m -s /bin/bash diana
- sudo useradd -m -s /bin/bash eve
- 
- # 그룹 생성
- sudo groupadd developers
- sudo groupadd managers
- 
- # 사용자를 그룹에 추가
- sudo usermod -a -G developers alice
- sudo usermod -a -G developers bob
- sudo usermod -a -G developers charlie
- sudo usermod -a -G managers diana
- sudo usermod -a -G managers alice
- # eve는 기타 사용자로 어떤 그룹에도 속하지 않음
- 
- # 복잡한 디렉터리 구조 생성
- mkdir -p {company/{departments/{dev,hr,finance,marketing},projects/{project_a,project_b,project_c}},shared/{documents,resources,tools},private/{alice,bob,charlie,diana,eve},backup/{daily,weekly,monthly},logs/{2023/{01..12},2024/{01..12}}}
- 
- # 다양한 파일 생성
- touch company/departments/dev/{main.py,test.py,config.py,README.md}
- touch company/departments/hr/{employees.xlsx,contracts.pdf,policies.txt}
- touch company/departments/finance/{budget.xlsx,reports.pdf,invoices.csv}
- touch company/projects/project_a/{spec.doc,code.zip,data.json}
- touch company/projects/project_b/{requirements.txt,source.tar.gz,notes.md}
- touch shared/documents/{manual.pdf,guidelines.txt,templates.docx}
- touch shared/resources/{images.zip,fonts.tar,icons.png}
- touch private/alice/{personal.txt,settings.conf,backup.tar}
- touch private/bob/{notes.md,config.json,archive.zip}
- touch backup/daily/{backup_$(date +%Y%m%d).tar.gz,log_$(date +%Y%m%d).txt}
- touch logs/2024/06/{access.log,error.log,debug.log,system.log}
- 
- # 실행 가능한 스크립트 파일 생성
- echo '#!/bin/bash' > shared/tools/deploy.sh
- echo 'echo "Deployment script"' >> shared/tools/deploy.sh
- echo '#!/bin/bash' > shared/tools/backup.sh
- echo 'echo "Backup script"' >> shared/tools/backup.sh
- echo '#!/bin/bash' > company/departments/dev/build.sh
- echo 'echo "Build script"' >> company/departments/dev/build.sh
- 
- # 설정 파일 생성
- echo "database_host=localhost" > company/departments/dev/database.conf
- echo "api_key=secret123" > company/departments/dev/api.conf
- echo "salary_data=confidential" > company/departments/hr/salaries.txt
- 
- echo "실습 환경이 구성되었습니다!"
- tree permission_practice

## 명령문 총정리
```bash
mkdir permission_practice
cd permission_practice

sudo useradd -m -s /bin/bash alice
sudo useradd -m -s /bin/bash bob
sudo useradd -m -s /bin/bash charlie
sudo useradd -m -s /bin/bash diana
sudo useradd -m -s /bin/bash eve

sudo groupadd developers
sudo groupadd managers

sudo usermod -a -G developers alice
sudo usermod -a -G developers bob
sudo usermod -a -G developers charlie
sudo usermod -a -G managers diana
sudo usermod -a -G managers alice

mkdir -p company/departments/{dev,hr,finance,marketing}
mkdir -p company/projects/{project_a,project_b,project_c}
mkdir -p shared/{documents,resources,tools}
mkdir -p private/{alice,bob,charlie,diana,eve}
mkdir -p backup/{daily,weekly,monthly}
mkdir -p logs/2023/{01..12}
mkdir -p logs/2024/{01..12}

touch company/departments/dev/{main.py,test.py,config.py,README.md}
touch company/departments/hr/{employees.xlsx,contracts.pdf,policies.txt}
touch company/departments/finance/{budget.xlsx,reports.pdf,invoices.csv}
touch company/projects/project_a/{spec.doc,code.zip,data.json}
touch company/projects/project_b/{requirements.txt,source.tar.gz,notes.md}
touch shared/documents/{manual.pdf,guidelines.txt,templates.docx}
touch shared/resources/{images.zip,fonts.tar,icons.png}
touch private/alice/{personal.txt,settings.conf,backup.tar}
touch private/bob/{notes.md,config.json,archive.zip}
touch backup/daily/backup_$(date +%Y%m%d).tar.gz
touch backup/daily/log_$(date +%Y%m%d).txt
touch logs/2024/06/{access.log,error.log,debug.log,system.log}

echo '#!/bin/bash' > shared/tools/deploy.sh
echo 'echo "Deployment script"' >> shared/tools/deploy.sh
echo '#!/bin/bash' > shared/tools/backup.sh
echo 'echo "Backup script"' >> shared/tools/backup.sh
echo '#!/bin/bash' > company/departments/dev/build.sh
echo 'echo "Build script"' >> company/departments/dev/build.sh

echo "database_host=localhost" > company/departments/dev/database.conf
echo "api_key=secret123" > company/departments/dev/api.conf
echo "salary_data=confidential" > company/departments/hr/salaries.txt

echo "실습 환경이 구성되었습니다!"
tree permission_practice
```
## 1. 기본 권한 설정
### 1-1. 개발팀 파일 권한 설정
- 개발팀(developers 그룹) 관련 파일들의 권한을 다음과 같이 설정하세요:
- 1. company/departments/dev/ 디렉터리: 개발팀만 접근 가능, 소유자와 그룹은 읽기/쓰기/실행 가능
- 2. company/departments/dev/main.py: 개발팀은 읽기/쓰기, 기타는 읽기만 가능
- 3. company/departments/dev/build.sh: 개발팀만 실행 가능
명령어를 작성하세요:
### 1-1 답안 작성란
```bash
1. sudo chgrp developers .
2. chmod 064 company/departments/dev/main.py
3. chmod 010 company/departments/dev/build.sh
```
---
### **1-2. 개인 디렉터리 보안 설정**

각 사용자의 개인 디렉터리와 파일을 다음과 같이 설정하세요:

- private/alice/ 디렉터리: alice만 접근 가능
- private/alice/personal.txt: alice만 읽기/쓰기 가능
- private/bob/config.json: bob만 읽기/쓰기 가능


###  1-2 답안 작성란
``` bash
1. sudo chown -R alice private/alice/ && chmod -R 700 private/alice/
2. sudo chmod 600 private/alice/personal.txt
3. sudo chown bob private/bob/config.josn && sudo chmod 600 private/bob/config.json
```

## **2. 그룹 기반 권한 관리**

### **2-1. 공유 리소스 접근 권한**

shared/ 디렉터리의 권한을 다음과 같이 설정하세요:

- shared/documents/: developers와 managers 그룹 모두 읽기 가능, 소유자만 쓰기 가능
- shared/resources/: developers 그룹만 접근 가능
- shared/tools/: 모든 사용자가 읽기 가능, developers 그룹만 실행 가능



### 2-1 답안 작성란
```bash
#sudo setfacl -m g:developers:r shared/documents/
#sudo setfacl -m g:managers:r shared/documents/
#sudo chown developers shared/documents/
#chmod 240 -r shared/documents 
#sudo setfacl -m g:managers:r shared/documents/
```
```bash
sudo chown :developers shared/resources/
sudo chmod 070 shared/resources/
```
```bash
sudo chown :developers shared/tools/
sudo chmod 454 shared/tools/
```
 
---
### **2-2. 프로젝트별 협업 권한**

프로젝트 디렉터리의 권한을 다음과 같이 설정하세요:

- company/projects/project_a/: developers 그룹 구성원들이 협업할 수 있도록 설정
- company/projects/project_b/: alice와 bob만 접근 가능하도록 설정


### 2-2 답안 작성란
```bash
sudo chown -R :developers company/projects/project_a/
sudo chmod -R 070 company/projects/project_a/
```
```bash
sudo groupadd projectb
sudo usermod -a G projectb alice,bob

sudo chown :projectb company/projects/project_b/
sudo chmod 070 company/projects/project_b/
```

# **3. 고급 권한 설정**

### **3-1. 특수 권한 적용**

다음 파일들에 특수 권한을 설정하세요:

- shared/tools/deploy.sh: SetGID 설정으로 developers 그룹 권한으로 실행
- company/departments/hr/salaries.txt: SetUID 설정 (실제 환경에서는 권장하지 않지만 실습용)


### 3-1 답안 작성란
 ```bash
sudo chown -R :developers shared/tools/
sudo chmod g+s shared/tools/
 ```

```bash
sudo chmod u+s company/depratments/hr/salaries.txt
```
---
### 3-2. 숫자 표기법으로 복합 권한 설정

다음 파일들의 권한을 숫자 표기법으로 설정하세요:

- company/departments/finance/budget.xlsx: 소유자(rw-), 그룹(r--), 기타(---)
- shared/documents/manual.pdf: 소유자(rw-), 그룹(r--), 기타(r--)
- logs/2024/06/system.log: 소유자(rw-), 그룹(r--), 기타(---)

### 3-2 답안 작성란
```bash
sudo chmod 640 company/departments/finance/budget.xlsx
```
```bash
sudo chmod 644 shared/documents/manual.pdf
```
```bash
sudo chmod 640 logs/2024/06/system.log
```
## **4. 소유권 및 그룹 관리**

### **4-1. 소유권 변경**

다음과 같이 파일과 디렉터리의 소유권을 변경하세요:

- company/departments/dev/ 디렉터리와 모든 하위 파일: alice 소유, developers 그룹
- company/departments/hr/ 디렉터리와 모든 하위 파일: diana 소유, managers 그룹
- shared/tools/ 디렉터리와 모든 하위 파일: root 소유, developers 그룹


---
- ### 4-1 답안 작성란
```bash
sudo chown -R alice:developers company/departments/dev/
```
```bash
sudo chown -R diana:managers company/departments/hr/
```
```bash
sudo chown -R root:developers shared/tools/
```
---
### **4-2. 그룹 전용 변경**

다음 디렉터리들의 그룹만 변경하세요:

- company/projects/: managers 그룹으로 변경
- backup/daily/: developers 그룹으로 변경

**명령어를 작성하세요:**

 ### 4-2 답안 작성란
 ```bash
 sudo chown :managers compnay/projects/
 ```
 ```bash
 sudo chown :developers backup/daily
 ```
## **6. umask 및 기본 권한 관리**

### **6-1. umask 설정 및 테스트**

현재 시스템의 umask 값을 확인하고 다음과 같이 변경한 후 테스트하세요:

- umask 값을 027로 설정
- 새 파일과 디렉터리를 생성하여 기본 권한 확인
- 원래 umask 값으로 복원

### 6-1 답안 작성란
```bash
umask 027
touch test1 && mkdir test2
ls -al test1 test2
# /etc/login.defs umask 설정 값 확인
umask 0022
```
### **6-2. 사용자별 umask 커스터마이징**

각 사용자별로 다른 umask 값을 설정하세요:

- alice: umask 022 (일반적인 개발자 설정)
- diana: umask 077 (보안 강화 설정)
- eve: umask 002 (그룹 협업 친화적 설정)

 ### 6-2 답안 작성란 
 ```bash
 sudo echo 'umask 022' >> /home/alice/.bashrc
 source /home/alice/.bashrc

 sudo echo 'umask 077' >> /home/diana/.bashrc
 source /home/diana/.bashrc

 sudo echo 'umask 002' >> /home/eve/.bashrc
 source /home/eve/.bashrc
 ```

### **8-1. 스크립트 실행 환경 설정**

다음 스크립트 파일들의 실행 권한을 적절히 설정하세요:

- shared/tools/deploy.sh: developers 그룹만 실행 가능
- shared/tools/backup.sh: alice와 diana만 실행 가능
- company/departments/dev/build.sh: 소유자만 실행 가능


### 8-1 답안 작성란
---
```bash
sudo chown shared/tools/deploy.sh && chmod 050 shared/tools/deploy.sh
```
```bash
sudo groupadd alice_diana
sudo usermod -aG alice_diana alice 
sudo usermod -aG alice_diana diana
sudo chown :alice_diana shared/tools/backup.sh
sudo chmod 050 shared/tools/backup.sh
```
```bash
sudo chmod 500 company/departments/dev/build.sh
```
### **8-2. 시스템 스크립트 보안 설정**

시스템 관리용 스크립트를 다음과 같이 설정하세요:

- root 소유의 시스템 관리 스크립트 생성 (system_check.sh)
- 일반 사용자가 sudo 없이 실행할 수 있도록 SetUID 설정
- 실행 로그를 남기도록 권한 설정

 ### 8-2 답안 작성란
---
```bash
#리눅스 보안상 set uid는 스크립트 코딩 언어에는 사용할 수 없음 사용할거라면 바이너리 파일에만 가능
touch system_check.sh
sudo chown root:root system_check.sh
sudo chmod 4700 system_check.sh
# 여기서 권한을 주면 사용할 수 있지만 set uid를 해도 실행 되지는 않음
# 실제로 실행을 할거라면 
sudo chmod 4705 system_check.sh
sh system_check.sh 

cat system_check.sh
#!/bin/bash
logger -t system_check "실행됨: $(whoami) at $(date)"
echo "시스템 점검 실행!"
```
## **9. 디렉터리별 접근 제어**

### **9-1. 계층적 접근 제어**

다음과 같은 계층적 접근 권한을 설정하세요:

- company/ : 모든 직원이 읽기 가능
- company/departments/ : 각 부서원만 해당 부서 디렉터리 접근 가능
- company/departments/finance/ : managers 그룹만 접근 가능
- company/projects/ : 프로젝트 참여자만 해당 프로젝트 접근 가능

**명령어를 작성하세요:**

### 9-1 답안 작성란
---
```bash
sudo chmod 777 company
```
```bash
sudo chmod 770 company/departments
```
```bash
sudo chgrp :managers compnay/departmets/finance
```
```bash
sudo groupadd project
sudo chgrp :project company/projects
```


### **9-2. 임시 작업 공간 설정**

임시 작업을 위한 공간을 다음과 같이 설정하세요:

- temp/ 디렉터리 생성 (모든 사용자가 파일 생성 가능)
- Sticky Bit 설정으로 자신의 파일만 삭제 가능
- 1주일 후 자동 삭제되도록 권한 설정 (cron 작업용)

---
### 9-2 답안 작성란
```bash
mkdir temp
sudo chmod 1777 temp
crontab -e
0 1 * * * root find /path/to/temp -type f -mtime +6 -exec rm -f {} \;
```

## **10. 백업 및 아카이브 권한 관리**

### **10-1. 백업 파일 보안**

백업 관련 파일들의 보안을 다음과 같이 설정하세요:

- backup/daily/ : developers 그룹이 백업 생성 가능, 읽기 전용
- backup/weekly/ : managers만 접근 가능
- backup/monthly/ : root만 접근 가능
- 모든 백업 파일은 생성 후 읽기 전용으로 자동 변경

### 10-1 답안 작성란
---
- **root 권한을 없다하더라도 sudo 를 사용하면 chmod를 사용할 수 있다.**
```bash
# 백업 폴더로서 지속된 백업파일이 만들어질 것을 고려해 디렉터리에 set gid를 주어 생성된 파일들을 그룹을 통일 시켜준다.
sudo chown -R root:developers backup/daily
sudo chmod 2474 backup/daily
```
```bash
# 백업 폴더로서 지속된 백업파일이 만들어질 것을 고려해 디렉터리에 set gid를 주어 생성된 파일들을 그룹을 통일 시켜준다.
sudo chown -R root:managers backup/weekly
sudo chmod 2470 backup/weekly
```

``` bash
sudo chown -R root:root backup/monthly
sudo chmod 700 backup/monthly
```
