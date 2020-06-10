# 可变的状态

MobX一个重要方面是其状态可变性。

和Redux或者 [useReducer](https://reactjs.org/docs/hooks-reference.html#usereducer)这些使用不可变数据结构的流行解决方案相反，MobX基于直接改变来[通知任意的订阅者](https://mobx-react.js.org/observe-why)

由于对MobX状态对象的引用不会随时间变化，因此可以避免对不可变状态的检查。

> ```
> 使用`shouldComponentUpdate`进行大量检查以避免不必要的渲染是很常见的模式。 但是MobX根本不需要这样做。
> ```

