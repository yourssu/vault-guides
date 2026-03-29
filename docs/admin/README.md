# 암호화 설정 가이드

`docs/admin/` 디렉토리는 [git-crypt](https://github.com/AGWA/git-crypt)와 GPG를 사용해 암호화됩니다.
등록된 GPG 키를 가진 관리자만 내용을 확인할 수 있습니다. GPG 키 등록 문의는 [README의 기여자](../../README.md#기여자)에게 연락하세요.

---

## 1. GPG 키 생성

GPG 키가 없는 경우 아래 명령어로 생성합니다.

```bash
gpg --full-generate-key
# RSA 4096, 만료 없음 선택 권장

# 키 ID 확인
gpg --list-keys --keyid-format SHORT
```

---

## 2. 초기 설치

```bash
brew install git-crypt gpg   # macOS
# apt install git-crypt gpg  # Ubuntu
```

---

## 3. 새 팀원 등록 (관리자만 가능)

새 팀원의 GPG 공개키를 받아 등록합니다.

```bash
# 1. 팀원의 공개키 가져오기
gpg --keyserver keyserver.ubuntu.com --recv-keys <KEY_ID>
# 또는 파일로 받은 경우
gpg --import teammate-pubkey.asc

# 2. git-crypt에 등록
git-crypt add-gpg-user <EMAIL 또는 KEY_ID>

# 3. 커밋 & 푸시
git push
```

등록 후 팀원은 `git-crypt unlock`만 실행하면 됩니다.

---

## 4. 복호화 (저장소 clone 후)

자신의 GPG 키가 등록되어 있다면 자동으로 복호화됩니다.

```bash
git clone <repo-url>
git-crypt unlock
```

unlock 후에는 `docs/admin/` 파일이 평문으로 보입니다.

---

## 5. 새 파일 추가

`docs/admin/` 안에 파일을 추가하면 `.gitattributes` 설정에 의해 자동으로 암호화됩니다.

```bash
# 암호화 상태 확인
git-crypt status
```

---

## 6. 암호화 잠금 (작업 완료 후)

```bash
git-crypt lock
```

lock 후에는 `docs/admin/` 파일이 다시 바이너리(암호화)로 표시됩니다.

---

## 7. GPG 개인키 백업

개인키를 분실하면 암호화된 파일을 복구할 수 없습니다. 반드시 백업해 두세요.

```bash
# 개인키 백업 (저장소 루트에서 실행)
gpg --export-secret-keys --armor <EMAIL> > <NICKNAME>-private.asc
```

- `*-private.asc` 파일은 `.gitignore`에 등록되어 있어 git에 업로드되지 않습니다.
- 백업 파일은 USB, 외장 드라이브, 암호화된 클라우드 등 **안전한 별도 공간**에 보관하세요.

복원 시:

```bash
gpg --import <NICKNAME>-private.asc
```

---

## 관련 파일

| 파일 | 역할 |
|------|------|
| `.gitattributes` | 암호화 대상 경로 지정 (`docs/admin/**`) |
| `.gitignore` | `*-private.asc` 커밋 방지 |
| `.git-crypt/` | git-crypt 내부 설정 및 GPG로 암호화된 대칭키 저장 |
| `*-private.asc` | GPG 개인키 백업 파일 (로컬 전용, git 제외) |

> 대칭키 파일(`.key`)을 따로 관리할 필요 없이 GPG 키페어로 unlock합니다.
