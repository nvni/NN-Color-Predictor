# Neural Network Color Predictor

Cấu trúc thư mục:

```
|   index.html
|   README.md
|   sketch.js
|   style.css
|   
\---lib
        matrix.js
        matrix.test.js
        nn.js
        p5.js
        p5.sound.min.js
```

#### Lib

Các file trong thư mục này các bạn có thể download tại đây: https://github.com/CodingTrain/Toy-Neural-Network-JS/

#### sketch.js

Đây là file chính chứ code để chạy.

Khởi tạo

```javascript
function setup() {
   // Khởi tạo canvas
  createCanvas(600, 300);
	
  // Đặt chế độ không lặp. Canvas sẽ không tự render lại
  noLoop();
	
  // Tạo mạng Neural Network: NeuralNetwork(số lượng input, số lớp ẩn, số lượng output)
  brain = new NeuralNetwork(3, 3, 2);
    
   // Training với 10000 mẫu
  for (let i = 0; i < 10000; i++) {
    let r = random(255);
    let g = random(255);
    let b = random(255);
    let targets = trainColor(r, g, b);
    let inputs = [r / 255, g / 255, b / 255];
    brain.train(inputs, targets);
  }
    
  pickColor();
}
```

Vẽ

```javascript
function draw() {
  background(r, g, b);
  strokeWeight(4);
  stroke(0);
  line(width / 2, 0, width / 2, height);

  textSize(64);
  noStroke();
  fill(0);
  textAlign(CENTER);

  text("black", 150, 100);
  fill(255);
  text("white", 450, 100);
  let which = colorPredictor(r, g, b);
  if (which == "black") {
    fill(0);
    ellipse(150, 200, 60);
  } else {
    fill(255);
    ellipse(450, 200, 60);
  }
}
```



##### Tham khảo:

https://www.youtube.com/watch?v=KtPpoMThKUs

https://p5js.org/

