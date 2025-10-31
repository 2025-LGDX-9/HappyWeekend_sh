# Git & GitHub 완전 가이드 📚

Git과 GitHub의 주요 기능들을 단계별로 설명하는 가이드입니다.

## 목차
1. [Git 기본 개념](#git-기본-개념)
2. [Git 초기 설정](#git-초기-설정)
3. [저장소 초기화 (init)](#저장소-초기화-init)
4. [원격 저장소 연결 (remote)](#원격-저장소-연결-remote)
5. [파일 추가 및 커밋 (add, commit)](#파일-추가-및-커밋-add-commit)
6. [원격 저장소에 업로드 (push)](#원격-저장소에-업로드-push)
7. [저장소 복제 (clone)](#저장소-복제-clone)
8. [브랜치 관리 (branch)](#브랜치-관리-branch)
9. [브랜치 병합 (merge)](#브랜치-병합-merge)
10. [기타 유용한 명령어](#기타-유용한-명령어)

---

## Git 기본 개념

### Git이란?
- **분산 버전 관리 시스템**
- 코드의 변경 이력을 추적하고 관리
- 여러 개발자가 협업할 수 있게 도와주는 도구

### GitHub이란?
- Git 저장소를 호스팅하는 웹 서비스
- 온라인에서 코드를 공유하고 협업할 수 있는 플랫폼

---

## Git 초기 설정

Git을 처음 사용할 때 사용자 정보를 설정해야 합니다.

```bash
# 사용자 이름 설정
git config --global user.name "당신의 이름"

# 이메일 설정
git config --global user.email "your.email@example.com"

# 설정 확인
git config --list
```

---

## 저장소 초기화 (init)

### 새로운 Git 저장소 만들기

```bash
# 현재 디렉토리를 Git 저장소로 초기화
git init

# 새 디렉토리를 만들고 Git 저장소로 초기화
git init my-project
cd my-project
```

### 결과
- `.git` 폴더가 생성됨
- 현재 디렉토리가 Git 저장소가 됨

---

## 원격 저장소 연결 (remote)

### 원격 저장소 추가

```bash
# GitHub 저장소와 연결
git remote add origin https://github.com/사용자명/저장소명.git

# 원격 저장소 목록 확인
git remote -v

# 원격 저장소 정보 자세히 보기
git remote show origin
```

### 원격 저장소 관리

```bash
# 원격 저장소 URL 변경
git remote set-url origin https://github.com/새로운주소/저장소명.git

# 원격 저장소 제거
git remote remove origin
```

---

## 파일 추가 및 커밋 (add, commit)

### 파일 상태 확인

```bash
# 현재 상태 확인
git status

# 변경사항 자세히 보기
git diff
```

### 파일 스테이징 (add)

```bash
# 특정 파일 추가
git add 파일명.txt

# 여러 파일 추가
git add 파일1.txt 파일2.txt

# 모든 변경된 파일 추가
git add .

# 모든 파일 추가 (삭제된 파일 포함)
git add -A
```

### 커밋 (commit)

```bash
# 커밋 메시지와 함께 커밋
git commit -m "커밋 메시지"

# 스테이징과 커밋을 한번에
git commit -am "변경사항을 추가하고 커밋"

# 커밋 히스토리 확인
git log

# 간단한 로그 확인
git log --oneline
```

### 커밋 메시지 작성 팁
- **명확하고 간결하게** 작성
- **현재형**으로 작성 (예: "Add feature" not "Added feature")
- **50자 이내**로 제목 작성
- 필요시 본문에 상세 설명 추가

---

## 원격 저장소에 업로드 (push)

### 기본 push

```bash
# 현재 브랜치를 원격 저장소에 업로드
git push origin main

# 처음 push할 때 (upstream 설정)
git push -u origin main

# upstream 설정 후 간단히 push
git push
```

### push 옵션들

```bash
# 강제 push (주의!)
git push --force

# 모든 브랜치 push
git push --all

# 태그까지 함께 push
git push --tags
```

---

## 저장소 복제 (clone)

### 원격 저장소 복제

```bash
# GitHub 저장소를 로컬로 복제
git clone https://github.com/사용자명/저장소명.git

# 특정 이름으로 복제
git clone https://github.com/사용자명/저장소명.git 새로운폴더명

# 특정 브랜치만 복제
git clone -b 브랜치명 https://github.com/사용자명/저장소명.git
```

### clone vs init의 차이
- **clone**: 기존 원격 저장소를 복사해옴
- **init**: 새로운 저장소를 생성

---

## 브랜치 관리 (branch)

### 브랜치란?
- 독립적인 작업 공간
- 메인 코드를 건드리지 않고 새로운 기능 개발 가능
- 나중에 메인 브랜치와 병합 가능

### 브랜치 기본 명령어

```bash
# 현재 브랜치 확인
git branch

# 모든 브랜치 확인 (원격 포함)
git branch -a

# 새 브랜치 생성
git branch 새브랜치명

# 브랜치 생성과 동시에 이동
git checkout -b 새브랜치명

# 또는 (Git 2.23+)
git switch -c 새브랜치명
```

### 브랜치 이동

```bash
# 브랜치 변경
git checkout 브랜치명

# 또는 (Git 2.23+)
git switch 브랜치명

# 이전 브랜치로 돌아가기
git checkout -

# 또는
git switch -
```

### 브랜치 삭제

```bash
# 로컬 브랜치 삭제
git branch -d 브랜치명

# 강제 삭제
git branch -D 브랜치명

# 원격 브랜치 삭제
git push origin --delete 브랜치명
```

---

## 브랜치 병합 (merge)

### merge란?
- 서로 다른 브랜치의 변경사항을 합치는 과정
- 주로 기능 개발 완료 후 메인 브랜치에 합칠 때 사용

### 기본 merge

```bash
# main 브랜치로 이동
git checkout main

# 다른 브랜치를 현재 브랜치에 병합
git merge 기능브랜치명
```

### merge 종류

#### 1. Fast-forward merge
```bash
# 단순히 포인터만 이동 (충돌 없음)
git merge feature-branch
```

#### 2. 3-way merge
```bash
# 새로운 merge 커밋 생성
git merge feature-branch
```

#### 3. 충돌 해결
```bash
# 충돌 발생시
git merge feature-branch
# 충돌 파일 수정 후
git add 충돌파일.txt
git commit -m "Resolve merge conflict"
```

### merge vs rebase

| merge | rebase |
|-------|--------|
| 히스토리 보존 | 히스토리 정리 |
| 안전함 | 위험할 수 있음 |
| 복잡한 히스토리 | 깔끔한 히스토리 |

---

## 기타 유용한 명령어

### 변경사항 관리

```bash
# 변경사항 임시 저장
git stash

# 임시 저장된 변경사항 복원
git stash pop

# 스태시 목록 확인
git stash list

# 특정 커밋으로 되돌리기
git reset --hard 커밋해시

# 작업 디렉토리 정리
git clean -fd
```

### 원격 저장소 동기화

```bash
# 원격 저장소의 최신 변경사항 가져오기
git fetch

# 원격 저장소의 변경사항을 가져와서 병합
git pull

# 특정 브랜치 pull
git pull origin main
```

### 커밋 히스토리

```bash
# 그래프로 히스토리 보기
git log --graph --oneline

# 특정 파일의 히스토리
git log --follow 파일명

# 커밋 간 차이점 보기
git diff 커밋1..커밋2
```

---

## 일반적인 Git 워크플로우

### 1. 새 프로젝트 시작
```bash
mkdir my-project
cd my-project
git init
git remote add origin https://github.com/username/my-project.git
```

### 2. 기존 프로젝트 참여
```bash
git clone https://github.com/username/project.git
cd project
```

### 3. 새 기능 개발
```bash
git checkout -b feature/new-feature
# 코드 작성...
git add .
git commit -m "Add new feature"
git push origin feature/new-feature
```

### 4. 메인 브랜치에 병합
```bash
git checkout main
git pull origin main
git merge feature/new-feature
git push origin main
git branch -d feature/new-feature
```

---

## 주의사항 ⚠️

1. **commit 전에 항상 `git status`로 확인**
2. **의미 있는 커밋 메시지 작성**
3. **큰 파일이나 민감한 정보는 `.gitignore`에 추가**
4. **`git push --force`는 신중하게 사용**
5. **협업 시 규칙 정하고 따르기**

---

## 도움이 되는 리소스 📖

- [Git 공식 문서](https://git-scm.com/doc)
- [GitHub 가이드](https://guides.github.com/)
- [Git 시각화 도구](https://git-school.github.io/visualizing-git/)
- [커밋 메시지 컨벤션](https://www.conventionalcommits.org/)

---

*Happy Coding! 🚀*