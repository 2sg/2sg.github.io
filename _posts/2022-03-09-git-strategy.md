# git branch

## Git Flow

### 구성

- 다음과 같은 branch들로 구성된다.
    - **develop**
        - 현재 개발이 완료된 상태와 일치하는 branch
        - 여기서 개발이 완료되었다는것은 언제든지 운영서버에 배포될 수 있는 상태를 말한다.
    - **master**
        - 현재 운영중인 production환경과 일치하는 branch
    - **feature**
        - 새로운 기능 혹은 이슈에 대해서 대응하기 위하여 develop에서 분리하여 만드는 branch
        - develop을 개발완료상태로 유지하며 다른 개발자들과 conflict을 방지하기 위한 목적으로 사용하는 branch
    - **release**
        - 배포준비가 된 develop으로부터 운영서버에 배포하기 전 분리하여 만드는 branch
        - 운영서버에 릴리즈할 기능을 develop으로부터 분리하기 위한 목적으로 사용한다.
    - **hotfix**
        - 현재 운영환경의 이슈를 수정하기 위하여 master에서 분리하여 만드는 branch

### 규칙

- branch를 merge할 때는 항상 —no-ff옵션을 붙여 branch에 대한 기록이 사라지는것을 방지한다.

### 장점

- 프로젝트의 규모가 크고 개발자가 많을수록 브랜치를 구분하기 편하다. 소스코드를 관리하기에 용이하다.

### 단점

- 너무나도 브랜치가 많아져 흐름을 복잡하게 만들기도 한다.
- release와 master의 역할구분이 모호하다.

## Github Flow

### 구성 및 운영방식

- master 하나로 진행하는 방식이다.
- 기능, 이슈에 상관없이 master로부터 새로운 브랜치를 만들고 master에 머지되어 최신상태를 유지한다.
- pull request를 통해서 배포이전에 팀원들 사이 피드백, 버그 찾는 과정이 진행되어야한다.

### 주의해야할점

- git flow와는 다르게 release브랜치가 따로 존재하지 않아 pull request에서 충분히 리뷰와 피드백이 진행되어야한다.
- master에 머지가 이루어질때마다 배포가 이루어지는게 이상적이다. CI/CD를 통하여 배포자동화를 적용하는것이 좋다.

## GitLab Flow

### 구성

- gitlabflow는 이슈트래을 연동해 전략을 단순화하고자 한다. merge request를 활용해 승인이 되는 이슈만 머지하도록 하는것이 핵심이다.
    - feature
        - 모든 기능구현은 feature에서 진행된다.
        - master로부터 분리되어나와 master로 머지되며 기능구현이 완료되면 merge request를 통하여 팀원간 협의가 완료되면 master로 머지한다.
    - master
        - git flow의 develop브랜치와 같은 역할을 한다.
        - feature에서 병합된 기능에 대해서 테스트하기 위한 브랜치다.
    - production
        - git flow의 mater와 같다.
        - 운영환경의 버전과 일치한다.
