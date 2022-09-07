# ESlint 配置

```bash
npm i eslint -D
npx eslint --init
```

执行上面命令后会提示一些选项，我们依次选择符合我们项目的配置。

# 集成 Prettier

```bash
npm i prettier -D
echo {}> .prettierrc

安装解决冲突需要用到的两个依赖

npm i eslint-config-prettier eslint-plugin-prettier -D
```

# vscode

`.vscode/settings.json`

```
{
  "prettier.enable": true,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true,
    "source.organizeImports": true,
  }
}
```

# Husky

```bash
npm i husky -D
npx husky install
```

然后我们需要在每次执行 npm install 时自动启用 husky
如果你的 npm 版本大于等于 7.1.0

```bash
npm set-script prepare "husky install"
```

然后添加一个 lint 钩子

```bash
npx husky add .husky/pre-commit "npm run lint"
```

[前端工程化配置指南](https://juejin.cn/post/6971812117993226248)
