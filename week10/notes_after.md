작성: Claude Code / 확인: (황태하)

# week09 tools.py 함수 정리

- `week09/tools.py`는 영화진흥위원회(KOBIS) 오픈 API에서 **일별 박스오피스** 정보를 가져오는 도구 모음임
- 함수는 총 2개임: `get_boxoffice_rank_1`, `get_movie_audience`

## 공통 사항

- API 키는 `secret.py`의 `API_KEY`를 가져와 씀
- 요청 주소(`BASE_URL`)는 `searchDailyBoxOfficeList.json`(일별 박스오피스 목록)임
- 요청 파라미터는 `key`(API 키), `targetDt`(조회 날짜, 8자리 `YYYYMMDD`)임
- `requests.get(..., timeout=10)`으로 호출함
- 응답 JSON의 `boxOfficeResult` → `dailyBoxOfficeList`에서 영화 목록을 꺼냄

## 함수 목록

### 1. `get_boxoffice_rank_1(date)`

- 역할: 그 날짜의 박스오피스 **1위 영화 제목**을 알려줌
- 받는 것: `date`(문자열) — 8자리 날짜임. 예: `"20260824"`
- 돌려주는 것: 1위 영화 제목(문자열)임. 예: `"오디세이"`
- 동작: 영화 목록의 첫 번째 항목(`movies[0]`)의 `movieNm`을 돌려줌

### 2. `get_movie_audience(date, title)`

- 역할: 그 날짜 순위에서 영화를 찾아 **일일 관객 수**를 알려줌
- 받는 것:
  - `date`(문자열) — 8자리 날짜임. 예: `"20260824"`
  - `title`(문자열) — 영화 제목임. 예: `"오디세이"`
- 돌려주는 것: 관객 수(문자열)임. 예: `"186,587명"`
- 동작:
  - 영화 목록을 하나씩 돌며 `movieNm`이 `title`과 정확히 같은 영화를 찾음
  - `audiCnt`를 정수로 바꾼 뒤 천 단위 쉼표와 "명"을 붙여 돌려줌
  - 순위에 없으면 `"'제목' 은(는) 날짜 순위에 없습니다."` 문장을 돌려줌

## 참고할 점

- 두 함수에 같은 API 호출 코드가 반복됨
- 오류 처리가 없음: 네트워크 오류, 잘못된 날짜, 빈 목록(`movies[0]`의 `IndexError`) 등은 그대로 예외가 남
- `get_movie_audience`는 제목이 띄어쓰기까지 정확히 같아야 찾음
