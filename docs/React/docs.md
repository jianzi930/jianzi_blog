## React 脚手架（CLI）

- React 脚手架的介绍
- 使用 React 脚手架创建项目
- 项目目录结构调整

### React 脚手架的介绍

- 脚手架：为了保证各施工过程顺利进行而搭设的工作平台
- 对于前端项目开发来说，脚手架是为了保证前端项目开发过程顺利进行而搭设的开发平台
- 脚手架的意义：
  - 现代的前端开发日趋成熟，需要依赖于各种工具，比如，webpack、babel、eslint、sass/less/postcss等
  - 工具配置繁琐、重复，各项目之间的配置大同小异
  - 开发阶段、项目发布，配置不同
    - 项目开始前，帮你搭好架子，省去繁琐的 webpack 配置
    - 项目开发时，热更新、格式化代码、git 提交时自动校验代码格式等
    - 项目发布时，一键自动打包，包括：代码压缩、优化、按需加载等

### 使用 React 脚手架创建项目
- 命令：`npx create-react-app react-basic`
  - npx create-react-app 是固定命令，`create-react-app` 是 React 脚手架的名称
  - react-basic 表示项目名称，可以修改
- 启动项目：`yarn start` or `npm start` 
- `npx` 是 npm v5.2 版本新添加的命令，用来简化 npm 中工具包的使用
  - 原始：1 全局安装`npm i -g create-react-app` 2 在通过脚手架的命令来创建 React 项目
  - 现在：npx 调用最新的 create-react-app 直接创建 React 项目

### 项目目录结构说明和调整

- 说明：
  - `src` 目录是我们写代码进行项目开发的目录
  - 查看 `package.json` 两个核心库：`react`、`react-dom`（脚手架已经帮我们安装好，我们直接用即可）
- 调整：
  1. 删除 src 目录下的所有文件
  2. 创建 index.js 文件作为项目的入口文件，在这个文件中写 React 代码即可

## React 的基本使用