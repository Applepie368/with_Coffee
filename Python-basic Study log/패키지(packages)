# 2026.03.04 (수)

💿 패키지를 만들어보자

디렉터리와 파이썬을 한 번에 쓸 수 있는 그런 집합체라고 이해했다.

뭐 쉽게 말해서 우리 컴퓨터 파일 안에 파일 있고, 문서도 있고 한데, 하나의 프로젝트를 만들 때 관련있는 파일을 만들고 분류한 것이라고 생각하면 편하다

이번에 배우면서 느낀게, python interpreter 말고 명령 프롬프트나 terminal에서 쓰는 명령어가 윈도우랑 달라서 좀 배울 때 헷갈린다는것이다

그리고 수학처럼 순차적으로 배우기는 솔직히 힘들기 때문에 앞에 뭔가 새로운 것도 계속 나오고 그때마다 찾아보고 흠... 솔직히 재미랑 별개로 좀 중구난방한 것 같다

예를들어 이러한 패키지가 있다고 해보자

game/
  __init__.py
  sound/
    __init__.py
    echo.py
  graphic/
    __init__.py
    render.py

요게 패키지다, 각 폴더에 파일이 있는거

흠, 이거 어떻게 오늘 배운걸 정리할지 모르겠는데, 패키지 안의 함수를 실행하는 여러 방법이 있었다

1번 echo 모듈 import 하는법
```python
  import game.sound.echo
  game.sound.echo.echo_test()
```
echo라는 모듈에 echo_test)라는 함수가 있는데 이걸 가져오는거다

2번 echo 모듈이 있는 디렉터리까지 from ~ import ... 하는거
```python
  from game.sound.import echo
  echo.echo_test()
```

3번 echo 모듈의 echo_test 함수를 직접 import 하여 실행하는 방법
```python
  from game.sound.echo import echo_test
  echo_test()
```



