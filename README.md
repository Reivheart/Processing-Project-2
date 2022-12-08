# Processing-Project-2

import processing.video.*;


String PATH = "C:/Users/chino/OneDrive/Desktop/Project_2/10000000_5770379186341615_6185318327229075217_n.mp4";
Movie mov;

void setup() {
  size(700, 1000);
  frameRate(30);
  mov = new Movie(this, PATH);
  mov.play();
  mov.speed(1);
  mov.volume(1);
  colorMode(HSB, 1);
  background(10);
}
void movieEvent(Movie m) {
  m.read();
}
void draw() {
  mov.loadPixels();
  //image(mov, 0, 0, width, height);
  int x = width/2;
  int y = height/2;
  for(int i=0; i<100; i++) {
    int c = mov.get(x, y);
    float h = hue(c);
    float s = saturation(c);
    float b = brightness(c);
    fill(h, s, b);
    ellipse(x, y, s*10, s*10);
    x += sin(h*100) * b * 40;
    y += cos(h*100) * b * 40;  
  }
}
