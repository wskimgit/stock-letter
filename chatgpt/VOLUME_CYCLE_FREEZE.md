# 거래량 순환매 지시문 동결 기록

## 현재 동결 기준

- frozen_instruction: `VOLUME_CYCLE_INSTRUCTION_v2.0.0.md`
- frozen_operational_status: `FROZEN`
- freeze_timestamp: `2026-08-11T13:49+09:00`
- repository: `wskimgit/stock-letter`
- branch: `main`
- frozen_blob_sha: `eefa43d535af5d338efc6e9f5e4b28a0eafaa724`
- wiki_schema: `VOLUME_CYCLE_WIKI_V2`
- wiki_file: `../거래량-순환매-Wiki.md`

## 직전 동결 기준

- previous_frozen_instruction: `VOLUME_CYCLE_INSTRUCTION_v1.2.0.md`
- previous_status: `FROZEN_HISTORY`
- previous_blob_sha: `687d70bb5db6fce33c70d94db7cc0bc496f9a547`
- 처리: 파일은 수정·삭제하지 않고 이전 기준본으로 보존한다.

## 감시종목 변경

### 신규 기본 유니버스
- KR: 빅텍 `065450`, 퍼스텍 `010820`, 한일단조 `024740`
- US: RCAT, KTOS, DPRO

### 기본 유니버스 제외
- 스페코 `013810`: 평시 기본 유동성 부족
- UAVS: 저유동성·희석·갭 위험 과다

## 버전 이력

- `v1.0.0` = RELEASED_HISTORY
- `v1.1.0` = HISTORY
- `v1.2.0` = FROZEN_HISTORY
- `v2.0.0` = **현재 FROZEN 운영 기준본**

## 동결 원칙

1. 현재 운영 기준은 `VOLUME_CYCLE_INSTRUCTION_v2.0.0.md`이다.
2. v2.0.0의 동결 무결성 기준 SHA는 `eefa43d535af5d338efc6e9f5e4b28a0eafaa724`이다.
3. v2.0.0 파일은 직접 수정·덮어쓰기하지 않는다.
4. 이후 변경은 반드시 새 버전 파일로 생성한다.
5. 재질의 시 GitHub를 먼저 읽고 최신 시장데이터와 비교한다.
6. Wiki의 Current View, Intraday View, Revision Timeline은 계속 갱신할 수 있다.
7. 유동성 게이트를 거래량 고갈 신호보다 먼저 적용한다.

운영선:
`v1.0.0 RELEASED_HISTORY → v1.1.0 HISTORY → v1.2.0 FROZEN_HISTORY → v2.0.0 FROZEN`
