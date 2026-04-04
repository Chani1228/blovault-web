# BLO VAULT — 향후 구성 (체크리스트)

공개 웹(`blovault-web`)·앱·운영을 **도메인·법무·보안** 기준으로 마무리할 때 정리할 항목입니다. (임시 연락처는 현재 개인 Gmail — 아래 “연락처” 참고.)

## 연락처 / 브랜딩

- [ ] **`@blovault.com` 메일** — `privacy@`, `support@`, `security@`(또는 역할 분리) 개설 후 앱·정책·Plaid·스토어 전부 교체
- [ ] **대표 연락처 단일화** — 스토어, Plaid, 취약점 공시(VDP) 문구와 동일 주소 사용
- [ ] (선택) **GitHub Pages 커스텀 도메인** — 예: `legal.blovault.com` → 이 레포 Pages

## 법무 / 정책

- [ ] **변호사 검토** — Privacy Policy · Terms of Service 최종본 (현재 DRAFT 표기 제거)
- [ ] **데이터 보존·삭제** — 구독 종료 후 서버/로컬 보존 기간이 제품에 맞으면 정책·앱·백엔드 작업과 문구 일치
- [ ] **CCPA / 주별 규정** — `legal/` 문서와 앱 내 CCPA 화면을 실제 프로세스(요청 접수 메일 등)에 맞게 갱신

## 보안 / 기술 (앱 로드맵과 동기화)

- [ ] **TLS 인증서 퍼블릭 키 핀ning** — 구현 시 Plaid·보안 설문 문구 업데이트
- [ ] **탈옥·루트 탐지** — 도입 시 정책·스토어 설명 반영
- [ ] **인증 실패 / Panic Delete** — 설계한 임계치(예: N회 실패)가 있으면 구현과 문서 일치
- [ ] **Sentry·Supabase** — 프로덕션 프로젝트, RLS, 키 로테이션 운영 절차 문서화

## Plaid / 파트너

- [ ] **프로덕션 제출 패키지 PDF** — 위 항목 반영 후 URL·이메일·스크린샷 재점검
- [ ] **Data retention 첨부** — 내부 정책 확정 후 최종본 업로드

## 이 저장소(`blovault-web`)

- [ ] **GitHub Pages** 켜기(미설정 시) — `index.html` 랜딩 노출
- [ ] **README “Current product configuration”** — 메인 앱 레포와 주기적 동기화

---

*마지막 정리: 2026-04-04*
