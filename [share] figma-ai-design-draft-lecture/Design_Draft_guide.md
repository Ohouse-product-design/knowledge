# Figma + AI로 디자인 초안 만들기 — 통합 가이드

> 📌 비디자이너·초보자 기준으로 작성된 단계별 가이드입니다.
> 📌 모든 링크·프롬프트·클릭 순서를 그대로 복사해서 따라 할 수 있습니다.
> 📌 실무자 인터뷰 8가지 워크플로우를 기법별로 재구성한 문서입니다.

---

## 목차

1. [먼저 알아야 할 용어들](#1-먼저-알아야-할-용어들)
2. [사전 준비 — 도구 설치하기](#2-사전-준비--도구-설치하기)
3. [공통 4단계 프레임워크](#3-공통-4단계-프레임워크)
4. [초안 생성하기 — 6가지 핵심 루트](#4-초안-생성하기--6가지-핵심-루트)
5. [수정·디벨롭 기법 모음](#5-수정디벨롭-기법-모음)
6. [여러 화면이 연결된 플로우 프로토타입](#6-여러-화면이-연결된-플로우-프로토타입)
7. [A/B/C 베리에이션 만드는 3가지 방법](#7-abc-베리에이션-만드는-3가지-방법)
8. [공유·배포 방식 비교](#8-공유배포-방식-비교)
9. [막혔을 때 대응 — 3대 함정](#9-막혔을-때-대응--3대-함정)
10. [팀 자산화 전략 — 프로젝트가 쌓일수록 빨라지기](#10-팀-자산화-전략)
11. [내 상황에 맞는 방법 찾기](#11-내-상황에-맞는-방법-찾기)
12. [기억할 5가지 핵심 메시지](#12-기억할-5가지-핵심-메시지)
13. [외부 참고 자료](#13-외부-참고-자료)

---

## 1. 먼저 알아야 할 용어들

이 문서에 계속 등장할 이름들. 한 번만 읽고 넘어가세요.

### 🎨 Figma (피그마)
**한 줄 설명**: 웹브라우저에서 쓰는 디자인 툴.
- 홈페이지: https://www.figma.com
- 무료 회원가입 가능
- 이 가이드에서는 **이미 있는 피그마 파일**을 AI에게 전달하는 용도로만 씁니다.

### 🤖 Claude Code
**한 줄 설명**: 터미널에서 돌아가는 AI 에이전트. 자연어로 시키면 코드를 만들어 파일로 저장해줌.
- 다운로드: https://claude.com/claude-code
- 설치 후 터미널에서 `claude` 명령어로 실행

### 💻 Cursor (커서)
**한 줄 설명**: AI가 내장된 코드 에디터.
- 다운로드: https://cursor.com
- 무료 플랜 있음
- Claude Code가 만든 파일들을 열고 수정하는 용도

### 🔌 Figma MCP
**한 줄 설명**: Figma와 Claude Code를 연결해주는 "다리". 설치하면 AI가 피그마 파일을 직접 읽음.
- 공식 문서: https://help.figma.com/hc/en-us/articles/32132100833559
- 한 번만 설정해두면 계속 사용

### 🧪 Google AI Studio
**한 줄 설명**: 구글 AI 놀이터. 이미지를 넣고 "웹페이지로 만들어줘" 요청 가능.
- 주소: https://aistudio.google.com

### 🚀 Vercel (버셀)
**한 줄 설명**: 만든 프로토타입을 인터넷에 올려 링크로 공유.
- 주소: https://vercel.com
- 무료 플랜 있음

### 🎨 Figma Make
**한 줄 설명**: 피그마 내장 AI 기능. 피그마 안에서 프로토타입 생성.
- 주소: https://www.figma.com/make/

### 📦 플러그인 (Plugin)
**한 줄 설명**: 피그마에 설치하는 확장 기능. 피그마 메뉴에서 바로 설치.

### 💬 프롬프트 (Prompt)
**한 줄 설명**: AI에게 시키는 말. Claude에게 건네는 그 문장.

---

## 2. 사전 준비 — 도구 설치하기

**모두 다 설치할 필요는 없습니다.** 첫 실습은 Claude Code만 있으면 됩니다.

| 우선순위 | 도구 | 링크 | 언제 필요 |
|---------|-----|------|----------|
| 🟢 필수 | **Claude Code** | claude.com/claude-code | 모든 방식 |
| 🟢 필수 | **Figma 계정** | figma.com | 디자인 파일 열기 |
| 🔵 선택 | Cursor | cursor.com | 루트 4·5 |
| 🔵 선택 | Google AI Studio | aistudio.google.com | 이미지 우회 루트 |
| 🔵 선택 | Vercel | vercel.com | 배포·공유 시 |
| 🔵 선택 | Figma 데스크톱 앱 | figma.com/downloads | Figma MCP 사용 시 |

### 2-1. Claude Code 설치 (필수)
1. https://claude.com/claude-code 접속
2. "Install" 클릭 → 운영체제 맞춰 설치
3. 터미널에 `claude` 입력 → 실행되면 성공

> 💡 **터미널이 뭐예요?**
> - Mac: `Spotlight(Cmd+Space)` → "터미널" 검색 → 실행
> - Windows: 시작 메뉴 → "cmd" 검색 → 실행

### 2-2. Figma MCP 연결 (루트 2·6 필수)
1. 피그마 **데스크톱 앱** 설치 (웹 버전은 MCP 안 됨)
2. 데스크톱 앱 → Preferences → **"Enable Dev Mode MCP Server"** 체크
3. Claude Code에서 MCP 등록:
   ```bash
   claude mcp add --transport http figma https://mcp.figma.com/mcp
   ```
4. Claude Code 실행 후 `/mcp` → Figma → OAuth 인증
5. 확인: `claude mcp list` 에 `figma` 나오면 성공

---

## 3. 공통 4단계 프레임워크

어떤 방식을 선택하든 결국 이 4단계로 수렴합니다.

```
[1] 셋업        →  [2] 초안 생성   →  [3] 디벨롭·수정  →  [4] 공유·확인
    준비 단계        Figma→Code          반복 개선          프리뷰/배포
```

- **[1] 셋업**: 도구 설치, 피그마 파일 확보, PRD 정리
- **[2] 초안 생성**: 어떤 브릿지로 Figma를 코드로 옮길지 결정 → **4절** 참고
- **[3] 디벨롭·수정**: 반복 개선. 이게 가장 오래 걸림 → **5절** 참고
- **[4] 공유·확인**: 목적에 따라 프리뷰 방식 선택 → **8절** 참고

> 💡 **핵심 마인드셋**: 프로토타입은 피그마와 **100% 일치하지 않아도 된다**. 목적은 **UT 검증**이지 피그마 복제가 아니다. 중요한 화면·인터랙션에만 집중.

---

## 4. 초안 생성하기 — 6가지 핵심 루트

피그마(또는 아이디어)를 코드로 옮기는 방법. 상황에 맞게 선택하세요.

### 루트 요약 비교

| 루트 | 난이도 | 세팅 | 추천 상황 |
|-----|-------|-----|----------|
| **4-1. 경량 루트** | ⭐ | 최소 | 처음 해보는 분 |
| **4-2. Figma MCP 정밀 루트** | ⭐⭐ | 보통 | 더 정확한 결과 필요 |
| **4-3. Figma Make 내장 루트** | ⭐ | 최소 | 피그마 안에서 완결 |
| **4-4. 이미지 우회 루트** | ⭐⭐⭐ | 보통 | MCP 결과가 엉망일 때 |
| **4-5. 플러그인 Export 루트** | ⭐⭐⭐ | 많음 | 레이어 컨벤션이 깔끔한 파일 |
| **4-6. ODS 특화 루트** | ⭐⭐ | 보통 | 오늘의집 ODS 과업 |

---

### 4-1. 경량 루트 — Figma URL을 Claude Code에 던지기

**핵심**: 피그마 프레임 링크만 있으면 끝. 세팅 거의 없음.

#### 준비물
- [x] Claude Code 설치됨
- [x] 피그마 파일 링크

#### 따라하기

**Step 1. 피그마에서 프레임 링크 복사**
1. 피그마 파일 열기
2. 만들고 싶은 화면(프레임) 클릭
3. 우클릭 → **Copy/Paste as** → **Copy link to selection**
4. 클립보드에 다음과 같은 URL이 복사됨:
   ```
   https://www.figma.com/design/AbCdEfG12345/MyDesign?node-id=1-234
   ```

**Step 2. 작업 폴더 만들기**
```bash
cd ~/Desktop
mkdir my-prototype
cd my-prototype
```

**Step 3. Claude Code 실행**
```bash
claude
```

**Step 4. 프롬프트 복붙 (URL만 바꾸기)**
```
첨부한 url 대로 디자인 구현해줘.
만든 다음에 로컬 서버로 띄워서 브라우저에서 확인할 수 있게 해줘.

URL: (여기에 피그마 프레임 링크)
```

**Step 5. 브라우저에서 확인**
- 터미널에 "Server running at http://localhost:3000" 나오면 접속
- 만들어진 프로토타입이 보이면 성공

---

### 4-2. Figma MCP 정밀 루트

**핵심**: Figma MCP라는 "다리"를 설치하면 AI가 피그마를 더 정확하게 읽음.

#### 준비물
- [x] Claude Code 설치됨
- [x] Figma MCP 연결 완료 (2-2 참고)
- [x] 피그마 파일 링크

#### 따라하기

**Step 1. 피그마에서 프레임 링크 복사** (4-1과 동일)

**Step 2. 작업 폴더 + Claude Code 실행**
```bash
cd ~/Desktop && mkdir my-prototype-v2 && cd my-prototype-v2 && claude
```

**Step 3. 프롬프트 복붙**
```
@피그마링크@ 이 화면을 똑같이 html로 만들어줘.
Figma MCP로 화면 읽어서 구조를 정확하게 파악해줘.
```

**Step 4. 하나씩 디벨롭하기**
```
상단 탑바는 sticky 되게 해줘
```
```
@이 영역@은 버튼을 눌렀을 때 아래로 펼쳐지게 해줘
```
```
카드를 클릭하면 상세 화면으로 이동하는 애니메이션을 넣어줘
```

> 💡 `@이 영역@`처럼 **구체적으로 지칭**하는 게 핵심. "저기 위에"는 AI가 잘못 이해합니다.

---

### 4-3. Figma Make 내장 루트

**핵심**: 피그마 안에 내장된 AI. 별도 터미널이나 에디터 없이 완결.

#### 준비물
- [x] 피그마 계정 (Figma Make 가능한 플랜)
- [x] 피그마 파일 링크

#### 따라하기

**Step 1. Figma Make 접속**
1. https://www.figma.com 로그인
2. 상단 메뉴 또는 홈에서 **"Make"** 선택
3. 새 Make 프로젝트 생성

**Step 2. 핵심 원칙 — 모든 요소를 "빠짐없이" 나열**

❌ 나쁜 예:
```
상품 상세 페이지 만들어줘
```

✅ 좋은 예:
```
@피그마링크@

이 화면을 똑같이 만들어줘.

상품정보는 이렇게 만들어줘.
브랜드명부터 상품명, 상품명 옆에 공유하기 아이콘,
리뷰, 할인율, 정상가, 판매가, 쿠폰할인가, 쿠폰 받기 버튼,
장바구니 쿠폰 안내까지 모두 포함해줘.

텍스트 스타일과 사이 간격과 컬러까지 동일하게 맞춰서 만들어줘.
```

→ 눈에 보이는 **모든 요소**를 나열해야 AI가 빠뜨리지 않음.

**Step 3. 하나씩 디벨롭** (4-2 Step 4와 동일)

---

### 4-4. 이미지 우회 루트 — Google AI Studio

**핵심**: Figma MCP가 제대로 안 먹을 때 **이미지 업로드**로 프로토타입을 받아옴.

#### 왜 이 루트인가?
> 💬 *"피그마 MCP 연결로 디자인 시스템 토큰을 읽게 해도 디자인이 엉망으로 나와서 손 대야 할 곳이 너무 많더라고요. 그래서 AI Studio 경유 경로를 선호합니다."*

#### 준비물
- [x] Google 계정
- [x] Cursor 설치됨
- [x] 피그마 파일 (캡처 가능한 상태)

#### 따라하기

**Step 1. 피그마 화면 캡처**
- Mac: `Cmd + Shift + 4` → 영역 드래그
- Windows: `Win + Shift + S` → 영역 드래그
- 프레임 전체가 보이게

**Step 2. Google AI Studio 접속**
1. https://aistudio.google.com 접속 → 구글 로그인
2. 좌측 **"Chat"** 또는 **"Create Prompt"** 클릭
3. 모델 선택 (기본 최신 Gemini)

**Step 3. 이미지 업로드 + 프롬프트**
1. 📎 클립 아이콘 → 캡처 이미지 선택
2. 프롬프트 복붙:

```
첨부한 피그마 시안을 기반으로 웹 프로토타입을 만들어줘.

요구사항:
- (이 화면이 뭐 하는 화면인지 설명)
- (중요한 동작 1)
- (중요한 동작 2)
- 모바일 기준 (width 390px)
- HTML, CSS, JavaScript 파일로 분리해서 만들어줘

각 파일의 전체 코드를 보여줘.
```

**Step 4. 코드 다운로드**
1. AI Studio가 만든 `index.html`, `style.css`, `script.js` 코드를 복사
2. 로컬에 같은 폴더(예: `~/Desktop/my-prototype-v3/`)에 저장

**Step 5. Cursor에서 폴더 열기**
1. Cursor 실행
2. **File → Open Folder** (`Cmd+O`) → Step 4 폴더 선택
3. `index.html` 더블클릭 → 브라우저에서 열림

**Step 6. Cursor 채팅 (`Cmd+L`)에서 디벨롭 요청**

---

### 4-5. 플러그인 Export 루트 — autoHTML

**핵심**: 피그마 플러그인으로 HTML 코드를 **먼저 뽑고**, 그 코드를 Cursor에서 AI로 다듬는 방식.

#### 준비물
- [x] 피그마 계정
- [x] Cursor 설치됨

#### 따라하기

**Step 1. autoHTML 플러그인 설치**
1. 피그마 파일 열기
2. **Resources** (`Shift+I`) → **Plugins** 탭
3. 검색창에 **"autoHTML"**
4. **Install** 클릭

**Step 2. 프레임 선택 후 플러그인 실행**
1. 변환할 프레임 클릭
2. 상단 **Plugins → autoHTML** 실행
3. **"Generate HTML"** 클릭
4. HTML 코드 **Copy**

**Step 3. Cursor에서 작업 시작**
1. Cursor 실행 → 새 폴더 열기
2. `index.html` 파일 생성 → 코드 붙여넣기 → 저장

**Step 4. Cursor AI에게 다듬기 요청**
```
이 HTML은 피그마의 autoHTML 플러그인으로 export한 코드야.
구조는 이대로 유지하면서:
1. 반응형이 되도록 CSS를 정리해줘 (모바일 우선)
2. 버튼 hover 효과 추가해줘
3. 클릭 이벤트가 필요한 요소들은 JavaScript로 기본 동작 추가해줘
```

> 💡 **중요**: 피그마 파일의 **레이어 이름**이 `Frame 17`, `Rectangle 42`처럼 기본값이면 AI가 헷갈림. **의미 있는 이름**(`header`, `product-card`, `submit-button`)으로 바꿔두면 결과가 훨씬 좋아집니다.

---

### 4-6. ODS 특화 루트 — ods-pdp skill

**핵심**: 오늘의집 ODS 디자인 시스템에 맞춰 만들어진 전용 스킬 사용.

#### 준비물
- [x] `ods-pdp skill` 접근 권한 (내부 도구)
- [x] 기존 디자인 화면 (피그마 또는 스크린샷)

#### 시나리오 A — 명확한 스펙이 있는 과업

**Step 1. 시안 제안 요청**
```
디자인 시안을 제안해줘.

기존 디자인 화면: (피그마 링크 또는 스크린샷 첨부)

요구사항:
- (화면의 목적)
- (주요 기능 1)
- (주요 기능 2)

ods 디자인 시스템 기준으로 만들어줘.
```

**Step 2. PRD 함께 고도화**
```
방금 만든 시안을 기반으로 PRD를 정리해줘.
- 화면 목적
- 주요 유저 시나리오
- 필요한 화면 상태 (로딩/에러/빈 상태)
- 데이터 요구사항
```

**Step 3. 피그마로 최종 보완** — AI로 해결 안 되는 부분은 수동 조정

#### 시나리오 B — 인터랙션이 필요한 과업

1. 피그마에서 **스케치 수준**으로 빠르게 디자인 (완벽하게 만들지 말 것)
2. ods-pdp skill로 HTML 프로토타입 생성:
   ```
   (피그마 링크 첨부)
   이 디자인을 기반으로 ods 시스템을 사용한 HTML 프로토타입을 만들어줘.
   인터랙션에 집중해서 만들어줘. 완벽한 디자인보다 동작이 중요해.
   ```
3. 로컬 확인 → Vercel 배포 (8절 참고)

---

## 5. 수정·디벨롭 기법 모음

초안을 만든 다음이 **가장 시간이 많이 드는 단계**입니다. 여기 있는 7가지 기법을 상황에 맞게 섞어 쓰세요.

### 5-1. 기본 원칙 3가지 (공통)

#### 원칙 ① 잘게 쪼개기
> "깨지는 컴포넌트만 셀렉해서 다시 재생성 요청"
> "전체 이미지보다 모듈, 컴포넌트 단위로 잘게 쪼개서 전달"

- ❌ 전체 재생성
- ✅ 깨진 영역만 선택해서 부분 재요청

#### 원칙 ② 수치를 무조건 명시
AI는 스펙에 없는 숫자를 상상으로 채워 넣습니다.

❌ 나쁜 예:
```
카드를 여러 개 배치해줘
```

✅ 좋은 예:
```
카드를 정확히 6개 배치해줘.
- 그리드: 2열 x 3행
- 카드 간 간격: 가로 16px, 세로 24px
- 카드 너비: 화면 너비에 맞춰 자동
- 카드 높이: 180px 고정
```

#### 원칙 ③ 변경 전 상태 저장 (git commit)
수정이 누적되면 엉뚱한 곳이 깨집니다.

```bash
# 작업 폴더에서 한 번만 실행:
git init
git add .
git commit -m "초기 상태"
```

큰 변경 전마다:
```bash
git add . && git commit -m "여기까지 잘 됨 - (설명)"
```

깨졌을 때 되돌리기:
```bash
git reset --hard HEAD
```

---

### 5-2. QA 스타일 번호 매기기 ⭐

수정 사항을 **1, 2, 3 번호**로 매겨서 한 번에 전달. AI가 누락 없이 처리.

**프롬프트 (복붙용)**:
```
아래 수정사항을 반영해줘. (첨부 이미지 참고)

1. Radius 12로 변경
2. 텍스트 값 semibold인지 확인 및 변경 필요
3. (수정사항 3)
4. (수정사항 4)
```

**왜 효과적인가**
- AI는 번호 매겨진 지시를 **누락 없이** 처리
- "이것도 좀 바꿔주고 저것도..."보다 훨씬 정확
- 재확인도 쉬움 ("1번은 됐는데 3번이 안 됐어" 식으로)

> 💡 QA 시트를 개발자에게 전달하듯이 명확하게.

---

### 5-3. 이미지로 잘게 잘라 재전달

수치를 말로 전달하기 어려울 때.

**순서**:
1. 수정이 필요한 **영역만** 캡처 (전체 X)
2. Claude Code 또는 Cursor에 이미지 첨부
3. 프롬프트:

```
이 이미지랑 동일하게 다시 맞춰줘.
칩 영역이 2열 그리드로 나와야 하고,
버튼은 하단에 full width로.
```

**AS-IS / TO-BE 패턴** (디자인 변경 시)

프로젝트 진행 중 디자인이 수정되면 **변경 전·후 이미지를 모두 캡처**해서 전달:

```
Flow는 동일해.
아래 두 이미지 참고해서 디자인 변경해줘.

[AS-IS 이미지 첨부]
[TO-BE 이미지 첨부]

이 이미지에서 이 이미지로 디자인이 변경되었으니
프로토타입에서도 동일하게 변경해줘.
```

---

### 5-4. 프롬프트 오브 프롬프트 패턴 ⭐

말로 설명하기 어려운 인터랙션(바텀시트, 복잡한 트랜지션)을 요청할 때.

**핵심 아이디어**: *"어떻게 설명해야 AI가 알아들을까"를 **또 다른 AI에게 물어보는 것***

**Step 1. Claude에게 프롬프트 생성 요청**
```
네이버 지도 앱의 바텀시트 같은 걸 만들고 싶어.
아래에서 위로 끌어올릴 수 있고, 세 단계(닫힘/반/열림)로 고정되고,
끌어올리면 검색 결과 리스트가 나오는 구조야.

이걸 Cursor AI에게 정확하게 구현시킬 수 있도록
상세한 프롬프트로 변환해서 제안해줘.
position, z-index, transition 같은 세부 스펙도 포함해서.
```

**Step 2. AI가 만든 상세 프롬프트를 Cursor에 그대로 붙여넣기**

→ AI가 `position`, `z-index`, `transition` 등 세부 스펙까지 알아서 채운 프롬프트가 나옵니다.

---

### 5-5. Design to Figma 역방향 루트 (레퍼런스 기반 초안)

보통은 Figma→코드 방향이지만, 역으로 **레퍼런스 이미지를 피그마 안으로 가져와서** ODS 컴포넌트로 재구성할 수 있습니다.

**Step 1. 만들고 싶은 화면을 설명하거나 PRD/회의록 준비**

**Step 2. 피그마 캔버스에 ODS 페이지 링크 복붙**

**Step 3. 피그마 캔버스에 레퍼런스 이미지 직접 붙여넣기**
- 경쟁 서비스 스크린샷, 벤치마크 이미지 등

**Step 4. 레퍼런스 기반 초안 요청**
```
레퍼런스 참고하되, ODS 컴포넌트 활용해서 초안 만들어줘.
```

→ ODS 디자인 시스템에 맞춰 **재해석된 초안**이 나옵니다.

---

### 5-6. 화면 패턴 재사용

반복 사용되는 구조가 발견되면 별도 문서로 빼두고 재사용.

**Step 1.** 첫 구현 후 패턴 정의 문서 생성 (예: `상품카드_패턴.md`)

**Step 2.** 다음에 쓸 때:
```
{page이름} 화면을 구현할 때
{page이름} 패턴을 참조해서 구현해줘
```

→ 프로젝트가 쌓일수록 속도가 빨라지는 구조.

---

### 5-7. 요소 하나씩 클릭해서 수정

패딩·마진 같은 작은 수정은 **사이드 패널에서 요소 하나씩 클릭해서** 요청.

❌ 한꺼번에:
```
카드 3개의 간격, 텍스트 크기, 색상 모두 바꿔줘
```

✅ 하나씩:
```
(카드 클릭) 이 카드의 좌측 패딩을 24px로 바꿔줘
```

→ 확인 후 다음 요소로 넘어가기.

---

## 6. 여러 화면이 연결된 플로우 프로토타입

UT 돌릴 때 화면이 여러 개 이어지는 플로우가 필요한 경우.

### 6-1. 피그마에서 분홍 화살표로 플로우 연결 ⭐

가장 창의적인 기법 중 하나. 피그마에서 **화면 간 이동을 분홍 화살표로 그려두고** 그 플로우대로 프로토타입을 만들게 합니다.

#### 사전 준비 (피그마)
1. 피그마 캔버스에 여러 화면 배치
2. 화면 A의 버튼 → 화면 B로 이동 관계를 **분홍색 화살표**로 그리기
3. 모든 화면을 하나의 Frame으로 묶기
4. Frame 전체 선택 → **Copy link to selection**

#### 프롬프트 (복붙용)
```
이 링크 타고가면 화면별로 어떻게 동작하는지
분홍색 화살표로 flow 연결해뒀는데
그 순서대로 프로토타입 만들어줘.

링크: (Frame 전체 링크)
```

> 💬 *"놀랍게도 잘 만들어줌"*

### 6-2. 모바일 버전 팁 (2가지 프롬프트)

**웹에서 앱처럼 보이게 하고 싶을 때**:
```
375*812 사이즈에 맞게 앱 화면으로 보이게 만들어줘
```

**핸드폰에서 접속했을 때 웹 프레임 없애고 싶을 때**:
```
웹 프레임 없애고, 모바일 최적화로 만들어줘
```

---

## 7. A/B/C 베리에이션 만드는 3가지 방법

UT 돌릴 때 여러 안을 비교하고 싶은 경우.

### 7-1. 접근법 A — 프롬프트형 (한 번에 ABCD 요청)

**UX 베리에이션 (복붙용)**:
```
선택한 프레임의 플로우를 크게 깨지 않는 상태에서
아래 정의한 기대 액션을 달성할 수 있는
UX 플로우 시안 4가지(A, B, C, D)를 제안해줘.

기대 액션: (예: "사용자가 상품을 찜 목록에 추가한다")
```

**UI 베리에이션 (복붙용)**:
```
아래 데이터를 기반으로 상품 카드 모듈 시안 ABC를 제안해줘.

데이터:
- 상품명
- 브랜드명
- 판매가
- 정상가
- 할인율
- 썸네일 이미지
- 리뷰 개수
- 별점
```

### 7-2. 접근법 B — 베이스 복제형 ⭐⭐

**가장 추천**. UT에서 비교하기 편합니다.

#### 아이디어
베이스 프로토타입을 하나 만들고 → **시작화면(메뉴)**에서 A/B/C안으로 분기.

#### Step 1. 베이스 프로토타입 먼저 만들기 (4절 중 하나 사용)

#### Step 2. 복붙용 프롬프트
```
첫 시작화면을 하나 만들어줘.
그리고 시작화면에 A안이라고 버튼을 만들고
그걸 누르면 현재 만들어진 프로토타입이 나오게 해줘.

그리고 첫 시작화면에 B안과 C안 버튼도 추가해줘.
B안과 C안도 A안과 동일하게 우선 작동하도록 만들어줘.

이어서 B안과 C안을 개선할게.
```

#### Step 3. 각 안 개선하기
```
B안에서만 상단 네비게이션을 숨기고,
대신 플로팅 버튼을 우측 하단에 추가해줘.
```
```
C안에서만 카드 리스트를 그리드가 아니라 세로 리스트로 바꿔줘.
```

### 7-3. 접근법 C — 제약 풀기형 ⭐

이미 만든 초안에서 변형을 만들 때. **"꼭 ~가 아니어도 돼"** 라는 표현이 핵심.

**Step 1. 화면 배경 설명**
```
이 화면은 포인트 적립 안내를 보여주는 화면이야.
사용자가 해당 페이지에 진입했을 때
얼마의 포인트를 받을 수 있는지 시각적으로 강조해야 해.
```

**Step 2. 현재 시안 설명**
```
나는 관련된 아이콘과 실제 적립되는 포인트를 함께 보여주는 시안을
배너 형태로 만들었어.
```

**Step 3. 제약 풀기 프롬프트** ⭐
```
UI가 꼭 배너 형태가 아니어도 돼.
UI 형태, 위치 등 다양하게 고려해서 새로운 시안들을 만들어줘.
```

**핵심**: *"꼭 ~가 아니어도 돼"* — AI에게 **"기존 형식의 제약을 풀어도 된다"**는 신호.

### 세 접근법 비교

| | 접근법 A (프롬프트형) | 접근법 B (베이스 복제형) | 접근법 C (제약 풀기형) |
|-|---------------------|------------------------|----------------------|
| 생성 속도 | 빠름 (한 번에 4개) | 느림 (순차적) | 보통 |
| 차별화 | AI가 자유롭게 해석 | 내가 직접 통제 | AI가 형식 제약 풀어 재해석 |
| UT 적합성 | ❌ (각각 따로 전달) | ✅ (시작 메뉴 통합) | ⚠️ (후속 정리 필요) |
| 베이스 프로토 필요 | ❌ | ✅ | ✅ |
| 아이디어 발산 | ✅ | ❌ | ✅✅ |

---

## 8. 공유·배포 방식 비교

| 방식 | 세팅 난이도 | 추천 상황 |
|------|-----------|----------|
| **Claude Code 채팅창 프리뷰** | ⭐ (없음) | 혼자 빠르게 확인 |
| **Cursor 로컬 웹뷰** | ⭐⭐ (보통) | 개발 중 반복 확인 |
| **Vercel 배포** | ⭐⭐⭐ (약간) | 팀·개발자와 공유, UT |

### 8-1. Claude Code 채팅창 프리뷰
Claude Code에 요청:
```
만든 걸 로컬 서버로 띄워서 브라우저에서 확인할 수 있게 해줘
```

### 8-2. Cursor 로컬 웹뷰
Cursor에서 `index.html` 더블클릭 → 브라우저 오픈
또는 터미널에서:
```bash
cd (폴더 경로)
python3 -m http.server 3000
```

### 8-3. Vercel 배포

**방법 A — 웹사이트에서**
1. https://vercel.com 로그인
2. "New Project" → GitHub 리포 연결 또는 폴더 업로드
3. "Deploy" 클릭
4. 공유 가능한 URL 생성 (예: `deploy-indol-chi.vercel.app`)

**방법 B — CLI로**
```bash
npm install -g vercel
cd (프로토타입 폴더)
vercel
```
질문에 답하면 자동 배포.

---

## 9. 막혔을 때 대응 — 3대 함정

실무자들이 공통으로 겪는 3가지. 가장 체계적인 정리입니다.

### 함정 ① 복잡한 인터랙션이 꼬임

**증상**: 바텀시트의 z-index 뒤집힘, 스크롤 트리거 오작동.

**대응법 1. 캡처해서 다시 전달**
```
이 부분이 이상해. 스크린샷을 참고해서 고쳐줘.
현재 문제: (뭐가 이상한지 구체적으로)
기대 동작: (어떻게 되어야 하는지)
```

**대응법 2. 프롬프트 분할**
```
1단계: 바텀시트의 기본 레이아웃만 먼저 만들어줘. 확인 후 다음 단계 진행.
```
확인 후 →
```
2단계: 이제 드래그해서 위아래로 움직이는 기능 추가해줘.
```
확인 후 →
```
3단계: 세 단계(닫힘/반/열림) 스냅 위치 설정해줘.
```

### 함정 ② AI가 수치를 임의로 채움

**대응법**: 모든 수치 명시 + 결과 반드시 검증 (5-1 원칙 ② 참고).

### 함정 ③ 수정이 쌓이다 엉뚱한 곳이 깨짐

**대응법**:
- `git commit`으로 상태 저장 (5-1 원칙 ③ 참고)
- 변경 범위를 **좁게** 지정:
```
다른 건 절대 건드리지 말고, 상품 카드의 그림자만 살짝 진하게 바꿔줘.
```

### 빠른 되돌리기 프롬프트 (복붙용)
```
방금 전 변경 취소해줘. 이전 상태로 되돌려줘.
```
```
방금 수정한 부분에서 X 부분만 다시 원래대로 되돌려주고, 나머지는 그대로 둬.
```

---

## 10. 팀 자산화 전략

프로젝트가 쌓일수록 **속도가 빨라지는 구조**를 만드는 법.

### 10-1. 셋업 문서 3종 세트

프로젝트 시작 전에 **팀 공용으로** 한 번 만들어두고 계속 재사용.

**문서 a. ODS 파운데이션 문서**
- 토큰, 레이아웃(breakpoint) 관리
- auto-fill, 패딩 등 정의

**문서 b. 컴포넌트·에셋 관리 문서**
- b-1: 디자인시스템 에셋 ↔ 스토리북 연결 (`fe.co-workerhou.se/catalog`)
- b-2: 글로벌 컴포넌트 구조 정의 (GNB, 네비게이션 등)

**문서 c. 컨트롤 패널 UI 문서**
- 프로토타입 프리뷰 외부의 컨트롤 (A/B 메뉴, 핸들 등)

### 10-2. 화면 패턴 문서화 (5-6 절 참고)

같은 구조가 두 번 이상 나오면 별도 패턴 문서로 추출. 다음 프로젝트에서 바로 재사용.

### 10-3. 컴포넌트·레이어 컨벤션 표준화

피그마 파일의 레이어 이름이 `Frame 17`, `Rectangle 42`처럼 기본값이면 AI가 헷갈림.
- 의미 있는 이름 (`header`, `product-card`, `submit-button`)
- 이 규칙을 팀 문서로 명문화하면 누구 파일이든 AI 결과가 일관됨

---

## 11. 내 상황에 맞는 방법 찾기

### 🌱 처음 해본다 / 세팅 최소화
→ **4-1 경량 루트** (Claude Code + Figma URL)

### 🎯 더 정확한 결과가 필요하다
→ **4-2 Figma MCP 정밀 루트**

### 🎨 피그마 안에서 완결하고 싶다
→ **4-3 Figma Make 내장 루트**

### 🚨 피그마 MCP 써봤는데 결과가 엉망
→ **4-4 이미지 우회 루트** (Google AI Studio)

### 🧱 피그마 파일의 레이어가 깔끔히 정리됨
→ **4-5 autoHTML 플러그인 루트**

### 🏠 ODS 디자인 시스템 과업
→ **4-6 ods-pdp skill 루트**

### 🎭 UT용 A/B/C 비교 시안
→ **7-2 베이스 복제형** 또는 **7-3 제약 풀기형**

### 🔀 여러 화면 플로우 프로토타입
→ **6-1 피그마 화살표 플로우 연결**

### 📋 수정사항이 많아 한 번에 전달하고 싶다
→ **5-2 QA 스타일 번호 매기기**

### 🎨 복잡한 인터랙션 (바텀시트, 앵커링)
→ **5-4 프롬프트 오브 프롬프트 패턴**

### 📸 레퍼런스 이미지로 ODS 스타일 만들기
→ **5-5 Design→Figma 역방향**

### 🧱 팀 단위 프로젝트, 처음부터 제대로
→ **10절 팀 자산화 전략** 먼저 구축

### 🚀 외부(팀·개발자)와 공유해야 함
→ **8-3 Vercel 배포**

---

## 12. 기억할 5가지 핵심 메시지

### ① 완성도보다 검증 속도
> *"프로토타입은 피그마 디자인과 100% 일치하지 않아도 괜찮아요. 완성도보다 검증 속도가 더 중요해요."*

프로토타입의 목적은 **UT 검증**이지 피그마 복제가 아닙니다. 중요한 화면·인터랙션에만 집중.

### ② 잘게 쪼개서 반복
전체 재생성은 망하는 지름길. 깨진 부분만 **선택해서** 재요청.

### ③ 수치는 무조건 명시
AI의 상상력을 믿지 말 것. 숫자·위치·크기를 모두 명시.

### ④ 내 도구 조합을 찾아라
6가지 루트가 모두 달랐습니다. **정답은 없고, 내 과업에 맞는 조합**만 있습니다. 본인 상황에서 2~3가지 방법을 실제로 해봐야 감이 옵니다.

### ⑤ 재사용 가능한 자산을 쌓아라
같은 구조가 두 번 나오면 **패턴으로 문서화**. 프로젝트가 쌓일수록 속도가 빨라지는 구조를 만드세요.

---

## 13. 외부 참고 자료

### 🔗 Figma MCP + Claude Code
| 제목 | 링크 |
|-----|------|
| Claude Code to Figma 공식 소개 (Figma 블로그) | https://www.figma.com/blog/introducing-claude-code-to-figma/ |
| Guide to the Figma MCP server (공식 문서) | https://help.figma.com/hc/en-us/articles/32132100833559 |
| Beginner Step-by-Step Setup Guide | https://medium.com/@nithin_94885/claude-code-mcp-with-figma-a-beginners-step-by-step-setup-guide-84546b46c07d |
| UX Engineer's Honest Guide | https://medium.com/@alexdev82/figma-mcp-claude-code-a-ux-engineers-honest-guide-to-the-design-to-code-bridge-5b492abab2cb |
| 50분 튜토리얼 (Felix Lee) | https://creatoreconomy.so/p/master-claude-code-figma-mcp-for-design-felix-lee |
| Claude Code + Figma (UX Planet) | https://uxplanet.org/claude-code-figma-f647facbe181 |

### 🎨 Figma Make
| 제목 | 링크 |
|-----|------|
| Figma Make 공식 페이지 | https://www.figma.com/make/ |
| Create functional prototype (공식) | https://help.figma.com/hc/en-us/articles/31304485164695 |
| AI Interactive Prototype Generator | https://www.figma.com/solutions/ai-interactive-prototype-generator/ |
| Prototyping with Figma AI (Builder.io) | https://www.builder.io/blog/figma-ai-prototyping |

### 🧪 Google AI Studio
| 제목 | 링크 |
|-----|------|
| Google AI Studio 홈 | https://aistudio.google.com/welcome |
| Build apps in Google AI Studio (공식) | https://ai.google.dev/gemini-api/docs/aistudio-build-mode |
| Gemini + AI Studio 18분 튜토리얼 | https://creatoreconomy.so/p/gemini-3-1-ai-studio-full-prototyping-tutorial |
| Generate UI with image attachments | https://developer.android.com/studio/gemini/generate-ui-with-images |

### 💻 Cursor
| 제목 | 링크 |
|-----|------|
| Cursor for Designers Guide | https://adplist.substack.com/p/a-designers-guide-to-cursor-and-claude |
| Frontend Design Cursor Skill | https://cursor.com/en-US/marketplace/skills/frontend-design |
| Rapid Frontend Prototyping (UXPin) | https://www.uxpin.com/studio/blog/rapid-frontend-prototyping-ai-cursor-storybook/ |
| Cursor AI Complete Guide | https://medium.com/@hilalkara.dev/cursor-ai-complete-guide-2025-real-experiences-pro-tips-mcps-rules-context-engineering-6de1a776a8af |

### 🚀 Vercel 배포
| 제목 | 링크 |
|-----|------|
| Vercel 공식 홈 | https://vercel.com |
| How to Deploy Static HTML to Vercel | https://stefankudla.com/posts/how-to-deploy-a-static-html-css-and-javascript-website-to-vercel |
| Host HTML/CSS/JS on Vercel (GeeksforGeeks) | https://www.geeksforgeeks.org/javascript/how-to-host-html-css-javascript-website-on-vercel/ |
| Deploy a Website with Vercel (Codédex) | https://www.codedex.io/projects/deploy-a-website-with-vercel |

### 📘 한국어 블로그·사례
| 제목 | 링크 |
|-----|------|
| Claude Code에서 Figma로 (WeDesignX) | https://www.wedesignx.com/knowledge/claude-code-to-figma |
| 커서AI/클로드/피그마로 프로덕트 디자인 (브런치) | https://brunch.co.kr/@ghidesigner/275 |
| Claude MCP로 UX설계, Figma로 UI디자인 (브런치) | https://brunch.co.kr/@ghidesigner/270 |
| AI에게 39개 기능 피드백한 사례 (GPTers) | https://www.gpters.org/llm-service/post/we-fed-back-39-LeHo4NMQRKLhCij |
| 피그마 없이 3개월 AI로 디자인 (고위드) | https://www.gowid.com/blog/ai-design-experiences |
| [MCP, Claude, Figma] AI에게 Figma 작업 시켜보자 (velog) | https://velog.io/@jiiker_/MCP-Claude-Figma-AI%EC%97%90%EA%B2%8C-Figma-%EC%9E%91%EC%97%85%EC%9D%84-%EC%8B%9C%EC%BC%9C%EB%B3%B4%EC%9E%90 |
| 생성형 AI 클로드 완전정복 (maily) | https://maily.so/makegrowth/posts/l1zqe74lz5x |

### 🎯 UX 리서치·UT 관련
| 제목 | 링크 |
|-----|------|
| NN/G — UX Prototypes: Lo-Fi vs Hi-Fi | https://www.nngroup.com/articles/ux-prototype-hi-lo-fidelity/ |
| Top AI Tools for UX Designers (Figma) | https://www.figma.com/resource-library/ai-tools-for-ux-designers/ |
| 40 UX AI Tools to Master (Eleken) | https://www.eleken.co/blog-posts/ux-ai-tools |
| Incorporate AI into UX Workflow (Design Monks) | https://www.designmonks.co/blog/incorporate-ai-into-your-ux-workflow |

### 📺 비디자이너·초보자용 추천 학습 경로

처음 시작하시는 분이라면 아래 순서로 보시는 걸 추천합니다:

1. **개념 잡기**: [Figma 공식 — Claude Code to Figma 소개](https://www.figma.com/blog/introducing-claude-code-to-figma/)
2. **설치·세팅**: [Beginner Setup Guide](https://medium.com/@nithin_94885/claude-code-mcp-with-figma-a-beginners-step-by-step-setup-guide-84546b46c07d)
3. **첫 프로토타입**: [50분 튜토리얼](https://creatoreconomy.so/p/master-claude-code-figma-mcp-for-design-felix-lee)
4. **한국어 레퍼런스**: [WeDesignX 글](https://www.wedesignx.com/knowledge/claude-code-to-figma)
5. **배포까지**: [Vercel 정적 사이트 배포 튜토리얼](https://stefankudla.com/posts/how-to-deploy-a-static-html-css-and-javascript-website-to-vercel)

---

*문서 작성: 2026-04-14*
*기반: 실무자 인터뷰 8가지 워크플로우를 기법별로 재구성*
