# zwan0192_TUT2_Quiz_8

## Imaging Technique Inspiration

I am inspired by the pointillism technique, particularly as seen in Georges Seurat's "A Sunday Afternoon on the Island of La Grande Jatte".

![This is the first image](readmeImages/img_1.jpg)

And "The Seine seen from La Grande Jatte".

![This is the first image](readmeImages/img_2.jpg)

I'd incorporate pointillism's stippling effect to digitally reinterpret a masterpiece in p5.js. This method translates well to pixels, making it ideal for demonstrating the basics of digital image construction. It allows for creative user interaction, as viewers can alter the dot density or colors, actively exploring the juxtaposition of individual elements and their collective visual harmony, embodying the assignment's goal of creative presentation through coding.

## Coding Technique Exploration

In the part of the code, I found a work about water lilies, which has rich brush strokes and wonderful color matching, and every generated picture is very harmonious, which is worth learning. Here is a link to this work.

https://openprocessing.org/sketch/1990406

*This sketch render a vibrant, dynamic water lily scene with organic randomness and flowing water effects.*

![This is the first image](readmeImages/img_3.jpg)

![This is the first image](readmeImages/img_4.jpg)

The drawNoiseLine Function seems to draw a line with "noisy" appearance, possibly to represent the stem or fine details on the petals.  It uses Perlin noise to vary the thickness and rotation of the line segments, creating a more organic and less uniform line.

```
function drawNoiseLine(_x, _y, _dir, _length, _fromC, _toC) {
    let dotCount = _length / 2;

    let nowX = _x;
    let nowY = _y;

    for (let i = 0; i < dotCount; i++) {
        let t = i / (dotCount - 1);
        let nowC = NYLerpColor(_fromC, _toC, easeInQuad(t));

        stroke(nowC.h, nowC.s, nowC.b);

        let pointSizeNoise = noise(nowX * 0.01, nowY * 0.01, 666);
        let nowSize = lerp(0.1, 2.0, pointSizeNoise);
        nowSize += random(0.0, 1.0);

        strokeWeight(nowSize);

        let rotNoise = noise(nowX * 0.01, nowY * 0.01, 1234);
        let rotAdd = lerp(-60, 60, rotNoise);
        let nowRot = _dir + rotAdd;

        point(nowX, nowY);

        nowX += sin(radians(nowRot)) * 2;
        nowY += -cos(radians(nowRot)) * 2;
    }
}
```