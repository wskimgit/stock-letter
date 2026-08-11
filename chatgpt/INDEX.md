# ChatGPT 종목 누적 분석 Index

- 저장체계: `CHATGPT_STOCK_WIKI_V1`
- LAB 연계: 없음
- 기준 시작일: 2026-08-08
- 갱신 조건: 의미 있는 상태·핵심가격·행동 변화

## 종목 Wiki

| 시장 | 종목 | 이름 | 현재 상태 | 최근 완료세션 | 최근 갱신 | 문서 |
|---|---|---|---|---|---|---|
| US | MS | Morgan Stanley | 매입 대기 | 2026-08-07 | 2026-08-08 | [MS](stocks/US/MS.md) |
| US | DELL | Dell Technologies | 매입 대기 | 2026-08-07 | 2026-08-08 | [DELL](stocks/US/DELL.md) |

## 전략 Wiki

| 전략 | 저장체계 | 감시 대상 | 지시문 상태 | 최근 갱신 | 문서 |
|---|---|---|---|---|---|
| 거래량 순환매 | `VOLUME_CYCLE_WIKI_V2` | KR: 빅텍·퍼스텍·한일단조 / US: RCAT·KTOS·DPRO | `v2.0.0 FROZEN` | 2026-08-11 | [거래량 순환매 Wiki](../거래량-순환매-Wiki.md) |

### 거래량 순환매 기준문

- 현재 동결 지시문: [VOLUME_CYCLE_INSTRUCTION_v2.0.0.md](VOLUME_CYCLE_INSTRUCTION_v2.0.0.md)
- 현재 동결 blob SHA: `eefa43d535af5d338efc6e9f5e4b28a0eafaa724`
- 직전 동결 이력: [VOLUME_CYCLE_INSTRUCTION_v1.2.0.md](VOLUME_CYCLE_INSTRUCTION_v1.2.0.md)
- 동결 기록: [VOLUME_CYCLE_FREEZE.md](VOLUME_CYCLE_FREEZE.md)
- v2.0.0 핵심 변경: 스페코→퍼스텍, UAVS→KTOS 교체 및 최소 유동성 게이트 도입

## 상태 정의

`M0 / M1 / M2 / W / S1 / S2 / S3` + 장중 `P-*`

`LAB 가상후보`는 이 Wiki의 상태로 사용하지 않는다.
