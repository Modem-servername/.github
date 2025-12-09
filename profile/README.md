# :clipboard: 팀 Git 협업 및 워크플로우 가이드라인

본 가이드는 코드 충돌을 방지하고 원활한 협업을 위해 **작업 시작 전(준비)**과 **작업 완료 후(등록)**에 반드시 지켜야 할 절차를 규정합니다.

-----

## 1. 작업 준비 (Preparation)

작업을 시작하기 전, 나의 로컬 환경을 최신 상태로 만들거나 안전한 작업 공간을 확보하는 단계입니다. 현재 상황에 맞춰 **A** 또는 **B** 중 하나를 따르세요.

### 상황 A: 작업을 시작하기 전인 경우 (권장)

가장 일반적인 절차입니다. `main`을 최신화한 뒤 브랜치를 생성합니다.

1.  **메인 브랜치로 이동**
    ```bash
    git checkout main
    ```
2.  **원격 저장소의 최신 코드 당겨오기 (Update)**
    ```bash
    git pull origin main
    ```
3.  **내 작업용 브랜치 생성 및 이동**
    ```bash
    # git checkout -b feature/기능명
    git checkout -b feature/login-page
    ```

### 상황 B: 이미 코드를 작성했는데 Pull을 깜빡한 경우 (비상)

`main` 브랜치에서 이미 작업을 시작했다면, **절대 `pull` 하지 말고** 즉시 브랜치를 생성하여 대피합니다.

1.  **작업 내용을 그대로 들고 새 브랜치로 이동**
    *(이 명령어를 실행하면 작성 중이던 코드가 새 브랜치로 안전하게 옮겨집니다.)*
    ```bash
    # git checkout -b feature/기능명
    git checkout -b feature/signup-api
    ```
2.  **작업 진행**
    이동된 브랜치에서 그대로 작업을 이어서 진행합니다.

-----

## 2. 작업 등록 (Registration)

기능 구현이 완료되면 코드를 저장하고 GitHub에 병합을 요청하는 단계입니다.

### 단계 1: 터미널에서의 작업 (Push)

내 코드를 GitHub 원격 저장소로 업로드합니다.

1.  **변경 사항 스테이징 (Add)**
    ```bash
    git add .
    ```
2.  **변경 사항 기록 (Commit)**
    ```bash
    # git commit -m "작업 내용 요약"
    git commit -m "feat: 로그인 API 구현 완료"
    ```
3.  **원격 저장소로 업로드 (Push)**
    ```bash
    # git push origin feature/기능명
    git push origin feature/login-page
    ```

### 단계 2: GitHub 웹사이트에서의 작업 (Merge)

터미널이 아닌 GitHub 웹 인터페이스를 통해 안전하게 합칩니다.

1.  **Pull Request (PR) 생성**
      * GitHub 저장소 페이지 접속 -> 상단 경고창의 `Compare & pull request` 클릭.
      * 방향 확인: `base: main` :arrow_left: `compare: feature/기능명`
      * 내용 작성 후 `Create pull request` 클릭.
2.  **코드 리뷰 및 병합 (Merge)**
      * 팀원 확인 후 이상이 없으면 `Merge pull request` 클릭.
      * `Confirm merge`를 눌러 최종 반영.

-----

## :warning: 핵심 수칙 (Golden Rules)

1.  **Direct Commit 금지:** `main` 브랜치에 직접 커밋하거나 푸시하지 않습니다.
2.  **1기능 1브랜치:** 하나의 기능은 하나의 브랜치에서 작업합니다.
3.  **gitignore 준수:** `__pycache__`, `node_modules`, `.env`, 시스템 파일 등은 절대 커밋하지 않습니다.
