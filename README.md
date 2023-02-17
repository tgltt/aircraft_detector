# aircraft_detector军用飞行器检测项目
<div>
本工程是计算机视觉<b><i>物体检测</i></b>方面的应用，采用的数据集是Kaggle 军用飞行器数据集，共<b>40</b>个分类，<b>10,000</b>多张图片，占用<b>10GB</b>的磁盘空间，该数据集Kaggle持续在更新中。<br>
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
<br>
