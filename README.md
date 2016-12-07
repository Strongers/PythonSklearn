### Python sklearn 学习笔记
`By Stronger`
-----
### 学习内容
```
  package sklearn
  sklearn.cluster.AgglomerativeClustering
  sklearn.cluster.FeatureAgglomeration
  sklearn.model_selection.GridSearchCV
  sklearn.model_selection.RandomizedSearchCV
  sklearn.model_selection.ParameterGrid
  sklearn.model_selection.ParameterSampler
  sklearn.model_selection.fit_grid_point
```
##### AgglomerativeClustering

###### Class
AgglomerativeClustering(n_clusters=2, affinity='euclidean', memory=Memory(cachedir=None), connectivity=None, compute_full_tree='auto', linkage='ward', pooling_func=<function mean>) <br>
###### 解释
Recursively merges the pair of clusters that minimally increases a given linkage distance. <br>
通过最小距离,递归的将新的元素加入到现有的聚类结果中 <br>**属于分层聚类的一种算法** <br>
<br>
1. n_clusters : int, default=2 <br>
The number of clusters to find. <br>
聚类的数量 <br>
<br>
2. connectivity : array-like or callable, optional <br>
Connectivity matrix. Defines for each sample the neighboring samples following a given structure of the data. This can be a connectivity matrix itself or a callable that transforms the data into a connectivity matrix, such as derived from kneighbors_graph. Default is None, i.e, the hierarchical clustering algorithm is unstructured. <br>
连接矩阵 <br>
<br>
3. affinity : string or callable, default: “euclidean” <br>
距离计算方式，如欧式距离、L2、L1 <br>
<br>
4. memory : Instance of joblib.Memory or string (optional) <br>用于缓存树的结果输出，输入为路径字符串，当设定为空值时，结果树将不被储存<br>
<br>
