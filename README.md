# claude-skills

에이전트가 만든 코드를 머지 전에 거르는 리뷰 기준. 레포와 상관없는 일반 기준만 둔다. 레포마다 다른 기준(모듈 지도, 재사용할 것, 테스트 경계, 화면 토큰)은 각 레포의 `docs/review/`에 두고, 스킬이 그 문서를 먼저 읽는다.

## review-kit

| 스킬 | 보는 것 | 레포 기준 문서 |
| --- | --- | --- |
| `maintainability-review` | 기존 추상화 우회, 의존 방향, 변경 이유로 본 단위, 빠진 API·과한 추상화 | `docs/review/architecture.md` |
| `test-review` | 동작이 깨지면 실패하나, 리팩터링에 깨지지 않나, 이름만 읽어도 흐름이 보이나 | `docs/review/testing.md` |
| `ui-consistency-review` | 디자이너 없는 프로젝트에서 토큰·컴포넌트·상태 표현·문구가 기존 화면과 맞나 | `docs/review/design.md` |

세 스킬 모두 셀프 체크(구현 중), 변경 리뷰(PR), 점검(기존 코드 전체) 모드가 있고, 지적을 `blocking`과 `suggestion`으로 나눈다.

## 설치

로컬:

```
/plugin marketplace add es-kimo/claude-skills
/plugin install review-kit@es-kimo
```

GitHub Actions (`anthropics/claude-code-action@v1`):

```yaml
plugin_marketplaces: https://github.com/es-kimo/claude-skills.git
plugins: review-kit@es-kimo
claude_args: --allowedTools "Skill,..."
```
