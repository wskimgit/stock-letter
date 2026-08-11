# CHATGPT_STOCK_WIKI_V1 운영 규칙

## 1. 독립성

이 Wiki는 `lab.php`와 독립한다. LAB 후보·가상체결·성과·experiment_hash를 자동으로 가져오거나 합산하지 않는다. 이 Wiki의 기록으로 브로커 주문, 실전자본 변경, LAB 상태 변경을 만들지 않는다.

## 2. 데이터 시점

분석은 최근 완료 정규장 기준으로 한다. 장중·시간외·NXT·프리·애프터마켓 가격은 참고값으로만 기록한다. 핵심 데이터의 기준일이 다르면 가격·이평·ATR을 혼합하지 않는다.

## 3. 선행 게이트

자료 무결성·기업위험 → 시장상태 → 섹터 → 종목구조 → 가격·거래량 반응 → 진입상태 → 지지·무효화·손익비 순서로 판정한다. 상위 단계가 불가하면 하위 계산을 중단한다.

## 4. 시장상태

프로젝트 시장상태는 `ON / WAIT / OFF`를 사용한다. WAIT·OFF에서는 Champion 신규매입, 물타기, 대체 실전추천, 실전 매입가·손익비 산정을 하지 않는다. 선발·관찰만 허용한다.

## 5. 종목 페이지 갱신 조건

아래 중 하나 이상이 바뀔 때만 저장한다.

- 시장상태
- 종목 상태
- 핵심 구조 판정
- 지지/돌파/무효화/목표의 의미 있는 가격대
- 기업위험
- 행동 지침
- 분석 근거가 되는 데이터 revision 또는 기업행동

단순 종가 변화, 문장 다듬기, 같은 상태의 반복 확인은 새 revision을 만들지 않는다.

## 6. Wikipedia형 갱신

각 종목 파일은 `Current View`와 `Revision Timeline`을 가진다.

- Current View: 최신 유효 판단으로 교체한다.
- Revision Timeline: 과거 기록을 삭제·수정하지 않고 아래에 append한다.
- 잘못된 과거 판단을 발견하면 원문을 고치지 않고 새 revision에 `정정`을 기록한다.
- GitHub commit history가 외부 revision history 역할을 한다.

## 7. 식별자

각 revision은 다음을 갖는다.

- `revision_id`: `YYYYMMDD-NN`
- `analysis_date`
- `latest_complete_session`
- `market`
- `ticker`
- `status`
- `market_state`
- `source_summary`
- `change_type`

## 8. 저장 성공

GitHub write가 성공하기 전에는 `저장 완료`, `이력 반영 완료`라고 표현하지 않는다. 실패하면 분석 결과와 저장 실패를 분리해서 보고한다.

## 9. 추천 시 읽기 우선

기존 종목을 다시 분석할 때는 먼저 `INDEX.md`와 해당 종목 페이지를 읽고 이전 판단과 비교한다. 이전 이력을 읽지 않은 상태에서 `누적변경`을 단정하지 않는다.

## 10. 신규 종목

페이지가 없으면 템플릿으로 신규 생성한다. 신규 추천이 없으면 빈 종목 페이지를 만들지 않는다.

## 11. 거래량 순환매 Wiki

`거래량-순환매-Wiki.md`는 `VOLUME_CYCLE_WIKI_V1`로 관리한다.

- 기본 감시종목: KR `스페코(013810)`, `빅텍(065450)`, `한일단조(024740)` / US `DPRO`, `RCAT`, `UAVS`.
- 사용자가 이 6종목의 순환매 상태, 거래량 고갈, 거래량 폭증, 매입·대기·매도 상태를 반복 질의하면 새 날짜별 MD 파일을 만들지 않는다.
- 먼저 `CURRENT.md`, `INDEX.md`, `RULES.md`, `VOLUME_CYCLE_FREEZE.md`, 동결 지시문, `거래량-순환매-Wiki.md`를 순서대로 확인하고 최신 완료 정규장 데이터와 비교한다.
- 상태 코드, 행동, 핵심 거래량 배율, 의미 있는 가격대, 기업위험 또는 감시종목 구성이 바뀔 때만 GitHub Wiki를 갱신한다.
- `Current View`는 최신 판단으로 교체하고 `Revision Timeline`에는 의미 있는 변경만 append한다.
- 장중·NXT·프리·애프터마켓 데이터는 참고값으로만 사용하며 완료장 판정과 혼합하지 않는다.
- 순환매 상태 코드는 `M0 / M1 / M2 / W / S1 / S2 / S3`를 사용한다.

## 12. 거래량 순환매 지시문 동결

`VOLUME_CYCLE_INSTRUCTION_v1.0.0.md`는 2026-08-11 기준 **FROZEN 기준본**이다.

- 동결 blob SHA: `7510654f7447fdfdcacc703fe8cf6b49f3f6c59d`
- 동결 기록: `VOLUME_CYCLE_FREEZE.md`
- 동결 파일의 본문은 수정·덮어쓰기 금지.
- 파일 내부의 `상태: ACTIVE` 문구는 동결 당시 원본의 일부로 보존하며, 운영상 상태는 `CURRENT.md`와 `VOLUME_CYCLE_FREEZE.md`의 `FROZEN` 판정을 우선한다.
- PATCH/MINOR/MAJOR 변경은 각각 새 버전 파일로만 생성한다.
- 새 버전은 사용자 명시 승인 전 FROZEN v1.0.0을 대체하지 않는다.
- 동결 무결성 확인이 필요하면 현재 blob SHA를 동결 SHA와 비교한다.
- 동결 대상은 지시문 규칙 본문이며 `거래량-순환매-Wiki.md`의 시장 상태 기록은 계속 갱신한다.
