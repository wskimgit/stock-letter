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
| 거래량 순환매 | `VOLUME_CYCLE_WIKI_V2` | KR: 빅텍·퍼스텍·한일단조 / US: RCAT·KTOS·DPRO | `v2.2.0 FROZEN` | 2026-08-11 | [거래량 순환매 Wiki](../거래량-순환매-Wiki.md) |

### 거래량 순환매 기준문

- 현재 동결 지시문: [VOLUME_CYCLE_INSTRUCTION_v2.2.0.md](VOLUME_CYCLE_INSTRUCTION_v2.2.0.md)
- 현재 동결 blob SHA: `99694d8d476dea84aae28b1d344ce273ef5e4fa2`
- 직전 동결 이력: [VOLUME_CYCLE_INSTRUCTION_v2.1.0.md](VOLUME_CYCLE_INSTRUCTION_v2.1.0.md)
- 동결 기록: [VOLUME_CYCLE_FREEZE.md](VOLUME_CYCLE_FREEZE.md)
- v2.0.0 핵심 변경: 스페코→퍼스텍, UAVS→KTOS 교체 및 최소 유동성 게이트 도입
- v2.1.0 핵심 변경: 직전 주요고점 이후 달력/거래일 경과, 과거 고점간격 평균·중앙값·범위·표본수, 순환 타이밍 상태 추가
- v2.2.0 핵심 변경: **순환 경과일을 6종목 공통 필수 운영값으로 승격하고 실제 계산값을 Wiki Current View에 상시 유지**

## 상태 정의

`M0 / M1 / M2 / W / S1 / S2 / S3` + 장중 `P-*`

순환 타이밍은 상태코드와 별도로 관리하며 단독 매수·매도 신호로 사용하지 않는다.

`LAB 가상후보`는 이 Wiki의 상태로 사용하지 않는다.
