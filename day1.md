# CLI

1. CLI 

   - Git Bash 사용

     UNIX 계열 명령어와 Windows 간의 차이를 없애주는 인터프리터. 

     (1) 루트, 홈 디렉토리 

     ​	a. 루트 디렉토리(Root, `/`)

     ​		모든 파일, 폴더 담고있는 최상위 폴더

     ​		Win의 경우 보통 C드라이브. 

     ​	b. 홈 디렉토리(Home, `~`)

     ​		*Tilde(틸드, ~)* 라고도 부름. 현재 로그인된 사용자의 홈 폴더

     ​	 	Win에서 C:/사용자(Users)/현재 사용자 계정

   - 절대 경로와 상대 경로

     (1) 절대경로 : 루트 디렉토리부터 목적지점까지의 모든 경로

     ​		ex. C:/Users/candy/Desktop

     (2) 상대경로 : 현재 작업하는 디렉토리 기준의 상대적 경로

     ​	 `./` : 현재 작업 폴더

     ​	`../` : 현재 작업 폴더의 부모 폴더(상위 폴더)

     

2. CLI와 GUI

   CLI: Command Line Interface

   GUI: Graphic USer Interface 

    

3. 명령어

   (1) `touch`

   - 파일 생성 명령어

   - 띄어쓰기로 여러개 파일 생성

   - 숨김파일은 `.`을 파일명앞에 

     ```bash
     $ touch text.txt 
     ```

   (2) `mkdir`

   - make directory 
   - 새 폴더 생성 명령어 
   - 띄어쓰기로 여러 폴더 생성

   ```bash
   $ mkdir folder
   $ mkdir 'happy hacking'
   ```

   (3) `ls`

   - list segments 

   - 현재 작업중인 디렉토리 폴더/파일 목록 보여줌 

   - 옵션

     ​	`-a`: all 옵션. 숨김파일까지 모두 보여줌.

     ​	`-l`: long 옵션. 용량, 수정날짜 등 파일 정보 보여줌. 

     ```bash
     #기본 사용
     $ ls
     
     #all 
     $ ls -a
     
     #all, long 
     $ ls -a -l
     
     #축약형
     $ ls -al
     ```

​		 (4) `mv`

			- move 
			- 폴더/파일을 다른 폴더 내로 이동하거나 이름을 변경
			- 작성한 이름의 폴더가 있는 경우 이동하나, 없으면 이름 변경

```bash
#text.txt 를 folder 폴더 안에 넣기
$ mv text.txt folder

#text1.txt의 이름을 text2.txt로 바꿀 때 
$ mv text1.txt text2.txt
```

​		(5) `cd` 

- change directory
- 현재 작업 중인 디렉토리 변경
- `cd ~`  홈 디렉토리로 이동 (`cd`로 입력해도 홈)
- `cd ..` 부모 디렉토리로 이동 (위로 가기)
- `cd -`  바로 이전 디렉토리로 이동(뒤로 가기)

```bash
#현재 작업 중인 디렉토리에 있는 folder 폴더로 이동
$ cd folder

#절대 경로를 통한 디렉토리 변경
$ cd C:/Users/usnhee/Desktop

#상대 경로를 통한 디렉토리 변경
$cd ../parent/child
```

​		(6) `rm`

- remove
- 폴더/파일 지우기
- 휴지통으로 가지 않고 완전 삭제
- *(asterisk, wildcard) 사용해서 `rm *.txt` 입력하면 txt 파일 전테 지움
- `-r` : recursive 옵션. **폴더** 지울때 사용

```bash
$ rm test.txt
$ rm -r folder
```

​		(7) `start, open`

  - 폴더/파일을 연다. 
  - window는 `start` / Mac에서는 `open`

```bash
$ start test.txt
```

4. Useful Shortcuts 

   - `위 아래 방향키` : 과거 작성했던 명령어 조회 
   - `tab` : 폴더/파일 이름 자동 완성
   - `ctrl + a` : 커서가 맨 앞으로 이동
   - `ctrl + e` : 커서가 맨 뒤로 이동
   - `ctrl + w` : 커서가 앞 단어를 삭제 
   - `ctrl + l` : 터미널 화면을 깨끗하게  청소( 스크롤 올리면 과거 내역 있음)
   - `ctrl + insert` : 복사
   - `shift + insert` : 붙여넣기 

   
