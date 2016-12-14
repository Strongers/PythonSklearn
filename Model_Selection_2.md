#### Hyper-parameter optimizers 超参优化 <br>
<br>
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
