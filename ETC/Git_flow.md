## Git flow

![image](https://user-images.githubusercontent.com/61968474/133736875-c9ee21a7-ed3b-4711-bacc-5159180993d7.png)

- 소스 코드를 관리하고 출시하기 위한 브랜치 관리 전략 중 하나
- 프로젝트에 참여하는 인원이 여러 명일 경우 효율적인 분업과 협업의 편리를 위해 사용됨
- 버전 관리를 위해 워크 플로우 전략이 필요

### master branch
- 출시될 수 있는 브랜치

### develop branch
- 다음 출시 버전을 개발하는 브랜치
- master branch에서부터 시작된 브랜치
- 수시로 버그를 수정한 커밋들이 추가됨
- master, develop branch를 메인 브랜치라고 함

### feature branch
- 기능을 개발하는 브랜치
- develop branch에서 생성
- 작업 완료 후 develop branch로 merge

### release branch
- 이번 출시 버전을 준비하는 브랜치 (QA)
- develop branch에서 생성

### hotfix branch
- 출시 버전에 발생한 버그를 수정하는 브랜치
- 긴급 수정하기 위한 브랜치

