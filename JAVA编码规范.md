# 异常处理

#### 1. 只有异常情况下才使用异常

简单的说，就是不要用异常来处理正常的业务逻辑。

反例：
使用异常来达到终止无限循环的目的
```
try{
    int i=0;
    while(true){
        range[i++].climb();
    }catch(ArrayIndexOutOfBoundsException e){
        //Ingore
    }
}
```

#### 2. 对可预见的，或可恢复的异常使用受检异常

业务逻辑自定义的异常，建议都使用可受检异常。因为往往高层调用时，需要捕获这些自定义异常。进行异常的流程处理。以下是异常的继承关系：
```
Throwable
    ----Error
    ----Exception
            ----IOExcetion
            ----RuntimeException
```
其中Error和RuntimeException及其子类为未受检异常，Exception除RuntimeException及其子类以外为受检异常

#### 3. 如果给每一层逻辑定义了对应异常，那么高层调用最好屏蔽底层异常，使用高层异常

如果底层异常信息对高层非常重要不能丢失，那么可以使用异常链来处理。

建议：
下面是高层的代码在调用底层代码时，捕获了底层异常，并抛出高层异常的做法。Throwable中定义的cause在javadoc中解释为：The throwable that caused this throwable to get thrown。
```
try{
    ...
}catch(LowerLevelException e){
    throw new HigherLevelExceotion(e);
}
```
```
class HigherLevelExceotion extends Exception{
    HigherLevelExceotion(Throwable cause){
        super(cause)
    }
}
```

#### 4. 逻辑内部抛出所有异常，都要在方法上写注解@throws并说明用途

用javadoc的@throws标签注释所有受检和不受检的异常。使用throws标记受检的异常，不要使用throws标记不受检的异常。使用API的同学有责任区分受检异常和不受检异常。

#### 5. 把异常细节设置到细节消息中

程序未捕获异常时，往往系统会自动打印异常的堆栈轨迹。即toString的调用结果。我们要把异常细节设置到其中。方便排查。

建议：
使用构造器保存异常细节到堆栈。下面是一个数组越界异常构造器
```
public IndexOutOfBoundsException(int lowerBound, int upperBound, int index){
    //系统打印堆栈时，就会把失败细节带上
    super(String.format("lowerBound:%d, upperBound:%d, index:%d", lowerBound,)upperBound, index);
    
    //上层需要单独识别异常细节时，可单独get获取
    this.lowerBound = lowerBound;
    this.upperBound = upperBound;
    this.index = index;
}
```


#### 6. 异常失败要尽量使对象保持原子性

反例：
下面是一个队列pop操作，如果队列是空，抛出异常，但是之后这个队列状态改变了，size有可能变负数了。
```
public Object pop(){
    Object result = elements[--size];
    elements[size] = null;
    return result;
}
```

建议：
把可能失败的检查前置到操作对象状态前
```
public Object pop(){
    if(size == 0){
        throw new EmptyException();
    }
    Object result = elements[--size];
    elements[size] = null;
    return result;
}
```

#### 7. 不要忽略异常

不要忽略异常，如果确实可以忽略，请写明注释。但是把异常记录下来是明智的做法。

反例：
```
try{
    ...
}catch(SomeException){
}
```

