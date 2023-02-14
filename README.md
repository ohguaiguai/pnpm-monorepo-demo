1. 子项目相同依赖是否会自动提升?

- 没有声明 workspace 时检测不到子项目的依赖
- 声明 workspace 时同样检测不到子项目的依

2. 在子项目中安装依赖是否会自动提升？
   也不会。这个和 yarn2+ 不同，yarn2+ 无论在哪里安装依赖，都会把依赖放在 根 .yarn/cache 中保证相同版本的依赖只有一份。

所以只能手动把子项目中公共依赖放在父级 package.json 中，然后在父级中执行 pnpm install， 跑下试试:

pnpm 不能在根目录启动子项目

```js
pnpm start --filter app1
```

进入 app1 执行 `pnpm start`, 发现找不到 react-scripts 命令, 尝试使用 `npm start` 可以正常启动服务, 说明 npm 会向上查找，而 pnpm 不会

app1 引入 common 不需要 使用 index.d.ts 来声明一下
