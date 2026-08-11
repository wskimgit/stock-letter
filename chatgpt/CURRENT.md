# Current configuration

- Wiki schema: `CHATGPT_STOCK_WIKI_V1`
- Project instruction candidate: `INSTRUCTION_v4.6-candidate.3.md`
- Project instruction status: `SPEC CANDIDATE`
- LAB implementation candidate: `1.5.1-candidate.14`
- LAB GitHub source mode: `GITHUB_PRIMARY`
- LAB canonical data: `../lab_data/LATEST.json`
- LAB data schema: `../lab_data/LATEST.schema.json`
- LAB web policy: `../lab_data/LAB_WEB_POLICY_v1.8_FROZEN.md`
- LAB web policy status: `SPEC FROZEN`
- LAB local NAS artifacts: `MIRROR_AND_DIAGNOSTIC`
- LAB coupling: `NONE`
- Volume-cycle Wiki schema: `VOLUME_CYCLE_WIKI_V2`
- Volume-cycle current frozen instruction: `VOLUME_CYCLE_INSTRUCTION_v2.2.0.md`
- Volume-cycle current instruction status: `FROZEN`
- Volume-cycle current frozen blob SHA: `99694d8d476dea84aae28b1d344ce273ef5e4fa2`
- Volume-cycle previous instruction: `VOLUME_CYCLE_INSTRUCTION_v2.1.0.md`
- Volume-cycle previous instruction status: `RELEASED_HISTORY`
- Volume-cycle previous blob SHA: `99986e11d0b2a5aa6f98a1ba3787c63508febd4d`
- Volume-cycle older history: `VOLUME_CYCLE_INSTRUCTION_v2.0.0.md`, `VOLUME_CYCLE_INSTRUCTION_v1.2.0.md`, `VOLUME_CYCLE_INSTRUCTION_v1.1.0.md`, `VOLUME_CYCLE_INSTRUCTION_v1.0.0.md`
- Volume-cycle freeze registry: `VOLUME_CYCLE_FREEZE.md`
- Volume-cycle Wiki: `../거래량-순환매-Wiki.md`
- Git branch: `main`
- v2.2.0 original freeze: `2026-08-11T15:16+09:00`
- v2.2.0 freeze reaffirmed: `2026-08-11T16:48+09:00`
- v2.1.0 released from frozen history: `2026-08-11T16:48+09:00`

LAB 자료를 사용하는 질의(`lab.php 자료로 추천`, `LAB 후보 분석` 등)는 `CURRENT.md → INSTRUCTION_v4.6-candidate.3.md → ../lab_data/LATEST.json` 순으로 확인한다. `LATEST.json`이 `WAITING_FOR_LAB_SYNC`, `DATA_STALE`, `DATA_INVALID`이거나 시장세션/후보세션 무결성이 깨져 있으면 최신 추천으로 사용하지 않는다. NAS `/lab_cache/*`, `/lab.php?view=*`, `/lab_chatgpt.html`은 GitHub source 감사·fallback용이며 1차 원천이 아니다.

LAB 현재 추천행은 현재 코드의 active `experiment_hash`와 현재 `market_session`만 사용한다. 과거 experiment_hash는 성과·감사 이력에만 유지하고 `VIRTUAL_OPEN`은 신규 추천이 아닌 `virtual_open_reference`로만 본다. LAB과 ChatGPT Stock Wiki는 계속 독립한다.

거래량 순환매 재질의 시에는 `CURRENT.md → INDEX.md → RULES.md → VOLUME_CYCLE_FREEZE.md → 현재 FROZEN 지시문 → 거래량-순환매-Wiki.md` 순으로 확인한다.

현재 기본 감시종목은 KR `빅텍(065450)`, `퍼스텍(010820)`, `한일단조(024740)` / US `RCAT`, `KTOS`, `DPRO`이다.

핵심 판정은 `확정상태 + 장중 잠정상태(P-*) + 유동성 게이트 + 기업위험 + 순환 경과일 + 현재 행동지시`를 사용한다.

`v2.2.0`부터 순환 경과일은 6종목 모두의 필수 운영 데이터다. 각 종목에서 직전 주요고점일, 고점상태, 달력/거래일 경과, 평균·중앙값·범위·표본수·자료상태를 Wiki Current View에 유지한다. 계산값이 검증되지 않은 필드는 추정하지 않고 `미산정/재검증 필요`로 표시한다.

순환 경과일은 단독 매수·매도 신호가 아니며, 유동성·M1/M2·거래량 고갈·바닥 유지와 결합해 우선순위만 보정한다.

`VOLUME_CYCLE_INSTRUCTION_v2.2.0.md`만 현재 FROZEN 운영 기준본이다. 본문과 SHA를 직접 수정·덮어쓰기하지 않는다. `v2.1.0`은 동결 효력을 해제하고 `RELEASED_HISTORY`로 보존한다. 향후 변경은 새 버전으로 생성한다.
