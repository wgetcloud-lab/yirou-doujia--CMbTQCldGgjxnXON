[合集 \- manim(33\)](https://github.com)[1\.【manim动画教程】\-\- 安装2023\-03\-28](https://github.com/wang_yb/p/17264724.html)[2\.【manim动画教程】\-\- 基本图形2023\-03\-29](https://github.com/wang_yb/p/17269340.html)[3\.【manim动画教程】\-\- 坐标系2023\-04\-10](https://github.com/wang_yb/p/17301528.html)[4\.【manim动画教程】\-\- 文本样式2023\-04\-07](https://github.com/wang_yb/p/17294918.html)[5\.【manim动画教程】\-\- 文字和公式2023\-04\-04](https://github.com/wang_yb/p/17285467.html)[6\.【manim动画教程】\-\- 图形样式2023\-03\-31](https://github.com/wang_yb/p/17275154.html)[7\.【manim动画教程】\-\-相机2023\-04\-19](https://github.com/wang_yb/p/17334029.html)[8\.【manim动画教程】\-\-高级动画效果2023\-04\-14](https://github.com/wang_yb/p/17317576.html)[9\.【manim动画教程】\-\-常用动画效果2023\-04\-12](https://github.com/wang_yb/p/17309865.html)[10\.【manim】之滚动字幕2022\-12\-06](https://github.com/wang_yb/p/16955924.html)[11\.【manim】之圆规动画2023\-01\-31](https://github.com/wang_yb/p/17079903.html)[12\.【manim】之目录动画2023\-02\-28](https://github.com/wang_yb/p/17163051.html)[13\.manim边学边做\-\-DecimalNumber06\-12](https://github.com/wang_yb/p/18243662)[14\.manim边学边做\-\-Integer06\-13](https://github.com/wang_yb/p/18245670)[15\.manim边学边做\-\-Variable06\-14](https://github.com/wang_yb/p/18248823)[16\.manim边学边做\-\-Title06\-20](https://github.com/wang_yb/p/18258229)[17\.manim边学边做\-\-BulletedList06\-21](https://github.com/wang_yb/p/18261017):[楚门加速器p](https://tianchuang88.com)[18\.manim边学边做\-\-SingleStringMathTex06\-23](https://github.com/wang_yb/p/18264154)[19\.manim边学边做\-\-MathTex06\-28](https://github.com/wang_yb/p/18272507)[20\.manim边学边做\-\-Tex07\-01](https://github.com/wang_yb/p/18278554)[21\.manim边学边做\-\-Text07\-04](https://github.com/wang_yb/p/18284013)[22\.manim边学边做\-\-Paragraph07\-09](https://github.com/wang_yb/p/18291657)[23\.manim边学边做\-\-MarkupText07\-10](https://github.com/wang_yb/p/18294000)[24\.manim边学边做\-\-Code07\-16](https://github.com/wang_yb/p/18304450)[25\.manim边学边做\-\-Matrix07\-17](https://github.com/wang_yb/p/18307871)[26\.manim边学边做\-\-Table07\-25](https://github.com/wang_yb/p/18322456)[27\.manim边学边做\-\-点08\-09](https://github.com/wang_yb/p/18351279)[28\.manim边学边做\-\-圆形类08\-15](https://github.com/wang_yb/p/18361469)[29\.manim边学边做\-\-圆弧形08\-20](https://github.com/wang_yb/p/18368851)[30\.manim边学边做\-\-直线类08\-22](https://github.com/wang_yb/p/18374417)[31\.manim边学边做\-\-带箭头直线09\-02](https://github.com/wang_yb/p/18392446)[32\.manim边学边做\-\-曲线类09\-04](https://github.com/wang_yb/p/18396028)33\.manim边学边做\-\-角度标记09\-07收起
`manim`中绘制一个角度其实就是绘制两条直线，本篇介绍的不是绘制角度，而是绘制**角度标记**。


对于**锐角**和**钝角**，**角度标记**是一个弧，弧的度数与角的度数一样；


对于**直角**，**角度标记**是一个垂直的拐角。


`manim`中关于**角度标记**的模型主要有3个：


1. `Angle`：根据两条直线绘制角度标记
2. `RightAngle`：根据两条**互相垂直**的线绘制直角标记
3. `Elbow`：不受限于直线，任意方向和大小的直角标记


其中，`RightAngle`模块继承自`Angle`。


![](https://img2024.cnblogs.com/blog/83005/202409/83005-20240907110849829-2077972424.png)


**角度标记**的主要作用是在动画中标记出一些特殊角度，更好的展示数学定理的证明过程。


# 1\. 主要参数


`Angle`模块是通用的角度标记，它的主要参数有：




| **参数名称** | **类型** | **说明** |
| --- | --- | --- |
| line1 | Line | 构成角度的第一条线 |
| line2 | Line | 构成角度的第二条线 |
| radius | float | 角度标记的半径 |
| quadrant | Point2D | 此参数控制角度标记显示在哪个位置 |
| other\_angle | bool | `True`：顺时针从line1到line2`False`：逆时针从line1到line2 |
| dot | bool | 是否在角度标记中显示一个点 |
| dot\_radius | float | 点的半径 |
| dot\_distance | float | 点到圆弧（角度标记）的相对距离 |
| dot\_color | Color | 点的颜色 |
| elbow | bool | 是否显示成直角的形状 |


后面在使用示例中演示这些参数的使用。


`RightAngle`模块继承自`Angle`，除了上面`Angle`的参数之外，还有一个自己特有的参数。




| **参数名称** | **类型** | **说明** |
| --- | --- | --- |
| length | float | 标记的大小 |


`Elbow`模块与上面两个不一样，它不是根据两条线来生成角度标记。




| **参数名称** | **类型** | **说明** |
| --- | --- | --- |
| width | float | 标记的大小 |
| angle | float | 标记朝向那个方向 |


`Elbow`的形状和`RightAngle`是一样的。


# 2\. 主要方法


`Angle`模块的方法主要有3个：




| **名称** | **说明** |
| --- | --- |
| from\_three\_points | 根据三个点来生成角度标记 |
| get\_lines | 获取生成角度的两条线 |
| get\_value | 获取角度的值 |


一般我绘制一个角度标记时，都是根据两条相交的线来确定角度位置的。


通过`from_three_points`方法，可以根据任意3个点来生成一个角度标记。



```
A = np.array([2, -1, 0])
B = np.array([0, 0, 0])
C = np.array([1, 1, 0])

angle = Angle.from_three_points(A, B, C)

```

函数的参数是`A`，`B`，`C`三个点，


* A：角度的起点
* B：角度的顶点
* C：角度的终点


生成的角度以`B`为顶点，从点A到点C逆时针旋转。


![](https://img2024.cnblogs.com/blog/83005/202409/83005-20240907110849878-404070963.gif)


方法`get_lines`可获取构成角度的两条线，也就是上图中的`BA`，`BC`两条线。



```
lines = angle.get_lines()

```

最后，`get_value`方法，可以实时得到当前角度的值，值可以是度数，也可以是弧度。



```
print(f"角度：{angle.get_value(degrees=True)}")
print(f"弧度：{angle.get_value()}")

# 运行结果
角度：71.56505117707799
弧度：1.2490457723982544

```

# 3\. 使用示例


## 3\.1\. 角度大小


因为角度标记`Angle`是一个弧形，所以角度的大小通过参数`radius`（半径）来调整。



```
line1 = Line(LEFT, RIGHT)
line2 = Line(DOWN, UP)

Angle(line1, line2)
Angle(line1, line2, radius=0.2)
Angle(line1, line2, radius=0.5)
Angle(line1, line2, radius=0.8)

```

![](https://img2024.cnblogs.com/blog/83005/202409/83005-20240907110849864-662632714.gif)


## 3\.2\. 角度位置


角度标记的位置由两个参数来控制，`quadrant`和`other_angle`。


`quadrant`参数一共有四种选项：`(1, 1)`或`(1, -1)`或`(-1, 1)`或`(-1, -1)`


这个参数分两部分，分别表示角度标记在`Line1`上的**起点位置**和在`Line2`上的**终点位置**。


比如下面相交的两条直线，`quadrant`的第一个值和第二个值分别在`Line1`和`Line2`上的位置如图。


![](https://img2024.cnblogs.com/blog/83005/202409/83005-20240907110849658-967025837.png)


`other_angle`默认为`False`，表示绘制角度时从`Line1`到`Line2`；


设置`other_angle`为True时，绘制角度的顺序相反，从`Line2`到`Line1`。



```
l1 = Line(
    LEFT + (1 / 3) * UP,
    RIGHT + (1 / 3) * DOWN,
)
l2 = Line(
    DOWN + (1 / 3) * RIGHT,
    UP + (1 / 3) * LEFT,
)

Angle(l1, l2)
Angle(l1, l2, quadrant=(1, -1))
Angle(l1, l2, quadrant=(-1, 1))
Angle(l1, l2, quadrant=(-1, -1))
Angle(l1, l2, other_angle=True)
Angle(l1, l2, quadrant=(1, -1), other_angle=True)
Angle(l1, l2, quadrant=(-1, 1), other_angle=True)
Angle(l1, l2, quadrant=(-1, -1), other_angle=True)


```

![](https://img2024.cnblogs.com/blog/83005/202409/83005-20240907110849628-581521788.png)


## 3\.3\. 角度中的点


`Angle`中可以加一个点的标记，当一个画面中有很多角度的时候，这个标记可以帮助我们区分不同的角。


通过`dot_radius`，`dot_distance`和`dot_color`等参数，可以调整点的大小，位置和颜色。



```
line1 = Line(
    LEFT / 2,
    RIGHT / 2,
)
line2 = Line(
    DOWN / 2,
    UP / 2,
)

Angle(
    line1,
    line2,
    dot=True,
    dot_radius=0.02,
    dot_color=RED,
)
Angle(
    line1,
    line2,
    dot=True,
    dot_radius=0.08,
    dot_color=BLUE,
)
Angle(
    line1,
    line2,
    dot=True,
    dot_distance=0.2,
    dot_color=GREEN,
)
Angle(
    line1,
    line2,
    dot=True,
    dot_distance=0.8,
    dot_color=YELLOW,
)

```

![](https://img2024.cnblogs.com/blog/83005/202409/83005-20240907110849593-1569875604.gif)


## 3\.4\. 直角标记


最后，还有一个特殊的角度标记\-\-直角标记。


`manim`中提供了2个模块来标记直角，`RightAngle`和`Elbow`。


它们的显示效果差不多，区别在于，`RightAngle`需要根据两条线来生成，


而`Elbow`更加灵活一些，它可以在任意位置生成直角标记。



```
line1 = Line(
    LEFT / 2,
    RIGHT / 2,
)
line2 = Line(
    DOWN / 2,
    UP / 2,
)

RightAngle(
    line1,
    line2,
    length=0.2,
)
RightAngle(
    line1,
    line2,
    length=0.4,
)
RightAngle(
    line1,
    line2,
    quadrant=(1, -1),
)
RightAngle(
    line1,
    line2,
    quadrant=(-1, -1),
)
Elbow(width=0.5)
Elbow(width=1)
Elbow(width=1, angle=PI / 2)
Elbow(width=1, angle=5 * PI / 4)


```

![](https://img2024.cnblogs.com/blog/83005/202409/83005-20240907110849593-2123419777.gif)


# 4\. 附件


文中完整的代码放在网盘中了（`angle.py`），


下载地址: [完整代码](https://github.com) (访问密码: 6872\)


