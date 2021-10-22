# Matlab/Simulink

##### 基础知识

- Simulink文件的扩展名：`.slx`或`.mdl`。两者区别在于slx是二进制文件，mdl是文本格式文件。slx旨在取代mdl文件。

- matlab代码文件的扩展名为`.m`
- Matlab/Simulink低版本无法打开高版本文件，保存成低版本对应的文件版本方可打开
- simulin快捷键![image-20211022170853337](C:\Users\123\Program\VCU\basic\image-20211022170853337.png)



## Simulink建模基础

#### Simulink模块

##### 模块库：

1. Simulink模块库包含公共模块库和专业模块库
2. 公共模块库包含常用模块库等16个子库
3. 控制策略开发主要基于公共模块库中的模块

##### 模块：

- 模块是构成Simulink模型的元素，将各种模块信号相连，可完成相应的逻辑连接，实现相应的功能
- Simulink的强大之处在于它提供了丰富的标准模块库

##### Simulink基础模块—掌握其使用方法

1. 四则运算模块
2. 关系操作模块
3. 逻辑运算模块
4. 延时模块
5. 选择开关模块
6. 查表模块

模型的仿真

## Stateflow建模基础

##### 创建Stateflow模型

方法1：在Simulink库中找到Stateflow模块库的chart模块，将其添加到Simulink开发环境中

方法2：在Matlab命令行窗口输入命令`sf`，即可打开Stateflow工具箱`sflib`,并创建新的包含chart模块的Stateflow模型文件

##### Stateflow框图形式分类

- 在Stateflow模型中，将包含由状态的Stateflow框图成为状态图

- 在Stateflow模型中，讲不包含任何状态的Stateflow框图称为流程图

##### note：

1. 流程图不能包含任何状态，只能依靠连接节点完成通路的连接和判断分支

### 状态图（state)：

##### 状态名

添加的状态通过左上角`?`来表示目前状态还没有具体定义。

状态名命名要以字符开始

##### 状态标签

组成

1. 状态名称
2. 注释（可省略）`%注释内容`
3. 响应的状态动作

##### 状态动作

状态动作的关键字有三种：

1. entry/en:在状态被激活的**那一时刻**所执行的动作
2. exit/ex：当状态退出活动状态是执行相应的动作
3. during/du：当状态保持活动状态时执行相应的动作

### 连接节点(Junction)

NOTE:

- 连接节点不是记忆元件，在状态图中任何转移的执行都不能停留在节点上，转移必须到达某个状态才能停止

- 依靠连接节点完成通路的连接和判断分支

### 转移

概述：

- 当转移发生时，原装胎变为非活动状态，目标状态变为活动状态
- 从图形上看，转移是带有箭头的线，是整个状态图或流程图变成了有向图

##### 默认转移

默认转移是一类特殊的状态转移。根据要求，当有限状态系统被激活时，必有相应的确定的某个状态被激活

##### 转移标签

- 一个完整的转移标签由四部分组成`event[conditon]{conditon actions}/{transtion actions}`
- 转移标签的四个部分不一定完整出现，但不论出现哪些内容，标签内容必须按顺序写

##### 转移优先级

1. 父状态转移优先于子状态转移
2. 同一层级安装**执行序号**转移

## 流程图

简介：

- 流程图是不包含状态的Stateflow框图。流程图当中没有状态，主要用到的图形对象是连接节点和转移，用到的非图形对象就是数据对象

- 流程图总是从默认转移开始执行
- 流程图在无有效转移分支的节点上中止
- 连续的两次触发之间，流程图一直处于非活动状态

结构：

1. 顺序结构 
2. 选择结构
3. 循环结构
