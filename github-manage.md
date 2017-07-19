# Github 活动规范

## 命名

* 仓库名称
  
  单词全部小写，用短横线连接
* 仓库描述
  
  Topics 命名也是单词全部小写，用短横线连接

## 提交

**格式**

```
<type>(<scope>): <subject>

<body>

<footer>
```

**示例**

```
fix(middleware): ensure Range headers adhere more closely to RFC 2616

Add one new dependency, use `range-parser` (Express dependency) to compute
range. It is more well-tested in the wild.

Fixes #2310
```

**\<type\> 用于说明 commit 的类别，只允许以下 7 种标志**

* `feat` 新功能
* `fix` 修复 bug
* `docs` 修改了文档
* `style` 修改了格式（不影响代码运行的变动）
* `refactor` 重构（即不是新增功能，也不是修改 bug 的代码变动）
* `test` 增加测试（没有产品代码变动）
* `chore` 构建过程或辅助工具的变动

**\<scope\> 用于说明 commit 的影响范围，比如 init, runner, watcher, config, web-server, proxy, etc.**

* 如果 `<scope>` 难以确定或范围太大，则 `<scope>` 可以为空

**\<subject\> 是对 commit 目的的简短描述**

* 使用第一人称现在时（ 祈使句 ），比如 change，而不是 changed 或 changes
* 字母全部小写
* 不要超过 `50` 个字符
* 不要用 `句点` 结尾
* 如果只是修复了语法错误或者排版，可以写 `Grammar` 或 `Typo`

**\<body\> 是对 commit 目的的详细描述**

* 可以分成多行
* 使用第一人称现在时，比如 change，而不是 changed 或 changes
* 应该说明代码变动的动机，以及与以前行为的对比

**\<footer\> 部分只用于两种情况**

* 不兼容变动

  如果当前代码与上一个版本不兼容，则 Footer 部分以 BREAKING CHANGE 开头，后面是对变动的描述、以及变动理由和迁移方法。

  ```
  BREAKING CHANGE: isolate scope bindings definition has changed.

  To migrate the code follow the example below:

  Before:

  scope: {
    myAttr: 'attribute',
  }

  After:

  scope: {
    myAttr: '@',
  }

  The removed `inject` wasn't generaly useful for directives so there should be no code using it.
  ```
* 关闭 Issue

  如果当前 commit 针对某个 issue，那么可以在 Footer 部分关闭这个 issue 。

  ```
  Closes #234
  ```
  
  也可以一次关闭多个 issue

  ```
  Closes #123, #245, #992
  ```

**Revert**

还有一种特殊情况，如果当前 commit 用于撤销以前的 commit，则必须以 `revert:` 开头，后面跟着被撤销 Commit 的 Header。

```
revert: feat(pencil): add 'graphiteWidth' option

This reverts commit 667ecc1654a317a13331b17617d973392f415f02.
```

Body 部分的格式是固定的，必须写成 `This reverts commit <hash>.`，其中的 `<hash>` 是被撤销 commit 的 SHA 标识符。

如果当前 commit 与被撤销的 commit，在同一个发布（release）里面，那么它们都不会出现在 Change log 里面。如果两者在不同的发布，那么当前 commit，会出现在 Change log 的 `Reverts` 小标题下面

## 参考资料

[1] [karma-runner/git-commit-msg](http://karma-runner.github.io/1.0/dev/git-commit-msg.html)
[2] [viosey/hexo-theme-material/wiki/Commit-message-format](https://github.com/viosey/hexo-theme-material/wiki/Commit-message-format)