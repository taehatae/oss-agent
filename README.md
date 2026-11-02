# week09 - 박스오피스 조회

## 무엇을 하는 코드인가

영화진흥위원회(KOBIS) 오픈 API로 특정 날짜의 일별 박스오피스를 조회합니다.

- `tools.py`: 1위 영화 제목(`get_boxoffice_rank_1`)과 영화별 일일 관객 수(`get_movie_audience`)를 알려주는 함수
- `main.py`: 위 함수를 호출해 결과를 출력하는 예제

## 설치

```bash
pip install -r requirements.txt
```

그리고 같은 폴더에 `secret.py`를 만들어 KOBIS API 키를 넣습니다. 이 파일은 `.gitignore`에 들어 있어 저장소에 올라가지 않습니다.

```python
API_KEY = "발급받은_키"
```

## 실행

```bash
cd week09
python main.py
```
