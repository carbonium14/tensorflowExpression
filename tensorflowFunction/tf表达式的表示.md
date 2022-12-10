# 表达式
## tf.abs
//目前只考虑实数的情况，不考虑复数，复数的方式为a+bi -> √(a^2+b^2)  
(x>0) and (x) or (x<0) and (-1\*x)
## tf.add
//前两个为一个是张量，一个是常量的相加情况，后面是两个都是张量的情况，只考虑一位数组，不考虑长度不同的情况  
//假设输入的两个量是x和y，最终输出的结果放在z里面  
(len(x)>1 and len(y)==1 and z\[0]=x\[0]+y and z\[1]=x\[1]+y and ... and z\[len(x)-1]=x\[len(x)-1]+y) or   
(len(y)>1 and len(x)==1 and z\[0]=y\[0]+x and z\[1]=y\[1]+x and ... and z\[len(y)-1]=y\[len(y)-1]+x) or   
(len(x)==len(y) and z\[0]=x\[0]+y\[0] and z\[1]=x\[1]+y\[1] and ... and z\[len(y)-1]=y\[len(y)-1]+x\[len(x)-1])  
## tf.add_n
//同样只考虑一位数组的情况，由于该函数自身要求必须长度相等，在此不考虑长度不等时的情况  
//假设输入的量为a1、a2...an，输出在ans里  
(ans\[0]=a1\[0]+a2\[0]+...+an\[0]) and (ans\[1]=a1\[1]+a2\[1]+...+an\[1]) and ... and (ans\[len(a1)-1]=a1\[len(a1)-1]+a2\[len(a1)-1]+...+an\[len(a1)-1])  
## tf.argmax
## tf.argmin
## tf.argsort
## tf.boolean_mask
//假设输入的量是a，掩码是b，按照要求长度应该相等  
(a\[0] and b\[0]==true) and (a\[1] and b\[1]==true) and ... and(a\[len(a)-1] and b\[len(b)-1]==true)  
## tf.broadcast_to
## tf.cast
## tf.clip_by_value
## tf.concat
## tf.constant
## tf.divide
## tf.equal
## tf.exp
## tf.expand_dims
## tf.eye
## tf.fill
## tf.gather
## tf.gather_nd
## tf.greater
## tf.greater_equal
## tf.math.bincount
## tf.math.ceil
## tf.math.count_nonzero
## tf.math.cumsum
## tf.math.divide_no_nan
## tf.math.floor
## tf.math.log
## tf.math.negative
## tf.math.reciprocal
## tf.math.reciprocal_no_nan
## tf.math.segment_max
## tf.math.segment_mean
## tf.math.segment_min
## tf.math.segment_prod
## tf.math.segment_sum
## tf.math.squared_difference
## tf.math.top_k
## tf.math.unsorted_segment_max
## tf.math.unsorted_segment_mean
## tf.math.unsorted_segment_min
## tf.math.unsorted_segment_prod
## tf.math.unsorted_segment_sum
## tf.matmul
## tf.maximum
## tf.minimum
## tf.multiply
## tf.not_equal
## tf.one_hot
## tf.ones
## tf.ones_like
## tf.pad
## tf.range
## tf.reduce_any
## tf.reduce_max
## tf.reduce_mean
## tf.reduce_min
## tf.reduce_prod
## tf.reduce_sum
## tf.reshape
## tf.reverse
## tf.roll
## tf.round
## tf.searchsorted
## tf.sequence_mask
## tf.shape
## tf.sign
## tf.sort
## tf.sqrt
## tf.square
## tf.squeeze
## tf.stack
## tf.subtract
## tf.tensordot
## tf.tile
## tf.transpose
## tf.unique_with_counts
## tf.unstack
## tf.where
## tf.zeros
## tf.zeros_like
