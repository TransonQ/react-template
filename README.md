# 模板说明

## ESlint 配置

```bash
npm i eslint -D
npx eslint --init
```

执行上面命令后会提示一些选项，我们依次选择符合我们项目的配置。

## 集成 Prettier

eslint 管代码质量, prettier 管代码格式

```bash
npm i prettier -D
echo {}> .prettierrc

安装解决冲突需要用到的两个依赖

npm i eslint-config-prettier eslint-plugin-prettier -D
```

## vscode

`.vscode/settings.json`

```json
{
  "prettier.enable": true,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true,
    "source.organizeImports": true
  }
}
```

## Husky

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

## Commitlint

为什么需要 Commitlint，除了在后续的生成 changelog 文件和语义发版中需要提取 commit 中的信息，也利于其他同学分析你提交的代码，所以我们要约定 commit 的规范。

```bash
npm i @commitlint/config-conventional @commitlint/cli -D
echo {}> .commitlintrc
```

`最后将Commitlint添加到钩子`

```
npx husky add .husky/commit-msg 'npx --no-install commitlint --edit "$1"'
```

`.commitlintrc`

```json
{
  "extends": ["@commitlint/config-conventional"]
}
```

### Angular 规范说明：

- [Commits MUST be prefixed with a type:](https://www.conventionalcommits.org/en/v1.0.0-beta.2/#specification)
  - feat：新功能
  - fix：修补 BUG
  - docs：修改文档，比如 README, CHANGELOG, - CONTRIBUTE 等等
  - style：不改变代码逻辑 (仅仅修改了空格、格式缩进、逗号等等)
  - refactor：重构（既不修复错误也不添加功能）
  - perf：优化相关，比如提升性能、体验
  - test：增加测试，包括单元测试、集成测试等
  - build：构建系统或外部依赖项的更改
  - ci：自动化流程配置或脚本修改
  - chore：非 src 和 test 的修改，发布版本等
  - revert：恢复先前的提交

> 参考
>
> - [前端工程化配置指南](https://juejin.cn/post/6971812117993226248)
