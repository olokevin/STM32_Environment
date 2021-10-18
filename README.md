# 嵌软组梯队培训第一次任务

准备开发环境，基本

## 准备开发环境

but在此之前...先掌握一些实用工具！

### Typora

* 官网安装Typora软件：轻量化的文本编辑器
* 学习Markdown语法(基本语法即可)
* 学会Typora的使用(其实也不是很需要学，界面实在是过于友好了)
  * 分级标题
  * 插入链接
  * 插入图片，表格，代码
  * 插入公式(需要了解LaTex公式编辑语法 用到了再学)
* 然后你就可以告别Word了

### Github

* [教程链接](https://www.liaoxuefeng.com/wiki/896043488029600)
* 需要掌握：
  * 本地创建版本库
  * 本地库与github远程库关联
  * 从github的库中clone代码
  * 提交代码(push)与获取代码(pull)
  * 版本回退
  * 创建分支与合并分支(可之后再学习)
  * 如何多人协作(可之后再学习)
* 用Typora撰写文档，记录实现以上操作的方法，以及你遇到的坑和解决办法
* 在github上创建自己的库，将学习文档同步到库中。这样你就有一个到处都能用的笔记本辣！
* 其实也不那么方便...github还经常登不上去(要梯子的私戳组长)
* 记笔记可以试试Office的OneNote，跨平台使用，实时同步

### 嵌入式开发环境

按照招新考核题中的需求，安装以下软件：

* Keil μVision MDK 
  * 官网搜索安装。如果下载较慢，可以试试 [下载链接](http://www.armbbs.cn/forum.php?mod=viewthread&tid=96992)
  * 安装v5.29版本(最新版本可能无法破解jlink驱动) 也可以尝试安装最新版本并自行研究破解方法
  * 安装后需破解
* Keil 芯片包
  * 官网搜索安装。如果下载较慢，可以试试 [下载链接](http://www.armbbs.cn/forum.php?mod=viewthread&tid=96992)
  * 需要安装STM32F0xx, STM32F1xx和STM32F4xx芯片包
  * 下载完成后，直接双击打开.pack文件，Keil会自动安装此芯片包
* STM32CubeMX
  * 官网下载即可，也可以上CSDN搜索安装配置教程
  * 注意会要求安装java。不要安装最新版本的java(可能不兼容)
  * 不要选择默认安装位置和软件包安装位置(建议改到D盘)
* Jlink驱动与破解，Jscope驱动

* 以上需要用到的安装包，破解程序都可以在这个github库里找到 [STM32_Environment](https://github.com/olokevin/STM32_Environment) 
* 用你新学会的github相关操作把他尻下来吧！

## 物资准备

一块STM32核心板+一根Jlink调试器

### STM32核心板

* 最便宜：F103C6T6 入门适用 建议选择带USB转串口，焊接好排针的 [购买链接](https://item.taobao.com/item.htm?spm=a1z0k.7385961.1997985097.d4918997.5f5f5b81lVhMyj&id=653818961902&_u=t2dmg8j26111)
* 推荐：F411CEU6 F4性能相较于F1提升很多 [购买链接](https://item.taobao.com/item.htm?spm=a230r.1.14.40.679e2342d73mw8&id=594670660262&ns=1&abbucket=19#detail)
* 狼牙同款：F405RGT6 和团队A板采用同款主控 还可以拿来玩micro-python [购买链接](https://item.taobao.com/item.htm?spm=a1z0k.7385961.1997985097.d4918997.5f5f5b81lVhMyj&id=570027048942&_u=t2dmg8j26111)
* 到胃：F407VET6/F407ZGT6 F4+大量外设资源 [购买链接](https://item.taobao.com/item.htm?id=537030227032&ali_refid=a3_430582_1006:1124961243:N:Qmyl3kynfp8L69LZxL%2Biz9G%2BajqCBn8a:3ef7e8ef7e02aa5793f1065d3455188c&ali_trackid=1_3ef7e8ef7e02aa5793f1065d3455188c&spm=a230r.1.14.6#detail)

### Jlink调试器

* [购买链接](https://item.taobao.com/item.htm?spm=a1z09.2.0.0.64882e8drwK5vT&id=587781660523&_u=h2029crc1jca95)

### 可选配件：

* USB转串口(如果购买的系统板上板载USB-TTL芯片可暂时不买，但建议配备一个)
* TFT-LCD显示屏(支持SPI驱动)
* 蓝牙模块 HC-05*2 主从机
* WiFi模块 ESP8266串口透传
* K210系统板 可以跑神经网络的国产单片机(STI提高题可以用到)
  * [购买链接](https://item.taobao.com/item.htm?spm=a1z0k.7385961.1997985097.d4918997.5f5f5b81lVhMyj&id=586580351110&_u=t2dmg8j26111)
  * [官方WiKi](https://wiki.sipeed.com/soft/maixpy/zh/get_started/get_started_power_on.html)，照着教程上手即可
  * [教程贴汇总](https://bbs.sipeed.com/thread/492) 上手后可以在社区找个小项目做

## 实操任务

### 单片机的“Hello World": 点灯

* 学习参考视频中关于GPIO口的部分，阅读参考书籍中GPIO相关章节
* 任务描述：使用CubeMX配置工程，在Keil IDE中编写代码与调试。使用最小系统板上自带的LED灯，让LED灯每隔一段固定时间有规律地自动改变一次状态。LED状态至少包括三种。
* 参考: LED等先以1s为周期交替点亮、熄灭，再每隔1s闪烁一次，再常亮5s，如此循环。鼓励自行设计LED状态
* 忠告：
  * 路径里不要有中文或中文符号！！！
  * 确认开发环境正常再开始
  * 充分阅读提供的资源再动手！很多常见问题我们已经为你准备好了教程，只是你自己没注意到orz
  * CubeMX里新建工程时需要与自己主控型号匹配
  * 引脚分配需要与原理图对应

完成过程中有任何问题，先尝试自己上网搜索解决，没有头绪可以发在群内讨论。

## 参考资源

### STM32 HAL库视频资源

* [STM32入门教程(基于HAL库+CubeMX+MDK-ARM)](https://www.bilibili.com/video/BV1y7411m7gg?p=1)
* [STM32系列视频(CubeMX+MDK5+HAL库+库函数一站式学习)](https://www.bilibili.com/video/BV1q4411d7RX?spm_id_from=333.999.0.0)

### 书籍教程：

自行下载与自己开发板型号配套的教程(F1系列 F4系列略有差别 同一系列内通用)

注意区分标准库与HAL库

* [正点原子资料下载站](http://www.openedv.com/docs/book-videos/zdyzbook/1stm32/index.html)
* [野火资料下载站](http://doc.embedfire.com/products/link/zh/latest/tutorial/ebf_stm32_hal_tutorial.html)
* 推荐：官方手册(User Manual/Reference Manual)
  * 英文，中文都有 可能初学入门不适合看 但之后建议多参考官方手册



Enjoy!