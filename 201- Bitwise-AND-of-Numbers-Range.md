# 201. Bitwise AND of Numbers Range

## problem description

Given a range [m, n] where 0 <= m <= n <= 2147483647, return the bitwise AND of all numbers in this range, inclusive.

**Example 1:**

```text
Input: [5,7]
Output: 4
```

**Example 2:**

```text
Input: [0,1]
Output: 0
```

## algorithm thought

这题可以从递归的角度思考问题。如果a>b,那么range(a,b)中的所有数字相与，最后一位bit肯定是0。这个很好证明，a&a+1 最后一位肯定是0。b>=a+1,range(a,b)中所有数相与，最后一位肯定为0.

确定好了最后一位了，前面的可以递归解决，让ab都右移一位，递归判断，直到最后，a<=b,这时候要么就是ab都为1或者是b为0.不管哪种情况，直接返回b就行了

## code

```c++
class Solution {
public:
    int rangeBitwiseAnd(int m, int n) {
       return n>m?(rangeBitwiseAnd((m>>1),(n>>1))<<1):m;
    }
};
```

## algorithm analysis

这个算法最多执行32次，时间复杂度O(1)