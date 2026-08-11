# LAB WEB POLICY v1.8 — FROZEN

상태: **SPEC FROZEN**  
직전: `LAB_WEB_POLICY_v1.7_FROZEN.md`  
변경 원칙: v1.7을 수정하지 않고 v1.8을 새 버전으로 동결한다.

## 1. 배포/운영 파일

- 저장·배포본 파일명은 반드시 버전 포함: 예 `lab_v1.5.1-candidate.14.php`
- 운영 서버 파일명은 항상 사이트 루트 `/lab.php`
- `/trade/` 경로는 사용하지 않는다.
- 비밀번호·로그인·로그아웃 기능을 만들지 않는다.

## 2. 로컬 LAB 공개자료

- `/lab_cache/chatgpt_latest.json`
- `/lab_cache/chatgpt_manifest.json`
- `/lab_cache/recommendation_latest.json`
- `/lab_cache/summary_latest.json`
- `/lab.php?view=public-*`
- `/lab_chatgpt.html`

위 자료는 **로컬 mirror·진단·fallback**이다.

## 3. GitHub ChatGPT 1차 자료원

- Repository: `wskimgit/stock-letter`
- Branch: `main`
- Canonical: `lab_data/LATEST.json`
- GitHub commit history를 LAB 데이터 발행 이력으로 사용한다.
- ChatGPT의 LAB 질의는 GitHub canonical을 1차 조회한다.

## 4. GitHub 쓰기 보안

- token은 환경변수 `LAB_GITHUB_TOKEN`에서만 읽는다.
- token 값을 PHP 코드·JSON·HTML·로그·GitHub 데이터에 기록하지 않는다.
- 권장 권한은 해당 저장소 Contents read/write만이다.
- GitHub 쓰기 실패는 실제 LAB 계산·가상상태를 변경하지 않는다.
- GitHub가 필수 발행원으로 설정된 버전에서는 쓰기 실패 시 publication을 `PARTIAL_PUBLISH`로 표시한다.
- `source_fingerprint`가 동일하면 중복 commit을 만들지 않는다.

## 5. 세션 무결성

- 공급자 응답 세션이 기존 정상 cache보다 과거이면 거부한다.
- benchmark 최신세션이 runtime `last_successful_session`보다 과거이면 시장 Tick을 중단한다.
- cron 최신세션이 runtime보다 과거이면 cron 시장처리를 중단한다.
- runtime/production/cache 세션이 불일치하면 `DATA_STALE`.
- 후보 data_date가 market_session보다 미래이면 `DATA_STALE`이며 top candidate는 null.

## 6. Recommendation 현재성

- 현재 코드의 active experiment_hash만 현재 Recommendation에 포함한다.
- 과거 experiment_hash는 성과·감사 이력에만 보존한다.
- 현재 시장세션의 후보행만 `current_review_rows`에 포함한다.
- VIRTUAL_WAIT는 원 후보의 score/reason을 보존한다.
- 같은 상태에서는 score가 높은 후보를 우선한다.
- VIRTUAL_OPEN은 `virtual_open_reference`로 분리하며 신규 추천순위에서 제외한다.

## 7. 실전 경계

- `actual_buy=false`
- LAB은 실제 주문·실전자본·실전포지션·브로커를 변경하지 않는다.
- OFF/WAIT에서는 Champion 신규매입 금지.
- ON이어도 기업위험·종목구조·가격/거래량·지지·무효화·손익비를 별도 검증한다.
- LAB과 ChatGPT Stock Wiki는 독립한다.
