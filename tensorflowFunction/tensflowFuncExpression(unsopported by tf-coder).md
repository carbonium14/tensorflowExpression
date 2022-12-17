## 目前忽略函数: ##
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

## tf.dtypes.complex ##
```
表示实数的输入张量x，表示虚数的输入张量y，输出的虚数张量t
(x.len = y.len) and ((x.type = float32 and y.type = float32) or (x.type = float64 and y.type = float64)) and (t[0] = x[0] + y[0]j) and ... and(t[x.len - 1] = x[x.len -  1] + y[x.len - 1]j)
```

## tf.cond ##
```  
输入谓词pred，正确函数true_func，错误函数false_func，返回函数result
(pred and result = true_func) or (pred = false and result = false_func)
```

## tf.math.cumsum ##
```
按照维度进行累加，exclusive表示输出结果的第一元素是否与输入的第一个元素一致，false表示一致，reverse表示是否反着加，true表示反着
先限制输入为二维以内的张量
对于一维输入张量x：设输出张量为y
(exclusive = false and reserve = false and y[0] = x[0] and y[1] = y[0] + x[1] and y[2] = y[1] + x[2] and ... and y[x.len-1] = y[x.len-2] + x[len-1]) or
(exclusive = true and reserve = false and y[0] = 0 and y[1] = y[0] + x[0] and y[2] = y[1] + x[1] and ... and y[x.len-1] = y[x.len-2] + x[len-2]) or
(exclusive = false and reserve = true and y[0] = x[x.len-1] and y[1] = y[0] + x[x.len-2] and y[2] = y[1] + x[x.len-3] and ... and y[x.len-1] = y[x.len-2] + x[0]) or
(exclusive = true and reserve = true and y[0] = 0 and y[1] = y[0] + x[x.len-1] and y[2] = y[1] + x[x.len-2] and ... and y[x.len-1] = y[x.len-2] + x[1])
对于二维输入张量x，一维长度为m，二维长度为n，且输入的要求维度为axis:设输出张量为y
假设exclusive = false and reserve = false
(axis = 0 and y[0][0] = x[0][0] and y[1][0] = y[0][0] + x[1][0] and ... and y[m-1][0] = y[m-2][0] + x[m-1][0] and
 ...
 and y[0][n-1] = x[0][n-1] and y[1][n-1] = y[0][n-1] + x[1][n-1] and ... and y[m-1][n-1] = y[m-2][n-1] + x[m-2][n-1]) or 
 (axis = 1 and y[0][0] = x[0][0] and y[0][1] = y[0][0] + x[0][1] and ... and y[0][n-1] = y[0][n-2] + x[0][n-1] and
 ...
 and y[n-1][0] = x[n-1][0] and y[n-1][1] = y[n-1][0] + x[n-1][1] and ... and y[n-1][n-1] = y[n-1][n-2] + x[n-1][n-1])         
```









