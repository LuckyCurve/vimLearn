# Vim学习之路



### 移动操作

| 快捷键                      | 含义                                                         |
| --------------------------- | ------------------------------------------------------------ |
| `h`、`j`、`k`、`l`          | ←、↓、→、↑                                                   |
| `0(数字零)`、`^`、`$`、`g_` | 移动光标到行首、移动光标到行首【非空格】、移动光标到行尾、移动光标到行尾【非空格】 |
| `f{char}`、`F{char}`        | 查找行内下一个字符，查找行内上一个字符，`;`可重复执行当前命令，`,`操作回退 |
| `t{char}`、`T{char}`        | 查找行内下一个字符（光标落在当前字符前面）、查找行内上一个字符（光标落在后面） |
| `e`                         | move cursor to the end of the word                           |
| `w`                         | move cursor to the begining of the next word                 |
| `b`                         | move cursor to the begining of the previous word             |
|                             |                                                              |
|                             |                                                              |
|                             |                                                              |
|                             |                                                              |



### 修改指令

| 快捷键           | 含义                                                         |
| ---------------- | ------------------------------------------------------------ |
| `.`              | 重复上次修改（`i`操作被认为是整体的一次修改，重放会重放所有操作）【核心：一键移动一键修改】 |
| `x`              | 删除光标下的字符，并不进入插入模式，如果想删除字符并进入插入模式：`s` |
| `a`              | 当前光标后插入，等价于`i→`                                   |
| `A`              | 在当前光标行后插入，等价于`$a`                               |
| `o`              | 在当前行后插入一个新行                                       |
| `O`              | 在当前行前插入一个新行                                       |
| `>G`             | 增加从当前行到文本末尾的缩进层                               |
| `dd`             | 删除当前行，并将当前行保存至剪切板里                         |
| `p`              | 粘贴剪切板                                                   |
| `u`、`<C-r>`     | undo、redo                                                   |
| `*`              | 选中当前光标下的单词，相当于`/{string}`，也可用`n`、`N`来进行重复和回退操作 |
| `<C-a>`、`<C-x>` | 将当前数字加 number，将当前数字减 number，number 默认为1，默认找到当前行下一个顺位数字 |
| `daw`            | 删除一个单词                                                 |
| `dap`            | 删除一个段落                                                 |
|                  |                                                              |



### 操作符指令【后面需要跟随操作范围的修改指令】

| 快捷键     | 含义                                                         |
| ---------- | ------------------------------------------------------------ |
| `c`        | 修改操作，从当前字符开始。如`c$`，执行修改【从当前字符删除到行尾所有字符并插入】操作 |
| `d`        | 删除凑走                                                     |
| `y`        | 复制到寄存器                                                 |
| `g-`       | 大小写反转                                                   |
| `>`        | 增加缩进                                                     |
| `<`        | 减少缩进                                                     |
| `=`        | 自动缩进【基于上一行缩进】                                   |
| `gu`、`gU` | make text lower or upper case,`guaw`/`guap` operate a word or a graph |

**当一个操作符重复两次时，当前操作会用于当前行**，`gUgU`缩写成`gUU`，`>>`用于当前行锁进





### *等价复合操作总结*

| 复合操作   | 等价复合操作 | 含义                       |
| ---------- | ------------ | -------------------------- |
| `$a`       | `A`          | 在当前行末插入             |
| `c$`       | `C`          | 删除到行尾的所有字符并输出 |
| `cl`、`xi` | `s`          | 删除当前光标单词并插入     |
| `0c`       | `S`          | 删除行并插入               |
| `0i`       | `|`          | 在行首插入                 |
| `o`        | `A<CR>`      | 在当前行后插入一个空行     |
| `O`        | `ko`         | 在当前行前插入一个空行     |
|            |              |                            |





### 可重复执行的操作

| 命令                                       | 含义                                     | 重复 | 回退 |
| ------------------------------------------ | ---------------------------------------- | ---- | ---- |
| `{edit}`                                   | 执行修改【i、s、a进入编辑模式】          | `.`  | `u`  |
| `f{char}`、`F{char}`、`t{char}`、`T{char}` | 行内字符查找操作                         | `;`  | `,`  |
| `/pattern<CR>`、`?pattern<CR>`             | 全文字符串检索                           | `n`  | `N`  |
| `:s/source/target`                         | 完成行内字符串替换操作                   | `&`  | `u`  |
| `:%s/source/target`                        | 替换所有的 %  range means the whole file |      |      |
| `number <operation>`                       | 重复当前 operation number 次             |      |      |
|                                            |                                          |      |      |









