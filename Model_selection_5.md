#### sklearn.model_selection.fit_grid_point

### by Stronger

## sklearn.model_selection.fit_grid_point(X, y, estimator, parameters, train, test, scorer, verbose, error_score='raise', **fit_params)
- 对一组参数运行拟合<br>

## parameters
- X : array-like, sparse matrix or list <br>
  - 输入数据<br>
- y : array-like or None<br>
  - 输入数据的目标<br>
- estimator : estimator object<br>
  - 估计器：将把每个候选参数值带入其中；estimator必须具有score方法用于计算得分<br>
- parameters : dict<br>
  - 获选参数<br>
- train : ndarray, dtype int or bool<br>
  - 训练集的Boolean掩码或索引<br>
- test : ndarray, dtype int or bool<br>
  - 测试集的Boolean掩码或索引<br>
- scorer : callable or None<br>
- verbose : int<br>
  - 返回值的详细程度<br>
- **fit_params : kwargs<br>
  - 传递给fit方法或estimator的额外参数<br>
- error_score : ‘raise’ (default) or numeric<br>

## return
- score : float <br>
  - 该参数在给定测试、训练集下，模型的分数<br>
- parameters : dict <br>
  - 测试过的参数<br>
- n_samples_test : int<br>
  - 划分的训练集的数量<br>
