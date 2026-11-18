# boxoffice — KOBIS 박스오피스 조회 스킬

## 하는 일
- 날짜(8자리)를 주고 박스오피스 1위를 물으면 그날 1위 영화 제목을 알려 줌
- 날짜와 영화 제목을 주고 관객 수를 물으면 그날 그 영화의 관객 수를 알려 줌

## 들어 있는 파일
- .claude/skills/boxoffice/SKILL.md
- .claude/skills/boxoffice/scripts/boxoffice.py
- .claude/skills/boxoffice/LICENSE

## 필요한 것
- 프로젝트 폴더(명령을 실행하는 곳)에 tools.py 와 secret.py 가 있어야 함
- tools.py 는 이 저장소의 week12/tools.py 를 복사해 씀
- boxoffice.py 는 실행한 폴더의 tools.py 를 불러 씀
- Python 과 requests 패키지 (pip install requests)

## 설치
- boxoffice 폴더를 프로젝트 폴더의 .claude/skills/ 안에 둠
- Claude Code 를 그 프로젝트 폴더에서 실행하고 /reload-skills (또는 다시 시작)
- /skills 목록에 boxoffice 가 나오면 설치된 것임

## 바깥으로 요청하는 곳
- https://www.kobis.or.kr/kobisopenapi/webservice/rest/boxoffice/searchDailyBoxOfficeList.json
- 보내는 것: API 키(key)와 날짜(targetDt)뿐임

## 키
- 프로젝트 폴더의 secret.py 에 API_KEY = "발급받은 키" 로 둠
- KOBIS 오픈API 사이트에서 각자 발급받아야 함
- secret.py 는 .gitignore 에 들어 있어서 이 저장소에는 키가 없음

## 권한
- SKILL.md 에 allowed-tools 가 없음
- 그래서 스크립트(python ... boxoffice.py)를 실행할 때마다 명령 실행 허용 여부를 물어봄

## 라이선스
- MIT License
- 파일 위치: .claude/skills/boxoffice/LICENSE.txt