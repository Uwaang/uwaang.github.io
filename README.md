# Obsidian → Hugo → GitHub Pages

이 리포지토리는 Obsidian 노트를 원본으로 사용하여 **Hugo + PaperMod** 테마로 정적 블로그를 생성하고, GitHub Actions를 활용해 `gh-pages` 브랜치로 자동 배포합니다.

## 웹에서 포스팅 편집하기

### 방법 1: Netlify CMS (추천)
1. **Netlify 계정 생성** 및 이 리포지토리 연결
2. **Netlify Identity** 활성화 (Site settings → Identity → Enable Identity)
3. **Git Gateway** 활성화 (Identity → Services → Git Gateway → Enable)
4. 관리자 초대: Identity → Invite users
5. 웹에서 접속: `https://your-site.netlify.app/admin/`

### 방법 2: GitHub 웹 에디터
- 각 포스트 하단의 "📝 이 포스트 편집하기" 링크 클릭
- GitHub에서 직접 마크다운 편집 후 커밋

### 방법 3: GitHub Codespaces
- 리포지토리에서 Code → Codespaces → Create codespace
- 클라우드 VS Code에서 편집

## 빠른 시작

```bash
# 1) 테마 추가 (최초 1회)
git submodule add --depth=1 https://github.com/adityatelange/hugo-PaperMod themes/PaperMod

# 2) 첫 글 작성 예시
hugo new posts/hello-world.md
# Obsidian에서 작성한 내용으로 파일 수정

# 3) 로컬 미리보기
hugo server -D

# 4) 커밋 & 푸시
git add .
git commit -m "feat: init blog"
git push origin main
# => GitHub Actions가 빌드 & gh-pages 브랜치에 배포
```

## 구조 설명
```
content/posts/   # Obsidian 노트 위치 (Front Matter 필요)
static/img/      # 이미지·첨부 파일 보관
static/admin/    # Netlify CMS 관리자 페이지
config.toml      # 사이트 설정
.github/workflows/hugo.yml  # IaC: 빌드·배포 파이프라인
```

## giscus 설정
1. GitHub Repo → Settings → Discussions 활성화
2. https://giscus.app 에서 repo, category 선택 후 코드 생성
3. 생성된 `repoID`, `categoryID` 값을 `config.toml` → `[params.giscus]` 섹션에 기입

## 참고 링크
- PaperMod 테마: https://github.com/adityatelange/hugo-PaperMod
- peaceiris/actions-hugo: https://github.com/peaceiris/actions-hugo
- peaceiris/actions-gh-pages: https://github.com/peaceiris/actions-gh-pages
- Netlify CMS: https://www.netlifycms.org/ 