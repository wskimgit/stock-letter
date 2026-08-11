# Current configuration

- Wiki schema: `CHATGPT_STOCK_WIKI_V1`
- Project instruction candidate: `INSTRUCTION_v4.6-candidate.1.md`
- Volume-cycle Wiki schema: `VOLUME_CYCLE_WIKI_V1`
- Volume-cycle frozen baseline: `VOLUME_CYCLE_INSTRUCTION_v1.0.0.md`
- Volume-cycle frozen baseline status: `FROZEN`
- Volume-cycle frozen baseline blob SHA: `7510654f7447fdfdcacc703fe8cf6b49f3f6c59d`
- Volume-cycle previous active instruction: `VOLUME_CYCLE_INSTRUCTION_v1.1.0.md`
- Volume-cycle active instruction: `VOLUME_CYCLE_INSTRUCTION_v1.2.0.md`
- Volume-cycle active instruction status: `ACTIVE`
- Volume-cycle active blob SHA: `687d70bb5db6fce33c70d94db7cc0bc496f9a547`
- Volume-cycle freeze registry: `VOLUME_CYCLE_FREEZE.md`
- Volume-cycle Wiki: `../거래량-순환매-Wiki.md`
- LAB coupling: `NONE`
- Git branch: `main`
- Started: `2026-08-08`
- Volume-cycle v1.0.0 frozen from: `2026-08-11`
- Volume-cycle v1.1.0 active history from: `2026-08-11`
- Volume-cycle v1.2.0 active from: `2026-08-11`

일반 주식 프로젝트 운영 시 먼저 `CURRENT.md` → `INDEX.md` → 해당 종목 페이지 → `RULES.md` 순으로 확인한다.

거래량 순환매 재질의 시에는 `CURRENT.md` → `INDEX.md` → `RULES.md` → `VOLUME_CYCLE_FREEZE.md` → CURRENT가 가리키는 최신 ACTIVE `VOLUME_CYCLE_INSTRUCTION` → `거래량-순환매-Wiki.md` 순으로 확인한다.

그 후 최근 완료 정규장으로 **확정상태**를 확인하고, 정규장이 진행 중이면 장중 가격·동시간대 보정 거래량을 추가해 **장중 잠정상태(P-*)**와 **현재 행동지시**를 산출한다.

`VOLUME_CYCLE_INSTRUCTION_v1.0.0.md`는 **FROZEN 기준본**이며 본문을 수정하지 않는다. 파일 내부의 `상태: ACTIVE` 표시는 동결 전 원본 스냅샷의 일부로 보존한다.

`VOLUME_CYCLE_INSTRUCTION_v1.1.0.md`는 한 줄 행동지시를 도입한 이전 ACTIVE 이력으로 보존한다.

사용자의 2026-08-11 명시 지시에 따라 `VOLUME_CYCLE_INSTRUCTION_v1.2.0.md`를 MINOR 후속 버전으로 생성하고 **ACTIVE 운영 지시문**으로 승격하였다. v1.2.0은 장중 데이터를 현재 행동 판정의 핵심 입력으로 사용하며 `확정상태 + 장중상태 + 현재 행동지시` 3층 구조를 적용한다.

향후 변경은 v1.2.0을 직접 덮어쓰기보다 버전 규칙에 따라 새 버전 파일로 생성한다. v1.0.0 FROZEN 기준본은 계속 보존한다.

`거래량-순환매-Wiki.md`는 동결 대상이 아니며 최신 ACTIVE 지시문에 따라 Current View, Intraday View, Revision Timeline을 갱신할 수 있다.
