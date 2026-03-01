本题就像去超市买东西，手里拿着一大叠不同面额的钞票，总是先掏出面额最大的那张，直到找不开为止，因此使用**查表法（Lookup Table）**。定义两个对应的数组：一个存放整数值，一个存放对应的罗马数字字符串。从数组最大值（1000）开始循环，只要 $num$ 大于等于当前面额，就拼接到结果中，并减去该面额。

```cpp
class Solution {
public:
    string intToRoman(int num) {
        int value[] = {
            1, 4, 5, 9,
            10, 40, 50, 90, 
            100, 400, 500, 900,
            1000,
        };
        string reps[] = {
            "I", "IV", "V", "IX",
            "X", "XL", "L", "XC", 
            "C", "CD", "D", "CM",
            "M",
        };

        string ans;
        for (int i = 12; i >= 0; i--) {
            while (num >= value[i]) {
                num -= value[i];
                ans += reps[i];
            }
        }
        return ans;
    }
};
```