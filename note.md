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

.travis.yml 파일생성

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