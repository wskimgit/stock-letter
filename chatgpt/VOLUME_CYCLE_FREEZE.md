# 거래량 순환매 지시문 동결 기록

- frozen_instruction: `VOLUME_CYCLE_INSTRUCTION_v1.0.0.md`
- operational_status: `FROZEN`
- freeze_date: `2026-08-11`
- repository: `wskimgit/stock-letter`
- branch: `main`
- frozen_blob_sha: `7510654f7447fdfdcacc703fe8cf6b49f3f6c59d`
- wiki_schema: `VOLUME_CYCLE_WIKI_V1`
- wiki_file: `../거래량-순환매-Wiki.md`

## 동결 원칙

1. `VOLUME_CYCLE_INSTRUCTION_v1.0.0.md`의 내용은 더 이상 수정하지 않는다.
2. 해당 파일 내부의 `상태: ACTIVE` 문구는 **동결 당시 원본 스냅샷의 일부**로 보존하며, 운영상 상태는 본 파일과 `CURRENT.md`의 `FROZEN` 판정을 우선한다.
3. 이후 오류 수정·규칙 추가·전략 변경은 반드시 새 버전 파일로 생성한다.
4. 새 버전은 사용자 명시 승인 전 `CANDIDATE` 또는 `DRAFT`로 관리하며, 동결된 v1.0.0을 자동 대체하지 않는다.
5. 새 버전을 운영 기준으로 승격하려면 사용자의 명시적 승인과 `CURRENT.md` 포인터 변경이 필요하다.
6. 재질의 시 GitHub 선확인 순서는 `CURRENT.md → INDEX.md → RULES.md → VOLUME_CYCLE_FREEZE.md → 동결 지시문 → 거래량-순환매-Wiki.md`로 한다.
7. 동결 무결성 검증 시 현재 blob SHA를 `7510654f7447fdfdcacc703fe8cf6b49f3f6c59d`와 비교한다. 다르면 원본 훼손 가능성으로 보고 동결 기준본으로 사용하지 않는다.
8. `거래량-순환매-Wiki.md`의 Current View와 Revision Timeline은 시장 상태 변화에 따라 계속 갱신할 수 있다. **동결 대상은 지시문 v1.0.0의 규칙 본문이지, 시장 상태 Wiki 자체가 아니다.**

## 변경 정책

- PATCH 필요 → `VOLUME_CYCLE_INSTRUCTION_v1.0.1.md` 신규 생성
- MINOR 필요 → `VOLUME_CYCLE_INSTRUCTION_v1.1.0.md` 신규 생성
- MAJOR 필요 → `VOLUME_CYCLE_INSTRUCTION_v2.0.0.md` 신규 생성

기존 `VOLUME_CYCLE_INSTRUCTION_v1.0.0.md`는 어떤 경우에도 덮어쓰지 않는다.
