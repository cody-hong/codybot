Codybot 스킬


`/codybot`은 교육 미션 안내문을 분석하고, 학습자 수준에 맞춰 개념 설명, 자기주도학습 계획, 제출 체크리스트, AI 결과 검토 기준을 안내하는 한국어 미션 코치입니다.

* codybot은 기본적으로 CLI 기반으로 작동하도록 만든 구조입니다. (CLI는 직접 공부하기 !)


스킬 파일 위치:

```text
skills/codybot/SKILL.md
```

Claude Code 플러그인용 메타데이터:

```text
.claude-plugin/plugin.json
.claude-plugin/marketplace.json
```

### Codex에서 GitHub로 설치하기

다른 Codex 환경에서 이 스킬을 설치하려면 아래 명령어를 실행합니다.

```bash
python3 /Users/hongbin/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo cody-hong/codyssey_B1_1 \
  --path skills/codybot
```

설치 후 Codex를 재시작합니다.

재시작 후에는 아래처럼 사용할 수 있습니다.

```text
/codybot
```

또는:

```text
/codybot 이 미션 안내문을 왕초보 기준으로 분석해줘
```

### Codex에서 수동 설치하기

GitHub 설치가 어렵다면 로컬에서 직접 복사할 수도 있습니다.

```bash
mkdir -p ~/.codex/skills/codybot
cp skills/codybot/SKILL.md ~/.codex/skills/codybot/SKILL.md
```

복사 후 Codex를 재시작합니다.

### Claude Code 플러그인으로 설치하기

Claude Code에서 플러그인 설치를 지원하는 경우 아래 방식으로 설치할 수 있도록 `.claude-plugin` 메타데이터를 추가했습니다.

```text
/plugin marketplace add cody-hong/codyssey_B1_1
/plugin install codybot@codybot
```

이 방식은 Claude Code의 플러그인 기능을 사용하는 설치 방식입니다. 환경에 따라 실제 설치 가능 여부가 달라질 수 있으므로, 설치가 되지 않으면 위의 Codex 설치 방식이나 수동 설치 방식을 사용합니다.

### Gemini CLI extension으로 설치하기 [하단 Antigravity CLI (`agy`) 사용자 가이드 참고]

Gemini CLI에서 extension 설치를 지원하는 경우 아래 명령어로 설치할 수 있습니다.

```bash
gemini extensions install https://github.com/cody-hong/codyssey_B1_1
```

설치 후 Gemini CLI 세션을 재시작합니다.

설치 확인:

```bash
gemini extensions list
```

Gemini CLI 안에서는 아래 명령어로 extension 상태를 확인할 수 있습니다.

```text
/extensions list
```

사용:

```text
/codybot
```

Gemini CLI용 구성 파일:

```text
gemini-extension.json
GEMINI.md
commands/codybot.toml
skills/codybot/SKILL.md
```

`gemini-extension.json`은 Gemini CLI가 이 저장소를 extension으로 인식하기 위한 파일입니다. `GEMINI.md`는 extension이 로드될 때 기본 지침을 제공하고, `commands/codybot.toml`은 `/codybot` 명령을 제공하며, `skills/codybot/SKILL.md`는 실제 미션 코치 스킬 규칙을 담고 있습니다.

 ### 🚀[추가] Antigravity CLI (`agy`) 사용자 가이드 
 * Gemini cli가 26.06.18 종료됨에 따라 agy 사용 가이드를 첨부합니다.

    Antigravity CLI 환경에서 편리하게 `codybot` 미션 코치를 추가하고 사용하는 방법입니다.

    #### 1. Antigravity CLI 실행하기
    터미널을 열고 아래 명령어를 입력하여 `agy` 대화창으로 진입합니다.
    ```bash
    agy

  #### 2. 대화창에서 AI 에이전트에게 설치 요청하기

  대화창이 열리면 아래와 같이 깃허브 주소를 주면서 설치해달라고 대화로 요청합니다.
  (직접 명령어를 타이핑해 클론하고 설치할 필요 없이, AI 비서가 알아서 처리합니다.)

  │ 요청 예시:
  │ "이 깃허브 저장소에서 코디봇 플러그인 설치해줘: https://github.com/cody-hong/codyssey_B1_1"

  #### 3. 코디봇 실행하기

  설치가 완료되면 대화창에 아래 명령어를 입력하여 미션 코칭 서비스를 시작합니다.

    /codybot

### 설치 후 기대 동작

`/codybot`을 입력하면 먼저 학습 레벨을 선택하게 안내합니다.

```text
1. 왕초보
2. 초보자
3. 중급자
4. 전문가
```

학습 레벨을 선택하면 바로 분석하지 않고, 다음 문장으로 미션 안내문 입력을 요청합니다.

```text
좋아요. 이제 분석할 미션 안내문을 그대로 보내주세요.
```

이후 미션 안내문을 보내면 선택한 수준에 맞춰 핵심 개념, 필수 산출물, 기능 요구사항, 학습 순서, 제출 체크리스트, 검증 포인트를 단계별로 안내합니다.
| `B1-1 미션 : ChatGPT에게 일을 제대로 시키는 법 배우기.md` | Codyssey B1-1 미션 원문 정리 |
| `references/2026-06-04 좋은 프롬프트 만드는 방법 조사.md` | 공식 문서와 신뢰 가능한 자료 기반 프롬프트 작성법 조사 |


* CLI설치 없이 사용하고 싶다 하시면 [#prompt.md](https://github.com/cody-hong/codybot/blob/main/prompt.md) 이동 전문 붙여넣기 !
