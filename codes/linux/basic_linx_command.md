# 📁Level 1: 기본 탐색 및 폴더 조작

```
PS C:\Develops\Quest> mkdir powershell_pratice


    디렉터리: C:\Develops\Quest


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2025-07-15   오후 3:36                powershell_pratice


PS C:\Develops\Quest> cd .\powershell_pratice\
PS C:\Develops\Quest\powershell_pratice> mkdir documents/


    디렉터리: C:\Develops\Quest\powershell_pratice


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2025-07-15   오후 3:36                documents


PS C:\Develops\Quest\powershell_pratice> mkdir images/


    디렉터리: C:\Develops\Quest\powershell_pratice


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2025-07-15   오후 3:36                images


PS C:\Develops\Quest\powershell_pratice> mkdir backup/


    디렉터리: C:\Develops\Quest\powershell_pratice


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2025-07-15   오후 3:36                backup


PS C:\Develops\Quest\powershell_pratice> mkdir temp/


    디렉터리: C:\Develops\Quest\powershell_pratice


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2025-07-15   오후 3:36                temp


PS C:\Develops\Quest\powershell_pratice> cd .\documents\
PS C:\Develops\Quest\powershell_pratice\documents> ls
PS C:\Develops\Quest\powershell_pratice\documents> cd C:\Develops\Quest\
PS C:\Develops\Quest> cd .\powershell_pratice\
```
# 📄 Level 2: 파일 생성 및 조작
```
PS C:\Develops\Quest\powershell_pratice> "Hello PowerShell" > hello.txt
PS C:\Develops\Quest\powershell_pratice> mv .\hello.txt .\documents\
PS C:\Develops\Quest\powershell_pratice> "" > photo1.jpg
PS C:\Develops\Quest\powershell_pratice> "" > photo2.jpg
PS C:\Develops\Quest\powershell_pratice> cat .\documents\hello.txt
Hello PowerShell
PS C:\Develops\Quest\powershell_pratice> ls


    디렉터리: C:\Develops\Quest\powershell_pratice


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2025-07-15   오후 3:36                backup
d-----      2025-07-15   오후 3:38                documents
d-----      2025-07-15   오후 3:36                images
d-----      2025-07-15   오후 3:36                temp
-a----      2025-07-15   오후 3:39              6 photo1.jpg
-a----      2025-07-15   오후 3:39              6 photo2.jpg


PS C:\Develops\Quest\powershell_pratice> cp .\documents\hello.txt .\backup\
PS C:\Develops\Quest\powershell_pratice> cp .\images\^C
PS C:\Develops\Quest\powershell_pratice> mv .\photo1.jpg .\images\
PS C:\Develops\Quest\powershell_pratice> mv .\photo2.jpg .\backup\
PS C:\Develops\Quest\powershell_pratice> cp .\images\photo* .\backup\
```
# 🔄 Level 3: 파일 이동 및 이름 변경
```
PS C:\Develops\Quest\powershell_pratice> "" > .\temp\test.txt
PS C:\Develops\Quest\powershell_pratice> mv .\temp\test.txt .\documents\
PS C:\Develops\Quest\powershell_pratice> mv .\documents\test.txt .\documents\moved_file.txt
PS C:\Develops\Quest\powershell_pratice> mv .\images\photo1.jpg .\images\picture1.jpg
PS C:\Develops\Quest\powershell_pratice> mv .\temp\ \temporary
PS C:\Develops\Quest\powershell_pratice> ls


    디렉터리: C:\Develops\Quest\powershell_pratice


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2025-07-15   오후 3:40                backup
d-----      2025-07-15   오후 3:42                documents
d-----      2025-07-15   오후 3:43                images


PS C:\Develops\Quest\powershell_pratice> ls C:\temporary\ .\temporary
PS C:\Develops\Quest\powershell_pratice> ls


    디렉터리: C:\Develops\Quest\powershell_pratice


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2025-07-15   오후 3:40                backup
d-----      2025-07-15   오후 3:42                documents
d-----      2025-07-15   오후 3:43                images


PS C:\Develops\Quest\powershell_pratice> ls C:\temporary .\temporary
PS C:\Develops\Quest\powershell_pratice> ls


    디렉터리: C:\Develops\Quest\powershell_pratice


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2025-07-15   오후 3:40                backup
d-----      2025-07-15   오후 3:42                documents
d-----      2025-07-15   오후 3:43                images


PS C:\Develops\Quest\powershell_pratice> mv C:\temporary .\temporary
```
# 🗑️ Level 4: 삭제연습
```
PS C:\Develops\Quest\powershell_pratice> ls


    디렉터리: C:\Develops\Quest\powershell_pratice


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2025-07-15   오후 3:40                backup
d-----      2025-07-15   오후 3:42                documents
d-----      2025-07-15   오후 3:43                images
d-----      2025-07-15   오후 3:42                temporary


PS C:\Develops\Quest\powershell_pratice> rm .\documents\moved_file.txt
PS C:\Develops\Quest\powershell_pratice> "" > .\images\photh2.jpg
PS C:\Develops\Quest\powershell_pratice> "" > .\images\photo2.jpg
PS C:\Develops\Quest\powershell_pratice> rm .\images\photh2.jpg
PS C:\Develops\Quest\powershell_pratice> rm .\images\photo2.jpg
PS C:\Develops\Quest\powershell_pratice> rm .\temporary\
PS C:\Develops\Quest\powershell_pratice> rm .\backup

확인
C:\Develops\Quest\powershell_pratice\backup의 항목에는 하위 항목이 있으며 Recurse 매개 변수를 지정하지 않았습니다.
계속하면 해당 항목과 모든 하위 항목이 제거됩니다. 계속하시겠습니까?
[Y] 예(Y)  [A] 모두 예(A)  [N] 아니요(N)  [L] 모두 아니요(L)  [S] 일시 중단(S)  [?] 도움말 (기본값은 "Y"): Y
PS C:\Develops\Quest\powershell_pratice>
PS C:\Develops\Quest\powershell_pratice>
```
# 🚀 Level 5: 종합 응용
```
PS C:\Develops\Quest\powershell_pratice> mkdir my_project


    디렉터리: C:\Develops\Quest\powershell_pratice


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2025-07-15   오후 3:48                my_project


PS C:\Develops\Quest\powershell_pratice> cd .\my_project\
PS C:\Develops\Quest\powershell_pratice\my_project> mkdir src


    디렉터리: C:\Develops\Quest\powershell_pratice\my_project


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2025-07-15   오후 3:48                src


PS C:\Develops\Quest\powershell_pratice\my_project> mkdir docs


    디렉터리: C:\Develops\Quest\powershell_pratice\my_project


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2025-07-15   오후 3:48                docs


PS C:\Develops\Quest\powershell_pratice\my_project> mkdir tests


    디렉터리: C:\Develops\Quest\powershell_pratice\my_project


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2025-07-15   오후 3:48                tests


PS C:\Develops\Quest\powershell_pratice\my_project> mkdir build


    디렉터리: C:\Develops\Quest\powershell_pratice\my_project


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2025-07-15   오후 3:48                build


PS C:\Develops\Quest\powershell_pratice\my_project> cd .\src\


PS C:\Develops\Quest\powershell_pratice\my_project\src> echo ""print('Hello World')"" main.py

print
Hello World

main.py
PS C:\Develops\Quest\powershell_pratice\my_project\src> ls
PS C:\Develops\Quest\powershell_pratice\my_project\src> echo ""print('Hello World')"" > main.py
PS C:\Develops\Quest\powershell_pratice\my_project\src> cat .\main.py

print
Hello World

PS C:\Develops\Quest\powershell_pratice\my_project\src> echo `"print('Hello World')` > main.py
PS C:\Develops\Quest\powershell_pratice\my_project\src> cat .\main.py
"print
Hello World
PS C:\Develops\Quest\powershell_pratice\my_project\src> echo `"print('Hello World')"
>> ` > main.py^C
PS C:\Develops\Quest\powershell_pratice\my_project\src> echo `"print('Hello World')`" > main.py
PS C:\Develops\Quest\powershell_pratice\my_project\src> cat .\main.py
"print
Hello World
"
PS C:\Develops\Quest\powershell_pratice\my_project\src> "print('Hello World')" > hello.py
PS C:\Develops\Quest\powershell_pratice\my_project\src>
PS C:\Develops\Quest\powershell_pratice\my_project\src> cat .\hello.py
print('Hello World')
PS C:\Develops\Quest\powershell_pratice\my_project\src> "This is my project" > C:\Develops\Quest\powershell_pratice\my_project\docs\readme.txt
PS C:\Develops\Quest\powershell_pratice\my_project\src> cat C:\Develops\Quest\powershell_pratice\my_project\docs\readme.txt
This is my project
PS C:\Develops\Quest\powershell_pratice\my_project\src> cat .\hello.py
print('Hello World')
PS C:\Develops\Quest\powershell_pratice\my_project\src> echo ^"print('Hello World')^" > hello.py
PS C:\Develops\Quest\powershell_pratice\my_project\src> cat .\hello.py
^print('Hello World')^
PS C:\Develops\Quest\powershell_pratice\my_project\src> ' "print(''Hello World'')" ' > hello.py
PS C:\Develops\Quest\powershell_pratice\my_project\src> cat .\hello.py
 "print('Hello World')"
PS C:\Develops\Quest\powershell_pratice\my_project\src> ' "This is my project" ' > C:\Develops\Quest\powershell_pratice\my_project\docs\readme.txt
PS C:\Develops\Quest\powershell_pratice\my_project\src> cat C:\Develops\Quest\powershell_pratice\my_project\docs\readme.txt
 "This is my project"
PS C:\Develops\Quest\powershell_pratice\my_project\src> '"This is my project"' > C:\Develops\Quest\powershell_pratice\my_project\docs\readme.txt
PS C:\Develops\Quest\powershell_pratice\my_project\src> cat C:\Develops\Quest\powershell_pratice\my_project\docs\readme.txt
"This is my project"
PS C:\Develops\Quest\powershell_pratice\my_project\src> cp .\main.py 'C:\Develops\Quest\powershell_pratice\my_project\build\'
PS C:\Develops\Quest\powershell_pratice\my_project\src> cd ..
PS C:\Develops\Quest\powershell_pratice\my_project> cd .\docs\
PS C:\Develops\Quest\powershell_pratice\my_project\docs> mv .\readme.txt proejct_info.txt
PS C:\Develops\Quest\powershell_pratice\my_project\docs> ls


    디렉터리: C:\Develops\Quest\powershell_pratice\my_project\docs


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----      2025-07-15   오후 3:56             46 proejct_info.txt


PS C:\Develops\Quest\powershell_pratice\my_project\docs> cd ..
PS C:\Develops\Quest\powershell_pratice\my_project> ls


    디렉터리: C:\Develops\Quest\powershell_pratice\my_project


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2025-07-15   오후 3:48                build
d-----      2025-07-15   오후 3:57                docs
d-----      2025-07-15   오후 3:52                src
d-----      2025-07-15   오후 3:48                tests


PS C:\Develops\Quest\powershell_pratice\my_project> rm .\tests\
PS C:\Develops\Quest\powershell_pratice\my_project> tree
폴더 PATH의 목록입니다.
볼륨 일련 번호는 52B6-33C5입니다.
C:.
├─build
├─docs
└─src
PS C:\Develops\Quest\powershell_pratice\my_project> cat .\docs\proejct_info.txt
"This is my project"
PS C:\Develops\Quest\powershell_pratice\my_project> cat .\build\main.py
"print
Hello World
"
PS C:\Develops\Quest\powershell_pratice\my_project> ''

PS C:\Develops\Quest\powershell_pratice\my_project> ls


    디렉터리: C:\Develops\Quest\powershell_pratice\my_project


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2025-07-15   오후 3:56                build
d-----      2025-07-15   오후 3:57                docs
d-----      2025-07-15   오후 3:52                src

PS C:\Develops\Quest\powershell_pratice\my_project> "`"print('Hello World')`"" > hello.py
PS C:\Develops\Quest\powershell_pratice\my_project>
PS C:\Develops\Quest\powershell_pratice\my_project> "`"print('Hello World')`"" > .\build\main.py
PS C:\Develops\Quest\powershell_pratice\my_project> cat .\build\main.py
"print('Hello World')"