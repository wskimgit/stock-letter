# Current configuration

- Wiki schema: `CHATGPT_STOCK_WIKI_V1`
- Project instruction: `INSTRUCTION_v4.7.1.md`
- Project instruction status: `SPEC FROZEN`
- Project instruction frozen blob SHA: `b4628d9cc6f8974f5013d82a171931300b1fd732`
- Project instruction freeze registry: `INSTRUCTION_FREEZE.md`
- Previous project instruction: `INSTRUCTION_v4.7.0.md` — `RELEASED_HISTORY`
- Older project instruction: `INSTRUCTION_v4.6-candidate.4.md` — `SUPERSEDED_CANDIDATE_HISTORY`
- LAB implementation candidate: `1.5.1-candidate.16`
- LAB GitHub source mode: `GITHUB_ACTIONS_PULL`
- LAB canonical data: `../lab_data/LATEST.json`
- LAB pull source: `/lab_cache/github_source.json`
- LAB sync workflow: `../.github/workflows/lab-data-sync.yml`
- LAB data schema: `../lab_data/LATEST.schema.json`
- LAB web policy: `../lab_data/LAB_WEB_POLICY_v1.9_FROZEN.md`
- LAB web policy status: `SPEC FROZEN`
- LAB NAS GitHub credentials: `NONE`
- LAB local NAS artifacts: `PULL_SOURCE_MIRROR_AND_DIAGNOSTIC`
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
- Project instruction v4.7.1 original freeze: `2026-08-12T00:55+09:00`
- Project instruction v4.7.1 freeze reaffirmed: `2026-08-12T01:02+09:00`
- Project instruction v4.7.0 original freeze: `2026-08-12T00:34+09:00`
- Project instruction v4.7.0 released from frozen history: `2026-08-12T01:02+09:00`
- v2.2.0 original freeze: `2026-08-11T15:16+09:00`
- v2.2.0 freeze reaffirmed: `2026-08-11T16:48+09:00`
- v2.1.0 released from frozen history: `2026-08-11T16:48+09:00`

일반 전체 추천 질의(`추천하라`, `종목 추천`, 국가별 종목 추천 등)는 `CURRENT.md → INDEX.md → RULES.md → 활성 Stock Wiki 종목 전수 재검증 → stale/불완전 종목 외부 최신자료 재수집 → 의미 있는 변화 저장 → 신규 후보 탐색 → 기존+신규 동일기준 비교 → 국가별 최대 1종목 선정` 순으로 처리한다.

기존 Wiki 종목의 완료세션이 오래됐다는 사실만으로 `자료 부족`으로 하향하지 않는다. 거래소·공시·기업 IR·데이터 공급자·Yahoo Finance 등 금융정보서비스·주요 금융언론을 목적에 맞게 사용해 최신 완료세션 자료를 먼저 재수집한다. 가격·기술지표는 가능한 한 하나의 동일 수정 일봉 OHLCV 계열로 5·20·60·120·200일선과 ATR(14)을 계산한다. 외부 재수집 후에도 핵심자료가 실제로 확보되지 않을 때만 `자료 제한/자료 부족`을 사용한다.

기존 Wiki 종목이 최신 완료세션으로 재검증되지 않았으면 과거 `즉시 매입 가능/매입 대기/선발` 상태를 현재 추천 근거로 재사용하지 않는다. 동시에 stale이라는 이유만으로 자동 하향하지도 않는다.

상태가 의미 있게 변하면 Current View + Revision Timeline + INDEX를 동기화한다. 단순 반복확인이나 종가변화만 있으면 새 Revision을 만들지 않는다. 필요하면 최근 검증세션 메타데이터만 갱신할 수 있으며, write가 없으면 `상태 재검증: 유지 / Wiki write 없음`으로 표시한다.

LAB 자료를 사용하는 질의(`lab.php 자료로 추천`, `LAB 후보 분석` 등)는 `CURRENT.md → INSTRUCTION_v4.7.1.md → ../lab_data/LATEST.json` 순으로 확인한다. `LATEST.json`이 `WAITING_FOR_LAB_SYNC`, `DATA_STALE`, `DATA_INVALID`이거나 시장세션/후보세션 무결성이 깨져 있으면 최신 추천으로 사용하지 않는다. NAS `/lab_cache/*`, `/lab.php?view=*`, `/lab_chatgpt.html`은 GitHub canonical 감사·fallback용이며 1차 원천이 아니다.

`lab.php`는 GitHub token/PAT/SSH key를 사용하지 않는다. Tick/cron 후 `/lab_cache/github_source.json`을 발행하고 `.github/workflows/lab-data-sync.yml`이 5분 주기로 HTTPS 우선, HTTP fallback으로 이를 pull하여 `lab_data/LATEST.json`에 commit한다. 별도 사용자 GitHub secret/PAT는 요구하지 않는다. 동일 `source_fingerprint`이면 commit하지 않는다.

`1.5.1-candidate.16`부터 GitHub pack의 `active_experiment_hashes`는 **experiment_hash 문자열 목록**으로 고정하고, setup별 대응은 `active_experiment_map`으로 분리한다. PHP는 GitHub pull source를 쓰기 전에 동일 무결성 규칙으로 자체 검증한다. GitHub Actions validator는 candidate.15의 setup=>hash 형식도 호환해서 읽되 canonical 형식은 candidate.16 목록형이다.

LAB 현재 추천행은 현재 코드의 active `experiment_hash`와 현재 `market_session`만 사용한다. 과거 experiment_hash는 성과·감사 이력에만 유지하고 `VIRTUAL_OPEN`은 신규 추천이 아닌 `virtual_open_reference`로만 본다. LAB과 ChatGPT Stock Wiki는 계속 독립한다.

거래량 순환매 재질의 시에는 `CURRENT.md → INDEX.md → RULES.md → VOLUME_CYCLE_FREEZE.md → 현재 FROZEN VOLUME_CYCLE_INSTRUCTION → 거래량-순환매-Wiki.md` 순으로 확인한다.

현재 기본 감시종목은 KR `빅텍(065450)`, `퍼스텍(010820)`, `한일단조(024740)` / US `RCAT`, `KTOS`, `DPRO`이다.

핵심 판정은 `확정상태 + 장중 잠정상태(P-*) + 유동성 게이트 + 기업위험 + 순환 경과일 + 현재 행동지시`를 사용한다.

`v2.2.0`부터 순환 경과일은 6종목 모두의 필수 운영 데이터다. 각 종목에서 직전 주요고점일, 고점상태, 달력/거래일 경과, 평균·중앙값·범위·표본수·자료상태를 Wiki Current View에 유지한다. 계산값이 검증되지 않은 필드는 추정하지 않고 `미산정/재검증 필요`로 표시한다.

순환 경과일은 단독 매수·매도 신호가 아니며, 유동성·M1/M2·거래량 고갈·바닥 유지와 결합해 우선순위만 보정한다.

`VOLUME_CYCLE_INSTRUCTION_v2.2.0.md`만 현재 FROZEN 거래량 순환매 운영 기준본이다. 본문과 SHA를 직접 수정·덮어쓰기하지 않는다. `v2.1.0`은 동결 효력을 해제하고 `RELEASED_HISTORY`로 보존한다. 향후 변경은 새 버전으로 생성한다.

`INSTRUCTION_v4.7.1.md`만 현재 일반 종목 누적 분석의 **SPEC FROZEN** 기준본이다. 본문과 SHA를 직접 수정하지 않는다. `INSTRUCTION_v4.7.0.md`는 동결 효력을 해지하고 `RELEASED_HISTORY`로 보존한다. 향후 일반 지시문 변경은 새 버전으로 생성한다.
