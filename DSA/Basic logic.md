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

### Add Binary

I/P : `a = "11", b = "1"`<br>

O/P : `100`

<span style='color:Orange'>Easy & Asked frequently</span>

**Thinking** : <br>

- We can iterate over the two string from the back.
- Add the digits + carry % 2 to get the result.
- $C_n=(D+C)/2$ , C new carry, D both digits , C previous carry.

**Approach** : <br>

```cpp
string solve(string a, string b) {
  int carry = 0;
  int i = a.size() - 1;
  int j = b.size() - 1;
  int alen = a.size();
  int blen = b.size();
  string result = "";
  while (i >= 0 || j >= 0 || carry != 0) {
    int x = 0;
    if (i >= 0 && a[i] == '1')
      x = 1;
    int y = 0;
    if (j >= 0 && b[j] == '1')
      y = 1;
    result = to_string((x + y + carry) % 2) + result;
    carry = (x + y + carry) / 2;
    i--;
    j--;
  }
  return result;
}
```

Time complexity : $O(n)$.
