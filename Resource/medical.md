# Mecial

## Medical specific metrics

>In the cancer example, sensitivity and specificity are the following:

> **Sensitivity=Recall**: Of all the people **with** cancer, how many were correctly diagnosed?

> **Specificity**: Of all the people **without** cancer, how many were correctly diagnosed?
And precision and recall are the following:

>**Recall**: Of all the people who **have cancer**, how many did we diagnose as having cancer?

>**Precision**: Of all the people **we diagnosed** with cancer, how many actually had cancer?



x|Diagnosed Sick|Diagnosed Healthy|Metrics
-|:-:|:-:|-:
Sick|True Positive|False Negative|**Recall=Sensitivity** 
Healthy|False Positive|True Negative|**Specificity**
**metrics**|**Precision**

- TP: (True Positives) Sick people that we correctly diagnosed as sick.
- TN: (True Negatives) Healthy people that we correctly diagnosed as healthy.
- FP: (False Positives) Healthy people that we incorrectly diagnosed as sick.
- FN: (False Negatives) Sick people that we incorrectly diagnosed as healthy.
then:

Sensitivity = $\frac{TP}{TP + FN}$

Specificity = $\frac{TN}{TN + FP}$

Recall = $\frac{TP}{TP + FN}$

Precision = $\frac{TP}{TP + FP}$

## OSS

## Medical Image processing

1. An Introduction to Biomedical Image Analysis with TensorFlow and DLTK [link](https://medium.com/tensorflow/an-introduction-to-biomedical-image-analysis-with-tensorflow-and-dltk-2c25304e7c13)

2. Medical Image Analysis with Deep learning [Part1](https://www.kdnuggets.com/2017/03/medical-image-analysis-deep-learning.html) [Part2](https://www.kdnuggets.com/2017/04/medical-image-analysis-deep-learning-part-2.html)  [Part3](https://www.kdnuggets.com/2017/06/medical-image-analysis-deep-learning-part-3.html)

[Taposh Dutta-Roy blog ](https://medium.com/@taposhdr)
[Medium Link Part 1](https://medium.com/@taposhdr/medical-image-analysis-with-deep-learning-i-23d518abf531)
[Medium Link Part 4](https://medium.com/@taposhdr/medical-image-analysis-with-deep-learning-iv-479b5fa446e7)

3. DICOM Image processing group articles [link](https://blog.csdn.net/column/details/dicom.html)

## Tech and Algorithm

1. CLAHE (Contrast Limited Adaptive Histogram Equalization)
   cv2.createCLAHE

2. Change CT value with WW(Window Width), WL(Window Level), CT HU(hounsfield unit ，HU), Algorithm [link](https://blog.csdn.net/chenhuakang/article/details/79164134)

3. U-Net

4. V-Net - medial algorithm [Blog](https://blogs.nvidia.com/blog/2018/03/28/ai-healthcare-gtc/) can automatically measure anatomy and assess functionality
5. AutoMap - medial application. [Blog](https://blogs.nvidia.com/blog/2018/03/28/ai-healthcare-gtc/)  from the MGH Martinos center, can shorten acquisition time of MRI and boosts image quality
6. Clara - [Blog](https://blogs.nvidia.com/blog/2018/03/28/ai-healthcare-gtc/) Medical Image Supercomputer , from Nvidia
7. Cinematic rendering -  [Blog](https://blogs.nvidia.com/blog/2018/03/28/ai-healthcare-gtc/) pioneered by Elliot Fishman at Johns Hopkins University brings a new level of quality, ultimately saving time for radiologists and improving patient outcomes.
8. NiffyNet - [official](http://niftynet.io/) [github](https://github.com/NifTK/NiftyNet) [Paper]

### 3D CNN

1. [CT影像肺结节](https://zhuanlan.zhihu.com/p/29984844) [OSS](https://tianchi.aliyun.com/forum/new_articleDetail.html?raceId=231601&postsId=2898&from=part)
2. [Kaggle实例](http://www.sohu.com/a/138840776_610300)
3. [detail](https://blog.csdn.net/u014154380/article/details/78395010)
4. [PointNet](http://www.sohu.com/a/164139251_651893)
5. [搭建 3D CNN](http://www.360doc.com/content/17/0421/10/10408243_647313566.shtml)

## Libraries

1. OpenCV
2. Simple ITK [official](http://www.simpleitk.org/)
3. Python Image Library, PIL
4. DLTK - [official](htps://dltk.github.io/) 

## [medical strategy]

1. [link](http://www.biomedicalcomputationreview.org/content/deep-learning-and-future-%E2%80%A8biomedical-image-analysis)

## [DICOM Python:pydicom]

https://www.raddq.com/dicom-processing-segmentation-visualization-in-python/

https://github.com/pydicom/pydicom

https://blog.csdn.net/dcxhun3/article/details/51777794

https://tianchi.aliyun.com/forum/new_articleDetail.html?raceId=231601&postsId=2898&from=part

### DICOM 3.0

1. Communication Protocol [link](https://blog.csdn.net/zssureqh/article/details/50063265)

## PACS

1. Platform compare [link](https://dcm4che.atlassian.net/wiki/download/attachments/950333/ossdicom.pdf?version=1&modificationDate=1178887181318&cacheVersion=1&api=v2)
2. Dcm4che  [wiki](5.https://dcm4che.atlassian.net/wiki/spaces/proj/overview?mode=global) [official](https://www.dcm4che.org/) [compileissue](https://blog.csdn.net/zssureqh/article/details/50811535)
3. Clear Canvas [link](https://github.com/ClearCanvas/ClearCanvas/releases) [github](http://clearcanvas.github.io/)
4. Connection method [link](https://wenku.baidu.com/view/05844b69af1ffc4ffe47acba.html)
5. Dcm4chee [Docker](https://github.com/dpatriarche/docker-dcm4chee) [github](https://github.com/dcm4che/dcm4chee-arc-light)

## [Tianchi Strategy]

http://www.donews.com/technology/detail/21693540

## [Nodule detection]

https://github.com/lfz/DSB2017

## [Keras and Tensorflow]

https://www.learnopencv.com/keras-tutorial-transfer-learning-using-pre-trained-models/

!!!!![Fine Tuning Practice]
https://blog.keras.io/building-powerful-image-classification-models-using-very-little-data.html
https://github.com/zhixuhao/unet
https://blog.csdn.net/jiandanjinxin/article/details/60583223

## DICOM 影像分析 Overview

1. Dicom is  easy [link](http://dicomiseasy.blogspot.com/)

https://www.leiphone.com/news/201706/xwSoWmhNgkn34iGS.html
https://www.kdnuggets.com/2017/03/medical-image-analysis-deep-learning.html

## SVS file

https://blog.csdn.net/formlsl/article/details/80681488

## Tools

1. ImageJ
2. OpenSlide  pathology [Official](https://openslide.org/) [windows](https://openslide.org/docs/windows/)
3. MicroDICOM

## Reference

!!!! https://blog.csdn.net/xiangz_csdn/article/details/54691990
http://www.openmicroscopy.org/