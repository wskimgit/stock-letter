# Current configuration

- Wiki schema: `CHATGPT_STOCK_WIKI_V1`
- Project instruction candidate: `INSTRUCTION_v4.6-candidate.1.md`
- Volume-cycle Wiki schema: `VOLUME_CYCLE_WIKI_V1`
- Volume-cycle active instruction: `VOLUME_CYCLE_INSTRUCTION_v1.0.0.md`
- Volume-cycle Wiki: `../거래량-순환매-Wiki.md`
- LAB coupling: `NONE`
- Git branch: `main`
- Started: `2026-08-08`
- Volume-cycle instruction active from: `2026-08-11`

일반 주식 프로젝트 운영 시 먼저 `CURRENT.md` → `INDEX.md` → 해당 종목 페이지 → `RULES.md` 순으로 확인한다.

거래량 순환매 재질의 시에는 `CURRENT.md` → `INDEX.md` → `RULES.md` → CURRENT가 가리키는 최신 `VOLUME_CYCLE_INSTRUCTION` → `거래량-순환매-Wiki.md` 순으로 먼저 확인한 뒤 최신 완료 정규장 데이터와 비교한다.

`v4.6-candidate.1`은 SPEC CANDIDATE이며 사용자 승인 전 FROZEN으로 표현하지 않는다.

`VOLUME_CYCLE_INSTRUCTION_v1.0.0.md`는 ACTIVE이며, 이후 변경 시 기존 파일을 덮어쓰지 않고 새 버전을 생성한 뒤 이 CURRENT 포인터를 갱신한다.
