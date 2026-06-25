# GitHub + Netlify 自动部署操作手册

目标：给提醒网页一个固定网址。以后修改页面设计或功能后，只要更新 GitHub，Netlify 自动同步到同一个网址。

## 你会用到的网址

- GitHub 官网：https://github.com/
- 注册 GitHub：https://github.com/signup
- 登录 GitHub：https://github.com/login
- 新建 GitHub 仓库：https://github.com/new
- Netlify 官网：https://www.netlify.com/
- Netlify 登录/注册：https://app.netlify.com/
- Netlify 新建站点入口：https://app.netlify.com/start
- Netlify Drop 临时拖拽部署：https://app.netlify.com/drop

## 第一步：准备网页文件

已经准备好的部署文件夹：

`/Users/cheer/Documents/Codex/2026-06-25/new-chat/outputs/reminder-web-deploy`

这个文件夹里最重要的是：

- `index.html`：提醒应用本体
- `README.md`：说明文档

上传到 GitHub 时，至少要上传 `index.html`。

## 第二步：创建 GitHub 仓库

1. 打开：https://github.com/new
2. 如果没有登录，先登录或注册。
3. Repository name 填：
   `reminder-web`
4. Description 可以填：
   `临时工作提醒网页`
5. 选择仓库可见性：
   - Public：公开，最省事。
   - Private：私有，也可以用 Netlify 部署，但授权时要允许 Netlify 访问。
6. 可以勾选 `Add a README file`，也可以不勾。
7. 点击 `Create repository`。

## 第三步：上传网页文件到 GitHub

进入刚创建的仓库后：

1. 点击 `Add file`。
2. 选择 `Upload files`。
3. 把下面这个文件拖进去：
   `/Users/cheer/Documents/Codex/2026-06-25/new-chat/outputs/reminder-web-deploy/index.html`
4. 如果你想把说明也放进去，也拖入：
   `/Users/cheer/Documents/Codex/2026-06-25/new-chat/outputs/reminder-web-deploy/README.md`
5. 页面底部会有提交说明，默认即可，或填：
   `Add reminder app`
6. 点击 `Commit changes`。

完成后，GitHub 仓库里应该能看到 `index.html`。

## 第四步：Netlify 绑定 GitHub 仓库

1. 打开：https://app.netlify.com/start
2. 登录或注册 Netlify。
3. 选择 `Import from Git` 或类似入口。
4. 选择 `GitHub`。
5. 第一次使用时，Netlify 会要求授权 GitHub。
6. 授权时选择你刚创建的仓库：`reminder-web`。
7. 进入部署设置页面后：
   - Branch to deploy：`main`
   - Base directory：留空
   - Build command：留空
   - Publish directory：留空或填 `.`
8. 点击 `Deploy` 或 `Deploy site`。

部署完成后，Netlify 会给你一个网址，例如：

`https://your-site-name.netlify.app`

这个就是你明天在办公室电脑可以打开的网址。

## 第五步：改成好记的网址名称

Netlify 默认网址通常是一串随机名字。你可以改成好记的：

1. 进入 Netlify 里的这个站点。
2. 找到 `Site configuration` 或 `Site settings`。
3. 找到 `Change site name`。
4. 改成类似：
   `cheer-reminder`
5. 保存后，网址会变成：
   `https://cheer-reminder.netlify.app`

如果这个名字被别人占用，就换一个。

## 以后怎么更新页面设计或功能

以后你想改设计、加功能，可以这样做：

1. 让 Codex 修改本地的 `index.html`。
2. 打开 GitHub 里的 `index.html`。
3. 点击右上角铅笔图标编辑。
4. 用新版本内容替换旧内容。
5. 点击 `Commit changes`。
6. Netlify 会自动重新部署。

通常几十秒到一两分钟后，同一个 Netlify 网址就会变成新版。

更省事的做法是以后用 GitHub Desktop 或命令行提交，但一开始用网页上传/编辑就够了。

## 关于提醒弹出

当前网页已经支持浏览器通知：

1. 用 Netlify 的 `https://...netlify.app` 网址打开。
2. 点击页面右上角“开启提醒”。
3. 浏览器弹出授权时选择允许。
4. 保持页面打开，到点会弹出通知。

注意：

- 只有填写了日期和时间的提醒会触发。
- 页面关闭后，纯静态网页不能保证继续提醒。
- 要做到页面关闭也提醒，需要加云端服务。

## 当前推荐路线

先完成：

GitHub 仓库 → Netlify 自动部署 → 获得固定网址

后续如果你确认这个小工具会长期用，再升级：

云端数据库 → 跨设备同步数据 → 后台定时提醒
