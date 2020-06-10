# 不要解构

Mobx可观察对象仅仅是对象，当解构时，任何原始变量将保持最新值，不再是可观察的。可与使用[boxed observables](https://mobx.js.org/refguide/boxed.html)专门跟踪原始值，更好的方式或者是传递整个状态对象。

```react
// do NOT do this, it breaks reactivity
const {
  userCateStore: { activeUserCate },
} = useRootStore()
const localStore = useLocalStore(() => ({
  get dataSource() {
    return activeUserCate
  },
}))
```

在这种情况下，你可以将整个组件包装为观察者，也可以仅解构到最近的父元素。

```react
const { userCateStore } = useRootStore()
const localStore = useLocalStore(() => ({
  get dataSource() {
    return userCateStore.activeUserCate
  },
}))
```

