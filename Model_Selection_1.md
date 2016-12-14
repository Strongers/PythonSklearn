#### Hyper-parameter optimizers 超参优化  
### sklearn.model_selection.GridSearchCV  
- 用于参数调优,使用CV(交叉验证)方法<br>
- class sklearn.model_selection.GridSearchCV(estimator, param_grid, scoring=None, fit_params=None, n_jobs=1, iid=True, refit=True, cv=None, verbose=0, pre_dispatch='2*n_jobs', error_score='raise', return_train_score=True) <br>

## 参数
- estimator:estimator object<br>
  - 分类器对象<br>
- param_grid:dict or list of dictionaries<br>
  - 参数网格,也就是要调优参数的候选值<br>
- scoring : string, callable or None, default=None<br>
  - 得分,当为空时，自动调用extimator的scoring方法<br>
- fit_params : dict, optional<br>
  - 向fit方法传递的参数<br>
- n_jobs:int, default=1<br>
  - 并行的数量<br>
- pre_dispatch : int, or string, optional<br>
  - 控制并行运算过程中内存的消耗<br>
- iid : boolean, default=True  <br>
  - 参数为TRUE时，假设数据在各份内相同地分布；最小化损失函数，最小化的是所有份的损失函数的和，并不是平均数<br>
- cv : int, cross-validation generator or an iterable, optional<br>
  - 参数为空时，默认3折交叉验证；为integer对象k时，为k折交叉验证；为交叉验证生成器对象时<br>
- refit : boolean, default=True<br>
  - 是否用整个数据集训练，当参数为False时，只用交叉验证的数据训练<br>
- verbose : integer<br>
  - 显示模型情况多少，数字越大越多<br>
- error_score : ‘raise’ (default) or numeric<br>
  - 如果在估计量拟合中出现错误，则分配给分数的值。 如果设置为'raise'，则会报错。 如果给出了数值，则引发FitFailedWarning。 此参数不影响refit步骤，这将始终引发错误<br>
- return_train_score : boolean, default=True<br>
  - 参数为False时，cv_results_将不包括训练的分数<br>
  
## 特性
- cv_results_ : dict of numpy (masked) ndarrays<br>
  - A dict with keys as column headers and values as columns<br>
- best_estimator_ : estimator<br>
  - 返回调优结果<br>
- best_score_ : float<br>
  - 返回最优模型的分数<br>
- best_index_ : int<br>
  - 返回最优参数，在params中的索引<br>
- scorer_:function<br>
  - 返回scoring方法<br>
- n_splits_ : int<br>
  - 返回k折交叉检验的K<br>
  
## 方法
- decision_function(\*args, \*\*kwargs)  
  - Call decision_function on the estimator with the best found parameters<br>
- fit(X[, y, groups])  
  - 运行调优程序，寻找最优参数  
- get_params([deep])  
  - 获取最优参数  
- inverse_transform(\*args, \*\*kwargs)  
  - 以下没有说明的都是调用estimator的相应方法  
- predict(\*args, \*\*kwargs)
- predict_log_proba(\*args, \*\*kwargs)  
- predict_proba(\*args, \*\*kwargs)  
- transform(\*args, \*\*kwargs)
- score(X[, y])  
  - 返回给定数据的分数  
- set_params(\*\*params)  
  - 设置参数  
