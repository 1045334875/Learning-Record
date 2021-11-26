# VIM使用

#### 进入 

vim test.c

#### 退出

- :wq保存并退出
- :q! 强制退出

#### 三个主要模式

1. Normal Mode
   1. 进入Insert
      - 在下方插入一行：o
      - 上方插入一行：O
      - 光标前，后插入：i，a
      - 行前后插入：I,A
2. Insert Mode
   1. 按i, a, I, A进入
   2. Esc退出
3. Visual Mode选择编辑
   1. 按v, V, ctrl +v进入
   2. Esc退出

#### 光标移动

- ###### 上下左右：hjkl

- 第一行：gg

- 最后一行，指定行：G

- 下一个单词开头，结尾：w，e

- 行首：0

- 第一个非空字符：^

- 行尾：$

- 移动到变量定义（函数体内部第一次出现的地方）：gd

- 全局函数：gD

- 前一个没有匹配的左大括号出：[{

#### 复制粘贴

- 复制：y（yy整行复制）
- 粘贴：p

#### 撤回

- 撤销：u
- 重做：ctrl+r

#### 删除

- 剪切：d（删除整行：dd）
- 剪切字符：x
- 从当前字符删除到行尾：D

#### 更改

- 修改大小写：~

#### Composable

- 删除两个单词：dw(delete word)   d2w(delete 2words)  2dw(做两次删除单词)
- 4dd删除四行
- d4j会删除五行
- d4j

#### 搜索替换

- 搜索上一个：？(N)  
- 搜索下一个： /  (n)
- 当前单词：#（往前搜）  *（往后搜）

- 替换       :[range]s/from/to/[flags]
  - flags
    - g:匹配该行所有
    - i：大小写不敏感
  - 例子：   :%s/ext4/xxx所有行
  - :6s/ext4/xxx第六行
  - :.+5s/ext4/xxx从当前行开始到加五行替换

#### 宏

- 录制宏：q（按一下开始，按一下结束）
- 运行宏：1000@（重复执行1000遍）

#### 修饰词

- i：inner（dip删除一段）
- a：around（dap把该段落和旁边空行删完）
- t：till（dt；删到；）
- f：find

分隔

- sp上下分格
- vsp左右分格
- 移动Ctrl+w（hjkl)

#### 标记

生成标签：m

#### 注释

vim-commentary / nerdcommenter

安装插件：

下载到/root/vim/pack/vendor/start里面就可以了

```
mkdir -p -/.vim/pack/vendor/start
```

在一行前输入gcc可以注释改行

#### man in vim

:help

