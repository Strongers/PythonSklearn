## sklearn.model_selection.ParameterSampler

### by Stronger

## class sklearn.model_selection.ParameterSampler(param_distributions, n_iter, random_state=None)
- 用于从指定分布中随机抽样生成指定数量的参数。用于超参选择，当给定为一系列数字时，将对数字进行无放回抽样；当给定为分布时，将进行有放回抽样。<br>

## parameters
- param_distributions : dict <br>
  - 指定参数分布：其中keywei参数值，value为给定参数的分布<br>
  - 参数分布需要有rvs方法，用于对其进行抽样<br>
- n_iter : integer <br>
  -指定参数的数量<br>
- random_state : int or RandomState <br>
  - 伪随机数生成器用于抽样<br>

## return
- params : dict of string to any<br>

## example
```
from sklearn.model_selection import ParameterSampler
from scipy.stats.distributions import expon
import numpy as np
np.random.seed(0)
param_grid = {'a':[1, 2], 'b': expon()}
param_list = list(ParameterSampler(param_grid, n_iter=4))
rounded_list = [dict((k, round(v, 6)) for (k, v) in d.items()) for d in param_list]
rounded_list == [{'b': 0.89856, 'a': 1},
...                  {'b': 0.923223, 'a': 1},
...                  {'b': 1.878964, 'a': 2},
...                  {'b': 1.038159, 'a': 2}]
return True
```
