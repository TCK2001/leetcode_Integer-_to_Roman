# leetcode_Integer-_to_Roman
+ 숫자를 입력하면 로마숫자로 변형해서 출력하는 문제
+ 假設給一個數字時，我們需要轉換成羅馬數字並且輸出

-----
+ Example1
```
Input: num = 3
Output: "III"
Explanation: 3 is represented as 3 ones.
```
----
+ Example2
```
Input: num = 58
Output: "LVIII"
Explanation: L = 50, V = 5, III = 3.
```
----
+ Example3
```
Input: num = 1994
Output: "MCMXCIV"
Explanation: M = 1000, CM = 900, XC = 90 and IV = 4.
```
----
```python
class Solution:
    def intToRoman(self, num: int) -> str:
        I = ["", "I", "II", "III", "IV", "V", "VI", "VII", "VIII", "IX"]　#  0 ~ 9 숫자 저장
        X = ["", "X", "XX", "XXX", "XL", "L", "LX", "LXX", "LXXX", "XC"] # 0 ~ 9
        C = ["", "C", "CC", "CCC", "CD", "D", "DC", "DCC", "DCCC", "CM"] # 0 ~ 9
        M = ["", "M", "MM", "MMM"] # 0 ~ 3 왜냐하면 1 <= num <= 3999
        
        res = ''
        if num >= 1000:
            thousand = M[num // 1000] 
            hundred = C[(num % 1000) // 100] # 앞에꺼 나누고 나머지 값에서 100 나누기
            ten = X[(num % 100) // 10] # 같은 원리
            one = I[num % 10] # 마지막 자릿수
            res = thousand + hundred + ten + one
            
        elif num >= 100:
            hundred = C[(num % 1000) // 100]
            ten = X[(num % 100) // 10]
            one = I[num % 10
            res = hundred + ten + one
                    
        elif num >=10 :
            ten = X[(num % 100) // 10]
            one = I[num % 10]
            res = ten + one
                    
        else:
            res = I[num % 10]
        return res # 결과값 반환
```
---
```
결론 : 
0~9 모든 숫자를 저장해서 나누기로 하나하나 씩 찾는게 더 빠름
```
---
```
結論:
直接一個一個除看看，比起用一些while迴圈跑快很多
```
---
### Result
Runtime: 42 ms, faster than 98.61% of Python3 online submissions for Integer to Roman.\
Memory Usage: 13.9 MB, less than 35.36% of Python3 online submissions for Integer to Roman.
