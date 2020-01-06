# Thinking In OO

## 类

类是对象的蓝图。

类是共享相同属性、操作、方法、关系或者行为的一组对象的描述符。

## 实例

实例是由类创建的对象。

* 实例的行为和信息结构在类中定义。
* 它的当前状态(实例变量的值)由对它执行的操作决定。

## 继承

一个类获取另一个类的状态和行为，并添加额外的状态和行为。

**"is a"**

​                                                        <img src="C:\Users\Think\AppData\Roaming\Typora\typora-user-images\image-20200104112524847.png" alt="image-20200104112524847" style="zoom:50%;" />

```Java
1 public class Airplane {
2
3   private int speed;
4
5   public Airplane(int speed) {
6   this.speed = speed;
7 }
8
9 public int getSpeed() {
10    return speed;
11 }
12
13 public void setSpeed(int speed) {
14    this.speed = speed;
15 }
16
17 }

```

``` Java
1 public class Jet extends Airplane {
2
3 private static final int MULTIPLIER = 2;
4
5 public Jet(int id, int speed) {
6    super(id, speed);	//引用超类
7 }
8
9 public void setSpeed(int speed) {
10 super.setSpeed(speed * MULTIPLIER);
11 }
12
13 public void accelerate() {
14 super.setSpeed(getSpeed() * 2);
15 }
16
17 }
18
```

沿用父类的方法可以不用再次定义

可以重写父类的方法

可以定义新的方法

## 多态

不同对象类型使用同一接口。

<img src="C:\Users\Think\AppData\Roaming\Typora\typora-user-images\image-20200104163043312.png" alt="image-20200104163043312" style="zoom: 50%;" />

## 组合/聚合

**"has a"**

聚合：表明一个对象包含一组其他对象。

* 传递性
* 不对称性

组合：是一种强的聚合，整体对象控制部分对象的生命周期。

## 封装

封装是隐藏对象的实现细节的过程。内部状态通常是其他对象无法访问的，操作对象数据的唯一途径是通过它的接口。

规则：一个对象应该只显示与它交互所需的接口。与对象的使用无关的细节应该对其他对象隐藏。

建议：用getters和setters方法

## 接口

接口描述类的用户如何与类交互。

Example：

![image-20200104165359179](C:\Users\Think\AppData\Roaming\Typora\typora-user-images\image-20200104165359179.png)

## 抽象

抽象表示一个对象与其他所有对象相区别的基本特征，因此提供了同观察者角度有关的清晰定义的概念界限。

抽象就是过滤掉对象的一部分特性和操作，直到只剩下**你所需要**的属性和操作。

抽象的质量通过两个指标来衡量：

* 内聚性，即如果抽象能够简洁地代表一种清晰的概念，那么抽象是内聚的。一个类的所有属性和方法必须直接和概念的表示相关。
* 耦合度，即与相关联的类的耦合程度。如果耦合度高，那么重用性就低，因为该抽象与系统中的其它模块相关以致于很难单独维护。

# Analysis & Design

## 概览

分析：强调的是对问题和需求的调查研究。

* do the right thing

设计：强调的是满足需求的概念上的解决方案。

* do the thing right

OOA(Object-oriented analysis)：发现和描述问题领域中的对象或概念。

OOD(Object-oriented design)：定义软件对象以及它们如何协作以满足需求。

**良好的对象设计：**

* Architectural cohesion 架构性的内聚
* Reusability 可重用性
* Maintenance 可维护性
* Scalability 可扩展性
* Flexibility 灵活性

### 示例

用例 -> 领域模型 -> 交互图 -> 类图

**领域模型：**问题领域的概念类以及真实对象的可视化表示。

**低表示差异：**OO设计和语言能够缩小软件构件和我们所设想的领域模型之间的差距。

大的复杂系统的开发有两种主要的分析方法：

* 面向功能的分析
* 面向对象分析

面向对象分析主要步骤：

* 识别对象
* 组织对象
* 定义对象之间的关系
* 定义对象的操作
* 定义对象内部细节

## 名词法

**领域模型**：表示了问题领域的“概念”及其关系。（没有定义操作的类图）

**出现在UP的细化阶段**

* 概念
* 概念之间的关系
* 概念的属性

**面向对象分析与结构化分析之间的最大差异是：前者根据对象划分系统，后者根据功能。**

### 方法

* 在问题领域的文本描述中，标识出名词、名词短语，把它们作为候选的概念类或者属性 

* 对发现的名称（短语）进行分析，辨别是合适的概念类吗？概念可以合并吗？等等

* 定义概念类之间的关系

* 定义概念类的属性

## 分析模型法

特性： 行为-信息-表现

实体类：<img src="C:\Users\Think\AppData\Roaming\Typora\typora-user-images\image-20200104234218973.png" alt="image-20200104234218973" style="zoom: 50%;" />

* 实体对象对显示系统状态的信息建模。这些信息通常用于记录操作的效果，因此与系统的行为相关。

边界类：<img src="C:\Users\Think\AppData\Roaming\Typora\typora-user-images\image-20200104234244505.png" alt="image-20200104234244505" style="zoom:50%;" />

* 边界/接口对象对输入和输出以及处理它们的操作建模

控制类：<img src="C:\Users\Think\AppData\Roaming\Typora\typora-user-images\image-20200105190017112.png" alt="image-20200105190017112" style="zoom: 67%;" />

* 控制对象对功能/操作进行建模，以验证和决定是否处理接口对象的信息并将其传递给实体对象，或者反过来。

<img src="C:\Users\Think\AppData\Roaming\Typora\typora-user-images\image-20200104234324904.png" alt="image-20200104234324904" style="zoom: 50%;" />

# 面向对象设计

**分配职责是关键。**

### RDD(Responsibility Driven Design)

* 认知职责
  * 私有封装的数据
  * 相关的对象
  * 能够导出或计算的事物
* 行为职责
  * 自身执行的一些行为
  * 初始化其他对象的一些动作
  * 控制和协调其他对象的动作

## CRC

类：**C**lasses (of objects)

职责：**R**esponsibilities (of the objects in each class)

协作：**C**ollaborations (with objects in other classes)

# Operation Contrast

### 契约形式

* 操作：操作的名称和参数
* 交叉引用：会发生此操作的用例
* 前置条件：执行操作之前，对系统或领域模型对象状态的重要假设
* 后置条件：完成操作后，领域模型对象的状态（结果-过去时）

{ *P* } **A** { *Q* }

**出现在UP的细化阶段**

前置条件可以被相等或者更弱的条件替代；后置条件可以被相等或者更强的条件替代。

### 后置条件

类型

* 创建或者删除实例
* 属性值的变化
* 形成或消除关联

# 逻辑架构

逻辑架构是软件类的宏观组织结构。

* Layer（层）：是对类、包或子系统的甚为粗粒度的分组，具有对系统费主要方面加以内聚的职责。
* Package（包）：一组内聚性相关的类

![image-20200105011002554](C:\Users\Think\AppData\Roaming\Typora\typora-user-images\image-20200105011002554.png)

**层结构的优点：**

* 使关系分离、高级服务与低级服务分离。减少耦合和依赖性、增强内聚性、提高潜在的复用性并且使概念更加清晰
* 封装和分解相关的复杂性
* 某些层能够被新的实现所替换
* 较低层包含可复用功能
* 某些层可以是分布式的
* 有助于团队开发

# 对象模型

动态：有助于设计逻辑、代码行为或方法体

* 交互图（顺序图或通信图）

静态：有助于设计包、类名、属性或方法特征标记的定义

* 类图

# GRASP

见iPad

# More GRASP patterns

## 多态(Polymorphism)

Q：如何处理**基于类型**的选择？如何创建可插拔的软件构件？

S：使用多态操作为依据类型变化的行为进行职责分配。

<img src="C:\Users\Think\AppData\Roaming\Typora\typora-user-images\image-20200105202342187.png" alt="image-20200105202342187" style="zoom: 67%;" />

优点：

* 易于增加新变化所需的扩展
* 无需影响客户便能够引入新的实现

## 纯虚构(Pure Fabrication)

Q：既不违反低耦合、高内聚或其他的原则，但依据信息专家原则获得的解决方案又不合适的情况下，如何把职责分配给对象？

S：把高度内聚的职责分配给人为虚构出来的一个类，这个类在领域模型里没有对应的概念。

优点：

* 支持高内聚
* 增加了潜在的复用性

## 间接性(Indirection)

Q：如何分配职责来避免两个或多个对象之间的直接耦合？如何解耦对象以保持低耦合并提高复用性潜力？

S：将职责分配给中间对象，以便在其他组件或服务之间进行协调，使它们不直接耦合。

优点：

* 实现了构件之间的低耦合

## 防止变异(Protected Variations)

Q：如何设计对象、系统和子系统，使其内部的变化和不稳定性不会对其他元素产生不良影响?

S：识别预计变化或不稳定之处，分配职责用以在这些变化之外创建稳定接口。

> Liskov替换原则(LSP)：
>
> 1）子类可以实现父类的抽象方法，但不能覆盖非抽象方法
> 2）子类可以新增自己的方法
> 3）子类重载父类方法时，方法的前置条件（即形式参数）要比父类的参数更宽松
> 4）子类实现父类抽象方法时，方法的后置条件（即返回值）要比父类的返回值更严格

> 迪米特法则(Law of Demeter)：
>
> 如果两个类没有其他理由直接相互感知或以其他方式耦合，那么这两个类就不应该直接交互。
>
> <img src="C:\Users\Think\Documents\Tencent Files\1272091180\Image\SharePic\20200105210345.png" alt="20200105210345" style="zoom: 50%;" />
>
> 在方法里只与以下对象发送消息：
>
> * this对象（自身）
> * 方法的参数
> * this的属性
> * 作为this属性的集合中的元素
> * 在方法中创建的对象

# GoF设计模式

模式：

* 一个反复出现的问题的解决方案
* 不是一个“具体的”解决方案，而是它的一个抽象版本
* 包含
  * 名称
  * 问题
  * 解决办法
  * 结果
* 作用：
  * 解决特定的设计问题
  * 减少重新设计的需要
  * 提供可重用的解决方案作为模板
  * 将知识从专家传递给新手

## 单例模式(Singleton)

问题：某个类只能实例化一个对象

解决方案：对类定义静态方法用以返回单实例

![20200105221204](C:\Users\Think\Documents\Tencent Files\1272091180\Image\SharePic\20200105221204.png)

![20200105230157](C:\Users\Think\Documents\Tencent Files\1272091180\Image\SharePic\20200105230157.png)

```Java
public class ServicesFactory{
    private static ServicesFactory();
    private static ServicesFactory instance = new ServicesFactory();
    public static ServiceFacotory getInstance{
        return instance;
    }
}
//SingleTon的三个关键点
//1）私有的： 构造函数
//2）私有的：成员变量，记录这个单实例
//3）公有的get函数：没有实例时创建它；已有实例则返回该实例。

```

单例模式在多线程时可能会出现问题。

在大多数情况下是不必要。

## 适配器模式(Adapter)

问题：如何解决接口不相容的问题，或者如何为具有不同接口的类似构件提供稳定的接口？

解决办法：通过中介适配器对象，将构件的原有接口转换为其他接口。

![20200105222633](C:\Users\Think\Documents\Tencent Files\1272091180\Image\SharePic\20200105222633.png)

![20200105230038](C:\Users\Think\Documents\Tencent Files\1272091180\Image\SharePic\20200105230038.png)

Adapter实现的是目标类的接口，从而将Adaptee伪装者成Target

## 外观模式(Facade)

问题：对一组完全不同的实现或接口（例如子系统中的实现和接口）需要公共、统一的接口，可能会与子系统内部的大量事物产生耦合，或者子系统的实现可能会改变，怎么办？

解决办法：提供对子系统进行访问的部分功能的接口并进行封装。

![20200105224708](C:\Users\Think\Documents\Tencent Files\1272091180\Image\SharePic\20200105224708.png)

![20200105230122](C:\Users\Think\Documents\Tencent Files\1272091180\Image\SharePic\20200105230122.png)

创建一个新的接口

## 外观模式和适配器模式的区别

* Facade定义了一个新的接口，而Adapter使用了一个旧的接口
* Facade通常封装多个对象，而Adapter封装单个对象
* Facade对象通常是单例的，因为只需要一个Facade对象

## 观察者模式(Observer)

![20200105231935](C:\Users\Think\Documents\Tencent Files\1272091180\Image\SharePic\20200105231935.png)

## 策略模式(strategy)

![20200105233934](C:\Users\Think\Documents\Tencent Files\1272091180\Image\SharePic\20200105233934.png)

## 简单工厂模式(Simple Factory)

![20200106002903](C:\Users\Think\Documents\Tencent Files\1272091180\Image\SharePic\20200106002903.png)

## 工厂模式(Factory)

![20200106002917](C:\Users\Think\Documents\Tencent Files\1272091180\Image\SharePic\20200106002917.png)

## 命令模式

![20200106005406](C:\Users\Think\Documents\Tencent Files\1272091180\Image\SharePic\20200106005406.png)

## 组合模式

![image-20200106011748236](C:\Users\Think\AppData\Roaming\Typora\typora-user-images\image-20200106011748236.png)

# **面向对象设计原则**

## 不好的设计的特点

* Rigidity (僵硬性)

  * code difficult to change

  * management reluctance(拒绝) to change anything becomes policy
* Fragility (易碎性)
  * even small changes can cause cascading effects
  * code breaks in unexpected places

* Immobility(固定性)
  * code is so tangled(纠结) that it's impossible to **reuse** anything

* Viscosity(黏滞性)
  * much easier to hack(乱砍) than to preserve original design

## OCP原则

**Open for Extension** - the behavior can be extended to meet new requirements

 **Closed** **for Modification** - the source code of the module is not allowed to change

拥抱变化但不改变以前的代码

### OCP启发

**使所有对象数据私有，没有全局变量。**

* 对公共数据的更改对“打开”模块会有风险
  * 可能会产生涟漪效应，需要在许多意想不到的地方进行改变;
  * 错误可能很难完全找到和修复。修复的话也可能会在其他地方导致错误。

## 优先选择组合而不是继承

### 继承

>继承破坏了封装
>
>* 导致超类和子类之间的高耦合

继承是静态/编译时绑定

* 如果要修改必须经过编辑-编译-调试...的周期

必须导入整个包

  * 不能仅访问超类的部分行为，必须全部访问。

超类定义了物理表示方式

  * Eg：超类使用列表数据结构，而子类使用树结构会更有效
  * 子类通常直接地引用公共和受保护的数据成员，这意味着在超类中更改实现细节会影响所有子类
  * 必须阅读超类代码才能完全理解(与只阅读接口不同)

### 组合

组合是动态/运行时绑定

* 可以通过“切换”对象引用来改变运行时的行为

通过边界接口解耦

> 没有破坏封装

明确职责分工

* 每个对象都明确地集中在一个/几个任务上
  * 更容易理解
  * 更容易维护
* 只要阅读接口就能理解
* 更容易进行隔离测试
* 每个类都很小
* 具有更大的重用潜力

## 依赖倒置原则(DIP-Dependency Inversion Principle)

> 高级模块不应该依赖于低级模块。两者都应该依赖于抽象。
>
> 抽象不应该依赖于细节。细节应该依赖于抽象

继承层次结构中的基类不应该知道它的任何子类

**OCP说明了目标;DIP说明了机制**

### DIP启发

依赖倒置原则的核心思想是**面向接口编程**，而不是面向实现编程

* 使用继承来避免直接绑定到类

![20200106015803](C:\Users\Think\Documents\Tencent Files\1272091180\Image\SharePic\20200106015803.png)

避免传递依赖关系

* 避免高层依赖低层抽象的结构

  ![20200106015818](C:\Users\Think\Documents\Tencent Files\1272091180\Image\SharePic\20200106015818.png)

* 使用继承和抽象类来有效地消除传递依赖

  ![20200106015825](C:\Users\Think\Documents\Tencent Files\1272091180\Image\SharePic\20200106015825.png)

当有疑问时，增加间接的层次

* 如果你对你设计的类找不到满意的解决方案，试着把责任委派给一个或多个类

  ![20200106020010](C:\Users\Think\Documents\Tencent Files\1272091180\Image\SharePic\20200106020010.png)
  
* 删除或绕过现有的间接层通常比以后添加它们更容易

  ![20200106020157](C:\Users\Think\Documents\Tencent Files\1272091180\Image\SharePic\20200106020157.png)

### 推论

如果一个类/模块是具体的，但是非常稳定，那么这个原则可以放宽。

## 里氏替换原则

子类可以替代父类

里氏替换原则讲的是基类和子类的关系，指任何基类可以出现的地方，子类一定可以出现

* 继承必须保证超类中所拥有的性质在子类中仍然成立，也就是说子类必须能够替换成它们的基类
* Liskov替换原则主要用来约束继承的泛滥问题。

目的：增加程序的健壮性，需求变更时也可以保持良好的兼容性和稳定性，即使增加子类，原有的子类可以继续运行