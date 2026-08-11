# 거래량 순환매 지시문 동결 기록

## 현재 동결 기준

- frozen_instruction: `VOLUME_CYCLE_INSTRUCTION_v2.2.0.md`
- frozen_operational_status: `FROZEN`
- freeze_timestamp: `2026-08-11T15:16+09:00`
- repository: `wskimgit/stock-letter`
- branch: `main`
- frozen_blob_sha: `99694d8d476dea84aae28b1d344ce273ef5e4fa2`
- wiki_schema: `VOLUME_CYCLE_WIKI_V2`
- wiki_file: `../거래량-순환매-Wiki.md`

## 직전 동결 기준

- previous_frozen_instruction: `VOLUME_CYCLE_INSTRUCTION_v2.1.0.md`
- previous_status: `FROZEN_HISTORY`
- previous_blob_sha: `99986e11d0b2a5aa6f98a1ba3787c63508febd4d`
- 처리: 파일은 수정·삭제하지 않고 이전 기준본으로 보존한다.

## 현재 기본 유니버스

- KR: 빅텍 `065450`, 퍼스텍 `010820`, 한일단조 `024740`
- US: RCAT, KTOS, DPRO

기본 제외:
- 스페코 `013810`: 평시 기본 유동성 부족
- UAVS: 저유동성·희석·갭 위험 과다

## v2.2.0 핵심 변경

- 순환 경과일을 6종목 공통 필수 운영값으로 승격
- 직전 주요고점일·고점상태(CONFIRMED/PROVISIONAL/DATA_LIMITED) 기록
- 달력일·거래일 경과를 항상 출력
- 평균·중앙값·범위·표본수·자료상태를 Wiki Current View에 유지
- 실제 계산된 종목별 순환통계 스냅샷을 기준문에 등록
- 미검증 값은 추정하지 않고 `미산정/재검증 필요`로 표시
- 경과일은 단독 매매신호가 아니라 유동성·M1/M2·거래량 고갈·바닥과 결합하는 보정요소

## 버전 이력

- `v1.0.0` = RELEASED_HISTORY
- `v1.1.0` = HISTORY
- `v1.2.0` = FROZEN_HISTORY
- `v2.0.0` = FROZEN_HISTORY
- `v2.1.0` = FROZEN_HISTORY
- `v2.2.0` = **현재 FROZEN 운영 기준본**

## 동결 원칙

1. 현재 운영 기준은 `VOLUME_CYCLE_INSTRUCTION_v2.2.0.md`이다.
2. v2.2.0의 동결 무결성 기준 SHA는 `99694d8d476dea84aae28b1d344ce273ef5e4fa2`이다.
3. v2.2.0 파일은 직접 수정·덮어쓰기하지 않는다.
4. 이후 변경은 반드시 새 버전 파일로 생성한다.
5. 재질의 시 GitHub를 먼저 읽고 최신 시장데이터와 비교한다.
6. Wiki의 Current View, Cycle Elapsed View, Intraday View, Revision Timeline은 계속 갱신할 수 있다.
7. 유동성·기업위험 게이트를 경과일보다 먼저 적용한다.
8. 표본이 부족하면 `자료상태=제한/부족`을 명시하고 주기성을 확정하지 않는다.

운영선:
`v1.0.0 RELEASED_HISTORY → v1.1.0 HISTORY → v1.2.0 FROZEN_HISTORY → v2.0.0 FROZEN_HISTORY → v2.1.0 FROZEN_HISTORY → v2.2.0 FROZEN`
