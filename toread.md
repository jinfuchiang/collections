## 内存系统
- [内存管理系统辞典](https://www.memorymanagement.org/)
## 网络
### TCP
- [tcpdump抓包、WireShark分析TCP协议](https://zhuanlan.zhihu.com/p/142665708)
- [MSS 设定方法](https://medium.com/fcamels-notes/tcp-maximum-segment-size-%E6%98%AF%E4%BB%80%E9%BA%BC%E4%BB%A5%E5%8F%8A%E6%98%AF%E5%A6%82%E4%BD%95%E6%B1%BA%E5%AE%9A%E7%9A%84-b5fd9005702e)
- [SYN cookie](https://www.youtube.com/watch?v=sLbihU82x7s)
### HTTP
- [使用 Fiddler 和 Chrome F12 调试网站](https://www.youtube.com/watch?v=QxKHi1wFBfc)
### 监管
- [GET /out: Automated Discovery of Application-Layer Censorship Evasion Strategies](https://www.usenix.org/conference/usenixsecurity22/presentation/harrity)
- [How Great is the Great Firewall? Measuring China's DNS Censorship](https://www.usenix.org/conference/usenixsecurity21/presentation/hoang)
- [Many Roads Lead To Rome: How Packet Headers Influence DNS Censorship Measurement](https://www.usenix.org/system/files/sec22-bhaskar.pdf)
- [使用正确的DNS](https://gitlab.com/NekoInverter/EhViewer/-/issues/70)
#### Young Xu 的文章
- [可视化监管的影响](https://www.thousandeyes.com/blog/monitoring-dns-in-china)
- [早期监管技术解构](https://www.thousandeyes.com/blog/deconstructing-great-firewall-china)
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
- [李博杰博士--小故事好看](https://ring0.me)
- [初级工程师应读](https://dev.to/jeroendedauw/advice-for-junior-developers-30am)
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
- [手把手编译Linux源码](https://www.linuxfromscratch.org/)
- [ELF图解](https://commons.wikimedia.org/wiki/File:ELF_Executable_and_Linkable_Format_diagram_by_Ange_Albertini.png)
- [Linux文件系统层级标准（FHS)](https://refspecs.linuxfoundation.org/fhs.shtml)
#### Ubuntu
##### AppImage
- [将 AppImage 文件添加为应用及设置默认打开方式](https://www.jianshu.com/p/ed3c35b8dcda)
- [提取 APPImage 中的 Icon（见评论区）](https://zhuanlan.zhihu.com/p/215507075)
#### 配置
- [像专家一样配置个人服务器](https://github.com/erebe/personal-server)
#### 杂项
- [文件属性（创建一个root都不能删除的文件）](https://linuxize.com/post/chattr-command-in-linux/)
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
- [算法题的一些奇技淫巧（常规操作？）](https://www.zhihu.com/question/33776070)
- [SPOJ：多语言、问题分类友好型OJ](https://www.spoj.com/)
- [Adevnt of Code: puzzle，先易后难](https://adventofcode.com/)
- [用longjmp实现try-catch-finally](http://groups.di.unipi.it/~nids/docs/longjump_try_trow_catch.html)
- [why do-while(0):分号与花括号](https://stackoverflow.com/questions/257418/do-while-0-what-is-it-good-for)
- [函数编写指南](https://youtu.be/yatgY4NpZXE)
- [以语言、编译器、任务、库分类的时空能耗benchmark](https://github.com/kostya/benchmarks)
- [用高级语言特性替代设计模式](https://wiki.c2.com/?AreDesignPatternsMissingLanguageFeatures)
- [脱符号表unneeded和all选项对比](https://www.technovelty.org/linux/stripping-shared-libraries.html)
- [软件架构栈(理清设计模式、OOP、MVC、DDD等的关系层级)](https://www.freecodecamp.org/news/software-design/)
- [穿透NAT思路（木马通信）](https://security.tencent.com/index.php/blog/msg/193)
- [用CMOV使二分搜索branchless（Clang默认实现）](https://probablydance.com/2023/04/27/beautiful-branchless-binary-search/)
- [针对软件优化的硬件手册](https://www.agner.org/optimize/)
- [使用prefetch、ffs、Cache优化二分搜索(Eytzinger二分)](https://algorithmica.org/en/eytzinger)
- [在C中做单元测试](https://codeahoy.com/learn/cprogramming/ch46)
### tutorial
- [WebGPU入门](https://eliemichel.github.io/LearnWebGPU/)
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
- <a href = "https://www.cnblogs.com/ralphjzhang/archive/2011/12/03/2274013.html">死锁判定</a>
- <a href = "https://stackoverflow.com/questions/18391808/how-do-i-get-the-backtrace-for-all-the-threads-in-gdb">打印所有线程的backtrace</a>
- <a href = "https://wiki.archlinux.org/title/Core_dump">Coredump archlinux wiki</a>
- [Python C++ 混调](https://developer.nvidia.com/blog/debugging-mixed-python-and-c-language-stack/)
## 公开课
- <a href = "https://github.com/awesome-cs-community/Awsome-Courses">合集1</a>
- <a href = "https://github.com/jackwener/CS-Awesome-Courses">合集2</a>
- <a href = "http://learn.lianglianglee.com/">专栏</a>
- <a href ="https://compilers.cool">编译原理</a>
### xv6
- [实验文档翻译+lab实况](http://xv6.dgs.zone/)用前端和archive的方法绕过内容授权
- [6.S081翻译](https://mit-public-courses-cn-translatio.gitbook.io/mit6-s081/)
## 书
- [ebook collection](https://soft.ryana.cn/)
## 软技能
- <a href = "https://www.codedump.info/post/20220304-weekly-8/">配图（图片的结构）</a>
- [配色-文章](https://zhuanlan.zhihu.com/p/457797561)
- [配色灵感-视频](https://www.bilibili.com/video/BV1ZA4y1f75e)
- <a href = "https://github.com/sparanoid/chinese-copywriting-guidelines">排版</a>
- [入职](https://www.cnblogs.com/figure9/p/3563869.html)
- [Antirez关于10倍程序员的看法](http://antirez.com/news/112)
- [使用 Reveal.js 做交互式在线PPT的心得](https://zhuanlan.zhihu.com/p/83425852)
- [Erik Demaine的slide模板](https://zhuanlan.zhihu.com/p/403004001)
- [如何应对知识爆炸](https://security.tencent.com/index.php/blog/msg/155)
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
- [搜索引擎聚合](https://duckduckgo.com/bangs)
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
- [网络资产扫描](https://zhuanlan.zhihu.com/p/460403187)
- [用前端技巧绕过内容授权](https://bbarrows.com/posts/how-to-get-around-paywalls-with-debug-tools)
- [用archive方法绕过内容授权](https://news.ycombinator.com/item?id=34953693)
- [安全工具合集](https://offsec.tools/)
- [搜索引擎作渗透tutorial](https://cloud.tencent.com/developer/article/1918288)
- [Google渗透用法数据库](https://www.exploit-db.com/google-hacking-database)
## 面试
### 简历
- [用draw.io画的简历模板](https://github.com/Zilize/DrawCV)
### 经验分享
- <a href = "https://liuzhenglai.com/post/625131eda6983941cca711cc">海外面试向</a>
### TW
- <a href = "https://www.nowcoder.com/discuss/544951">无人机规划题</a>
- <a href = "https://www.nowcoder.com/discuss/5845">购物车题</a>
### Google
- [官方面试算法题教学](https://techdevguide.withgoogle.com/paths/interview/)
## AIGC
### 高效使用 
- [文本生成prompts集合](https://prompts.chat/)
- [又一个文本prompts提示集合](https://quickref.me/chatgpt)
- [prompts课程](https://learnprompting.org/)
- [prompt军火库](https://github.com/microsoft/semantic-kernel/blob/main/samples/skills/CodingSkill/CodePython/skprompt.txt)
- [prompts工程](https://zhuanlan.zhihu.com/p/616860260)
## 行业报告
- [北京思集智库行业报告聚合](http://www.199it.com/)
## 提问艺术
### [坎宁安定律](http://bash.org/?152037)
- [Linux社区案例](http://bash.org/?152037)
- [tmux社区案例](https://www.reddit.com/r/linuxquestions/comments/dzli6o/best_alternative_to_tmux/)
## 英语
- [过去式的深层含义-史蒂芬](https://www.zhihu.com/question/54639510)
- [吾鄙己心者凡七: (so) that 引导目的状语从句](https://www.zhihu.com/question/20773893)
## 安全
- [password cracker:John the Ripper](https://github.com/openwall/john)
- [GPU password cracker:John the Ripper](https://github.com/hashcat/hashcat)

