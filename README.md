# Deep Learning
最近在学习深度神经网络的东西，看了不少了网络结构的知识，这里首先从github上的Mask RCNN开始试水。
## Note
* 操作系统 ubuntu： 16.04
## Sample 1： Balloon
* 步骤一： download整个Mask RCNN项目的文件
* 步骤二： download h5文件和数据集
* 步骤三： 使用安装命令安装requirement
* 步骤四： 执行安装：python setup.py install
* 步骤五： 命令行执行命令： 命令格式：python balloon.py splash --weights=[h5文件路径] --image=[文件名路径或者url]<br>

这个运行的时候没有什么问题，很简单，只是看下效果，处理后的图片会保存在samples/balloon/路径下
## Sample 1： COCO
### Method 1
    将demo.ipynb中的内容存在py文件中，放在mask_rcnn/samples下，运行后无法显示处理的图片
    
![](https://github.com/Paisins/Deep-learning/blob/master/Screenshot%20from%202018-12-27%2014-17-46.png)
### Method 2
后面我发现，使用jupyter notebook打开demo.ipynb后直接运行可以显示出图片来，但是凭我如何修改visualize.py文件都不能对输出结果产生影响，这让我很郁闷，也很奇怪。当我输入visualize的路径的时候，才发现它导入的根本不是我下载mask_rcnn下的visualize.py文件，所以前面的修改没有任何影响，于是我修改了导入的文件路径，终于可以保存文件了。
#### 修改一： demo.ipynb
``` python
# Import Mask RCNN
# sys.path.append(ROOT_DIR)  # To find local version of the library
# from mrcnn import utils
# import mrcnn.model as modellib
# from mrcnn import visualize

import imp
utils = imp.load_source('utils', '/home/jcj/Documents/Mask_RCNN/mask_rcnn/mrcnn/utils.py') 
modellib = imp.load_source('model', '/home/jcj/Documents/Mask_RCNN/mask_rcnn/mrcnn/model.py') 
visualize = imp.load_source('visualize', '/home/jcj/Documents/Mask_RCNN/mask_rcnn/mrcnn/visualize.py') 
```
#### 修改二： visualize.py
```python
# display_instances()
if auto_show:
    #保存图片
    plt.savefig("/home/jcj/Documents/Mask_RCNN/mask_rcnn/saved_picture/2.jpg")
    plt.show()
```
其实中间还有一个问题就是安装PyCOOtools文件，一般安装总会出各种问题，最后找到比较好的方法
```
pip install git+https://github.com/philferriere/cocoapi.git#subdirectory=PythonAPI
```
