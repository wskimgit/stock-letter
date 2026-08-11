# LAB Data for ChatGPT

이 디렉터리는 `lab.php`가 GitHub에 자동 발행하는 **읽기 전용 LAB 데이터 전달 영역**이다.

- Canonical file: `LATEST.json`
- Producer: `lab.php`
- Consumer: ChatGPT 종목 분석
- LAB only: `true`
- Actual buy: `false`
- GitHub commit history: publication history

`LATEST.json`은 현재 시장세션·현재 active experiment_hash만의 후보, benchmark/시장폭/섹터, 종목별 기술 snapshot, LAB metrics를 포함한다.

ChatGPT는 `chatgpt/CURRENT.md → chatgpt/INSTRUCTION_v4.6-candidate.3.md → lab_data/LATEST.json` 순으로 확인한다.

GitHub token은 이 저장소에 저장하지 않는다. 서버의 `LAB_GITHUB_TOKEN` 환경변수에만 설정한다.
