## tf.debugging.assert ##  
```
tf.debugging.Assert(condition, data, summarize=None, name=None) {  
    if ( condition != true ) {   
        print data;  
        return tf.errors.InvalidArgumentError; }  
    else return null; 
}
```

   
## tf.abs ##
```
tf.math.abs(x, name=None) {
    if(x.type == complex_number) {
        o1 = x.real;
        o2 = o1 * o1;
        o3 = x.imaginary;
        o4 = o3 * o3;
        o5 = o2 + o4;
        o4 = sqrt (o5);
        return o4;
    } else {
        if (x < 0) x = -x;
        return x;
    }
}
```



