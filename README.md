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

[前端工程化配置指南](https://juejin.cn/post/6971812117993226248)
