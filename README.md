学习要点：
1、sklearn.processing 中的LabelEncoder,将统计信息中的非数值信息自动转化为数值信息

2、会使用pandas中的.apply功能 X.apply(lambda x: d[x.name].fit_transform(x))
defaultdict的作用是在于，当字典里的key不存在但被查找时，返回的不是keyError而是一个默认值。
dict =defaultdict( factory_function)
这个factory_function可以是list、set、str等等，作用是当key不存在时，返回的是工厂函数的默认值，比如list对应[ ]，str对应的是空字符串，set对应set( )，int对应0。

3、关于数据的预处理问题
# 从sklearn.preprocessing导入StandardScaler
from sklearn.preprocessing import StandardScaler
# 标准化数据，保证每个维度的特征数据方差为1，均值为0，使得预测结果不会被某些维度过大的特征值而主导
ss = StandardScaler()
# fit_transform()先拟合数据，再标准化
X_train = ss.fit_transform(X_train)
# transform()数据标准化
X_test = ss.transform(X_test)


fit_transform()的作用就是先拟合数据，然后转化它将其转化为标准形式；即tranform()的作用是通过找中心和缩放等实现标准化
为什么在标准化数据的时候不使用fit_transform()函数呢？
为了数据归一化（使特征数据方差为1，均值为0），我们需要计算特征数据的均值μ和方差σ^2，再使用下面的公式进行归一化：X =(x-m)/(方差的平方)
我们在训练集上调用fit_transform()，其实找到了均值μ和方差σ^2，即我们已经找到了转换规则，我们把这个规则利用在训练集上，同样，我们可以直接将其运用到测试集上（甚至交叉验证集），所以在测试集上的处理，我们只需要标准化数据而不需要再次拟合数据。

/Users/kelang-tian/Desktop/fit_transform.png
# Decision-Tree
