## 유닛 테스트

### 테스트 단계

1. Setup -> Create sample database objects
2. Execution -> Call the code
3. Assertions -> Confirm expected output

### 왜 테스트 코드를 작성하는가?

- Expected in most professional dev teams
- Make it easier to change code
- Save time!
- Testable, better quality code

## TDD란 무엇일까?

- 전통적인 방법: Implement feature -> write code
- TDD: Write code -> Implement feature

### TDD의 이점은 무엇일까?

- 테스트 커버리지를 향상
- 실제로 동작을 보장
- 코드의 질을 향상

## Dockerfile

### 환경변수 PYTHONUNBUFFERED

파이썬에서 나오는 출력 버퍼를 기본으로 작동하면서 출력 로그를 붙잡고 있는데 이 버퍼링을 없애준다.

```Dockerfile
ENV PYTHONUNBUFFRED 1
```

### USER

명령을 실행할 사용자 계정을 설정한다. RUN, CMD, ENTRYPOINT에 적용된다.

## Travis CI

지속적 통합 툴로 깃헙으로 push할때 자동으로 테스트들과 프로젝트를 체킹해준다.

### 설정 방법

1. .travis.yml 파일생성
2.

```yml
#언어 설정
language: python
python:
  #파이썬 버전 설정
  - "3.6"

services:
  #서비스 설정
  - docker

# 기본적인 패키지를 설치
before_script: pip install docker-compose

script:
  #실제 스크립팅하는 부분, sh -c 는 쉘 스크립팅한다는 뜻임
  - docker-compose run app sh -c "python manage.py test && flake8"
```

## Flake8

linting tool

### .flake8

exclude 해준 파일 또는 폴더는 Flake8 linting에서 제외된다.

```yml
[flake8]
exclude =
  migrations,
  __pycache__,
  manage.py,
  settings.py

```

## unit test

1. 애플리케이션 안에 tests.py 생성
2.

```python
from django.test import TestCase
# 테스트하고 싶은 함수 import
from app.calc import add


class CalcTest(TestCase):
    # 테스트 함수 이름은 무조건 test로 시작해야 함
    def test_add_numbers(self):
        """ Test that two number are added together """
        self.assertEqual(add(3, 8), 11)
```

## TDD

- 먼저 유닛테스트시 테스트의 결과를 먼저 정의 후에 코드를 짠다.

### 장점

1. "테스트할 수 있는 코드를 작성해야한다"라고 생각하기 때문에 코드에 대한 생각을 개선하는데에 도움이 많이 된다.
2. 일반적으로 테스트하기 쉬운 코드는 유지 관리가 쉽고 테스트에 대해 미리 생각하지 않고 작성되는 코드보다 품질이 좋다.
