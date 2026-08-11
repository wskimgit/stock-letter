# 거래량 순환매 지시문 동결 기록

## 현재 동결 기준

- frozen_instruction: `VOLUME_CYCLE_INSTRUCTION_v2.1.0.md`
- frozen_operational_status: `FROZEN`
- freeze_timestamp: `2026-08-11T14:02+09:00`
- repository: `wskimgit/stock-letter`
- branch: `main`
- frozen_blob_sha: `99986e11d0b2a5aa6f98a1ba3787c63508febd4d`
- wiki_schema: `VOLUME_CYCLE_WIKI_V2`
- wiki_file: `../거래량-순환매-Wiki.md`

## 직전 동결 기준

- previous_frozen_instruction: `VOLUME_CYCLE_INSTRUCTION_v2.0.0.md`
- previous_status: `FROZEN_HISTORY`
- previous_blob_sha: `eefa43d535af5d338efc6e9f5e4b28a0eafaa724`
- 처리: 파일은 수정·삭제하지 않고 이전 기준본으로 보존한다.

## 현재 기본 유니버스

- KR: 빅텍 `065450`, 퍼스텍 `010820`, 한일단조 `024740`
- US: RCAT, KTOS, DPRO

기본 제외:
- 스페코 `013810`: 평시 기본 유동성 부족
- UAVS: 저유동성·희석·갭 위험 과다

## v2.1.0 핵심 변경

- 직전 주요 S2/S3 이벤트 고점일 기록
- 직전 주요고점부터 현재까지 달력일·거래일 경과 계산
- 과거 주요고점 간격의 평균·중앙값·범위 및 표본수 관리
- 표본 5개 이상이면 Q1~Q3를 우선 사용
- 경과일은 단독 매수/매도 신호가 아니라 M1/M2·유동성·기업위험과 결합하는 타이밍 보정요소
- 새 주요고점이 확정되면 경과일을 0으로 리셋

## 버전 이력

- `v1.0.0` = RELEASED_HISTORY
- `v1.1.0` = HISTORY
- `v1.2.0` = FROZEN_HISTORY
- `v2.0.0` = FROZEN_HISTORY
- `v2.1.0` = **현재 FROZEN 운영 기준본**

## 동결 원칙

1. 현재 운영 기준은 `VOLUME_CYCLE_INSTRUCTION_v2.1.0.md`이다.
2. v2.1.0의 동결 무결성 기준 SHA는 `99986e11d0b2a5aa6f98a1ba3787c63508febd4d`이다.
3. v2.1.0 파일은 직접 수정·덮어쓰기하지 않는다.
4. 이후 변경은 반드시 새 버전 파일로 생성한다.
5. 재질의 시 GitHub를 먼저 읽고 최신 시장데이터와 비교한다.
6. Wiki의 Current View, Intraday View, Revision Timeline은 계속 갱신할 수 있다.
7. 유동성·기업위험 게이트를 경과일보다 먼저 적용한다.
8. 경과일 통계의 표본이 부족하면 `자료상태=제한/부족`을 명시하고 주기성을 확정하지 않는다.

운영선:
`v1.0.0 RELEASED_HISTORY → v1.1.0 HISTORY → v1.2.0 FROZEN_HISTORY → v2.0.0 FROZEN_HISTORY → v2.1.0 FROZEN`
