# snu_med_globalcapstone_practice

This repository is used for hands-on practice with three modes of interacting with AI.

> 이 리포지토리는 AI Agent(Github Copilot)과 인터랙션해 의료 분야 프로젝트에 활용하기 위한 스타터 파일입니다.

---

This repository is a starter project for learning how to build and operate LLM agent-based projects with GitHub Copilot and OpenRouter, even without a GPU environment.

> 이 리포지토리는 **GPU가 없는 환경**에서도 GitHub Copilot과 OpenRouter를 이용해 LLM 에이전트 기반 프로젝트를 만들고 운영하는 방법을 실습하기 위한 스타터 프로젝트입니다.

Follow the guide below to prepare the environment and build a medical document web application step by step using three modes: Plan, Agent, and Debug.

> 아래 안내에 따라 환경을 준비하고, 세 가지 모드(Plan / Agent / Debug)를 통해 의료 분야 데이터를 다루는 웹 애플리케이션을 단계별로 구현해 보세요.

## Resources / 자료 링크

- **Lecture Materials (Notion)**: [GPU 없는 환경에서 배우는 LLM Agent with GitHub Copilot and OpenRouter](https://eiden-choe.notion.site/GPU-LLM-Agent-with-Github-Copilot-and-OpenRouter-3347cc1d72038011ba30e6840c0199c8?source=copy_link)
- **GitHub Repository**: [dablro12/snu_med_globalcapstone_practice](https://github.com/dablro12/snu_med_globalcapstone_practice)

> - **강의자료(노션)**: [GPU 없는 환경에서 배우는 LLM Agent with GitHub Copilot and OpenRouter](https://eiden-choe.notion.site/GPU-LLM-Agent-with-Github-Copilot-and-OpenRouter-3347cc1d72038011ba30e6840c0199c8?source=copy_link)
> - **깃허브 레포지토리**: [dablro12/snu_med_globalcapstone_practice](https://github.com/dablro12/snu_med_globalcapstone_practice)

## Getting Started / 시작하기

1. Fork this repository to your own GitHub account. On the Fork page, select **Owner** and enter a new repository name.

> 1. 이 저장소를 자신의 GitHub 계정으로 **Fork**합니다. Fork 화면에서 **Owner**를 선택하고 새 저장소 이름을 입력하세요.

2. In your new repository, click **`<> Code`** → **`Codespaces`** → **`Create codespace on main`**.

> 2. 새로 생성한 저장소에서 **`<> Code`** → **`Codespaces`** → **`Create codespace on main`**을 클릭하세요.

3. Wait a few moments for the environment to load. Python (Anaconda) and GitHub Copilot are pre-installed.

> 3. 환경이 로드될 때까지 잠시 기다리세요. Python(Anaconda)과 GitHub Copilot이 기본 설치되어 있습니다.

4. When the Codespace opens, VS Code IDE will launch in your browser. The interface includes a file explorer, code editor, terminal, and agent panel.

> 4. Codespace가 열리면 브라우저에서 VS Code IDE가 실행됩니다. 화면에는 파일 탐색기, 코드 에디터, 터미널, 에이전트 패널이 포함되어 있습니다.

5. In the agent panel, you can use three main interaction modes: **Agent**, **Ask**, and **Plan**.

> 5. 에이전트 패널에서는 **Agent**, **Ask**, **Plan**의 세 가지 주요 모드를 사용할 수 있습니다.

## Environment Setup / 환경 준비

### 1. GitHub Education and Codespace Setup / GitHub Education 신청 및 Codespace 연결

GitHub Education Pack provides free access to useful student benefits such as private repositories and GitHub Copilot.

> GitHub Education Pack을 이용하면 프라이빗 레포지토리와 GitHub Copilot 등 학생용 혜택을 무료로 사용할 수 있습니다.

Sign up for GitHub using your school account, then go to the GitHub Education page and click **Start an application** to complete student verification.

> 학교 계정으로 GitHub에 가입한 뒤 GitHub Education 페이지에서 **Start an application**을 클릭하여 학생 인증을 진행하세요.

Once your application is approved, fork this repository and open it in Codespaces.

> 승인이 완료되면 이 저장소를 포크한 뒤 Codespaces에서 열어 주세요.

### 2. VS Code IDE Components / VS Code IDE 구성 요소

VS Code includes the following main areas:

> VS Code에는 다음과 같은 주요 영역이 있습니다.

- **File Explorer**: Browse project files and create new files.

> - **파일 관리 창**: 프로젝트 파일을 탐색하고 새 파일을 생성합니다.

- **Code Editor**: Write Python, Markdown, and other code.

> - **코드 에디터 창**: Python, Markdown 등 코드를 작성합니다.

- **Terminal**: Run commands for environment setup and package installation.

> - **터미널 창**: 환경 설정과 패키지 설치를 위한 명령어를 실행합니다.

- **Agent Panel**: Use Copilot Chat in Agent, Ask, and Plan modes.

> - **에이전트 창**: Copilot Chat의 Agent, Ask, Plan 모드를 사용할 수 있습니다.

Run the following command in the terminal to initialize and activate the base Conda environment:

> 아래 명령어를 터미널에서 실행하여 Conda를 초기화하고 base 환경을 활성화하세요.

```bash
conda init && source ~/.bashrc && conda activate base
````

### 3. OpenRouter Account and API Key / OpenRouter 회원가입 및 API Key 설정

OpenRouter provides access to various pretrained models through API.

> OpenRouter는 다양한 사전학습 모델을 API 형태로 사용할 수 있게 해주는 서비스입니다.

To use a Vision-Language model in this project, follow these steps:

> 이 프로젝트에서 Vision-Language 모델을 사용하려면 아래 순서대로 진행하세요.

1. Visit [https://openrouter.ai/](https://openrouter.ai/) and sign in with your GitHub account.

> 1) [https://openrouter.ai/](https://openrouter.ai/)에 접속한 뒤 GitHub 계정으로 로그인하세요.

2. In the dashboard, go to **API Keys → Create**, then set a name and expiration date for your key.

> 2) 대시보드에서 **API Keys → Create**를 클릭하고, 키 이름과 만료일을 설정하세요.

3. Copy the generated API key and create a `.env` file in the project root.

> 3) 생성된 API Key를 복사한 뒤 프로젝트 루트에 `.env` 파일을 생성하세요.

4. Save the key in the following format:

> 4) 아래 형식으로 `.env` 파일에 저장하세요.

```env
OPENROUTER_API_KEY=여기에_복사한_API키
```

5. Make sure `.env` is included in `.gitignore` so that it is not uploaded to GitHub.

> 5) `.env` 파일이 GitHub에 업로드되지 않도록 `.gitignore`에 포함시키는 것이 좋습니다.

## Project Workflow / 프로젝트 진행 단계

This project demonstrates how to build a simple web application that extracts fields such as patient name, contact information, and exam date from medical documents using a Vision-Language model.

> 이 프로젝트는 Vision-Language Model을 활용해 병원 서류(진료 의뢰서, 검사 결과지 등)에서 환자 이름, 연락처, 검사일 등의 정보를 추출하는 간단한 웹앱을 만드는 과정을 다룹니다.

### 1. Using Plan Mode / Plan 모드 사용법

Plan mode helps turn a high-level idea into a concrete development plan.

> Plan 모드는 고수준 아이디어를 구체적인 개발 계획으로 바꾸는 데 도움을 줍니다.

You can use prompts like the following to design the project:

> 아래와 같은 프롬프트를 활용해 프로젝트를 설계할 수 있습니다.

1. **Feature definition**:
   “I want to build a web app where users upload a medical document image, and a Vision-Language model extracts fields such as name, phone number, and exam date into a table. The app should support image recognition, file upload (or webcam), and conversational interaction.”

> 1) **기능 정의**:
>    “사용자가 병원 서류 이미지를 업로드하면 Vision-Language Model이 이름, 연락처, 검사일 등의 정보를 추출해 표로 보여주는 웹앱을 만들고 싶어. 이미지 인식, 파일 업로드(또는 웹캠), 대화형 UI 기능이 필요해.”

2. **Task instruction**:
   “Create a `requirements.txt` file with the necessary Python libraries, and build a Streamlit app that performs the above tasks.”

> 2) **작업 지시**:
>    “필요한 파이썬 라이브러리를 `requirements.txt`에 정리하고, 위 기능을 수행하는 Streamlit 웹앱을 만들어줘.”

3. **Final instruction**:
   “Use a specific VLM model (for example, `qwen3.5-9b`) and make a development plan including setup, UI design, model calling, and output formatting.”

> 3) **최종 지시**:
>    “특정 VLM 모델(예: `qwen3.5-9b`)을 사용하고, 설치, UI 설계, 모델 호출, 출력 포맷까지 포함한 개발 계획을 세워줘.”

Plan mode usually returns a TODO list and a suggested project structure.

> Plan 모드는 보통 TODO 목록과 프로젝트 구조 제안을 결과로 제공합니다.

Review the plan and revise it if necessary before moving on.

> 다음 단계로 넘어가기 전에 계획을 검토하고 필요하면 수정하세요.

### 2. Using Agent Mode / Agent 모드 사용법

After the plan is finalized, use Agent mode to generate and execute the actual code.

> 계획이 확정되면 Agent 모드를 이용해 실제 코드를 생성하고 실행합니다.

Example prompts:

> 예시 프롬프트는 아래와 같습니다.

1. “Create a `requirements.txt` file and add packages such as Streamlit, transformers, and pillow.”

> 1) “`requirements.txt` 파일을 만들고 Streamlit, transformers, pillow 같은 패키지를 추가해줘.”

2. “Write a Streamlit app that preprocesses uploaded images and extracts text using a Vision-Language model.”

> 2) “업로드된 이미지를 전처리하고 Vision-Language 모델로 텍스트를 추출하는 Streamlit 앱을 작성해줘.”

3. Review the generated code, check the changes, and click **Keep** to apply them.

> 3) 생성된 코드를 확인하고 변경사항을 검토한 뒤 **Keep**을 눌러 적용하세요.

4. Run the web app and verify the output.

> 4) 웹앱을 실행한 뒤 결과가 잘 나오는지 확인하세요.

Agent mode supports iterative “vibe coding,” where you continuously refine the result through feedback and follow-up prompts.

> Agent 모드는 반복적인 피드백과 후속 프롬프트를 통해 결과를 계속 발전시키는 “vibe coding” 방식에 잘 맞습니다.

### 3. Using Debug Mode / Debug 모드 사용법

If errors occur during execution, use Debug mode to identify the cause and fix the issue.

> 실행 중 오류가 발생하면 Debug 모드를 활용해 원인을 파악하고 문제를 수정할 수 있습니다.

Copy the error message from the terminal and give a prompt such as:

> 터미널에서 에러 로그를 복사한 뒤 아래와 같이 요청할 수 있습니다.

“Please fix this error and check whether the app works stably after the fix.”

> “이 에러를 수정하고, 수정 후 안정적으로 동작하는지까지 확인해줘.”

Debug mode helps analyze the error, suggest fixes, and improve stability through testing.

> Debug 모드는 에러 원인을 분석하고 수정안을 제시하며, 테스트를 통해 안정성을 높이는 데 도움을 줍니다.

## Sharing Your Project on GitHub / 깃허브에 프로젝트 공유하기

When your work is complete, commit the changes with Git and push them to GitHub.

> 작업이 완료되면 Git으로 변경사항을 커밋하고 GitHub에 푸시하세요.

Sensitive files such as `.env` should be excluded from version control by adding them to `.gitignore`.

> `.env` 같은 민감한 파일은 `.gitignore`에 추가하여 버전 관리에서 제외해야 합니다.

You can also ask the agent to help generate a README file and commit message for your project.

> 에이전트에게 README 작성이나 커밋 메시지 생성도 요청할 수 있습니다.

## Reference / 참고 문헌

* Waseem, Muhammad, et al. “Vibe Coding in Practice: Flow, Technical Debt, and Guidelines for Sustainable Use.” *arXiv* preprint arXiv:2512.11922 (2025).

> - Waseem, Muhammad, et al. “Vibe Coding in Practice: Flow, Technical Debt, and Guidelines for Sustainable Use.” *arXiv* preprint arXiv:2512.11922 (2025).
