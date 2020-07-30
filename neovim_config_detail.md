## neovim配置说明

参考https://blog.csdn.net/qq_43497702/article/details/96485972

须知neovim的配置文件放在`~/.config/nvim/init.vim`，没有的话要新建



根据b站up主的视频https://www.bilibili.com/video/BV164411P7tw进行的初步配置



```shell
let mapleader=" "
syntax on
set number
set norelativenumber
set cursorline
set showcmd
set wildmenu

set hlsearch
exec "nohlsearch"
set incsearch
set ignorecase
set smartcase

noremap = nzz
noremap = Nzz
noremap <LEADER><CR> :nohlsearch<CR>
noremap P :split<CR> 
noremap V :vsplit<CR>
noremap i k      // 把k键映射到i键，光标上移
noremap k j      //如上
noremap j h      //如上
noremap I 5k     //如上
noremap K 5j     //如上

noremap h i      //如上
noremap H I      //如上

map s :<nop>     // map 命令是新定义hotkey
map S :w<CR>    // 
map Q :q<CR>
map R :source $MYVIMRC<CR>

call plug#begin('~/.vim/plugged')

Plug 'connorholyday/vim-snazzy'
Plug 'vim-airline/vim-airline'

call plug#end()

let g:SnazzyTransparent = 1
color snazzy
```



1. `noremap <LEADER><CR> :nohlsearch<CR>`

   在输入查找命令  `/ [搜索字符]`  后取消高亮用  `space`+`enter`

2. `noremap P :split<CR>`

   按  `shift`+`p`  实现左右分屏

3. `noremap V :vsplit<CR>`

   按  `shift`+`v`  实现上下分屏

4. ```
   noremap i k      // 把k键映射到i键，光标上移
   noremap k j      //如上
   noremap j h      //如上
   noremap I 5k     //如上
   noremap K 5j     //如上
   
   noremap h i      //如上
   noremap H I      //如上
   ```

   把   h左l右j下k上i插入  映射成  

   ![(E:\self_taught_lesson_include_python\EmbeddedSoftware\note\foto\01-3vim键位配置.png)](E:\self_taught_lesson_include_python\EmbeddedSoftware\note\foto\01-3vim键位配置.png)
   
   **并且：**
   
   * `shift` + `I`  --  向上移动5行
   * `shift` + `I`  --  向下移动5行
   
   
   
5. ```shell
   map s :<nop>     // map 命令是新定义hotkey
   map S :w<CR>    // 
   map Q :q<CR>
   map R :source $MYVIMRC<CR>
   ```

   * `s`  --  无操作（no operation）
   * `shift` + `s`  --  保存
   * `shift` + `q`  --  退出
   * `shift` + `r`  --  重载配置表



6. ```shell
   call plug#begin('~/.vim/plugged')
   
   Plug 'connorholyday/vim-snazzy'
   Plug 'vim-airline/vim-airline'
   
   call plug#end()
   let g:SnazzyTransparent = 1
   color snazzy
   ```

   call plug#begin('~/.vim/plugged')

   plug 'xxxxxxxxxxxxxxx'

   plug 'xxxxxxxxxxxxxxx'

   

   call plug#end()

   是指下载插件，这个操作需要先下载vim-plug，'xxxxxxxxxxx'呢是在github上找插件网页，比如snazzy的所在网页链接是

   [https://github.com/==connorholyday/vim-snazzy==](https://github.com/==connorholyday/vim-snazzy==)

   把黄色的部分复制到xxxxxxxxxxx

   **************

   无法在linux系统科学上网的情况下vim-plug的安装

   1. 在windows系统也就是主机系统，先在github下载plug.vim，然后把plug.vim拖拽到linux的任意文件夹，接着放在vim或者neovim对应的文件位置

      vim的话在：~/.vim/autoload/plug.vim 
   
      neovim的话在：/nvim/site/autoload/plug.vim
   
   *********
   
   ```shell
   let g:SnazzyTransparent = 1
   color snazzy
   ```
   
   把背景设成透明，启用snazzy配色
   
   
   
7. *vim本来的操作

   `h`  --  光标左插入

   `shift` + `h`  --  行首插入并编辑

   `a ` --  光标右插入

   `shift` + `a`  --  行尾插入并编辑

   `o`  --  向下新起一行并编辑

   `shfit` + `o`  --  向上新起一行并编辑

   `x`  -- 删除光标所在字符

   ********

   `d`删除复杂操作

   `d` + `<—`  --  删左边一个字符，光标的左边字符

   `d` + `—>`  --  删右边一个字符，光标字符  ==  `x`

   `d` + `3` + `—>`  --  删右边三个字符

   `d` + `d`  --  删整行

   

   在`d`命令后，再按`p`就是剪切

   比如 按 `d` + `d` 过后，再按`p`，就在光标所在位置粘贴

   ****

   `y`  复制复杂命令

   `y` + `<—`  --  复制左边一个字符，光标的左边字符

   `y` + `—>`  --  复制右边一个字符，光标字符

   `y` + `3` + `—>`  --  复制右边三个字符

   

   ****

   `p`  在光标行的下一行粘贴

   `shift` + `p`   在光标行的下一行粘贴在上一行

   ****

   要求：删除光标所在字符的整个字符并插入编辑

   `b` + `c` + `w`     ==    `c` + `h`(original `i`) + `w`

   

   ******

   对一对冒号内的字符进行操作的三个命令：

   1. 要求：删除冒号间 "qwewqeqe"  的字符并插入编辑

      `c` + `h` + `"`

   2. 要求：复制冒号间 "qwewqeqe"  的字符并插入编辑

      `y` + `h` + `"`

   3. 要求：剪切冒号间 "qwewqeqe"  的字符并插入编辑

      `d` + `h` + `"`

   

   ******

   `f`  查找单个字符复合命令

   1. 找到光标以后字母为  v  的第一个地方:

      `f` + `v`

   2. 从光标删除到冒号  :  

      `d` + `f` + `:`

   3. 从光标删除到冒号  :  

      `y` + `f` + `:`

   

   *******

   `/`  找一个单词

   1. 

      syntax: `/printf`   (不加空格)

      在敲回车后就可以移动光标

   2. 

   ```shell
   noremap <LEADER><CR> :nohlsearch<CR>
   ```

   ​	[空格键]   +    [回车键]    --    就会取消高亮注释

   3. 如果查找  `/printf`  右很多个的话，回车让光标可以移动,光标定位到下一个按  `n`  ，上一个按  `N`

   

   ***==最重要的撤销命令：==***

   **`u`**

   ********

8. *在vi编辑的时候，如何看当前文件路径：

   :!pwd

   

9. *在vi编辑的时候，如何看当前时间：

   :!date

   

10. *如何在vim中插入另外一个文件的全部内容：

    :r head.h

    ==【head.h必须先写好】==
    
    ****

11. 如何进入v-block模式？

    ==**按住  `ctrl` + `v`**==

    ![](E:\self_taught_lesson_include_python\EmbeddedSoftware\note\foto\03-1vblock模式.png)

    这个模式下可以连几句话敲击同样的语句，一起增删改查

    场景一：四行的开头语句都是  `map <LEADER>`

    空出四格后，进入V-BLOCK模式，在哪一行敲入`ctrl` + `v`，哪一行就是光标选中第一行（此时相当于按住鼠标左键），通过上下选中要操作的“行”

    方法一：然后敲入  `:normal` + `<command>`  ，`:normal hmap <LEADER>`

    方法二（推荐）：敲入  `shift` + `h` ， 再敲入 `map <LEADER>`



#### 12.***如何分屏查看两个文件？？？

1. 先分屏，分完屏后，敲入  `:e <filepath>`，将该文件路径下的文件展开到分屏下

   * `s` + `i`  向上分屏

   * `s` + `k`  向下分屏

   * `s` + `j`  向左分屏

   * `s` + `l`  向右分屏

2. 按  `space` + `i`，跳转到上屏

3. 按  `space` + `k`，跳转到下屏

4. 按  `space` + `j`，跳转到上屏

5. 按  `space` + `l`，跳转到下屏

```shell
map sl :set splitright<CR>:vsplit<CR>
map sj :set nosplitright<CR>:vsplit<CR>
map si :set nosplitbelow<CR>:split<CR>
map sk :set splitbelow<CR>:split<CR>

map <LEADER>l <C-w>l
map <LEADER>i <C-w>k
map <LEADER>j <C-w>h
map <LEADER>k <C-w>j
```



#### 13.想配置但是不敢配置的部分，原因是：还是会用到 ↑↓←→（上下左右） 键

```shell
map <up> :res +5<CR>
map <down> :res -5<CR>
map <left> :vertical resize-5<CR>
map <right> :vertical resize+5<CR>
```

**这里把  ↑↓←→（上下左右） 键  改成调整分屏大小的功能**



#### 14.***新插件的用途说明

* nerdtree--在vim旁边创建文件树
  * 要设置成按 `ff` 把文件树召唤出来
* YouCompleteMe--代码补全插件
  * 还需要在本地安装
* ale--错误提示
* tagbar--在右边显示函数列表
* mbbill--浏览修改历史
* markdown-preview--实时预览markdown格式



15.***在安装YCM出现的问题

1. 在  ./.vim/plugged/YouCompleteMe  文件下

   运行

   