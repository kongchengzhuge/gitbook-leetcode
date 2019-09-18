# 657. Robot Return to Origin

## Problem Description

There is a robot starting at position \(0, 0\), the origin, on a 2D plane. Given a sequence of its moves, judge if this robot **ends up at \(0, 0\)** after it completes its moves.

The move sequence is represented by a string, and the character moves\[i\] represents its ith move. Valid moves are R \(right\), L \(left\), U \(up\), and D \(down\). If the robot returns to the origin after it finishes all of its moves, return true. Otherwise, return false.

**Note**: The way that the robot is "facing" is irrelevant. "R" will always make the robot move to the right once, "L" will always make it move left, etc. Also, assume that the magnitude of the robot's movement is the same for each move.

## algorithm thought

机器人从原点出发，最后判断能否到达原点，一共4个操作，将所有的操作统计起来，最后比较上下是否一样，左右是否一样即可

## code

```text
class Solution {
public:
    bool judgeCircle(string moves) {
        stack<char> lr;
        stack<char> ud;
        for(auto ch:moves){
            if(ch=='L'){
                if(lr.empty()||lr.top()=='L'){
                    lr.push(ch);
                }else
                    lr.pop();
            }
            if(ch=='R'){
                if(lr.empty()||lr.top()=='R'){
                    lr.push(ch);
                }else
                    lr.pop();
            }
            if(ch=='U'){
                if(ud.empty()||ud.top()=='U'){
                    ud.push(ch);
                }else
                    ud.pop();
            }
            if(ch=='D'){
                if(ud.empty()||ud.top()=='D'){
                    ud.push(ch);
                }else
                    ud.pop();
            }
        }
        return lr.empty()&&ud.empty();
    }
};
```

## algorithm analysis

一个循环遍历数组，时间是O\(n\)，最开始拿到题目的时候直接类比成了括号匹配，就动手做了。其实括号匹配比这个多了一点位置上的限制，而这里只要统计数字即可。直接定义4个变量会更快，直接用4个寄存器存count，最后比较。



