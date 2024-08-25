# 🌳 Techeer Tree : 소원을 빌어봐

## 주제 설명

Techeer Tree는 테커인들이 자신의 목표나 소원을 작성하고, 이를 소원 나무에 게시하여 다른 사람들과 공유할 수 있는 플랫폼입니다. 작성된 소원은 모든 사용자에게 공개되어, 서로의 소원을 볼 수 있습니다.

## 안내사항

- 해커톤 진행시간은 다음과 같습니다.
  - Backend : 2024년 8월 24일(토) 12:00 ~ 2024년 8월 25일(일) 00:00
  - Frontend : 2024년 8월 25일(일) 12:00 ~ 2024년 8월 26일(월) 00:00
- 꼭 정해진 시간에 해커톤을 진행해주세요.
  - Backend 작업을 일찍 완료하시더라도, Frontend 작업은 정해진 시간에 시작해 주시고 그 전에는 충분히 휴식을 취하시길 바랍니다.
- 참가자는 본 레포지토리를 fork한 후, 기능 구현 완료 후 PR을 통해 제출해야 합니다.
  - 구현 내용은 README.md 하단에 이어서 작성해 주세요.
  - 과제의 소스코드는 본인의 GitHub 레포지토리에 **Public**으로 올려주세요.
- 진행 중 문의사항은 슬랙 “**2024-굿나잇-해커톤**” 채널(public)에 참가하여 남겨주세요.

## 기본 요구사항

- **Techeer Tree** 앱을 구현합니다.
- 일관된 코딩 컨벤션을 유지해주세요.
- 기능 당 커밋은 필수입니다.
- 환경변수는 분리하여 관리해 주세요.

## 기술스택

### 1. React.JS

- React 18.x 이상 및 Node.js 20.x 이상을 사용합니다.
- TypeScript를 사용할 경우, any 타입 사용을 금지합니다.

### 2. Next.JS

- Next.js 14.x 이상을 사용합니다.
- TypeScript를 사용할 경우, any 타입 사용을 금지합니다.

### 3. Flutter

- IOS 시뮬레이터 구동을 위한 Xcode가 설치되어 있어야 합니다.

### 4. Svelte

## 백엔드 해커톤을 진행하지 않은 경우 사용할 수 있는 백엔드 리포지토리 주소

- repository : https://github.com/printSANO/wish-tree
- swagger : http://localhost:8080/swagger/index.html

# 기능

### 공통 요구사항

> 권한 전환: 사용자는 모든 페이지에서 언제든 권한을 전환할 수 있습니다.

- **사용자 권한 :**
  - 사용자 권한은 프론트엔드에서 Admin과 User 두 가지로 구분되며, 모든 페이지에서 버튼 클릭으로 사용자 권한을 전환할 수 있습니다. (다만, 백엔드에서 제공하는 API는 Admin과 User의 구분이 되어 있지 않습니다.)
  - 새로 고침을 하더라도 사용자 권한은 초기화 되지 않습니다.
  - API 요청을 할 때 Parameter로 권한을 집어넣는 방식이 아닌 각 페이지마다 권한에 맞는 API를 호출하도록 기능을 구현합니다.
    ex) 소원 수정 및 삭제는 Admin만 가능하도록, 소원 등록은 User만 가능하도록 등
  - **예외 처리 :** 접근 권한이 없는 페이지에 접속하면 “${권한}은 이 페이지에 접근할 권한이 없습니다.”라는 메세지를 표시하고 기능 사용을 제한합니다. **(추가 기능)**

### 소원 나무 페이지 (소원 목록 조회)

> **소원 목록 조회:** 등록된 모든 소원을 조회합니다.

- **라우팅 URL :** ‘/’
- **페이지 접근 가능 권한** : Admin, User
- **소원 열매 달기 :** 별도의 ‘소원 열매 달기’ 버튼을 눌러 소원 열매 달기 페이지로 이동합니다.
- **소원 열매 목록 조회 :**
  - 각 목록에서 소원 열매에는 소원의 제목을 보여줍니다.
  - 소원 열매를 클릭하면 해당 소원 열매 페이지(소원 상세 페이지)로 이동합니다.
- **소원 열매 필터링 :** 소원 열매의 카테고리를 기준으로 필터링하여 소원 열매를 조회할 수 있습니다.
- **페이지네이션 :** 소원 목록을 페이지네이션 or 무한스크롤 기능을 통해 조회합니다. **(추가 기능)**

### 소원 열매 달기 페이지 (소원 등록)

> **소원 등록:** 소원을 등록합니다.

- **라우팅 URL :** ‘/wish’
- **페이지 접근 가능 권한** : User
- **입력 요구 :** 제목, 본문, 카테고리를 사용자는 필수적으로 입력합니다.
- **카테고리 선택 :** 카테고리는 ‘진로’, ‘건강’, ‘인간 관계’, ‘돈’, ‘목표’, ‘학업/성적’, ‘기타’ 중 하나를 드롭다운 메뉴에서 선택합니다.
- **예외 처리 :** 입력 요구란에 빈 문자열 및 null값으로 입력하여 등록 했을때 경고 메세지를 띄워줍니다. **(추가 기능)**

### 소원 열매 페이지 (소원 상세 조회)

> **소원 상세 조회:** 소원의 내용을 상세하게 조회합니다.

- **라우팅 URL :** ‘/wish-fruit/{wishId}’
- **페이지 접근 가능 권한** : Admin, User
- **소원 상세 조회 :** 해당 열매(소원)의 정보인 제목, 본문, 카테고리를 보여줍니다.
- **소원 열매 삭제 :** Admin만 해당 소원 열매를 삭제할 수 있습니다.
- **댓글 기능 :**
  - **댓글 작성 :** 소원에 사용자는 댓글을 작성할 수 있습니다. **(추가 기능)**
  - **댓글 조회 :** 해당 소원에 대한 댓글을 최신순으로 모두 볼 수 있습니다. **(추가 기능)**
  - **댓글 삭제 :** Admin만 해당 댓글을 삭제할 수 있습니다. **(추가 기능)**
- **예외 처리 :** 존재하지 않는 소원 열매를 조회하면 404(Not Found) 에러 메세지를 띄워주며 메인 페이지(’/’)로 이동하는 버튼을 보여줍니다. **(추가 기능)**

### 소원 열매 승인 페이지 (소원 승인)

> **소원 승인:** 등록한 소원을 승인하여 사용자들에게 소원을 보여줍니다.

- **라우팅 URL :** ‘/wish-fruit/allow’
- **페이지 접근 가능 권한** : Admin
- **승인/거절이 되지 않은 소원 열매 조회 :** 소원 열매의 승인 상태(승인, 보류, 거절)가 ‘보류’인 소원 열매를 조회합니다.
- **승인/거절 :** 조회한 소원 열매의 상태를 승인 또는 거절합니다.

# UI 예시

🎨[Figma](https://www.figma.com/design/y4nPreYtI8QTUO4la4y94A/Good-Night-3rd-Hackathon-Frontend?node-id=0-1&t=elt0ukmwQ9d6C2rv-1)

(UI 예시는 참고용으로만 제공되며, 그대로 따라하기보다는 참고하여 자유롭게 디자인해 주시길 바랍니다.)

# 기여해주신 분

- 👩🏻‍💻[김정현](https://github.com/kjeongh)
- 🧑🏻‍💻[조진우](https://github.com/jinoo0306)
- 👨🏻‍💻[정태원](https://github.com/teawon)
- 🧑🏻‍💻[오현택](https://github.com/HyunTaek5)

---

## Demo 및 기능 구현 보고

기본 요구 사항 모두 구현했습니다.

추가 기능사항도 예외 처리를 조금 했는데 댓글 기능은 구현하지 않았습니다.

https://github.com/user-attachments/assets/e4b3872e-af21-4c7f-90cc-6b8ec5e68bab

```
    # .env
    # 로컬 url
    VITE_SVELTE_APP_BASE_URL=http://localhost:8080
```
