#### Monorepo 代码组织思想  一个仓库管理所哟项目


Multirepo(传统repo项目)


#### lerna   一个管理工具  管理多个人软件包（package)  使用git  npm  管理多软件包仓库的工作流进行优化


```
git init name-project
    cd name-project
    lerna init

```
```
lerna publish
      version
      init  --independent/i  使用独立版本控制模式
      create  创建子项目    -y 默认初始化配置
      add  --scope   添加本地或者远程package作为当前项目里面的依赖
      bootstrap  安装各个子项目的声明的依赖 通过软连接处理子项目之间的关系依赖  --hoist 所有依赖安装到根目录达到共享
      clean   清除所有子项目的 node_modules 
      publish 
      run 
```



```
chainWebpack(config)=>{
    confog.module.rule("js").include.add("/packages").end().use("babel").loader("babel-loader").tap(options=>{
        return options
    })
}

```


###### error:0308010C:digital envelope routines::unsupported


```
# 👇️ macOS, Linux or Windows Git Bash
export NODE_OPTIONS=--openssl-legacy-provider

# ----------------------------------------------------

# 👇️ Windows CMD
set NODE_OPTIONS=--openssl-legacy-provider
npm install cross-env



{
  "scripts": {
    "dev": "cross-env NODE_OPTIONS=--openssl-legacy-provider next dev",
    "build": "cross-env NODE_OPTIONS=--openssl-legacy-provider next build && next export",
  }
}

```


yarn workspaces


## 以问答形式的提交
commitizen

cz-conventional-changelog   约定的版本log

![commit](https://github.com/commitizen/cz-cli/raw/master/meta/screenshots/add-commit.png)


- feat 新增一个功能
- fix  修复了一个bug
- docs  修改了文档 
- style 修改了样式 代码风格
- refactor 重构
- perf 性能 
- chore 改变了依赖
- revert 版本回退


####  约定提交格式校验

 @commitlint/cli
@commitlint/config-conventional
 husky  这里会有 git hooks

```bash
  npm set-script prpare "husky install"

  npm run prepare

  yarn husky add .husky/pre-commit 'yarn commitlint --edit "$1"'
  
  git add .husky/pre-commit
  ```
npm pkg set scripts.prepare="husky install"
npm run prepare
Add a hook:

npx husky add .husky/pre-commit "npm test"
git add .husky/pre-commit
Make a commit:

git commit -m "Keep calm and commit"
# `npm test` will run