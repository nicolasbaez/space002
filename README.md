## : : s p a c e 0 0 2

![space](https://github.com/nicolasbaez/space002/blob/master/space002.gif)

```processing
int cantidad=64;
float vx1[]=new float[cantidad];
float vy1[]=new float[cantidad];
float vx2[]=new float[cantidad];
float vy2[]=new float[cantidad];
float vx3[]=new float[cantidad];
float vy3[]=new float[cantidad];
float gravedad[]=new float[cantidad];
float tx[]=new float[cantidad];
float dGravedad=4;
int dEsp=32;
int cuadros=0;
void setup() {
  size(512, 216);
  smooth();
  for (int i=0; i<cantidad; i++) {
    vx1[i]=random(width);
    vy1[i]=0;
    vx2[i]=vx1[i]+random(-dEsp, dEsp);
    vy2[i]=vy1[i]+random(-dEsp, dEsp);
    vx3[i]=vx1[i]+random(-dEsp, dEsp);
    vy3[i]=vy1[i]+random(-dEsp, dEsp);
    tx[i]=random(64);
    gravedad[i]=random(dGravedad)+1;
  }
}
void draw() {
  background(0);
  for (int i=0; i<cantidad; i++) {
    stroke(255, 0, 0);
    fill(255, 0, 0, tx[i]);
    beginShape();
    vertex(vx1[i], vy1[i]);
    vertex(vx2[i], vy2[i]);
    vertex(vx3[i], vy3[i]);
    vertex(vx1[i], vy1[i]);
    endShape();
    vy1[i]+=gravedad[i];
    vy2[i]+=gravedad[i];
    vy3[i]+=gravedad[i];
    if (vy1[i]>height&&vy2[i]>height&&vy3[i]>height) {
      vx1[i]=random(width);
      vy1[i]=0;
      vx2[i]=vx1[i]+random(-dEsp, dEsp);
      vy2[i]=vy1[i]+random(-dEsp, dEsp);
      vx3[i]=vx1[i]+random(-dEsp, dEsp);
      vy3[i]=vy1[i]+random(-dEsp, dEsp);
      gravedad[i]=random(dGravedad)+1;
    }
  }
  cuadros++;
  println(cuadros);
  if (cuadros>=512&&cuadros<1024) {
    saveFrame("gif/space002-######.png");
  }
}
```
