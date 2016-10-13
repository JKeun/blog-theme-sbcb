+++
date = "2016-10-13T19:19:27+09:00"
title = "hello world"
image = "/img/about-bg.jpg"
description = "Python Data Analysis Environment Setting"
draft = false
tags = [
  "python",
  "data",
  "data science",
  "machine learning",
  "development",
]
categories = [
  "Macine learning",
  "Data Sciecne",
  "Development",
]

+++

# 데이터 분석 개발 환경 ( python v2.7.11 )

---
## pyenv, virtualenv, autoenv
### pyenv + virtualenv
`$ brew update`
`$ brew install pyenv`
`$ brew install pyenv-virtualenv`

`.bash_profile` & `.zshrc` 에 문구 추가
```
export PATH="$HOME/.pyenv/bin:$PATH"
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"
```
- pyenv
`$ pyenv version`
`$ pyenv install -list` : 설치할 수 있는 파이썬 리스트
`$ pyenv install [VERSION]`  : 설치
`$ pyenv shell [VERSION]` : 해당 버전 실행
`$ python -version` : 실행중인 파이썬 버전 확인

- virtualenv
`$ pyenv virtualenv [VERSION] [VIRTUALENV_NAME]` : 생성
`$ virtualenv versions` : 해당 버전 확인
`$ pyenv activate [VIRTUALENV_NAME]` : 해당 버전 실행
`$ pyenv deactivate` : 실행중인 버전 종료

- requirements.txt
`$ pip freeze > requirements.txt` : 
`$ pip list > requirements.txt`
`other-user$ pip install -r requirements.txt` : 다른 사용자가 설치할 경우

- autoenv
`$ brew install autoenv`
-  .bash_profile(.zshrc) 에 추가하기
`$ source ~/.autoenv/activate.sh`
or .bash_profile , .zshrc 에 각각 아래를 추가 
`$source ~/.commonrc`
`$ vi ~/.commonrc` 만든 후
`source ~/.autoenv/activate.sh`

- autoenv 실행하기
프로젝트 폴더에 `$ vi .env` 생성 후



---
### pip install [module]
`$ pip install numpy`
...
statsmodels 은 dev 버전 설치

---
## ./ipython/
- 파이썬 전체에 대한 적용
- pyenv는 pip install [module] 이 독립적이나, 아래의 것들은 pyenv 상관없이, python 을 쓰는 환경에는 모두 적용


---
### 00.py
- ~/.ipython/profile_default/startup/00.py
```
# from __future__ import division
from __future__ import print_function

import numpy as np
import scipy as sp
import pandas as pd
import statsmodels.api as sm
import statsmodels.formula.api as smf
import statsmodels.stats.api as sms
import sklearn as sk
import matplotlib as mpl
import matplotlib.pylab as plt
from mpl_toolkits.mplot3d import Axes3D
import seaborn as sns

sns.set()
sns.set_color_codes()
```

---
### ipython_config.py
- ~/.ipython/profile_default
```
c = get_config()

c.InteractiveShellApp.exec_lines = [
	'from __future__ import division'
	# 'from __future__ import print_function
'
]
```

---
### ipython_kernerl_config.py
```
c = get_config()
c.InteractiveShellApp.matplotlib = 'inline'
c.InlineBackend.figure_format = 'svg'
```
