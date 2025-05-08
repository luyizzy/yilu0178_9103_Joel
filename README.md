# Quiz 8

## Part 1: Imaging Technique Inspiration  
我选择的灵感来源于乔治·修拉（Georges Seurat）的点彩画法（Pointillism），尤其是其代表作《大碗岛的星期天下午》。点彩画通过密集的纯色小点并置，利用人眼的视觉混合效果形成整体画面。我希望在项目中借鉴这种"离散单元组合成连续图像"的视觉逻辑，通过程序化生成的粒子或图形元素构建动态画面。这种技术能自然适配数字媒介的像素本质，同时赋予作品复古与科技的矛盾美感，符合作业对"媒介实验性"的要求。

![The Sunday Afternoon on the Island of La Grande Jatte](readmeImages/seurat.jpg)  
*图1：修拉《大碗岛的星期天下午》（1886）*

![Pointillism Detail](readmeImages/detail.jpg)  
*图2：点彩画局部细节*

---

## Part 2: Coding Technique Exploration  
参考[p5.js粒子系统示例](https://openprocessing.org/sketch/1919992)，该代码通过动态生成粒子并控制其位置、颜色与运动轨迹，模拟了类似点彩画的视觉效果。关键技巧包括：  
- **粒子密度控制**：通过`particleCount`参数调节点的疏密  
- **颜色噪声混合**：使用柏林噪声生成颜色渐变  
- **动态笔触**：粒子随鼠标移动重组  

```javascript
// 代码片段示例
function setup() {
  createCanvas(800, 800);
  pixelDensity(1);
}

function draw() {
  loadPixels();
  for (let x = 0; x < width; x++) {
    for (let y = 0; y < height; y++) {
      let n = noise(x * 0.01, y * 0.01); // 柏林噪声
      let col = color(n * 255, 100, 150); // 颜色混合
      set(x, y, col);
    }
  }
  updatePixels();
}