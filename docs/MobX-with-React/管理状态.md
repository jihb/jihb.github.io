# 如何管理状态

React中的状态管理是一个非常宽泛的话题，而且经常会有新的模式引入。MobX简化了一些事情，但是仍然有几种不同的使用方式，便于选择使用。

### 创建一个状态

MobX中的状态由任何[可观察对象](https://mobx.js.org/refguide/observable.html)表示。你可以使用接下来文档中提到的任何一种方法。

对于高级和更健壮的状态监听，更好的选择可能是[mobx-state-tree](https://github.com/mobxjs/mobx-state-tree)。

最后，我们还会介绍一些新的钩子在下面的文档中，比如[useLocalStore](https://mobx-react.js.org/state-local) *(在类组件中不可用)*。

```react
import { observable } from 'mobx'
import { useLocalStore } from 'mobx-react' // 6.x or mobx-react-lite@1.4.0

function CreatingState() {
  const simpleState = React.useRef(observable.array([1, 2, 3])).current
  const [bigState] = React.useState(createExpensiveStore)
  const localState = useLocalStore(() => ({
    count: 0,
    inc() {
      localState.count += 1
    },
  }))
  return <Rendering simple={simpleState} big={bigState} local={localState} />
}

class CreatingState extends React.PureComponent {
  // or use constructor if class properties are not available for you
  simpleState = observable.array([1, 2, 3])
  render() {
    // class component does not support any other way of
    // keeping observable state within a component
    return <Rendering simple={this.simpleState} />
  }
}
```

*警告。永远不要使用`React.useMemo`来保持对状态对象的引用。它可能会被React随机丢弃导致丢失数据。* 

### 访问数据

状态管理第二个重要方面是如何在组件树之间传递创建的可观察对象。 虽然这些和MobX的逻辑无关，但也值得在这里提一下。

在简单的场景中，你可以在一个组件的内部创建一个可观察对象，然后通过`props`传递（如上所示）。 和你常使用的方法例如[useReducer](https://reactjs.org/docs/hooks-reference.html#usereducer)类似，不过useReducer只能传递一个对象。

为了更强大的状态管理，建议通过旧版[inject](https://mobx-react.js.org/recipes-inject)使用[React Context](https://mobx-react.js.org/recipes-context)。

#### 全局变量状态？

可以将应用程序状态保留在全局变量中，在组件文件中导入。 这种方式在大多数情况下都可以使用。

但是，假如你在写测试，则全局变量是一个问题，并且可能很脆弱。 简而言之，我们不建议将状态保留在全局变量中。

