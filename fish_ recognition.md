# Fish Recogniztion
第一次接触的图像识别项目是关于鱼类识别的，目标是识别出图像中的鱼的种类及对应的数量，范围是亚洲常见鱼类，因为数据集的问题，识别类目初始定为10类。
## Note
- 训练工具：Google Colab
- 数据集：论坛及百度图片搜索，人工筛选得到
- 训练模型：[keras-retinanet](https://github.com/fizyr/keras-retinanet)
## Stage1：获取数据集
- 利用爬虫在鱼类论坛上下载了近千张图片（筛选后的数量），在百度图片上按关键词搜索后又获取了近千张图片（筛选后的数量）
- 使用[VGG打标签工具](http://www.robots.ox.ac.uk/~vgg/software/via/via_demo.html)对已下载对图片打标签
## Stage2：数据处理
- 使用pandas将导出的csv文件做处理，变成模型训练所要求的格式
## Stage3：Google Colab
- 将项目和图片数据上传至谷歌云盘
- 按照教程创建colab notebook文件，以及关联到云盘，执行训练
- 训练结束后将训练好的h5文件导出
## Parameter
- 我是第一次接手这样的项目，虽然之前看书的时候了解了很多学习率，激活函数等东西，但是实际中并没有去调整这些参数，都是按照默认值去训练的，唯一修改的地方就是steps的值，默认值是10000，我最初设置为800，后来修改成了1400。
## Question
1. 