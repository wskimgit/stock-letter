# Current configuration

- Wiki schema: `CHATGPT_STOCK_WIKI_V1`
- Project instruction candidate: `INSTRUCTION_v4.6-candidate.1.md`
- Volume-cycle Wiki schema: `VOLUME_CYCLE_WIKI_V1`
- Volume-cycle frozen instruction: `VOLUME_CYCLE_INSTRUCTION_v1.0.0.md`
- Volume-cycle instruction status: `FROZEN`
- Volume-cycle frozen blob SHA: `7510654f7447fdfdcacc703fe8cf6b49f3f6c59d`
- Volume-cycle freeze registry: `VOLUME_CYCLE_FREEZE.md`
- Volume-cycle Wiki: `../거래량-순환매-Wiki.md`
- LAB coupling: `NONE`
- Git branch: `main`
- Started: `2026-08-08`
- Volume-cycle frozen from: `2026-08-11`

일반 주식 프로젝트 운영 시 먼저 `CURRENT.md` → `INDEX.md` → 해당 종목 페이지 → `RULES.md` 순으로 확인한다.

거래량 순환매 재질의 시에는 `CURRENT.md` → `INDEX.md` → `RULES.md` → `VOLUME_CYCLE_FREEZE.md` → `VOLUME_CYCLE_INSTRUCTION_v1.0.0.md` → `거래량-순환매-Wiki.md` 순으로 먼저 확인한 뒤 최신 완료 정규장 데이터와 비교한다.

`v4.6-candidate.1`은 SPEC CANDIDATE이며 사용자 승인 전 FROZEN으로 표현하지 않는다.

`VOLUME_CYCLE_INSTRUCTION_v1.0.0.md`는 운영 기준 **FROZEN**이다. 해당 파일 본문은 수정하지 않는다. 파일 내부의 `상태: ACTIVE` 표시는 동결 전 원본 스냅샷의 일부로 보존한다. 이후 변경은 반드시 새 버전 파일로 생성하며, 새 버전은 사용자 명시 승인 전 기존 FROZEN 기준본을 대체하지 않는다.

`거래량-순환매-Wiki.md`는 동결 대상이 아니며, 동결된 v1.0.0 규칙에 따라 Current View와 Revision Timeline을 계속 갱신한다.
