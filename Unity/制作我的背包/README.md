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

### 3、背包物品信息的显示

Slot 表示我的背包界面中MaterialGrid的小格子
InventoryManager 连接ui与数据，将背包里物品信息显示在我的背包界面

### 4、实现拖拽效果(DragHandler接口)
