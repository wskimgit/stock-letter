# 종목 누적 분석 지시문 동결 기록

## 현재 유일한 동결본

- Version: `v4.7.1`
- File: `chatgpt/INSTRUCTION_v4.7.1.md`
- Status: `SPEC FROZEN`
- Original freeze time: `2026-08-12T00:55+09:00`
- Freeze reaffirmed: `2026-08-12T01:02+09:00`
- Frozen blob SHA: `b4628d9cc6f8974f5013d82a171931300b1fd732`
- Creation commit: `8fc92061e1e017a0e7b0d2b9170620008b225ad3`
- Wiki schema: `CHATGPT_STOCK_WIKI_V1`

`v4.7.1`만 현재 운영에 효력이 있는 일반 종목 누적 분석 지시문이다.

## 직전 동결본 — 효력 해지

- Version: `v4.7.0`
- File: `chatgpt/INSTRUCTION_v4.7.0.md`
- Original status: `SPEC FROZEN`
- Current status: `RELEASED_HISTORY`
- Original freeze time: `2026-08-12T00:34+09:00`
- Release time: `2026-08-12T01:02+09:00`
- Frozen blob SHA: `6e8491d67f44216f0525bd022eb7efe1aeffc446`
- Creation commit: `4c6bfb43bb4658a860e698670c0c028cd2ccdd49`

`v4.7.0`의 동결 효력은 해지한다. 파일 본문과 기존 SHA는 수정하지 않고 역사 이력으로 보존한다. 현재 운영 기준으로 사용하지 않는다.

## 이전 candidate 이력

- Version: `v4.6-candidate.4`
- File: `chatgpt/INSTRUCTION_v4.6-candidate.4.md`
- Original status: `SPEC CANDIDATE`
- Blob SHA: `05e41d07c4b7087e81dbcbac4f753f88e183650e`
- Current role: `SUPERSEDED_CANDIDATE_HISTORY`

## v4.7.1 동결 핵심

1. 전체 추천 질의에서는 신규 탐색 전에 기존 활성 Stock Wiki 종목을 최신 완료 정규장 기준으로 전수 재검증한다.
2. stale Wiki 상태를 현재 추천 근거로 자동 재사용하지 않는다.
3. stale이라는 이유만으로 즉시 `자료 부족/자료 제한`으로 하향하지 않는다.
4. stale 또는 기술자료 불완전 종목은 거래소·공시·기업 IR·데이터 공급자·Yahoo Finance 등 금융정보서비스·주요 금융언론을 이용해 외부 최신자료 재수집을 먼저 시도한다.
5. 가격·기술지표는 가능한 한 하나의 동일 수정 일봉 OHLCV 계열에서 MA5·20·60·120·200과 ATR(14)을 직접 계산한다.
6. 서로 다른 기준일 또는 수정주가 체계의 종가·이평·ATR을 임의 혼합하지 않는다.
7. 기업위험은 가격정보 사이트만으로 완료하지 않고 공시·기업 공식자료를 우선한다.
8. 외부 재수집 이후에도 핵심자료가 실제로 부족할 때만 `자료 제한/자료 부족`을 사용한다.
9. 과거 단순 stale 때문에 잘못 `자료 부족`으로 하향된 기록은 삭제하지 않고 다음 최신 재검증에서 `CORRECTION` 또는 `STATUS` Revision으로 정정한다.
10. 의미 있는 판단 변화가 있으면 Current View + Revision Timeline + INDEX를 동기화하고, 단순 반복확인은 새 Revision을 만들지 않는다.
11. 기존 종목과 신규 후보를 동일 시장·동일 완료세션·동일 Champion 기준으로 비교한다.
12. 국가별 최대 1종목만 선정하며 적합 종목이 없으면 `추천 없음`으로 한다.
13. LAB과 Stock Wiki, 실전 주문은 계속 독립한다.

## 동결 정책

- `INSTRUCTION_v4.7.1.md`의 본문과 frozen blob SHA를 직접 수정하거나 덮어쓰지 않는다.
- 향후 변경이 필요하면 새 버전 파일을 만든다.
- 새 버전을 동결하면 현재 동결본의 효력을 명시적으로 해지하고 `RELEASED_HISTORY`로 보존한다.
- 과거 동결 파일과 SHA는 삭제하거나 새 판단에 맞춰 수정하지 않는다.
- GitHub 저장 성공 전에는 `동결 완료` 또는 `해지 완료`라고 표현하지 않는다.
