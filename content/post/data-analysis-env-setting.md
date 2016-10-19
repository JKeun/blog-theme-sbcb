+++
categories = [
  "Data Science"
]
date = "2016-10-14T10:11:07+09:00"
title = "Data Analysis Environment Setting"
image = "/img/about-bg.jpg"
description = "pip install, 00.py, ipython_config.py, ipython_kernel_config.py"
draft = true
tags = [
  "data",
  "data science",
  "jupyter notebook",
  "ipython",
  "dev"
]

+++
# 데이터 분석을 위한 초기 환경 세팅
- 기본적인 패키지 설치와 ipython(jupyter) 개발 환경에서 자주 사용하는 패키지 import 자동화를 다룬다.
- python 2 에서도 print 함수, division 함수를 python 3 버전처럼 사용할 수 있도록 한다. 
- matplotlib 의 그래프 inline 출력 자동화를 다룬다.

---
## pip install [module]
- 데이터 분석에 필요한 기본 패키지 설치

```
$ pip install numpy
$ pip install pandas
$ pip install sklearn
$ pip install matplotlib
$ pip install seaborn
```

- statsmodels 은 `pip install statsmodel` 이 아닌 dev 버전 설치
    - statsmodels 설치를 위해 patsy 패키지 설치
    - 

---
## ~/.ipython/ 세팅하기
- ipython 전체에 대한 적용
- pyenv는 pip install [module] 이 개별 분석 환경에 독립적으로 설치하는 것인 반면, `~/.ipython/` 폴더의 설정은 모든 python 분석 환경에 적용


### 00.py
- 모듈 자동 import
- startup 폴더에 00.py 파일을 만듦으로써 ipython 이 시작할때, 가장 먼저 이 파일이 실행되도록 한다.
- `$ vi ~/.ipython/profile_default/startup/00.py`

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

### ipython_config.py
- ipython 의 기본설정 파일
- division 문의 경우 **00.py** 에서 불러올 땐 작동하지 않고, **ipython_config.py** 에서 작동함
- print 문의 경우 **00.py**, **ipython_config.py** 둘다 작동 잘 됨
    - 따라서 ipython_config.py 에는 division 문을 추가한다
- `$ vi ~/.ipython/profile_default/ipython_config.py`

```
c = get_config()

c.InteractiveShellApp.exec_lines = [
	'from __future__ import division'
	# 'from __future__ import print_function'
]
```


### ipython_kernel_config.py
- ipython kernel 설정 
- 그래프를 그리는 작업을 할 때 inline 으로 출력
- `$ vi ~/.ipython/profile_defalult/ipython_kernel_config.py`

```
c = get_config()
c.InteractiveShellApp.matplotlib = 'inline'
c.InlineBackend.figure_format = 'svg'
```


