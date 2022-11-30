# 下载包

```
npm install @check-121/private-module@1.0.0
```

```
"@check-121/private-module": "1.0.0"
```

# private-module

如何使用 Github 发布私有 NPM 包

1. 创建 Github 个人访问令牌
   Github 个人访问令牌页面， Settings / Developer settings / Personal access tokens

2. 使用 Github Registry 使用 NPM 进行身份验证

```
# 方法一：
npm login --scope=@OWNER --registry=https://npm.pkg.github.com
如：
npm login --scope=@check-121 --registry=https://npm.pkg.github.com


# 方法二：配置.npmrc 文件, 用来另一个项目下载 npm 包

@OWNER:registry=https://npm.pkg.github.com
//npm.pkg.github.com/:_authToken=${NPM_TOKEN}
```

3. 开始创建 npm 包

```
(1) npm init
{
  "name": "@check-121/private-module",
  "version": "1.0.0",
  "description": "An example package",
  "main": "index.js",
  ...
}

(2) 保存更改、提交并推送到 Github。

(3) 安装标准版本工具包， 它可以自动化版本控制以符合 semver 标准并基于Conventional Commits生成CHANGELOG.md。
npm install -D standard-version@latest

(4)配置 package.json
"scripts": {
    "release": "standard-version && git push --follow-tags && npm publish"
}

第一部分
# standard-version
添加所有新编辑的文件
使用我们项目的最新版本创建标签
使用我们最近的提交创建一个 changelod.md

第二部分
# git push –follow-tags
该部分将确保它将所有新创建的标签推送到当前提交

第三部分
# npm publish
将您最新版本的软件包发布到注册表

(5)发布npm包
npm run release
```

转载自：<https://blog.csdn.net/qq_20173195/article/details/126553769>
