1. 灰度变换：grep_level_transform.py

   灰度变化根据数字图像处理里实现的有：

   图像反转， 对数变换， 幂律变换，分段函数变换，灰度分层，比特分层以及一个在博客上看到的变换，暂时还不清楚叫什么，在冈萨雷斯书上没有提到过，具体作用未知。

   具体的作用都在代码中有注释

   在我看来灰度变换全是用来拉伸对比度的，只不过不同的函数实现在不同的场景可能效果会好一点，在具体实现中还要看ROI区域，在选择灰度变换函数

   

 2.直方图均衡：histogram_euqlize.py

​	直方图均衡的作用：对过曝，或者过暗的图片都有增强效果，主要是将集中的pdf分散到整个定义域

​	具体实现分三步：

	1. 计算图像概率密度直方图；
 	2. 根据公式计算S_k:公式推到和计算公式参看冈萨雷斯74页；
 	3. 根据映射关系生成对应的图像：new_img[i, j] = S_k( img[i, j] )



​	直方图规定化：

​	首先要给定一个目标pdf，

​	1.求出给定pdf直方图规范化对应的灰度级，记为G_k;计算给定图片的直方图规范化，记为S_k;

 2. 对每一个S_k中的灰度级，在G_k中找出最接近的灰度级，并且存为grey_level;

 3. 求出变换后的图片：new_img[i, j  = grey_level(img[i, j])

    这里对最后一步还是有一点疑问，以后在细看了。



3.空间滤波：使用opencv中的方法实现

​	1.线性平滑滤波：均值滤波（随机噪声），高斯滤波（高斯噪声）

​	2.非线性平滑滤波：中值滤波（消除椒盐噪声）

​	进行边缘保留滤波通常用到两个方法：高斯双边滤波和均值迁移滤波

​	3.锐化滤波器：拉普拉斯算子（二阶），sobel算子（一阶）：主要用来增强细节和轮廓



4.书上的两个应用：

​	1.出版社和印刷常用做法：高提升滤波

​	2.混合空间增强（还有点问题，没有全部实现），可参考[这里](https://blog.csdn.net/xiaosha00000/article/details/84861893)

