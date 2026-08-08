# ChatGPT 종목 누적 분석 Wiki

이 디렉터리는 `lab.php`와 완전히 별개의 ChatGPT 종목 분석 이력 저장소다.

## 목적

- LAB 가상실험 이력과 ChatGPT 분석 이력을 이중화한다.
- 종목별로 하나의 문서를 유지하며 Wikipedia처럼 최신판을 갱신한다.
- 과거 판단은 삭제하지 않고 문서의 `변경 이력`에 누적한다.
- GitHub commit history를 2차 revision history로 사용한다.
- 이 저장소의 기록은 실전 주문 또는 LAB 가상체결을 발생시키지 않는다.

## 디렉터리

```text
chatgpt/
├─ README.md
├─ INDEX.md
├─ RULES.md
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

1. **현재판(Current View)**: 가장 최근 완료 정규장 기준의 현재 시장상태, 기업위험, 구조, 상태, 지지/돌파/무효화, 목표/손익비, 행동을 표시한다.
2. **변경 이력(Revision Timeline)**: 의미 있는 판정 변화만 날짜순으로 append한다. 과거 항목을 새 판단에 맞춰 고쳐 쓰지 않는다.

## 읽기/쓰기 절차

ChatGPT가 종목을 분석하거나 추천할 때:

1. 최신 완료 정규장과 데이터 무결성을 확인한다.
2. `chatgpt/INDEX.md`를 읽는다.
3. 해당 종목 페이지가 있으면 먼저 읽어 이전 상태와 비교한다.
4. 시장→기업위험→구조→가격반응→진입상태 순으로 판정한다.
5. 의미 있는 변화가 있을 때만 종목 페이지의 Current View를 갱신하고 Revision Timeline에 1행을 추가한다.
6. 상태/핵심가격/행동이 바뀌면 `INDEX.md`도 갱신한다.
7. GitHub 저장 성공 후에만 `이력 반영 완료`라고 표현한다.

## LAB과의 분리

- `lab.php`, LAB runtime/cache, experiment_hash, GAP/RS/VCP 성과와 이 디렉터리는 독립이다.
- LAB 자료를 이곳에 자동 병합하지 않는다.
- 같은 종목이 LAB과 ChatGPT 양쪽에 존재할 수 있으나 상태와 성과를 합산하지 않는다.
- ChatGPT Wiki는 분석 이력 저장소이며 주문·자본·포지션 파일을 읽거나 쓰지 않는다.

## 초기 운영 기준

2026-08-08부터 신규 분석/추천 종목을 누적한다. 기존 과거 종목은 사용자가 명시적으로 요청하거나 후속 분석에서 다시 등장할 때부터 편입한다.
