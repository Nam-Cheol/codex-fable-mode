![Codex Fable Mode hero](./Codex-Fable-Mode_hero.png)

# Codex Fable Mode

[![Documentation-only plugin](https://img.shields.io/badge/type-documentation--only-2f6f5f)](#한계)
[![Codex plugin](https://img.shields.io/badge/Codex-plugin-111827)](#명령어로-설치하기-codex-cli)
[![Version v0.2.1](https://img.shields.io/badge/version-v0.2.1-6b7280)](#버전-운영)
[![Provider-neutral](https://img.shields.io/badge/guidance-provider--neutral-4b5563)](#한계)

[English README](./README.en.md)

`fable-mode`는 Codex가 사용자의 의도에 맞춰 산출물 형태, 사고 깊이, 절차, 도구 사용량을 먼저 잠그고 필요한 만큼만 움직이도록 돕는 문서 전용 플러그인입니다.

설치되는 스킬은 하나뿐입니다. 사용자는 항상 `$fable-mode`만 호출하면 됩니다. 이 스킬은 하네스도, 두 번째 런타임도, 딱딱한 spec generator도 아닙니다. 단순 질문은 바로 답하고, 작은 수정은 최소한으로 확인해 고치며, 구현 작업은 계획-구현-검증으로 마무리하고, 모호한 제품/디자인/아키텍처 작업은 더 깊게 의도를 잡습니다.

현재 라우팅은 특정 주제나 시각 스타일이 아니라 작업 행위 자체를 더 강하게 감시합니다. 어린이/우주/디자인 전용 모드가 아닙니다. 먼저 Output Lock으로 answer, edit, implementation, review, audit, design artifact, research, clarification, validation 중 주 산출물을 잠급니다. 그다음 Procedure Budget과 Tool Budget으로 계획, 질문, 파일 읽기, 검증이 필요한 만큼만 쓰이게 합니다.

[명령어로 설치하기](#명령어로-설치하기-codex-cli) · [Codex Desktop 설치](#codex-desktop-설치) · [사용 방법](#사용-방법) · [검증 보기](#수동-검증)

## 빠르게 보기

| 필요한 순간 | fable-mode가 돕는 방식 |
| --- | --- |
| 답만 필요한 질문 | 바로 답하고 불필요한 계획을 만들지 않습니다. |
| 작은 수정 | 가장 작은 관련 범위만 확인하고 고칩니다. |
| 구현 작업 | 짧게 계획하고, 구현하고, 관련 검증으로 마무리합니다. |
| 출력 형식이 흔들리는 작업 | Output Lock으로 answer, edit, implementation, review, audit, design artifact, research, clarification, validation 중 하나를 먼저 잠급니다. |
| 절차가 커지기 쉬운 작업 | Procedure Budget으로 질문, 계획, audit lane, 검증의 양을 제한합니다. |
| 도구 사용이 과해지기 쉬운 작업 | Tool Budget으로 필요한 근거와 변경, touched surface 검증까지만 도구를 씁니다. |
| 제품/디자인/아키텍처 | 의도, 산출물 형태, 근거, substrate를 먼저 분류합니다. |
| 형식이 애매한 작업 | 구현 도구와 실제 산출물 형식을 구분합니다. |
| 근거가 필요한 작업 | 파일, 자산, 측정, 현재 정보, 레퍼런스가 필요한지 확인합니다. |
| 위험한 작업 | 확인 질문과 더 강한 검증을 사용합니다. |

## Workflow

```mermaid
flowchart LR
    A["사용자 요청"] --> B["Intent framing"]
    B --> C["Output Lock"]
    C --> D{"Depth gate"}
    D --> E["Procedure budget"]
    E --> F["Constraints"]
    F --> G["Ask or act"]
    G --> H["Grounding/capability stop gates"]
    H --> I["Tool budget"]
    I --> J["Audit only if required"]
    J --> K["Implement or answer"]
    K --> L["Pre-final critique"]
    L --> M["짧게 보고"]
```

## fable-mode란

fable-mode는 intent-aware work를 위한 단일 Codex operating mode입니다.

Codex가 어떻게 깊이를 조절할지 판단하도록 돕습니다.

- 먼저 주 산출물을 answer, edit, implementation, review, audit, design artifact, research, clarification, validation 중 하나로 잠급니다.
- Output Lock은 reasoning depth, 읽을 reference, 질문할지 행동할지, 도구 허용 여부, 충분한 검증 범위, 최종 응답 길이를 정합니다.
- Procedure Budget은 단순 답변을 구현 작업으로 키우거나 작은 수정을 redesign으로 키우지 못하게 합니다.
- Tool Budget은 자신감 연출용 도구 사용을 막고, 근거 수집과 touched surface 검증까지만 도구를 쓰게 합니다.
- 단순 질문은 바로 답합니다.
- 작은 수정은 필요한 범위만 읽고 최소 변경으로 고칩니다.
- 일반 구현은 짧게 계획하고, 구현하고, 관련 검증을 합니다.
- 모호한 제품/디자인/아키텍처 작업은 intent framing과 필요한 audit lane을 사용합니다.
- 명시적인 제약은 계약처럼 다루고, 마무리 전에 지켰는지 다시 확인합니다.
- 출력 형식과 구현 도구를 구분해 웹페이지, dashboard, card UI 같은 익숙한 틀로 자동 해석하지 않습니다.
- 근거가 필요한 작업에서는 파일, 자산, 측정, 현재 정보, 레퍼런스를 확인하거나 부족함을 말합니다.
- 현재 환경의 도구와 권한으로 가능한 일인지 확인하고, 불가능하면 가장 가까운 정직한 경로를 제안합니다.
- 사용자가 청중을 지정하면 그 청중에 맞게 깊이, 언어, 상호작용 밀도, 증거 수준을 조절합니다.
- 위험하거나 되돌리기 어려운 작업은 더 조심스럽게 멈춰 확인합니다.

UI나 디자인 작업에서도 결과물이 자동으로 웹페이지라고 가정하지 않습니다. 먼저 output form, grounding, capability fit을 확인한 다음 DOM, CSS layout, canvas, SVG, WebGL, fixed-frame, asset-grounded media, hybrid 중 맞는 substrate를 고릅니다. 이 흐름은 실제 작업면이 필요한 도구를 일반적인 DOM 카드/그리드로 밀어 넣는 일을 줄입니다.

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
<summary>이미 태그된 고정 버전 예시(v0.2.1)</summary>

나중에도 같은 버전을 다시 설치해야 하거나, 팀 문서에서 정확한 버전을 맞춰야 한다면 태그에 고정해서 설치하세요. 아래는 이미 태그된 버전을 쓰는 예시입니다.

```bash
# 1. 이 줄을 붙여넣고 Enter를 누릅니다.
codex plugin marketplace add Nam-Cheol/codex-fable-mode --ref v0.2.1

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
/goal Use $fable-mode for this task. Choose the smallest sufficient reasoning depth. Check constraints, output form, grounding, capability fit, audience intent, and pre-final critique.
```

goal이 활성 상태로 유지되는 동안에는 후속 메시지마다 `$fable-mode`를 반복하지 않아도 됩니다. 주제가 크게 바뀌었거나, 긴 압축 세션 뒤 흐름이 흐려졌거나, Codex가 이 작업 방식을 놓치는 것 같을 때 다시 언급하면 됩니다.

구현이나 디버깅:

```text
$fable-mode 이 버그를 원인 분석부터 테스트까지 확인해서 고쳐줘.
```

UI나 디자인 작업에 적용:

```text
$fable-mode 이 화면을 제품 목적과 브랜드 기준에 맞게 다시 설계하고, 구현 전에 산출물 형식과 필요한 근거를 확인해줘.
```

형식을 잘못 해석하면 안 되는 작업에 적용:

```text
$fable-mode 이 요청은 웹페이지가 아니라 조작 가능한 시뮬레이터야. HTML을 쓰더라도 dashboard처럼 만들지 말고 매체를 먼저 판단해줘.
```

기본 사용 방식은 명시 호출입니다. 이 스킬은 `agents/openai.yaml`에서 implicit invocation을 꺼 두었기 때문에, 보통은 `$fable-mode`로 직접 불렀을 때 작동합니다.

도메인별 프롬프트는 [TEST_PROMPTS.md](./TEST_PROMPTS.md)에 평가 예시로만 둡니다. 그 예시들은 fable-mode의 내장 편향이나 core routing이 아닙니다.

## Output Lock과 예산

`fable-mode`는 Codex가 모든 일을 무겁게 다루지 않도록 먼저 주 산출물을 잠급니다.

Output Lock:

- answer
- edit
- implementation
- review
- audit
- design artifact
- research
- clarification
- validation

이 잠금은 이후 선택을 지배합니다.

- answer는 구현으로 커지지 않습니다.
- edit는 redesign으로 커지지 않습니다.
- review와 audit은 사용자가 요청하지 않으면 rewrite가 되지 않습니다.
- research는 필요한 source와 날짜 기준을 분리합니다.
- validation은 확인 대상 claim, 동작, 파일, artifact만 검증합니다.

Procedure Budget은 질문, 계획, audit lane, 검증의 양을 제한합니다.

- P0: 단순 답변은 계획 없이 바로 답합니다.
- P1: 작은 수정은 가장 작은 관련 범위만 확인합니다.
- P2: 일반 구현은 짧게 계획하고, 구현하고, 검증합니다.
- P3: 제품, 디자인, 아키텍처, review, audit, research는 필요한 구조만 씁니다.
- P4: 위험하거나 되돌리기 어려운 작업은 먼저 확인하고 단계화합니다.

Tool Budget은 도구를 근거, 변경, 검증에만 쓰게 합니다.

- T0: 안정적인 답변은 도구 없이 답합니다.
- T1: 필요한 파일, diff, 로그, 문서만 읽습니다.
- T2: 제한된 변경과 관련 검증을 합니다.
- T3: runtime, browser, screenshot, current source, asset이 필요한 경우에만 씁니다.
- T4: 권한 상승, destructive, broad 작업은 확인이 필요합니다.

도구는 자신감 연출용으로 쓰지 않습니다. 모든 것을 검증하지도 않습니다. 수정했거나 주장한 touched surface를 검증합니다.

## Depth Gate: L0-L4

Output Lock 이후 `fable-mode`는 가장 작은 충분한 사고 깊이를 고릅니다.

- L0: 단순 질문은 바로 답합니다.
- L1: 작은 버그나 CSS 문제는 가장 작은 관련 범위만 확인합니다.
- L2: 일반 구현은 짧게 계획하고, 구현하고, 검증합니다.
- L3: 제품, 디자인, 아키텍처 작업은 의도와 산출물 형태를 먼저 분류합니다.
- L4: 위험하거나 되돌리기 어려운 작업은 확인 질문과 더 강한 검증을 사용합니다.

그 위에 작업 행위 감시 장치가 더해졌습니다.

- Constraint integrity: 사용자의 명시 제약을 계약처럼 추출하고 검증합니다.
- Output form integrity: HTML, CSS, JS 같은 구현 도구와 실제 산출물 형식을 구분합니다.
- Grounding integrity: 사실, 시각, 코드베이스, 브랜드, 성능, 재현 근거가 필요한지 확인합니다.
- Capability fit: 현재 환경의 도구와 권한으로 필요한 근거와 검증을 수행할 수 있는지 판단합니다.
- Audience intent: 지정된 청중에 맞게 깊이, 언어, 증거 수준, 상호작용 밀도를 조절합니다.
- Pre-final critique: 제약, 형식, 근거, 역량, 작업 깊이, 의도 적합성을 마무리 전에 다시 봅니다.

## 출력 형식과 매체

fable-mode는 결과물을 자동으로 webpage로 보지 않습니다.

먼저 output form을 분류합니다.

- direct answer
- document
- code patch
- review
- webpage
- app screen
- creative tool
- game prototype
- deck
- animation
- editor
- dashboard
- data visualization
- simulation
- fixed-frame experience
- spatial or scene-based experience
- design exploration

그다음 substrate를 고릅니다.

- DOM
- CSS layout
- canvas
- SVG
- WebGL
- fixed-frame
- asset-grounded media
- hybrid

이렇게 해서 실제 작업면이 필요한 도구를 generic card/grid 구현으로 밀어 넣는 일을 줄입니다.

## 근거와 역량 판단

사용자가 실제 파일, 현재 정보, 재현 가능한 버그, 측정값, 브랜드 기준, 디자인 시스템, 시각 자산, 정확한 근거를 요구하면 fable-mode는 그 요구를 그럴듯한 근사치로 조용히 대체하지 않도록 안내합니다.

이 요구가 hard requirement라면 stop gate입니다. 필요한 근거, 자산, 측정, 재현, runtime, browser, 현재 정보 조회 같은 역량이 없으면 구현으로 들어가지 않습니다. 가능한 도구로 확인하거나, 사용자에게 필요한 자료를 묻거나, 제한된 답변/계획으로 output lock을 바꿉니다.

필요한 도구가 있으면 사용하고, 현재 환경에서 불가능하면 불가능하다고 말합니다. 그때는 지금 검증된 것, 추론한 것, 막힌 것, 더 정확한 결과를 위해 필요한 자산이나 도구를 분리해야 합니다.

## 수동 검증

이 저장소는 문서 전용 플러그인이라 검증용 런타임 스크립트를 따로 추가하지 않습니다. 대신 [VALIDATION.md](./VALIDATION.md)에 manifest JSON 확인, 필수 skill/reference 파일 확인, hooks/MCP/app 설정이 없다는 확인 절차를 적어 두었습니다.

## 버전 운영

기본 설치는 `--ref main`을 사용합니다. 이 플러그인은 실행 코드가 아니라 현재 권장 사고 워크플로 문서이므로, 일반 사용자는 업데이트할 때 최신 문서를 받는 편이 자연스럽습니다.

팀 문서나 재현 가능한 설치가 필요하면 `--ref v0.2.1`처럼 태그에 고정하세요. 짧은 문구 수정은 `plugin.json.version`을 유지할 수 있지만, 기본 동작 철학, reference 구조, 설치 방식, UI metadata가 바뀌면 patch 또는 minor version을 올립니다.

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

따라서 fable-mode는 더 나은 판단을 안내할 수는 있지만, 현재 환경에 없는 runtime tool을 만들어낼 수는 없습니다. 필요한 파일 읽기, 측정, 브라우징, 이미지 생성, 자산 수집, 외부 연동, 자동화 도구가 없거나 막혀 있다면 그것을 말하고 가능한 범위와 불가능한 범위를 분리해야 합니다.

## 저장소 구조

```text
.agents/plugins/marketplace.json
plugins/fable-mode/.codex-plugin/plugin.json
plugins/fable-mode/skills/fable-mode/SKILL.md
plugins/fable-mode/skills/fable-mode/agents/openai.yaml
plugins/fable-mode/skills/fable-mode/references/intent-framing.md
plugins/fable-mode/skills/fable-mode/references/output-lock.md
plugins/fable-mode/skills/fable-mode/references/depth-gate.md
plugins/fable-mode/skills/fable-mode/references/procedure-budget.md
plugins/fable-mode/skills/fable-mode/references/constraint-integrity.md
plugins/fable-mode/skills/fable-mode/references/ask-or-act.md
plugins/fable-mode/skills/fable-mode/references/output-form-integrity.md
plugins/fable-mode/skills/fable-mode/references/grounding-integrity.md
plugins/fable-mode/skills/fable-mode/references/capability-fit.md
plugins/fable-mode/skills/fable-mode/references/tool-budget.md
plugins/fable-mode/skills/fable-mode/references/audience-intent.md
plugins/fable-mode/skills/fable-mode/references/audit-lanes.md
plugins/fable-mode/skills/fable-mode/references/output-archetype.md
plugins/fable-mode/skills/fable-mode/references/substrate-selection.md
plugins/fable-mode/skills/fable-mode/references/small-fix-protocol.md
plugins/fable-mode/skills/fable-mode/references/pre-final-critique.md
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
TEST_PROMPTS.md
VALIDATION.md
Codex-Fable-Mode_hero.png
LICENSE
```
