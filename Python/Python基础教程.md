# 搭建开发环境

## Python下载安装

进入Python官网的下载区，https://www.python.org/downloads/，目前最新是3.13.0版本

![image-20260530211944450](./Python基础教程.assets/image-20260530211944450.png)

双击下载下来的 python-3.13.0-amd64.exe（3.13版本是当前最新的（一般最新的刚出来先别用），更推荐3.11版本，兼容性强，点击下面的Windows就能找到）



<img src="./Python基础教程.assets/image-20241103221132709.png" alt="image-20241103221132709" style="zoom:50%;" />

<img src="./Python基础教程.assets/image-20241103221242820.png" alt="image-20241103221242820" style="zoom:50%;" />

这里默认下一步next即可（注意pip一定要勾选，因为要使用它下载别的包）

<img src="./Python基础教程.assets/image-20241103221550511.png" alt="image-20241103221550511" style="zoom:50%;" />

点击Browse修改Python安装位置，这里为 D:\Python，注意记住（能找到）这个位置，然后点击 Install，等待......

<img src="./Python基础教程.assets/image-20241103221840794.png" alt="image-20241103221840794" style="zoom:50%;" />

出现此页面，successful，点击close，Python安装完毕。



## PyCharm下载安装

PyCharm 是由 JetBrains 开发的一款功能强大的 Python 集成开发环境（IDE）。提供了丰富的工具和功能。

PyCharm 是一个非常适合 Python 开发者的 IDE，无论是初学者还是经验丰富的开发者都能从中受益。

强烈推荐 PyCharm 作为 Python 开发首选 IDE ！！！



进入官网，https://www.jetbrains.com.cn/pycharm/download/?section=windows



![image-20241103224033858](./Python基础教程.assets/image-20241103224033858.png)

注意，请下载专业版（Professional），选择Windows版本，下面也有社区版，是免费的，但是不支持远程开发，为此这里选择专业版，最新版本 2024.2.4

双击下载下来的 pycharm-professional-2024.2.4.exe

<img src="./Python基础教程.assets/image-20241103225058623.png" alt="image-20241103225058623" style="zoom:50%;" />

下一步

<img src="./Python基础教程.assets/image-20241103225227111.png" alt="image-20241103225227111" style="zoom:50%;" />

下一步

<img src="./Python基础教程.assets/image-20241103225344948.png" alt="image-20241103225344948" style="zoom:50%;" />

下一步

<img src="./Python基础教程.assets/image-20241103225406202.png" alt="image-20241103225406202" style="zoom:50%;" />

安装，等待......

<img src="./Python基础教程.assets/image-20241103225627877.png" alt="image-20241103225627877" style="zoom:50%;" />

完成



## 创建第一个项目并配置环境

### Windows本地项目开发

双击桌面Pycharm打开

会提示你激活，激活的办法这里不说明，请支持正版！！！，激活后先退出



开始创建项目，第一种方法，你可以进入Pycharm，左上角，文件，新建项目...

我选择第二种方法，你可以在某个位置新创建一个文件夹（假设为 FirstProject）作为项目文件夹，右击新创建的项目文件夹 FirstProject，显示更多选项（Win11才需要），Open Folder as PyCharm Project

注意，第一次使用Pycharm可能是英语界面，切换为中文界面

![image-20241103231542600](./Python基础教程.assets/image-20241103231542600.png)

点击左上角主菜单

![image-20241103231638518](./Python基础教程.assets/image-20241103231638518.png)

点击 File—Settings...——Plugins，可以搜索 Chinese (Simplified) Language Pack / 中文语言包，如果已经预先安装了，Enable即可，如果没有，先安装一下，最后重启 IDE 即可。



再打开项目

![image-20241103233015362](./Python基础教程.assets/image-20241103233015362.png)

关键！！！点击左下角配置解释器（没有解释器PyCharm就是个编辑器，无法执行Python程序）

![image-20241103233205295](./Python基础教程.assets/image-20241103233205295.png)

选择 添加新的解释器——添加本地解释器...

![image-20241103233528651](./Python基础教程.assets/image-20241103233528651.png)

选择 Virtualenv 环境——新建，填写位置和基础解释器，位置是虚拟环境（例如各种包）存放的位置，默认是在你当前项目文件夹下，基础解释器，选择之前我们下载Python存放的文件夹的python.exe，默认也是可以给你自动识别出来的，基本这两项都不用自己填，注意一些就行。

点击确定，左下角变为 Python 3.13 (FirstProject)，解释器配置成功，项目文件夹出现 .venv 文件夹存放包（即虚拟环境）

![image-20241103233922279](./Python基础教程.assets/image-20241103233922279.png)

下面做一个项目，正弦波可视化，需要安装 `numpy` 和 `matplotlib` 包。

我们在项目文件夹下新建一个Python文件，右击FirstProject——新建——Python文件，命名为first，我们写入两句导包代码

![image-20241103235517994](./Python基础教程.assets/image-20241103235517994.png)

发现 numpy、matplotlib 下面是红色波浪线，原因是没有下载此包（或者没找到包）

下面开始安装包，点击左下角终端按钮

![image-20241103235728746](./Python基础教程.assets/image-20241103235728746.png)

在光标闪烁处通过以下命令安装它们

```shell
pip install numpy
pip install matplotlib
```

⚠️注意，可以切换成国内的清华镜像源（也有其他的镜像源），速度更快，不切换可能速度非常墨迹，半天下不动

```shell
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple numpy
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple matplotlib
# 下载任何包都可以在前面加上 pip install -i https://pypi.tuna.tsinghua.edu.cn/simple
```

或者一起安装

```shell
pip install numpy matplotlib
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple numpy matplotlib
```

![image-20241103235909948](./Python基础教程.assets/image-20241103235909948.png)

然后你发现波浪线消失，说明包成功下载并导入，在 .venv 文件夹你可以发现 numpy、matplotlib 文件夹生成在这里了，.venv 文件夹就是来管理各种包的。

完成剩余的代码

```python
import numpy as np
import matplotlib.pyplot as plt

# 设置参数
frequency = 1  # 频率
sampling_rate = 100  # 采样率
duration = 2  # 持续时间（秒）

# 生成时间轴
t = np.linspace(0, duration, int(sampling_rate * duration), endpoint=False)

# 生成正弦波
y = np.sin(2 * np.pi * frequency * t)

# 绘制图形
plt.figure(figsize=(10, 4))
plt.plot(t, y, label='Sine Wave', color='b')
plt.title('Sine Wave')
plt.xlabel('Time [s]')
plt.ylabel('Amplitude')
plt.axhline(0, color='black', lw=0.5, ls='--')
plt.axvline(0, color='black', lw=0.5, ls='--')
plt.grid()
plt.legend()
plt.show()
```

点击右上角绿色的▷按钮，运行

![image-20241104000147378](./Python基础教程.assets/image-20241104000147378.png)

成功

如果你感兴趣，可以再创建一个项目，你会深刻感受到，当我们开始着手一个新的Python项目时，通常会涉及到使用多个第三方库，每个库可能需要特定的版本或依赖关系。同时，不同项目可能需要不同的Python版本。这时，虚拟环境就发挥了关键作用，我们让每个项目都单独使用各自的虚拟环境，这样可以更好地隔离项目之间的库，并避免全局Python环境的混乱。在虚拟环境中，你可以轻松地更新和卸载库，而不会影响其他项目。



### Linux远程项目开发

大多数情况，假设要把本地的项目（以之前 FirstProject 为例）放到Linux服务器上运行（例如 AI 模型训练等等）

你可以先在Linux适当位置创建一个文件夹管理你的项目，比如我创建了 /home/FirstProjectLinux（记住，等会要用）

首先，Linux服务器上需要安装 Python

更新软件包列表

```shell
sudo apt update
sudo apt upgrade
```

安装 Python 和 pip（一定要安装 pip，否则无法用pip安装其他的包）

```shell
sudo apt install python3
sudo apt install python3-pip
```

查看Python版本，我这里是 Python 3.10.12

```shell
python3 --version 
```

查看 Python 位置，我这里是 /usr/bin/python3，等会要用

```c++
which python3
```



打开FirstProject项目

点击右下角解释器——添加新的解释器——SSH...

<img src="./Python基础教程.assets/image-20241104103304482.png" alt="image-20241104103304482" style="zoom:50%;" />

填写自己Linux服务器的主机和用户名和端口号（没有让管理员帮你创建一个账户）

<img src="./Python基础教程.assets/image-20241104111325359.png" alt="image-20241104111325359" style="zoom:50%;" />

下一步，输入密码，内省完成，再下一步

<img src="./Python基础教程.assets/image-20241104111507290.png" alt="image-20241104111507290" style="zoom:50%;" />

按提示填写，最后创建

<img src="./Python基础教程.assets/image-20241104112559813.png" alt="image-20241104112559813" style="zoom:50%;" />

注意，这个.venv文件是Linux上隐藏文件，ls命令看不到（xftp也看不到），你可以改成 venv（更好）

点击右下角解释器，发现解释器变为服务器上的了

![image-20241104112718126](./Python基础教程.assets/image-20241104112718126.png)

目前/home/FirstProjectLinux下还没文件，我们没有同步文件夹，点击左上角主菜单——工具——部署——上传到...，弹出选择你要上传到的服务器，选择自己的即可

![image-20241104113002453](./Python基础教程.assets/image-20241104113002453.png)

由于我们刚刚已经设置过映射关系，所以会上传到/home/FirstProjectLinux文件夹，如果不放心，可以查看部署——配置...，或者你可以重新设置映射位置

![image-20241104113232605](./Python基础教程.assets/image-20241104113232605.png)

上传完成后，我们可以在PyCharm打开Linux终端

![image-20241104113613397](./Python基础教程.assets/image-20241104113613397.png)

```shell
cd /home/FirstProjectLinux
ls
```

可以看到出现 first.py 文件，说明成功上传

发现，first.py 又缺少包了，因为尽管本地虚拟环境有，但远程Linux服务器没有下载

![image-20241104113809461](./Python基础教程.assets/image-20241104113809461.png)

使用PyCharm打开Linux终端（注意不是本地终端），输入命令

首先激活虚拟环境（非常重要）

```shell
cd /home/FirstProjectLinux
source .venv/bin/activate
```

可以看到命令提示前面多了(.venv) ，说明进入了虚拟环境

再安装

```shell
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple numpy matplotlib
```

等待更新解释器，如果不自动的话，手动点击右下角重新选择一下解释器，发现波浪线消失，安装成功

运行，成功

我们要修改py文件或者新建py文件（或其他文件），都是在某个py文件部署上传即可，远程py文件就更新了，或者你可以选择自动上传。













# 变量与简单数据类型

## 第一个 Python 程序

在 PyCharm 中新建一个 Python 文件，例如 `hello.py`，输入下面的代码：

```python
print("Hello, Python!")
```

运行后，控制台会输出：

```text
Hello, Python!
```

这里的 `print()` 是 Python 内置函数，用来把内容输出到控制台。双引号里面的 `"Hello, Python!"` 是一段文本，在 Python 中叫做字符串。

## 注释

注释是写给人看的说明文字，Python 解释器运行程序时会忽略注释。

单行注释使用 `#`：

```python
# 输出一句欢迎语
print("欢迎学习 Python")
```

注释也可以写在代码后面：

```python
age = 18  # age 表示年龄
```

多行说明可以连续使用多个 `#`：

```python
# 下面的代码用于保存学生信息
# name 表示学生姓名
# age 表示学生年龄
name = "小明"
age = 18
```

很多初学者会把注释写成“翻译代码”，例如：

```python
# 给 name 赋值为小明
name = "小明"
```

这种注释意义不大，因为代码本身已经很清楚。更好的注释应该解释“为什么这样写”或者“这段代码的业务含义”：

```python
# 默认使用访客身份，登录后再替换为真实用户名
username = "guest"
```

## 变量

变量可以理解为一个“名字”，用来指向某个数据。

```python
message = "今天开始学习 Python"
print(message)
```

运行结果：

```text
今天开始学习 Python
```

上面这行代码的意思是：把字符串 `"今天开始学习 Python"` 赋值给变量 `message`。之后我们使用 `message`，就相当于使用这段字符串。

变量的值可以改变：

```python
message = "今天开始学习 Python"
print(message)

message = "明天继续学习列表"
print(message)
```

运行结果：

```text
今天开始学习 Python
明天继续学习列表
```

注意，变量名只是名字，真正的数据在等号右边。等号 `=` 在 Python 中叫做赋值符号，不是数学里的“相等”。

## 变量命名规则

Python 变量名需要遵守以下规则：

1. 变量名只能包含字母、数字和下划线。
2. 变量名不能以数字开头。
3. 变量名不能使用 Python 关键字，例如 `if`、`for`、`while`。
4. 变量名区分大小写，`age` 和 `Age` 是两个不同变量。
5. 建议使用有意义的英文单词，多个单词之间用下划线连接。

正确示例：

```python
name = "小明"
student_age = 18
score_1 = 95
```

错误示例：

```python
1name = "小明"       # 错误，不能以数字开头
student-age = 18    # 错误，不能使用减号
for = "循环"         # 错误，for 是 Python 关键字
```

推荐写法：

```python
student_name = "小明"
total_score = 280
is_passed = True
```

不是说短变量名一定不能用，而是在初学阶段，变量名清楚比少打几个字更重要。

## 字符串

字符串就是文本数据，可以用单引号或双引号包起来。

```python
name1 = "小明"
name2 = '小红'

print(name1)
print(name2)
```

单引号和双引号效果基本一样。什么时候用哪一个？如果字符串本身包含单引号，可以外面用双引号：

```python
sentence = "I'm a Python learner."
print(sentence)
```

如果字符串本身包含双引号，可以外面用单引号：

```python
sentence = '他说："Python 很有趣。"'
print(sentence)
```

### 字符串拼接

可以使用 `+` 拼接字符串：

```python
first_name = "Li"
last_name = "Hua"
full_name = first_name + " " + last_name

print(full_name)
```

更推荐使用 f-string，把变量直接放进字符串中：

```python
name = "小明"
age = 18

message = f"{name} 今年 {age} 岁"
print(message)
```

运行结果：

```text
小明 今年 18 岁
```

f-string 的格式是：在字符串前面加 `f`，然后在字符串中用 `{}` 放变量或表达式。

```python
price = 9.9
count = 3

print(f"单价：{price}，数量：{count}，总价：{price * count}")
```

### 常用字符串方法

方法可以理解为“某个数据自己带的功能”。字符串常用方法如下：

```python
name = " python "

print(name.strip())      # 去掉两边空格
print(name.upper())      # 转成大写
print(name.lower())      # 转成小写
print(name.title())      # 单词首字母大写
```

示例：

```python
email = "  STUDENT@example.COM  "
email = email.strip().lower()
print(email)
```

运行结果：

```text
student@example.com
```

这里连续写了两个方法：先去掉两边空格，再转成小写。

### 字符串换行

可以使用 `\n` 表示换行：

```python
message = "第一行\n第二行\n第三行"
print(message)
```

也可以使用三引号保存多行字符串：

```python
poem = """床前明月光，
疑是地上霜。
举头望明月，
低头思故乡。"""

print(poem)
```

## 数字

Python 中常见的数字类型有整数和浮点数。

```python
age = 18          # int，整数
height = 1.75     # float，浮点数
price = 19.99
```

常见数字运算：

```python
print(10 + 3)   # 加法
print(10 - 3)   # 减法
print(10 * 3)   # 乘法
print(10 / 3)   # 除法，结果是浮点数
print(10 // 3)  # 整除，只保留整数部分
print(10 % 3)   # 取余
print(2 ** 3)   # 幂运算，2 的 3 次方
```

数字和字符串不能直接拼接：

```python
age = 18
print("我今年" + age + "岁")  # 报错
```

可以使用 f-string：

```python
age = 18
print(f"我今年{age}岁")
```

也可以把数字转换成字符串：

```python
age = 18
print("我今年" + str(age) + "岁")
```

## 布尔值

布尔值只有两个：`True` 和 `False`，表示真和假。

```python
is_student = True
is_raining = False

print(is_student)
print(is_raining)
```

布尔值经常用于条件判断：

```python
age = 18
is_adult = age >= 18

print(is_adult)
```

注意，`True` 和 `False` 的首字母必须大写，写成 `true` 或 `false` 会报错。

## 查看数据类型

使用 `type()` 可以查看一个数据的类型：

```python
name = "小明"
age = 18
height = 1.75
is_student = True

print(type(name))
print(type(age))
print(type(height))
print(type(is_student))
```

常见类型含义：

| 类型 | 含义 | 示例 |
| --- | --- | --- |
| `str` | 字符串 | `"小明"` |
| `int` | 整数 | `18` |
| `float` | 浮点数 | `1.75` |
| `bool` | 布尔值 | `True` |

## 类型转换

有时候我们需要把一种类型转换成另一种类型。

```python
age_text = "18"
age = int(age_text)

print(age + 1)
```

常用转换函数：

```python
int("18")        # 字符串转整数
float("3.14")    # 字符串转浮点数
str(100)         # 数字转字符串
bool(1)          # 转布尔值
```

注意，不能把无法表示数字的字符串转成数字：

```python
number = int("abc")  # 报错
```

## 输入

使用 `input()` 可以让用户在控制台输入内容。

```python
name = input("请输入你的名字：")
print(f"你好，{name}！")
```

需要特别注意：`input()` 得到的内容永远是字符串。

```python
age = input("请输入你的年龄：")
print(type(age))
```

即使你输入 `18`，它也是字符串 `"18"`，不是整数 `18`。如果要参与数字运算，需要转换：

```python
age = input("请输入你的年龄：")
age = int(age)

print(f"明年你 {age + 1} 岁")
```







# 列表

列表用于存储一组有顺序的数据。比如一个班级有多个学生，一个购物车里有多个商品，一个游戏背包里有多个道具，都可以用列表表示。

## 创建列表

列表使用方括号 `[]`，元素之间用逗号隔开。

```python
names = ["小明", "小红", "小刚"]
scores = [98, 87, 92]
mixed = ["小明", 18, True, 1.75]

print(names)
print(scores)
print(mixed)
```

一个列表中可以存放不同类型的数据，但实际开发中通常建议同一个列表存储同一类数据，这样更清晰。

## 访问列表元素

列表中的每个元素都有位置编号，叫做索引。Python 的索引从 `0` 开始。

```python
names = ["小明", "小红", "小刚"]

print(names[0])
print(names[1])
print(names[2])
```

运行结果：

```text
小明
小红
小刚
```

也可以使用负数索引，从后往前取：

```python
names = ["小明", "小红", "小刚"]

print(names[-1])  # 最后一个
print(names[-2])  # 倒数第二个
```

运行结果：

```text
小刚
小红
```

## 修改列表元素

列表是可以修改的。

```python
names = ["小明", "小红", "小刚"]
names[1] = "小兰"

print(names)
```

运行结果：

```text
['小明', '小兰', '小刚']
```

## 添加元素

使用 `append()` 在列表末尾添加元素：

```python
fruits = ["苹果", "香蕉"]
fruits.append("橙子")

print(fruits)
```

使用 `insert()` 在指定位置插入元素：

```python
fruits = ["苹果", "香蕉"]
fruits.insert(1, "西瓜")

print(fruits)
```

运行结果：

```text
['苹果', '西瓜', '香蕉']
```

`insert(1, "西瓜")` 表示把 `"西瓜"` 插入到索引 `1` 的位置，原来索引 `1` 及后面的元素会向后移动。

## 删除元素

使用 `del` 根据索引删除：

```python
fruits = ["苹果", "香蕉", "橙子"]
del fruits[1]

print(fruits)
```

使用 `pop()` 删除并返回元素。默认删除最后一个：

```python
fruits = ["苹果", "香蕉", "橙子"]
last_fruit = fruits.pop()

print(last_fruit)
print(fruits)
```

`pop()` 也可以指定索引：

```python
fruits = ["苹果", "香蕉", "橙子"]
fruit = fruits.pop(0)

print(fruit)
print(fruits)
```

使用 `remove()` 根据值删除：

```python
fruits = ["苹果", "香蕉", "橙子", "香蕉"]
fruits.remove("香蕉")

print(fruits)
```

运行结果：

```text
['苹果', '橙子', '香蕉']
```

注意，`remove()` 只会删除第一个匹配到的值。

## 列表长度

使用 `len()` 获取列表长度：

```python
names = ["小明", "小红", "小刚"]
print(len(names))
```

## 列表排序

使用 `sort()` 对列表永久排序：

```python
numbers = [3, 1, 4, 2]
numbers.sort()

print(numbers)
```

倒序排序：

```python
numbers = [3, 1, 4, 2]
numbers.sort(reverse=True)

print(numbers)
```

使用 `sorted()` 临时排序，不改变原列表：

```python
numbers = [3, 1, 4, 2]

print(sorted(numbers))
print(numbers)
```

运行结果：

```text
[1, 2, 3, 4]
[3, 1, 4, 2]
```

## 反转列表

使用 `reverse()` 反转列表顺序：

```python
names = ["小明", "小红", "小刚"]
names.reverse()

print(names)
```

运行结果：

```text
['小刚', '小红', '小明']
```

## 列表切片

切片用于获取列表的一部分。语法：

```python
列表名[开始索引:结束索引]
```

注意：包含开始索引，不包含结束索引。

```python
students = ["小明", "小红", "小刚", "小兰", "小李"]

print(students[0:3])
print(students[1:4])
```

运行结果：

```text
['小明', '小红', '小刚']
['小红', '小刚', '小兰']
```

如果从开头开始，可以省略开始索引：

```python
students = ["小明", "小红", "小刚", "小兰", "小李"]
print(students[:3])
```

如果一直取到最后，可以省略结束索引：

```python
students = ["小明", "小红", "小刚", "小兰", "小李"]
print(students[2:])
```

使用负数可以取最后几个元素：

```python
students = ["小明", "小红", "小刚", "小兰", "小李"]
print(students[-2:])
```

切片还可以设置步长：

```python
numbers = [1, 2, 3, 4, 5, 6, 7, 8]

print(numbers[0:8:2])
print(numbers[::2])
print(numbers[::-1])
```

运行结果：

```text
[1, 3, 5, 7]
[1, 3, 5, 7]
[8, 7, 6, 5, 4, 3, 2, 1]
```

`numbers[::-1]` 是一个常见写法，表示得到一个反转后的新列表。

## 复制列表

如果直接赋值，并不会复制出一个新列表：

```python
a = [1, 2, 3]
b = a

b.append(4)

print(a)
print(b)
```

运行结果：

```text
[1, 2, 3, 4]
[1, 2, 3, 4]
```

这是因为 `a` 和 `b` 指向的是同一个列表。

使用切片可以复制列表：

```python
a = [1, 2, 3]
b = a[:]

b.append(4)

print(a)
print(b)
```

运行结果：

```text
[1, 2, 3]
[1, 2, 3, 4]
```

## 遍历列表

使用 `for` 循环可以逐个访问列表中的元素：

```python
names = ["小明", "小红", "小刚"]

for name in names:
    print(name)
```

缩进非常重要。属于循环体的代码必须缩进：

```python
names = ["小明", "小红", "小刚"]

for name in names:
    print(f"{name}，欢迎你！")
    print("请入座。")

print("全部同学签到完成。")
```

前两行 `print()` 在循环里面，会执行多次；最后一行没有缩进，只会执行一次。

## 列表推导式

列表推导式可以用更简洁的方式生成列表。

普通写法：

```python
squares = []

for number in range(1, 6):
    squares.append(number ** 2)

print(squares)
```

列表推导式写法：

```python
squares = [number ** 2 for number in range(1, 6)]
print(squares)
```

运行结果：

```text
[1, 4, 9, 16, 25]
```

初学时可以先写普通循环，熟练后再使用列表推导式。









# 元组

元组和列表很像，也可以存储一组有顺序的数据。区别是：列表可以修改，元组创建后不能修改。

## 创建元组

元组使用圆括号 `()`：

```python
point = (10, 20)
colors = ("red", "green", "blue")

print(point)
print(colors)
```

访问元组元素也使用索引：

```python
point = (10, 20)

print(point[0])
print(point[1])
```

## 只有一个元素的元组

如果元组中只有一个元素，必须在元素后面加逗号：

```python
a = (10)
b = (10,)

print(type(a))
print(type(b))
```

运行结果：

```text
<class 'int'>
<class 'tuple'>
```

`(10)` 只是给数字加了括号，不是元组；`(10,)` 才是只有一个元素的元组。

## 元组不可修改

下面的代码会报错：

```python
point = (10, 20)
point[0] = 100
```

因为元组不允许修改已有元素。

但是可以给变量重新赋值，让它指向一个新的元组：

```python
point = (10, 20)
point = (100, 200)

print(point)
```

## 遍历元组

```python
colors = ("red", "green", "blue")

for color in colors:
    print(color)
```

## 元组中存储列表

元组不可修改，指的是元组中每个位置不能换成别的对象。但是如果元组中存的是列表，列表本身仍然可以修改。

```python
student = ("小明", [98, 87, 92])

print(student)

student[1].append(100)

print(student)
```

运行结果：

```text
('小明', [98, 87, 92])
('小明', [98, 87, 92, 100])
```

但是下面这样不行：

```python
student = ("小明", [98, 87, 92])
student[1] = [100, 100, 100]  # 报错
```





# 字典

字典用于存储“键值对”。如果列表像一排有编号的柜子，那么字典就像贴了标签的柜子。我们不是通过位置找数据，而是通过键找数据。

## 创建字典

字典使用花括号 `{}`，每个元素由键和值组成，中间用冒号连接。

```python
student = {
    "name": "小明",
    "age": 18,
    "score": 95
}

print(student)
```

其中 `"name"`、`"age"`、`"score"` 是键；`"小明"`、`18`、`95` 是对应的值。

## 访问字典中的值

使用键访问值：

```python
student = {
    "name": "小明",
    "age": 18,
    "score": 95
}

print(student["name"])
print(student["age"])
```

如果访问不存在的键，会报错：

```python
print(student["city"])  # 报错
```

更安全的方式是使用 `get()`：

```python
student = {
    "name": "小明",
    "age": 18
}

print(student.get("city"))
print(student.get("city", "未知城市"))
```

运行结果：

```text
None
未知城市
```

`get("city", "未知城市")` 表示：如果存在 `"city"`，就返回它的值；如果不存在，就返回默认值 `"未知城市"`。

## 添加和修改键值对

```python
student = {
    "name": "小明",
    "age": 18
}

student["city"] = "北京"   # 添加
student["age"] = 19       # 修改

print(student)
```

如果键不存在，就是添加；如果键已经存在，就是修改。

## 删除键值对

使用 `del` 删除：

```python
student = {
    "name": "小明",
    "age": 18,
    "city": "北京"
}

del student["city"]

print(student)
```

使用 `pop()` 删除并返回值：

```python
student = {
    "name": "小明",
    "age": 18
}

age = student.pop("age")

print(age)
print(student)
```

## 遍历字典

遍历所有键值对：

```python
student = {
    "name": "小明",
    "age": 18,
    "score": 95
}

for key, value in student.items():
    print(f"{key}: {value}")
```

只遍历所有键：

```python
for key in student.keys():
    print(key)
```

也可以简写为：

```python
for key in student:
    print(key)
```

只遍历所有值：

```python
for value in student.values():
    print(value)
```

## 字典中存储列表

一个键对应的值可以是列表：

```python
student = {
    "name": "小明",
    "scores": [98, 87, 92]
}

print(student["scores"])
print(student["scores"][0])
```

可以继续操作这个列表：

```python
student = {
    "name": "小明",
    "scores": [98, 87, 92]
}

student["scores"].append(100)

print(student)
```

运行结果：

```text
{'name': '小明', 'scores': [98, 87, 92, 100]}
```

## 列表中存储字典

如果有多个学生，每个学生又有多个属性，可以使用“列表中存字典”：

```python
students = [
    {"name": "小明", "age": 18, "score": 95},
    {"name": "小红", "age": 17, "score": 88},
    {"name": "小刚", "age": 19, "score": 91}
]

for student in students:
    print(f"{student['name']} 的分数是 {student['score']}")
```

运行结果：

```text
小明 的分数是 95
小红 的分数是 88
小刚 的分数是 91
```

这种结构非常常见。例如，一个班级有很多学生，一个网站有很多用户，一个订单列表里有很多订单。

## 字典中嵌套字典

也可以在字典中继续存储字典：

```python
users = {
    "user_001": {
        "name": "小明",
        "age": 18,
        "city": "北京"
    },
    "user_002": {
        "name": "小红",
        "age": 17,
        "city": "上海"
    }
}

print(users["user_001"]["name"])
```

遍历：

```python
for user_id, user_info in users.items():
    print(f"用户ID：{user_id}")
    print(f"姓名：{user_info['name']}")
    print(f"城市：{user_info['city']}")
```

嵌套结构很强大，但也不要嵌套太深，否则代码会变得难读。



# if 语句

程序不仅可以从上到下执行，还可以根据条件选择不同的执行路线，这就需要 `if` 语句。

## 基本 if 语句

```python
age = 18

if age >= 18:
    print("你已经成年")
```

`if` 后面是条件，条件成立时，缩进的代码会执行；条件不成立时，缩进的代码会跳过。

## if-else

```python
age = 16

if age >= 18:
    print("你已经成年")
else:
    print("你还未成年")
```

运行结果：

```text
你还未成年
```

`else` 表示“否则”。如果 `if` 条件不成立，就执行 `else` 下面的代码。

## if-elif-else

如果有多个条件，可以使用 `elif`：

```python
score = 86

if score >= 90:
    print("优秀")
elif score >= 80:
    print("良好")
elif score >= 60:
    print("及格")
else:
    print("不及格")
```

运行结果：

```text
良好
```

Python 会从上到下依次判断，一旦某个条件成立，就执行对应代码，并跳过后面的分支。

## 比较运算符

| 运算符 | 含义 | 示例 |
| --- | --- | --- |
| `==` | 等于 | `age == 18` |
| `!=` | 不等于 | `age != 18` |
| `>` | 大于 | `age > 18` |
| `<` | 小于 | `age < 18` |
| `>=` | 大于等于 | `age >= 18` |
| `<=` | 小于等于 | `age <= 18` |

注意，判断相等使用 `==`，赋值使用 `=`。

```python
age = 18      # 赋值
age == 18     # 判断是否等于 18
```

## 逻辑运算符

多个条件可以使用 `and`、`or`、`not` 连接。

`and` 表示并且，两个条件都成立才为真：

```python
age = 20
has_ticket = True

if age >= 18 and has_ticket:
    print("可以入场")
```

`or` 表示或者，有一个条件成立就为真：

```python
is_vip = False
has_coupon = True

if is_vip or has_coupon:
    print("可以享受优惠")
```

`not` 表示取反：

```python
is_closed = False

if not is_closed:
    print("商店正在营业")
```

## 判断元素是否在列表中

使用 `in`：

```python
names = ["小明", "小红", "小刚"]

if "小红" in names:
    print("小红在名单中")
```

使用 `not in`：

```python
names = ["小明", "小红", "小刚"]

if "小兰" not in names:
    print("小兰不在名单中")
```

## 布尔值作为条件

```python
is_login = True

if is_login:
    print("欢迎回来")
else:
    print("请先登录")
```

如果变量本身就是布尔值，不需要写成：

```python
if is_login == True:
    print("欢迎回来")
```

直接写 `if is_login:` 更自然。

## 条件表达式

简单的 if-else 可以写成一行：

```python
age = 18
message = "成年" if age >= 18 else "未成年"

print(message)
```

这种写法适合非常简单的判断。如果逻辑比较复杂，还是使用普通的 `if-else` 更清楚。



# for、while 循环

循环用于重复执行代码。比如打印 100 次内容、遍历一个列表、不断接收用户输入，都需要循环。

## for 循环

`for` 循环常用于遍历列表、元组、字符串、字典等可迭代对象。

```python
names = ["小明", "小红", "小刚"]

for name in names:
    print(name)
```

运行结果：

```text
小明
小红
小刚
```

## range()

`range()` 可以生成一段数字序列，常和 `for` 循环一起使用。

```python
for number in range(5):
    print(number)
```

运行结果：

```text
0
1
2
3
4
```

`range(5)` 生成的是从 `0` 到 `4`，不包含 `5`。

指定开始和结束：

```python
for number in range(1, 6):
    print(number)
```

指定步长：

```python
for number in range(1, 10, 2):
    print(number)
```

运行结果：

```text
1
3
5
7
9
```

## for 循环嵌套

循环里面还可以写循环，这叫循环嵌套。

例如打印乘法表：

```python
for i in range(1, 10):
    for j in range(1, i + 1):
        print(f"{j} x {i} = {i * j}", end="\t")
    print()
```

运行结果类似：

```text
1 x 1 = 1
1 x 2 = 2    2 x 2 = 4
1 x 3 = 3    2 x 3 = 6    3 x 3 = 9
...
```

解释：

1. 外层循环控制行数，`i` 从 1 到 9。
2. 内层循环控制每一行打印多少个式子。
3. `end="\t"` 表示打印后不换行，而是用制表符隔开。
4. 内层循环结束后，`print()` 用来换行。

再看一个例子，遍历班级和学生：

```python
classes = [
    ["小明", "小红"],
    ["小刚", "小兰"],
    ["小李", "小王"]
]

for class_students in classes:
    print("一个班级：")
    for student in class_students:
        print(student)
```

运行结果：

```text
一个班级：
小明
小红
一个班级：
小刚
小兰
一个班级：
小李
小王
```

循环嵌套很常用，比如处理二维表格、矩阵、棋盘、班级分组、商品分类等。

## 遍历字典列表

结合前面的字典知识，我们可以用 `for` 循环处理结构化数据：

```python
students = [
    {"name": "小明", "score": 95},
    {"name": "小红", "score": 88},
    {"name": "小刚", "score": 59}
]

for student in students:
    if student["score"] >= 60:
        print(f"{student['name']} 通过考试")
    else:
        print(f"{student['name']} 没有通过考试")
```

## while 循环

`while` 循环会在条件成立时一直执行。

```python
count = 1

while count <= 5:
    print(count)
    count += 1
```

运行结果：

```text
1
2
3
4
5
```

`count += 1` 等价于：

```python
count = count + 1
```

如果忘记修改条件变量，可能会造成死循环：

```python
count = 1

while count <= 5:
    print(count)
```

这段代码会一直打印 `1`，因为 `count` 永远不会变大。

## 使用 while 接收用户输入

```python
message = ""

while message != "退出":
    message = input("请输入内容，输入'退出'结束：")
    print(f"你输入的是：{message}")
```

更常见的写法是使用 `break`：

```python
while True:
    message = input("请输入内容，输入'退出'结束：")

    if message == "退出":
        break

    print(f"你输入的是：{message}")
```

`while True` 表示一直循环，直到遇到 `break` 才退出。

## break

`break` 用于立即结束整个循环。

```python
for number in range(1, 10):
    if number == 5:
        break
    print(number)
```

运行结果：

```text
1
2
3
4
```

当 `number` 等于 `5` 时，循环直接结束。

## continue

`continue` 用于跳过本次循环，继续下一次循环。

```python
for number in range(1, 6):
    if number == 3:
        continue
    print(number)
```

运行结果：

```text
1
2
4
5
```

当 `number` 等于 `3` 时，本次循环后面的 `print(number)` 被跳过。

## 循环中的 else

Python 的循环也可以带 `else`。当循环正常结束，没有被 `break` 打断时，会执行 `else`。

```python
numbers = [1, 3, 5, 7]

for number in numbers:
    if number % 2 == 0:
        print("找到偶数")
        break
else:
    print("没有找到偶数")
```

运行结果：

```text
没有找到偶数
```

这个语法不算特别常用，但在“查找某个元素，找不到就做某事”的场景中很方便。









# 函数

函数是一段带名字的代码，用来完成某个具体任务。前面我们已经使用过很多函数，例如 `print()`、`input()`、`len()`、`type()`。这些是 Python 提供的内置函数，我们也可以自己定义函数。

使用函数有几个好处：

1. 让代码更清晰，把复杂任务拆成一个个小任务。
2. 避免重复代码，同一段逻辑可以多次调用。
3. 方便修改，功能变化时只需要改函数内部。

## 定义函数

定义函数使用 `def` 关键字。

```python
def greet_user():
    """显示简单的问候语。"""
    print("Hello!")

greet_user()
```

运行结果：

```text
Hello!
```

解释：

1. `def greet_user():` 表示定义一个名为 `greet_user` 的函数。
2. 函数名后面必须有小括号 `()`。
3. 冒号 `:` 后面的缩进代码属于函数体。
4. 三引号中的字符串叫做文档字符串，用来说明函数功能。
5. `greet_user()` 表示调用函数。

函数定义本身不会立刻执行，只有调用函数时，函数体中的代码才会运行。

## 向函数传递信息

函数可以接收数据。

```python
def greet_user(username):
    """显示个性化问候语。"""
    print(f"Hello, {username.title()}!")

greet_user("jesse")
```

运行结果：

```text
Hello, Jesse!
```

这里的 `username` 是形参，表示函数定义中用来接收数据的变量；`"jesse"` 是实参，表示调用函数时传入的实际数据。

## 实参和形参

```python
def describe_pet(animal_type, pet_name):
    """显示宠物信息。"""
    print(f"\nI have a {animal_type}.")
    print(f"My {animal_type}'s name is {pet_name.title()}.")

describe_pet("hamster", "harry")
```

运行结果：

```text
I have a hamster.
My hamster's name is Harry.
```

`animal_type` 和 `pet_name` 是形参；`"hamster"` 和 `"harry"` 是实参。

## 位置实参

位置实参是最常见的传参方式。Python 会按照顺序把实参传给形参。

```python
def describe_pet(animal_type, pet_name):
    print(f"I have a {animal_type}.")
    print(f"My {animal_type}'s name is {pet_name.title()}.")

describe_pet("dog", "willie")
```

如果顺序写反，结果也会跟着错：

```python
describe_pet("willie", "dog")
```

输出会变成：

```text
I have a willie.
My willie's name is Dog.
```

所以使用位置实参时，要注意实参顺序。

函数可以调用多次：

```python
describe_pet("dog", "willie")
describe_pet("cat", "lucy")
```

## 关键字实参

关键字实参直接指定形参名，顺序就不重要了。

```python
def describe_pet(animal_type, pet_name):
    print(f"I have a {animal_type}.")
    print(f"My {animal_type}'s name is {pet_name.title()}.")

describe_pet(animal_type="dog", pet_name="willie")
describe_pet(pet_name="lucy", animal_type="cat")
```

关键字实参的优点是可读性更强，尤其是参数较多时，不容易传错。

## 默认值

可以给形参设置默认值。如果调用函数时没有传入对应实参，就使用默认值。

```python
def describe_pet(pet_name, animal_type="dog"):
    print(f"I have a {animal_type}.")
    print(f"My {animal_type}'s name is {pet_name.title()}.")

describe_pet("willie")
describe_pet("lucy", "cat")
```

运行结果：

```text
I have a dog.
My dog's name is Willie.
I have a cat.
My cat's name is Lucy.
```

注意，有默认值的形参通常放在后面。因为位置实参是按顺序匹配的，如果默认参数放前面，容易造成混乱。

## 等效的函数调用

同一个函数可以用多种方式调用。

```python
def describe_pet(pet_name, animal_type="dog"):
    print(f"I have a {animal_type}.")
    print(f"My {animal_type}'s name is {pet_name.title()}.")

describe_pet("willie")
describe_pet(pet_name="willie")
describe_pet("lucy", "cat")
describe_pet(pet_name="lucy", animal_type="cat")
describe_pet(animal_type="cat", pet_name="lucy")
```

只要最终传给每个形参的值一致，调用方式就是等效的。

## 避免实参错误

如果调用函数时少传或多传参数，会报错。

```python
def describe_pet(animal_type, pet_name):
    print(f"I have a {animal_type}.")
    print(f"My {animal_type}'s name is {pet_name.title()}.")

describe_pet("dog")  # 报错，缺少 pet_name
```

报错信息通常会告诉你缺少哪个参数。初学时不要害怕报错，认真读报错信息是学习 Python 的重要能力。

## 返回值

函数不一定只负责打印，也可以处理数据并把结果返回给调用者。返回结果使用 `return`。

```python
def get_formatted_name(first_name, last_name):
    """返回整洁的姓名。"""
    full_name = f"{first_name} {last_name}"
    return full_name.title()

musician = get_formatted_name("jimi", "hendrix")
print(musician)
```

运行结果：

```text
Jimi Hendrix
```

`return` 会把函数内部的结果送回函数调用的位置。

## 让实参变成可选的

有些信息不是每次都有，可以使用默认值让参数变成可选。

```python
def get_formatted_name(first_name, last_name, middle_name=""):
    """返回整洁的姓名。"""
    if middle_name:
        full_name = f"{first_name} {middle_name} {last_name}"
    else:
        full_name = f"{first_name} {last_name}"
    return full_name.title()

musician = get_formatted_name("jimi", "hendrix")
print(musician)

musician = get_formatted_name("john", "hooker", "lee")
print(musician)
```

运行结果：

```text
Jimi Hendrix
John Lee Hooker
```

空字符串 `""` 在条件判断中会被当作 `False`，非空字符串会被当作 `True`。

## 返回字典

函数可以返回任何类型的数据，包括字典。

```python
def build_person(first_name, last_name):
    """返回一个表示人的字典。"""
    person = {
        "first": first_name,
        "last": last_name
    }
    return person

musician = build_person("jimi", "hendrix")
print(musician)
```

运行结果：

```text
{'first': 'jimi', 'last': 'hendrix'}
```

也可以给字典增加可选信息：

```python
def build_person(first_name, last_name, age=None):
    """返回一个表示人的字典。"""
    person = {
        "first": first_name,
        "last": last_name
    }
    if age:
        person["age"] = age
    return person

musician = build_person("jimi", "hendrix", age=27)
print(musician)
```

`None` 表示“没有值”。当参数暂时没有合适的默认值时，经常使用 `None`。

## 结合 while 循环使用函数

函数可以放在循环中反复调用。

```python
def get_formatted_name(first_name, last_name):
    """返回整洁的姓名。"""
    full_name = f"{first_name} {last_name}"
    return full_name.title()

while True:
    print("\n请输入姓名：")
    print("输入 q 可以退出")

    first = input("First name: ")
    if first == "q":
        break

    last = input("Last name: ")
    if last == "q":
        break

    formatted_name = get_formatted_name(first, last)
    print(f"Hello, {formatted_name}!")
```

这段代码中，函数只负责整理姓名，循环负责不断接收用户输入。不同任务分开写，程序更清楚。

## 传递列表

函数可以接收列表。

```python
def greet_users(names):
    """向列表中的每位用户发出问候。"""
    for name in names:
        message = f"Hello, {name.title()}!"
        print(message)

usernames = ["hannah", "ty", "margot"]
greet_users(usernames)
```

运行结果：

```text
Hello, Hannah!
Hello, Ty!
Hello, Margot!
```

## 在函数中修改列表

列表传入函数后，函数可以修改这个列表。

```python
def print_models(unprinted_designs, completed_models):
    """模拟打印每个设计，直到没有未打印的设计为止。"""
    while unprinted_designs:
        current_design = unprinted_designs.pop()
        print(f"Printing model: {current_design}")
        completed_models.append(current_design)

def show_completed_models(completed_models):
    """显示打印好的所有模型。"""
    print("\nThe following models have been printed:")
    for completed_model in completed_models:
        print(completed_model)

unprinted_designs = ["phone case", "robot pendant", "dodecahedron"]
completed_models = []

print_models(unprinted_designs, completed_models)
show_completed_models(completed_models)
```

运行结束后，`unprinted_designs` 会变成空列表，`completed_models` 会保存已经处理好的模型。

## 禁止函数修改列表

如果不希望函数修改原列表，可以传入列表副本。

```python
unprinted_designs = ["phone case", "robot pendant", "dodecahedron"]
completed_models = []

print_models(unprinted_designs[:], completed_models)

print(unprinted_designs)
print(completed_models)
```

`unprinted_designs[:]` 会复制出一个新列表，函数修改的是副本，原列表保持不变。

不过，除非确实需要保留原列表，否则直接传原列表更简单、更高效。

## 传递任意数量的实参

有时候我们不知道函数会接收多少个参数，可以使用 `*`。

```python
def make_pizza(*toppings):
    """打印顾客点的所有配料。"""
    print(toppings)

make_pizza("pepperoni")
make_pizza("mushrooms", "green peppers", "extra cheese")
```

运行结果：

```text
('pepperoni',)
('mushrooms', 'green peppers', 'extra cheese')
```

形参名前面的 `*` 会把多个实参收集到一个元组中。

可以遍历这些实参：

```python
def make_pizza(*toppings):
    """概述要制作的披萨。"""
    print("\nMaking a pizza with the following toppings:")
    for topping in toppings:
        print(f"- {topping}")

make_pizza("pepperoni")
make_pizza("mushrooms", "green peppers", "extra cheese")
```

## 结合位置实参和任意数量实参

如果函数既有普通形参，又有任意数量形参，任意数量形参通常放在最后。

```python
def make_pizza(size, *toppings):
    """概述要制作的披萨。"""
    print(f"\nMaking a {size}-inch pizza with the following toppings:")
    for topping in toppings:
        print(f"- {topping}")

make_pizza(16, "pepperoni")
make_pizza(12, "mushrooms", "green peppers", "extra cheese")
```

`size` 接收第一个实参，剩下的实参都被收集到 `toppings` 中。

## 使用任意数量的关键字实参

如果不知道会收到哪些键值对，可以使用 `**`。

```python
def build_profile(first, last, **user_info):
    """创建用户简介字典。"""
    user_info["first_name"] = first
    user_info["last_name"] = last
    return user_info

user_profile = build_profile(
    "albert",
    "einstein",
    location="princeton",
    field="physics"
)

print(user_profile)
```

运行结果：

```text
{'location': 'princeton', 'field': 'physics', 'first_name': 'albert', 'last_name': 'einstein'}
```

形参名前面的 `**` 会把任意数量的关键字实参收集到一个字典中。

## 将函数存储在模块中

当程序越来越大，可以把函数放到单独的 `.py` 文件中，这个文件叫模块。假设创建一个文件 `pizza.py`：

```python
def make_pizza(size, *toppings):
    """概述要制作的披萨。"""
    print(f"\nMaking a {size}-inch pizza with the following toppings:")
    for topping in toppings:
        print(f"- {topping}")
```

在另一个文件 `making_pizzas.py` 中导入并使用：

```python
import pizza

pizza.make_pizza(16, "pepperoni")
pizza.make_pizza(12, "mushrooms", "green peppers", "extra cheese")
```

`import pizza` 表示导入整个 `pizza.py` 模块。调用模块中的函数时，需要写成 `模块名.函数名()`。

## if __name__ == "__main__"

很多初学者看到下面这行代码都会懵：

```python
if __name__ == "__main__":
```

它的作用可以先记成一句话：

这行代码用来判断：当前文件是“被直接运行”，还是“被别人导入”。

在 Python 中，每个 `.py` 文件都有一个内置变量 `__name__`。

如果这个文件是被直接运行的，`__name__` 的值就是 `"__main__"`。

如果这个文件是被其他文件导入的，`__name__` 的值就是模块名。

先看一个最简单的例子。创建文件 `hello.py`：

```python
print(__name__)
```

直接运行 `hello.py`，输出：

```text
__main__
```

再创建另一个文件 `test.py`：

```python
import hello
```

运行 `test.py`，会输出：

```text
hello
```

这说明：同一个 `hello.py`，直接运行时，`__name__` 是 `"__main__"`；被导入时，`__name__` 是 `"hello"`。

------

为什么需要它？

假设我们写了一个模块 `pizza.py`：

```python
def make_pizza(size, *toppings):
    """概述要制作的披萨。"""
    print(f"\nMaking a {size}-inch pizza with the following toppings:")
    for topping in toppings:
        print(f"- {topping}")

make_pizza(16, "pepperoni")
make_pizza(12, "mushrooms", "green peppers", "extra cheese")
```

直接运行 `pizza.py`，没有问题，会打印两份披萨信息。

但是如果在 `making_pizzas.py` 中导入它：

```python
import pizza

pizza.make_pizza(8, "cheese")
```

你会发现，除了 `8` 寸披萨，`pizza.py` 下面那两行测试代码也会自动运行。原因是：导入模块时，Python 会从上到下执行被导入文件中的代码。

这通常不是我们想要的。我们希望：

1. 直接运行 `pizza.py` 时，可以执行测试代码。
2. 别的文件导入 `pizza.py` 时，只导入函数，不自动执行测试代码。

这时就要使用：

```python
def make_pizza(size, *toppings):
    """概述要制作的披萨。"""
    print(f"\nMaking a {size}-inch pizza with the following toppings:")
    for topping in toppings:
        print(f"- {topping}")

if __name__ == "__main__":
    make_pizza(16, "pepperoni")
    make_pizza(12, "mushrooms", "green peppers", "extra cheese")
```

现在效果变成：

直接运行 `pizza.py`：会执行 `if` 下面的两行测试代码。

被 `making_pizzas.py` 导入：不会执行 `if` 下面的测试代码，只能通过 `pizza.make_pizza()` 主动调用函数。

------

可以把它理解成程序入口

在实际项目中，经常会写一个 `main()` 函数，把主要流程放进去，然后在文件最后写：

```python
def main():
    """程序主流程。"""
    print("程序开始运行")
    make_pizza(16, "pepperoni")

def make_pizza(size, *toppings):
    """概述要制作的披萨。"""
    print(f"\nMaking a {size}-inch pizza with the following toppings:")
    for topping in toppings:
        print(f"- {topping}")

if __name__ == "__main__":
    main()
```

这是一种很常见、很推荐的写法。它的意思是：

如果这个文件是被直接运行的，就调用 `main()`；如果这个文件是被导入的，就不要自动调用 `main()`。





创建 `calculator.py`：

```python
def add(a, b):
    """返回两个数的和。"""
    return a + b

def subtract(a, b):
    """返回两个数的差。"""
    return a - b

if __name__ == "__main__":
    print(add(3, 5))
    print(subtract(10, 4))
```

直接运行 `calculator.py`，输出：

```text
8
6
```

再创建 `app.py`：

```python
import calculator

result = calculator.add(100, 200)
print(result)
```

运行 `app.py`，只会输出：

```text
300
```

不会额外输出 `8` 和 `6`，因为 `calculator.py` 中的测试代码被放进了 `if __name__ == "__main__":` 下面。

------

什么时候要写它

下面这些情况适合写：

1. 一个文件里既有函数或类，又有测试代码。
2. 一个文件既可能直接运行，也可能被其他文件导入。
3. 想让程序入口更清楚。
4. 想避免导入模块时自动执行一堆代码。

简单记忆：

```python
if __name__ == "__main__":
    # 只有直接运行这个文件时，才执行这里的代码
```

如果一个文件只是很短的小练习，不会被别的文件导入，不写也没问题。但只要开始写模块、导入函数、导入类，就很推荐加上它。

## 导入特定函数

也可以只导入模块中的某个函数：

```python
from pizza import make_pizza

make_pizza(16, "pepperoni")
make_pizza(12, "mushrooms", "green peppers", "extra cheese")
```

这种写法调用函数时不需要写模块名。

## 使用 as 指定别名

如果函数名比较长，可以给函数起别名：

```python
from pizza import make_pizza as mp

mp(16, "pepperoni")
```

也可以给模块起别名：

```python
import pizza as p

p.make_pizza(16, "pepperoni")
```

## 导入模块中的所有函数

可以使用 `*` 导入模块中的所有函数：

```python
from pizza import *

make_pizza(16, "pepperoni")
```

这种写法虽然方便，但不推荐在较大的程序中使用。因为你可能不知道导入了哪些函数，容易造成命名冲突。更推荐使用 `import 模块名` 或 `from 模块名 import 函数名`。

## Lambda 表达式

Lambda 表达式也叫匿名函数。普通函数有名字，使用 `def` 定义；Lambda 表达式通常用于定义很短、只用一次的小函数。

基本语法：

```python
lambda 参数: 表达式
```

例如，下面是一个普通函数：

```python
def add(a, b):
    return a + b

print(add(3, 5))
```

可以写成 Lambda 表达式：

```python
add = lambda a, b: a + b

print(add(3, 5))
```

运行结果：

```text
8
```

不过，像上面这样把 Lambda 赋值给变量并不常见。如果一个函数需要反复使用，通常直接用 `def` 更清楚。Lambda 更常见的用法，是作为参数传给其他函数。



Lambda 和 sorted()

假设有一个学生列表，每个学生用字典表示：

```python
students = [
    {"name": "小明", "score": 95},
    {"name": "小红", "score": 88},
    {"name": "小刚", "score": 92}
]
```

如果想按照分数排序，可以这样写：

```python
students = [
    {"name": "小明", "score": 95},
    {"name": "小红", "score": 88},
    {"name": "小刚", "score": 92}
]

sorted_students = sorted(students, key=lambda student: student["score"])

print(sorted_students)
```

运行结果：

```text
[{'name': '小红', 'score': 88}, {'name': '小刚', 'score': 92}, {'name': '小明', 'score': 95}]
```

这里的：

```python
lambda student: student["score"]
```

意思是：给我一个 `student`，我返回它的 `"score"`。`sorted()` 就会根据这个返回值进行排序。

如果想从高到低排序：

```python
sorted_students = sorted(
    students,
    key=lambda student: student["score"],
    reverse=True
)

print(sorted_students)
```

再看一个按照字符串长度排序的例子：

```python
words = ["python", "java", "c", "javascript"]

sorted_words = sorted(words, key=lambda word: len(word))

print(sorted_words)
```

运行结果：

```text
['c', 'java', 'python', 'javascript']
```





Lambda 和 map()

`map()` 可以把一个函数应用到每个元素上。

```python
numbers = [1, 2, 3, 4, 5]

squares = list(map(lambda number: number ** 2, numbers))

print(squares)
```

运行结果：

```text
[1, 4, 9, 16, 25]
```

不过，这个例子用列表推导式通常更清楚：

```python
numbers = [1, 2, 3, 4, 5]

squares = [number ** 2 for number in numbers]

print(squares)
```

所以在 Python 中，很多时候列表推导式比 `map() + lambda` 更推荐。





Lambda 和 filter()

`filter()` 可以根据条件筛选元素。

```python
numbers = [1, 2, 3, 4, 5, 6]

even_numbers = list(filter(lambda number: number % 2 == 0, numbers))

print(even_numbers)
```

运行结果：

```text
[2, 4, 6]
```

同样，也可以用列表推导式：

```python
numbers = [1, 2, 3, 4, 5, 6]

even_numbers = [number for number in numbers if number % 2 == 0]

print(even_numbers)
```

初学时建议优先掌握列表推导式；遇到 `sorted(..., key=lambda ...)` 这种写法时，一定要能看懂，因为它非常常见。





Lambda 的限制

Lambda 只能写一个表达式，不能写多行复杂逻辑。

适合 Lambda 的情况：

```python
lambda x: x * 2
lambda student: student["score"]
lambda word: len(word)
```

不适合 Lambda 的情况：

```python
def check_score(score):
    if score >= 90:
        return "优秀"
    elif score >= 60:
        return "及格"
    else:
        return "不及格"
```

如果逻辑需要 `if-elif-else`、循环、多个步骤，就应该使用普通函数。

简单记忆：

1. `def` 适合正式、可复用、逻辑较多的函数。
2. `lambda` 适合临时、简短、通常只用一次的小函数。
3. 常见场景是 `sorted()` 的 `key` 参数。



## 函数编写建议

1. 函数名使用小写字母和下划线，例如 `get_formatted_name`。
2. 每个函数只做一件明确的事。
3. 给函数写简短的文档字符串，说明它做什么。
4. 形参默认值两边不要加空格，例如 `animal_type="dog"`。
5. 调用函数时，关键字实参两边也不要加空格，例如 `pet_name="willie"`。
6. 如果函数参数很多，可以分多行写，提高可读性。

示例：

```python
def build_profile(first, last, **user_info):
    """创建用户简介字典。"""
    user_info["first_name"] = first
    user_info["last_name"] = last
    return user_info

profile = build_profile(
    "albert",
    "einstein",
    location="princeton",
    field="physics",
)
```






# 类

面向对象编程是 Python 中非常重要的思想。前面我们学习的列表、字典、函数，更多是在描述数据和操作；类则可以把数据和操作数据的行为组织在一起。

简单来说，类是创建对象的模板。根据类创建出来的具体对象，叫做实例。

例如，可以定义一个 `Dog` 类，用它创建很多只狗；每只狗都有名字和年龄，也都可以坐下、打滚。

## 创建和使用类

```python
class Dog:
    """一次模拟小狗的简单尝试。"""

    def __init__(self, name, age):
        """初始化属性 name 和 age。"""
        self.name = name
        self.age = age

    def sit(self):
        """模拟小狗收到命令时坐下。"""
        print(f"{self.name} is now sitting.")

    def roll_over(self):
        """模拟小狗收到命令时打滚。"""
        print(f"{self.name} rolled over!")
```

解释：

1. 类名通常使用大驼峰命名法，例如 `Dog`、`ElectricCar`。
2. `__init__()` 是一个特殊方法，创建实例时会自动运行。
3. `self` 表示当前实例本身，必须放在实例方法的第一个参数位置。
4. `self.name = name` 会把形参 `name` 的值保存到实例属性 `name` 中。
5. 类中的函数叫方法。

## 根据类创建实例

```python
class Dog:
    """一次模拟小狗的简单尝试。"""

    def __init__(self, name, age):
        self.name = name
        self.age = age

    def sit(self):
        print(f"{self.name} is now sitting.")

    def roll_over(self):
        print(f"{self.name} rolled over!")

my_dog = Dog("Willie", 6)

print(f"My dog's name is {my_dog.name}.")
print(f"My dog is {my_dog.age} years old.")
```

运行结果：

```text
My dog's name is Willie.
My dog is 6 years old.
```

`my_dog = Dog("Willie", 6)` 会调用 `Dog` 类创建一个实例，并把它赋值给变量 `my_dog`。

## 访问属性

访问实例属性使用点号：

```python
print(my_dog.name)
print(my_dog.age)
```

点号可以理解为“从某个对象里面取出某个属性或方法”。

## 调用方法

调用实例方法也使用点号：

```python
my_dog.sit()
my_dog.roll_over()
```

运行结果：

```text
Willie is now sitting.
Willie rolled over!
```

## 创建多个实例

同一个类可以创建多个实例，每个实例都有自己的属性。

```python
my_dog = Dog("Willie", 6)
your_dog = Dog("Lucy", 3)

print(f"My dog's name is {my_dog.name}.")
my_dog.sit()

print(f"\nYour dog's name is {your_dog.name}.")
your_dog.sit()
```

`my_dog` 和 `your_dog` 都是 `Dog` 类的实例，但它们保存的数据不同。

## 使用类和实例

下面定义一个汽车类。

```python
class Car:
    """一次模拟汽车的简单尝试。"""

    def __init__(self, make, model, year):
        """初始化描述汽车的属性。"""
        self.make = make
        self.model = model
        self.year = year

    def get_descriptive_name(self):
        """返回整洁的汽车描述。"""
        long_name = f"{self.year} {self.make} {self.model}"
        return long_name.title()

my_new_car = Car("audi", "a4", 2024)
print(my_new_car.get_descriptive_name())
```

运行结果：

```text
2024 Audi A4
```

## 给属性指定默认值

有些属性不需要通过参数传入，可以在 `__init__()` 中设置默认值。

```python
class Car:
    """一次模拟汽车的简单尝试。"""

    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year
        self.odometer_reading = 0

    def get_descriptive_name(self):
        long_name = f"{self.year} {self.make} {self.model}"
        return long_name.title()

    def read_odometer(self):
        """打印汽车里程。"""
        print(f"This car has {self.odometer_reading} miles on it.")

my_new_car = Car("audi", "a4", 2024)
print(my_new_car.get_descriptive_name())
my_new_car.read_odometer()
```

`odometer_reading` 表示里程表读数，新车默认是 `0`。

## 修改属性的值

修改属性有三种常见方式。

第一种，直接修改属性：

```python
my_new_car.odometer_reading = 23
my_new_car.read_odometer()
```

第二种，通过方法修改属性：

```python
class Car:
    """一次模拟汽车的简单尝试。"""

    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year
        self.odometer_reading = 0

    def get_descriptive_name(self):
        long_name = f"{self.year} {self.make} {self.model}"
        return long_name.title()

    def read_odometer(self):
        print(f"This car has {self.odometer_reading} miles on it.")

    def update_odometer(self, mileage):
        """将里程表读数设置为指定值。"""
        self.odometer_reading = mileage

my_new_car = Car("audi", "a4", 2024)
my_new_car.update_odometer(23)
my_new_car.read_odometer()
```

第三种，通过方法让属性递增：

```python
class Car:
    """一次模拟汽车的简单尝试。"""

    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year
        self.odometer_reading = 0

    def read_odometer(self):
        print(f"This car has {self.odometer_reading} miles on it.")

    def update_odometer(self, mileage):
        self.odometer_reading = mileage

    def increment_odometer(self, miles):
        """让里程表读数增加指定的量。"""
        self.odometer_reading += miles

my_used_car = Car("subaru", "outback", 2019)
my_used_car.update_odometer(23_500)
my_used_car.increment_odometer(100)
my_used_car.read_odometer()
```

通过方法修改属性的好处是可以加入检查逻辑。例如，禁止把里程表往回调：

```python
def update_odometer(self, mileage):
    """将里程表读数设置为指定值，禁止回调。"""
    if mileage >= self.odometer_reading:
        self.odometer_reading = mileage
    else:
        print("You can't roll back an odometer!")
```

## 私有属性

在类中，有些属性不希望外部代码随便修改。例如汽车的里程表、用户的密码、银行卡余额等。如果外部可以随便改，程序就很容易出问题。

先看一个普通属性的问题：

```python
class Car:
    """一次模拟汽车的简单尝试。"""

    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year
        self.odometer_reading = 0

    def read_odometer(self):
        print(f"This car has {self.odometer_reading} miles on it.")

my_car = Car("audi", "a4", 2024)
my_car.odometer_reading = -100
my_car.read_odometer()
```

运行结果：

```text
This car has -100 miles on it.
```

这显然不合理。里程表不应该被随便改成负数。

## 单下划线属性

Python 中常用单下划线开头表示“这是内部属性，不建议外部直接访问”。

```python
class Car:
    """一次模拟汽车的简单尝试。"""

    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year
        self._odometer_reading = 0

    def read_odometer(self):
        print(f"This car has {self._odometer_reading} miles on it.")

    def update_odometer(self, mileage):
        if mileage >= self._odometer_reading:
            self._odometer_reading = mileage
        else:
            print("You can't roll back an odometer!")

my_car = Car("audi", "a4", 2024)
my_car.update_odometer(100)
my_car.read_odometer()
```

`_odometer_reading` 前面的单下划线是一种约定，意思是：这个属性供类内部使用，外部代码不要直接改它。

但是要注意，单下划线并不会真正阻止访问：

```python
my_car._odometer_reading = -100
my_car.read_odometer()
```

这段代码仍然可以运行。Python 更强调“约定”和“自觉”，而不是强行禁止。

## 双下划线属性

如果属性名前面使用两个下划线，Python 会对属性名进行特殊处理，让外部不容易直接访问。

```python
class BankAccount:
    """模拟银行账户。"""

    def __init__(self, owner, balance):
        self.owner = owner
        self.__balance = balance

    def show_balance(self):
        print(f"{self.owner} 的余额是：{self.__balance}")

    def deposit(self, amount):
        if amount > 0:
            self.__balance += amount
        else:
            print("存款金额必须大于 0")

    def withdraw(self, amount):
        if amount <= 0:
            print("取款金额必须大于 0")
        elif amount > self.__balance:
            print("余额不足")
        else:
            self.__balance -= amount

account = BankAccount("小明", 1000)
account.deposit(500)
account.withdraw(200)
account.show_balance()
```

运行结果：

```text
小明 的余额是：1300
```

如果从外部直接访问 `__balance`：

```python
print(account.__balance)  # 报错
```

会报错，因为 `__balance` 不是普通的公开属性。

## 双下划线并不是绝对安全

双下划线的本质是名称改写。上面的 `__balance` 会被 Python 改成类似 `_BankAccount__balance` 的名字。

所以，下面这样仍然可以访问：

```python
print(account._BankAccount__balance)
```

但是不应该这样写。双下划线不是用来做安全加密的，而是用来避免外部误操作，也能避免子类中属性重名。

如果真的要保存密码，不能只靠双下划线。密码应该使用专门的加密或哈希方式处理，不能明文保存。

## 通过方法访问私有属性

私有属性通常配合方法使用。外部代码不能随便改属性，只能通过类提供的方法操作。

```python
class User:
    """模拟用户。"""

    def __init__(self, username, password):
        self.username = username
        self.__password = password

    def check_password(self, password):
        """检查密码是否正确。"""
        return password == self.__password

    def change_password(self, old_password, new_password):
        """修改密码。"""
        if self.check_password(old_password):
            self.__password = new_password
            print("密码修改成功")
        else:
            print("旧密码错误，不能修改密码")

user = User("xiaoming", "123456")

print(user.check_password("000000"))
print(user.check_password("123456"))

user.change_password("000000", "abcdef")
user.change_password("123456", "abcdef")
print(user.check_password("abcdef"))
```

这段代码的重点是：外部不直接操作 `__password`，而是通过 `check_password()` 和 `change_password()` 这两个方法间接操作。这样类就可以控制修改规则。

## 私有方法

除了私有属性，也可以定义私有方法。

```python
class Order:
    """模拟订单。"""

    def __init__(self, price, count):
        self.price = price
        self.count = count

    def __calculate_total(self):
        """计算总价，供类内部使用。"""
        return self.price * self.count

    def show_total(self):
        total = self.__calculate_total()
        print(f"订单总价：{total}")

order = Order(19.9, 3)
order.show_total()
```

`__calculate_total()` 是私有方法，表示它主要给类内部调用，不希望外部直接调用。

## 什么时候使用私有属性

下面这些情况适合考虑私有属性：

1. 属性不能被外部随意修改，例如余额、密码、里程。
2. 修改属性前需要进行检查。
3. 属性只是类内部实现细节，外部不需要关心。
4. 希望外部代码通过方法来操作对象，而不是直接改数据。

简单记忆：

```python
self.name = name          # 公开属性，外部可以正常访问
self._name = name         # 内部属性，不建议外部直接访问
self.__name = name        # 私有属性，外部不容易直接访问
```

初学时可以先掌握公开属性和单下划线属性。等你开始写较复杂的类，再使用双下划线保护关键数据。





## 继承

一个类可以继承另一个类。原来的类叫父类，新类叫子类。子类会自动拥有父类的属性和方法，还可以添加自己的属性和方法。

例如，电动汽车也是汽车，所以可以让 `ElectricCar` 继承 `Car`。

```python
class Car:
    """一次模拟汽车的简单尝试。"""

    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year
        self.odometer_reading = 0

    def get_descriptive_name(self):
        long_name = f"{self.year} {self.make} {self.model}"
        return long_name.title()

    def read_odometer(self):
        print(f"This car has {self.odometer_reading} miles on it.")

class ElectricCar(Car):
    """电动汽车的独特之处。"""

    def __init__(self, make, model, year):
        """先初始化父类的属性。"""
        super().__init__(make, model, year)

my_leaf = ElectricCar("nissan", "leaf", 2024)
print(my_leaf.get_descriptive_name())
```

`super().__init__(make, model, year)` 会调用父类 `Car` 的初始化方法，让子类实例拥有父类中定义的属性。

## 给子类定义属性和方法

子类可以有自己的属性和方法。

```python
class ElectricCar(Car):
    """电动汽车的独特之处。"""

    def __init__(self, make, model, year):
        super().__init__(make, model, year)
        self.battery_size = 40

    def describe_battery(self):
        """打印电池容量。"""
        print(f"This car has a {self.battery_size}-kWh battery.")

my_leaf = ElectricCar("nissan", "leaf", 2024)
print(my_leaf.get_descriptive_name())
my_leaf.describe_battery()
```

`battery_size` 是电动汽车独有的属性，所以放在 `ElectricCar` 中更合适。

## 重写父类方法

如果父类中的某个方法不适合子类，可以在子类中定义同名方法，这叫重写。

```python
class Car:
    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year

    def fill_gas_tank(self):
        print("This car needs a gas tank.")

class ElectricCar(Car):
    def __init__(self, make, model, year):
        super().__init__(make, model, year)

    def fill_gas_tank(self):
        print("This car doesn't have a gas tank!")

my_leaf = ElectricCar("nissan", "leaf", 2024)
my_leaf.fill_gas_tank()
```

调用 `my_leaf.fill_gas_tank()` 时，Python 会优先使用子类中的方法。

## 将实例用作属性

当一个类越来越复杂，可以把一部分功能拆成另一个类，再把这个类的实例作为属性。

```python
class Battery:
    """一次模拟电动汽车电池的简单尝试。"""

    def __init__(self, battery_size=40):
        self.battery_size = battery_size

    def describe_battery(self):
        print(f"This car has a {self.battery_size}-kWh battery.")

    def get_range(self):
        """打印电池续航信息。"""
        if self.battery_size == 40:
            range_miles = 150
        elif self.battery_size == 65:
            range_miles = 225
        else:
            range_miles = 0

        print(f"This car can go about {range_miles} miles on a full charge.")

class ElectricCar(Car):
    """电动汽车的独特之处。"""

    def __init__(self, make, model, year):
        super().__init__(make, model, year)
        self.battery = Battery()

my_leaf = ElectricCar("nissan", "leaf", 2024)
print(my_leaf.get_descriptive_name())
my_leaf.battery.describe_battery()
my_leaf.battery.get_range()
```

这里 `ElectricCar` 有一个属性 `battery`，它保存的是 `Battery` 类的实例。调用电池方法时写成 `my_leaf.battery.describe_battery()`。

这种写法叫组合。继承表示“是什么”，组合表示“有什么”。电动汽车是汽车，所以用继承；电动汽车有电池，所以用组合。



## 导入类

和函数一样，类也可以放在模块中。

假设创建文件 `car.py`：

```python
class Car:
    """一次模拟汽车的简单尝试。"""

    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year
        self.odometer_reading = 0

    def get_descriptive_name(self):
        long_name = f"{self.year} {self.make} {self.model}"
        return long_name.title()

    def read_odometer(self):
        print(f"This car has {self.odometer_reading} miles on it.")
```

在另一个文件中导入：

```python
from car import Car

my_new_car = Car("audi", "a4", 2024)
print(my_new_car.get_descriptive_name())
```

如果想在 `car.py` 中临时测试这个类，也可以把测试代码放到 `if __name__ == "__main__":` 下面：

```python
class Car:
    """一次模拟汽车的简单尝试。"""

    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year
        self.odometer_reading = 0

    def get_descriptive_name(self):
        long_name = f"{self.year} {self.make} {self.model}"
        return long_name.title()

if __name__ == "__main__":
    my_car = Car("audi", "a4", 2024)
    print(my_car.get_descriptive_name())
```

这样直接运行 `car.py` 时，会创建汽车实例并打印信息；其他文件 `from car import Car` 时，只会导入 `Car` 类，不会自动执行下面的测试代码。

## 在一个模块中存储多个类

一个模块中可以存储多个相关的类。例如在 `car.py` 中同时保存 `Car`、`Battery`、`ElectricCar`。

```python
from car import ElectricCar

my_leaf = ElectricCar("nissan", "leaf", 2024)
print(my_leaf.get_descriptive_name())
my_leaf.battery.describe_battery()
```

也可以一次导入多个类：

```python
from car import Car, ElectricCar

my_mustang = Car("ford", "mustang", 2024)
my_leaf = ElectricCar("nissan", "leaf", 2024)

print(my_mustang.get_descriptive_name())
print(my_leaf.get_descriptive_name())
```

## 导入整个模块

也可以导入整个模块：

```python
import car

my_mustang = car.Car("ford", "mustang", 2024)
my_leaf = car.ElectricCar("nissan", "leaf", 2024)
```

这种方式调用时需要写模块名，代码稍长，但来源更清楚。

## 使用别名

如果类名或模块名较长，可以使用别名：

```python
from electric_car import ElectricCar as EC

my_leaf = EC("nissan", "leaf", 2024)
```

模块也可以起别名：

```python
import electric_car as ec

my_leaf = ec.ElectricCar("nissan", "leaf", 2024)
```



## 类编写建议

1. 类名使用大驼峰命名法，例如 `Dog`、`ElectricCar`。
2. 实例名和模块名使用小写字母加下划线，例如 `my_dog`、`electric_car.py`。
3. 每个类后面写一个文档字符串，说明这个类表示什么。
4. 类中的方法之间空一行。
5. 模块中可以先写标准库导入，再写第三方库导入，最后写自己写的模块导入。
6. 不要一开始就设计过度复杂的继承关系，先让代码清楚地表示真实问题。
