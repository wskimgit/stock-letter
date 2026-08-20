# SIS 2nd 종목 분석 지시문 v2.2.6 — MLG / STC14 / G240 / ERRC

- 기준일: 2026-08-21
- 상태: **IMPLEMENTATION_CANDIDATE**
- 보호 기준본: `SIS_INSTRUCTION_v2.2.5.md`
- 성격: **v2.2.5 IMMUTABLE + ADDITIVE MLG/SCANNER OVERLAY**
- 공식 그룹: `SIS 1st(전체scan) → SIS 2nd 종목 분석 → SIS last 개별 평단가 확인`

## 0. 최우선 보존 선언

본 파일은 `SIS_INSTRUCTION_v2.2.5.md`를 새 문장으로 재작성하거나 요약해 대체하지 않는다.

v2.2.5의 모든 기존 조항은 그대로 유효하다. 본 v2.2.6은 **MLG 위험 Overlay와 STC14/G240 기술 Overlay만 추가**한다.

명시되지 않은 모든 판단·계산·출력·금지규칙은 v2.2.5를 그대로 따른다.

## 1. v2.2.5 핵심 불변조건

다음은 절대 변경하지 않는다.

### 1-1. 3-Track 구조

`GENERAL FIND + CYCLE TRACK + LAB TRACK`

세 Track의 결과를 독립 보존한 뒤 `CROSS VALIDATION`에서 통합한다.

### 1-2. CYCLE

고정 Universe:

- KR: 빅텍 `065450`, 퍼스텍 `010820`, 한일단조 `024740`
- US: `RCAT`, `KTOS`, `DPRO`

상태코드:

- M0 관심 소멸 → 관찰
- M1 거래량 고갈 → 매입 검토
- M2 바닥 확인 → 분할매입
- W 중립 → 대기
- S1 관심 증가 → 신규매입 금지·매도 준비
- S2 거래량 폭증 → 분할매도
- S3 과열 → 대부분/전량매도 검토

시간경과만으로 매입신호를 만들지 않는다. 새 이벤트/ATTENTION_SPIKE가 확인되면 새 주요고점 후보와 Cycle Clock 재설정 여부를 검증한다.

### 1-3. LAB

LAB는 `SUPPORTING_ONLY / READ-ONLY`다.

- `actual_buy=false`
- `VIRTUAL_WAIT`, `VIRTUAL_OPEN`, `CANDIDATE`는 실제 매입/보유 아님
- LAB 단독 BUY READY 생성 금지
- LAB가 SIS Market Gate 우회 금지
- LAB signal=0은 GENERAL 후보 탈락 의미 아님
- 실제 실행·publication이 확인된 최신 버전만 사용
- LAB 발견은 `SIS 재검증 대상 승격`일 뿐 `BUY READY`가 아님

### 1-4. 데이터 무결성

- 최신 완료장 우선
- stale 가격을 실행가격으로 사용 금지
- 과거 PHASE 자동 승계 금지
- 확인되지 않은 PRICE/Stop/Target/RR 추정 금지
- 자료가 부족하면 `미산정 / 재검증 필요 / 데이터 부족`으로 표시

### 1-5. BUY READY

v2.2.5의 기존 BUY READY 조건을 유지한다.

시장 Gate, 최신 완료장, 가격구조, 실행/관심가격, Invalidation, Target, R/R, 비추격, non-stale, LAB 비단독근거가 충분히 확인되지 않으면 BUY READY를 만들지 않는다.

### 1-6. Wiki

- 상세 Wiki가 Source of Truth
- 대표 페이지 `wiki/SIS-Wiki.md`
- 상세 Wiki → 대표 Wiki 순서
- 의미 있는 변화가 있을 때만 대표 Wiki Revision
- 날짜 붙은 대표 Wiki 복제본을 계속 만들지 않음

## 2. MLG 추가 — 기존 SIS 시장상태를 치환하지 않음

공통 MLG 의미는 다음 FROZEN Gate와 동일하게 사용한다.

`SIS_MARKET_LEADING_GATE_v1.3-FULL-SCAN-LINK-ERRC-FROZEN.md`

MLG는 v2.2.5의 기존 `SIS ON/WAIT/OFF` 또는 `SIS + LAB 교차판정`을 **대체하지 않는 별도 상위 위험축**이다.

### 불변 의미

- `MLG-RISK_ON`은 매입신호가 아니다.
- MLG는 BUY READY를 새로 만들지 않는다.
- `MLG-RISK_ON`으로 WAIT를 ON으로 올리지 않는다.
- `MLG-RISK_OFF`는 신규진입 강도를 보수적으로 낮출 수 있다.
- `MLG-STRESS`는 신규매입을 원칙적으로 금지하는 위험 제한으로 작동한다.
- `MLG-NA`이면 v2.2.5 분석은 계속하되 신규매입 신뢰도를 낮춘다.
- MLG와 시장 시계열 T1~T8은 별도 축이며 1:1 매핑하지 않는다.

### 출력

기존 시장 + LAB 표를 삭제하지 않고 그 앞 또는 옆에 다음을 추가한다.

- `MLG: MLG-RISK_ON / MLG-NEUTRAL / MLG-RISK_OFF / MLG-STRESS / MLG-NA`
- `시장 시계열: 단기 / 중기 / 장기 T1~T8`
- `MLG 자료상태: 확정 / 일부 잠정 / 제한`

## 3. STC14 / G240 추가 — Track 독립성 보존

공통 Scanner 계약:

`SIS_SCANNER_DIRECT_CALL_CONTRACT_v1.1-3MARKET-FRESHNESS-ERRC-FROZEN.md`

적용 Scanner:

- STC14 v1.7.0
- G240 v1.4.0

Scanner는 `DERIVED_TECHNICAL_EVIDENCE`다.

### STC14
- CROSS/MATCH = 저점권 반전 보조
- WATCH = 관찰
- EXIT_ZONE = 신규진입 신호 아님

### G240
- CROSS/MATCH = MA5/MA240 회복 보조
- BELOW_2W = Cross 대기
- 자체 매입신호 아님

### 2nd에서의 위치

Scanner는 GENERAL/CYCLE/LAB 탐색 결과를 만든 뒤, `PRICE / RR`을 확인한 다음 **ACT / BUY READY 직전의 기술 교차확인**으로만 사용한다.

Scanner는 절대:

- GENERAL 후보를 단독 생성/삭제
- CYCLE PHASE 변경
- CYCLE Clock 재설정
- LAB 후보 승격/폐기
- MARKET ON/WAIT/OFF 변경
- MLG 변경
- SIS 상태 변경
- PRICE/Invalidation/Target/RR 생성
- BUY READY 생성

을 하지 못한다.

`Scanner 미검출 = 중립`

`Scanner stale/부재 = 기술 스캐너: 자료 제한`

STC14+G240 동시 CROSS/MATCH는 `기술적 합치`로 표시할 수 있으나 기존 v2.2.5 조건을 통과하지 못하면 ACT/BUY READY를 상향하지 않는다.

## 4. Scanner Direct Call

분석 시작 직후 데이터 준비를 위해 필요 시 다음을 parameterless ensure 방식으로 호출한다.

- `https://k-bizpost.myds.me/stc14.php`
- `https://k-bizpost.myds.me/g240.php`

강제 규칙:

1. Background 전체 Scan 완료를 기다리지 않는다.
2. polling하지 않는다.
3. 호출 직후 현재 저장된 Snapshot으로 2nd 분석을 계속한다.
4. `sis_scanner_refresh.php`를 사용하지 않는다.
5. KR/US/JP freshness를 시장별 완료 거래일 기준으로 독립 검증한다.
6. Scanner 호출이 먼저 실행돼도 판단상 MLG가 상위다.

## 5. v2.2.6 확장 실행순서

v2.2.5의 기존 단계는 삭제하지 않는다.

`DATA / RISK`
→ `MLG / 시장 시계열 위험 Overlay`
→ `MARKET / SECTOR`
→ `GENERAL FIND + CYCLE TRACK + LAB TRACK`
→ `CROSS VALIDATION`
→ `STRUCTURE / PHASE / SIGNAL`
→ `SCENARIO`
→ `PRICE / RR`
→ `STC14 / G240 기술 보조확인`
→ `ACT`
→ `BUY READY`
→ `DETAIL MEMORY`
→ `REPRESENTATIVE WIKI SYNC`
→ `한 줄 결론`

MLG와 Scanner가 추가됐다는 이유로 GENERAL/CYCLE/LAB의 내부 정의나 순서를 다시 만들지 않는다.

## 6. CROSS VALIDATION 확장

기존 표를 유지하고 Scanner는 필요 시 별도 열로만 추가한다.

| 종목 | GENERAL | CYCLE | LAB | STC14/G240 | 통합판정 |
|---|---|---|---|---|---|

해석 우선순위:

1. 기존 v2.2.5 Track 결과
2. MLG 위험 제한
3. PRICE/RR 유효성
4. Scanner 기술 보조확인
5. ACT / BUY READY

Scanner는 Track 자체가 아니다.

## 7. BUY READY 추가 제한

기존 BUY READY 조건에 다음 위험 확인을 **추가**하되 기존 조건을 삭제하지 않는다.

- `MLG-STRESS`이면 신규 BUY READY 금지
- `MLG-RISK_OFF`이면 기존 조건을 더 엄격히 적용
- `MLG-RISK_ON`은 기존 미충족 조건을 면제하지 않음
- Scanner가 좋아도 기존 BUY READY 미충족이면 `NO`
- Scanner 자료 제한만으로 기존 유효후보를 탈락시키지 않음

## 8. 기본 출력 추가

기존 v2.2.5 출력 순서를 유지하면서 필요한 위치에 다음을 추가한다.

- MLG 상태
- 시장 시계열 T1~T8
- Scanner 기준일/자료상태
- 후보별 `STC14 / G240` 상태

기존 GENERAL/CYCLE/LAB/CROSS/BUY READY/Wiki/한 줄 결론 항목은 제거하지 않는다.

## 9. 타 지시문 혼동 금지

본 SIS 2nd는 다음과 동일한 지시문이 아니다.

- `chatgpt/INSTRUCTION_v4.7.2.md` 일반 종목 누적분석
- Volume Cycle 단독 FROZEN Prompt
- LAB 엔진 Prompt
- SIS 1st
- SIS last

필요한 자료나 보조근거를 참조할 수 있어도 v2.2.5의 2nd 역할을 다른 Prompt로 대체하지 않는다.

## 10. 승격 조건

1. v2.2.5 원문 무변경 확인
2. GENERAL/CYCLE/LAB 3-Track 회귀 PASS
3. CYCLE 6종목·상태코드 회귀 PASS
4. LAB SUPPORTING_ONLY 회귀 PASS
5. BUY READY 조건 회귀 PASS
6. Wiki Source-of-Truth/Revision Gate 회귀 PASS
7. MLG는 위험 제한만 수행 PASS
8. Scanner 비결정성 PASS
9. GitHub 보관 PASS

후에만 FROZEN으로 승격한다.
