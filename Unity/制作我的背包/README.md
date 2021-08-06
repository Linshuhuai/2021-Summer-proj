# 制作我的背包
## 参考资料

B站视频教程：https://www.bilibili.com/video/BV1YJ41197SU/?p=2&spm_id_from=pageDriver

参考的一个游戏背包系统的框架：https://www.processon.com/view/link/5c651a9ce4b0c4e2165357fe

## 实现过程
### 1、UI图形界面设置
* 想在Unity直接使用.png格式的图片，要设置图片Inspector面板中texture type的选项为Sprite（2D and UI）
* Button可以通过设置以下内容控制对象的显示与否
* 使用Grid Layout Group

![8abd48b6e327b805d15fcba6dc2a7a0](https://user-images.githubusercontent.com/68037461/126873534-db447df4-9570-47b6-ba12-3d4683da9d1d.png)

### 2、数据库存储方法

ScriptableObject

Inventory 背包类
Item 物品类
InventoryManager 背包控制类

#### 使用静态类变量存储实现单例

   在场景FindMaterial场景中，hierachy里面有一个叫做InventoryManager的GameObject，并且这个物体还有挂着其他类型的子物体（BagCanvas）。需要保证这个物体在切换场景后仍然存在，并且只存在一个。
具体代码见InventoryManager，其中要注意Awake函数中Destroy和DontDestroyOnLoad的运用，后者保证这个物体在切换场景后仍然存在，前者保证该物体只存在一个。

**另外，挂在这个脚本上的子物体不能直接被当作函数的载体，因为这个物体在切换场景后回到原场景是有变化的。**  
  E.G. BagCanvas里面有一个closeButton按钮，用于控制BagCanvas的显示与否，如果直接在Button的OnClick属性对BagCanvas使用SetActive(false)函数，在切换场景后回到原场景会失效。一个正确的方法是在InventoryManager脚本里加一个Button变量closeButton，closeButton实例化为closeButton，用`closeButton.onClick.AddListener(SetActiveFalse)`控制按钮开关。

### 3、背包物品信息的显示

Slot 表示我的背包界面中MaterialGrid的小格子，包括 slotItem（Item 类型）和 slotImage（Image 类型）两个参数，前者保存物体的信息，后者保存物体在背包中显示的icon图片。

InventoryManager 连接ui与数据，将背包里物品信息显示在我的背包界面。其中CreateNewItem函数将收集到的物体展示在背包里，RefreshItem函数更新物品槽。每次打开背包的时候要调用RefreshItem函数更新一下。

### 4、实现拖拽效果(DragHandler接口)
