Given coordinates of 4 points, bottom-left and top-right corners of two rectangles. The task is to find the coordinates of the intersecting rectangle formed by the given two rectangles. 
![](https://i.imgur.com/y6weQbf.png)
Need to output the coordinates of the green shaded rectangular region. 
The bottom left coordinates will be:
$x5=min(x1,x3)$
$y6=min(y1,y3$
The top right coordinates will be:
$x7=max(x2,x4)$
$y7=max(y2,y4)$
if $x5>x7$ or $y6>y7$ then no intersection rectangle is formed. 
```cpp
void FindPoints(int x1, int y1, int x2, int y2, int x3, int y3, int x4,
                int y4) {
  // bottom_left of intersecting box
  int bottom_left_x = std::max(x1, x3);
  int bottom_left_y = std::max(y1, y3);
  // top_right_of intersecting box
  int top_right_x = std::min(x2, x4);
  int top_right_y = std::min(y2, y4);
  if (bottom_left_x > top_right_x || bottom_left_y > top_right_y) {
    std::cout << "No rectangle is merging!" << std::endl;
    return;
  }
  std::cout << "The bottom left coordinates are : (" << bottom_left_x << ", "
            << bottom_left_y << ")"
            << " \n";
  std::cout << "The top right coordinates are : (" << top_right_x << ", "
            << top_right_y << ")"
            << " \n";
  int bottom_right_x = top_right_x;
  int bottom_right_y = bottom_left_y;
  std::cout << "The bottom right coordinates are : (" << bottom_right_x << ", "
            << bottom_right_y << ")"
            << " \n";
  int top_left_x = bottom_left_x;
  int top_left_y = top_right_y;
  std::cout << "The top left coordinates are : (" << top_left_x << ", "
            << top_left_y << ")"
            << " \n";
}
```
