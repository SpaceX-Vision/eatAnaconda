# Anaconda 详解

更新日志：

**1.1** 2021.9.13 操作虚拟环境相关知识

## 为什么要使用 Anaconda？

1. Anaconda 附带了一大批常用数据科学包，它附带 Python 和 conda，还有 150 多个科学包及其依赖项，因此可以快速的进行科学开发。
2. 拥有 conda 包管理工具，和 pip 配合可以很方便的管理 Python 包。
3. 可以创建虚拟环境。

### 什么是虚拟环境？

举个例子，假设我是一名人工智能课和 Python 课的老师，人工智能课需要 Python3.7 环境，而 Python 课需要 Python3.6 环境，一台电脑很难让两种环境共存，并且会出现依赖紊乱的问题，那么怎么办呢？这就需要用到虚拟环境了。为两种课程创建两个不同的虚拟环境，并且这两个环境互相独立不受干扰，就可以完美的解决不同环境下的工作需求了。

## Anaconda 安装

**奶牛网盘已到期无法使用，请自行到官网下载对应自己操作系统的版本。**

~~从官网下载二进制文件贼慢，我已经下载好放到奶牛网盘了(交过钱了，不限速)，[点击下载 Anaconda](https://cowtransfer.com/s/57a74c23fe6345)~~

> PS：请下载对应自己操作系统的二进制文件。

下载完成后，macOS 用户请直接打开 pkg 跟着党(误)走，**Windows** 用户请注意⚠️：下载完二进制文件后请右键**以管理员身份运行**，切记！

安装时前面基本上都是点「Next」，但到下图这个步骤时一定要**把第一个复选框给勾上**！！！！不然后面很麻烦，切记！**「Add Anaconda3 to my PATH environment variable」一定要勾选！**这个选项是把 Anaconda 添加到系统的环境变量中，这样可以更方便的使用命令行而不是图形化的方式使用 Anaconda。

![截屏2021-02-16 下午3.04.10.png](https://res.craft.do/user/full/3d2e681a-7335-fb0a-0234-c0c4c265da20/doc/138EB6CF-E24B-451B-9B00-6A3CCEBF4863/56C250E7-9715-4F19-82CA-618AC04BDD88_2)

后面就一直「Next」就好了。

安装时请一定要记住你的 Anaconda 安装目录，接下来要用。

当安装器运行结束后，Windows 的 Anaconda 还是不可以用的，需要加一下系统环境变量，根据下图步骤打开 Windows 配置环境变量的界面(手边没 Windows 电脑网上找的图):

![截屏2021-02-16 下午3.04.37.png](https://res.craft.do/user/full/3d2e681a-7335-fb0a-0234-c0c4c265da20/doc/138EB6CF-E24B-451B-9B00-6A3CCEBF4863/E9788DA7-81A4-4E12-BD4E-C844C6D4ECE7_2)

在环境变量内添加上面红色框框内的**第二个 Scripts 值**，**注意⚠️：值为你的 Anaconda 安装目录，比如我把 Anaconda 安装到了 F 盘，那么应该添加 F:\Aanaconda\Scripts，同理安装到了 C 盘，那么应该添加 C:\Aanaconda\Scripts。**如果你上面在安装时没有勾选「Add Anaconda3 to my PATH environment variable」，那么接下来也是补救的机会，把红框框剩下两个变量加上就可以补救了。

此时打开终端(Windows 应该是 PowerShell)，在你的用户标示前应该有一个**(base),**输入  `conda -V`  如果打印出一行 conda 的版本号，那么恭喜你安装成功！🎉如果很不幸，出现了各种奇奇怪怪的错误，那么请检查上述安装步骤，重点检查环境变量，正确的安装应该会在环境变量内有三个 anaconda 相关的变量。

![截屏2021-02-16 上午10.25.00.png](https://res.craft.do/user/full/3d2e681a-7335-fb0a-0234-c0c4c265da20/doc/138EB6CF-E24B-451B-9B00-6A3CCEBF4863/12B92714-C42A-48FE-9BBE-E8E62C851DDC_2)

## conda 基本使用

🎉🎉🎉首先恭喜你成功安装了 Anaconda，那么接下来我们就要学习一下最基本的 conda 操作。

### 创建环境

你是一名 Python 老师，今天校长突然找到你，决定让你带一个人工智能的班级，上面提到过，两种不同课程班级的 Python 版本是不一样的，所以我们现在需要给人工智能班级创建一个虚拟环境，使用 conda 创建虚拟环境很简单，只需要在终端中输入：

```shell
conda create --name aiclass python=3
```

其中「aiclass」为本虚拟环境的环境名，自己起的，没有要求。后面「python=3」指定了本环境的 Python 版本为 3.x，即最新版的 python3。

按下回车，这时 conda 会自动检测依赖和询问我们是否要安装依赖包，我们输入 Y 或者再按下回车，conda 就会帮助我们安装依赖包和我们指定版本的 Python。

![截屏2021-02-16 上午10.47.31 1.png](https://res.craft.do/user/full/3d2e681a-7335-fb0a-0234-c0c4c265da20/doc/138EB6CF-E24B-451B-9B00-6A3CCEBF4863/E1A26489-036B-4E54-9BFF-8AE0E5E353E9_2)

安装完成后，会和上图差不多，此时我们的「aiclass」虚拟环境就创建好了。

### 激活环境

我们可以看到，在我们用户名标示的左边还是「base」环境，我们需要把当前终端切换到我们刚刚创建的「aiclass」环境，切换也非常简单，只需要输入：

```shell
conda activate aiclass
```

![截屏2021-02-16 上午10.51.25.png](https://res.craft.do/user/full/3d2e681a-7335-fb0a-0234-c0c4c265da20/doc/138EB6CF-E24B-451B-9B00-6A3CCEBF4863/B960723E-391B-4500-AFF3-99638BFEF48F_2)

这时左边已经显示我们进入了「aiclass」虚拟环境当中。

### 查看环境列表

在2077年大疆教育已经不只有人工智能和 Python 课程了，还有核弹制作、火星勘测等课程，显然我们要对每个课程建立一个虚拟环境，那么我们怎么查看我们建立了多少虚拟环境呢？也很简单，只需要输入：

```shell
conda info --env
```

![截屏2021-02-16 上午10.55.57.png](https://res.craft.do/user/full/3d2e681a-7335-fb0a-0234-c0c4c265da20/doc/138EB6CF-E24B-451B-9B00-6A3CCEBF4863/AC867537-57CE-4EC1-A1A2-6DD8786FE501_2)

可以看到 conda 给我们列出了当前计算机上的所有虚拟环境，中间有 * 标识的就是我们现在所处的虚拟环境。

### 通过 conda 安装包

上面我提到过，Anaconda 是有 conda 包管理工具的，所以极多的科学包可以通过 conda 安装，比如深度学习领域最火的 Tensorflow：

```shell
conda install tensorflow
```

### 通过 pip 安装包

Python 最火的包管理工具那要当属 pip 了，明天你就要上课，人工智能课程需要使用 DJI 官方的 RoboMaster SDK，很遗憾 DJI 官方并没有提交到 conda，所以你是无法使用 conda 指令安装的，但是在 Anaconda 下也可以使用 pip 安装第三方包：

```shell
pip install robomaster
```

### 查看虚拟环境下的所有包

大熊老师在你的电脑上建了个虚拟环境，环境名字是：“daxiongzhenshuai”，你看到名字傻眼了，这个环境是用来干啥的？不用着急，我们只需要查看一下这个环境下的所有包就可以分析出这个环境是干嘛的了：

```shell
conda list
```

当你看到 `pyspider` 包的时候你恍然大悟，原来这个环境是大熊老师爬相亲网站的爬虫环境，向单身的大熊老师致敬。2333333333

### 删除环境

下午校长突然找到你，不让你带人工智能课程的那个班了，上午幸福来的太突然，下午意外也挺突然。此时你伤心欲绝，只好删掉好不容易创建的人工智能班虚拟环境，那么删除一个环境也很简单：

```shell
conda remove -n aiclass --all
```

![截屏2021-02-16 下午2.12.04.png](https://res.craft.do/user/full/3d2e681a-7335-fb0a-0234-c0c4c265da20/doc/138EB6CF-E24B-451B-9B00-6A3CCEBF4863/9D939579-9684-47C0-B23F-DF5F8D1C49E1_2)

但是好像并没有删除成功，你注意到左边显示我们还在「aiclass」环境中了吗？因为我们目前激活了「alclass」虚拟环境，相当于我们正在运行赛博朋克2077，此时我们去卸载赛博朋克2077是肯定不行的，因为他的主进程程序还在运行，这也是某些毒瘤软件你怎么也卸载不掉的原因，只要毒瘤软件保持运行，你就永远删不掉✌️所以想要删掉「aiclass」虚拟环境，就必须停止激活，很简单，我们换个虚拟环境激活就好咯，那么考验来了，你还记得怎么激活一个虚拟环境吗？来我们一起把当前环境激活为「base」环境。

![截屏2021-02-16 下午2.17.36.png](https://res.craft.do/user/full/3d2e681a-7335-fb0a-0234-c0c4c265da20/doc/138EB6CF-E24B-451B-9B00-6A3CCEBF4863/1EE8FA63-1715-4A68-9D7D-92EE6358D706_2)

这时我们再运行删除指令就可以删除「aiclass」了，但是 conda 为了防止大熊老师故意删你环境，保险起见删除前会再询问你一下，我们只需要按下回车即可，这时候我们再查询所有环境，发现「aiclass」已经人间蒸发了：

![截屏2021-02-16 下午2.21.19.png](https://res.craft.do/user/full/3d2e681a-7335-fb0a-0234-c0c4c265da20/doc/138EB6CF-E24B-451B-9B00-6A3CCEBF4863/6EFF3370-A658-4F03-A0D2-EBBA0397C94C_2)

## Anaconda 进阶

### 导出环境

终于，校区要更换一波硬件了！原先上课的电脑又丑又卡，更换后的电脑简直流畅的飞起！但是问题来了，之前上课创建的环境怎么转移到新的电脑上呢？其实非常简单，通过 conda 自带的导出环境功能即可完成，在**终端**运行以下代码：

```shell
conda env export > ~/environment.yaml
```

**export >** 后面的内容为你指定的保存目录，上面代码段保存到 macOS / Linux 系统当前用户目录下，**Windows 系统请更改为符合 Windows 系统的储存路径。**

### 导入环境

当从旧电脑导出环境成功后，可以用 U 盘拷贝刚才导出的 environment.yaml 文件到新电脑中，在新电脑安装完 Anaconda 后可以在**终端**使用以下代码导入环境：

```shell
conda env create -f ~/environment.yaml
```

同样的，**create -f** 后面为拷贝到新电脑的 environment.yaml 文件位置，运行完毕后旧电脑上的环境就可以同步到新电脑咯！

## Anaconda 能干啥？

# TODO

## 总结

Anaconda 个人觉得非常非常非常好用，现在每次拿到新电脑必先装 Anaconda。当然因为 Anaconda 内置了大量的科学库，导致体积庞大，在意磁盘空间的小朋友可以选择 miniconda，没有内置科学库，使用起来和 Anaconda 一样的。

