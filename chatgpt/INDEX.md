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
| 거래량 순환매 | `VOLUME_CYCLE_WIKI_V1` | KR: 스페코·빅텍·한일단조 / US: DPRO·RCAT·UAVS | `v1.2.0 FROZEN / v1.0.0 RELEASED_HISTORY` | 2026-08-11 | [거래량 순환매 Wiki](../거래량-순환매-Wiki.md) |

### 거래량 순환매 기준문

- 현재 동결 지시문: [VOLUME_CYCLE_INSTRUCTION_v1.2.0.md](VOLUME_CYCLE_INSTRUCTION_v1.2.0.md)
- 현재 동결 blob SHA: `687d70bb5db6fce33c70d94db7cc0bc496f9a547`
- 동결 시각: `2026-08-11T12:46+09:00`
- 직전 활성 이력: [VOLUME_CYCLE_INSTRUCTION_v1.1.0.md](VOLUME_CYCLE_INSTRUCTION_v1.1.0.md)
- 이전 동결 기준본: [VOLUME_CYCLE_INSTRUCTION_v1.0.0.md](VOLUME_CYCLE_INSTRUCTION_v1.0.0.md)
- 이전 기준본 상태: `RELEASED_HISTORY`
- 이전 blob SHA: `7510654f7447fdfdcacc703fe8cf6b49f3f6c59d`
- 동결 기록: [VOLUME_CYCLE_FREEZE.md](VOLUME_CYCLE_FREEZE.md)
- v1.1.0 핵심 변경: `1.2 현재 순환 순서` 및 재질의 출력에 **한줄 행동지시** 추가
- v1.2.0 핵심 변경: **장중 데이터를 현재 행동 판정에 적극 반영**, `확정상태 + 장중 잠정상태(P-*) + 현재 행동지시` 3층 구조 도입, 동시간대 거래량 보정 적용
- 향후 지시문 변경은 현재 동결본을 덮어쓰지 않고 새 버전 파일로 생성한다.

## 상태 정의

`즉시 매입 가능 / 매입 대기 / 선발 / 관찰 / 보유 / 해제 / 추천 없음 / 자료 부족`

`LAB 가상후보`는 이 Wiki의 상태로 사용하지 않는다. LAB 상태는 `lab.php`에서만 관리한다.
