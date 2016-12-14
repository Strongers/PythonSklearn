#### Hyper-parameter optimizers 超参优化 <br>
### sklearn.model_selection.RandomizedSearchCV <br>
- 与GridSearchCV区别在于：不是从固定的集合内选取参数，而是从给定的分布中选取一定数量的值作为测试对象，n_iter指定测试对象数量<br>
- 当给定一个集合作为备选对象时，将对该集合做**无放回**抽样；当给定分布时，将对集合做**有放回**抽样<br>
- 建议为连续型参数指定连续型分布<br>

## parameters <br>
- estimator : estimator object<br>
  - 估计器对象<br>
- param_distributions<br>
  - 参数分布，字典类型，变量名称作为key+给定的备选集合或分布。注意：分布必须提供rvs方法用于抽样,当为给定集合时，做均匀抽样<br>
- n_iter : int, default=10<br>
  - 测试参数的数量<br>
- scoring : string, callable or None, default=None<br>
  - 评分标准,如未指定，将采用estimator的scoring方法<br>
- fit_params : dict, optional<br>
  - 向fit方法传递的参数<br>
- n_jobs : int, default=1<br>
- pre_dispatch : int, or string, optional<br>
- iid : boolean, default=True  <br>
  - 参数为TRUE时，假设数据在各份内相同地分布；最小化损失函数，最小化的是所有份的损失函数的和，并不是平均数<br>
- cv : int, cross-validation generator or an iterable, optional<br>
  - 参数为空时，默认3折交叉验证；为integer对象k时，为k折交叉验证；为交叉验证生成器对象时<br>
- refit : boolean, default=True<br>
  - 是否用整个数据集训练，当参数为False时，只用交叉验证的数据训练<br>
- verbose : integer<br>
  - 显示模型情况多少，数字越大越多<br>
- random_state : int or RandomState<br>
  - 使用伪随机数生成器来完成参数的均匀随机抽样，而不是使用scipy.stats包来进行抽样<br>
- error_score : ‘raise’ (default) or numeric<br>
  - 如果在估计量拟合中出现错误，则分配给分数的值。 如果设置为'raise'，则会报错。 如果给出了数值，则引发FitFailedWarning。 此参数不影响refit步骤，这将始终引发错误<br>
- return_train_score : boolean, default=True<br>
  - 参数为False时，cv_results_将不包括训练的分数<br>
  
## Attributes<br>
- cv_results_ : dict of numpy (masked) ndarrays<br>
  - A dict with keys as column headers and values as columns<br>
- best_estimator_ : estimator<br>
  - 返回调优结果<br>
- best_score_ : float<br>
  - 返回最优模型的分数<br>
- best_params_ : dict<br>
  - 返回最优参数<br>
- best_index_ : int<br>
  - 返回最优参数，在params中的索引<br>
- scorer_:function<br>
  - 返回scoring方法<br>
- n_splits_ : int<br>
  - 返回k折交叉检验的K<br>
  
## Notes<br>
- 当n_jobs参数大于1时，数据被拷贝到每个参数的环境中（并不是复制n_jobs个，复制份数和参数的数量相等）。当每个job都耗时较小时可以提高计算效率，当数据集较大时会增加内存消耗。解决该问题的方案为：设置pre_dispatch参数，此时只将pre_dispatch复制多份，pre_dispatch的建议数量为2 * n_jobs<br>

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
