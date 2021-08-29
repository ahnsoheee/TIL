## Git

![다운로드](https://user-images.githubusercontent.com/61968474/131254144-a586fb9a-12ac-436a-8a97-61dacf429179.png)

- 온라인으로 소스코드 공유 및 협업, 저장할 수 있는 시스템

### 저장소
#### 1. workspace
- 실제 소스코드를 작업하는 공간
- 현재 작업 중인 파일이 있는 내 PC의 directory
- 일반적인 프로젝트 폴더

#### 2. index (stage)
- workspace의 코드를 저장하는 공간
- 수정 내역의 대기 장소

#### 3. local repository
- 개인 PC에 저장되는 저장소

#### 4. remote repository
- 원격 저장소 전용 서버에서 관리됨
- 공유되는 저장소
- github 등


### 명령어
#### 1. git init 
- repository 생성
#### 2. git status 
- 파일의 상태를 확인
#### 3. git checkout 
- 브랜치 변경
- 실제 git에서는 브랜치를 지정하지만, 구현한 명령 동작은 지정한 repository를 사용한다는 의미.
#### 4. git add
- workspace에서 staging area로 올리는 명령어.
#### 5. git update
-  실제 git에는 존재하지 않는 명령어지만, 구현한 명령어에서는 파일이 수정된 것을 반영하기 위해 사용된다.
#### 6. git commit 
- 실제 git에서는 stage area에 올라간 Staged 파일들을 local repository에 커밋 메시지와 저장한다.
- 구현한 명령어는 local repository 역할을 하는 - gitRepository라는 저장소에 커밋메시지와 함께 저장된다.
- 실제 git에서는 commit id로 SHA1 Hash를 사용한다.
- 실제 git에서는 commit할 때 commit id, Author, Date, commit msg를 반영하지만 구현한 명령어는 commit msg만을 반영한다.
#### 7. git log
- commit history를 출력
#### 8. git push 
- local repository에서 remote repository로 저장
