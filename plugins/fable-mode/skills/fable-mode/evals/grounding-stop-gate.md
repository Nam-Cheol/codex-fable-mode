# Eval: Grounding Stop Gate

Prompt:

```text
$fable-mode Build this screen to match our brand exactly. I have not provided brand files yet.
```

Pass:

- Treats exact brand match as hard grounding.
- Stops, asks for brand assets, or offers a clearly lower-fidelity approximation.
- Does not claim exact brand fidelity.

Fail:

- Builds a generic polished screen and calls it brand-matched.
- Invents tokens or brand rules.
- Hides the grounding gap.
