#### Generalized Linear Models

## By Stronger

```
class sklearn.linear_model.ARDRegression(n_iter=300, tol=0.001,<br>
                                              alpha_1=1e-06, alpha_2=1e-06, lambda_1=1e-06,<br>
                                              lambda_2=1e-06, compute_score=False, threshold_lambda=10000.0, <br>
                                              fit_intercept=True, normalize=False, copy_X=True, verbose=False)<br>
```

- **贝叶斯ARD回归**使用ARD(automatic relevance detemination)先验拟合回归模型的权重。回归模型的权重假定为高斯分布。还估计参数λ（权重分布的精度）和α（噪声分布的精度）。该估计通过迭代实现<br>

## parameters
- n_iter : int, optional<br>
  - 迭代的最大次数<br>
- tol : float, optional<br>
  - w的收敛条件，默认为0.001<br>
- alpha_1 : float, optional<br>
  - 超参数：与alpha相关的Gamma分布的形状参数<br>
- alpha_2 : float, optional<br>
  - 超参数：与alpha相关的Gamma分布的速率参数<br>
- lambda_1 : float, optional<br>
  - 超参数：与lambda相关的Gamma分布的形状参数<br>
- lambda_2 : float, optional<br>
  - 超参数：与lambda相关的Gamma分布的速率参数<br>
- compute_score : boolean, optional<br>
  - 当参数为**TRUE**时，计算每次迭代中目标函数的值<br>
- threshold_lambda : float, optional<br>
  - 删去高精度权重的阈值,default = 10000<br>
- fit_intercept : boolean, optional<br>
  - 是否计算截距（当数据已经中心化的时候，可选择不计算截距时）<br>
- normalize : boolean, optional, default False<br>
  - 当参数为TRUE时，在拟合模型之前将先对X进行标准化。当参数fit_intercept为false时，该参数将被忽略。
  - 当对X进行标准化后，超参数的学习结果将具有更高的鲁棒性，并且结果将与样本的数量无关。standardized 无法达到同样的效果，如果你希望进行standardized ，请调用preprocessing.StandardScaler过程，同时保持normalize=False<br>
- copy_X : boolean, optional, default True<br>
  - 确定X是否被复制，如参数为Flase，则X将被重写<br>
- verbose : boolean, optional, default False<br>
  - 显示的详细程度<br>

## Attributes
- coef_ : array, shape = (n_features)<br>
  - 回归模型的参数（分布的mean）<br>
- alpha_ : float<br>
  - 估计的噪声的精度<br>
- lambda_ : array, shape = (n_features)<br>
  - 权重的估计精度<br>
- sigma_ : array, shape = (n_features, n_features)<br>
  - 估计的方差-协方差矩阵<br>
- scores_ : float<br>
  - 当compute_score = True时，显示目标函数的值<br>

## methods
- fit(X, y)<br>
  - 根据给定的训练数据和参数拟合ARDRegression模型<br>
- get_params([deep])<br>
  - 获取模型的参数<br>
- predict(X)<br>
  - 使用模型进行预测<br>
- score(X, y[, sample_weight])<br>
  - 返回模型的R方,作为score<br>
- set_params(\*\*params)<br>
  - 设置模型的参数<br>
