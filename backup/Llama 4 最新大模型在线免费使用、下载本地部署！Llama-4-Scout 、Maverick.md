AI界从来没有“周末”这个词，连硅谷也不休息！

![](https://www.freedidi.com/wp-content/uploads/2025/04/67ac9d2ab620250407181957.webp)

就在这个大周日，Meta突然发布了Llama 4家族的新成员，而且一出手就是**三款模型**，直接引爆AI圈——

Llama 4 Scout、Llama 4 Maverick，还有一个**还在路上的巨无霸**：Llama 4 Behemoth。

这次发布的Llama 4，是Meta历史上**首个基于MoE（混合专家）架构**的模型系列，直接剑指开源最强！

🔹**中杯Llama 4 Scout**：

- 17B激活参数，16位专家模型
    
- 支持100万上下文窗口！
    
- 单个H100显卡即可运行
    
- 同类SOTA，性能超越Gemma 3和Mistral 3.1
    

🔹**大杯Llama 4 Maverick**：

- 同样17B参数，但拥有128位专家
    
- 性能干掉GPT-4o和Gemini 2.0 Flash！
    
- 代码能力等于DeepSeek-V3，参数却只有一半
    
- 单卡可跑，性价比爆表
    

🔹**超大杯Llama 4 Behemoth（预告）**：

- **2万亿参数**，还在训练中
    
- 是前面两个模型的“祖师爷”
    
- 内测成绩超过GPT-4.5、Claude 3.7、Gemini 2.0 Pro
    

**Llama 4 最新模型下载**

1、Llama  官方下载：【**[点击前往](https://www.llama.com/)**】

2、Hugging face 下载：【**[点击前往](https://huggingface.co/meta-llama)**】

**Llama 4 两大模型在线免费使用**

1、Hugging face 提供

Llama-4-Maverick 【[点击前往](https://huggingface.co/spaces/openfree/Llama-4-Maverick-17B-Research)】、Llama-4-Scout 【[点击前往](https://huggingface.co/spaces/openfree/Llama-4-Scout-17B-Research)】

注意：Hugging face 在线提供的免费试用版，暂不支持图片识别！ 所以我们可以使用下方提供的平台

2、Together 【[点击前往](https://api.together.ai/playground/v2/chat/meta-llama/Llama-4-Scout-17B-16E-Instruct)】

注册会送免费使用额度，可以直接免费试用Llama 4最新的两大模型Llama-4-Scout 和Llama-4-Maverick ，支持图片识别，可以很好的测试最新的视觉模型性能！

![](https://www.freedidi.com/wp-content/uploads/2025/04/d94b640d1b20250407183150.webp)

视频中演示的打地鼠代码（优化版），把下方的代码贴到 https://editor.p5js.org 就可以在线运行使用！

```
// 可爱风格打地鼠游戏

let holes = []; // 地洞数组
let moles = []; // 地鼠数组
let score = 0; // 得分
let gameTime = 60; // 游戏时间(秒)
let timer; // 计时器
let gameOver = false; // 游戏结束标志
let bgColor; // 背景颜色
let hammerAngle = 0; // 锤子角度
let hammerSize = 60; // 锤子大小
let hitEffect = false; // 打击效果
let hitTimer = 0; // 打击效果计时
let startScreen = true; // 开始画面
let font; // 游戏字体

function preload() {
  // 这里可以预加载自定义字体
  // font = loadFont('assets/cute_font.ttf');
}

function setup() {
  createCanvas(800, 600);
  colorMode(HSB, 360, 100, 100, 1);
  bgColor = color(200, 30, 95); // 浅蓝色背景
  textAlign(CENTER, CENTER);
  
  // 初始化地洞 (3x3网格)
  for (let i = 0; i < 9; i++) {
    let x = 150 + (i % 3) * 200;
    let y = 150 + floor(i / 3) * 180;
    holes.push(new Hole(x, y, 100));
  }
  
  // 初始化地鼠
  for (let i = 0; i < 9; i++) {
    moles.push(new Mole(holes[i]));
  }
  
  // 设置计时器
  timer = gameTime;
}

function draw() {
  background(bgColor);
  
  if (startScreen) {
    drawStartScreen();
    return;
  }
  
  if (gameOver) {
    drawGameOver();
    return;
  }
  
  // 绘制草地
  drawGrass();
  
  // 更新和显示地洞
  for (let hole of holes) {
    hole.display();
  }
  
  // 更新和显示地鼠
  for (let mole of moles) {
    mole.update();
    mole.display();
  }
  
  // 绘制锤子
  drawHammer();
  
  // 绘制打击效果
  if (hitEffect) {
    drawHitEffect();
    hitTimer--;
    if (hitTimer <= 0) {
      hitEffect = false;
    }
  }
  
  // 绘制UI
  drawUI();
  
  // 游戏逻辑更新
  updateGame();
}

function mousePressed() {
  if (startScreen) {
    startScreen = false;
    // 开始游戏计时
    setInterval(countDown, 1000);
    return;
  }
  
  if (gameOver) {
    resetGame();
    return;
  }
  
  // 锤击动画
  hammerAngle = -PI/4;
  
  // 检查是否击中地鼠
  for (let mole of moles) {
    if (mole.isUp && dist(mouseX, mouseY, mole.x, mole.y - mole.riseHeight) < mole.size/2) {
      mole.hit();
      score += 10;
      hitEffect = true;
      hitTimer = 10;
    }
  }
}

function mouseReleased() {
  // 锤子恢复原位
  hammerAngle = 0;
}

function drawStartScreen() {
  // 可爱标题
  fill(350, 80, 80);
  textSize(64);
  text("打地鼠游戏", width/2, height/3);
  
  // 开始按钮
  fill(120, 80, 90);
  noStroke();
  ellipse(width/2, height/2, 200, 80);
  fill(255);
  textSize(32);
  text("开始游戏", width/2, height/2);
  
  // 说明文字
  fill(0);
  textSize(20);
  text("点击出现的地鼠获得分数", width/2, height*2/3);
  text(`游戏时间: ${gameTime}秒`, width/2, height*2/3 + 40);
}

function drawGameOver() {
  // 半透明遮罩
  fill(0, 0, 0, 0.7);
  rect(0, 0, width, height);
  
  // 游戏结束文字
  fill(0, 80, 100);
  textSize(64);
  text("游戏结束!", width/2, height/3);
  
  // 得分显示
  fill(255);
  textSize(48);
  text(`得分: ${score}`, width/2, height/2);
  
  // 重新开始按钮
  fill(120, 80, 90);
  noStroke();
  ellipse(width/2, height*2/3, 200, 80);
  fill(255);
  textSize(32);
  text("再玩一次", width/2, height*2/3);
}

function drawGrass() {
  // 绘制底部草地
  noStroke();
  fill(120, 60, 80);
  beginShape();
  vertex(0, height);
  vertex(0, height - 50);
  for (let x = 0; x <= width; x += 20) {
    let y = height - 50 + sin(x * 0.05 + frameCount * 0.1) * 15;
    vertex(x, y);
  }
  vertex(width, height - 50);
  vertex(width, height);
  endShape(CLOSE);
}

function drawHammer() {
  push();
  translate(mouseX, mouseY);
  rotate(hammerAngle);
  
  // 锤柄
  stroke(40, 40, 40);
  strokeWeight(8);
  line(0, 0, -hammerSize, hammerSize);
  
  // 锤头
  noStroke();
  fill(200, 40, 40);
  ellipse(-hammerSize - 10, hammerSize + 10, hammerSize/2, hammerSize/2);
  
  pop();
}

function drawHitEffect() {
  push();
  translate(mouseX, mouseY);
  
  // 爆炸星星效果
  noStroke();
  fill(60, 100, 100, 0.8);
  for (let i = 0; i < 8; i++) {
    push();
    rotate(i * PI/4 + frameCount * 0.2);
    triangle(0, 0, 30, 5, 30, -5);
    pop();
  }
  
  // 文字效果
  fill(0, 100, 100);
  textSize(24);
  text("+10", 0, -40);
  
  pop();
}

function drawUI() {
  // 得分显示
  fill(0);
  textSize(32);
  text(`得分: ${score}`, 150, 50);
  
  // 时间显示
  text(`时间: ${timer}秒`, width - 150, 50);
}

function updateGame() {
  // 随机让地鼠出现
  if (frameCount % 30 === 0 && random() < 0.2) {
    let inactiveMoles = moles.filter(m => !m.isUp && !m.isHit);
    if (inactiveMoles.length > 0) {
      let randomMole = random(inactiveMoles);
      randomMole.popUp();
    }
  }
}

function countDown() {
  if (!gameOver) {
    timer--;
    if (timer <= 0) {
      gameOver = true;
    }
  }
}

function resetGame() {
  score = 0;
  timer = gameTime;
  gameOver = false;
  for (let mole of moles) {
    mole.reset();
  }
}

// 地洞类
class Hole {
  constructor(x, y, size) {
    this.x = x;
    this.y = y;
    this.size = size;
    this.color = color(30, 60, 50); // 深棕色
  }
  
  display() {
    // 地洞阴影
    noStroke();
    fill(0, 0, 0, 0.2);
    ellipse(this.x + 5, this.y + 5, this.size, this.size/2);
    
    // 地洞主体
    fill(this.color);
    ellipse(this.x, this.y, this.size, this.size/2);
    
    // 地洞内部
    fill(0, 0, 30);
    ellipse(this.x, this.y + 5, this.size * 0.8, this.size/3);
  }
}

// 地鼠类
class Mole {
  constructor(hole) {
    this.hole = hole;
    this.x = hole.x;
    this.y = hole.y;
    this.size = hole.size * 0.7;
    this.isUp = false;
    this.isHit = false;
    this.riseHeight = 0;
    this.maxRise = this.size * 1.5;
    this.speed = random(2, 4);
    this.color = color(random(20, 40), random(70, 90), random(70, 90));
    this.faceColor = color(0, 0, 100);
    this.blushColor = color(0, 80, 90);
    this.eyeSize = this.size * 0.15;
    this.animationTimer = 0;
  }
  
  update() {
    if (this.isUp && !this.isHit) {
      // 地鼠上升动画
      this.riseHeight = min(this.riseHeight + this.speed, this.maxRise);
      
      // 随机眨眼
      if (frameCount % 120 === 0 && random() < 0.3) {
        this.animationTimer = 5;
      }
    } else if (this.isHit) {
      // 被打中后下降
      this.riseHeight = max(this.riseHeight - this.speed * 2, 0);
      if (this.riseHeight <= 0) {
        this.isUp = false;
        this.isHit = false;
      }
    }
  }
  
  display() {
    if (this.isUp) {
      push();
      translate(0, -this.riseHeight);
      
      // 地鼠身体
      noStroke();
      fill(this.color);
      ellipse(this.x, this.y, this.size, this.size);
      
      // 脸颊红晕
      if (!this.isHit) {
        fill(this.blushColor);
        ellipse(this.x - this.size * 0.25, this.y + this.size * 0.1, this.size * 0.2, this.size * 0.1);
        ellipse(this.x + this.size * 0.25, this.y + this.size * 0.1, this.size * 0.2, this.size * 0.1);
      }
      
      // 脸部
      fill(this.faceColor);
      ellipse(this.x, this.y - this.size * 0.1, this.size * 0.7, this.size * 0.7);
      
      // 眼睛
      fill(0);
      if (this.animationTimer > 0) {
        // 眨眼动画
        rect(this.x - this.size * 0.2, this.y - this.size * 0.15, this.eyeSize * 1.5, this.eyeSize * 0.3);
        rect(this.x + this.size * 0.2, this.y - this.size * 0.15, this.eyeSize * 1.5, this.eyeSize * 0.3);
        this.animationTimer--;
      } else {
        ellipse(this.x - this.size * 0.2, this.y - this.size * 0.15, this.eyeSize);
        ellipse(this.x + this.size * 0.2, this.y - this.size * 0.15, this.eyeSize);
      }
      
      // 鼻子
      fill(350, 80, 80);
      ellipse(this.x, this.y - this.size * 0.05, this.eyeSize * 0.7);
      
      // 嘴巴
      noFill();
      stroke(0);
      strokeWeight(2);
      if (this.isHit) {
        // 被打中时的表情
        arc(this.x, this.y + this.size * 0.1, this.size * 0.3, this.size * 0.2, PI, TWO_PI);
      } else {
        // 开心表情
        arc(this.x, this.y + this.size * 0.1, this.size * 0.3, this.size * 0.2, 0, PI);
      }
      
      pop();
    }
  }
  
  popUp() {
    this.isUp = true;
    this.isHit = false;
    this.riseHeight = 0;
    this.speed = random(2, 4);
    
    // 随机决定多久后会下去
    setTimeout(() => {
      if (this.isUp && !this.isHit) {
        this.isHit = true; // 标记为被打中状态(即使没被打中也用这个状态来下降)
      }
    }, random(1000, 3000));
  }
  
  hit() {
    this.isHit = true;
  }
  
  reset() {
    this.isUp = false;
    this.isHit = false;
    this.riseHeight = 0;
  }
}
```