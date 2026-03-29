# Vault 사용 가이드

Vault는 유어슈 구성원들이 함께 쓰는 **비밀번호 관리 서비스**예요. 노션·스프레드시트에 흩어져 있던 계정 정보를 한 곳에 모아두고, 웹사이트에 접속할 때 아이디·비밀번호를 자동으로 채워줘요.

> 서비스 주소: https://vault.yourssu.com

## 문서

- [사용자 가이드](docs/user-guide.md) — 상세 설정 및 사용법
- [관리자 가이드](docs/admin-guide.md) — 구성원 초대, 그룹/컬렉션 관리

---

## Quick Guide

### 회원가입

> Vault는 관리자 초대를 받아야 가입할 수 있어요. 슬랙에서 @leopold 또는 @ducks 에게 요청해 주세요.

1. `nickname.urssu@gmail.com` 받은편지함(스팸메일함 포함)에서 **Yourssu Vault** 발신 초대 메일 확인 후 **Join Organization Now** 클릭
2. 이메일(`nickname.urssu@gmail.com`), 이름(`닉네임 [파트]`), 마스터 비밀번호 입력 후 **계정 만들기**
3. 이메일로 온 6자리 인증 코드 입력
4. 관리자 승인 완료 후 팀 계정에 접근 가능

> 마스터 비밀번호는 관리자도 복구할 수 없어요. 반드시 안전한 곳에 기록해 두세요.

---

### 로그인 (처음 설치 시)

**크롬 확장 프로그램**
1. [Bitwarden 크롬 확장 프로그램](https://chromewebstore.google.com/detail/bitwarden-password-manage/nngceckbapebfimnlniiiahkandclblb) 설치
2. 확장 프로그램 실행 → 화면 아래 **"접근 중: bitwarden.com"** 클릭 → **자체 호스팅** 선택
3. 서버 URL에 `https://vault.yourssu.com` 입력 후 저장
4. 이메일·마스터 비밀번호 입력 → 이메일로 온 인증 코드 입력

**모바일 앱**
1. [App Store](https://apps.apple.com/app/bitwarden-password-manager/id1137397744) / [Google Play](https://play.google.com/store/apps/details?id=com.x8bit.bitwarden) 에서 Bitwarden 설치
2. 로그인 화면 하단 서버 주소 탭 → **자체 호스팅** → `https://vault.yourssu.com` 입력
3. 이메일·마스터 비밀번호 입력 → 이메일로 온 인증 코드 입력

---

### 사용하기

- **자동 완성**: 로그인 페이지에서 입력창 옆 Bitwarden 아이콘 클릭 또는 확장 프로그램 팝업에서 항목 선택
- **OTP 코드**: Bitwarden이 자동으로 생성 → 클립보드에 복사됨 → 붙여넣기(Ctrl+V)
- **새 항목 저장**: 확장 프로그램 팝업 → **+ 새 항목** → 유형 선택 후 저장

