## Faster-Rcnn：目标检测模型在Pytorch当中的实现
---
logs:包含训练评估指标和训练保存的模型

model_data：包含预训练模型

VOCdevkit：对应VOC数据集

模型下载链接：
链接：https://pan.baidu.com/s/1xI1Vgtqb3nELf8xJ4F2w4Q?pwd=68v6 
提取码：68v6


## 训练步骤
### a、训练VOC2012数据集
1. 数据集的准备   
下载之后将VOCdevkit文件夹对齐

2. 数据集的处理   
修改voc_annotation.py里面的annotation_mode=2，运行voc_annotation.py生成根目录下的2012_train.txt和2012_val.txt。 
训练集：测试集=9：1

3. 开始网络训练   
train.py的默认参数用于训练VOC数据集，直接运行train.py即可开始训练。   

4. 训练结果预测
训练结果预测需要用到两个文件，分别是frcnn.py和predict.py。我们首先需要去frcnn.py里面修改model_path以及classes_path，这两个参数必须要修改。   
**model_path指向训练好的权值文件，在logs文件夹里。   
classes_path指向检测类别所对应的txt。** 
#输出预测框   
运行predict.py，mode="predict"进行检测了。运行后输入图片路径即可检测。  
#输出rpn推荐框    
完成修改后就可以运行predict.py，mode="predict_rpn"进行检测了。运行后输入图片路径即可检测。 
注：默认输出300个推荐框，想要修改数量，打开frcnn.py,修改detect_rpn_image函数中最后绘制box的循环
for i in range(20): #设置绘制的候选框数量，修改循环次数，改变框数量




## 评估步骤 
### a、评估的测试集
1. 本文使用VOC格式进行评估。
2. 在frcnn.py里面修改model_path以及classes_path。**model_path指向训练好的权值文件，在logs文件夹里。classes_path指向检测类别所对应的txt。**  
3. 运行get_map.py即可获得评估结果，评估结果会保存在map_out文件夹中。



## Reference
https://github.com/chenyuntc/simple-faster-rcnn-pytorch  
https://github.com/eriklindernoren/PyTorch-YOLOv3  
https://github.com/BobLiu20/YOLOv3_PyTorch
https://github.com/bubbliiiing/faster-rcnn-pytorch
