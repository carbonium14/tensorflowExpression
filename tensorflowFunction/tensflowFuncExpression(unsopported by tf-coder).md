## 目前忽略函数：##
* assert相关函数
* 基础类型转化相关函数



   
## tf.broadcast_static_shape ##
```
函数的作用：给定已知shape，计算广播后的shape  
广播的原则：两个数组从末尾向前算起的维度的轴长度相等；或者其中一方的长度是1。广播会在缺失和(或)长度为1的维度上进行
输入：两个已知的shape，x和y，他们的维度是m和n，输出一个shape表示为z
(m < n and (((x[m] = y[n] or x[m] = 1) and z[n] = y[n]) or (y[n] = 1 and z[n] = x[m])) and ... and (z[n-m-1] = y[n-m-1]) and ... and (z[1] = y[1]))  
or ((m > n) and (((x[m] = y[n] or x[m] = 1) and z[n] = y[n]) or (y[n] = 1 and z[n] = x[m])) and ... and (z[m-n-1] = x[m-n-1]) and ... and (z[1] = x[1]))
or ((m = n) and (((x[m] = y[n] or x[m] = 1) and z[n] = y[n]) or (y[n] = 1 and z[n] = x[m])) and ... and (((x[1] = y[1] or x[1] = 1)and z[1] = y[1]) or (y[1] = 1 and z[1] = x[1])) )

```



