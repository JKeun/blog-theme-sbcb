+++
date = "2016-10-13T19:19:27+09:00"
title = "Python Development Environment Setting"
image = "/img/about-bg.jpg"
description = "Pyenv, Virtualenv, Autoenv"
draft = false
tags = [
  "python",
  "dev", "development",
  "pyenv",
  "virtualenv",
  "autoenv"
]
categories = [
  "Development",
]

+++

# 데이터 분석 개발 환경 ( python v2.7.11 )
파이썬 개발환경 및 패키지 관리 자동화를 위한 세팅

---
## pyenv + virtualenv

pyenv 는 파이썬 2.7, 3.11 을 자유롭게 오가며 사용할 수 있게 해준다.


**brew upate, install pyenv, virtualenv**

- `$ brew update`
- `$ brew install pyenv`
- `$ brew install pyenv-virtualenv`

 
**.bash_profile & .zshrc 에 문구 추가**
```
export PATH="$HOME/.pyenv/bin:$PATH"
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"
``` 
   
**pyenv 사용법**

- `$ pyenv version`
- `$ pyenv install -list` : 설치할 수 있는 파이썬 리스트
- `$ pyenv install [VERSION]`  : 설치
- `$ pyenv shell [VERSION]` : 해당 버전 실행
- `$ python -version` : 실행중인 파이썬 버전 확인


**virtualenv 사용법**

- `$ pyenv virtualenv [VERSION] [VIRTUALENV_NAME]` : 생성
- `$ virtualenv versions` : 해당 버전 확인
- `$ pyenv activate [VIRTUALENV_NAME]` : 해당 버전 실행
- `$ pyenv deactivate` : 실행중인 버전 종료

**requirements.txt**

- `$ pip freeze > requirements.txt` 
- `$ pip list > requirements.txt`
- `$ pip install -r requirements.txt` : 다른 사용자가 설치할 경우

**autoenv 설치 및 세팅**

- `$ brew install autoenv`
- .bash_profile(or .zshrc) 에 추가하기
- `$ source ~/.autoenv/activate.sh`
    - 또는 .bash_profile , .zshrc 에 `$source ~/.commonrc` 를 추가 후
    - `$ vi ~/.commonrc` 를 만든 후
    - .commonrc에 `source ~/.autoenv/activate.sh`를 추가


**autoenv 실행하기**

- 해당 프로젝트 폴더에 `$ vi .env` 생성 후 아래를 추가

```
echo "Activating pyenv for [PROJECT_NAME] Python v.3.5.1"
pyenv activate [PROJECT_NAME]
```

- 이후 해당 폴더에 들어올 때마다 파이썬환경 자동으로 켜짐
- `$pyenv deactivate` : 해당 파이썬 환경 종료
