#### ParameterGrid 参数网格  

### by Stronger

### sklearn.model_selection.ParameterGrid
- 给定一系列参数的值，将候选参数用于迭代<br>

## parameters 
- param_grid : dict of string to sequence, or sequence of such<br>
  - 参数序列 <br>

## code example

```
from sklearn.model_selection import ParameterGrid
param_grid = {'a': [1, 2], 'b': [True, False]}
list(ParameterGrid(param_grid)) == ([{'a': 1, 'b': True}, {'a': 1, 'b': False},{'a': 2, 'b': True}, {'a': 2, 'b': False}])
## return True
```


