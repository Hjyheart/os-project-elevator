# os-project-elevator
操作系统课设一 电梯调度

## 开发工具与语言
    工具：Intellij IDEA
    语言：java

## 实现说明
### elevator类
- 定义currentState标识当前电梯状态
- 定义currentFloor标识当前电梯所在楼层
- 定义upStopList和downStopList标识上升停止队列和下降停止队列
- 获取ui线程的按钮队列
- 对三个状态进行检索，通过对按钮的操作实现电梯调度

### ui类
ui的主线程

## 使用说明
- 位于左侧的多选按钮可以选择要去的楼层，有需求的楼层会显示绿色
- 红色按钮代表电梯的位置，电梯初始状态为“－”，在上升和下降时分别为“UP”和“DOWN”
- 电梯在下客时会呈现蓝色，并滞留一段时间

## 注意事项
- 上升的电梯在到达任何楼层时会一次性带走所有上升的乘客
- 下降的电梯在到达任何楼层时会一次性带走所有下降的乘客
    
## 基本算法
### 乘客
- 在乘客提出需求时检索当前所有电梯状态。优先考虑离乘客比较近且将要到达该楼层的移动电梯
- 在没有符合条件的移动电梯的情况下，调动离乘客最近的静止电梯

### 电梯
- 电梯初始状态均为静止，在响应请求时会被设置为上升或下降状态
- 电梯自检状态来变更行为
- 电梯每到一个楼层都会自检下客队列，判断是否下客
- 电梯每到一个楼层都会自检当前楼层对应自己状态的上客队列，判断是否需要在该楼层停下来载客
- 当电梯在某一楼层下光乘客，并且该楼层有乘客要上电梯，电梯将自行变更状态载客运行

## 缺陷
- 没有实现加速度系统
- 没有实现邻近楼层的突然请求的拒绝

## Demo
![Demo][https://github.com/Hjyheart/os-project-elevator/blob/master/%E7%94%B5%E6%A2%AF%E8%B0%83%E5%BA%A6/%E7%94%B5%E6%A2%AFDemo.png]
