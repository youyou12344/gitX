## 安装公共 gitB
测试在 gitX 中安装公共库 gitB 。
### `坑` 远程仓库拉取失败
问题: git+https://github.com/youyou12344/gitB 安装不动，卡在如下：
``` shell
  "dependencies": {
    "gitB": "git+https://github.com/youyou12344/gitB"
  },
```
``` shell
npm install

# 卡住
idealTree:gitX: sill idealTree buildDeps
```
怀疑是 github 的问题，尝试换源：

1、 https://hub.fastgit.org/youyou12344/gitB 报错 503

2、 https://r.cnpmjs.org/youyou12344/gitB 报错 404

3、尝试本地 gitB 项目启动服务，使用本地地址 http://192.168.31.234:8080 ，报错
``` shell
npm ERR! code 128
npm ERR! An unknown git error occurred
npm ERR! command git --no-replace-objects ls-remote http://169.254.24.92:8080
npm ERR! fatal: 仓库 'http://169.254.24.92:8080/' 未找到

npm ERR! A complete log of this run can be found in:
npm ERR!     /Users/lijing/.npm/_logs/2022-06-12T08_41_24_111Z-debug.log
```

4、 https://e.coding.net/interval-yy/git/gitB.git
``` shell
# 成功！
added 1 package in 1s
```


## 安装私有 gitC
测试在 gitX 中安装私有库 gitC 。
``` shell
    "gitC": "git+https://e.coding.net/interval-yy/git/gitC.git",
```

嚯！居然正常安装了？？？


## 安装指定 tag
``` shell
    "gitC": "git+https://e.coding.net/interval-yy/git/gitC.git#2006121701",
    "gitC": "git+https://e.coding.net/interval-yy/git/gitC.git#220612",
```
问题: coding 的 tag 获取方式好像不是 #tagid 。


分析不同的 git 管理工具，对应的tag地址。
- github
  - 仓库: https://github.com/youyou12344/gitC.git
  - 仓库对应的 tag :  https://github.com/youyou12344/gitC/tree/2006121701
  - 仓库对应的 tag 包: https://github.com/youyou12344/gitC/releases/tag/2006121701 (打了tag自动生成)
- coding
  - 仓库: https://e.coding.net/interval-yy/git/gitC.git
  - 仓库对应的 tag : https://interval-yy.coding.net/p/git/d/gitC/git/tree/2006121701
  - 仓库对应的 tag 包: https://interval-yy.coding.net/p/git/d/gitC/git/releases/1 (需要手动发布版本)

*不知道怎么指定tag版本--2022/06/12*  

