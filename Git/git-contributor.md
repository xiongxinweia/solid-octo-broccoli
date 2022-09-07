# 参与本项目

+ [**你需要学会使用markdown🖱️**](https://github.com/3293172751/CS_COURSE/blob/master/markdown/README.md)
+ [符合Google代码规范](https://zh-google-styleguide.readthedocs.io/en/latest/google-cpp-styleguide/)

### 谷歌代码规范

<img src="https://s2.loli.net/2022/07/05/E1GMeZO5A3kbK29.png" style="zoom:200%;" />



### 贡献步骤

步骤：

1. 首先在`Github`上`fork`本仓库到你的仓库
2. `git clone`克隆到本地
3. 在本地修改对应的代码
4. `git push`到自己的仓库
5. 在自己的仓库进行`pull request`的操作

`Github`会首先比较你仓库中的项目与目的项目的区别，并且会检查这两者之间是否可以进行合并操作

等了一会之后，`Github`提示`Able to merge`可以进行合并后，你就可以点击`Create pull request`了。

这里会让你填一个对你修改代码的一个说明，然后就可以真正的创建一个`pull request`了（点击这个`Create pull request`按钮）



### 我们希望什么样的request？

1. **优化已有代码或者文档**

![](https://s2.loli.net/2022/05/28/6rnRNubHeXAp54s.png)

2. **补充和分享项目笔记**
3. **修改错误的代码**
4. **给看不懂的地方一些补充和说明**

**push代码之前 一定要 先pull最新代码**，否则提交的pr可能会有删除其他push的操作。

一个pr 不要修改过多文件，因为一旦有一个 文件修改有问题，就不能合入，影响其他文件的合入了。

git add之前，要git diff 查看一下，本次提交所修改的代码是不是 自己修改的，是否 误删，或者误加的文件。

提交代码，不要使用git push -f 这种命令，要足够了解 -f 意味着什么。

不用非要写出牛逼的代码才能提交PR，只要发现文章中有任何问题，或者错别字，都欢迎提交PR，成为contributor。



**commit 时建议以 "contributor-name : subject"，比如 小明 : linux学习笔记。然后 push 上来，最后提交一个 pull request。**

```
git clone https://github.com/3293172751/Block_Chain.git
```

