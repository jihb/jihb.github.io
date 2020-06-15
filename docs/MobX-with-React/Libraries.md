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