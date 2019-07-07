# Lego FeatureScript


## Lego bricks
Parameter option:
>   * Row Lego
>   * Col Lego\
[Source Code](https://github.com/JCTGY/Lego_FeatureScript/blob/master/legoBricks.fs)\
[Onshape Document](https://cad.onshape.com/documents/da6b009e9c013270aeae4cd8/w/05c0f5a10696f0c50747bc21/e/385ac05fe04a705f8d000c23)

![Lego](https://user-images.githubusercontent.com/46547632/60761377-ec34c600-9ffb-11e9-8d17-fe38b507a6f4.gif)\
In created bottom hollow tube for lego: \
add true add the back, which means only extrude the part outter ring
```
opExtrude(context, id + "tubeCirExtrude, true",
```
Insted of the bottom code. Will still need to delet the inner tube body to make the hollow tube.\
However, will leave the code as it is for future references
```
            for (var c = 2; c <= col ; c += 1)
            {
                for (var r = 2; r <= row ; r += 1)
                {
                    skCircle(tubeSketch, "tubeCir" ~ tubeCirId, {
                            "center" : vector(width * (r - 1), width * (c - 1)) * millimeter,
                            "radius" : dia / 4.8 * 6.4  / 2 * millimeter
                    });
                    tubeCirId += 1;
                }
            }
            skSolve(tubeSketch);
            opExtrude(context, id + "tubeCirExtrude", {
                "entities" : qSketchRegion(id + "tubeSketch"),
                "direction" : evOwnerSketchPlane(context, {"entity" : qSketchRegion(id + "tubeSketch")}).normal,
                "endBound" : BoundingType.BLIND,
                "endDepth" : (height - thick) * millimeter
            });
```

![2 X 2 Lego.png](/image/2X2_Lego.png)
![2 X 2 Lego.png](/image/2X2_Lego_Back.png)\
X * 1 || 1 * X lego brick have a solid supporting tube\
![5 X 1 Lego.png](/image/5X1_Lego.png)
![5 X 1 Lego.png](/image/5X1_Lego_Back.png)
![10 X 10 Lego.png](/image/10X10_Lego.png)
