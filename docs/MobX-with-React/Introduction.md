# 简介 

在React中使用MobX让组件的响应变得容易。而且它也可以处理好整个应用的状态。

*此站点主要给出如何在React函数组件和Hooks中使用MobX的示例。在类组件中使用也是类似的。在一些有类组件特殊行为的情况中，我们会提到并提供合适的示例*

你可以选择查看一下下面的一个备忘录应用的示例，或者继续了解[为什么要去监听状态](MobX-with-React/Observe-state/How-to-observe.md)或者是[怎么样管理状态](MobX-with-React/Manage-state/How-to-manage-state.md)。

你想要迁移至Hooks吗？可以看一下我们的[迁移指南](MobX-with-React/Recipes/Migration-guide.md)

```react
import React from 'react'
import { observer, useLocalStore } from 'mobx-react' // 6.x or mobx-react-lite@1.4.0

export const TodoList = observer<{ initialTodos: string[] }>(
  ({ initialTodos }) => {
    const todoRef = React.useRef()
    const store = useLocalStore(() => ({
      todos: createTodos(initialTodos) as Record<string, boolean>,
      get pendingTodos() {
        return Object.keys(store.todos).filter(
          todo => store.todos[todo] === false,
        )
      },
      get doneTodos() {
        return Object.keys(store.todos).filter(
          todo => store.todos[todo] === true,
        )
      },
      addTodo: () => {
        store.todos[todoRef.current.value] = false
        todoRef.current.value = ''
      },
      toggleTodo: (todo: string) => {
        store.todos[todo] = !store.todos[todo]
      },
    }))

    const renderTodo = (done: boolean) => todo => (
      <Todo key={todo} done={done} text={todo} onToggle={store.toggleTodo} />
    )

    return (
      <form onSubmit={store.addTodo}>
        {store.pendingTodos.map(renderTodo(false))}
        {store.doneTodos.map(renderTodo(true))}
        <br />
        <input ref={todoRef} />
        <button>Add todo</button>
      </form>
    )
  },
)
```



### References

[https://mobx-react.js.org/][https://mobx-react.js.org/]

