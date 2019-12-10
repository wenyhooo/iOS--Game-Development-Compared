# iOS--Game-Development-Compared


|            | metal          | metalKit       |OpenGl ES 2.0 |OpenGl ES 3.0 |SpriteKit     |Unity         |SceneKit      |
| ---------- | :-----------:  | :-----------:  |:-----------: |:-----------: |:-----------: |:-----------: |:-----------: |
| 机型        | 64位          |64位            | 32位          |64位          |  32位        |跨平台         |  32位        
| 系统        | iOS 8 + A7    |iOS 9 + A7      | iOS8          |iOS8          |  iOS7        |依赖untiy版本  |  iOS8       |
|      模型   | 3D             |3D             | 3D           |3D              |  2D          |3D            |  3D        |
|    语言      | OC/Swift     |OC/Swift       | C              |C              |  OC/Swift     |  C#          |OC/Swift     |
|空工程包大小  | 0M              |0M          | 0M              |0M            |  0M            |  28.2M        |0M        |
|上手程度     |     较难         |较难          | 难             |难            |  简单          |  较难        |一般        |

- iPhone 5、iPhone 5c、iPad 4都是32位机器。
- iOS11之后不再支持32位机器, iPhone5S和ipad air、 A7处理器之后都64位，以前的机器、处理器是32位。
- iPhone5S和ipad air之后的机型都是64位，以前的版本都是32位的老机型。
____________________________________________________________

- OpenGL ES2.0发布于2004年
- OpenGL ES3.0发布于2008年
- WWDC 2018, apple已宣布在iOS12之后,iOS/ Mac OS系统将弃用OpenGL/CL,  目前在iOS13API中,  GLKit和OpenGL ES 都被标记为Deprecated。
- 现代GPU的渲染管线已经更新迭代,发生变化, 古老的OpenGl ES2.0已经无法使用现代图形技术的发展, 不支持多线程操作,不支持异步处理, OpenGL本身设计存在的问题已经影响了GPU真正的性能发挥. 为此Apple设计Metal。

### Metal:
苹果为了苹果机器而创建,基于Foundation,使用GCD在CPU和GPU之间保持同步,它是更先进的GPU管道抽象,而OpenGL ES只能自己手动重写,比较考验开发实力, 想要充分发挥硬件性能的开发者来说,选择官方的Metal可以进行更快的并行计算,得到优势。
##### Metal主要优化:
  - 最小化GPU工作时CPU的消耗,与OpenGl ES相比,显著降低了消耗. OpenGL在创建缓冲区还是纹理,它都会复制一份以防止GPU在使用它们的时候被意外访问,这样的复制操作,是非常耗时的. 而Metal并不复制资源。
  - Metal另一个显著优势:预估GPU状态来避免多余的验证和编译, 通常在OpenGL中, 需要一次设置GPU的状态,在每个绘制指令draw call之前需要验证新的状态.而Metal选择了另外一种方法,渲染路径对象可以被多个不同资源共同使用,一个渲染路径无需更进一步的验证,使API的消耗降到最低, 从而增加每帧的绘制指令的数量。
  - Metal为了速度在安全性做出的妥协, 导致在开发过程中出了问题可能是完全随机的效果,例如闪屏和崩溃等,而OpenGL ES则通常是黑屏。

### SpriteKit：
- 是苹果在 2013 年推出来的 2D 游戏开发框架,它最初的设计很多来自 Cocos2D-iPhone 项目，特别是 API 方面，几乎和 Cocos2D-iPhone 没有差别，所以Cocos2D 用户可以用很小的成本转到 SpriteKit 上面来。
- 已有的 SpriteKit 游戏跑在 iOS 9 上面，不需要做任何修改即可享受 Metal 带来的性能提升。如果你的设备支持 Metal, 那么它就会使用 Metal, 反之则切换到 OpenGL ES.
### SceneKit：
- 和SpriteKit一样建立在OpenGL/Metal的基础上,cocoa下的3D渲染框架, 组件几乎都是面向对象,可以用熟悉的iOS开发语言编写

### 一个unity 空工程打包到appstore 安装大小为28.2MB, 实际下载大小为17.3MB
