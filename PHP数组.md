# PHP 数组
1. 对象当数组使用 需 实现接口ArrayAccess
```
    interface ArrayAccess {
        abstract public boolean offsetExists ( mixed $offset )  // 检查一个偏移位置是否存在
        abstract public mixed offsetGet ( mixed $offset )   // 获取一个偏移位置的值
        abstract public void offsetSet ( mixed $offset , mixed $value )     // 设置一个偏移位置的值
        abstract public void offsetUnset ( mixed $offset )  // 复位一个偏移位置的值
    }

    $obj = new obj;
    $obj[] = 'Append 1';
    $obj[] = 'Append 2';
    printf($obj);
```

2. 数组的key 和 value的限制
    * key 可以是integer 或者 string
    * value 可以是任意类型
    - key 会有如下的强制转换
        * 包含有合法整型值的字符串会被转化为整型
        * 浮点数和布尔型会被转化成整型
        * 键名 null 实际会被存储为 ''
        * 数组和对象不能被用作键名
        * 相同键名，之前会被覆盖

3. 数组的访问
    * 方括号[] 或 花括号{}

4. 数组unset
    * unset 之后， 键 和 值会被删除，但是索引会继续保留, 不会重建索引
```
    $arr = [1, 2, 3];
    foreach ($arr as $key => $val) {
        unset($arr[$key]);
    }
    $arr[] = 4;
    // var_dump 结果为 [ 3 => 4 ];
```

5. 其它类型转化为数组
    * int, float, boolean, resource 类型 (array) $var = [$var]
    - object 类型， 结果为数组，key 是属性名， value 是属性值 
        * 可见性 public : 键名不变
        * 可见性 protected : 键名变为 \*+属姓名
        * 可见性 private : 键名变为 类名+属姓名
    * null 会转化成 空数组 []