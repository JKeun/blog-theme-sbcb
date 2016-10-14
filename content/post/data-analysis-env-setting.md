+++
categories = [
  "Data Science"
]
date = "2016-10-14T10:11:07+09:00"
title = "Data Analysis Environment Setting"
image = "/img/about-bg.jpg"
description = "00.py, ipython_config.py, ipython_kernerl_config.py"
draft = true
tags = [
  "data",
  "data science",
  "jupyter notebook",
  "ipython",
  "dev"
]

+++

**pip install [module]**
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
