## 目前忽略函数：##
* assert相关函数
* 基础类型转化相关函数



   
## tf.broadcast_static_shape ##
```
函数的作用：给定已知shape，计算广播后的shape  
广播的原则：两个数组从末尾向前算起的维度的轴长度相等；或者其中一方的长度是1。广播会在缺失和(或)长度为1的维度上进行
输入：两个已知的shape，x和y，他们的维度是m和n，输出一个shape表示为z
(m < n and (((x[m-1] = y[n-1] or x[m-1] = 1) and z[n-1] = y[n-1]) or (y[n-1] = 1 and z[n-1] = x[m-1])) and ... and (z[n-m-1] = y[n-m-1]) and ... and (z[0] = y[0]))  
or ((m > n) and (((x[m-1] = y[n-1] or x[m-1] = 1) and z[n-1] = y[n-1]) or (y[n-1] = 1 and z[n-1] = x[m-1])) and ... and (z[m-n-1] = x[m-n-1]) and ... and (z[0] = x[0]))
or ((m = n) and (((x[m-1] = y[n-1] or x[m-1] = 1) and z[n-1] = y[n-1]) or (y[n-1] = 1 and z[n-1] = x[m-1])) and ... and (((x[0] = y[0] or x[0] = 1) and z[0] = y[0]) or (y[0] = 1 and z[0] = x[0])) )

```

## tf.broadcast_dynamic_shape ##
```  
输入：两个已知的shape，x和y，他们的维度是m和n，输出一个shape表示为z
(m < n and (((x[m-1] = y[n-1] or x[m-1] = 1) and z[n-1] = y[n-1]) or (y[n-1] = 1 and z[n-1] = x[m-1])) and ... and (z[n-m-1] = y[n-m-1]) and ... and (z[0] = y[0]))  
or ((m > n) and (((x[m-1] = y[n-1] or x[m-1] = 1) and z[n-1] = y[n-1]) or (y[n-1] = 1 and z[n-1] = x[m-1])) and ... and (z[m-n-1] = x[m-n-1]) and ... and (z[0] = x[0]))
or ((m = n) and (((x[m-1] = y[n-1] or x[m-1] = 1) and z[n-1] = y[n-1]) or (y[n-1] = 1 and z[n-1] = x[m-1])) and ... and (((x[0] = y[0] or x[0] = 1) and z[0] = y[0]) or (y[0] = 1 and z[0] = x[0])) )
```

## tf.clip_by_global_norm ##
```
假设已经得到了global_norm，global_norm = sqrt(sum([l2norm(t)**2 for t in t_list]))，t_list是输入的张量  
输入：要进行裁剪的张量t，截取比率c，用户事先计算得出的global_norm u，返回的是一个裁剪好的张量r，假设是一维张量  
 (u = infinity and r = NaN) or (c > u and r = t) or (u > c and r[0] = t[0] * c / u and ... and r[len(t)-1] = t[len(t) - 1] * c / u)

```

## tf.clip_by_norm ##
```
假设输入的是一维张量，输入：进行裁剪的张量t，允许的最大剪辑值c，传入的张量t的L2范数n，输出张量r
(n <= c and r = t) or (n > c and r[0] = t[0] * c / n and ... and r[len(t) - 1] = t[len(t) - 1] * c / n)
```






