# Current configuration

- Wiki schema: `CHATGPT_STOCK_WIKI_V1`
- Project instruction candidate: `INSTRUCTION_v4.6-candidate.1.md`
- Volume-cycle Wiki schema: `VOLUME_CYCLE_WIKI_V2`
- Volume-cycle current frozen instruction: `VOLUME_CYCLE_INSTRUCTION_v2.1.0.md`
- Volume-cycle current instruction status: `FROZEN`
- Volume-cycle current frozen blob SHA: `99986e11d0b2a5aa6f98a1ba3787c63508febd4d`
- Volume-cycle previous frozen instruction: `VOLUME_CYCLE_INSTRUCTION_v2.0.0.md`
- Volume-cycle previous frozen status: `FROZEN_HISTORY`
- Volume-cycle previous frozen blob SHA: `eefa43d535af5d338efc6e9f5e4b28a0eafaa724`
- Volume-cycle older history: `VOLUME_CYCLE_INSTRUCTION_v1.2.0.md`, `VOLUME_CYCLE_INSTRUCTION_v1.1.0.md`, `VOLUME_CYCLE_INSTRUCTION_v1.0.0.md`
- Volume-cycle freeze registry: `VOLUME_CYCLE_FREEZE.md`
- Volume-cycle Wiki: `../거래량-순환매-Wiki.md`
- LAB coupling: `NONE`
- Git branch: `main`
- v2.1.0 frozen from: `2026-08-11T14:02+09:00`

거래량 순환매 재질의 시에는 `CURRENT.md → INDEX.md → RULES.md → VOLUME_CYCLE_FREEZE.md → 현재 FROZEN 지시문 → 거래량-순환매-Wiki.md` 순으로 확인한다.

현재 기본 감시종목은 KR `빅텍(065450)`, `퍼스텍(010820)`, `한일단조(024740)` / US `RCAT`, `KTOS`, `DPRO`이다.

핵심 판정은 `확정상태 + 장중 잠정상태(P-*) + 유동성 게이트 + 기업위험 + 직전 주요고점 경과일 + 현재 행동지시`를 사용한다.

각 종목은 `last_major_peak_date`, 달력/거래일 경과, 과거 고점간격 평균·중앙값·범위, 표본수와 순환 타이밍을 함께 관리한다. 경과일은 단독 매수신호로 사용하지 않는다.

`VOLUME_CYCLE_INSTRUCTION_v2.1.0.md`는 현재 FROZEN 운영 기준본이며 본문을 직접 수정·덮어쓰기하지 않는다. 향후 변경은 새 버전으로 생성한다.
