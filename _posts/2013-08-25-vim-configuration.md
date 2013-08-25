---
layout: post
title: "Vim configuration file"
description: ""
category: "Programming"
tags: ["Vim"]
---

# Vim configuration file `~/.vimrc`

	set nocompatible "不要使用vi的键盘模式，而是vim自己的
	source $VIMRUNTIME/mswin.vim
	behave mswin	"兼容windows下的快捷键

	""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""" 
	" GVIM自身的设置
	"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
	language messages zh_CN.utf-8   " 解决consle输出乱码
	colorscheme desert              " 灰褐色主题
	set guioptions-=T		" 隐藏工具栏
	set guifont=Monaco:h10	        " 字体 && 字号
	set noerrorbells		" 关闭错误提示音
	set nobackup			" 不要备份文件
	set linespace=0			" 字符间插入的像素行数目
	set shortmess=atI		" 启动的时候不显示那个援助索马里儿童的提示
	set novisualbell		" 不要闪烁 
	set scrolloff=3			" 光标移动到buffer的顶部和底部时保持3行距离
	set mouse=a             " 可以在buffer的任何地方 ->
	set selection=exclusive         " 使用鼠标（类似office中 ->
	set selectmode=mouse,key        " 在工作区双击鼠标定位）
	set cursorline                  " 突出显示当前行
	set nu!   " 显示行号
	set whichwrap+=<,>,h,l		" 允许backspace和光标键跨越行边界 
	set completeopt=longest,menu    "按Ctrl+N进行代码补全

	""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""" 
	" 文本格式和排版 
	""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""" 
	set list                        " 显示Tab符，->
	set listchars=tab:\|\ ,         " 使用一高亮竖线代替
	set tabstop=4			" 制表符为4
	set autoindent			" 自动对齐（继承前一行的缩进方式）
	set smartindent			" 智能自动缩进（以c程序的方式）
	set softtabstop=4 
	set shiftwidth=4		" 换行时行间交错使用4个空格
	set noexpandtab			" 不要用空格代替制表符
	set cindent			" 使用C样式的缩进
	set smarttab			" 在行和段开始处使用制表符
	set nowrap			" 不要换行显示一行 

	 
	"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
	" 状态行(命令行)的显示
	"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
	set cmdheight=2		     " 命令行（在状态行下）的高度，默认为1，这里是2
	set ruler				 " 右下角显示光标位置的状态行
	set laststatus=2		 " 开启状态栏信息 
	set wildmenu		     " 增强模式中的命令行自动完成操作 


	"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
	" 文件相关
	"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
	set fenc=utf-8
	set encoding=utf-8		" 设置vim的工作编码为utf-8，如果源文件不是此编码，vim会进行转换后显示
	set fileencoding=utf-8		" 让vim新建文件和保存文件使用utf-8编码
	set fileencodings=utf-8,gbk,cp936,latin-1
	filetype on				     " 侦测文件类型
	filetype indent on			     " 针对不同的文件类型采用不同的缩进格式
	filetype plugin on			     " 针对不同的文件类型加载对应的插件
	syntax on				     " 语法高亮
	filetype plugin indent on    " 启用自动补全


	"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
	" 查找
	"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
	set hlsearch                 " 开启高亮显示结果
	set nowrapscan               " 搜索到文件两端时不重新搜索
	set incsearch                " 开启实时搜索功能


	"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
	" 语言的编译和运行           
	" 支持的语言：java	     F5编译(保存+编译)  F6运行
	"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
	func! CompileCode()
		exec "w"
		if &filetype == "java"
			exec "!javac -encoding utf-8 %"
		endif
	endfunc
	func! RunCode()
		if &filetype == "java"
			exec "!java -classpath %:h; %:t:r"
		endif
	endfunc
	 
	" F5 保存+编译
	map <F5> :call CompileCode()<CR>

	"  F6 运行
	map <F6> :call RunCode()<CR>


	"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
	" 实用功能
	"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
	"--------引号 && 括号自动匹配
	:inoremap ( ()<ESC>i
	:inoremap ) <c-r>=ClosePair(')')<CR>
	:inoremap { {}<ESC>i
	:inoremap } <c-r>=ClosePair('}')<CR>
	:inoremap [ []<ESC>i
	:inoremap ] <c-r>=ClosePair(']')<CR>
	":inoremap < <><ESC>i
	":inoremap > <c-r>=ClosePair('>')<CR>
	:inoremap " ""<ESC>i
	:inoremap ' ''<ESC>i
	:inoremap ` ``<ESC>i
	function ClosePair(char)
		if getline('.')[col('.') - 1] == a:char
			return "\<Right>"
		else
			return a:char
		endif
	endf
	"--------启用代码折叠，用空格键来开关折叠 
	set foldenable		     " 打开代码折叠
	set foldmethod=syntax        " 选择代码折叠类型
	set foldlevel=100            " 禁止自动折叠
	nnoremap <space> @=((foldclosed(line('.')) < 0) ? 'zc':'zo')<CR> 

	"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
	" 插件
	"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
	" <F9>打开文件浏览窗口   插件为WinManager
	let g:winManagerWindowLayout='FileExplorer'
	nmap <F9> :WMToggle<CR>

	" MiniBufExplorer     
	let g:miniBufExplMapWindowNavVim = 1 
	let g:miniBufExplMapWindowNavArrows = 1 
	let g:miniBufExplMapCTabSwitchBufs = 1 
	let g:miniBufExplModSelTarget = 1 
