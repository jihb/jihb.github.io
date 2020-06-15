# 库

截止到2018年底，在React使用Mobx已经有了一种统一的方式，就是[mobx-react](https://github.com/mobxjs/mobx-react) 库。

然后[React Hooks](https://reactjs.org/docs/hooks-intro.html) 出现了，[mobx-react-lite](https://github.com/mobxjs/mobx-react-lite) 旨在支持这个崭新的特性。 这对于一些发烧友来说很棒，但是对于新的使用者已经（并且还在）产生一些困难。



**可以使用 [mobx-react-lite](https://github.com/mobxjs/mobx-react-lite)在新的React Hooks的项目中。对于一些旧的项目继续往下看**

> 在不久的将来，`mobx-react-lite`可能会被弃用并变成`mobx-react`。
>
> 不过不用担心，迁移会像替换一个字符串一样简单。

## 还不能使用React Hooks？

🤷‍♂️ *你的代码因为在使用类组件所以无法使用React Hooks (React 16.8+)?*

👌 不要紧张，继续使用 `mobx-react@5`.

## 迁移到React Hooks？

🤷‍♂️ *类组件依然在你的代码中，但是你也可以(并且希望)使用Hooks*

👌使用 `mobx-react@6`，其中包含 `mobx-react-lite` ，并且会将它自动用于函数组件.

> `mobx-react@6` 中的`Provider/inject` 已经迁移到了[React Context](https://reactjs.org/docs/context.html)，它可能会在未来的版本中被完全删除。考虑直接使用[Context](https://mobx-react.js.org/recipes-context) 

## 全部使用Hooks？

🤷‍♂️ *代码中没有类组件?*

👌 直接使用 `mobx-react-lite` 作为一个更小更快的变体.

> 该库不包括传播状态的方法(Provider, inject)，查看更多关于[访问状态](https://mobx-react.js.org/state-how#accessing-a-state)



## 什么版本的`mobx`?

目前mobx有两个维护版本，V4 (LTS)和V5。您可以将它们中的任何一个与上面提到的任何库一起使用。主要的区别是你是否需要支持IE11，因为IE11不支持ES6代理(MobX V5依赖于它们)。