### sklearn.model_selection.GridSearchCV  
1. 用于参数调优,使用CV(交叉验证)方法<br>
1. class sklearn.model_selection.GridSearchCV(estimator, param_grid, scoring=None, fit_params=None, n_jobs=1, iid=True, refit=True, cv=None, verbose=0, pre_dispatch='2*n_jobs', error_score='raise', return_train_score=True) <br>
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
- iid : boolean, default=True  
  - 参数为TRUE时，假设数据在各份内相同地分布；最小化损失函数，最小化的是所有份的损失函数的和，并不是平均数<br>
- cv : int, cross-validation generator or an iterable, optional<br>
  - 参数为空时，默认3折交叉验证；为integer对象k时，为k折交叉验证；为交叉验证生成器对象时<br>
- 
