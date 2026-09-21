# AI Engineering from Scratch — 전수조사 분석 및 활용 가이드 (한국어)

> 이 문서는 레포지토리 전체(3,401개 파일)를 전수조사하여 정리한 한국어 분석 노트입니다.
> 작성일: 2026-09-21

## 저장소 주소

| 구분 | URL |
|---|---|
| 이 저장소 (포크) | https://github.com/bmshin94/ai-engineering-from-scratch |
| 원본 저장소 (upstream) | https://github.com/rohitg00/ai-engineering-from-scratch |
| 공식 웹사이트 | https://aiengineeringfromscratch.com |
| 자격증 안내 | https://aiengineeringfromscratch.com/certifications.html |
| 창작자의 다른 프로젝트 | https://github.com/rohitg00/agentmemory |

라이선스: **MIT** (저작권 표시 및 라이선스 전문 유지 조건으로 상업적 이용·수정·재배포 가능)

---

## 1. 한 줄 정의

> AI/ML을 **수학 기초부터 자율 에이전트까지 523개 레슨**으로, 프레임워크 없이 맨손 구현하며 배우는
> 무료 오픈소스 커리큘럼. 여기에 **AI 에이전트가 직접 1:1 과외를 해주는 Agent Skills 8종**이 내장되어 있다.

- 523 레슨 / 20 페이즈 / 약 342시간
- 4개 언어: Python, TypeScript, Rust, Julia
- 12개 언어 번역 (한국어 랜딩 포함)
- 실측 트래픽: 월 114,584 독자 / 181,995 페이지뷰 (2026-08-29 기준)

---

## 2. 폴더 전수조사 결과

| 폴더 | 정체 | 내용 |
|---|---|---|
| `phases/` | **본체** | 20개 페이즈, 523개 레슨 |
| `skills/` | **AI 튜터 8종** | 이식 가능한 `SKILL.md` |
| `.claude/skills/` | 클로드 코드용 미러 | 클론 시 슬래시 커맨드 자동 인식 |
| `certifications/` | Claude 자격증 대비 | 4개 트랙, 33개 레슨, 모의고사 |
| `site/` | 웹사이트 소스 | 바닐라 JS 정적 사이트 |
| `api/` | Vercel 서버리스 함수 4개 | 레슨/마크다운/자격증 라우팅 |
| `scripts/` | 빌드·검증 자동화 23종 | 감사, 번역, 책 빌드, 스킬 설치 |
| `learning-paths/` | 진로별 커리큘럼 12종 | JSON 매니페스트 |
| `i18n/` | 12개 언어 번역 | `ko/` 한국어 포함 |
| `book/` | PDF/EPUB 빌드 설정 | Pandoc 테마·레이아웃 |
| `glossary/` | 용어집 | `terms.md`, `myths.md` |
| `outputs/` | 학습자 산출물 저장소 | skills/agents/prompts/mcp-servers |
| `.github/workflows/` | CI 3종 | 커리큘럼 검증, 번역, 책 빌드 |

---

## 3. 커리큘럼 지도 (523 레슨)

| Phase | 주제 | 레슨 수 |
|---|---|---:|
| 00 | Setup and Tooling | 12 |
| 01 | Math Foundations | 22 |
| 02 | ML Fundamentals | 18 |
| 03 | Deep Learning Core | 13 |
| 04 | Computer Vision | 28 |
| 05 | NLP Foundations to Advanced | 29 |
| 06 | Speech and Audio | 17 |
| 07 | Transformers Deep Dive | 16 |
| 08 | Generative AI | 15 |
| 09 | Reinforcement Learning | 12 |
| 10 | LLMs from Scratch | 24 |
| 11 | LLM Engineering | 17 |
| 12 | Multimodal AI | 25 |
| 13 | **Tools and Protocols (MCP)** | **31** |
| 14 | **Agent Engineering** | **54** |
| 15 | Autonomous Systems | 22 |
| 16 | Multi-Agent and Swarms | 25 |
| 17 | Infrastructure and Production | 28 |
| 18 | Ethics, Safety, Alignment | 30 |
| 19 | **Capstone Projects** | **85** |
| | **합계** | **523** |

### 레슨 한 개의 구조

```text
phases/<NN>-<phase>/<NN>-<lesson>/
├── docs/en.md     # 레슨 본문 (논문 인용 포함)
├── code/          # main.py / main.ts / *.rs / *.jl
├── quiz.json      # 6문항 (pre / check 단계 구분)
├── assets/        # 다이어그램 SVG
└── outputs/       # 재사용 가능한 산출물
```

### 레슨의 6단계 리듬

```text
MOTTO → PROBLEM → CONCEPT → BUILD IT → USE IT → SHIP IT
```

핵심 철학은 **Build It / Use It 분리**다. 먼저 프레임워크 없이 맨손으로 구현한 뒤,
같은 연산을 PyTorch 등 프로덕션 라이브러리로 다시 돌린다. 그래서 프레임워크가
블랙박스로 남지 않는다.

### 코드 파일 실측

| 언어 | 파일 수 |
|---|---:|
| Python | 643 |
| TypeScript | 129 |
| Julia | 20 |
| Rust | 10 |

대부분 `math`, `random`, `json`, `numpy` 등 표준/경량 라이브러리만 사용한다.

---

## 4. AI 튜터 스킬 8종

| 스킬 | 역할 | 상태 파일 |
|---|---|---|
| `start-learning` | 10문항 배치고사 → 개인 학습계획 생성 | `LEARNING.md` |
| `learn` | 1회 호출 = 1레슨 과외 (개념→코드→퀴즈→기록) | `LEARNING.md` |
| `find-your-level` | 시작 페이즈 진단 | - |
| `course-guide` | 막힌 주제 → 정확한 레슨으로 라우팅 | - |
| `check-understanding` | 페이즈 단위 퀴즈 | - |
| `learn-mcp` | MCP 17레슨 집중 코스 | `MCP-LEARNING.md` |
| `learn-agent-skills` | Agent Skills 5레슨 집중 코스 | `AGENT-SKILLS-LEARNING.md` |
| `claude-certification` | Claude 자격증 튜터 | `CLAUDE-CERTIFICATION.md` |

**설계상 영리한 점**: `learn` 스킬은 레포를 클론하지 않아도 동작한다.
로컬에 `phases/`가 있으면 로컬 파일을, 없으면
`raw.githubusercontent.com/rohitg00/ai-engineering-from-scratch/main/<path>`에서
레슨을 직접 스트리밍한다. 설치 부담이 사실상 0이다.

### 호스트별 호출 문법

| 호스트 | 시작 | MCP 코스 | 퀴즈 |
|---|---|---|---|
| Claude Code | `/start-learning` | `/learn-mcp` | `/check-understanding 13` |
| Codex | `start-learning` | `learn-mcp` | `check-understanding 13` |
| 기타 호스트 | `Use start-learning to begin the course.` | 자연어 요청 | 자연어 요청 |

슬래시 커맨드는 보편 문법이 아니다. `SKILL.md` 포맷만 이식 가능하고, 호출 문법은 호스트 소유다.

---

## 5. 재사용 가능한 산출물 508개

| 종류 | 개수 |
|---|---:|
| `skill-*.md` | 396 |
| `prompt-*.md` | 99 |
| `agent-*.md` | 2 |
| MCP 관련 스킬 | 13 |

대표 예시:
- `skill-mcp-server-scaffolder.md` — MCP 서버 뼈대 생성
- `skill-mcp-threat-model.md` — MCP 보안 위협 모델링 (툴 포이즈닝 대응)
- `skill-mcp-conformance-release-gate.md` — MCP 적합성 릴리스 게이트
- `prompt-api-troubleshooter.md` — API 에러 디버깅

레슨을 듣지 않아도 산출물만 설치해 바로 활용할 수 있다.

```bash
python3 scripts/install_skills.py ~/.claude/skills --type skill --dry-run   # 미리보기
python3 scripts/install_skills.py ~/.claude/skills --type skill             # 실제 설치
```

---

## 6. 설치 및 사용법

### 방법 A — AI 튜터 설치 (권장)

```bash
node --version && npx --version && python3 --version
npx skills add rohitg00/ai-engineering-from-scratch
```

### 방법 B — 클론해서 사용

```bash
git clone https://github.com/bmshin94/ai-engineering-from-scratch.git
cd ai-engineering-from-scratch
python3 phases/00-setup-and-tooling/01-dev-environment/code/verify.py --route beginner
python3 phases/01-math-foundations/01-linear-algebra-intuition/code/vectors.py
```

클론하면 `.claude/skills/` 덕분에 Claude Code가 스킬 8종을 자동 인식한다. `npx` 설치가 불필요하다.

### 방법 C — 웹사이트에서 읽기

https://aiengineeringfromscratch.com

### 권장 학습 리듬 (공식 5단계)

1. `docs/en.md`를 읽고 핵심 아이디어를 자기 말로 설명한다.
2. 코드는 복사하지 말고 직접 타이핑한다.
3. 레포 루트에서 레슨 명령을 실행한다.
4. 증거를 남긴다: 명령어, 작업 디렉터리, 종료 코드, 유의미한 출력, 변경한 산출물.
5. 출력을 설명하고 작은 변경을 스스로 가할 수 있을 때만 다음으로 넘어간다.

---

## 7. 정체 판별: 플러그인 / 스킬 / MCP

| 구분 | 판정 | 근거 |
|---|---|---|
| 플러그인 | 아님 | `plugin.json`, `.claude-plugin/`, `marketplace.json` 부재 |
| **Agent Skill** | **맞음** | `skills/*/SKILL.md` 8개 + `.claude/skills/` 미러 |
| MCP 서버 | 아님 | MCP는 **가르치는 주제**일 뿐, 레포 자체가 MCP 서버는 아님 |

### 세 개념 비교

| | Agent Skill | MCP | Plugin |
|---|---|---|---|
| 정체 | 마크다운 설명서 | 통신 프로토콜 | 배포 묶음 |
| 실행 방식 | 에이전트가 읽고 행동 | 서버 프로세스 실행 | 스킬·명령·MCP 묶음 |
| 대표 파일 | `SKILL.md` | `mcp.json` + 서버 코드 | `plugin.json` |
| 비유 | 업무 매뉴얼 | USB 포트 | 앱스토어 앱 |

---

## 8. API 토큰 필요 여부

523개 레슨 중 `ANTHROPIC_API_KEY` 또는 `OPENAI_API_KEY`를 언급하는 파일은 **9개(약 1.7%)** 뿐이다.

| 항목 | 비용 |
|---|---|
| 레포 사용료 | 무료 (MIT) |
| 레슨 실행 | 대부분 0원 (로컬 실행) |
| 레슨 스트리밍 | 0원 (공개 raw URL, 토큰 불필요) |
| 코딩 에이전트 호스트 | 사용자가 이미 쓰는 구독 |
| LLM API 키 | Phase 00-04, Phase 11 일부, Phase 19 일부에서만 |
| 자격증 응시료 | $99 ~ $175 (완전 선택) |

결론: Phase 0~10은 추가 비용 없이 완주 가능하다.

---

## 9. 왜 GitHub에서 유명한가 (분석 7가지)

1. **물량과 완성도** — 3,401개 파일, 523레슨 × (본문 + 다국어 코드 + 퀴즈 + 산출물).
2. **문제 정의의 날카로움** — "학생 84%가 AI 도구를 쓰지만 18%만 전문적 사용에 준비됐다고 느낀다."
3. **AI-native 학습이라는 새 카테고리** — 링크 모음이 아니라 에이전트가 직접 가르친다.
4. **"from scratch" 브랜드 공식** — `llm.c`, `nanoGPT`, `build-your-own-x` 계보.
5. **창작자 인지도** — Agent Memory 제작자, 기존 팬층 유입.
6. **접근성** — 12개 언어, 웹/터미널/전자책 3경로, MIT.
7. **프로급 운영** — CI 3종, 검증 스크립트 23개, `AGENTS.md` 기여 규칙, 자동 리뷰봇.

---

## 10. 로컬 에이전트 구축 활용도

관련 레슨이 **160개**에 달한다.

| Phase | 레슨 수 | 내용 |
|---|---:|---|
| 13 Tools and Protocols | 31 | MCP 서버/클라이언트/전송/보안/레지스트리 |
| 14 Agent Engineering | 54 | 에이전트 루프, 메모리, 플래닝, 서브에이전트, 평가 |
| 15 Autonomous Systems | 22 | 장기 실행, 자기수정 |
| 16 Multi-Agent and Swarms | 25 | 에이전트 협업, 토론 |
| 17 Infrastructure and Production | 28 | 배포, 서빙, 모니터링 |

### 바로 쓸 수 있는 캡스톤 (Phase 19)

- `01-terminal-native-coding-agent` — 터미널 네이티브 코딩 에이전트
- `02-rag-over-codebase` — 코드베이스 RAG
- `06-devops-troubleshooting-agent` — DevOps 트러블슈팅 에이전트
- `09-code-migration-agent` — 코드 마이그레이션 에이전트
- `10-multi-agent-software-team` — 멀티에이전트 소프트웨어 팀
- `13-mcp-server-with-registry` — 레지스트리 포함 MCP 서버
- `17-personal-ai-tutor` — 개인 AI 튜터

각 캡스톤은 Python과 TypeScript 구현을 모두 제공한다.

### 추천 3주 최단 루트

| 주차 | 내용 |
|---|---|
| 1주 | `phases/14-agent-engineering/01-the-agent-loop` — 에이전트 5대 구성요소를 stdlib 200줄 미만으로 구현 |
| 2주 | `phases/13-tools-and-protocols/06~09` (MCP 기초·서버·클라이언트·전송) + `15-mcp-security-tool-poisoning` |
| 3주 | `phases/19-capstone-projects/01-terminal-native-coding-agent` 완성 |

Phase 14-01 본문 인용:

> "2026년의 모든 에이전트는 2022년 ReAct 루프의 변형이다 — Claude Code, Cursor, Devin, Operator 포함.
> 프레임워크를 건드리기 전에 이 루프를 확실히 익혀라."

**에이전트 루프의 5대 구성요소**

1. 메시지 버퍼 (message buffer)
2. 툴 레지스트리 (tool registry)
3. 정지 조건 (stop condition)
4. 턴 예산 (turn budget)
5. 관찰 포매터 (observation formatter)

---

## 11. React / PHP 재구현 가능성

### 현재 스택 (실측)

```text
프론트엔드 : 바닐라 JS + HTML + CSS (React 미사용)
             site/app.js (28KB), figures-*.js 약 70개
빌드       : site/build.js (Node 스크립트, 92KB)
백엔드     : Vercel 서버리스 함수 4개 (api/*.js, CommonJS)
데이터베이스: 없음 (정적 파일 + JSON)
```

React도 DB도 쓰지 않는 순수 정적 사이트라 재구현 난이도가 낮다.

### React (Next.js) 버전

```jsx
// app/lesson/[...slug]/page.jsx
import fs from 'fs/promises';
import { MDXRemote } from 'next-mdx-remote/rsc';

export async function generateStaticParams() {
  // phases/ 스캔 → 523개 정적 경로 생성
}

export default async function LessonPage({ params }) {
  const md = await fs.readFile(
    `phases/${params.slug.join('/')}/docs/en.md`, 'utf8'
  );
  return (
    <article className="lesson">
      <MDXRemote source={md} />
      <QuizWidget path={params.slug} />
      <ProgressTracker />
    </article>
  );
}
```

추천 스택: Next.js 15 + MDX + Tailwind + shadcn/ui

### PHP (Laravel) 버전

```php
<?php
$raw   = $_GET['path'] ?? '';
$path  = preg_replace('/[^a-z0-9\-\/]/', '', $raw);
$file  = realpath(__DIR__ . "/phases/{$path}/docs/en.md");
$base  = realpath(__DIR__ . '/phases');

// Path Traversal 방어: 반드시 base 경로 하위인지 검증
if ($file === false || strpos($file, $base) !== 0) {
    http_response_code(404); exit('Not found');
}

$parsedown = new Parsedown();
echo $parsedown->text(file_get_contents($file));
```

추천 스택: Laravel 11 + Blade + Livewire + MySQL

**보안 주의**: 경로 파라미터는 반드시 정규화 + base 경로 검증을 거쳐야 한다 (Path Traversal 방어).

### 선택 기준

| 목적 | 추천 |
|---|---|
| 포트폴리오, 빠른 배포 | Next.js (Vercel 무료) |
| 회원제 유료 서비스 | Laravel (결제·관리자 구현 유리) |
| 한국 시장 상용 서비스 | Laravel (호스팅 저렴, PG 연동 자료 풍부) |

레슨 콘텐츠는 `.md`와 `.json`이라는 순수 데이터이므로 언어·프레임워크와 무관하게 재사용 가능하다.

---

## 12. 수익화 아이디어

### 12.1 법적 체크리스트

MIT 라이선스이므로 상업적 이용이 가능하나 **저작권 표시와 라이선스 전문 유지**가 조건이다.

| 항목 | 가능 여부 |
|---|---|
| 콘텐츠 기반 유료 서비스 | 가능 (출처·라이선스 표기 필수) |
| 번역본 판매 | 가능 |
| 스킬 개조 및 배포 | 가능 |
| "Claude Certified" 등 상표 사용 | **불가 — Anthropic 상표** |
| 기존 스폰서 배너(SerpApi 등) 재사용 | **불가 — 제거 필요** |
| "공식 파트너" 표기 | **불가** |

원칙: 콘텐츠는 재료일 뿐이며, 수익은 내가 더한 가치에서 나온다.

### 12.2 티어 1 — 즉시 실행 가능

**아이디어 1. 한국어 완역 + 로컬라이징 서비스** (추천도 5/5)

`i18n/ko/`는 랜딩 페이지만 번역되어 있고 523개 레슨 본문은 영어다. 한국 개발자의 실질적 진입 장벽이다.

- 수익 모델: 프리미엄(Phase 0~5 무료) + 구독 월 19,900원 또는 평생 이용권 199,000원
- 작업: LLM 초벌 번역 → 기술 용어 감수 (`scripts/translate_lessons.py` 재활용)
- 차별화: 한국 채용 시장 맞춤 예제, 국내 기업 사례 추가
- 초기 비용: 사실상 0원 (Vercel 무료 + 도메인)

**아이디어 2. 스킬 번들 판매** (추천도 4/5)

396개 스킬 중 엄선 + 한글화 + 개선. Gumroad / 크몽 / Lemon Squeezy 판매, 29,000~49,000원. 주말 2~3일이면 MVP 가능하며 가장 빠르게 첫 매출을 낼 수 있다.

**아이디어 3. 콘텐츠 마케팅 파이프라인**

523개 레슨 = 523개 포스트 소재. 유튜브·블로그·인프런으로 애드센스 + 제휴 + 강의 유입.

### 12.3 티어 2 — 1~3개월 투자

**아이디어 4. SaaS "AI 학습 트래커"** (추천도 5/5, 가장 유망)

현재 레포의 약점을 정확히 파고든다.

| 현재 한계 | SaaS의 해결 |
|---|---|
| 진도가 로컬 `LEARNING.md` | 클라우드 동기화 |
| 팀·기수 관리 불가 | 그룹 대시보드 |
| 수료증 없음 | 검증 가능한 수료증 |
| 학습 통계 없음 | 취약 페이즈 분석 리포트 |
| 결제 없음 | 구독 결제 |

- 스택: Next.js 또는 Laravel + Supabase + Stripe/토스페이먼츠
- 가격: B2C 월 9,900원 / B2B 팀당 월 99,000원

오픈소스가 콘텐츠를 무료로 제공하므로, **관리·협업·증명**을 판다.

**아이디어 5. 기업 사내교육 (B2B)** (추천도 4/5)

8주 부트캠프 형태. 커리큘럼은 이 레포, 제공 가치는 라이브 강의 + 코드 리뷰 + 사내 데이터 커스터마이징.
단가 500만~3,000만원/기업. 단가가 가장 높으나 영업이 필요하다.

**아이디어 6. MCP / 에이전트 전문 컨설팅** (추천도 5/5)

Phase 13~17의 160개 레슨을 무기로 전환한다.

- MCP 서버 구축 대행: 300만~1,000만원/건
- 사내 에이전트 PoC: 500만~2,000만원
- `skill-mcp-*` 13종이 작업 템플릿 역할

### 12.4 티어 3 — 장기 자산형

**아이디어 7. 전자책 / 종이책 출간**

`book/`에 Pandoc PDF/EPUB 빌드 설정이 이미 완비되어 있다.

```bash
python3 scripts/build_book.py
```

**아이디어 8. 자격증 대비반** — 명칭 주의

- 안전: "Claude 자격증 대비 스터디" (사실 서술)
- 위험: "공식 Claude Certified 과정" (상표 침해)

**아이디어 9. 커뮤니티 구독** — 디스코드 멤버십 월 9,900원. 100명이면 월 99만원.

### 12.5 추천 실행 로드맵

| 기간 | 실행 | 목표 |
|---|---|---|
| 0~1개월 | 스킬 번들 판매 + 블로그/유튜브 | 첫 매출, 인지도 |
| 1~3개월 | 한국어 완역 사이트 (Next.js) | 구독자 100명 |
| 3~6개월 | 학습 트래커 SaaS + MCP 컨설팅 | 반복 매출 + 고단가 |
| 6개월~ | B2B 기업교육 + 전자책 | 확장 |

### 12.6 핵심 인사이트

1. 콘텐츠가 무료라는 것은 경쟁자도 동일하게 가져간다는 뜻이다. 승부처는 **번역 품질, 한국적 맥락, 커뮤니티, 관리 기능**이다.
2. 가장 방어 가능한 해자는 **한국어 + 한국 시장**이다. 원저자가 따라오기 어려운 영역이다.
3. 지식을 파는 것보다 **지식으로 문제를 해결하는 쪽**이 단가가 훨씬 높다. 교육으로 신뢰를 쌓고 컨설팅으로 수확한다.

---

## 13. 참고 문서

| 문서 | 경로 |
|---|---|
| 기여 및 에이전트 운영 규칙 | `AGENTS.md` |
| 전체 로드맵 | `ROADMAP.md` |
| 레슨 작성 템플릿 | `LESSON_TEMPLATE.md` |
| 포크 가이드 | `FORKING.md` |
| 다국어 정책 | `docs/i18n.md` |
| 용어집 / AI 미신 | `glossary/terms.md`, `glossary/myths.md` |
| 자격증 시작 가이드 | `certifications/claude/GETTING_STARTED.md` |

---

## 14. 다음 액션 체크리스트

- [ ] `/start-learning` 실행해 `LEARNING.md` 학습계획 생성
- [ ] `python3 scripts/install_skills.py ~/.claude/skills --type skill --dry-run` 로 스킬 목록 확인
- [ ] `phases/14-agent-engineering/01-the-agent-loop` 부터 에이전트 루트 시작
- [ ] `phases/13-tools-and-protocols/15-mcp-security-tool-poisoning` 로 MCP 보안 확인
- [ ] 수익화 방향 결정: 한국어 완역(티어1) 또는 MCP 컨설팅(티어2)
