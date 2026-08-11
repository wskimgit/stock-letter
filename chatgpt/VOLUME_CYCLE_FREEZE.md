# 거래량 순환매 지시문 동결 기록

- frozen_instruction: `VOLUME_CYCLE_INSTRUCTION_v1.0.0.md`
- frozen_operational_status: `FROZEN_BASELINE`
- freeze_date: `2026-08-11`
- repository: `wskimgit/stock-letter`
- branch: `main`
- frozen_blob_sha: `7510654f7447fdfdcacc703fe8cf6b49f3f6c59d`
- active_successor: `VOLUME_CYCLE_INSTRUCTION_v1.1.0.md`
- active_successor_status: `ACTIVE`
- active_successor_blob_sha: `711e269566aa37a8acc0da0a3c2724d92b89c422`
- active_successor_from: `2026-08-11`
- wiki_schema: `VOLUME_CYCLE_WIKI_V1`
- wiki_file: `../거래량-순환매-Wiki.md`

## 동결 원칙

1. `VOLUME_CYCLE_INSTRUCTION_v1.0.0.md`의 내용은 더 이상 수정하지 않는다.
2. 해당 파일 내부의 `상태: ACTIVE` 문구는 **동결 당시 원본 스냅샷의 일부**로 보존하며, 기준본 상태는 본 파일과 `CURRENT.md`의 `FROZEN_BASELINE` 판정을 우선한다.
3. 이후 오류 수정·규칙 추가·전략 변경은 반드시 새 버전 파일로 생성한다.
4. 새 버전은 사용자 명시 승인 전 `CANDIDATE` 또는 `DRAFT`로 관리하며, 동결된 v1.0.0을 자동 대체하지 않는다.
5. 사용자의 2026-08-11 명시 지시에 따라 `VOLUME_CYCLE_INSTRUCTION_v1.1.0.md`를 MINOR 후속 버전으로 생성하고 ACTIVE 운영 지시문으로 승격하였다.
6. v1.1.0의 활성화는 v1.0.0 동결 해제를 의미하지 않는다. v1.0.0은 변경 전 기준본·감사 기준으로 영구 보존한다.
7. 재질의 시 GitHub 선확인 순서는 `CURRENT.md → INDEX.md → RULES.md → VOLUME_CYCLE_FREEZE.md → 최신 ACTIVE 지시문 → 거래량-순환매-Wiki.md`로 한다.
8. v1.0.0 동결 무결성 검증 시 현재 blob SHA를 `7510654f7447fdfdcacc703fe8cf6b49f3f6c59d`와 비교한다. 다르면 원본 훼손 가능성으로 보고 동결 기준본으로 사용하지 않는다.
9. `거래량-순환매-Wiki.md`의 Current View와 Revision Timeline은 시장 상태 변화에 따라 계속 갱신할 수 있다. **동결 대상은 v1.0.0 기준본문이지, 시장 상태 Wiki 자체가 아니다.**

## 변경 정책

- PATCH 필요 → 새 PATCH 버전 파일 생성
- MINOR 필요 → 새 MINOR 버전 파일 생성
- MAJOR 필요 → 새 MAJOR 버전 파일 생성

현재 운영선:

`v1.0.0 FROZEN BASELINE → v1.1.0 ACTIVE`

기존 `VOLUME_CYCLE_INSTRUCTION_v1.0.0.md`는 어떤 경우에도 덮어쓰지 않는다.
