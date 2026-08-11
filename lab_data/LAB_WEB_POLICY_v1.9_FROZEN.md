# LAB WEB POLICY v1.9 — FROZEN

상태: **SPEC FROZEN**  
직전: `LAB_WEB_POLICY_v1.8_FROZEN.md`  
변경 원칙: v1.8을 수정하지 않고 v1.9를 새 버전으로 동결한다.

## 1. 배포/운영 파일

- 저장·배포본 파일명은 반드시 버전 포함: 예 `lab_v1.5.1-candidate.15.php`
- 운영 서버 파일명은 항상 사이트 루트 `/lab.php`
- `/trade/` 경로는 사용하지 않는다.
- 비밀번호·로그인·로그아웃 기능을 만들지 않는다.

## 2. 로컬 LAB 공개자료

- `/lab_cache/chatgpt_latest.json`
- `/lab_cache/chatgpt_manifest.json`
- `/lab_cache/recommendation_latest.json`
- `/lab_cache/summary_latest.json`
- `/lab_cache/github_source.json`
- `/lab.php?view=public-*`
- `/lab_chatgpt.html`

`github_source.json`은 GitHub Actions가 가져갈 공개 발행원이며, 나머지는 로컬 mirror·진단·fallback이다.

## 3. GitHub ChatGPT 1차 자료원

- Repository: `wskimgit/stock-letter`
- Branch: `main`
- Canonical: `lab_data/LATEST.json`
- Workflow: `.github/workflows/lab-data-sync.yml`
- GitHub commit history를 LAB 데이터 발행 이력으로 사용한다.
- ChatGPT의 LAB 질의는 GitHub canonical을 1차 조회한다.

## 4. NAS 무자격증명 원칙

- `lab.php`는 GitHub token/PAT/SSH key를 읽거나 저장하거나 전송하지 않는다.
- NAS에는 GitHub 쓰기 자격증명을 설치하지 않는다.
- `LAB_GITHUB_TOKEN` 환경변수를 사용하지 않는다.
- `lab.php`는 GitHub Contents API PUT/POST를 호출하지 않는다.
- GitHub Actions가 공개 `/lab_cache/github_source.json`을 pull하고 저장소 자체 workflow 권한으로 `lab_data/LATEST.json`을 commit한다.
- workflow 권한은 `permissions: contents: write`만 사용한다.
- 사용자가 별도 GitHub secret/PAT를 만들 필요가 없다.
- 동일 `source_fingerprint`이면 중복 commit을 만들지 않는다.

GitHub 플랫폼이 workflow 실행 과정에서 내부 임시 자격증명을 제공하는 것은 허용하되, 그 자격증명을 NAS/lab.php에 복사·노출·보관하지 않는다.

## 5. Pull 동기화

- workflow 기본 주기: 5분.
- 수동 `workflow_dispatch` 허용.
- HTTPS source fetch를 우선하고 실패 시 HTTP fallback을 허용한다.
- source JSON은 `schema_version`, `lab_only=true`, `actual_buy=false`, `source_fingerprint`, 시장별 세션 무결성을 검증한 뒤에만 commit한다.
- source 검증 실패 시 기존 GitHub `LATEST.json`을 보존한다.
- GitHub 동기화 지연은 LAB 가상상태·성과·실전자본을 변경하지 않는다.

## 6. 세션 무결성

- 공급자 응답 세션이 기존 정상 cache보다 과거이면 거부한다.
- benchmark 최신세션이 runtime `last_successful_session`보다 과거이면 시장 Tick을 중단한다.
- cron 최신세션이 runtime보다 과거이면 cron 시장처리를 중단한다.
- runtime/production/cache 세션이 불일치하면 `DATA_STALE`.
- 후보 data_date가 market_session보다 미래이면 `DATA_STALE`이며 top candidate는 null.
- GitHub workflow는 `current_review_rows`의 data_date와 market_session 불일치, inactive experiment_hash 혼입, VIRTUAL_OPEN 혼입, 중복행을 거부한다.

## 7. Recommendation 현재성

- 현재 코드의 active experiment_hash만 현재 Recommendation에 포함한다.
- 과거 experiment_hash는 성과·감사 이력에만 보존한다.
- 현재 시장세션의 후보행만 `current_review_rows`에 포함한다.
- VIRTUAL_WAIT는 원 후보의 score/reason을 보존한다.
- 같은 상태에서는 score가 높은 후보를 우선한다.
- VIRTUAL_OPEN은 `virtual_open_reference`로 분리하며 신규 추천순위에서 제외한다.

## 8. 실전 경계

- `actual_buy=false`
- LAB은 실제 주문·실전자본·실전포지션·브로커를 변경하지 않는다.
- OFF/WAIT에서는 Champion 신규매입 금지.
- ON이어도 기업위험·종목구조·가격/거래량·지지·무효화·손익비를 별도 검증한다.
- LAB과 ChatGPT Stock Wiki는 독립한다.
