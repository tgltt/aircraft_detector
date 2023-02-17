# aircraft_detector军用飞行器检测项目
<div>
本工程是AI<b>深度学习</b>在计算机视觉<b><i>物体检测</i></b>方面的应用，采用的数据集是Kaggle 军用飞行器数据集，共<b>40</b>个分类，<b>10,000</b>多张图片，数据集压缩包占用<b>10GB</b>的磁盘空间，该数据集Kaggle持续在更新中。<br>
</div>
<br>

<li><b>40种军用飞行器类别</b><br>
<div>
    A-10, A-400M, AG-600, AV-8B, B-1, B-2, B-52 Be-200, C-130, C-17, C-5, E-2, EF-2000, F-117, F-14, F-15, F-16, F/A-18, F-22, F-35, F-4, J-20, JAS-39, MQ-9, Mig-31, Mirage2000, RQ-4, Rafale, SR-71(可能包含A-12), Su-34, Su-57, Tornado, Tu-160, Tu-95(Tu-142), U-2, US-2(US-1A Kai), V-22, Vulcan, XB-70, YF-23
</div>
<br>
 
<li><b>Kaggle数据集</b><br>
<div>
数据集地址：https://www.kaggle.com/datasets/a2015003713/militaryaircraftdetectiondataset <br>
数据集页面：
<img width="1064" alt="image" src="https://user-images.githubusercontent.com/36066270/219633087-160e9ef9-f541-4802-9fc2-2ad6340864cd.png">
</div>
<br>
<br>
    
<li><b>工程结构说明</b><br>

|    文件/文件夹         |                   功能描述               |
|       ----            |                    ----                 |
| kaggle_jupyter        | 存放本工程运行在jupyter notebook的实现文件 |
| paper                 | 存放模型相关的论文(ResNet、SSD)           |
| res50+ssd             | 存放ResNet50预训练模型                   |
| save_weights          | 存放模型每个迭代训练完成后的模型参数       |
| test_img              | 存放测试模型用的图片和视频                |
| src                   | 存放SSD模改后的模型                      |
| train_utils           | 存放训练功能相关的文件                    |
| train_ssd300.py       | 训练模型的主函数及入口类                  |
| my_dataset.py         | 定义批量访问数据集的功能类                 |
| transforms.py         | 预处理图片的功能类                        |
| predict_test.py       | 验证模型的推理功能类, 只验证图片           |
| predict_test_video.py | 验证模型的推理功能类, 只验证视频           |
<br>
<br>

<li><b>环境配置</b><br>
<div>Pip 安装包含所有 requirements.txt 的包，环境要求 Python>=3.6，且 PyTorch>=1.7
此外，需安装Coco性能(mAP)评估工具，使用下面的命令:</div>
    
```bash
pip install pycocotools 
```
<br>
<br>  
    
<li><b>工程算法说明</b><br>
<div>
    本工程基于<b>多任务多尺度的物体检测框架SSD</b>，根据军用航空器数据集的特点，进行<b>算法模型改造</b>，涉及改造点为图片数据格式筛选、训练集/测试集数据划分、图像标签数据结构转换为COCO数据格式、学习率及学习率调度参数调整、根据军用飞行器数据集计算Normalization的均值及标准差等。<br>
</div>
    
<div align=center>
    <img width="737" alt="image" src="https://user-images.githubusercontent.com/36066270/219654243-874a721d-72c2-4a6b-a577-747701e9fa5d.png"><br>
    <img width="813" alt="image" src="https://user-images.githubusercontent.com/36066270/219656949-dd7f7981-2f2a-49ff-a6b2-553306c1c126.png"><br>
    <b>SSD原理图</b> 
</div>
<br>
<br>

<li><b>本工程运行效果</b><br>
    以下检测结果图片在本工程的test_img目录下，检测结果上方文字，左边表示航空器类型，右边表示检测结果置信度。<br><br>
    检测图片路径：<a href="test_img/7854921f5e41d063b65bca8b429b6aa8.jpg">test_img/7854921f5e41d063b65bca8b429b6aa8.jpg</a><br>
    <img width="521" alt="image" src="https://user-images.githubusercontent.com/36066270/219657506-67d3406f-ac83-4ccd-bc90-842f17be536b.png"><br><br>
    检测图片路径：<a href="test_img/02d408885ea1339fac6e2344086599ab.jpg">test_img/02d408885ea1339fac6e2344086599ab.jpg</a><br>
    <img width="787" alt="image" src="https://user-images.githubusercontent.com/36066270/219657823-e0d68fe0-12fa-41f8-9f8f-0513461433c5.png"><br><br>
    检测图片路径：<a href="test_img/00ebecac178be3c3890a067d6a28234e.jpg">test_img/00ebecac178be3c3890a067d6a28234e.jpg</a><br>
    <img width="465" alt="image" src="https://user-images.githubusercontent.com/36066270/219658699-75fd9c95-e053-4f01-ab6c-a99620e5db46.png"><br><br>

美国C130大力神运输机视频检测效果： <a href="test_img/video/C130_detect.mp4">test_img/video/C130_detect.mp4</a><br>
美国F35攻击机视频检测效果：<a href="test_img/video/F35_detect.mp4">test_img/video/F35_detect.mp4</a><br>

<li><b>模型性能(COCO评估)</b><br>
    数据集10, 000张图片, 8,000张用于训练，剩下2,000张图片用于测试和评估，采用GPU P100训练70小时, 总共经历250个迭代(epochs)，目前达到的性能Iou 0.50以上的mAP为64.1%。召回率为61.5%.<br><br>
    
<div align=center>
<b>模改后的算法模型性能指标(epochs=249)</b>

|          PR指标         |     IoU   |   area | maxDets| AP/AR取值 |
|          :-----         |   :----:  | :----: | :----: |  :----:  |
| Average Precision  (AP) | 0.50:0.95 |  all   |   100  |  0.497   |
| Average Precision  (AP) | 0.50      |  all   |   100  |  0.641   |
| Average Precision  (AP) | 0.75      |  all   |   100  |  0.571   |
| Average Precision  (AP) | 0.50:0.95 |  small |   100  |  0.160   |
| Average Precision  (AP) | 0.50:0.95 | medium |   100  |  0.238   |
| Average Precision  (AP) | 0.50:0.95 | large  |   100  |  0.535   |
| Average Recall     (AR) | 0.50:0.95 |  all   |   1    |  0.499   |
| Average Recall     (AR) | 0.50:0.95 |  all   |   10   |  0.615   |
| Average Recall     (AR) | 0.50:0.95 |  all   |   100  |  0.615   |
| Average Recall     (AR) | 0.50:0.95 |  small |   100  |  0.183   |
| Average Recall     (AR) | 0.50:0.95 | medium |   100  |  0.314   |
| Average Recall     (AR) | 0.50:0.95 | large  |   100  |  0.655   |
</div>
    
<br>

    
<li><b>展望</b><br>
本工程对小物体(100*100以内)检测效果不太佳，另外对极相似的机型检测效果还不太稳定，比如F15、F35、J20、Mig31的检测效果比较摇摆，后续需对此两点进一步性能优化。
