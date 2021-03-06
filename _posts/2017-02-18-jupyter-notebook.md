---
layout: post
title: Jupyter notebook
date: 2017-02-18 06:00:54
categories: Programming
tags: Python Jupyter notebook 科学作图   
excerpt: "这篇文章简单介绍 Jupyter notebook 作为 interactive shell 和 浏览器 IDE 在基于 Python 的科学作图方面的应用."
---

* content
{:toc}

## Jupyter notebook (former IPython notebook)

关于 [Project Jupyter](http://jupyter.org/) 的历史我也不甚了解, 简单来说, Python 作为一种解释性语言, 从其自带的 command line 解释器 (interactive shell) 我们就可以看出, Python 具有迅速执行少量代码的强大功能, 甚至可以一定程度上替代 shell script (是的, windows 我黑的就是你...Python脚本的优点是很大程度跨平台, 不用单独记多套 shell script).

但是, Python 自带的解释器在改写成代码或者存储变量复用方面还是有很多欠缺之处(可能当初谁也没想到解释器可以开发出这么多种用法...) 于是就有了 [IPython](https://ipython.org/), 目的是增强 Python 的 interactive shell. 而 Jupyter notebook 则是将这个 shell 整合到浏览器之中, 也就是说, 浏览器成为了我们交互的 shell / IDE, 这就是传说中的浏览器编程的一种 Python 实现了.

那么, notebook 与源码相比, 有什么优势呢?

关键就在于 **交互**.

交互性的代码可以让编程者随时观察自己代码的运行效果:

- 比如使用了 df.dropna(), 是否成功了? 打个 df.shape 看看变没变就好了; 
- 又如图上的各种 label 位置和尺寸, 完全不需要思考, 先画出来, 再根据实际的显示情况调整参数, 比盲人摸象般的设计(猜测)更容易上手.

## Jupyter notebook 在科学计算等领域的应用

Jupyter notebook 的实现本质是一个大的 json 文件. 因此它容易被分享, 即可以在线先浏览大致的效果, 也可以在不同的电脑上随时运行, 甚至还可以在线运行.

因此, Jupyter notebook 一定程度上取代了源码, 成为 Python 科学应用领域(包括科学计算, 科学作图, 统计模型, 以及现在大热的机器学习)等领域的分享媒介. GitHub 及很多 notebook 分享网站也进一步拓展了 Jupyter 的分享范围.

具体到科学计算和科学作图领域, numpy, scipy, pandas, statmodel, matplotlib 等主要的库都可与 Jupyter notebook 良好兼容. 基本上开箱即用.

更重要的是, 很多人分享了他们的一些典型应用过程. 如 numpy 的各种 slice 手法, 用一个 notebook 展示是一种非常有效的形态:

- 一方面, 每个命令的意义很清晰, 读者可以单独执行; 
- 另一方面, notebook 中的代码可运行, 因此读者还可以在本地调整参数, 看看参数改了之后会是什么效果.

notebook在分享方面的这两个特点, 一方面可以使教学者把知识"掰开了揉碎了"传给读者, 另一方面也使读者便于举一反三. 考虑到全世界的难以计数的学习者, 这种学习方法的改进真是让人激动不已.

## Windows 7 下部署 Jupyter notebook

不幸的是, Windows 环境下的软件安装一直是个老大难问题. 不过在科学计算领域, 也有 [Anaconda](https://www.continuum.io/downloads) 等集成好所有常见库的 exe 包可供使用, 推荐小白采用. 从 pip 安装时, 可能会遇到 numpy, scipy 等库编译失败的情况, 此时可搜索在线的一些预编译包, 使用 `.whl` 文件安装.

部署 Jupyter notebook 之后, 还可使用一系列的插件提高浏览器环境的工作手感.

nbextensions 中提供了 zenmode, [vimbinding](https://github.com/lambdalisue/jupyter-vim-binding) 等插件, 由于个人最近爱上了 Vim, 自然也就体验了一把 vimbinding 提升手速的感觉.

VIM binding 作为 Jupyter notebook 的一个插件, 改变了其操作模式:

- Jupyter notebook 在默认状态下有两种模式, 一种是输入模式(cell 左端绿色), 一种是命令模式(cell 左端蓝色), 类似于 Vim 的 insert 和 normal mode.
- 而在 Vim binding 下, 两种模式的命令都有一定调整, 更贴近 Vim 的两种模式. 同时也加入了 visual mode, 并保留了 Jupyter normal mode (不推荐使用, 特意把切换快捷键改成了 Shift+Esc)

实际体验下来, 诸如 dypcg$0aoir. 等基本操作基本正常, 可能由于浏览器的原因存在一些bug, 比如 `.` 命令似乎不能识别输入的方向键, 在用方向键调整括号中输入位置的时候有bug.

一个比较大的不便是系统剪切板不能访问. 这个对多 notebook 时候的操作稍有影响, 只能通过系统自带命令访问剪贴板, 然后进入 insert 命令再用粘贴.

## 更进一步的想象: 可视化雕琢代码的过程

interactive shell 的想象空间非常巨大.

有时候, 我们编写代码的过程比较像雕塑家打造一件作品的过程. 我们先选择材料, 再大致搭出代码的逻辑主体, 最后雕琢代码细节, 使其成为完整的一件作品.

Jupyter notebook 完全可以记录这个过程. 这种记录对于编程学习者可能是一种最有效的帮助. 

编程的代码是最终的产品, 但从这个产品中, 我们很难看出原作者雕琢它的过程(如同我们不能看出雕塑的过程). 此时, 就像那幅经典的画马图一样, 我们会进入完全不明觉厉的状态然后弃疗.

而在 notebook 中, 作者完全可以像录视频一样展现他/她思考的全过程: 

- 这里先写个带 bug 的凑合用下, 最后再调; 
- 那里的 magic number 其实可能是一个一个数字试出来的; 
- 最后的测试怎么写用例效率比较高.

这些过程中的细节, 就成为了代码大厦的导航图, 让学习者理解作者的思路, 仿佛人在身边一般. 而在技术的不断发展下, 以 notebook 为载体, 这种高质量的教学方式需要的成本又十分有限, 只是一个 json 文件, 比起视频来说环保了很多(视频最大的遗憾是不可交互运行. 视频+notebook 我觉得是最完美的解决方案).

我相信, 这样的创造会让世界更美好.

此外, Jupyter notebook 在浏览器中的架构, 便于架设基于浏览器的 server, 提供相关在线服务. 也可以成为一种把代码转化成黑箱服务的思路. 只需要在服务器部署代码库, 然后通过浏览器直接 i/o 最终产品, 减少了用户配置代码的困难. 此外也可以保护解释性语言的源码.

## 夹杂的一点吐槽和待修的 bugs

Jupyter 的版本管理是一团糟...一个大 json 用 Git 管理会崩掉的.. diff 会很乱

更大的问题是网页 IDE 完全没集成版本管理. 只能有一个 checkpoint 的设定对于用户也太不友好了, 这年头 Word 都有自动保存...目前这个实在是不太行...也看到有人给出了解决方案 [IPython Notebook Multiple Checkpoints - Stack Overflow](http://stackoverflow.com/questions/19142465/ipython-notebook-multiple-checkpoints).