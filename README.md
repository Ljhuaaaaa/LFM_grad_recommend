# LFM_Grad_Recommend
# Summary
本项目通过MovieLens开源数据集，分为训练集和测试集，使用训练集数据进行LFM矩阵分解算法迭代，得到P和Q矩阵，最后为测试集用户进行TopN推荐，以及计算测试集的均方误差和预测评分

MovieLens数据集地址：https://grouplens.org/datasets/movielens/

# Data-processing
本项目只使用无上下文信息的显性反馈数据，所以把MovieLens数据集中的时间戳删掉，并且数据分为8份取其中的一份作为测试集，其余7分作为训练集(此处使用了随机数种子，可以方便以后分别使用不同的份数作为测试集进行训练和测试)

# Model
采用的是LFM矩阵分解算法(隐因子模型)进行推荐，使用训练集进行LFM算法的训练，得到用户-隐因子矩阵和隐因子-产品矩阵，再对测试集中的用户进行TopN推荐，以及计算测试集中的预测评分和均方误差

# Conclusion
均方误差为0.79，也算是一个不错的结果了(可以遍历份数，去对均方误差求平均值，更有说服力)。

LFM算法相较于ItemCF和UserCF算法来说，精确度，召回率和覆盖率会更高些，但是LFM算法无法进行实时推荐，每当有新用户新产品进来时，则需要重新进行LFM算法迭代，从而时间代价太大。
