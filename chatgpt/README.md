# ChatGPT 종목 누적 분석 Wiki

이 디렉터리는 `lab.php`와 완전히 별개의 ChatGPT 종목 분석 이력 저장소다.

현재 일반 종목 분석 상위 기준문은 `INSTRUCTION_v4.7.0.md / SPEC FROZEN`이다.

## 목적

- LAB 가상실험 이력과 ChatGPT 분석 이력을 이중화한다.
- 종목별로 하나의 문서를 유지하며 Wikipedia처럼 최신판을 갱신한다.
- 과거 판단은 삭제하지 않고 문서의 `Revision Timeline`에 누적한다.
- GitHub commit history를 2차 revision history로 사용한다.
- 이 저장소의 기록은 실전 주문 또는 LAB 가상체결을 발생시키지 않는다.
- 전체 추천 시 기존 Wiki 종목이 오래된 상태로 남아 신규 후보와 경쟁하지 않도록 먼저 재검증한다.

## 디렉터리

```text
chatgpt/
├─ CURRENT.md
├─ README.md
├─ INDEX.md
├─ RULES.md
├─ INSTRUCTION_v4.7.0.md
├─ INSTRUCTION_FREEZE.md
├─ stock_history.schema.json
├─ templates/
│  └─ STOCK.md
└─ stocks/
   ├─ KR/
   ├─ US/
   └─ JP/
```

## 종목 페이지 원칙

파일명은 거래소에서 식별 가능한 ticker/code를 사용한다.

- 한국: `stocks/KR/000660.md`
- 미국: `stocks/US/MS.md`
- 일본: `stocks/JP/7203.md`

한 종목의 페이지는 다음 두 층으로 관리한다.

1. **Current View**: 최근 유효판단 기준의 시장상태, 기업위험, 구조, 상태, 지지/돌파/무효화, 목표/손익비, 행동을 표시한다. 필요하면 최근 완료세션과 최근 검증세션을 구분해 기록한다.
2. **Revision Timeline**: 의미 있는 판정 변화만 날짜순으로 append한다. 과거 항목을 새 판단에 맞춰 고쳐 쓰지 않는다.

## 단일 종목 읽기/쓰기 절차

ChatGPT가 기존 종목을 분석할 때:

1. `CURRENT.md`를 읽는다.
2. `INDEX.md`를 읽는다.
3. 해당 종목 페이지를 읽는다.
4. `RULES.md`를 확인한다.
5. 최신 완료 정규장과 데이터 무결성을 확인한다.
6. 시장→기업위험→구조→가격반응→진입상태 순으로 재판정한다.
7. 의미 있는 변화가 있으면 Current View와 Revision Timeline을 갱신한다.
8. 상태/핵심가격/행동이 바뀌면 `INDEX.md`도 동기화한다.
9. GitHub 저장 성공 후에만 `이력 반영 완료`라고 표현한다.

## 전체 추천 질의 절차

`추천하라`, `종목 추천`, `한국·미국·일본 추천`처럼 지정 종목이 없는 경우에는 신규 종목 탐색부터 시작하지 않는다.

고정 순서:

`CURRENT.md → INDEX.md → RULES.md → 활성 Wiki 종목 전수 재검증 → 의미 있는 변화 저장 → 신규 후보 탐색 → 기존+신규 동일기준 비교 → 국가별 최대 1종목`

운영 원칙:

- INDEX에 등재된 `해제`가 아닌 기존 종목은 원칙적으로 최신 완료장 기준 재검증 대상이다.
- 기존 페이지의 완료세션이 stale이면 과거 `즉시 매입 가능/매입 대기/선발` 상태를 현재 추천 근거로 자동 재사용하지 않는다.
- 최신 재검증이 불가능하면 `자료 제한/자료 부족`으로 처리한다.
- 기존 종목과 신규 후보는 동일 시장·동일 완료세션·동일 Champion 기준으로 비교한다.
- 의미 있는 변화가 있으면 Current View + Revision Timeline + INDEX를 함께 갱신한다.
- 단순 종가변화나 같은 상태 반복확인은 새 Revision을 만들지 않는다.
- 상태가 그대로이고 GitHub write도 없으면 `상태 재검증: 유지 / Wiki write 없음`으로 표시한다.
- 적절한 후보가 없으면 `추천 없음`으로 끝낸다.

## LAB과의 분리

- `lab.php`, LAB runtime/cache, experiment_hash, GAP/RS/VCP 성과와 이 디렉터리는 독립이다.
- LAB 자료를 Stock Wiki에 자동 병합하지 않는다.
- 같은 종목이 LAB과 ChatGPT 양쪽에 존재할 수 있으나 상태와 성과를 합산하지 않는다.
- ChatGPT Wiki는 분석 이력 저장소이며 주문·자본·포지션 파일을 읽거나 쓰지 않는다.

## 동결 기준

현재 일반 종목 분석 기준:

- `INSTRUCTION_v4.7.0.md`
- 상태: `SPEC FROZEN`
- 동결일: `2026-08-12`
- 동결 기록: `INSTRUCTION_FREEZE.md`

동결 지시문은 직접 수정하지 않는다. 변경 시 새 버전을 만들고 기존 파일은 보존한다.

## 초기 운영 기준

2026-08-08부터 신규 분석/추천 종목을 누적한다. 기존 과거 종목은 사용자가 명시적으로 요청하거나 후속 분석에서 다시 등장할 때부터 편입한다.
