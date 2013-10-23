### scala 集合类型
1. Set(有可变不可变实现)
2. Map(有可变不可变实现)
3. List(只有不可变实现)


直接调用类名会调用相应的apply 方法，
filter, map, forall, foldLeft(/:) (p88), foldRight(\:)

方法名第一个字符决定了它的优先级，最后一个字符决定了调用目标(以冒号":", "+", "-", "!", "~"结尾的调用目标是运算符后面的实例)
for 表达式

    val doubleEven = for (i <- 1 to 10; if i % 2 == 0)
        yield i * 2

