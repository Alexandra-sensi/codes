let img;
let cellSize;

function preload() {
  //put preload code here
  img = loadImage('data/tortue.jpg');
}

function setup() {
  createCanvas(windowWidth, windowHeight);
  img.resize(img.width * 0.7, img.height * 0.7);
  rectMode(CENTER);

}

function draw() {
  background(0);
  //image(img, 0, 0);
  //img.get(mouseX, mouseY);
  noStroke();

  cellSize = map(mouseX, 0, width, 10, 80);

  translate(width / 2 - img.width / 2, height / 2 - img.height / 2);
  //algotythm image drawing
  for (var x = 0; x < img.width / cellSize; x++) {
    for (var y = 0; y < img.height / cellSize; y++) {
      let c = img.get(x * cellSize, y * cellSize);
      let b = brightness(c);
      let w = map(b * (mouseY * 0.005), 0, 255, 0, 20);

      push();
      translate(x * cellSize, y * cellSize);
      fill(255); //couleur si on met 255 tout est par défaut blanc
      rotate(frameCount * 0.1);
      rect(0, 0, w * 2, w * 0.5);
      pop();

    }
  }
  /*
    for (var x = 0; x < img.width; x++) {
      for (var y = 0; y < img.height; y++) {
        let c = img.get(x * cellSize, y * cellSize);
        let b = brightness(c);

        push();
        translate(x * cellSize, y * cellSize);
        fill(c);
        rect(0, 0, 2, 2);
        pop();

      }
    }

    for (var x = 0; x < img.width; x++) {
      for (var y = 0; y < img.height; y++) {
        let c = img.get(x, y);
        let b = brightness(c);
        fill(0, 0, blue(c), 85);
        rect(x - 20, y - 20, 1, 1);

      }
    }*/
}
