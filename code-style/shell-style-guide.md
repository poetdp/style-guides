# Shell 编写规范

## 注释

**头部**

```
#!/bin/bash
#
# 功能的简要概述
# 版权声明 & 作者信息 可选
```

**函数功能**

所有的函数注释应该包含：

- 函数的描述
- 全局变量的使用和修改
- 使用的参数说明
- 返回值，而不是上一条命令运行后默认的退出状态

```
#######################################
# Cleanup files from the backup dir
# Globals:
#   BACKUP_DIR
#   ORACLE_SID
# Arguments:
#   None
# Returns:
#   None
#######################################
function() {

}
```

**TODO**

```
# TODO(用户名): Handle the unlikely edge cases (bug ####)(bug / ticket 编号)
```

## 格式

**缩进**

缩进两空格，不使用制表符

**行的长度**

行的长度不超过 80 ，超过 80 的文字串想办法使其变短或合理地分割

```
# DO use 'here document's
cat <<END;
I am an exceptionally long
string.
END

# Embedded newlines are ok too
long_string="I am an exceptionally
  long string."
```

## 参考资料

[1] [google-shell-styleguide](http://zh-google-styleguide.readthedocs.io/en/latest/google-shell-styleguide)