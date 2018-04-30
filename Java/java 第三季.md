**java 中的异常抛出：**

throw ：将产生的异常抛出（动作）

throws ：声明将要抛出何种异常的类型（声明）

```
public void 方法名(参数列表) throws 异常列表{
    //调用会抛出异常的方法或者：
    throw new Exception();
}
```

自定义异常：

```
class 自定义异常类 extends 异常类型{}
```

**java 中的异常链：**



