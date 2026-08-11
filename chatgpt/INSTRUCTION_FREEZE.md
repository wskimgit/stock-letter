# 종목 누적 분석 지시문 동결 기록

## 현재 동결본

- Version: `v4.7.0`
- File: `chatgpt/INSTRUCTION_v4.7.0.md`
- Status: `SPEC FROZEN`
- Freeze time: `2026-08-12T00:34+09:00`
- Frozen blob SHA: `6e8491d67f44216f0525bd022eb7efe1aeffc446`
- Creation commit: `4c6bfb43bb4658a860e698670c0c028cd2ccdd49`
- Wiki schema: `CHATGPT_STOCK_WIKI_V1`

## 직전 기준

- Version: `v4.6-candidate.4`
- File: `chatgpt/INSTRUCTION_v4.6-candidate.4.md`
- Original status: `SPEC CANDIDATE`
- Blob SHA: `05e41d07c4b7087e81dbcbac4f753f88e183650e`
- Current role: `SUPERSEDED_CANDIDATE_HISTORY`

직전 candidate 파일은 이력 보존을 위해 그대로 둔다. 현재 운영 기준으로 사용하지 않는다.

## v4.7.0 동결 핵심

1. 전체 추천 질의에서는 신규 탐색 전에 기존 활성 Stock Wiki 종목을 최신 완료 정규장 기준으로 전수 재검증한다.
2. stale Wiki 상태를 현재 추천 근거로 자동 재사용하지 않는다.
3. 재검증 불가 종목은 `자료 제한/자료 부족`으로 처리한다.
4. 의미 있는 판단 변화가 있으면 Current View + Revision Timeline + INDEX를 동기화한다.
5. 단순 반복확인은 새 Revision을 만들지 않는다.
6. 기존 종목과 신규 후보를 동일 시장·동일 완료세션·동일 Champion 기준으로 비교한다.
7. 국가별 최대 1종목만 선정하며 적합 종목이 없으면 `추천 없음`으로 한다.
8. LAB과 Stock Wiki, 실전 주문은 계속 독립한다.

## 동결 정책

`INSTRUCTION_v4.7.0.md`의 본문과 frozen blob SHA를 직접 수정하거나 덮어쓰지 않는다.

향후 변경이 필요하면 새 버전 파일을 만든다. 예:

- `INSTRUCTION_v4.7.1.md`
- 또는 다음 minor/major 버전

새 버전을 동결할 경우 이 파일에는 새 동결 기록을 추가하되 과거 동결 기록을 삭제하지 않는다.

GitHub 저장 성공 전에는 `동결 완료`라고 표현하지 않는다.
