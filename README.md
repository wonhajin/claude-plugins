# claude-plugins

wonhajin의 Claude Code 플러그인 마켓플레이스(`wonhajin`)입니다. 목록만 두고, 각 플러그인은 자기 레포의 `main`에서 받아 옵니다.

| 플러그인 | 설명 | 레포 |
|---|---|---|
| `privacy-mask` | 프롬프트 전송 전 로컬에서 개인정보·비밀값 마스킹 | [wonhajin/privacy_mask](https://github.com/wonhajin/privacy_mask) |
| `context-band` | 입력창 위 띠에 모델 · effort · 컨텍스트 사용량 · 세션 비용 표시 | [wonhajin/context_band](https://github.com/wonhajin/context_band) |

## 설치

```bash
claude plugin marketplace add wonhajin/claude-plugins
claude plugin install privacy-mask@wonhajin
claude plugin install context-band@wonhajin
```

새 버전은 `claude plugin update <플러그인>@wonhajin`으로 받습니다.

## 플러그인 추가

`.claude-plugin/marketplace.json`의 `plugins`에 항목을 추가합니다. 이름은 kebab-case(`-`)로, 그 플러그인 `plugin.json`의 `name`과 같아야 합니다.

```json
{ "name": "<plugin-name>", "source": { "source": "url", "url": "https://github.com/wonhajin/<repo>.git", "ref": "main" } }
```

`"source": "github"`(`owner/repo`)는 쓰지 않습니다. 그 형식은 `claude plugin update` 때 HTTPS 대체 없이 SSH로만 받아서, GitHub 계정에 SSH 키를 등록하지 않은 사람은 업데이트가 실패합니다(Claude Code 2.1.292 기준). `url`에 `https://` 주소를 주면 누구나 인증 없이 받습니다.
