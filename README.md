<picture>
    <source srcset="./.github/logo-dark.png" media="(prefers-color-scheme: light)">
    <source srcset="./.github/logo-white.png" media="(prefers-color-scheme: dark)">
    <img src="./.github/logo-dark.png" alt="logo">
</picture>



## 自托管

适用于家庭实验室的自托管方案。

**通过 Docker Hub：**

```sh
docker run -d --name it-tools --restart unless-stopped -p 8080:80 corentinth/it-tools:latest
```

**通过 GitHub Packages：**

```sh
docker run -d --name it-tools --restart unless-stopped -p 8080:80 ghcr.io/corentinth/it-tools:latest
```

**其他方案：**

- [Cloudron](https://www.cloudron.io/store/tech.ittools.cloudron.html)
- [Tipi](https://www.runtipi.io/docs/apps-available)
- [Unraid](https://unraid.net/community/apps?q=it-tools)

## 贡献

### 推荐的 IDE 配置

推荐使用 [VSCode](https://code.visualstudio.com/) 并安装以下扩展：

- [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar)（并禁用 Vetur）
- [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin)
- [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
- [i18n Ally](https://marketplace.visualstudio.com/items?itemName=lokalise.i18n-ally)

建议使用以下设置：

```json
{
  "editor.formatOnSave": false,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  },
  "i18n-ally.localesPaths": ["locales", "src/tools/*/locales"],
  "i18n-ally.keystyle": "nested"
}
```

### TypeScript 中 `.vue` 导入的类型支持

TypeScript 默认无法处理 `.vue` 导入的类型信息，因此我们使用 `vue-tsc` 替代 `tsc` CLI 来进行类型检查。在编辑器中，需要安装 [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin)，让 TypeScript 语言服务能够识别 `.vue` 类型。

如果你觉得独立的 TypeScript 插件速度不够快，Volar 还实现了性能更好的 [Take Over Mode](https://github.com/johnsoncodehk/volar/discussions/471#discussioncomment-1361669)。可以按以下步骤启用：

1. 禁用内置的 TypeScript 扩展
   1. 在 VSCode 命令面板中运行 `Extensions: Show Built-in Extensions`
   2. 找到 `TypeScript and JavaScript Language Features`，右键并选择 `Disable (Workspace)`
2. 在命令面板中运行 `Developer: Reload Window`，重新加载 VSCode 窗口。

### 项目初始化

```sh
pnpm install
```

### 开发环境编译与热重载

```sh
pnpm dev
```

### 生产环境类型检查、编译与压缩

```sh
pnpm build
```

### 使用 [Vitest](https://vitest.dev/) 运行单元测试

```sh
pnpm test
```

### 使用 [ESLint](https://eslint.org/) 进行代码检查

```sh
pnpm lint
```

### 创建新工具

如需创建新工具，可以运行脚本来生成新工具的样板代码：

```sh
pnpm run script:create:tool my-tool-name
```

它会在 `src/tools` 中创建包含正确文件的目录，并在 `src/tools/index.ts` 中添加导入。你只需要把导入的工具添加到合适的分类中，然后开发该工具即可。


## 声明

本项目来自[CorentinTh](https://github.com/CorentinTh/it-tools)，本人作为开发小白，抱着学习态度，想把项目复现以及增加新功能在自己的站点，感谢原作者的分享