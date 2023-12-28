# major_project
```js
let bt, p, result, R, G, B;
let r, g, b;

function setup() {
  createCanvas(200, 200);
  background(220);

  bt = createButton('보색찾기');
  bt.position(65, 35);

  r = createInput('');
  r.position(65, 10);
  r.size(30);

  g = createInput('');
  g.position(105, 10);
  g.size(30);

  b = createInput('');
  b.position(145, 10);
  b.size(30);

  bt.mousePressed(changeColor);
  
  p = createP('');
  p.style('font-size','10px');
  p.position(10,60);
  
  result = createP('');
  result.style('font-size','15px');
  result.position(65,125);
}

function draw() {
  R = parseInt(r.value());
  G = parseInt(g.value());
  B = parseInt(b.value());
  
  if(R > 255 || G > 255 || B > 255 || R<0 || G<0 || B<0){
    p.html('입력 값은 0 이상 255 이하이어야 합니다.');
    p.show();
    
    noStroke();
    fill(0);
    square(10, 10, 50);
  } else {
    fill(R, G, B);
    square(10, 10, 50);
    p.hide();
  }
}

function changeColor() {  
  fill(255-R, 255-G, 255-B);
  square(10,110,50);
  var hexCode = rgbToHex(R, G, B);
  result.html(hexCode);
  result.show();
  
  fill(0);
  text('()',65,120);
}

function rgbToHex(r, g, b) {
  // 각 RGB 값을 16진수로 변환하여 변수에 저장
  var hexR = r.toString(16).padStart(2, '0');
  var hexG = g.toString(16).padStart(2, '0');
  var hexB = b.toString(16).padStart(2, '0');

  // 헥스 코드로 변환된 값 반환
  return '#' + hexR + hexG + hexB;
}

```
