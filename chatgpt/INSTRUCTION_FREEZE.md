# 종목 누적 분석 지시문 동결 기록

## 현재 유일한 동결본

- Version: `v4.7.2`
- File: `chatgpt/INSTRUCTION_v4.7.2.md`
- Status: `SPEC FROZEN`
- Freeze time: `2026-08-18T09:29+09:00`
- Frozen blob SHA: `4524356f60d2e39b5133c46ebb3eb33a4a29a433`
- Freeze commit: `23414a93bd68cc928f03ca817f74e3a507eb58fb`
- ERRC report: `chatgpt/INSTRUCTION_v4.7.2_ERRC.md`
- ERRC result: `PASS`
- Wiki schema: `CHATGPT_STOCK_WIKI_V1`

`v4.7.2`만 현재 운영에 효력이 있는 일반 종목 누적 분석 지시문이다.

## 직전 동결본 — 효력 해지

- Version: `v4.7.1`
- File: `chatgpt/INSTRUCTION_v4.7.1.md`
- Original status: `SPEC FROZEN`
- Current status: `RELEASED_HISTORY`
- Original freeze time: `2026-08-12T00:55+09:00`
- Release time: `2026-08-18T09:29+09:00`
- Frozen blob SHA: `b4628d9cc6f8974f5013d82a171931300b1fd732`
- Creation commit: `8fc92061e1e017a0e7b0d2b9170620008b225ad3`

`v4.7.1`의 동결 효력은 해지한다. 파일 본문과 기존 SHA는 수정하지 않고 역사 이력으로 보존한다.

## 이전 동결본 — 효력 해지

- Version: `v4.7.0`
- File: `chatgpt/INSTRUCTION_v4.7.0.md`
- Original status: `SPEC FROZEN`
- Current status: `RELEASED_HISTORY`
- Original freeze time: `2026-08-12T00:34+09:00`
- Release time: `2026-08-12T01:02+09:00`
- Frozen blob SHA: `6e8491d67f44216f0525bd022eb7efe1aeffc446`
- Creation commit: `4c6bfb43bb4658a860e698670c0c028cd2ccdd49`

`v4.7.0`의 동결 효력은 해지한다. 파일 본문과 기존 SHA는 수정하지 않고 역사 이력으로 보존한다.

## 이전 candidate 이력

- Version: `v4.6-candidate.4`
- File: `chatgpt/INSTRUCTION_v4.6-candidate.4.md`
- Original status: `SPEC CANDIDATE`
- Blob SHA: `05e41d07c4b7087e81dbcbac4f753f88e183650e`
- Current role: `SUPERSEDED_CANDIDATE_HISTORY`

## v4.7.2 동결 핵심

1. v4.7.1의 전체 추천 선재검증·stale 외부 재수집·LAB/Wiki 분리·GitHub canonical 규칙을 유지한다.
2. 5일선은 상위 게이트를 통과한 뒤 사용하는 단기 진입 타이밍 기준선으로 추가한다.
3. 상승 중인 5일선 위에서는 조건부 `5D-MOMENTUM` 20~30% 선진입을 검토할 수 있다.
4. 5일선 아래에서는 20일선/직전 돌파가격/구조지지를 유지하는 `5D-PULLBACK`을 우선한다.
5. `5일선 이탈 → 20일선/핵심지지 이탈 → 구조저점 훼손`의 단계형 위험관리로 구분한다.
6. 5일선 이탈 자체는 자동매도·자동해제 신호가 아니다.
7. `5D-RECLAIM`은 5일선 이탈 후 거래량 감소·20일선/지지 유지·5일선 재돌파 구조를 우선한다.
8. `5D-HALT`는 20일선 종가이탈/지지 훼손/RR<1.5/과도이격/시장 WAIT·OFF/중대기업위험 등에서 추격전략을 중단한다.
9. 60일선 미돌파 초기 회복형은 바닥형성·MA5 상승·MA20 회복/상승·저점 상승·저항여유·RR>=1.5일 때만 20~30% 선행진입을 허용한다.
10. 60일선은 자동 목표가가 아니라 우선 저항/재검증 구간이다.
11. Stochastic/RSI 과열은 단독 금지신호가 아니라 구조·이격·저항·거래량과 결합한 위험 보정요소다.
12. RR은 먼 최종목표가 아니라 바로 위 현실적 저항 기준으로 1.5 이상이어야 한다.
13. 장중/NXT/프리마켓/애프터마켓 5일선 위치는 완료장 확정신호로 사용하지 않는다.
14. Wiki Current View와 일반 분석 출력에 5일선 진입모드를 기록할 수 있다.
15. LAB 구현 메타데이터는 `v1.5.1-candidate.17 / IMPLEMENTATION_CANDIDATE`로 갱신한다.
16. ERRC·회귀검증 결과는 `PASS`다.

## 동결 정책

- `INSTRUCTION_v4.7.2.md`의 본문과 frozen blob SHA를 직접 수정하거나 덮어쓰지 않는다.
- 향후 변경이 필요하면 새 버전 파일을 만든다.
- 새 버전을 동결하면 현재 동결본의 효력을 명시적으로 해지하고 `RELEASED_HISTORY`로 보존한다.
- 과거 동결 파일과 SHA는 삭제하거나 새 판단에 맞춰 수정하지 않는다.
- GitHub 저장 성공 전에는 `동결 완료` 또는 `해지 완료`라고 표현하지 않는다.
