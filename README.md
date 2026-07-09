# OBJET STUDIO

오브젝트 기반 추상 구성 툴 + 랜덤 콜라주 아카이브 페이지.
GitHub Pages로 호스팅하고, 등록한 그림은 GitHub 저장소에 자동 커밋됩니다.

## 파일 구성

```
your-repo/
├── index.html      → 그리기 스튜디오 (메인)
├── archive.html    → 랜덤 콜라주 아카이브
├── README.md       → 이 파일
└── gallery/        → (자동 생성) 등록된 오브젝트 PNG
    ├── 2026-07-09/
    │   ├── pattern_2026-07-09_143022_OBJ-01.png
    │   └── pattern_2026-07-09_143145_OBJ-02.png
    └── 2026-07-10/
        └── ...
```

## 1. GitHub 저장소 만들기

1. 새 저장소 생성 (`objet-studio` 등 원하는 이름). **Public** 권장 — 아카이브 페이지 접근이 편함.
2. `index.html`, `archive.html`, `README.md` 세 파일을 저장소 루트에 업로드.
3. `main` 브랜치에 커밋.

## 2. GitHub Pages 활성화

1. 저장소 → **Settings → Pages**.
2. **Source**: *Deploy from a branch* 선택.
3. **Branch**: `main` / `/ (root)` 선택 후 Save.
4. 1~2분 후 `https://<사용자명>.github.io/<저장소명>/` 로 접속 가능.

## 3. Personal Access Token (PAT) 발급

그림을 저장소로 자동 커밋하기 위해 필요합니다.

1. GitHub → **Settings** (우측 상단 프로필) → **Developer settings** → **Personal access tokens** → **Fine-grained tokens** → **Generate new token**.
2. 설정:
   - **Token name**: `objet-studio` (자유)
   - **Expiration**: 원하는 기간
   - **Repository access**: *Only select repositories* → 위에서 만든 저장소 선택
   - **Repository permissions** → **Contents**: **Read and write**
3. 생성 후 토큰(`github_pat_...`)을 복사. **한 번만 보여지니 안전한 곳에 임시 저장**.

## 4. 스튜디오에서 GitHub 연결

1. `https://<사용자명>.github.io/<저장소명>/` 접속.
2. 상단 우측 **GitHub · 미연결** 옆의 `설정` 버튼 클릭.
3. 다음을 입력:
   - **Owner**: GitHub 사용자명
   - **Repository**: 저장소명
   - **Branch**: `main`
   - **Path prefix**: `gallery` (또는 원하는 폴더명)
   - **Personal Access Token**: 위에서 발급받은 토큰
4. **저장 & 연결 테스트** 클릭. 성공하면 상단 chip에 `<owner>/<repo>` 표시.

이후 스튜디오에서 그림을 그리고 **오브젝트로 등록 →** 버튼을 누르면 PNG가 자동으로 `gallery/YYYY-MM-DD/` 폴더에 커밋됩니다.

## 5. 아카이브 페이지 보기

상단의 **아카이브 →** 링크 (또는 `archive.html` 직접 접속).

- 저장소의 `gallery/` 아래 모든 PNG를 재귀적으로 스캔.
- 랜덤 위치·회전·크기로 화면에 겹치듯 배치 (콜라주 스타일).
- **중복 없이 각 그림 1회씩** 표시.
- 우측 상단 **↻ 재배치** 버튼으로 새로운 랜덤 레이아웃 생성.
- 마우스 hover 시 라임 컬러 후광 효과.

## 보안 참고

- 토큰은 **로컬 브라우저의 `localStorage`에만** 저장되며 외부로 전송되지 않습니다.
- 하지만 공용 컴퓨터에서 사용 후에는 반드시 `설정` → `연결 해제` 버튼을 누르세요.
- 개인 노트북/데스크톱에서만 사용하면 안전합니다.
- 저장소가 Public이어도 토큰이 없으면 아무도 커밋할 수 없습니다.

## 브라우저 호환성

- **드로잉 스튜디오**: 최신 Chrome/Edge/Safari/Firefox 모두 OK.
- **로컬 폴더 저장** (File System Access API): Chrome/Edge/Opera만 지원.
- **GitHub 커밋**: 모든 최신 브라우저 지원.
- **아카이브 페이지**: 모든 최신 브라우저 지원.
