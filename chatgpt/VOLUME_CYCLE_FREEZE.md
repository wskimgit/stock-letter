# 거래량 순환매 지시문 동결 기록

## 현재 동결 기준

- frozen_instruction: `VOLUME_CYCLE_INSTRUCTION_v1.2.0.md`
- frozen_operational_status: `FROZEN`
- freeze_timestamp: `2026-08-11T12:46+09:00`
- repository: `wskimgit/stock-letter`
- branch: `main`
- frozen_blob_sha: `687d70bb5db6fce33c70d94db7cc0bc496f9a547`
- wiki_schema: `VOLUME_CYCLE_WIKI_V1`
- wiki_file: `../거래량-순환매-Wiki.md`

## 이전 동결 기준 해제

- previous_frozen_instruction: `VOLUME_CYCLE_INSTRUCTION_v1.0.0.md`
- previous_status: `RELEASED_HISTORY`
- release_timestamp: `2026-08-11T12:46+09:00`
- previous_blob_sha: `7510654f7447fdfdcacc703fe8cf6b49f3f6c59d`
- 처리: 기존 FROZEN_BASELINE 운영 지위만 해제한다. 파일은 삭제·수정하지 않고 감사·버전 이력으로 보존한다.

## 버전 이력

- `v1.0.0` = 이전 FROZEN BASELINE → `RELEASED_HISTORY`
- `v1.1.0` = 한줄 행동지시 도입, 이전 ACTIVE 이력
- `v1.2.0` = 장중 보정·3층 상태체계 도입 → **현재 FROZEN 운영 기준본**

## 동결 원칙

1. 현재 운영 기준은 `VOLUME_CYCLE_INSTRUCTION_v1.2.0.md`이다.
2. v1.2.0의 동결 무결성 기준 SHA는 `687d70bb5db6fce33c70d94db7cc0bc496f9a547`이다.
3. v1.2.0 파일의 본문은 동결 후 수정·덮어쓰기하지 않는다.
4. 파일 내부의 `상태: ACTIVE`, `동결 기준본: v1.0.0` 등은 동결 직전 스냅샷의 일부이므로 원문 그대로 보존한다. 운영상 상태와 기준은 `CURRENT.md`와 본 동결 기록의 `FROZEN` 판정을 우선한다.
5. 기존 v1.0.0의 FROZEN_BASELINE 지위는 해제되었으며 더 이상 현재 규칙 기준으로 사용하지 않는다.
6. v1.0.0은 `RELEASED_HISTORY`로 보존한다. 이는 삭제·폐기를 뜻하지 않으며 과거 비교·감사용 이력이다.
7. 이후 오류 수정·규칙 추가·전략 변경은 반드시 `v1.2.0`을 직접 수정하지 않고 새 버전 파일로 생성한다.
8. 새 버전은 사용자 명시 승인 전 `DRAFT` 또는 `CANDIDATE`로 관리하며 현재 FROZEN v1.2.0을 자동 대체하지 않는다.
9. 재질의 시 GitHub 선확인 순서는 `CURRENT.md → INDEX.md → RULES.md → VOLUME_CYCLE_FREEZE.md → 현재 FROZEN 지시문 → 거래량-순환매-Wiki.md`로 한다.
10. `거래량-순환매-Wiki.md`의 Current View, Intraday View, Revision Timeline은 시장 변화에 따라 계속 갱신할 수 있다. 동결 대상은 지시문 규칙 본문이지 시장 상태 Wiki 자체가 아니다.

## 변경 정책

- PATCH 필요 → 새 PATCH 버전 파일 생성
- MINOR 필요 → 새 MINOR 버전 파일 생성
- MAJOR 필요 → 새 MAJOR 버전 파일 생성

현재 운영선:

`v1.0.0 RELEASED_HISTORY → v1.1.0 HISTORY → v1.2.0 FROZEN`

현재 동결본 `VOLUME_CYCLE_INSTRUCTION_v1.2.0.md`는 어떤 경우에도 직접 덮어쓰지 않는다.
