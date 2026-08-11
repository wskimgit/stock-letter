# Current configuration

- Wiki schema: `CHATGPT_STOCK_WIKI_V1`
- Project instruction candidate: `INSTRUCTION_v4.6-candidate.1.md`
- Volume-cycle Wiki schema: `VOLUME_CYCLE_WIKI_V1`
- Volume-cycle current frozen instruction: `VOLUME_CYCLE_INSTRUCTION_v1.2.0.md`
- Volume-cycle current instruction status: `FROZEN`
- Volume-cycle current frozen blob SHA: `687d70bb5db6fce33c70d94db7cc0bc496f9a547`
- Volume-cycle previous frozen baseline: `VOLUME_CYCLE_INSTRUCTION_v1.0.0.md`
- Volume-cycle previous baseline status: `RELEASED_HISTORY`
- Volume-cycle previous baseline blob SHA: `7510654f7447fdfdcacc703fe8cf6b49f3f6c59d`
- Volume-cycle previous active history: `VOLUME_CYCLE_INSTRUCTION_v1.1.0.md`
- Volume-cycle freeze registry: `VOLUME_CYCLE_FREEZE.md`
- Volume-cycle Wiki: `../거래량-순환매-Wiki.md`
- LAB coupling: `NONE`
- Git branch: `main`
- Started: `2026-08-08`
- v1.0.0 baseline released: `2026-08-11T12:46+09:00`
- v1.2.0 frozen from: `2026-08-11T12:46+09:00`

일반 주식 프로젝트 운영 시 먼저 `CURRENT.md` → `INDEX.md` → 해당 종목 페이지 → `RULES.md` 순으로 확인한다.

거래량 순환매 재질의 시에는 `CURRENT.md` → `INDEX.md` → `RULES.md` → `VOLUME_CYCLE_FREEZE.md` → CURRENT가 가리키는 최신 FROZEN `VOLUME_CYCLE_INSTRUCTION` → `거래량-순환매-Wiki.md` 순으로 확인한다.

그 후 최근 완료 정규장으로 **확정상태**를 확인하고, 정규장이 진행 중이면 장중 가격·동시간대 보정 거래량을 추가해 **장중 잠정상태(P-*)**와 **현재 행동지시**를 산출한다.

`VOLUME_CYCLE_INSTRUCTION_v1.2.0.md`는 2026-08-11 12:46 KST부터 **FROZEN 운영 기준본**이다. 해당 파일의 blob SHA `687d70bb5db6fce33c70d94db7cc0bc496f9a547`를 동결 무결성 기준으로 사용하며 본문을 수정·덮어쓰기하지 않는다. 파일 내부의 `상태: ACTIVE` 및 v1.0.0 관련 문구는 동결 직전 원본 스냅샷의 일부로 보존한다.

`VOLUME_CYCLE_INSTRUCTION_v1.0.0.md`의 기존 `FROZEN_BASELINE` 운영 지위는 해제되었다. 파일은 삭제하거나 수정하지 않고 `RELEASED_HISTORY` 감사 이력으로 보존하며 더 이상 현재 기준본으로 사용하지 않는다.

`VOLUME_CYCLE_INSTRUCTION_v1.1.0.md`는 이전 ACTIVE 이력으로 보존한다.

향후 지시문 변경이 필요하면 `v1.2.0`을 직접 수정하지 않고 새 버전 파일을 생성한다. 새 버전은 사용자 명시 승인 전 현재 FROZEN v1.2.0을 대체하지 않는다.

`거래량-순환매-Wiki.md`는 동결 대상이 아니며, FROZEN v1.2.0 규칙에 따라 Current View, Intraday View, Revision Timeline을 계속 갱신할 수 있다.
