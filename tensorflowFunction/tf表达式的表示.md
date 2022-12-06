# 表达式
## tf.abs

    x>=0?x:-x
    if(x是复数) √(a\*a+b\*b) //x是a+bi的形式

## tf.add

    //如果出现了一个张量一个常量的情况，假定x是张量y是常量，即如果x是常量y是张量则交换
    if(x是张量y是常量) {
      for(int i=0;i<x.size;i++) {
        x[i]+=y
      }
      return x
    }
    if(xy都是张量) {
      if(x.size===y.size) {
        for(int i=0;i<x.size;i++) {
            x[i]+=y[i]
        }
        return x
      } else {
        //如果xy不等长，应该把短的那个一次复制到和长的一样长，之后再执行相加指令
      }
    }
