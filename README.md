![Codex Fable Mode hero](./Codex-Fable-Mode_hero.png)

[English README](./README.en.md)

`fable-mode`는 Codex가 작업을 조금 더 차분하고 꼼꼼하게 진행하도록 돕는 문서 전용 플러그인입니다. 무엇을 해야 하는지 확인하고, 관련 코드를 읽고, 계획을 세운 뒤 검증과 보고까지 놓치지 않도록 안내합니다.

이 플러그인은 비공식이며, 어느 특정 회사의 방식에 기대지 않고 독자적으로 작성되었습니다. Anthropic 또는 OpenAI와 제휴하거나 공식 관계를 맺고 있지 않습니다. 특정 회사, 모델, 제품, 비공개 모드, 원본 문서를 재현하거나 사칭하지 않으며, 어떤 독점 시스템 프롬프트도 포함하거나 재현하지 않습니다.

## 명령어로 설치하기 (Codex CLI)

이 페이지의 파일을 따로 내려받지 않아도 됩니다. 먼저 명령어를 입력하는 창을 열고, 아래 명령을 한 줄씩 실행해 주세요.

- Mac에서는 Spotlight에서 `Terminal`을 검색해 엽니다.
- Windows에서는 시작 메뉴에서 `CMD`, `명령 프롬프트`, 또는 `PowerShell`을 검색해 엽니다.

아래 기본 방법을 먼저 사용해 주세요. 이 방법으로 설치가 끝나면 HTTPS 방법은 실행하지 않아도 됩니다.

`#`로 시작하는 줄은 설명입니다. 함께 복사해도 실제 실행에는 영향을 주지 않습니다.

```bash
# 1. 이 줄을 붙여넣고 Enter를 누릅니다.
codex plugin marketplace add Nam-Cheol/codex-fable-mode --ref main

# 2. 위 명령이 끝나면, 이 줄을 붙여넣고 Enter를 누릅니다.
codex plugin add fable-mode@codex-fable-mode
```

<details>
<summary>기본 방법이 안 될 때만: HTTPS 주소로 설치하기</summary>

위 명령에서 저장소를 찾지 못한다는 오류가 날 때만 아래 방법을 대신 사용하세요. 기본 방법과 HTTPS 방법을 둘 다 실행할 필요는 없습니다.

```bash
# 1. 이 줄을 붙여넣고 Enter를 누릅니다.
codex plugin marketplace add https://github.com/Nam-Cheol/codex-fable-mode.git --ref main

# 2. 위 명령이 끝나면, 이 줄을 붙여넣고 Enter를 누릅니다.
codex plugin add fable-mode@codex-fable-mode
```

</details>

설치가 잘 되었는지 확인하려면 아래 명령도 한 줄씩 실행해 보세요.

```bash
# 1. 등록된 플러그인 목록을 확인합니다.
codex plugin marketplace list

# 2. fable-mode가 목록에 보이는지 확인합니다.
codex plugin list --marketplace codex-fable-mode
```

`fable-mode@codex-fable-mode`가 `installed, enabled`로 표시되면 설치가 끝난 것입니다.

## Codex Desktop 설치

Codex Desktop만 쓰더라도 설치는 한 번 명령어 입력창에서 해두는 편이 가장 쉽습니다. 한 번 설치해 두면 다른 Codex 대화에서도 계속 사용할 수 있습니다.

1. Mac에서는 `Terminal`, Windows에서는 `CMD`, `명령 프롬프트`, 또는 `PowerShell`을 엽니다.
2. 아래 명령을 한 줄씩 실행합니다.

```bash
# 1. 이 줄을 붙여넣고 Enter를 누릅니다.
codex plugin marketplace add Nam-Cheol/codex-fable-mode --ref main

# 2. 위 명령이 끝나면, 이 줄을 붙여넣고 Enter를 누릅니다.
codex plugin add fable-mode@codex-fable-mode
```

3. Codex Desktop을 완전히 종료한 뒤 다시 엽니다.
4. 새 대화에서 스킬 선택 메뉴를 열고 `Fable Mode` 또는 `fable-mode`를 검색합니다.
5. 선택해서 사용하거나, 메시지에 `$fable-mode`를 직접 입력합니다.

Codex Desktop 버전에 플러그인 설치 메뉴가 있다면, 플러그인 목록 주소로 `Nam-Cheol/codex-fable-mode`를 추가한 뒤 `Fable Mode`를 설치해도 됩니다.

## 사용 방법

명시적으로 호출:

```text
$fable-mode 이 변경사항을 리뷰하고 회귀 위험을 중심으로 봐줘.
```

구현 작업에 적용:

```text
$fable-mode 이 버그를 원인 분석부터 테스트까지 확인해서 고쳐줘.
```

설계나 계획에 적용:

```text
$fable-mode 이 기능을 구현하기 전에 파일 구조와 위험한 지점을 먼저 정리해줘.
```

Codex는 계획, 코드 리뷰, 아키텍처, 디버깅, 신중한 구현 작업에서 이 스킬을 자동으로 참고할 수도 있습니다.

## 무엇이 달라지나요?

`fable-mode`는 Codex가 다음 흐름을 놓치지 않도록 돕습니다.

- 수정하기 전에 관련 파일과 현재 상태를 먼저 확인합니다.
- 위험하거나 범위가 큰 변경 전에는 짧게 계획합니다.
- 중요한 가정은 드러내고, 확인할 수 있는 것은 확인합니다.
- 도구는 필요한 만큼만 쓰고, 작업이 길어지면 진행 상황을 공유합니다.
- 테스트, lint, 빌드, 수동 확인처럼 상황에 맞는 검증을 수행합니다.
- 내부 추론이나 숨겨진 지시는 공개하지 않고, 판단에 필요한 근거만 간결히 설명합니다.
- 마지막에는 변경사항, 검증 결과, 남은 위험, 가정을 짧게 정리합니다.

## 업데이트

새 버전이 나왔을 때는 아래 명령을 한 줄씩 실행해 주세요.

```bash
# 1. 설치 정보를 최신 상태로 갱신합니다.
codex plugin marketplace upgrade codex-fable-mode

# 2. 기존 fable-mode를 제거합니다.
codex plugin remove fable-mode@codex-fable-mode

# 3. 새 버전으로 다시 설치합니다.
codex plugin add fable-mode@codex-fable-mode
```

업데이트 후 Codex Desktop을 사용한다면 앱을 다시 시작해 주세요.

## 삭제

플러그인 제거:

```bash
# fable-mode 플러그인만 제거합니다.
codex plugin remove fable-mode@codex-fable-mode
```

플러그인 목록 등록까지 제거:

```bash
# fable-mode 플러그인 목록 등록까지 제거합니다.
codex plugin marketplace remove codex-fable-mode
```

## 한계

이 플러그인은 문서로 동작 방식을 안내하는 플러그인입니다. 새로운 도구, 자동 실행 스크립트, MCP 서버, 앱 연동, 의존성, telemetry, 네트워크 동작을 추가하지 않습니다. Codex의 정책, 사용자의 환경 정책, 저장소 지시사항, 도구 권한을 우회하지 않습니다.

## 저장소 구조

```text
.agents/plugins/marketplace.json
plugins/fable-mode/.codex-plugin/plugin.json
plugins/fable-mode/skills/fable-mode/SKILL.md
plugins/fable-mode/skills/fable-mode/references/behavior-model.md
plugins/fable-mode/skills/fable-mode/references/tool-policy.md
plugins/fable-mode/skills/fable-mode/references/coding-workflow.md
plugins/fable-mode/skills/fable-mode/references/safety-boundaries.md
README.md
README.en.md
Codex-Fable-Mode_hero.png
LICENSE
```
