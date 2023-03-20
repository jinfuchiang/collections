## 内存系统
- [内存管理系统辞典](https://www.memorymanagement.org/)
## 网络
### TCP
- [tcpdump抓包、WireShark分析TCP协议](https://zhuanlan.zhihu.com/p/142665708)
- [MSS 设定方法](https://medium.com/fcamels-notes/tcp-maximum-segment-size-%E6%98%AF%E4%BB%80%E9%BA%BC%E4%BB%A5%E5%8F%8A%E6%98%AF%E5%A6%82%E4%BD%95%E6%B1%BA%E5%AE%9A%E7%9A%84-b5fd9005702e)
- [SYN cookie](https://www.youtube.com/watch?v=sLbihU82x7s)
### HTTP
- [使用 Fiddler 和 Chrome F12 调试网站](https://www.youtube.com/watch?v=QxKHi1wFBfc)
## Paper
### 系统
- [AddressSanitizer: A Fast Address Sanity Checker](https://www.usenix.org/conference/atc12/technical-sessions/presentation/serebryany)
### 攻击
- [Cache Games – Bringing Access-Based Cache Attacks on AES to Practice](https://ieeexplore.ieee.org/document/5958048/) 利用
 Linux CFS 展开的攻击
## 他山之石
- <a href = "https://github.com/huangrt01/CS-Notes">包含 CUDA、3 pieces、cs144 笔记 </a>
- <a href = "https://www.cnblogs.com/kangyupl/p/stanford_cs144_labs.html">cs144 笔记</a>
- <a href = "https://kiprey.github.io/tags/CS144/">cs144 笔记</a>
- <a href = "https://www.zhihu.com/people/xing-xing-14-99-67/posts">Linux、系统、性能笔记 -- by 阿里混合云勿飞</a>
- [朴素linux--C和Linux底层知识](https://github.com/1184893257/simplelinux)
## Online Source Code
- <a href = "https://elixir.bootlin.com/linux/latest/source">linux, glibc ...</a>
## GCC
- <a href = "https://wizardforcel.gitbooks.io/100-gcc-tips/content/inhibit-linemarkers.html">Inhibit generation of linemarkers</a>
- [内联汇编各种标识的含义](https://github.com/1184893257/simplelinux/blob/master/inlineasm.md)
## Barrier
- <a href = "https://stackoverflow.com/questions/15491751/real-life-use-cases-of-barriers-dsb-dmb-isb-in-arm">many useful link</a>
## 逆向
<a href = "https://godbolt.org/">高级语言2汇编</a>
## 操作系统
### I/O
- [I/O 复用 demo](https://devarea.com/linux-io-multiplexing-select-vs-poll-vs-epoll/)
### Linux
- [Linux 主题大全](http://www.haifux.org/)
- [LDD（Linux Device Drivers）伴读](https://redirect.cs.umbc.edu/~jtang/archives/cs421.f19/schedule.html)
#### Ubuntu
##### AppImage
- [将 AppImage 文件添加为应用及设置默认打开方式](https://www.jianshu.com/p/ed3c35b8dcda)
- [提取 APPImage 中的 Icon（见评论区）](https://zhuanlan.zhihu.com/p/215507075)
### Arm
#### assembler
- <a href = "http://shell-storm.org/online/Online-Assembler-and-Disassembler/">汇编2转义字符串</a>
- <a href = "http://shell-storm.org/online/Online-Assembler-and-Disassembler/">汇编2Python</a>
- <a href = "http://armconverter.com">汇编2hex</a>
#### disassembler
- <a href = "https://onlinedisassembler.com/odaweb/">hex2assembly</a>
## Markdown
- <a href = "https://www.markdownguide.org/basic-syntax">Markdown Guide</a>
- [Markdown表格生成](https://www.tablesgenerator.com/markdown_tables)
## 数据库
- MySQL运维内参（群友推荐：InnoDB、较抽象）
- 是否应该使用MMAP作为数据库的buffer pool
  - 正方：<a href = "https://db.cs.cmu.edu/mmap-cidr2022/">Are You Sure You Want to Use MMAP in Your Database Management System?</a>
  - 反方：
    - <a href = "https://ravendb.net/articles/re-are-you-sure-you-want-to-use-mmap-in-your-database-management-system">re: Are You Sure You Want to Use MMAP in Your Database Management System?</a> 
    - <a href = "https://www.modb.pro/db/381185">译文</a>
## 编译
- <a href = "https://www.youtube.com/watch?v=aZbVvl_eeMA">编译器行业闲聊</a>
- <a href = "https://defuse.ca/online-x86-assembler.htm">x86/x64在线汇编/反汇编器</a>
- <a href = "https://regex101.com/">正则在线+速查</a>
### [Python AST ecosystem](https://github.com/hchasestevens/europython-2018/blob/master/exploring-ast-ecosystem.ipynb)
##### Documentation
- [Green Tree Snakes - the missing Python AST docs](https://greentreesnakes.readthedocs.io/en/latest/)
##### Visualization
- [python-ast-explorer - a simple AST Web visualizer](https://github.com/maligree/python-ast-explorer)
- [showast - An IPython/Jupyter notebook plugin for visualizing abstract syntax trees](https://github.com/hchasestevens/show_ast)
##### Static analysis
- [astor - AST observe/rewrite](https://github.com/berkerpeksag/astor)
- [astpath - A command-line search utility for Python ASTs using XPath syntax](https://github.com/hchasestevens/show_ast)
- [ASTsearch - an intelligent search tool for Python code](https://github.com/hchasestevens/show_ast)
##### Linting
- [bellybutton - Custom Python linting through AST expressions](https://github.com/hchasestevens/bellybutton)
##### DSLs
- [Pony - translate generators and lambda to SQL queries](https://github.com/ponyorm/pony)
- [xpyth - translate comprehension syntax to XPath](https://github.com/hchasestevens/xpyth)
- [Cosmic Ray: mutation testing for Python](https://github.com/sixty-north/cosmic-ray)
#### Application
https://github.com/hchasestevens/asttools
- [https://github.com/ponyorm/pony]()
https://github.com/hchasestevens/xpyth
https://github.com/sixty-north/cosmic-ray

## 编程实践
- [使用rdtsc的注意事项](https://stackoverflow.com/questions/19941588/negative-clock-cycle-measurements-with-back-to-back-rdtsc)
## ABI
- <a href = "https://stackoverflow.com/questions/18133812/where-is-the-x86-64-system-v-abi-documented">x86-64 ABI</a>
## C语言
- <a href = "http://git.musl-libc.org/cgit/musl/plain/src/setjmp/">异常实现</a>
- [https://stackoverflow.com/a/14643530](长度为 0 的数组)
## C++
- <a href = "https://www.luogu.com.cn/blog/AccRobin/grammar-candies">现代C++语法糖</a>
- <a href = "https://github.com/Cpp-Club/Cxx_HOPL4_zh">现代C++白皮书 -- Bjarne Stroustrup 著 吴咏炜、杨文波、张云潮 等 译</a>
- [C++比较器写法大全](https://jimmy-shen.medium.com/customize-comparison-in-c-fa48c0eac6d8)
- [C++单例模式](https://stackoverflow.com/a/1008289)
- [C++内存区域](https://stackoverflow.com/a/10157210)
## Debug
### 多线程调试
- <a href = "https://www.cnblogs.com/ralphjzhang/archive/2011/12/03/2274013.html">死锁判定</a>
- <a href = "https://stackoverflow.com/questions/18391808/how-do-i-get-the-backtrace-for-all-the-threads-in-gdb">打印所有线程的backtrace</a>
### Core Dump
- <a href = "https://wiki.archlinux.org/title/Core_dump">archlinux wiki</a>
## 公开课
- <a href = "https://github.com/awesome-cs-community/Awsome-Courses">合集1</a>
- <a href = "https://github.com/jackwener/CS-Awesome-Courses">合集2</a>
- <a href = "http://learn.lianglianglee.com/">专栏</a>
- <a href ="https://compilers.cool">编译原理</a>
### xv6
- [实验文档翻译+lab实况](http://xv6.dgs.zone/)
- [6.S081翻译](https://mit-public-courses-cn-translatio.gitbook.io/mit6-s081/)
## 书
- [ebook collection](https://soft.ryana.cn/)
## 软技能
- <a href = "https://www.codedump.info/post/20220304-weekly-8/">配图</a>
- <a href = "https://github.com/sparanoid/chinese-copywriting-guidelines">排版</a>
### 作图
- [draw.io插件：画数据流图、威胁模型图](https://github.com/michenriksen/drawio-threatmodeling)
- [draw.io插件：画数学函数图像](https://github.com/OrangeX4/drawio-function-plot-plugin)
- [Excalidraw 手绘风格作图](https://excalidraw.com/)
- [文本生成流程图](https://flowchart.fun/)
- [作图软件清单](https://www.zhihu.com/column/c_1479506700219150337)
## 数学
- <a href = "https://zhuanlan.zhihu.com/p/60964047">Catalan数</a>
- [重复/不可重复组合/排列](https://www.shuxuele.com/combinatorics/combinations-permutations.html)
- [leetcode中的算法](https://zhuanlan.zhihu.com/p/342610561)
## 搜索引擎
- <a href = "toutiao.io">技术文章整合</a>
## 浮点数
- <a href = "https://0.30000000000000004.com/">各语言浮点数运算行为鉴赏</a>
## 状态机
- <a href = "https://github.com/statelyai/xstate">JavaScript构建状态机和画状态图</a>
## 数据结构
- [线段树](https://codeforces.com/blog/entry/18051)
## 安全
- [如何隐藏IP](https://educatedguesswork.org/posts/traffic-relaying/)
- [软件安全学习资源集合](https://github.com/CHYbeta/Web-Security-Learning)
- [Web安全学习资源集合](https://github.com/CHYbeta/Web-Security-Learning)
## 面试
### 简历
- [用draw.io画的简历模板](https://github.com/Zilize/DrawCV)
### 经验分享
- <a href = "https://liuzhenglai.com/post/625131eda6983941cca711cc">海外面试向</a>
### TW
- <a href = "https://www.nowcoder.com/discuss/544951">无人机规划题</a>
- <a href = "https://www.nowcoder.com/discuss/5845">购物车题</a>
## AIGC
### 高效使用 
- [文本生成prompts集合](https://prompts.chat/)
- [又一个文本prompts提示集合](https://quickref.me/chatgpt)
- [prompts课程](https://learnprompting.org/)

## 行业报告
- [北京思集智库行业报告聚合](http://www.199it.com/)
