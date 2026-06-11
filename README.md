![Codex Fable Mode hero](./Codex-Fable-Mode_hero.png)

[English README](./README.en.md)

`fable-mode`는 Codex가 사용자의 의도에 맞춰 필요한 만큼만 사고 깊이를 조절하도록 돕는 문서 전용 플러그인입니다.

설치되는 스킬은 하나뿐입니다. 사용자는 항상 `$fable-mode`만 호출하면 됩니다. 이 스킬은 하네스도, 두 번째 런타임도, 딱딱한 spec generator도 아닙니다. 단순 질문은 바로 답하고, 작은 수정은 최소한으로 확인해 고치며, 구현 작업은 계획-구현-검증으로 마무리하고, 모호한 제품/디자인/아키텍처 작업은 더 깊게 의도를 잡습니다.

## fable-mode란

fable-mode는 intent-aware work를 위한 단일 Codex operating mode입니다.

Codex가 어떻게 깊이를 조절할지 판단하도록 돕습니다.

- 단순 질문은 바로 답합니다.
- 작은 수정은 필요한 범위만 읽고 최소 변경으로 고칩니다.
- 일반 구현은 짧게 계획하고, 구현하고, 관련 검증을 합니다.
- 모호한 제품/디자인/아키텍처 작업은 intent framing과 audit lane을 사용합니다.
- 위험하거나 되돌리기 어려운 작업은 더 조심스럽게 멈춰 확인합니다.

UI나 디자인 작업에서는 결과물이 자동으로 웹페이지라고 가정하지 않습니다. 먼저 output archetype을 분류하고, 그다음 DOM, CSS layout, canvas, SVG, WebGL, fixed-stage, hybrid 중 맞는 substrate를 고릅니다. 이 흐름은 픽셀 에디터, 드로잉 도구, 그래프 편집기, 슬라이드 덱처럼 일반적인 DOM 카드/그리드로 만들면 어색하거나 무거워지는 작업을 피하도록 돕습니다.

이 플러그인은 비공식이며, 어느 특정 회사의 방식에 기대지 않고 독자적으로 작성되었습니다. Anthropic 또는 OpenAI와 제휴하거나 공식 관계를 맺고 있지 않습니다. 특정 회사, 모델, 제품, 비공개 모드, 원본 문서를 재현하거나 사칭하지 않으며, 어떤 독점 시스템 프롬프트도 포함하거나 재현하지 않습니다. UI/design 안내도 원본 프롬프트를 복사하거나 포함하지 않는 provider-neutral 문서입니다.

## 명령어로 설치하기 (Codex CLI)

이 페이지의 파일을 따로 내려받지 않아도 됩니다. 먼저 명령어를 입력하는 창을 열고, 아래 명령을 한 줄씩 실행해 주세요.

- Mac에서는 Spotlight에서 `Terminal`을 검색해 엽니다.
- Windows에서는 시작 메뉴에서 `CMD`, `명령 프롬프트`, 또는 `PowerShell`을 검색해 엽니다.

아래 기본 방법을 먼저 사용해 주세요. 이 방법은 `main`을 따라가므로, 업데이트할 때 현재 권장 문서를 받을 수 있습니다. 이 방법으로 설치가 끝나면 HTTPS 방법은 실행하지 않아도 됩니다.

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

<details>
<summary>고정 버전(v0.1.0)으로 설치하기</summary>

나중에도 같은 버전을 다시 설치해야 하거나, 팀 문서에서 정확한 버전을 맞춰야 한다면 태그에 고정해서 설치하세요.

```bash
# 1. 이 줄을 붙여넣고 Enter를 누릅니다.
codex plugin marketplace add Nam-Cheol/codex-fable-mode --ref v0.1.0

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

### 명령어 설치가 잘 안 될 때

Codex 버전이나 환경에 따라 명령어 설치가 실패할 수 있습니다. 그럴 때는 Codex를 실행한 뒤 `/plugins`를 열어 플러그인 화면에서 설치해 보세요.

1. Codex에서 `/plugins`를 엽니다.
2. `codex-fable-mode` 마켓플레이스가 보이면 선택합니다.
3. `Fable Mode` 또는 `fable-mode`를 찾습니다.
4. `Install plugin`을 눌러 설치합니다.

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

명령어 설치가 실패하면 Codex Desktop에서 `/plugins`를 열고 `codex-fable-mode`를 선택한 다음 `Install plugin`을 눌러 설치해 주세요.

## 사용 방법

한 번만 쓰는 작업:

```text
$fable-mode
이 컴포넌트의 텍스트 넘침을 고쳐줘.
```

긴 작업이나 `/goal`로 이어지는 작업:

```text
/goal Use $fable-mode for this task. Choose the smallest sufficient reasoning depth. For UI/design work, classify the output archetype and substrate before implementation.
```

goal이 활성 상태로 유지되는 동안에는 후속 메시지마다 `$fable-mode`를 반복하지 않아도 됩니다. 주제가 크게 바뀌었거나, 긴 압축 세션 뒤 흐름이 흐려졌거나, Codex가 이 작업 방식을 놓치는 것 같을 때 다시 언급하면 됩니다.

구현이나 디버깅:

```text
$fable-mode 이 버그를 원인 분석부터 테스트까지 확인해서 고쳐줘.
```

UI나 디자인 작업에 적용:

```text
$fable-mode 이 대시보드 화면을 제품 목적에 맞게 다시 설계하고 구현 전에 세 가지 방향을 비교해줘.
```

Codex는 계획, 코드 리뷰, 아키텍처, 디버깅, 신중한 구현, UI/프론트엔드 디자인 작업에서 이 스킬을 자동으로 참고할 수도 있습니다.

## 무엇이 달라지나요?

`fable-mode`는 Codex가 모든 일을 무겁게 다루지 않도록 돕습니다.

- L0: 단순 질문은 바로 답합니다.
- L1: 작은 버그나 CSS 문제는 가장 작은 관련 범위만 확인합니다.
- L2: 일반 구현은 짧게 계획하고, 구현하고, 검증합니다.
- L3: 제품, 디자인, 아키텍처 작업은 의도와 산출물 형태를 먼저 분류합니다.
- L4: 위험하거나 되돌리기 어려운 작업은 확인 질문과 더 강한 검증을 사용합니다.

## 디자인 동작

UI, frontend, design 작업에서 fable-mode는 결과물을 자동으로 webpage로 보지 않습니다.

먼저 output archetype을 분류합니다.

- webpage
- app screen
- creative tool
- game prototype
- deck
- animation
- editor
- dashboard
- data visualization
- design exploration

그다음 substrate를 고릅니다.

- DOM
- CSS layout
- canvas
- SVG
- WebGL
- fixed-stage
- hybrid

이렇게 해서 실제 작업면이 필요한 도구를 generic card/grid 구현으로 밀어 넣는 일을 줄입니다.

## 수동 검증

이 저장소는 문서 전용 플러그인이라 검증용 런타임 스크립트를 따로 추가하지 않습니다. 대신 [VALIDATION.md](./VALIDATION.md)에 manifest JSON 확인, 필수 skill/reference 파일 확인, hooks/MCP/app 설정이 없다는 확인 절차를 적어 두었습니다.

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

이 플러그인은 문서로 동작 방식을 안내하는 플러그인입니다. 새로운 도구, 자동 실행 스크립트, MCP 서버, 앱 연동, 의존성, postinstall 명령, API 호출 예제, telemetry, 네트워크 동작을 추가하지 않습니다. Codex의 정책, 사용자의 환경 정책, 저장소 지시사항, 도구 권한을 우회하지 않습니다.

## 저장소 구조

```text
.agents/plugins/marketplace.json
plugins/fable-mode/.codex-plugin/plugin.json
plugins/fable-mode/skills/fable-mode/SKILL.md
plugins/fable-mode/skills/fable-mode/references/intent-framing.md
plugins/fable-mode/skills/fable-mode/references/depth-gate.md
plugins/fable-mode/skills/fable-mode/references/ask-or-act.md
plugins/fable-mode/skills/fable-mode/references/audit-lanes.md
plugins/fable-mode/skills/fable-mode/references/output-archetype.md
plugins/fable-mode/skills/fable-mode/references/substrate-selection.md
plugins/fable-mode/skills/fable-mode/references/small-fix-protocol.md
plugins/fable-mode/skills/fable-mode/references/design-thinking.md
plugins/fable-mode/skills/fable-mode/references/final-response.md
plugins/fable-mode/skills/fable-mode/references/behavior-model.md
plugins/fable-mode/skills/fable-mode/references/tool-policy.md
plugins/fable-mode/skills/fable-mode/references/coding-workflow.md
plugins/fable-mode/skills/fable-mode/references/safety-boundaries.md
plugins/fable-mode/skills/fable-mode/references/design-anti-patterns.md
plugins/fable-mode/skills/fable-mode/references/design-exploration.md
plugins/fable-mode/skills/fable-mode/references/design-review-rubric.md
README.md
README.en.md
VALIDATION.md
Codex-Fable-Mode_hero.png
LICENSE
```
