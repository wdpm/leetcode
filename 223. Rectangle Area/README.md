# 223. Rectangle Area
Find the total area covered by two rectilinear rectangles in a 2D plane.

Each rectangle is defined by its bottom left corner and top right corner as shown in the figure.
![](./rectangle_area.png)

Assume that the total area is never beyond the maximum possible value of int.
``` js
/**
 * @param {number} A
 * @param {number} B
 * @param {number} C
 * @param {number} D
 * @param {number} E
 * @param {number} F
 * @param {number} G
 * @param {number} H
 * @return {number}
 */
var computeArea = function(A, B, C, D, E, F, G, H) {
    //该问题的关键是：怎么求相交区域的面积？
    //1.穷举所有可能性,判断分支过多，没有意义。
    //正确的思路是：归纳出求交集的一般方法(公式)，才能简化代码，保持条理清晰
    //第一个矩形面积
    var area1=(C-A)*(D-B);
    //第二个矩形面积
    var area2=(G-E)*(H-F);
    
    if(area1===0){
        return area2;
    }
    
    if(area2===0){
        return area1;
    }
    
    //Math.max(A,E)：求左边x轴最大值
    //Math.min(C,G)：求右边x轴最小值
    //Math.max(Math.min(C,G),left)：求前二者中最大值。注意：当两个矩形不相交时，left==right，right-left为0
    var left=Math.max(A,E); var right=Math.max(Math.min(C,G),left);
    var bottom=Math.max(B,F); var top=Math.max(Math.min(D,H),bottom);
    
    return area1+area2-(right-left)*(top-bottom);
};
```