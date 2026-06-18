# Codybot

`/codybot`은 교육 미션 안내문을 분석하고, 학습자 수준에 맞춰 개념 설명, 자기주도학습 계획, 제출 체크리스트, AI 결과 검토 기준을 안내하는 한국어 미션 코치입니다.

이 저장소는 `codybot`을 여러 환경에서 재사용할 수 있게 만든 배포본입니다.

## 무엇이 들어 있나요

```text
skills/codybot/SKILL.md
.claude-plugin/plugin.json
.claude-plugin/marketplace.json
gemini-extension.json
GEMINI.md
commands/codybot.toml
prompt.md
```

## 사용 방식

### Codex에서 스킬로 사용

다른 Codex 환경에서 이 스킬을 설치하려면 아래 명령어를 실행합니다.

```bash
python3 /Users/hongbin/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo cody-hong/codybot \
  --path skills/codybot
```

설치 후 Codex를 재시작한 뒤 다음처럼 사용합니다.

```text
/codybot
```

또는:

```text
/codybot 이 미션 안내문을 왕초보 기준으로 분석해줘
```

### 수동 설치

GitHub 설치가 어렵다면 로컬에서 직접 복사할 수 있습니다.

```bash
mkdir -p ~/.codex/skills/codybot
cp skills/codybot/SKILL.md ~/.codex/skills/codybot/SKILL.md
```

### Claude Code 플러그인

Claude Code에서 플러그인 설치를 지원하는 환경이라면 아래 메타데이터를 사용합니다.

```text
/plugin marketplace add cody-hong/codybot
/plugin install codybot@codybot
```

### Gemini CLI extension

Gemini CLI에서 extension 설치를 지원하는 환경이라면 아래 명령으로 설치할 수 있습니다.

```bash
gemini extensions install https://github.com/cody-hong/codybot
```

설치 후 세션을 재시작하고 다음처럼 사용합니다.

```text
/codybot
```

### Antigravity CLI (`agy`) 사용자 가이드

`agy` 환경에서도 `codybot`을 참고용으로 사용할 수 있습니다.

#### 1. Antigravity CLI 실행하기

터미널에서 아래 명령어를 입력해 `agy` 대화창으로 진입합니다.

```bash
agy
```

#### 2. 대화창에서 설치 요청하기

대화창이 열리면 아래처럼 GitHub 주소를 주고 설치를 요청합니다.

```text
이 GitHub 저장소에서 코디봇 플러그인 설치해줘: https://github.com/cody-hong/codybot
```

#### 3. 코디봇 실행하기

설치가 끝나면 대화창에 아래 명령어를 입력합니다.

```text
/codybot
```

## 바로 붙여넣기용 프롬프트

`prompt.md`에는 새 채팅창에 바로 붙여넣을 수 있는 통합 프롬프트가 들어 있습니다.

처음 써보는 경우에는 이 파일을 먼저 복사해서 사용하면 됩니다.

## 기본 동작

`/codybot`을 입력하면 먼저 학습 레벨을 고르게 안내합니다.

1. 왕초보
2. 초보자
3. 중급자
4. 전문가

레벨을 고른 뒤에는 바로 분석하지 않고, 미션 안내문 입력을 요청합니다.

```text
좋아요. 이제 분석할 미션 안내문을 그대로 보내주세요.
```

이후 입력된 미션 안내문을 바탕으로 핵심 개념, 필수 산출물, 기능 요구사항, 학습 순서, 제출 체크리스트, 검증 포인트를 단계별로 안내합니다.

## 참고

- `prompt.md`에는 복사해서 바로 붙여넣을 수 있는 통합 프롬프트가 들어 있습니다.
- `skills/codybot/SKILL.md`에는 실제 코치 규칙이 들어 있습니다.
- `GEMINI.md`와 `commands/codybot.toml`은 Gemini CLI용 구성입니다.
- `.claude-plugin/`은 Claude Code 플러그인용 메타데이터입니다.
