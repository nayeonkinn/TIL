# Python Chatbot Practice



### 실습 준비

1. 텔레그램 다운로드
2. 크롬 텔레그램 확장 프로그램 설치
   - https://chrome.google.com/webstore/detail/telegram-for-chrome/djjkifoefibfoodilnhkmbhmadbgacni?hl=ko

3. 텔레그램에서 '파이썬 챗봇' 검색하여 가입 및 인증
4. 필요 라이브러리 설치
   - pip install requests
   - pip install beautifulsoup4
   - pip install lxml



### 실습 : 안녕봇

```python
import requests

# 요청 보낼 url
url = 'http://api.agify.io/?name=nayeon'

# url로 요청을 보내는 방법
# requests.get('url')

response = requests.get(url).json() # json 형태로 달라
# print(response)

name = response.get('name')
age = response.get('age')
print(f'안녕하세요 {name}님({age}), 환영합니다.')
```



### 실습 : 로또 번호

```python
import requests

url = 'https://www.dhlottery.co.kr/common.do?method=getLottoNumber&drwNo=1021'

response = requests.get(url).json()
# print(response)
print(response.get('drwtNo1'))
print(response.get('drwtNo2'))
print(response.get('drwtNo3'))
print(response.get('drwtNo4'))
print(response.get('drwtNo5'))
print(response.get('drwtNo6'))
print(response.get('bnusNo'))
```



### Tip
- VS Code 유용한 단축키
  - alt + shift + 방향키 : 원하는 방향으로 해당 줄 복제
  - 가로 스크롤 : shift + 스크롤