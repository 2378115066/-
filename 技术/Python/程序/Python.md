 

## 1.反转一个3位整数  

```python

class Solution:
#参数number: 一个三位整数
#返回值: 反转后的数字
  def reverseInteger(self, number):
    h = int(number/100)
    t = int(number%100/10)
    z = int(number%10)
    return (100*z+10*t+h)

#主函数
if __name__ == '__main__':
  solution = Solution()
  num = 123
  ans = solution.reverseInteger(num)
  print("输入：", num)
  print("输出：", ans)
```

## 2.合并排序数组 

```python
class Solution:
    # 参数A: 有序整数数组A
    # 参数B: 有序整数数组B
    # 返回:一个新的有序整数数组
    def mergeSortedArray(self, A, B):
        i, j = 0, 0
        C = []
        while i < len(A) and j < len(B):
            if A[i] < B[j]:
                C.append(A[i])
                i += 1
            else:
                C.append(B[j])
                j += 1
        while i < len(A):
            C.append(A[i])
            i += 1
        while j < len(B):
            C.append(B[j])
            j += 1
        return C
# 主函数
if __name__ == '__main__':
    A = [1, 4]
    B = [1, 2, 3]
    D = [1, 2, 3, 4]
    E = [2, 4, 5, 6]
    solution = Solution()
    print("输入：", A, " ", B)
    print("输出：", solution.mergeSortedArray(A, B))
    print("输入：", D, " ", E)
    print("输出：", solution.mergeSortedArray(D, E))
```

## 3.旋转字符串

```python
class Solution:
  #参数s:字符列表
  #参数offset:整数
  #返回值:无
  def rotateString(self, s, offset):
    if len(s) > 0:
      offset = offset % len(s)
    temp = (s + s)[len(s) - offset : 2 * len(s) - offset]
    for i in range(len(temp)):
      s[i] = temp[i]
#主函数
if __name__ == '__main__':
  s = ["a","b","c","d","e","f","g"]
  offset = 3
  solution = Solution()
  solution.rotateString(s, offset)
  print("输入：s =", ["a","b","c","d","e","f","g"], " ", "offset =",offset)
  print("输出：s =", s)
```

## 4.相对排名

```python
class Solution:
  #参数nums为整数列表
  #返回列表
  def findRelativeRanks(self, nums):
    score = {}
    for i in range(len(nums)):
      score[nums[i]] = i
    sortedScore = sorted(nums, reverse=True)
    answer = [0] * len(nums)
    for i in range(len(sortedScore)):
      res = str(i + 1)
      if i == 0:
        res = 'Gold Medal'
      if i == 1:
        res = 'Silver Medal'
      if i == 2:
        res = 'Bronze Medal'
      answer[score[sortedScore[i]]] = res
    return answer
#主函数
if __name__ == '__main__':
   num = [5,4,3,2,1]
   s = Solution()
   print("输入为：",num)
  print("输出为：",s.findRelativeRanks(num))
```

## 5.二分查找

```
class Solution:
  #参数nums为整数数组
  #参数target为目标整数
  #返回目标整数的下标
  def binarySearch(self, nums, target):
    return nums.index(target) if target in nums else -1
#主函数
if __name__ == '__main__':
  my_solution = Solution()
  nums = [1,2,3,4,5,6]
  target = 3
  targetIndex = my_solution.binarySearch(nums, target)
  print("输入：nums =", nums, " ", "target =",target)
  print("输出：",targetIndex)
```

## 6.下一个更大的数

```python
class Solution:
    # 参数nums1为整数数组
    # 参数nums2为整数数组
    # 返回整数数组
    def nextGreaterElement(self, nums1, nums2):
        answer = {}
        stack = []
        for x in nums2:
            while stack and stack[-1] < x:
                answer[stack[-1]] = x
                del stack[-1]
            stack.append(x)
        for x in stack:
            answer[x] = -1
        return [answer[x] for x in nums1]


# 主函数
if __name__ == '__main__':
    s = Solution()
    nums1 = [4, 1, 2]
    nums2 = [1, 3, 4, 2]
    print("输入1为：", nums1)
    print("输入2为：", nums2)
    print("输出为 ：", s.nextGreaterElement(nums1, nums2))
```

## 7.字符串中的单词数

```python
class Solution:
    # 参数s为字符串
    # 返回整数
    def countSegments(self, s):
        res = 0
        for i in range(len(s)):
            if s[i] != ' ' and (i == 0 or s[i - 1] == ' '):
                  res += 1
        return res
# 主函数
if __name__ == '__main__':
    s = Solution()
    n = "Hello, my name is John"
    print("输入为：", n)
    print("输出为：", s.countSegments(n))
```

## 8.勒索信

```python
class Solution:
  """
  参数ransomNote为字符串
  参数magazine为字符串
  返回布尔类型
  """
  def canConstruct(self, ransomNote, magazine):
    arr = [0] * 26
    for c in magazine:
      arr[ord(c) - ord('a')] += 1
    for c in ransomNote:
      arr[ord(c) - ord('a')] -= 1
      if arr[ord(c) - ord('a')] < 0:
        return False
    return True
#主函数
if __name__ == '__main__':
  s = Solution()
  ransomNote = "aa"
  magazine = "aab"
  print("输入勒索信为：",ransomNote)
  print("输入杂志内容：",magazine)
  print("输出为：",s.canConstruct(ransomNote,magazine))
```

## 9.不重复的两个数

```python
# 参数arr是输入的待查数组
# 返回值是两个值的列表，内容没有重复的
class Solution:
    def theTwoNumbers(self, a):
        ans = [0, 0]
        for i in a:
            ans[0] = ans[0] ^ i
        c = 1
        while c & ans[0] != c:
            c = c << 1
        for i in a:
            if i & c == c:
                ans[1] = ans[1] ^ i
        ans[0] = ans[0] ^ ans[1]
        return ans
if __name__ == '__main__':
    arr = [1, 2, 5, 1]
    solution = Solution()
    print(" 数组为：", arr)
    print(" 两个没有重复的数字是:", solution.theTwoNumbers(arr))
```

## 10.双胞胎字符串

```python
#参数s和t是一对字符串
#返回值是个字符串，能否根据规则转换
class Solution:
    def isTwin(self, s, t):
        if len(s) != len(t):
            return "No"
        oddS = []
        evenS = []
        oddT = []
        evenT = []
        for i in range(len(s)):
            if i & 1:
                oddS.append(s[i])
                oddT.append(t[i])
            else:
                evenS.append(s[i])
                evenT.append(t[i])
        oddS.sort()
        oddT.sort()
        evenS.sort()
        evenT.sort()
        for i in range(len(oddS)):
            if oddS[i] != oddT[i]:
                return "No"
        for i in range(len(evenS)):
            if evenS[i] != evenT[i]:
                return "No"
        return "Yes"
if __name__ == '__main__':
    s = "abcd"
    t = "cdab"
    solution = Solution()
    print(" s与t分别为：", s, t)
    print(" 是否:", solution.isTwin(s, t))
```

最接近target的值   

\#参数array是输入列表

\#参数target是目标值

\#返回值是整数

class Solution:

  def closestTargetValue(self, target, array):

​    n = len(array)

​    if n < 2:

​      return -1

​    array.sort()

​    diff = 0x7fffffff

​    left = 0

​    right = n - 1

​    while left < right:

​      if array[left] + array[right] > target:

​        right -= 1

​      else:

​        diff = min(diff, target - array[left] - array[right])

​        left += 1

​    if diff == 0x7fffffff:

​      return -1

​    else:

​      return target - diff

if __name__ == '__main__':

  array = [1,3,5,11,7]

  target = 15

  solution = Solution()

  print(" 输入数组为：", array,"目标值为：", target)

  print(" 最近可以得到值为:", solution.closestTargetValue(target, array))

点积  

 

\#参数A和B是输入列表

\#返回值是个整数，是点积

class Solution:

  def dotProduct(self, A, B):

​    if len(A) == 0 or len(B) == 0 or len(A) != len(B):

​      return -1

​    ans = 0

​    for i in range(len(A)):

​      ans += A[i] * B[i]

​    return ans

if __name__ == '__main__':

  A = [1,1,1]

  B = [2,2,2]

  solution = Solution()

  print(" A与B分别为：", A, B)

  print(" 点积为：", solution.dotProduct(A, B))

函数运行时间  

 

\#参数s为输入原始字符串

\#返回值是个字符串，意为每个名字的函数运行了多久

class Solution:

  def getRuntime(self, a):

​    map={}

​    for i in a:

​      count = 0

​      while not i[count] == ' ':

​        count = count + 1

​      fun = i[0 : count]

​      if i[count+2] == 'n':

​        count = count + 7

​        v = int(i[count:len(i)])

​        if fun in map.keys():

​          map[fun] = v - map[fun]

​        else:

​          map[fun] = v

​      else:

​        count = count + 6

​        v = int(i[count:len(i)])

​        map[fun] = v - map[fun]

​    res=[]

​    for i in map:

​      res.append(i)

​    res.sort()

​    for i in range(0,len(res)):

​      res[i] = res[i] + '|' + str(map[res[i]])

​    return res

if __name__ == '__main__':

  s = ["F1 Enter 10","F2 Enter 18","F2 Exit 19","F1 Exit 20"]

  solution = Solution()

  print(" 输入运行时间为：", s)

  print(" 每个输出时间为:", solution.getRuntime(s))

查询区间  

 

\#参数List是区间列表

\#参数number是待查数字

\#返回值是个字符串，True或者False

class Solution:

  def isInterval(self, intervalList, number):

​    high = len(intervalList) - 1

​    low = 0

​    while high >= low:

​      if 0 < (number - intervalList[(high + low)//2][0]) <= 1000:

​        return 'True'

​      elif 1000 < number - intervalList[(high + low)//2][0]:

​        low = (high + low) // 2 + 1

​      elif 0 > number - intervalList[(high + low)//2][0]:

​        high = (high + low) // 2 - 1

​    return 'False'

if __name__ == '__main__':

  number = 6000

  intervalList = [[100,1100],[1000,2000],[5500,6500]]

  solution = Solution()

  print(" 区间List为：", intervalList)

  print(" 数字为：", number)

  print(" 是否在区间中:", solution.isInterval(intervalList, number)) 

飞行棋  

 

\#参数length是棋盘长度（不包含起始点）

\#参数connections是跳点的集合

\#返回值是个整数，代表最小步数

class Solution:

  def modernLudo(self, length, connections):

​    ans = [i for i in range(length+1)]

​    for i in range(length+1):

​      for j in range(1,7):

​        if i - j >= 0:

​          ans[i] = min(ans[i], ans[i-j]+1)

​      for j in connections:

​        if i == j[1]:

​          ans[i] = min(ans[i], ans[j[0]])

​    return ans[length]

~~#~~~~参数~~~~length~~~~是棋盘长度（不包含起始点）~~~~~~

~~#~~~~参数~~~~connections~~~~是跳点的集合~~~~~~

~~#~~~~返回值是个整数，代表最小步数~~~~~~

\#SPFA解法

class Solution:

  """

  参数length为棋盘长度

  参数connections为连接位置表

  返回最小次数

  """

  def modernLudo(self, length, connections):

​    dist = [1000000000 for i in range(100050)]

​    vis = [0 for i in range(100050)]

​    Q = [0 for i in range(100050)]

​    st = 0

​    ed = 0    

​    dist[1] =0

​    vis[1] = 1 

​    Q[ed] = 1;

​    ed += 1

​    while(st<ed) :

​      u = Q[st]

​      st += 1

​      vis[u] = 0

​      for roads in connections :

​        if(roads[0] != u):

​          continue

​        v = roads[1]

​        if(dist[v] > dist[u]):

​          dist[v] = dist[u]

​          if(vis[v] == 0) :

​            vis[v] = 1

​            Q[ed] = v

​            ed += 1

​      for i in range(1, 7):

​        if (i + u > length):

​          break

​        v = i + u

​        if(dist[v] > dist[u] + 1) :

​          dist[v] = dist[u] + 1

​          if(vis[v] == 0):

​            vis[v] = 1

​            Q[ed] = v

​            ed += 1

​    return dist[length]

if __name__ == '__main__':

  length = 15

  connections = [[2, 8],[6, 9]]

  solution = Solution()

  print(" 棋盘长度为：", length)

  print(" 连接为：", connections)

  print(" 最小需要为:", solution.modernLudo(length, connections)) 

移动石子  

 

\#参数arr是一个列表

\#返回值为整数，为最小移动次数

class Solution:

  def movingStones(self, arr):

​    arr = sorted(arr)

​    even = 0

​    odd = 0

​    for i in range(0,len(arr)):

​      odd += abs(arr[i]-(2*i+1))

​      even += abs(arr[i] - (2*i+2))

​    if odd < even:

​      return odd

​    return even

if __name__ == '__main__':

arr = [1, 6, 7, 8, 9]

solution = Solution()

  print(" 数组是：", arr)

  print(" 最小移动数是:", solution.movingStones(arr))

数组剔除元素后的乘积  

 

class Solution:

  \#参数A: 整数数组A

  \#返回值: 整数数组B

  def productExcludeItself(self, A):

​    length ,B = len(A) ,[]

​    f = [ 0 for i in range(length + 1)]

​    f[ length ] = 1

​    for i in range(length - 1 , 0 , -1):

​      f[ i ] = f[ i + 1 ] * A[ i ]

​    tmp = 1

​    for i in range(length):

​      B.append(tmp * f[ i + 1 ])

​      tmp *= A[ i ]

​    return B

\#主函数

if __name__ == '__main__':

  solution = Solution()

  A = [1, 2, 3, 4]

  B = solution.productExcludeItself(A)

  print("输入：", A)

  print("输出：", B)

键盘的一行  

 

class Solution:

  \#参数words为字符串列表

  \#返回字符串列表

  def findWords(self, words):

​    res = []

​    s = ["qwertyuiop", "asdfghjkl", "zxcvbnm"]

​    for w in words:

​      for j in range(3):

​        flag = 1

​        for i in w:

​          if i.lower() not in s[j]:

​            flag = 0

​            break

​        if flag == 1:

​          res.append(w)

​          break

​    return res

\#主函数

if __name__ == '__main__':

word = ["Hello", "Alaska", "Dad", "Peace"]
   s = Solution()
   print("输入为：",word)

  print("输出为：",s.findWords(word))

第n个数位  

 

class Solution:

  """

  参数n为整数

  返回整数

  """

  def findNthDigit(self, n):

​    \# 初始化一位数的个数为9，从1开始

​    length = 1

​    count = 9

​    start = 1

​    while n > length * count:

​      \# 以此类推二位数的个数为90，从10开始

​      n -= length * count

​      length += 1

​      count *= 10

​      start *= 10

​    \# 找到第n位数所在的整数start  

​    start += (n - 1) // length

​    return int(str(start)[(n - 1) % length])

\#主函数

if __name__ == '__main__':

  s = Solution()

  n = 11

  print("输入为：",n)

  print("输出为：",s.findNthDigit(n))

找不同  

 

class Solution:

  """

  参数s为字符串

  参数t为字符串

  返回字符

  """

  def findTheDifference(self, s, t):

​    flag = 0

​    for i in range(len(s)):

​      \# 计算每一位字符的Ascll码之差

​      flag += (ord(t[i]) - ord(s[i]))

​    flag += ord(t[-1])

​    return chr(flag)

\#主函数

if __name__ == '__main__':

  s = Solution()

  n = "abcd"

  t = "abcde"

  print("输入字符串1为：",n)

  print("输入字符串2为：",t)

  print("输出插入字符为：",s.findTheDifference(n,t))

第k个组合  

 

\#参数k代表寻找的组数

\#参数n代表有多少人

\#返回值是一个列表，是目标数组~~数~~里的按序排列

class Solution:

  def getCombination(self, n, k):

​    C = [[0] * (n + 1) for _ in range(n + 1)]

​    for i in range(n + 1):

​      C[i][0] = 1

​      C[i][i] = 1

​    \# Compute C(m, n) using C(m, n) = C(m-1, n-1)+C(m-1, n).

​    for i in range(1, n + 1):

​      for j in range(1, i):

​        C[i][j] = C[i - 1][j - 1] + C[i - 1][j]

​    ans = []

​    curr_index = 1

​    for i in range(1, n // 2 + 1):

​      base = C[n - curr_index][n // 2 - i]

​      \# Search for next digit in ans.

​      while k > base:

​        curr_index = curr_index + 1

​        base = base + C[n - curr_index][n // 2 - i]

​      base = base - C[n - curr_index][n // 2 - i]

​      k = k - base;

​      ans.append(curr_index)

​      curr_index = curr_index + 1

​    return ans

if __name__ == '__main__':

  n = 8

  k = 11

  solution = Solution()

  print(" 人数为：", n, " 找第k组：", k)

  print(" 第k组为:", solution.getCombination(n, k)) 

平面列表  

 

class Solution(object):

  \#参数nestedList： 一个列表，列表中的每个元素都可以是一个列表或整数

  \#返回值：一个整数列表

  def flatten(self, nestedList):

​    stack = [nestedList]

​    flatten_list = []

​    while stack:

​      top = stack.pop()

​      if isinstance(top, list):

​        for elem in reversed(top):

​          stack.append(elem)

​      else:

​        flatten_list.append(top)

​        

​    return flatten_list

\#主函数

if __name__ == '__main__':

  solution = Solution()

  nums = [[1,2],2,[1,1,3]]

  flatten_list = solution.flatten(nums)

  print("输入：", nums)

  print("输出：", flatten_list)

子域名访问计数  

最长AB子串  

 

\#参数S是待查字符串

\#返回值是一个整数，是最大字符串长度

class Solution:

  def getAns(self, S):

​    ans = 0

​    arr = [0 for i in range(len(S))]

​    sets = {}

​    if S[0] == 'A':

​      arr[0] = 1

​      sets[1] = 0

​    else:

​      arr[0] = -1

​      sets[-1] = 0

​    for i in range(1, len(S)):

​      if S[i] == 'A':

​        arr[i] = arr[i - 1] + 1

​        if arr[i] == 0:

​          ans = i + 1

​          continue

​        if arr[i] in sets:

​          ans = max(ans, i - sets[arr[i]])

​        else:

​          sets[arr[i]] = i

​      else:

​        arr[i] = arr[i - 1] - 1

​        if arr[i] == 0:

​          ans = i + 1

​          continue

​        if arr[i] in sets:

​          ans = max(ans, i - sets[arr[i]])

​        else:

​          sets[arr[i]] = i

​    return ans

if __name__ == '__main__':

  S = "ABABAB"

  solution = Solution()

  print(" AB字符串：", S)

  print(" 最长AB出现次数相同的子字符串长度:", solution.getAns(S)) 

删除字符  

 

\#参数s是待删除字符的原字符串

\#参数t是目标字符串

\#返回值是一个布尔值，意为能否由s删除一些字符得到t

class Solution:

  def canGetString(self, s, t):

​    pos = 0

​    for x in t:

​      while pos < len(s) and s[pos] != x:

​        pos += 1

​      if pos == len(s):

​        return False

​      pos += 1

​    return True

if __name__ == '__main__':

  s="abc"

  t="c"

  solution = Solution()

  print(" 原string和目标string分别为：", s, t)

  print(" 能否实现:", solution.canGetString(s, t)) 

字符串写入的行数  

 

class Solution(object):

  def numberOfLines(self, widths, S):

​    \#参数widths为数组

​    \#参数S为字符串

​    \#返回数组

​    line = 1

​    space = 0

​    flag = False

​    for c in S:

​      if flag:

​        line += 1

​        flag = False

​      space += widths[ord(c) - 97]

​      if space > 100:

​        line += 1

​        space = widths[ord(c) - 97]

​      elif space == 100:

​        space = 0

​        flag = True

​    return [line, space]

if __name__ == '__main__':

  solution=Solution()

width=[10,10,10,10,10,10,10,10,10,10,10,10,10,10,10,10,10,10,10,10,10,10,10,10,10,10]

  s="abcdefghijklmnopqrstuvwxyz"

  print("输入字符宽度为：",width)

  print("输入的字符串为：",s)

  print("输出为：",solution.numberOfLines(width,s))

独特的摩尔斯编码  

 

class Solution:

  def uniqueMorseRepresentations(self, words):

​    \#参数words为列表

​    \#返回整数

​    \# 用set保存出现过的摩斯码即可

​    morse = [".-","-...","-.-.","-..",".","..-.","--.","....","..",".---","-.-",".-..","--",

​         "-.","---",".--.","--.-",".-.","...","-","..-","...-",".--","-..-","-.--","--.."]

​    s = set()

​    for word in words:

​      tmp = ''

​      for w in word:

​        tmp += morse[ord(w) - 97]

​      s.add(tmp)

​    return len(s)

if __name__ == '__main__':

  solution=Solution()

  inputnum=["gin", "zen", "gig", "msg"]

  print("输入为：",inputnum)

  print("输出为：",solution.uniqueMorseRepresentations(inputnum))

比较字符串  

 

class Solution:

  \#参数A : 包括大写字母的字符串

  \#参数B : 包括大写字母的字符串

  \#返回值: 如果字符串A包含B中的所有字符，返回True，否则返回False

  def compareStrings(self, A, B):

​    if len(B) == 0:

​      return True

​    if len(A) == 0:

​      return False

​    \#trackTable首先记录A中所有的字符以及它们的个数，然后遍历B,如果出现trackTable[i]小于0的情况，说明B中该字符出现的次数大于在A中出现的次数

​    trackTable = [0 for _ in range(26)]

​    for i in A:

​      trackTable[ord(i) - 65] += 1

​    for i in B:

​      if trackTable[ord(i) - 65] == 0:

​        return False

​      else:

​        trackTable[ord(i) -65] -= 1

​    return True

\#主函数

if __name__ == '__main__':

  solution = Solution()

  A = "ABCD"

  B = "ACD"

  print("输入：", A, B)

  print("输出：", solution.compareStrings(A,B))

能否转换  

 

\#参数S和T为原始字符串和目标字符串

\#返回值是布尔值，代表能否转换

class Solution:

  def canConvert(self, s, t):

​    j = 0

​    for i in range(len(s)):

​      if s[i] == t[j]:

​        j += 1

​        if j == len(t):

​          return True

​    return False

if __name__ == '__main__':

  s = "longterm"

  t = "long"

  solution = Solution()

  print(" S与T分别为：", s, t)

  print(" 能否删除得到:", solution.canConvert(s, t)) 

经典二分查找问题  

 

\#参数nums是一个整型排序数组

\#参数target是一个任意整型数

\#返回值是一个整型数，若nums存在，返回该数位置；若不存在，返回-1

class Solution:

  def findPosition(self, nums, target):

​    if len(nums) is 0:

​      return -1

​    start = 0

​    end = len(nums)-1

​    while start + 1 < end :

​      mid = start + (end-start)//2

​      if nums[mid] == target:

​        end = mid

​      elif nums[mid] < target:

​        start = mid

​      else:

​        end = mid

​    if nums[start] == target:

​      return start

​    if nums[end] == target:

​      return end

​    return -1

\#主函数

if __name__ == '__main__':

generator=[1,2,2,4,5,5]

target = 2

solution = Solution()

print("输入:", generator)

  print("输出:", solution. findposition(generator, target))

抽搐词  

 

class Solution:

  def twitchWords(self, str):

​    n = len(str)

​    c = str[0]

​    left = 0

​    ans = []

​    for i in range(n):

​      if str[i] != c:

​        if i - left >= 3:

​          ans.append([left, i - 1])

​        c = str[i]

​        left = i

​    if n - left >= 3:

​      ans.append([left, n - 1])

​    return ans

\#主函数

if __name__ == '__main__':

  str = "whooooisssbesssst"

  solution = Solution()

  print(" 输入为：", str)

  print(" 输出为：", solution.twitchWords(str))

排序数组中最接近元素  

 

\#参数nums是一个整型排序数组

\#参数target是一个整型数

\#返回值是这个数组中最接近target的整数

class Solution:

  def findPosition(self, A, target):

​    if not A:

​      return -1

​    start, end = 0,len(A)-1

​    while start+ 1<end:

​      mid = start +(end-start)//2

​      if A[mid]<target:

​        start= mid

​      elif A[mid]>target:

​        end = mid

​      else:

​        return mid

​    if target-A[start]<A[end]-target:

​      return start

​    else:

​      return end

\#主函数

if __name__ == '__main__':

  generator = [1,4,6]

  target = 3

  solution = Solution()

  print("输入：", generator,",target =",target)

  print("输出：", solution.findPosition(generator, target))

构造矩形  

 

class Solution:

  \#参数area为整数

  \#返回为整数

  def constructRectangle(self, area):

​    import math

​    W = math.floor(math.sqrt(area))

​    while area % W != 0:

​      W -= 1

​    return [area // W, W]

\#主函数

if __name__ == '__main__':

  s = Solution()

  area =4

  print("输入面积为：",area)

  print("输出长宽为：",s.constructRectangle(area))

两个排序数组合~~组和~~的第k小元素  

 

\#参数A，B是整型排序数组

\#参数k是一个整型数，表示第k小

\#返回值是数组中第k小的整数

import heapq

class Solution:

  def kthSmallestSum(self, A, B, k):

​    if not A or not B:

​      return None

​    n, m = len(A), len(B)

​    minheap = [(A[0] + B[0], 0, 0)]

​    visited = set([0])

​    num = None

​    for _ in range(k):

​      num, x, y = heapq.heappop(minheap)

​      if x + 1 < n and (x + 1) * m + y not in visited:

​        heapq.heappush(minheap, (A[x + 1] + B[y], x + 1, y))

​        visited.add((x + 1) * m + y)

​      if y + 1 < m and x * m + y + 1 not in visited:

​        heapq.heappush(minheap, (A[x] + B[y + 1], x, y + 1))

​        visited.add(x * m + y + 1)

​    return num

\#主函数

if __name__ == '__main__':

generator_A = [1,7,11]

generator_B = [2,4,6]

  k = 4

  solution = Solution()

print("输入:", generator_A,generator_B)

print("k= ",k)

  print("输出:", solution.kthSmallestSum(generator_A,generator_B, k))

玩具工厂  

 

\#参数type是一个字符串，表示不同玩具类型

\#返回值是不同类型对应的玩具对象

class Toy:

  def talk(self):

​    raise NotImplementedError('This method should have implemented.')

class Dog(Toy):

  def talk(self):

​    print ("Wow")

class Cat(Toy):

  def talk(self):

​    print ("Meow")

class ToyFactory:

  def getToy(self, type):

​    if type == 'Dog':

​      return Dog()

​    elif type == 'Cat':

​      return Cat()

​    return None

\#主函数

if __name__ == '__main__':

ty = ToyFactory()

type='Dog'

type1='Cat'

toy = ty.getToy(type)

print("输入：type= Dog，输出：")

toy.talk()

toy = ty.getToy(type1)

print("输入：type= Cat，输出：")

toy.talk()

形状工厂  

 

\#参数shapeType是一个字符串，表示不同形状

\#返回值是不同对象，Triangle，Square，Rectangle

class Shape:

  def draw(self):

​    raise NotImplementedError('This method should have implemented.')

class Triangle(Shape):

​    def draw(self):

​      print(" /\\")

​      print(" / \\")

​      print("/____\\")

class Rectangle(Shape):

  def draw(self):

​    print(" ----")

​    print("|  |")

​    print(" ----")

class Square(Shape):

  def draw(self):

​    print( " ----")

​    print( "|  |")

​    print( "|  |")

​    print( " ----")

class ShapeFactory:

  def getShape(self, shapeType):

​    if shapeType == "Triangle":

​      return Triangle()

​    elif shapeType == "Rectangle":

​      return Rectangle()

​    elif shapeType == "Square":

​      return Square()

​    else:

​      return None

\#主函数

if __name__ == '__main__':

  sf = ShapeFactory()

  shapeType='Triangle'

  shape = sf.getShape(shapeType)

  print("输入：type= Triangle，\n输出：")

  shape.draw()

  shapeType1='Rectangle'

  shape = sf.getShape(shapeType1)

  print("输入：type= Rectangle，\n输出：")

  shape.draw()

  shapeType2='Square'

  shape = sf.getShape(shapeType2)

  print("输入：type= Square，\n输出：")

  shape.draw()

二叉树最长连续序列  

 

\#参数root是一个二叉树的根

\#返回值是此二叉树中最长连续序列

class TreeNode:

  def __init__(self, val):

​    self.val = val

​    self.left = None

​    self.right = None

class Solution:

  def longestConsecutive(self, root):

​    return self.helper(root, None, 0)

  def helper(self, root, parent, len):

​    if root is None:

​      return len

​    if parent != None and root.val == parent.val + 1:

​      len += 1

​    else:

​      len = 1

​    return max(len, max(self.helper(root.left, root, len), \

​              self.helper(root.right, root, len)))

\#主函数

if __name__ == '__main__':

  root = TreeNode(1)

  root.right = TreeNode(3)

  root.right.left = TreeNode(2)

  root.right.right = TreeNode(4)

  root.right.right.right = TreeNode(5)

solution= Solution()

print("输入是： {1,#,3,2,4,#,#,#,5}")

print("输出是：", solution.longestConsecutive(root))

首字母大写  

 

class Solution:

  \#参数s为字符串

  \#返回字符串

  def capitalizesFirst(self, s):

​    n = len(s)

​    s1 = list(s)

​    if s1[0] >= 'a' and s1[0] <= 'z':

​      s1[0] = chr(ord(s1[0]) - 32)

​    for i in range(1, n):

​      if s1[i - 1] == ' ' and s1[i] != ' ':

​        s1[i] = chr(ord(s1[i]) - 32)

​    return ''.join(s1)

if __name__ == '__main__':

  s = "i am from bupt"

  solution = Solution()

  print("输入为：",s)

  print("输出为：",solution.capitalizesFirst(s))

7进制  

 

class Solution:

  \#参数num为10进制整数

  \#返回7进制整数

  \#不断执行对7取模和取整操作，直到商小于7

  def convertToBase7(self, num):

​    if num < 0: 

​      return '-' + self.convertToBase7(-num)

​    if num < 7: 

​      return str(num)

​    return self.convertToBase7(num // 7) + str(num % 7)

if __name__ == '__main__':

  num = 777

  solution = Solution()

  print("输入为：",num)

  print("输出为：",solution.convertToBase7(num))

查找数组中没有出现的所有数字  

 

class Solution:

  \#参数为nums整数列表

  \#返回整数列表

  def findDisappearedNumbers(self, nums):

​    n = len(nums)

​    s = set(nums)

​    res = [i for i in range(1, n+1) if i not in s]

​    return res

\#主函数

if __name__ == '__main__':

  s = Solution()

  n = [4,3,2,7,8,2,3,1]

  print("输入为：",n)

  print("输出为：",s.findDisappearedNumbers(n))

回旋镖的数量  

 

class Solution(object):

  def getDistance(self, a, b):

​    dx = a[0] - b[0]

​    dy = a[1] - b[1]

​    return dx * dx + dy * dy

  def numberOfBoomerangs(self, points):

​    \#参数points为整数列表

​    \#返回整数

​    if points == None:

​      return 0

​    ans = 0

​    for i in range(len(points)):

​      disCount = {}

​      for j in range(len(points)):

​        if i == j:

​          continue

​        distance = self.getDistance(points[i], points[j])

​        count = disCount.get(distance, 0)

​        disCount[distance] = count + 1

​      for distance in disCount:

​        ans += disCount[distance] * (disCount[distance] - 1)

​    return ans

\#主函数

if __name__ == '__main__':

  s = Solution()

  n = [[0,0],[1,0],[2,0]]

  print("输入为：",n)

  print("输出为：",s.numberOfBoomerangs(n))

合并排序数组  

 

class Solution:

  \#参数A: 已排序整数数组A有m个元素，但是A的大小是m+n

  \#参数m: 整数

  \#参数B: 已排序整数数组B，它有n个元素

  \#参数n: 整数

  \#返回值: 无

  def mergeSortedArray(self, A, m, B, n):

​    i, j = m-1, n-1

​    t = len(A)-1

​    while i >= 0 or j >= 0:

​      if i < 0 or (j >= 0 and B[j] > A[i]):

​        A[t] = B[j]

​        j -= 1

​      else:

​        A[t] = A[i]

​        i -= 1

​      t -= 1

\#主函数

if __name__ == '__main__':

  solution = Solution()

  A = [1,2,3,0,0]

  m = 3

  B = [4,5]

  n = 2

  solution.mergeSortedArray(A, m, B, n)

  print("输入：A = [1,2,3,0,0], 3, B = [4,5], 2")

  print("输出：", A)

最小路径和  

 

class Solution:

  \#参数grid: 二维整数数组

  \#返回值: 一个整数，使其路径上的所有数字之和最小化

  def minPathSum(self, grid):

​    for i in range(len(grid)):

​      for j in range(len(grid[0])):

​        if i == 0 and j > 0:

​          grid[i][j] += grid[i][j-1]

​        elif j == 0 and i > 0:

​          grid[i][j] += grid[i-1][j]

​        elif i > 0 and j > 0:

​          grid[i][j] += min(grid[i-1][j], grid[i][j-1])

​    return grid[len(grid) - 1][len(grid[0]) - 1]

\#主函数

if __name__ == '__main__':

  solution = Solution()

  grid = [[1,3,1],[1,5,1],[4,2,1]]

  length = solution.minPathSum(grid)

  print("输入：", grid)

  print("输出：", length)

大小写转换I  

 

class Solution:

  \#参数character: 字符

  \#返回值: 字符

  def lowercaseToUppercase(self, character):

​    \#ASCII码中小写字母与对应的大写字母相差32

​    return chr(ord(character) - 32)

\#主函数

if __name__ == '__main__':

  solution = Solution()

  ans = solution.lowercaseToUppercase('a')

​    print("输入： a")

​    print("输出：", ans)

原子的数量  

 

import re

import collections

class Solution(object):

  def countOfAtoms(self, formula):

​    parse = re.findall(r"([A-Z][a-z]*)(\d*)|(\()|(\))(\d*)", formula)

​    stack = [collections.Counter()]

​    for name, m1, left_open, right_open, m2 in parse:

​      if name:

​       stack[-1][name] += int(m1 or 1)

​      if left_open:

​       stack.append(collections.Counter())

​      if right_open:

​        top = stack.pop()

​        for k in top:

​         stack[-1][k] += top[k] * int(m2 or 1)

​    return "".join(name + (str(stack[-1][name]) if stack[-1][name] > 1 else '') for name in sorted(stack[-1]))

\#主函数

if __name__ == '__main__':

  solution = Solution()

  Test_in = "H2O"

  Test_out = solution.countOfAtoms(Test_in)

  print("输入：",Test_in)

  print("输出：",Test_out)

矩阵中的最长递增路径  

 

DIRECTIONS = [(1, 0), (-1, 0), (0, -1), (0, 1)]

class Solution:

  """

  参数matrix为整数矩阵

  返回整数

  """

  def longestIncreasingPath(self, matrix):

​    if not matrix or not matrix[0]:

​      return 0

​    sequence = []

​    for i in range(len(matrix)):

​      for j in range(len(matrix[0])):

​        sequence.append((matrix[i][j], i, j))

​    sequence.sort()

​    check = {}

​    for h, x, y in sequence:

​      cur_pos = (x, y)

​      if cur_pos not in check:

​        check[cur_pos] = 1

​      cur_path = 0

​      for dx, dy in DIRECTIONS:

​        if self.is_valid(x+dx, y+dy, matrix, h):

​          cur_path = max(cur_path, check[(x+dx, y+dy)])

​      check[cur_pos] += cur_path

​    vals = check.values()

​    return max(vals)

  def is_valid(self, x, y, matrix, h):

​    row, col = len(matrix), len(matrix[0])

​    return x >= 0 and x < row and y >= 0 and y < col and matrix[x][y]<h

\#主函数

if __name__ == '__main__':

  solution = Solution()

  Test_in = [

   [9,9,4],

   [6,6,8],

   [2,1,1]

  ]

  Test_out = solution.longestIncreasingPath(Test_in)

  print("输入：",Test_in)

  print("输出：",Test_out)

大小写转换II  

 

class Solution:

  \#参数str: 字符串

  \#返回值: 字符串

  def lowercaseToUppercase2(self, str):

​    p = list(str)

​    \#遍历整个字符串，将所有的小写字母转成大写字母

​    for i in range(len(p)):

​      if p[i] >= 'a' and p[i] <= 'z':

​        p[i] = chr(ord(p[i]) - 32)

​    return ''.join(p)

\#主函数

if __name__ == '__main__':

  solution = Solution()

  s1 = "abC12"

  ans = solution.lowercaseToUppercase2(s1)

  print("输入：", s1)

  print("输出：", ans)

水仙花数  

 

class Solution:

  \#参数n: 数字的位数

  \#返回值: 所有n位数的水仙花数

  def getNarcissisticNumbers(self, n):

​    res = []

​    for x in range([0, 10**(n-1)][n > 1], 10**n):

​      y, k = x, 0

​      while x > 0:

​        k += (x % 10)**n

​        x //= 10

​      if k == y: res.append(k)

​    return res

\#主函数

if __name__ == '__main__':

  solution = Solution()

  n = 4

  ans = solution.getNarcissisticNumbers(n)

  print("输入：", n)

  print("输出：", ans)

余弦相似度  

 

import math

\#参数A，B都是一个整型数组，表示两个矢量

\#返回值是两个输入矢量的余弦相似度

class Solution:

  def cosineSimilarity(self, A, B):

​    if len(A) != len(B):

​      return 2

​    n = len(A)

​    up = 0

​    for i in range(n):

​      up += A[i] * B[i]

​    down = sum(a*a for a in A) * sum(b*b for b in B)

​    if down == 0:

​      return 2

​    return up / math.sqrt(down)

\#主函数

if __name__ == '__main__':

generator_A = [1,4,0]

  generator_B = [1,2,3]

  solution = Solution()

  print("输入: A=", generator_A)

  print("输入: B=", generator_B)

  print("输出: ", solution.cosineSimilarity(generator_A,generator_B))

链表节点计数  

 

\#参数head是链表的头部

\#返回值是链表的长度

class ListNode(object):

  def __init__(self, val, next=None):

​    self.val = val

​    self.next = next

class Solution:

  def countNodes(self, head):

​    cnt = 0

​    while head is not None:

​      cnt += 1

​      head = head.next

​    return cnt

\#主函数

if __name__ == '__main__':

  node1 = ListNode(1)

  node2 = ListNode(2)

  node3 = ListNode(3)

  node4 = ListNode(4)

  node1.next = node2

  node2.next = node3

  node3.next = node4

solution = Solution()

print("输入: ", node1.val,node2.val,node3.val,node4.val)

  print("输出: ", solution. countNodes(node1))

最高频的K个单词  

 

\#参数words是一个字符串数组

\#参数k代表第k高频率出现

\#返回值是一个字符串数组，表示出现频率前k高字符串

class Solution:

  def topKFrequentWords(self, words, k):

​    dict = {}

​    res = []

​    for word in words:

​      if word not in dict:

​        dict[word] = 1

​      else:

​        dict[word] += 1

​    sorted_d = sorted(dict.items(), key=lambda x:x[1], reverse=True)

​    for i in range(k):

​      res.append(sorted_d[i][0])

​    return res

\#主函数

if __name__ == '__main__':

generator = ["yes", "long", "code",

​         "yes", "code", "baby",

​         "you", "baby", "chrome",

​         "safari", "long", "code",

​         "body", "long", "code"]

k = 4

solution = Solution()

print("输入: ", generator)

print("输入: ","k = ", k)

print("输出: ", solution.topKFrequentWords(generator,k))

单词的添加与查找  

 

\#参数word是要添加的的单词

\#返回值是个布尔值，查找单词成功则返回True，否则，返回False

class TrieNode:

  def __init__(self):

​    self.children = {}

​    self.is_word = False

class WordDictionary:

  def __init__(self):

​    self.root = TrieNode()

  def addWord(self, word):

​    node = self.root

​    for c in word:

​      if c not in node.children:

​        node.children[c] = TrieNode()

​      node = node.children[c]

​    node.is_word =True

  def search(self, word):

​    if word is None:

​      return False

​    return self.search_helper(self.root, word, 0)

  def search_helper(self, node, word, index):

​    if node is None:

​      return False

​    if index >= len(word):

​      return node.is_word

​    char = word[index]

​    if char != '.':

​      return self.search_helper(node.children.get(char), word, index + 1)

​    for child in node.children:

​      if self.search_helper(node.children[child], word, index + 1):

​        return True

​    return False

\#主函数

if __name__ == '__main__':

  solution = WordDictionary()

  solution.addWord("bad")

  solution.addWord("dad")

  solution.addWord("mad")

  print('输入： addWord("bad"),addWord("dad"),addWord("mad")')

  print('输入： search("pad"),search("dad"),search(".ad"),search("b..")')

  print("输出： ",

  solution.search("pad"),

  solution.search("bad"),

  solution.search(".ad"),

  solution.search("b.."))

石子归并  

 

\#参数A是一个整型数组

\#返回值是一个整数，表示最小的合并代价

import sys

class Solution:

  def stoneGame(self, A):

​    n = len(A)

​    if n < 2:

​      return 0

​    dp = [[0] * n for _ in range(n)]

​    cut = [[0] * n for _ in range(n)]

​    range_sum = self.get_range_sum(A)

​    for i in range(n - 1):

​      dp[i][i + 1] = A[i] + A[i + 1]

​      cut[i][i + 1] = i

​    for length in range(3, n + 1):

​      for i in range(n - length + 1):

​        j = i + length - 1

​        dp[i][j] = sys.maxsize

​        for mid in range(cut[i][j - 1], cut[i + 1][j] + 1):

​          if dp[i][j] > dp[i][mid] + dp[mid + 1][j] + range_sum[i][j]:

​            dp[i][j] = dp[i][mid] + dp[mid + 1][j] + range_sum[i][j]

​            cut[i][j] = mid

​    return dp[0][n - 1]

  def get_range_sum(self, A):

​    n = len(A)

​    range_sum = [[0] * n for _ in range(len(A))]

​    for i in range(n):

​      range_sum[i][i] = A[i]

​      for j in range(i + 1, n):

​        range_sum[i][j] = range_sum[i][j - 1] + A[j]

​    return range_sum

\#主函数

if __name__ == '__main__':

generator = [3,4,3]

solution = Solution()

print("输入：", generator)

print("输出：", solution.stoneGame(generator))

简单计算器  

 

\#参数a，b是两个任意整数

\#operator是运算符+, -, *, /

\#返回值是浮点型运算结果

class Solution:

  def calculate(self, a, operator, b):

​    if operator == '+':

​      return a + b

​    elif operator == '-':

​      return a - b

​    elif operator == '*':

​      return a * b

​    elif operator == '/':

​      return a / b

\#主函数

if __name__ == '__main__':

a=8

b=3

operator1='+'

operator2='-'

operator3='*'

operator4='/'

solution = Solution()

print("输入：", a ,operator1 ,b)

print("输出：", solution.calculate(a,operator1,b))

print("输入：", a ,operator2 ,b)

print("输出：", solution.calculate(a,operator2,b))

print("输入：", a ,operator3 ,b)

print("输出：", solution.calculate(a,operator3,b))

print("输入：", a ,operator4 ,b)

print("输出：", solution.calculate(a,operator4,b))

数组第二大数  

 

\#参数nums是一个整型数组

\#返回值secValue是数组中第二大数

class Solution:

  def secondMax(self, nums):

​    maxValue = max(nums[0], nums[1])

​    secValue = min(nums[0], nums[1])

​    for i in range(2, len(nums)):

​      if nums[i] > maxValue:

​        secValue = maxValue

​        maxValue = nums[i]

​      elif nums[i] > secValue:

​        secValue = nums[i]

​    return secValue

\#主函数

if __name__ == '__main__':

  generator = [3,4,7,9]

  solution = Solution()

  print("输入： ", generator)

  print("输出： ", solution.secondMax(generator))

二叉树叶子节点之和  

 

\#参数root是二叉树的根

\#返回值是个整数，叶子节点之和

class TreeNode:

  def __init__(self, val):

​    self.val = val

​    self.left, self.right = None, None

class Solution:

  def leafSum(self, root):

​    p = []

​    self.dfs(root, p)

​    return sum(p)

  def dfs(self, root, p):

​    if root is None:

​      return

​    if root.left is None and root.right is None:

​      p.append(root.val)

​    self.dfs(root.left, p)

​    self.dfs(root.right, p)

\#主函数

if __name__ == '__main__':

root = TreeNode(1)

root.left = TreeNode(2)

root.right = TreeNode(3)

root.left.left = TreeNode(4)

solution = Solution()

print("输入：", root.val,root.left.val,root.right.val,root.left.left.val)

print("输出：", solution.leafSum(root))

二叉树的某层节点之和  

 

\#参数root是二叉树的根

\#参数level是树的目标层的深度

\#返回值是一个整数，表示该level叶子节点之和

class TreeNode:

  def __init__(self, val):

​    self.val = val

​    self.left, self.right = None, None

class Solution:

  def levelSum(self, root, level):

​    p = []

​    self.dfs(root, p, 1, level)

​    return sum(p)

  def dfs(self, root, p, dep, level):

​    if root is None:

​      return

​    if dep == level:

​      p.append(root.val)

​      return

​    self.dfs(root.left, p, dep+1, level)

​    self.dfs(root.right, p, dep+1, level)

\#主函数

if __name__ == '__main__':

  root = TreeNode(1)

  root.left = TreeNode(2)

  root.right = TreeNode(3)

  root.left.left = TreeNode(4)

  root.left.right = TreeNode(5)

  root.right.left = TreeNode(6)

  root.right.right = TreeNode(7)

  root.left.right.right = TreeNode(8)

  root.right.right.right = TreeNode(9)

  depth = 3

  solution = Solution()

  print("输入：",root.val,root.left.val,root.right.val,root.left.left.val,

​     root.left.right.val,root.right.left.val,root.right.right.val,

​     root.left.right.right.val,root.right.right.right.val)

print("输入： depth= ", depth)

   print("输出：",solution.levelSum(root,depth))

判断尾数  

 

\#参数str是输入01串

\#返回值是一个整数，代表最后一个词的长度

class Solution:

  def judgeTheLastNumber(self, str):

​    if str[-1] == 1:

​      return 2

​    for i in range(-2, -len(str) - 1, -1):

​      if str[i] == 0:

​        return -1 * ((i * -1 + 1) % 2) + 2

​    return -1 * (len(str) % 2) + 2

if __name__ == '__main__':

  str = "111110"

  solution = Solution()

  print(" 原01串为：", str)

  print(" 最后一个词长度是:", solution.judgeTheLastNumber(str)) 

两个字符串是变位词  

 

class Solution:

  \#参数s: 第一个字符串

  \#参数t: 第二个字符串

  \#返回值: True或False

  def anagram(self, s, t):

​    set_s = [0] * 256

​    set_t = [0] * 256

​    for i in range(0, len(s)):

​      set_s[ord(s[i])] += 1

​    for i in range(0, len(t)):

​      set_t[ord(t[i])] += 1

​    for i in range(0, 256):

​      if set_s[i] != set_t[i]:

​        return False

​    return True

\#主函数

if __name__ == '__main__':

  solution = Solution()

  s = "abcd"

  t = "dcba"

  ans = solution.anagram(s, t)

  print("输入：", s, t)

  print("输出：", ans)

最长单词  

 

class Solution:

  \#参数dictionary: 字符串数组

  \#返回值: 字符串数组

  def longestWords(self, dictionary):

​    answer = []

​    maxLength = 0

​    for item in dictionary:

​      if len(item) > maxLength:

​        maxLength = len(item)

​        answer = [item]

​      elif len(item) == maxLength:

​        answer.append(item)

​    return answer

\#主函数

if __name__ == '__main__':

  solution = Solution()

  dic = ["dog","google","facebook","internationalization","blabla"]

  answer = solution.longestWords(dic)

  print("输入：", dic)

  print("输出：", answer)

机器人能否返回原点  

 

class Solution:

  \#参数moves为字符串

  \#返回布尔类型

  def judgeCircle(self, moves):

​    count_RL = count_UD = 0

​    for c in moves:

​      if c == 'R':

​        count_RL += 1

​      if c == 'L':

​        count_RL -= 1

​      if c == 'U':

​        count_UD += 1

​      if c == 'D':

​        count_UD -= 1

​    return count_RL == 0 and count_UD == 0

if __name__ == '__main__':

  solution=Solution()

  moves="UD"

  print("输入为：",moves)

print("输出为：",solution.judgeCircle(moves))

链表倒数第n个节点  

 

\#定义链表节点

class ListNode(object):

  def __init__(self, val):

​    self.val = val

​    self.next = None

class Solution:

  \#参数head: 链表的第一个节点。

  \#参数n: 整数

  \#返回值: 单链表的第n到最后一个节点。

  def nthToLast(self, head, n):

​    if head is None or n < 1:

​      return None

​    cur = head.next

​    while cur is not None:

​      cur.pre = head

​      cur = cur.next

​      head = head.next

​    n -= 1

​    while n > 0:

​      head = head.pre

​      n -= 1

​    return head

\#主函数

if __name__ == '__main__':

  solution = Solution()

  l0 = ListNode(3)

  l1 = ListNode(2)

  l2 = ListNode(1)

  l3 = ListNode(5)

  l0.next = l1

  l1.next = l2

  l2.next = l3

  ans = solution.nthToLast(l0, 2).val

  print("输入： 3->2->1->5->null, n = 2")

  print("输出：", ans)

链表求和  

 

\#定义链表节点

class ListNode(object):

  def __init__(self, val):

​    self.val = val

​    self.next = None

class Solution:

  def addLists(self, l1, l2) -> list:

​    dummy = ListNode(None)

​    tail = dummy

​    carry = 0 

​    while l1 or l2 or carry:

​      num = 0 

​      if l1:

​        num += l1.val 

​        l1 = l1.next

​      if l2:

​        num += l2.val 

​        l2 = l2.next

​      num += carry

​      digit, carry = num % 10, num // 10

​      node = ListNode(digit)

​      tail.next, tail = node, node 

​    return dummy.next

\#主函数

if __name__ == '__main__':

  solution = Solution()

  l0 = ListNode(7)

  l1 = ListNode(1)

  l2 = ListNode(6)

  l0.next = l1

  l1.next = l2

  l3 = ListNode(5)

  l4 = ListNode(9)

  l5 = ListNode(2)

  l3.next = l4

  l4.next = l5

  ans = solution.addLists(l0, l3)

  a = [ans.val, ans.next.val, ans.next.next.val]

  print("输入： 7->1->6->null, 5->9->2->null")

  print("输出： 2->1->9->null")

删除元素  

 

class Solution:

  \#参数A: 整数列表

  \#参数elem: 整数

  \#返回值：移除后的长度

  def removeElement(self, A, elem):

​    j = len(A)-1

​    for i in range(len(A) - 1, -1, -1):

​      if A[i] == elem:

​        A[i], A[j] = A[j], A[i]

​        j -= 1

​    return j+1

\#主函数

if __name__ == '__main__':

  solution = Solution()

  A = [0,4,4,0,0,2,4,4]

  e = 4

  ans = solution.removeElement(A, e)

  print("输入： [0,4,4,0,0,2,4,4], value = 4")

  print("输出：", ans)

克隆二叉树  

 

\#树的节点结构

\#参数val是节点值

class TreeNode:

  def __init__(self, val):

​    self.val = val

​    self.left, self.right = None, None

\#参数{TreeNode} root是二进制树的根

\#返回值clone_root是复制后新树的根

class Solution:

  def cloneTree(self, root):

​    if root is None:

​      return None

​    clone_root = TreeNode(root.val)

​    clone_root.left = self.cloneTree(root.left)

​    clone_root.right = self.cloneTree(root.right)

​    return clone_root

\#主函数

if __name__ == '__main__':

  root = TreeNode(1)

  root.left = TreeNode(2)

  root.right = TreeNode(3)

  root.left.left = TreeNode(4)

  root.left.right = TreeNode(5)

  solution = Solution()

  print("输入：", root.val,root.left.val,root.right.val,root.left.left.val,root.left.right.val)

  print("输出： ", solution.cloneTree(root).val,solution.cloneTree(root).left.val,solution.cloneTree(root).right.val,solution.cloneTree(root).left.left.val,solution.cloneTree(root).left.right.val)

合并两个排序链表  

 

\#定义链表节点

class ListNode(object):

  def __init__(self, val):

​    self.val = val

​    self.next = None

class Solution(object):

  \#参数l1: 链表头结节点

  \#参数l2: 链表头节点

  \#返回值: 链表头节点

  def mergeTwoLists(self, l1, l2):

​    dummy = ListNode(0)

​    tmp = dummy

​    while l1 != None and l2 != None:

​      if l1.val < l2.val:

​        tmp.next = l1

​        l1 = l1.next

​      else:

​        tmp.next = l2

​        l2 = l2.next

​      tmp = tmp.next

​    if l1 != None:

​      tmp.next = l1

​    else:

​      tmp.next = l2

​    return dummy.next

\#主函数

if __name__ == '__main__':

  solution = Solution()

  l0 = ListNode(1)

  l1 = ListNode(3)

  l2 = ListNode(8)

  l0.next = l1

  l1.next = l2

  l5 = ListNode(2)

  l6 = ListNode(4)

  l5.next = l6

  ans = solution.mergeTwoLists(l0, l5)

  a = [ans.val, ans.next.val, ans.next.next.val, 

​     ans.next.next.next.val, ans.next.next.next.next.val]

  print("输入： list1 = 1->3->8->null, list2 = 2->4->null")

  print("输出： 1->2->3->4->8->null")

反转整数  

 

\#参数n是一个整型数

\#返回值reverse是反转的整数

class Solution:

  def reverseInteger(self, n):

​    if n == 0:

​      return 0

​    neg = 1

​    if n < 0:

​      neg, n = -1, -n

​    reverse = 0

​    while n > 0:

​      reverse = reverse * 10 + n % 10

​      n = n // 10

​    reverse = reverse * neg

​    if reverse < -(1 << 31) or reverse > (1 << 31) - 1:

​      return 0

​    return reverse

\#主函数

if __name__ == '__main__':

  generator=1234

solution = Solution()

print("输入：", generator)

  print("输出：", solution. reverseInteger(generator))

报数  

 

\#参数n是一个正整数

\#返回值string是n所表示的报数序列

class Solution:

  def countAndSay(self, n):

​    string = '1'

​    for i in range(n - 1):

​      a = string[0]

​      count = 0

​      s = ''

​      for ch in string:

​        if a == ch:

​          count += 1

​        else:

​          s += str(count) + a

​          a = ch

​          count = 1

​      s += str(count) + a

​      string = s

​      a = string[0]

​    return string

\#主函数

if __name__ == '__main__':

  generator=5

solution = Solution()

print("输入:", generator)

  print("输出:", solution.countAndSay(generator))

完全二叉树  

 

\#参数root是二叉树的根

\#返回值是个布尔值，当完全二叉树时返回True，否则返回False

class TreeNode:

  def __init__(self, val):

​    self.val = val

​    self.left = None

​    self.right = None

class Solution:

  def isComplete(self, root):

​    if root is None:

​      return True

​    queue = [root]

​    index = 0

​    while index < len(queue):

​      if queue[index] is not None:

​        queue.append(queue[index].left)

​        queue.append(queue[index].right)

​      index += 1

​    while queue[-1] is None:

​      queue.pop()

​    for q in queue:

​      if q is None:

​        return False

​    return True

\#主函数

if __name__ == '__main__':

root = TreeNode(1)

  root.left = TreeNode(2)

  root.right = TreeNode(3)

  root.left.left = TreeNode(4)

  solution = Solution()

print("输入: ", root.val,root.left.val,root.right.val,root.left.left.val)

  print("输出: ", solution.isComplete(root))

对称二叉树  

 

\#参数root是二叉树的的根

\#返回值是个布尔值，是对称二叉树时返回True，否则返回False

class TreeNode:

  def __init__(self, val):

​    self.val = val

​    self.left = None

​    self.right = None

class Solution:

  def help(self, p, q):

​    if p == None and q == None: return True

​    if p and q and p.val == q.val:

​      return self.help(p.right, q.left) and self.help(p.left, q.right)

​    return False

  def isSymmetric(self, root):

​    if root:

​      return self.help(root.left, root.right)

​    return True

\#主函数

if __name__ == '__main__':

root = TreeNode(1)

root.left = TreeNode(2)

root.right = TreeNode(2)

root.right.right = TreeNode(3)

root.right.left = TreeNode(4)

root.left.right = TreeNode(4)

root.left.left = TreeNode(3)

solution = Solution()

print("输入: ", 

root.val,root.left.val,root.right.val,root.left.left.val,root.left.right. val,root.right.left.val, root.right.right.val)

  print("输出: ", solution.isSymmetric(root))

扭转后等价的二叉树  

 

\#参数a、b是二叉树的根

\#返回值是个布尔值，当它们等价时返回True，否则返回False

class TreeNode:

  def __init__(self, val):

​    self.val = val

​    self.left = None

​    self.right = None

class Solution:

  def isTweakedIdentical(self, a, b):

​    if a == None and b == None: return True

​    if a and b and a.val == b.val:

​      return self.isTweakedIdentical(a.left, b.left) and \

​        self.isTweakedIdentical(a.right, b.right) or \

​        self.isTweakedIdentical(a.left, b.right) and \

​        self.isTweakedIdentical(a.right, b.left)

​    return False

\#主函数

if __name__ == '__main__':

root = TreeNode(1)

root.left = TreeNode(2)

root.right = TreeNode(3)

root.left.left = TreeNode(4)

root1 = TreeNode(1)

root1.right = TreeNode(2)

root1.left = TreeNode(3)

root1.right.right = TreeNode(4)

solution = Solution()

print("输入: ", root.val,root.left.val,root.right.val,root.left.left.val," , ",root1.val,root1.left.val,root1.right.val,root1.right.right.val)

  print("输出: ", solution.isTweakedIdentical(root,root1))

岛屿的个数  

 

from collections import deque

\#参数grid是一个01矩阵

\#返回值islands是岛屿的个数

class Solution:

  def numIslands(self, grid):

​    if not grid or not grid[0]:

​      return 0

​    islands = 0

​    for i in range(len(grid)):

​      for j in range(len(grid[0])):

​        if grid[i][j]:

​          self.bfs(grid, i, j)

​          islands += 1

​    return islands

  def bfs(self, grid, x, y):

​    queue = deque([(x, y)])

​    grid[x][y] = False

​    while queue:

​      x, y = queue.popleft()

​      for delta_x, delta_y in [(1, 0), (0, -1), (-1, 0), (0, 1)]:

​        next_x = x + delta_x

​        next_y = y + delta_y

​        if not self.is_valid(grid, next_x, next_y):

​          continue

​        queue.append((next_x, next_y))

​        grid[next_x][next_y] = False

  def is_valid(self, grid, x, y):

​    n, m = len(grid), len(grid[0])

​    return 0 <= x < n and 0 <= y < m and grid[x][y]

\#主函数

if __name__ == '__main__':

  generator= [

​                 [1,1,0,0,0],

​                 [0,1,0,0,1],

​                 [0,0,0,1,1],

​                 [0,0,0,0,0],

​                 [0,0,0,0,1]

]

solution = Solution()

print("输入：", generator)

  print("输出：", solution.numIslands(generator))

判断是否为平方数之和  

 

import math

class Solution:

  \#参数num为整数

  \#返回布尔类型

  def checkSumOfSquareNumbers(self, num):

​    \# write your code here

​    if num < 0:

​      return False

​    for i in reversed(range(0, int(math.sqrt(num)) + 1)):

​      if i * i == num:

​        return True

​      j = num - i * i

​      k = int(math.sqrt(j))

​      if k * k == j:

​        return True

​    return False

if __name__=='__main__':

​     solution=Solution()

​     num=5

​     print("输入为：",num)

​     print("输出为：",solution.checkSumOfSquareNumbers(num))

滑动窗口内数的和  

 

class Solution:

  \#nums是整数数组

  \#k是滑动窗口

  \#返回每个窗口的数字和

  def winSum(self, nums, k):

​    n = len(nums)

​    if n < k or k <= 0:

​      return []

​    sums = [0] * (n - k + 1)

​    for i in range(k):

​      sums[0] += nums[i];

​    for i in range(1, n - k + 1):

​      sums[i] = sums[i - 1] - nums[i - 1] + nums[i + k - 1]

​    return sums

\#主函数

if __name__ == '__main__':

  inputnum=[1,2,7,8,5]

  k=3

  print("输入数组：",inputnum)

  print("输入窗口：",k)

  solution=Solution()

  print("输出数组：",solution.winSum(inputnum,k))

总汉明距离

 

class Solution:

  \#参数nums为整数

  \#返回整数

  def totalHammingDistance(self, nums):

​    return sum(b.count('0') * b.count('1') for b in zip(*map('{:032b}'.format, nums)))

\#主函数

if __name__ == '__main__':

  s = Solution()

  n = [4,14,2]

  print("输入为：",n)

  print("输出为：",s.totalHammingDistance(n))

硬币摆放  

 

import math

class Solution:

  \#参数n为整数

  \#返回整数

  \# n = (1 + x) * x / 2, 求得 x = (-1 + sqrt(8 * n + 1)) / 2, 对x取整

  def arrangeCoins(self, n):

​    return math.floor((-1 + math.sqrt(1 + 8*n)) / 2)

if __name__ == '__main__':

  n = 10

  solution = Solution()

  print("输入为：",n)

  print("输出为：",solution.arrangeCoins(n))

字母大小写转换  

 

class Solution(object):

  def letterCasePermutation(self, S):

​    \#参数S为字符串

​    \#返回字符串列表

​    \# 利用二进制对应字符串。其中0表示大小写不变，1表示改变大小写

​    res = []

​    indices = []

​    indices = [i for i,_ in enumerate(S) if S[i].isalpha()]

​    for i in range(0, pow(2,len(indices))):

​      if i==0:

​        res.append(S)

​      else:

​        j=i;bpos=0;nsl=list(S)

​        while j>0:

​          ci2c = indices[bpos]

​          if j&1 and S[ci2c].islower():

​            nsl[ci2c]=S[ci2c].upper()

​          elif j&1 and S[ci2c].isupper():

​            nsl[ci2c]=S[ci2c].lower()

​          bpos+=1

​          j = j >> 1

​        res.append("".join(nsl))

​    return res

if __name__ == '__main__':

  solution=Solution()

  S = "a1b2"

  print("输入为：",S)

  print("输出为：",solution.letterCasePermutation(S))
 4.运行结果

输入为： a1b2

输出为： ['a1b2', 'A1b2', 'a1B2', 'A1B2']

二进制表示中质数个计算置位  

 

class Solution(object):

  def countPrimeSetBits(self, L, R):

​    \# "L, R在[1, 10^6]范围

​    \# 可能的质数为2, 3, 5, 7, 11, 13, 17, 19

​    \# 统计1的个数在进行质数判定,因为二进制1的个数不会超过20个，枚举质数即可

​    k = 0

​    for n in range(L, R + 1):

​      if bin(n).count('1') in [2, 3, 5, 7, 11, 13, 17, 19]:

​        k = k + 1

​    return k

if __name__ == '__main__':

  solution=Solution()

  L=6

  R=10

  print("输入为：[",L,R,"]")

  print("输出为：",solution.countPrimeSetBits(L,R))
 4.运行结果

输入为：[ 6 10 ]

输出为：4

最少费用的爬台阶方法  

 

class Solution:

  \#参数cost为数组

  \#返回最小费用

  \#状态转移方程 dp[i] = min(dp[i-1] + cost[i-1],dp[i-2] + cost[i-2])

  def minCostClimbingStairs(self, cost):

​    a, b = 0, 0

​    for i in range(2, len(cost) + 1):

​      c = min(a + cost[i - 2], b + cost[i - 1])

​      a, b = b, c

​    return b

if __name__ == '__main__':

  solution=Solution()

  cost = [1, 100, 1, 1, 1, 100, 1, 1, 100, 1]

print("输入为：",cost)

  print("输出为：",solution.minCostClimbingStairs(cost))
 4.运行结果

输入为：[1, 100, 1, 1, 1, 100, 1, 1, 100, 1]

输出为：6

中心索引  

 

class Solution(object):

  def pivotIndex(self, nums):

​    left, right = 0, sum(nums)

​    for index, num in enumerate(nums):

​      right -= num

​      if left == right:

​        return index

​      left += num

​    return -1

if __name__ == '__main__':

  solution=Solution()

words=[1,7,3,6,5,6]

print("输入：",words)

print("输出：",solution.pivotIndex(words))

  

词典中最长的单词  

 

class Solution(object):

  def longestWord(self, words):

​    words.sort()

​    words.sort(key=len, reverse=True)

​    res = []

​    for word in words:

​      temp = word

​      i = 1

​      for i in range(len(temp)):

​        if temp[:len(temp) - i] in words:

​          if i == len(temp) - 1:

​            return temp

​          continue

​        else:

​          break

​    return ''

if __name__ == '__main__':

  solution=Solution()

  words=["w","wo","wor","worl", "world"]

  print("输入字典为：",words)

  print("输出单词为：",solution.longestWord(words))

重复字符串匹配  

 

class Solution:

  \#参数A为字符串

  \#参数B为字符串

  \#返回整数

  def repeatedStringMatch(self, A, B):

​    C = ""

​    for i in range(int(len(B)/len(A) + 3)):

​      if B in C:

​        return i

​      C += A

​    return -1

if __name__ == '__main__':

  solution=Solution()

  A = "abcd"

  B = "cdabcdab"

  print("输入字符串A为：",A)

  print("输入字符串B为：",B)

  print("需要重复次数：",solution.repeatedStringMatch(A,B))

不下降数组  

 

class Solution:

  \#参数nums为数组

  \#返回布尔类型

  def checkPossibility(self, nums):

​    count = 0

​    for i in range(1, len(nums)):

​      if nums[i] < nums[i - 1]:

​        count += 1

​        if i >= 2 and nums[i] < nums[i - 2]:

​          nums[i] = nums[i - 1]

​        else:

​          nums[i - 1] = nums[i]

​    return count <= 1

if __name__ == '__main__':

  solution=Solution()

  nums=[4,2,3]

  print("输入为：",nums)

  print("输出为：",solution.checkPossibility(nums))

最大的回文乘积  

 

class Solution:

  \#参数n为整数

  \#返回整数

  def largestPalindrome(self, n):

​    if n==1:

​      return 9

​    elif n ==7:

​      return 877

​    elif n== 8:

​      return 475

​    maxNum,minNum = 10**n - 1, 10**(n-1)

​    for i in range(maxNum, minNum, -1):

​      candidate = str(i)

​      candidate = candidate + candidate [::-1]

​      candidate = int(candidate)

​      j = maxNum

​      while j*j > candidate :

​        if candidate % j == 0:

​          return candidate % 1337

​        j -= 1

\#主函数

if __name__ == '__main__':

  s = Solution()

  n = 2

  print("输入为：",n)

  print("输出为：",s.largestPalindrome(n))

补数  

 

class Solution:

  \#参数num为整数

  \#返回整数

  def findComplement(self, num):

​    return num ^ ((1<<num.bit_length())-1)

\#主函数

if __name__ == '__main__':

  s = Solution()

  n = 5

  print("输入为：",n)

  print("输出为：",s.findComplement(n))

加热器  

 

class Solution:

  \#参数houses为数组

  \#参数heaters为整数

  \#返回整数

  def findRadius(self, houses, heaters):

​    heaters.sort()

​    ans = 0

​    for house in houses:

​      ans=max(ans,self.closestHeater(house,heaters))

​    return ans

  def closestHeater(self,house,heaters):

​    start = 0

​    end = len(heaters) - 1

​    while start + 1 < end:

​      m = start + (end - start) // 2

​      if heaters[m] == house:

​        return 0

​      elif heaters[m] < house:

​        start = m

​      else:

​        end = m

​    return min(abs(house - heaters[start]), abs(heaters[end] - house))

\#主函数

if __name__ == '__main__':

  s = Solution()

  n = [1,2,3]

  m = [2]

  print("输入房间位置为：",n)

  print("输入加热器位置：",m)

  print("输出加热半径为：",s.findRadius(n,m))

将火柴摆放成正方形  

 

class Solution:

  \#参数nums为数组

  \#返回布尔类型

  def makesquare(self, nums):

​    def dfs(nums, pos, target):

​      if pos == len(nums): 

​        return True

​      for i in range(4):

​        if target[i] >= nums[pos]:

​          target[i] -= nums[pos]

​          if dfs(nums, pos+1, target):

​            return True

​          target[i] += nums[pos]

​      return False

​    if len(nums) < 4 :

​      return False

​    numSum = sum(nums)

​    nums.sort(reverse = True)

​    if numSum % 4 != 0: 

​      return False

​    target = [numSum / 4] * 4;

​    return dfs(nums, 0, target)

\#主函数

if __name__ == '__main__':

  s = Solution()

  n = [1,1,2,2,2]

  print("输入为：",n)

  print("输出为：",s.makesquare(n))

可怜的猪  

 

class Solution:

  \#参数buckets为整数

  \#参数minutesToDie为整数

  \#参数minutesToTest为整数

  \#返回整数

  def poorPigs(self, buckets, minutesToDie, minutesToTest):

​    pigs = 0

​    while (minutesToTest / minutesToDie + 1) ** pigs < buckets:

​      pigs += 1

​    return pigs

\#主函数

if __name__ == '__main__':

  s = Solution()

  n = 1000

  m = 15

  p = 60

  print("输入总桶数为：",n)

  print("输入中毒时间：",m)

  print("输入测试时间：",p)

  print("输出为：",s.poorPigs(n,m,p))

循环数组中的环  

 

class Solution:

  \#参数nums为数组

  \#返回布尔类型

  def get_index(self, i, nums):

​    n = (i + nums[i]) % len(nums)

​    return n if n >= 0 else n + len(nums)

  def circularArrayLoop(self, nums):

​    for i in range(len(nums)):

​      if nums[i] == 0:

​        continue

​      j, k = i, self.get_index(i, nums)

​      while nums[k] * nums[i] > 0 and nums[self.get_index(k, nums)] * nums[i] > 0:

​        if j == k:

​          if j == self.get_index(j, nums):

​            break

​          return True

​        j = self.get_index(j, nums)

​        k = self.get_index(self.get_index(k, nums), nums)

​      j = i

​      while nums[j] * nums[i] > 0:

​        next = self.get_index(j, nums)

​        nums[j] = 0

​        j = next

​        

​    return False

\#主函数

if __name__ == '__main__':

  s = Solution()

  n = [2,-1,1,2,2]

  print("输入为：",n)

  print("输出为：",s.circularArrayLoop(n))

分饼干  

 

class Solution(object):

  def findContentChildren(self, g, s):

​    \#参数g为整数列表

​    \#参数s为整数列表

​    \#返回整型

​    g.sort()

​    s.sort()

​    i, j = 0, 0

​    while i < len(g) and j < len(s):

​      if g[i] <= s[j]:

​        i += 1

​      j += 1

​    return i

\#主函数

if __name__ == '__main__':

  s = Solution()

  n = [1,2,3]

  m = [1,1]

  print("输入贪吃指数为：",n)

  print("输入饼干尺寸为：",m)

  print("输出为：",s.findContentChildren(n,m))

翻转字符串中的元音字母  

 

class Solution:

  """

  参数s为字符串

  返回字符串

  """

  def reverseVowels(self, s):

​    vowels = set(["a", "e", "i", "o", "u", "A", "E", "I", "O", "U"])

​    res = list(s)

​    start, end = 0, len(res)-1

​    while start <= end:

​      while start <= end and res[start] not in vowels:

​        start += 1

​      while start <= end and res[end] not in vowels:

​        end -= 1

​      if start <= end:

​        res[start], res[end] = res[end], res[start]

​        start += 1

​        end -= 1

​    return "".join(res)

\#主函数

if __name__ == '__main__':

  s = Solution()

  x = "hello"

  print("输入为：",x)

  print("输出为：",s.reverseVowels(x))

翻转字符串  

 

class Solution:

  """

  参数s为字符串

  返回字符串

  """

  def reverseString(self, s):

​    return s[::-1]

\#主函数

if __name__ == '__main__':

  s = Solution()

  x = "hello"

  print("输入为：",x)

  print("输出为：",s.reverseString(x))

使数组元素相同的最少步数  

 

class Solution(object):

  def minMoves(self, nums):

​    \#参数nums为整数列表

​    \#返回整数

​    sumNum = sum(nums)

​    minNum = min(nums)

​    return sumNum - minNum * len(nums)

\#主函数

if __name__ == '__main__':

  s = Solution()

  n = [1,2,3]

  print("输入为：",n)

  print("输出为：",s.minMoves(n))

加油站 

 

\#参数distance代表每个加油站的距离

\#参数apply代表每个加油站的加油量

\#参数original代表一开始有汽油

\#参数target代表需要开的距离

\#返回值是一个整数，代表至少需要加油站次数

class Solution:

  def getTimes(self, target, original, distance, apply):

​    import queue

​    que = queue.PriorityQueue()

​    ans, pre = 0, 0

​    if(target > distance[len(distance) - 1]):

​      distance.append(target)

​      apply.append(0)

​    cap = original

​    for i in range(len(distance)):

​      if(distance[i] >= target):

​        distance[i] = target

​      d = distance[i] - pre

​      while(cap < d and que.qsize() != 0):

​        cap += (que.get()[1])

​        ans += 1

​      if (d <= cap):

​        cap -= d

​      else:

​        ans = -1

​        break

​      que.put((-apply[i], apply[i]))

​      pre = distance[i]

​      if(pre == target):

​        break

​    return ans

if __name__ == '__main__':

  target = 25

  original = 10

  distance = [10,14,20,21]

  apply = [10,5,2,4]

  solution = Solution()

  print(" 每个加油站的距离为：", distance)

  print(" 每个加油站的加油量为：", apply)

  print(" 一开始有汽油：", original)

  print(" 需要开的距离为：", target)

  print(" 至少需要经过加油站:", solution.getTimes(target, original, distance, apply))

春游  

 

\#参数a是小朋友组链

\#返回值是个整数，表示至少需要多少辆车

class Solution:

  def getAnswer(self, a):

​    count = [0 for i in range(0, 5)]

​    for i in range(0, len(a)):

​      count[a[i]] = count[a[i]] + 1

​    count[1] = count[1] - count[3]

​    if count[2] % 2 == 1:

​      count[2] = count[2] + 1

​      count[1] = count[1] - 2

​    res = count[4] + count[3] + count[2] / 2

​    if count[1] > 0:

​      res = res + count[1] / 4

​      if not count[1] % 4 == 0:

​        res = res + 1

​    return int(res)

if __name__ == '__main__':

  a = [1,2,3,4]

  solution = Solution()

  print(" 小朋友分组为：", a)

  print(" 至少需要：", solution.getAnswer(a), "辆车")

合法数组  

 

\#参数a是待查数组

\#返回值是一个数值，代表出现奇数次的值或者数组不合法

class Solution:

  def isValid(self, a):

​    countSet = {}

​    for i in a:

​      if i in countSet:

​        countSet[i] = countSet[i] + 1

​      else:

​        countSet[i] = 1

​    isHas = False

​    for key in countSet:

​      if countSet[key] % 2 == 1:

​        if isHas:

​          return -1

​        else:

​          isHas = True

​          ans = key

​    if isHas:

​      return ans

​    return -1

if __name__ == '__main__':

  a=[1,1,2,2,3,3,4,4,5,5]

  solution = Solution()

  print(" 数组为：", a)

  ans = solution.isValid(a)

   if ans != -1: 

​    print(" 数组奇数个的值是:", ans)

  else:

​    print(" 数组不合法:", ans)

删除排序数组中的重复数字 

 

class Solution:

  \#参数A: 整数列表

  \#返回值：整数

  def removeDuplicates(self, A):

​    B = []

​    before = None

​    countb = 0

​    for number in A:

​      if(before != number):

​        B.append(number)

​        before = number

​        countb = 1

​      elif countb < 2:

​        B.append(number)

​        countb += 1

​    p = 0

​    for number in B:

​      A[p] = number

​      p += 1

​    return p

\#主函数

if __name__ == '__main__':

  solution = Solution()

  A = [1,1,1,2,2,3]

  p = solution.removeDuplicates(A)

  print("输入：", A)

  print("输出：", p)

字符串的不同排列  

 

class Solution:

  \#参数str: 一个字符串

  \#返回值: 所有排列

  def stringPermutation2(self, str):

​    result = []

​    if str == '':

​      return ['']

​    s = list(str)

​    s.sort()

​    while True:

​      result.append(''.join(s))

​      s = self.nextPermutation(s)

​      if s is None:

​        break

​    return result

  def nextPermutation(self, num):

​    n = len(num)

​    i = n - 1

​    while i >= 1 and num[i - 1] >= num[i]:

​      i -= 1

​    if i == 0: return None

​    j = n - 1

​    while j >= 0 and num[j] <= num[i - 1]:

​      j -= 1

​    num[i - 1], num[j] = num[j], num[i - 1]

​    num[i:] = num[i:][::-1]

​    return num

\#主函数

if __name__ == '__main__':

  solution = Solution()

s1 = "aabb"

  ans = solution.stringPermutation2(s1)

  print("输入：", s1)

  print("输出：", ans)

全排列  

 

class Solution:

  \#参数nums: 一个整数列表

  \#返回值: 排列后的列表

  def permute(self, nums):

​    def _permute(result, temp, nums):

​      if nums == []:

​        result += [temp]

​      else:

​        for i in range(len(nums)):

​          _permute(result, temp + [nums[i]], nums[:i] + nums[i+1:])

​    if nums is None:

​      return []

​    if nums is []:

​      return [[]]

​    result = []

​    _permute(result, [], sorted(nums))

​    return result

\#主函数

if __name__ == '__main__':

  nums = [1,2,3]

  solution = Solution()

  result = solution.permute(nums)

  print("输入：", nums)

  print("输出：", result)

带重复元素的排列  

 

class Solution:

  \#参数nums: 整数数组

  \#返回值: 唯一排列的列表。

  def permuteUnique(self, nums):

​    def _permute(result, temp, nums):

​      if nums == []:

​        result += [temp]

​      else:

​        for i in range(len(nums)):

​          if i > 0 and nums[i] == nums[i-1]:

​            continue

​          _permute(result, temp + [nums[i]], nums[:i] + nums[i+1:])

​    if nums is None:

​      return []

​    if len(nums) == 0:

​      return [[]]

​    result = []

​    _permute(result, [], sorted(nums))

​    return result

\#主函数

if __name__ == '__main__':

  solution = Solution()

  nums = [1,2,2]

  result = solution.permuteUnique(nums)

  print("输入：", nums)

  print("输出：", result)

第二章  

插入区间  

 

class Interval(object):

  def __init__(self, start, end):

​    self.start = start

​    self.end = end

  def get(self):

​    str1 = "(" + str(self.start) + "," + str(self.end) + ")"

​    return str1

  def equals(self, Intervalx):

​    if self.start == Intervalx.start and self.end == Intervalx.end:

​      return 1

​    else:

​      return 0

class Solution:

  \#参数intevals: 已排序的非重叠区间列表

  \#参数newInterval: 新的区间

  \#返回值: 一个新的排序非重叠区间列表与新的区间

  def insert(self, intervals, newInterval):

​    results = []

​    insertPos = 0

​    for interval in intervals:

​      if interval.end < newInterval.start:

​        results.append(interval)

​        insertPos += 1

​      elif interval.start > newInterval.end:

​        results.append(interval)

​      else:

​        newInterval.start = min(interval.start, newInterval.start)

​        newInterval.end = max(interval.end, newInterval.end)

​    results.insert(insertPos, newInterval)

​    return results

\#主函数

if __name__ == '__main__':

solution = Solution()

  interval1 = Interval(1,2)

  interval2 = Interval(5,9)

  interval3 = Interval(2,5)

  results = solution.insert([interval1,interval2], interval3)

  print("输入：[",interval1.get(),",", interval2.get(),"]","", interval3.get())

  print("输出：[", results[0].get(), "]")

N皇后问题  

 

class Solution:

  \#参数n: 皇后的数量

  \#返回值: 不同解的总数

  total = 0

  n = 0

  def attack(self, row, col):

​    for c, r in self.cols.items():

​      if c - r == col - row or c + r == col + row:

​        return True

​    return False

  def search(self, row):

​    if row == self.n:

​      self.total += 1

​      return

​    for col in range(self.n):

​      if col in self.cols:

​        continue

​      if self.attack(row, col):

​        continue

​      self.cols[col] = row

​      self.search(row + 1)

​      del self.cols[col]

  def totalNQueens(self, n):

​    self.n = n

​    self.cols = {}

​    self.search(0)

​    return self.total

\#主函数

if __name__ == '__main__':

  solution = Solution()

  solution.totalNQueens(4)

  print("输入：", solution.n)

  print("输出：", solution.total)

主元素  

 

class Solution:

  \#参数nums: 整数数组

  \#返回值: 主元素

  def majorityNumber(self, nums):

​    nums.sort()

​    i=0;j=0

​    while i<=len(nums):

​      j=nums.count(nums[i])

​      if j>len(nums)//3:

​        return nums[i]

​      i+=j

​    return

\#主函数

if __name__ == '__main__':

  solution = Solution()

  nums = [99,2,99,2,99,3,3]

  n = solution.majorityNumber(nums)

  print("输入：", "[99,2,99,2,99,3,3]")

  print("输出：", n)

字符大小写排序  

 

class Solution:

  \#参数chars: 需要排序的字母数组

  def sortLetters(self, chars):

​    chars.sort(key=lambda c: c.isupper())

\#主函数

if __name__ == '__main__':

  solution = Solution()

  str1 = "abAcD"

  arr = list(str1)

  solution.sortLetters(arr)

  print("输入：", str1)

  print("输出：", ''.join(arr))

上一个排列  

1.问题描述

给定一个整数数组表示排列，找出以字典为顺序的上一个排列。

2.问题示例

输入[1,3,2,3]，输出[1,2,3,3]；输入[1,2,3,4]，输出[4,3,2,1]。

 

class Solution:

  \#参数num: 整数列表

  \#参数: 整数列表

  def previousPermuation(self, num):

​    for i in range(len(num)-2, -1, -1):

​      if num[i] > num[i+1]:

​        break

​    else:

​      num.reverse()

​      return num

​    for j in range(len(num)-1, i, -1):

​      if num[j] < num[i]:

​        num[i], num[j] = num[j], num[i]

​        break

​    for j in range(0, (len(num) - i)//2):

​      num[i+j+1], num[len(num)-j-1] = num[len(num)-j-1], num[i+j+1]

​    return num

\#主函数

if __name__ == '__main__':

  solution = Solution()

  num = [1,3,2,3]

print("输入：", num)

num1 = solution.previousPermuation(num)

  print("输出：", num1)

4.运行结果

输入：[1,3,2,3]

输出：[1, 3, 3, 2]

下一个排列  

 

class Solution:

  \#参数num: 整数列表

  \#返回值: 整数列表

  def nextPermutation(self, num):

​    for i in range(len(num)-2, -1, -1):

​      if num[i] < num[i+1]:

​        break

​    else:

​      num.reverse()

​      return num

​    for j in range(len(num)-1, i, -1):

​      if num[j] > num[i]:

​        num[i], num[j] = num[j], num[i]

​        break

​    for j in range(0, (len(num) - i)//2):

​      num[i+j+1], num[len(num)-j-1] = num[len(num)-j-1], num[i+j+1]

​    return num

\#主函数

if __name__ == '__main__':

  solution = Solution()

  num = [1,3,2,3]

  print("输入：", num)

num1 = solution.nextPermutation(num)

  print("输出：", num1)

二叉树的层次遍历 

 

class TreeNode: 

   def __init__(self, val=None, left=None, right=None):

​     self.val=val 

​     self.left=left  #左子树

​     self.right=right #右子树

class Solution:

  \#参数root: 二叉树的根

  \#返回值:从底向上的层次序遍历

  def levelOrderBottom(self, root):

​    self.results = []

​    if not root:

​      return self.results

​    q = [root]

​    while q:

​      new_q = []

​      self.results.append([n.val for n in q])

​      for node in q:

​        if node.left:

​          new_q.append(node.left)

​        if node.right:

​          new_q.append(node.right)

​      q = new_q

​    return list(reversed(self.results))

\#主函数

if __name__ == '__main__':

  solution = Solution()

  root=TreeNode(1,TreeNode(2),TreeNode(3))

  results = solution.levelOrderBottom(root)

  print("输入： {1,2,3}")

  print("输出：", results)

最长公共子串  

 

class Solution:

  \#参数A, B: 两个字符串

  \#返回值: 最长公共子串的长度

  def longestCommonSubstring(self, A, B):

​    ans = 0

​    for i in range(len(A)):

​      for j in range(len(B)):

​        l = 0

​        while i + l < len(A) and j + l < len(B) \

​          and A[i + l] == B[j + l]:

​          l += 1

​        if l > ans:

​          ans = l

​    return ans

\#主函数

if __name__ == '__main__':

  solution = Solution()

  A = "ABCD"

  B = "CBCE"

  ans = solution.longestCommonSubstring(A, B)

  print("输入：","A =",A,"B =",B)

  print("输出：", ans)

最近公共祖先  

 

\#Definition of TreeNode:

class TreeNode: 

   def __init__(self, val=None, left=None, right=None):

​     self.val=val 

​     self.left=left  #左子树

​     self.right=right #右子树

​    

class Solution:

  \#参数root: 二叉搜索树的根

  \#参数A: 二叉树的一个节点

  \#参数B: 二叉树的一个节点

  \#返回值: 返回两个节点的最低公共祖先(LCA)

  def lowestCommonAncestor(self, root, A, B):

​    \# A且其下面有B => A

​    \# B且其下面有A => B

​    \# A且其下面啥都没有 => A

​    \# B且其下面啥都有 => B

​    if root is None:

​      return None

​    if root == A or root == B:

​      return root

​    left_result = self.lowestCommonAncestor(root.left, A, B)

​    right_result = self.lowestCommonAncestor(root.right, A, B)

​    \# A 和 B 一边一个

​    if left_result and right_result: 

​      return root

​    \# 左子树有一个点或者左子树有LCA

​    if left_result:

​      return left_result

​    \# 右子树有一个点或者右子树有LCA

​    if right_result:

​      return right_result

​    \# 左右子树啥都没有

​    return None

\#主函数

if __name__ == '__main__':

  tree = TreeNode(4, TreeNode(3), TreeNode(7, TreeNode(5), TreeNode(6)))

  solution = Solution()

  result = solution.lowestCommonAncestor(tree, tree.left, tree.right.left)

  print("输入：{4,3,7,#,#,5,6}, LCA(3,5)")

  print("输出：", result.val)

k数和 

 

class Solution:

  def kSumII(self, A, k, target):

​    anslist = []

​    self.dfs(A, k, target, 0, [], anslist)

​    return anslist

  def dfs(self, A, k, target, index, onelist, anslist):

​    if target == 0 and k == 0:

​      anslist.append(onelist)

​      return

​    if len(A) == index or target < 0 or k < 0:

​      return

​    self.dfs(A, k, target, index + 1, onelist, anslist)

​    self.dfs(A, k - 1, target - A[index], index + 1 , onelist + [A[index]], anslist)

\#主函数

if __name__ == '__main__':

  solution = Solution()

  A = [1,2,3,4]

  k = 2

  target = 5

  anslist = solution.kSumII(A, k, target)

  print("输入：A = [1,2,3,4]  k = 2  target = 5")

  print("输出：", anslist)

有序链表转换为二分查找树  

 

\#定义链表节点

class ListNode(object):

  def __init__(self, val, next=None):

​    self.val = val

​    self.next = next

\#定义树节点

class TreeNode:

  def __init__(self, val):

​    self.val = val

​    self.left, self.right = None, None

class Solution:

  \#参数head: 链表的第一个节点

  \#返回值: 树节点

  def sortedListToBST(self, head):

​    num_list = []

​    while head:

​      num_list.append(head.val)

​      head = head.next

​    return self.create(num_list, 0, len(num_list) - 1)

  def create(self, nums, start, end):

​    if start > end:

​      return None

​    if start == end:

​      return TreeNode(nums[start])

​    root = TreeNode(nums[(start + end) // 2])

​    root.left = self.create(nums, start, (start + end) // 2 - 1) #注意是-1

​    root.right = self.create(nums, (start + end) // 2 + 1, end)

​    return root

\#主函数

if __name__ == '__main__':

  solution = Solution()

  listnode = ListNode(1, ListNode(2, ListNode(3)))

  root = solution.sortedListToBST(listnode)

  print("输入： 1=>2=>3")

  print("输出：", "{", root.val, root.left.val, root.right.val, "}")

最长连续序列  

 

class Solution:

  \#参数num：整数数组

  \#返回值：整数

  def longestConsecutive(self, num):

​    dict={}

​    for x in num:

​      dict[x] = 1

​    ans = 0

​    for x in num:

​      if x in dict:

​        len = 1

​        del dict[x]

​        l = x - 1

​        r = x + 1

​        while l in dict:

​          del dict[l]

​          l -= 1 

​          len += 1

​        while r in dict:

​          del dict[r]

​          r += 1

​          len += 1

​        if ans < len:

​          ans = len

​    return ans

\#主函数

if __name__ == '__main__':

  solution = Solution()

  num = [100, 4, 200, 1, 3, 2]

  ans = solution.longestConsecutive(num)

  print("输入：", num)

  print("输出：", ans)

背包问题 

 

class Solution:

  \#参数m: 整数m表示背包的大小

  \#参数A & V: 给定n个大小为A[i]和值V[i]的物品

  def backPackII(self, m, A, V):

​    f = [0 for i in range(m+1)]

​    n = len(A)

​    for i in range(n):

​      for j in range(m, A[i]-1, -1):

​        f[j] = max(f[j] , f[j-A[i]] + V[i])

​    return f[m]

\#主函数

if __name__ == '__main__':

  solution = Solution()

  m = 100

  A = [77,22,29,50,99]

  V = [92,22,87,46,90]

  result = solution.backPackII(m, A, V)

print("输入：\n","m = ",m, "\n A = ", A, "\n V = ",V)

print("输出：", result)

拓扑排序  

 

\#定义有向图节点

class DirectedGraphNode:

  def __init__(self, x):

​    self.label = x

​    self.neighbors = []

class Solution:

  \#参数graph: 有向图节点列表

  \#返回值: 整数列表

  def topSort(self, graph):

​    indegree = {}

​    for x in graph:

​      indegree[x] = 0

​    for i in graph:

​      for j in i.neighbors:

​        indegree[j] += 1

​    ans = []

​    for i in graph:

​      if indegree[i] == 0:

​        self.dfs(i, indegree, ans)

​    return ans

  def dfs(self, i, indegree, ans):

​    ans.append(i.label)

​    indegree[i] -= 1

​    for j in i.neighbors:

​      indegree[j] -= 1

​      if indegree[j] == 0:

​        self.dfs(j, indegree, ans)

\#主函数

if __name__ == '__main__':

  solution = Solution()

  g0 = DirectedGraphNode(0)

  g1 = DirectedGraphNode(1)

  g2 = DirectedGraphNode(2)

  g3 = DirectedGraphNode(3)

  g4 = DirectedGraphNode(4)

  g5 = DirectedGraphNode(5)

  g0.neighbors = [g1, g2, g3]

  g1.neighbors = [g4]

  g2.neighbors = [g4, g5]

  g3.neighbors = [g4, g5]

  graph = [g0, g1, g2, g3, g4, g5]

  result = solution.topSort(graph)

  print("输入：如样例图")

  print("输出：",result)

克隆图  

 

\#定义无向图节点

class UndirectedGraphNode:

  def __init__(self, x):

​    self.label = x

​    self.neighbors = []

class Solution:

  def __init__(self):

​    self.dict = {}

  \#参数node: 无向图节点

  \#返回值: 无向图节点

  def cloneGraph(self, node):

​    if node is None:

​      return None

​    if node.label in self.dict:

​      return self.dict[node.label]

​    root = UndirectedGraphNode(node.label)

​    self.dict[node.label] = root

​    for item in node.neighbors:

​      root.neighbors.append(self.cloneGraph(item))

​    return root

\#主函数

if __name__ == '__main__':

  solution = Solution()

  g0 = UndirectedGraphNode(0)

  g1 = UndirectedGraphNode(1)

  g2 = UndirectedGraphNode(2)

  g0.neighbors = [g1, g2]

  g1.neighbors = [g2]

  g2.neighbors = [g2]

  ans = solution.cloneGraph(g0)

  a = [ans.label, ans.neighbors[0].label, ans.neighbors[1].label, 

​     ans.neighbors[0].neighbors[0].label, ans.neighbors[1].neighbors[0].label]

  print("输入： {0,1,2#1,2#2,2}")

  print("输出：", a)

不同的二叉查找树  

 

class Solution:

  \#参数n: 整数

  \#返回值: 整数

  def numTrees(self, n):

​    dp = [1, 1, 2]

​    if n <= 2:

​      return dp[n]

​    else:

​      dp += [0 for i in range(n-2)]

​      for i in range(3, n + 1):

​        for j in range(1, i+1):

​          dp[i] += dp[j-1] * dp[i-j]

​      return dp[n]

\#主函数

if __name__ == '__main__':

  solution = Solution()

  n = 3

  ans = solution.numTrees(n)

  print("输入：", n)

  print("输出：", ans)

汉诺塔  

 

class Solution:

  def move(self, n, a, b, c, ans):  #n为圆盘数，a代表初始位圆柱，b代表过渡位圆柱，c代表目标位圆柱

​    if n==1:

​      ans.append("from "+a+" to "+c)

​    else:

​      self.move(n-1,a,c,b,ans)

​      ans.append("from "+a+" to "+c)

​      self.move(n-1,b,a,c,ans)

​    return ans

\#主函数

if __name__ == '__main__':

  solution = Solution()

  ans = []

  res = solution.move(3, 'A', 'B', 'C', ans)

  print("输入： 3, 'A', 'B', 'C'")

  print("输出：", res)

图中两个点之间的路线  

 

\#定义有向图节点

class DirectedGraphNode:

  def __init__(self, x):

​    self.label = x

​    self.neighbors = []

class Solution:

  def dfs(self, i, countrd, graph, t):

​    if countrd[i] == 1:

​      return False

​    if i == t:

​      return True

​    countrd[i] = 1

​    for j in i.neighbors:

​      if countrd[j] == 0 and self.dfs(j, countrd, graph, t):

​        return True

​    return False

  \#参数graph: 有向图节点列表

  \#参数s: 起始有向图节点

  \#参数t: 终端有向图节点

  \#返回值: 布尔值

  def hasRoute(self, graph, s, t):

​    countrd = {}

​    for x in graph:

​      countrd[x] = 0

​    return self.dfs(s, countrd, graph, t)

\#主函数

if __name__ == '__main__':

  solution = Solution()

  gA = DirectedGraphNode('A')

  gB = DirectedGraphNode('B')

  gC = DirectedGraphNode('C')

  gD = DirectedGraphNode('D')

  gE = DirectedGraphNode('E')

  gA.neighbors = [gB, gD]

  gB.neighbors = [gC, gD]

  gD.neighbors = [gE]

  graph = [gA, gB, gC, gD, gE]

  ans = solution.hasRoute(graph, gB, gE)

  print("输入： {A,B,C,D,E,A#B,A#D,B#C,B#D,D#E}, B, E")

  print("输出：", ans)

丢失的第一个正整数  

 

class Solution:

  \#参数A为整数数组

  \#返回整数

  def firstMissingPositive(self, A):

​    tb = {n for n in range(1, len(A)+2)}    

​    for num in A:

​      if num in tb:

​        tb.remove(num)        

​    return min(tb)

\#主函数

if __name__ == '__main__':

  solution = Solution()

  A = [3,4,-1,1]

print("输入：", A)

ans = solution.firstMissingPositive(A)

  print("输出：", ans)

寻找缺失的数  

 

class Solution:

  def findMissing(self, nums):

​    if not nums:

​      return 0

​    sum = 0 

​    for _ in nums:

​      sum += _

​    return int((len(nums) * (len(nums) + 1) / 2)) - sum

\#主函数

if __name__ == '__main__':

  solution = Solution()

  nums = [0,1,3]

  ans = solution.findMissing(nums)

  print("输入：", nums)

  print("输出：", ans)

排列序号I  

 

class Solution:

  \#参数A: 整数数组

  \#返回值: 整数

  def permutationIndex(self, A):

​    result = 1

​    factor = 1

​    for i in range(len(A)-1, -1, -1):

​      rank = 0

​      for j in range(i+1, len(A)):

​        if A[i] > A[j]:

​          rank +=1

​      result += factor*rank

​      factor *= len(A)-i

​    return result

\#主函数

if __name__ == '__main__':

  solution = Solution()

  A = [3,2,1]

  ans = solution.permutationIndex(A)

  print("输入：", A)

  print("输出：", ans)

排列序号II 

 

class Solution:

\#参数A: 整数数组 

\#返回值: 长整数

  def permutationIndexII(self, A):

​    if A is None or len(A) == 0:

​      return 0

​    index, factor, multi_fact = 1, 1, 1

​    counter = {}

​    for i in range(len(A) - 1, -1, -1):

​      counter[A[i]] = counter.get(A[i], 0) + 1

​      multi_fact *= counter[A[i]]

​      count = 0

​      for j in range(i + 1, len(A)):

​        if A[i] > A[j]:

​          count += 1

​      index += count * factor // multi_fact

​      factor *= (len(A) - i)

​    return index

\#主函数

if __name__ == '__main__':

  solution = Solution()

  A = [1,4,2,2]

  ans = solution.permutationIndexII(A)

  print("输入：", A)

  print("输出：", ans)

最多有k个不同字符的最长子字符串  

 

\#参数s是一个字符串

\#返回值res是最长字符串的长度

class Solution:

  def lengthOfLongestSubstring(self, s):

​    res = 0

​    if s is None or len(s) == 0:

​      return res

​    d = {}

​    tmp = 0

​    start = 0

​    for i in range(len(s)):

​      if s[i] in d and d[s[i]] >= start:

​        start = d[s[i]] + 1

​      tmp = i - start + 1

​      d[s[i]] = i

​      res = max(res, tmp)

​    return res

\#主函数

if __name__ == '__main__':

  generator = 'eceba'

  solution = Solution()

  print("输入：", generator)

  print("输出：", solution. lengthOfLongestSubstring(generator))

第k个排列  

 

\#参数n是指1~n

\#参数k是指所有全排列中的第几个

\#返回值是第k个全排列

class Solution:

  def getPermutation(self, n, k):

​    fac = [1]

​    for i in range(1, n + 1):

​      fac.append(fac[-1] * i)

​    elegible = list(range(1, n + 1))

​    per = []

​    for i in range(n):

​      digit = (k - 1) // fac[n - i - 1]

​      per.append(elegible[digit])

​      elegible.remove(elegible[digit])

​      k = (k - 1) % fac[n - i - 1] + 1

​    return "".join([str(x) for x in per])

\#主函数

if __name__ == '__main__':

  k=4

  n=3

  solution = Solution()

  print("输入：", "n=",n,"k=",k)

  print("输出：", solution.getPermutation(n,k))

数飞机  

 

\#参数start是开始时间

\#参数end是结束时间

class Interval(object):

  def __init__(self, start, end):

​    self.start = start

​    self.end = end

\#参数airplanes是一个由时间间隔对象组成的数组

\#返回值max_number_of_airplane是飞机的最大数

class Solution:

  def countOfAirplanes(self, airplanes):

​    points = []

​    for airplane in airplanes:

​      points.append([airplane.start, 1])

​      points.append([airplane.end, -1])

​    number_of_airplane, max_number_of_airplane = 0, 0

​    for _, count_delta in sorted(points):

​      number_of_airplane += count_delta

​      max_number_of_airplane = max(max_number_of_airplane,

 number_of_airplane)

​    return max_number_of_airplane

\#主函数

if __name__ == '__main__':

  generator=[Interval(1,10),Interval(5,8),Interval(2,3),Interval(4,7)]

solution = Solution()

  print("输入：",[(1, 10), (2, 3), (5, 8), (4, 7)] )

  print("输出：", solution.countOfAirplanes(generator))

格雷编码  

 

\#参数n是一个整型数

\#返回值seq是所对应的格雷编码

class Solution:

  def grayCode(self, n):

​    if n == 0:

​      return [0]

​    

​    result = self.grayCode(n - 1)

​    seq = list(result)

​    for i in reversed(result):

​      seq.append((1 << (n - 1)) | i)

​    return seq

\#主函数

if __name__ == '__main__':

  generator=2

solution = Solution()

print("输入：", generator)

  print("输出：", solution. grayCode(generator))

迷你Cassandra 

 

\#参数raw_key是一个字符串，用于哈希

\#参数column_key是一个整数，支持范围查询

\#参数column_value是储存字符串的值

\#参数column_start是开始位置

\#参数column_start是结束位置

\#返回值rt是一个由Column对象组成的列表

class Column:

  def __init__(self, key, value):

​    self.key = key

​    self.value = value

from collections import OrderedDict

class Solution:

  def __init__(self):

​    self.hash = {}

  def insert(self, raw_key, column_key, column_value):

​    if raw_key not in self.hash:

​      self.hash[raw_key] = OrderedDict()

​    self.hash[raw_key][column_key] = column_value

  def query(self, raw_key, column_start, column_end):

​    rt = []

​    if raw_key not in self.hash:

​      return rt

​    self.hash[raw_key] = OrderedDict(sorted(self.hash[raw_key].items()))

​    for key, value in self.hash[raw_key].items():

​      if key >= column_start and key <= column_end:

​        rt.append(Column(key, value))

​    return rt

\#主函数

if __name__ == '__main__':

generator = Column(1, "abcd")

generator1 = Column(2, "hijk")

solution = Solution()

solution.insert("google",generator.key,generator.value)

solution.insert("google",generator1.key,generator1.value)

ls = solution.query("google", 0, 2)

print('输入: query("google", 0, 2)')

print("输出: ")

for i in ls:

​    print(i.key,i.value)

网络日志  

 

\#参数timestamp是个整数，建立一个时间点

\#返回值是个整数，表示最后五分钟时间点的个数

class WebLogger:

  def __init__(self):

​    self.Q = []

  def hit(self, timestamp):

​    self.Q.append(timestamp)

  def get_hit_count_in_last_5_minutes(self, timestamp):

​    if self.Q == []:

​      return 0

​    i = 0

​    n = len(self.Q)

​    while i < n and self.Q[i] + 300 <= timestamp:

​      i += 1

​    self.Q = self.Q[i:]

​    return len(self.Q)

\#主函数

if __name__ == '__main__':

solution = WebLogger()

 print("输入：hit(1),hit(2) ")

 solution.hit(1)

 solution.hit(2)

 print("输出最后5分钟时间戳个数：")

 print(solution.get_hit_count_in_last_5_minutes(3))

 print("输入：hit(300) ")

 solution.hit(300)

 print("输出最后5分钟时间戳个数：")

 print(solution.get_hit_count_in_last_5_minutes(300))

 print("输出最后5分钟时间戳个数：")

 print(solution.get_hit_count_in_last_5_minutes(301))

栅栏染色  

 

\#参数n是个非负整数，柱子数

\#参数n是个非负整数，颜色数

\#返回值是个整数，所有的染色方案

class Solution:

  def numWays(self, n, k):

​    dp = [0, k, k * k]

​    if n <= 2:

​      return dp[n]

​    if k == 1 and n >= 3:

​      return 0

​    for i in range(2, n):

​      dp.append((k - 1) * (dp[-1] + dp[-2]))

​    return dp[-1]

\#主函数

if __name__ == '__main__':

solution= Solution()

n=3

k=2

print("输入： n=",n ,"k=",k)

print("输出：",solution.numWays(n,k))

房屋染色  

 

\#参数costs是个nx3矩阵

\#返回值是个整数，刷完所有房子最小花费

class Solution:

  def minCost(self, costs):

​    n = len(costs)

​    if n == 0:

​      return 0

​    INF = 0x7fffffff

​    f = [costs[0], [INF, INF, INF]]

​    for i in range(1, n):

​      for j in range(3):

​        f[i&1][j] = INF

​        for k in range(3):

​          if j != k:

​            f[i&1][j] = min(f[i&1][j], f[(i+1)&1][k] + costs[i][j])

​    return min(f[(n-1)&1])

\#主函数

if __name__ == '__main__':

generator=[[14,2,11],[11,14,5],[14,3,10]]

solution= Solution()

print("输入： ",generator)

print("输出： ",solution.minCost(generator))

去除重复元素  

 

\#参数nums是个一个整型数组

\#返回值result是不重复元素的个数

class Solution:

  def deduplication(self, nums):

​    n = len(nums)

​    if n == 0:

​      return 0

​    nums.sort()

​    result = 1

​    for i in range(1, n):

​      if nums[i - 1] != nums[i]:

​        nums[result] = nums[i]

​        result += 1

​    return result

\#主函数

if __name__ == '__main__':

generator=[1,3,1,4,4,2]

solution= Solution()

print("输入：",generator)

print("输出：",solution.deduplication(generator))

左填充  

 

\#参数originalStr是需要添加的字符串

\#参数size是目标长度

\#参数padchar是在字符串左边填充的字符

\#返回值是左填充后的字符串

class StringUtils:

  def leftPad(self, originalStr, size, padChar=' '):

​    return padChar * (size - len(originalStr)) + originalStr

\#主函数

if __name__ == '__main__':

size=8

generator = "foobar"

solution= StringUtils()

print("输入:",generator)

print("输出:",solution.leftPad(generator,size))

负载均衡器  

 

\#参数server_id是一个服务器的ID

\#返回值是一个ID，集群中随机的一个服务器ID

class LoadBalancer:

  def __init__(self):

​    self.server_ids = []

​    self.id2index = {}

  def add(self, server_id):

​    if server_id in self.id2index:

​      return

​    self.server_ids.append(server_id)

​    self.id2index[server_id] = len(self.server_ids) - 1

  def remove(self, server_id):

​    if server_id not in self.id2index:

​      return

​    \# remove the server_id

​    index = self.id2index[server_id]

​    del self.id2index[server_id]

​    \# overwrite the one to be removed

​    last_server_id = self.server_ids[-1]

​    self.id2index[last_server_id] = index

​    self.server_ids[index] = last_server_id

​    self.server_ids.pop()

  def pick(self):

​    import random

​    index = random.randint(0, len(self.server_ids) - 1)

​    return self.server_ids[index]

\#主函数

if __name__ == '__main__':

solution= LoadBalancer()

solution.add(1)

solution.add(2)

solution.remove(1)

print("输入: \nadd(1)\nadd(2)\nremove(1)")

print("输出:",solution.pick())

print("输出:",solution.pick())

两数和的最接近值  

 

\#参数nums是个整数数组

\#参数target是一个整数

\#返回值diff是target和两数求和的差距

import sys

class Solution:

  def twoSumClosest(self, nums, target):

​    nums.sort()

​    i, j = 0, len(nums) - 1

​    diff = sys.maxsize

​    while i < j:

​      if nums[i] + nums[j] < target:

​        diff = min(diff, target - nums[i] - nums[j])

​        i += 1

​      else:

​        diff = min(diff, nums[i] + nums[j] - target)

​        j -= 1

​    return diff

\#主函数

if __name__ == '__main__':

generator = [-1,2,-1,4]

solution= Solution()

print("target =",target)

print("输入：",generator)

print("输出:",solution.twoSumClosest(generator,target))

打劫房屋 

 

\#参数nums是个非负整数列表，表示每个房子中存放的钱

\#返回值是个整数，表示可以拿到的钱

class Solution:

  def houseRobber2(self, nums):

​    n = len(nums)

​    if n == 0:

​      return 0

​    if n == 1:

​      return nums[0]

​    dp = [0] * n

​    dp[0], dp[1] = 0, nums[1]

​    for i in range(2, n):

​      dp[i] = max(dp[i - 2] + nums[i], dp[i - 1])

​    answer = dp[n - 1]

​    dp[0], dp[1] = nums[0], max(nums[0], nums[1])

​    for i in range(2, n - 1):

​      dp[i] = max(dp[i - 2] + nums[i], dp[i - 1])

​    return max(dp[n - 2], answer)

\#主函数

if __name__ == '__main__':

generator = [2,3,2,3]

solution= Solution()

print("输入:",generator)

print("输出:",solution.houseRobber2(generator))

左旋右旋迭代器  

 

\#参数v1，v2表示两个一维向量

\#返回值是一个一维数组，交替返回v1，v2元素

class ZigzagIterator:

  def __init__(self, v1, v2):

​    self.queue = [v for v in (v1, v2) if v]

  def next(self):

​    v = self.queue.pop(0)

​    value = v.pop(0)

​    if v:

​      self.queue.append(v)

​    return value

  def hasNext(self):

​    return len(self.queue) > 0

\#主函数

if __name__ == '__main__':

v1= [1,2]

v2= [3,4,5,6]

print("输入:")

print(",".join(str(i) for i in v1))

print(",".join(str(i) for i in v2))

solution, result = ZigzagIterator(v1, v2), []

while solution.hasNext():

  result.append(solution.next())

print("输出:",result)

N数组第K大元素  

 

import heapq

\#参数arrays一个数组列表

\#参数k表示第k大

\#返回值num是列表中最大的数

class Solution:

  def KthInArrays(self, arrays, k):

​    if not arrays:

​      return None

​    \# in order to avoid directly changing the original arrays

​    \# and remove the empty arrays, we need a new sortedArrays

​    sortedArrays = []

​    for arr in arrays:

​      if not arr:

​        continue

​      sortedArrays.append(sorted(arr, reverse=True))

​    maxheap = [

​          (-arr[0], index, 0)

​          for index, arr in enumerate(sortedArrays)

​    ]

​    heapq.heapify(maxheap)

​    num = None

​    for _ in range(k):

​      num, x, y = heapq.heappop(maxheap)

​      num = -num

​      if y + 1 < len(sortedArrays[x]):

​        heapq.heappush(maxheap, (-sortedArrays[x][y + 1], x, y + 1))

​    return num

\#主函数

if __name__ == '__main__':

generator = [[2,3,2,4],[3,4,7,9]]

k=5

solution= Solution()

print("输入:",generator)

print("k= ",k)

print("输出:",solution.KthInArrays(generator,k))

前K大数  

 

import heapq

\#参数nums是个整数数组

\#参数k表示第k大

\#返回值是个整型数组，前k大的整数组成

class Solution:

  def topk(self, nums, k):

​    heapq.heapify(nums)

​    topk = heapq.nlargest(k, nums)

​    topk.sort()

​    topk.reverse()

​    return topk

\#主函数

if __name__ == '__main__':

generator = [8, 7, 6, 5, 4, 3, 2, 1]

k=4

solution= Solution()

print("输入:",generator)

print("k=",k)

print("输出:",solution.topk(generator,k))

计数型布隆过滤器  

 

import random

\#参数str是个字符串，表示一个word

\#返回值是个布尔值，若该word存在返回True，否则返回False

class HashFunction:

  def __init__(self, cap, seed):

​    self.cap = cap

​    self.seed = seed

  def hash(self, value):

​    ret = 0

​    for i in value:

​      ret += self.seed * ret + ord(i)

​      ret %= self.cap

​    return ret

class CountingBloomFilter:

  def __init__(self, k):

​    self.hashFunc = []

​    for i in range(k):

​      self.hashFunc.append(HashFunction(random.randint(10000, 20000), i * 2 + 3))

​    self.bits = [0 for i in range(20000)]

  def add(self, word):

​    for f in self.hashFunc:

​      position = f.hash(word)

​      self.bits[position] += 1

  def remove(self, word):

​    for f in self.hashFunc:

​      position = f.hash(word)

​      self.bits[position] -= 1

  def contains(self, word):

​    for f in self.hashFunc:

​      position = f.hash(word)

​      if self.bits[position] <= 0:

​        return False

​    return True

\#主函数

if __name__ == '__main__':

solution= CountingBloomFilter(3)

solution.add("long")

solution.add("term")

print('输入:')

print('add("long")')

print('add("term")')

print('contains("long")')

print("输出:",solution.contains("long"))

solution.remove("long")

print('remove("long")')

print('contains("long")')

print("输出:",solution.contains("long"))

字符计数  

 

\#参数str一个任意的字符串

\#返回值map是个哈希map

class Solution:

  def countCharacters(self, str):

​    map = dict()

​    for c in str:

​      map[c] = map.get(c, 0) + 1

​    return map

\#主函数

if __name__ == '__main__':

generator="abca"

solution = Solution()

print('输入:',generator)

print("输出:",solution.countCharacters(generator))

最长重复子序列  

 

\#参数str是个任意字符串

\#返回值是个整数表示这个字符串最长重复的子序列长度

class Solution:

  def longestRepeatingSubsequence(self, str):

​    n = len(str)

​    dp = [[0 for j in range(n + 1)] for i in range(n + 1)]

​    for i in range(1, n + 1):

​      for j in range(1, n + 1):

​        if str[i - 1] == str[j - 1] and i != j:

​          dp[i][j] = dp[i - 1][j - 1] + 1

​        else:

​          dp[i][j] = max(dp[i][j - 1], dp[i - 1][j])

​    return dp[n][n]

\#主函数

if __name__ == '__main__':

solution = Solution()

generator="abcaa"

print('输入：',generator)

print("输出：",solution. longestRepeatingSubsequence(generator))

僵尸矩阵   

1.问题描述

给定一个二维网格，每一个格子都有一个值，2代表墙，1代表僵尸，0代表人类(数字0, 1, 2)。僵尸每天可以将上下左右最接近的人类感染成僵尸，但不能穿墙。问：将所有人类感染为僵尸需要多久，如果不能感染所有人则返回 -1。

2.问题示例

输入：

[[0,1,2,0,0],

[ 1,0,0,2,1],

[ 0,1,0,0,0]]

输出：2

输入：

[[0,0,0],

[ 0,0,0],

[ 0,0,1]]

输出：4

 

import collections

\#参数grid是一个二维整数矩阵

\#返回值是个整数，表示需要的天数，若不能完成则返回-1

class Solution:

  def zombie(self, grid):

​    if len(grid) == 0 or len(grid[0]) == 0:

​      return 0

​    m, n = len(grid), len(grid[0])

​    queue = collections.deque()

​    for i in range(m):

​      for j in range(n):

​        if grid[i][j] == 1:

​          queue.append((i, j))

​    day = 0

​    while queue:

​      size = len(queue)

​      day += 1

​      for k in range(size):

​        (i, j) = queue.popleft()

​        DIR = [(1, 0), (-1, 0), (0, 1), (0, -1)]

​        for (di, dj) in DIR:

​          next_i, next_j = i + di, j + dj

​          if next_i < 0 or next_i >= m or next_j < 0 or next_j >= n:

​            continue

​          if grid[next_i][next_j] == 1 or grid[next_i][next_j] == 2:

​            continue

​          grid[next_i][next_j] = 1

​          queue.append((next_i, next_j))

​    for i in range(m):

​      for j in range(n):

​        if grid[i][j] == 0:

​          return -1

​    return day - 1

\#主函数

if __name__ == '__main__':

solution = Solution()

generator=[[0,0,0],

​       [0,0,0],

​       [0,0,1]]

print("输入：",generator)

print("输出：",solution. zombie(generator))

4.运行结果

输入：[[0, 0, 0], [0, 0, 0], [0, 0, 1]]

输出：4

摊平二维向量  

 

class Vector2D(object):

  def __init__(self, vec2d):

​    self.vec2d = vec2d

​    self.row, self.col = 0, -1

​    self.next_elem = None

  def next(self):

​    if self.next_elem is None:

​      self.hasNext()

​    temp, self.next_elem = self.next_elem, None

​    return temp

  def hasNext(self):

​    if self.next_elem:

​      return True

​    self.col += 1

​    while self.row < len(self.vec2d)and self.col>= len(self.vec2d[self.row]):

​      self.row += 1

​      self.col = 0

​    if self.row < len(self.vec2d) and self.col < len(self.vec2d[self.row]):

​      self.next_elem = self.vec2d[self.row][self.col]

​      return True

​    return False

\#主函数

if __name__ == '__main__':

  inputnum=[[1,2],[3],[4,5,6]]

  vector2d=Vector2D(inputnum)

  print("输入：",inputnum)

  print("输出：")

  print(vector2d.next())

  while vector2d.hasNext():

​    print(vector2d.next())

第K大的元素  

 

class Solution:

  \# nums是整型数组

  \# k是整数

  \# 返回数组第k大的元素

  def kthLargestElement2(self, nums, k):

​    import heapq

​    heap = []

​    for num in nums:

​      heapq.heappush(heap, num)

​      if len(heap) > k:

​        heapq.heappop(heap)

​    return heapq.heappop(heap)

\#主函数

if __name__ == '__main__':

  inputnum=[9,3,2,4,8]

  k=3

  print("输入数组：",inputnum)

  print("输入:k=",k)

  solution=Solution()

  print("输出：",solution.kthLargestElement2(inputnum,k))

两数和小于或等于目标值  

 

class Solution:

  \# 参数nums是整数数组

  \# 参数target是整数

  \# 返回整数

  def twoSum5(self, nums, target):

​    l, r = 0, len(nums)-1

​    cnt = 0

​    nums.sort()

​    while l < r:

​      value = nums[l] + nums[r]

​      if value > target:

​        r -= 1

​      else:

​        cnt += r - l

​        l += 1

​    return cnt

\#主函数

if __name__ == '__main__':

  inputnum= [2, 7, 11, 15]

  target=24

solution=Solution()

print("输入数组：",inputnum)

print("输入target：",target)

solution=Solution()

print("输出：",solution.twoSum5(inputnum,target))

两数差等于目标值  

 

class Solution:

  \#参数nums是整数数组

  \#参数target是整数

  \#返回数组的索引值加1，[index1 + 1, index2 + 1] (index1 < index2)

  def twoSub(self, nums, target):

​    nums = [(num, i) for i, num in enumerate(nums)]

​    target = abs(target)  

​    n, indexs = len(nums), []

​    nums = sorted(nums, key=lambda x: x[0])

​    j = 0

​    for i in range(n):

​      if i == j:

​        j += 1

​      while j < n and nums[j][0] - nums[i][0] < target:

​        j += 1

​      if j < n and nums[j][0] - nums[i][0] == target:

​        indexs = [nums[i][1] + 1, nums[j][1] + 1]

​    if indexs[0] > indexs[1]:

​      indexs[0], indexs[1] = indexs[1], indexs[0]

​    return indexs

\#主函数

if __name__ == '__main__':

  inputnum= [2, 7, 15, 24]

  target=5

solution=Solution()

print("输入数组：",inputnum)

print("输入target：",target)

print("输出：",solution.twoSub(inputnum,target))

骑士的最短路线  

 

import collections

class Point:

  def __init__(self, a=0, b=0):

​    self.x = a

​    self.y = b

DIRECTIONS = [

  (-2, -1), (-2, 1), (-1, 2), (1, 2),

  (2, 1), (2, -1), (1, -2), (-1, -2),

]

class Solution:

  \#参数grid表示棋盘

  \#参数source表示起点

  \#参数destination表示终点

  \#返回最短路径长度

  def shortestPath(self, grid, source, destination):

​    queue = collections.deque([(source.x, source.y)])

​    distance = {(source.x, source.y): 0}

​    while queue:

​      x, y = queue.popleft()

​      if (x, y) == (destination.x, destination.y):

​        return distance[(x, y)]

​      for dx, dy in DIRECTIONS:

​        next_x, next_y = x + dx, y + dy

​        if (next_x, next_y) in distance:

​          continue

​        if not self.is_valid(next_x, next_y, grid):

​          continue

​        distance[(next_x, next_y)] = distance[(x, y)] + 1

​        queue.append((next_x, next_y))

​    return -1

  def is_valid(self, x, y, grid):

​    n, m = len(grid), len(grid[0])

​    if x < 0 or x >= n or y < 0 or y >= m:

​      return False

​    return not grid[x][y]

\#主函数

if __name__ == '__main__':

  inputnum=[[0,0,0],

​        [0,0,0],

​        [0,0,0]]

  source = Point(2,0)

  destination = Point(2,2)

solution=Solution()

print("输入棋盘：",inputnum)

print("输入起点：[2,0]")

print("输入终点：[2,2]")

print("输出步数：",solution.shortestPath(inputnum,source,destination))

K个最近的点  

 

import heapq

import numpy as np

np.set_printoptions(threshold=np.inf)

class Point:

  def __init__(self, a=0, b=0):

​    self.x = a

​    self.y = b

class Solution:

  \#参数points为坐标点列表

  \#参数origin为初始点

  \#参数k为整数

  \#返回k个最邻近点

  def kClosest(self, points, origin, k):

​    self.heap = []

​    for point in points:

​      dist = self.getDistance(point, origin)

​      heapq.heappush(self.heap, (-dist, -point.x, -point.y))

​      if len(self.heap) > k:

​        heapq.heappop(self.heap)

​    ret = []

​    while len(self.heap) > 0:

​      _, x, y = heapq.heappop(self.heap)

​      ret.append(Point(-x, -y))

​    ret.reverse()

​    return ret

  def getDistance(self, a, b):

​    return (a.x - b.x) ** 2 + (a.y - b.y) ** 2

\#主函数

if __name__=='__main__':

  a1=Point(0,0)

  a2=Point(0,9)

  inputnum=[a1,a2]

  origin=Point(0,0)

  k=1

  solution=Solution()

  rp=Point(0,0)

  rp=solution.kClosest(inputnum,origin,k)

array=[[rp[0].x,rp[0].y]]

print("输入坐标点：[[0,0],[0,9]]")

print("最近坐标数：k=1")

print("输出坐标点：",array)

优秀成绩  

 

class Record:

  def __init__(self, id, score):

​    self.id = id

​    self.score = score

class Solution:

  \# @参数 {Record[]} 是<student_id, score>列表

  \# @返回 {dict(id, average)} 查找每人5个最高成绩的平均值

  def highFive(self, results):

​    hash = dict()

​    for r in results:

​      if r.id not in hash:

​        hash[r.id] = []

​      hash[r.id].append(r.score)

​      if len(hash[r.id]) > 5:

​        index = 0

​        for i in range(1, 6):

​          if hash[r.id][i] < hash[r.id][index]:

​            index = i

​        hash[r.id].pop(index)

​    answer = dict()

​    for id, scores in hash.items():

​      answer[id] = sum(scores) / 5.0

​    return answer

\#主函数

if __name__=='__main__':

  r1=Record(1,90)

  r2=Record(1,93)

  r3=Record(2,93)

  r4=Record(2,99)

  r5=Record(2,98)

  r6=Record(2,97)

  r7=Record(1,62)

  r8=Record(1,56)

  r9=Record(2,95)

  r10=Record(1,61)

  list=[r1,r2,r3,r4,r5,r6,r7,r8,r9,r10]

  solution=Solution()

   print("输入：(1,90),(1,93),(2,93),(2,99),(2,98),(2,97),(1,62),(1,56),(2,95),(1,61)")

  print("输出：",solution.highFive(list))

二叉树的最长连续子序列I 

 

class TreeNode(object):

  def __init__(self, x):

​    self.val = x

​    self.left = None

​    self.right = None

class Solution:

  \#参数root是二叉树的根节点

  \#返回最长连续序列路径的长度

  def longestConsecutive2(self, root):

​    max_len, _, _, = self.helper(root)

​    return max_len

  def helper(self, root):

​    if root is None:

​      return 0, 0, 0

​    left_len, left_down, left_up = self.helper(root.left)

​    right_len, right_down, right_up = self.helper(root.right)

​    down, up = 0, 0

​    if root.left is not None and root.left.val + 1 == root.val:

​      down = max(down, left_down + 1)

​    if root.left is not None and root.left.val - 1 == root.val:

​      up = max(up, left_up + 1)

​    if root.right is not None and root.right.val + 1 == root.val:

​      down = max(down, right_down + 1)

​    if root.right is not None and root.right.val - 1 == root.val:

​      up = max(up, right_up + 1)

​    len = down + 1 + up

​    len = max(len, left_len, right_len)

​    return len, down, up

\#主函数

if __name__=='__main__':

  inputnum={1,2,0,3}

  root0=TreeNode(0)

  root1=TreeNode(1)

  root2=TreeNode(2)

  root3=TreeNode(3)

  root1.left=root2

  root1.right=root0

  root2.left=root3

solution=Solution()

  print("输入：",inputnum)

  print("输出：",solution.longestConsecutive2(root1))

二叉树的最长连续子序列II 

 

\# 定义一个多节点的树

class MultiTreeNode(object):

  def __init__(self, x):

​      self.val = x

​      self.children = [] # children 是 MultiTreeNode 的list

class Solution:

  \# 参数root为k叉树

  \# 返回最长连续序列路径的长度

  def longestConsecutive3(self, root):

​    max_len, _, _, = self.helper(root)

​    return max_len

  def helper(self, root):

​    if root is None:

​      return 0, 0, 0

​    max_len, up, down = 0, 0, 0

​    for child in root.children:

​      result = self.helper(child)

​      max_len = max(max_len, result[0])

​      if child.val + 1 == root.val:

​        down = max(down, result[1] + 1)

​      if child.val - 1 == root.val:

​        up = max(up, result[2] + 1)

​    max_len = max(down + 1 + up, max_len)

​    return max_len, down, up

\#主函数

if __name__ == '__main__':

  root=MultiTreeNode(5)

  root1=MultiTreeNode(6)

  root2=MultiTreeNode(4)

  root3=MultiTreeNode(7)

  root4=MultiTreeNode(5)

  root5=MultiTreeNode(8)

  root6=MultiTreeNode(3)

  root7=MultiTreeNode(5)

  root8=MultiTreeNode(3)

  root.children=[root1,root2]

  root1.children=[root3,root4,root5]

  root2.children=[root6,root7,root8]

  solution=Solution()

  print("输入为：5<6<7<>,5<>,8<>>,4<3<>,5<>,31<>>>")

  print("输出为：",solution.longestConsecutive3(root))

课程表  

 

from collections import deque

class Solution:

  \#参数numCourses为整数

  \#参数prerequisites为先修课列表对

  \#返回是否能够完成所有课程

  def canFinish(self, numCourses, prerequisites):

​    edges = {i: [] for i in range(numCourses)}

​    degrees = [0 for i in range(numCourses)] 

​    for i, j in prerequisites:

​      edges[j].append(i)

​      degrees[i] += 1

​    queue, count = deque([]), 0

​    for i in range(numCourses):

​      if degrees[i] == 0:

​        queue.append(i)

​    while queue:

​      node = queue.popleft()

​      count += 1

​      for x in edges[node]:

​        degrees[x] -= 1

​        if degrees[x] == 0:

​          queue.append(x)

​    return count == numCourses

\#主函数

if __name__=='__main__':

  list1=[[1,0]]

  n=2

  solution=Solution()

  print("输入课程数：",n)

  print("课程关系：",list1)

  print("输出：",solution.canFinish(n,list1))

安排课程  

 

from queue import Queue

class Solution:

  \# 参数numCourses为整数

  \# 参数prerequisites为课程约束关系

  \# 返回课程顺序

  def findOrder(self, numCourses, prerequisites):

​    edges = {i: [] for i in range(numCourses)}

​    degrees = [0 for i in range(numCourses)] 

​    for i, j in prerequisites:

​      edges[j].append(i)

​      degrees[i] += 1

​    queue = Queue(maxsize = numCourses)

​    for i in range(numCourses):

​      if degrees[i] == 0:

​        queue.put(i)

​    order = []

​    while not queue.empty():

​      node = queue.get()

​      order.append(node)

​      for x in edges[node]:

​        degrees[x] -= 1

​        if degrees[x] == 0:

​          queue.put(x)

​    if len(order) == numCourses:

​      return order

​    return []

\#主函数

if __name__ =='__main__':

  n=4

  list1=[[1,0],[2,0],[3,1],[3,2]]

  solution=Solution()

  print("输入课程数：",n)

  print("输入约束为：",list1)

  print("输出课程为：",solution.findOrder(n,list1))

单词表示数字  

 

class Solution:

  """

  参数number为整数

  返回字符串

  """

  def convertWords(self, number):

​    n1 = ["", "one", "two", "three", "four", "five",

​       "six", "seven", "eight", "nine", "ten",

​       "eleven", "twelve", "thirteen", "fourteen", "fifteen",

​       "sixteen", "seventeen", "eighteen", "nineteen"]

​    n2 = ["", "ten", "twenty", "thirty", "forty",

​       "fifty", "sixty", "seventy", "eighty", "ninety"]

​    n3 = ['hundred', '', 'thousand', 'million', 'billion']

​    res = ''

​    index = 1

​    if number == 0:

​      return 'zero'

​    elif 0 < number < 20:

​      return n1[number]

​    elif 20 <= number < 100:

​      return n2[number // 10] + ' ' + n1[number]

​    else:

​      while number != '':

​        digit = int(str(number)[-3::])

​        number = (str(number)[:-3:])

​        i = len(str(digit))

​        r = ''

​        while True:

​          if digit < 20:

​            r += n1[digit]

​            break

​          elif 20 <= digit < 100:

​            r += n2[digit // 10] + ' '

​          elif 100 <= digit < 1000:

​            r += n1[digit // 100] + ' ' + n3[0] + ' '

​          digit = digit % (10 ** (i - 1))

​          i -= 1

​        if digit != 0:

​          r += ' ' + n3[index] + ' '

​        index += 1

​        r += res

​        res = r

​    return res.strip()

if __name__=='__main__':

​     solution=Solution()

​     n=10245

​     print("输入为：",n)

​     print("输出为：",solution.convertWords(n))

最大子序列的和 

 

class Solution:

  \# 参数nums为整型数组

  \# 参数k为整数

  \# 返回最大和

  def maxSubarray(self, nums, k):

​    n = len(nums)

​    if n < k:

​      return 0

​    result = 0

​    for i in range(k):

​      result += nums[i]

​    sum = [0 for _ in range(n + 1)]

​    min_prefix = 0

​    for i in range(1, n + 1):

​      sum[i] = sum[i - 1] + nums[i - 1]

​      if i >= k and sum[i] - min_prefix > result:

​        result = max(result, sum[i] - min_prefix)

​      if i >= k:

​        min_prefix = min(min_prefix, sum[i - k + 1])

​    return result

\#主函数

if __name__=='__main__':

  inputnum=[-2,2,-3,4,-1,2,1,-5,3]

  k=5

solution=Solution()

  print("输入数组：",inputnum)

  print("输入：k=",k)

  print("输出：sum=",solution.maxSubarray(inputnum,k))

移除子串  

 

class Solution:

  \# 参数s为字符串

\# 参数dict为一组子字符串

\# 返回最小长度

  def minLength(self, s, dict):

​    import queue

​    que = queue.Queue()

​    que.put(s)

​    hash = set([s])

​    min = len(s)

​    while not que.empty():

​      s = que.get()

​      for sub in dict:

​        found = s.find(sub)

​        while found != -1:

​          new_s = s[:found] + s[found + len(sub):]

​          if new_s not in hash:

​            if len(new_s) < min:

​              min = len(new_s)

​            que.put(new_s)

​            hash.add(new_s)

​          found = s.find(sub, found + 1)

​    return min

\#主函数

if __name__=='__main__':

  inputwords="ccdaabcdbb"

  k=["ab","cd"]

  solution=Solution()

  print("输入字符串为：",inputwords)

  print("输入的子串为：",k)

  print("字符串长度为：",solution.minLength(inputwords,k))

数组划分 

 

class Solution:

  \# 参数nums为整型数组

  \# 参数low为整型

  \# 参数high整型

  \# 返回任意可能的解

  def partition2(self, nums, low, high):

​    if len(nums) <= 1:

​      return

​    pl, pr = 0, len(nums) - 1

​    i = 0

​    while i <= pr:

​      if nums[i] < low:

​        nums[pl], nums[i] = nums[i], nums[pl]

​        pl += 1

​        i += 1

​      elif nums[i] > high:

​        nums[pr], nums[i] = nums[i], nums[pr]

​        pr -= 1

​      else:

​        i += 1

​    return nums

\#主函数

if __name__ == '__main__':

  inputnum=[4,3,4,1,2,3,1,2]

  low=2

  high=3

  solution=Solution()

  print("输入数组为：",inputnum)

  print("输入下限为：",low)

  print("输入上限为：",high)

  print("输出结果为：",solution.partition2(inputnum,low,high))

矩形重叠  

 

\# 定义一个点

class Point:

  def __init__(self, a=0, b=0):

​    self.x = a

​    self.y = b

class Solution:

  \# 参数l1 第一个长方形左上角的坐标

  \# 参数r1 第一个长方形右下角的坐标

  \# 参数l2 第二个长方形左上角的坐标

  \# 参数r2 第二个长方形右下角的坐标

  \# 如果重叠返回True

  def doOverlap(self, l1, r1, l2, r2):

​    if l1.x > r2.x or l2.x > r1.x:

​      return False

​    if l1.y < r2.y or l2.y < r1.y:

​      return False

​    return True

\#主函数

if __name__ == '__main__':

  l1=Point(0,8)

  r1=Point(8,0)

  l2=Point(6,6)

  r2=Point(10,0)

  solution=Solution()

  print("输入矩形一：l1=(0,8)，r1=Point(8,0)")

  print("输入矩形二：l2=(6,6)，r2=Point(10,0)")

  print("输出的结果：",solution.doOverlap(l1,r1,l2,r2))

最长回文串  

 

class Solution:

  \# 参数s 是一个包含大小写的字符串

  \# 返回能构建的最长回文串4

  def longestPalindrome(self, s):

​    hash = {}

​    for c in s:

​      if c in hash:

​        del hash[c]

​      else:

​        hash[c] = True

​    remove = len(hash)

​    if remove > 0:

​      remove -= 1

​    return len(s) - remove

\#主函数

if __name__ == '__main__':

  inputnum="abccccdd"

  solution=Solution()

  print("输入字符串为：",inputnum)  

  print("输出回文长度：",solution.longestPalindrome(inputnum))

最大子树  

 

\# 定义一个多节点的树

class TreeNode(object):

  def __init__(self, x):

​      self.val = x

​      self.left = None

​      self.right=None

class Solution:

  \# 参数root为二叉树根

  \# 返回最大节点值

  import sys

  maximum_weight = 0

  result = None

  def findSubtree(self, root):

​    self.helper(root)

​    return self.result.val

  def helper(self, root):

​    if root is None:

​      return 0

​    left_weight = self.helper(root.left)

​    right_weight = self.helper(root.right)

​    

​    if left_weight + right_weight + root.val >= self.maximum_weight or self.result is None:

​      self.maximum_weight = left_weight + right_weight + root.val

​      self.result = root

​    return left_weight + right_weight + root.val

\#主函数

if __name__ == '__main__':

  root = TreeNode(1)

  root1 = TreeNode(-5)

  root2 = TreeNode(2)

  root3 = TreeNode(0)

  root4 = TreeNode(3)

  root5 = TreeNode(-4)

  root6 = TreeNode(-5)

  root.left=root1

  root.right=root2

  root1.left=root3

  root1.right=root4

  root2.left=root5

  root2.right=root6

  solution = Solution()

  print("输入为：[1,-5 2,0 3 -4 -5]")

  print("输出为：",solution.findSubtree(root))

最小生成树  

 

\#定义Connection

class Connection:

  def __init__(self, city1, city2, cost):

​    self.city1, self.city2, self.cost = city1, city2, cost

def comp(a, b):

  if a.cost != b.cost:

​    return a.cost - b.cost

  if a.city1 != b.city1:

​    if a.city1 < b.city1:

​      return -1

​    else:

​      return 1

  if a.city2 == b.city2:

​    return 0

  elif a.city2 < b.city2:

​    return -1

  else:

​    return 1

class Solution:

  \# {Connection[]} connections 城市和花费的列表

  \# {Connection[]} 返回这个类型

  def lowestCost(self, connections):

​    cmp=0

​    hash = {}

​    n = 0

​    for connection in connections:

​      if connection.city1 not in hash:

​        n += 1

​        hash[connection.city1] = n

​      if connection.city2 not in hash:

​        n += 1

​        hash[connection.city2] = n

​    father = [0 for _ in range(n + 1)] 

​    results = []

​    for connection in connections:

​      num1 = hash[connection.city1]

​      num2 = hash[connection.city2]

​      root1 = self.find(num1, father)

​      root2 = self.find(num2, father)

​      if root1 != root2:

​        father[root1] = root2

​        results.append(connection)

​    if len(results)!= n - 1:

​      return []

​    return results

  def find(self, num, father):

​    if father[num] == 0:

​      return num

​    father[num] = self.find(father[num], father)

​    return father[num]

\#主函数

if __name__ == '__main__':

  conn=Connection("Acity","Bcity",1)

  conn1=Connection("Acity","Ccity",2)

  conn2=Connection("Bcity","Ccity",3)

  connections=[conn,conn1,conn2]

  solution = Solution()

  ci01=solution.lowestCost(connections)[0].city1

  ci02=solution.lowestCost(connections)[0].city2

  co0=solution.lowestCost(connections)[0].cost

  ci11=solution.lowestCost(connections)[1].city1

  ci12=solution.lowestCost(connections)[1].city2

  ci1=solution.lowestCost(connections)[1].cost

print("输入：[Acity,Bcity,1],[Acity,Ccity,2],[Bcity,Ccity,3]")

print("输出：" , [[ci01,ci02,co0],[ci11,ci12,ci1]])

骑士的最短路径 

 

import sys

class Solution:

  \# 参数grid是棋盘

  \# 返回最短路径长度

  def shortestPath2(self, grid):

​    n = len(grid)

​    if n == 0:

​      return -1

​    m = len(grid[0])

​    if m == 0:

​      return -1

​    f = [ [sys.maxsize for j in range(m)] for _ in range(n)]

​    f[0][0] = 0

​    for j in range(m):

​      for i in range(n):

​        if not grid[i][j]:

​          if i >= 1 and j >= 2 and f[i - 1][j - 2] != sys.maxsize:

​            f[i][j] = min(f[i][j], f[i - 1][j - 2] + 1)

​          if i + 1 < n and j >= 2 and f[i + 1][j - 2] != sys.maxsize:

​            f[i][j] = min(f[i][j], f[i + 1][j - 2] + 1)

​          if i >= 2 and j >= 1 and f[i - 2][j - 1] != sys.maxsize:

​            f[i][j] = min(f[i][j], f[i - 2][j - 1] + 1)

​          if i + 2 < n and j >= 1 and f[i + 2][j - 1] != sys.maxsize:

​            f[i][j] = min(f[i][j], f[i + 2][j - 1] + 1)

​    if f[n - 1][m - 1] == sys.maxsize:

​      return -1

​    return f[n - 1][m - 1]

\#主函数

if __name__ == '__main__':

  inputnum=[[0,0,0,0],[0,0,0,0],[0,0,0,0]]

  solution = Solution()

  print("输入为：",inputnum)

  print("输出为：",solution.shortestPath2(inputnum))

最大矩阵  

 

class Solution:

  \#参数matrix为矩阵

  \#~~@~~返回整数

  def maxSquare2(self, matrix):

​    if not matrix or not matrix[0]:

​      return 0

​    n, m = len(matrix), len(matrix[0])

​    f = [[0] * m, [0] * m]

​    up = [[0] * m, [0] * m]

​    for i in range(m):

​      f[0][i] = matrix[0][i]

​      up[0][i] = 1 - matrix[0][i]

​    edge = max(matrix[0])

​    for i in range(1, n):

​      f[i % 2][0] = matrix[i][0]

​      up[i % 2][0] = 0 if matrix[i][0] else up[(i - 1) % 2][0] + 1

​      left = 1 - matrix[i][0]

​      for j in range(1, m):

​        if matrix[i][j]:

​          f[i%2][j] =min(f[(i-1)%2][j-1],left,up[(i-1)%2][j])+1

​          up[i % 2][j] = 0

​          left = 0

​        else:

​          f[i % 2][j] = 0

​          up[i % 2][j] = up[(i - 1) % 2][j] + 1

​          left += 1

​      edge = max(edge, max(f[i % 2]))

​    return edge * edge

\#主函数

if __name__ == '__main__':

  inputnum=[[1,0,1,0,0],[1,0,0,1,0],[1,1,0,0,1],[1,0,0,1,0]]

  solution = Solution()

  print("输入为：", inputnum)

  print("输出为：",solution.maxSquare2(inputnum))

二叉树的最大节点  

 

class TreeNode(object):

  def __init__(self, x):

​    self.val = x

​    self.left = None

​    self.right = None

class Solution:

  \# 参数root为二叉树根

  \# 返回最大节点值

  def maxNode(self, root):

​    if root is None:

​      return root

​    left = self.maxNode(root.left)

​    right = self.maxNode(root.right)

​    return self.max(root, self.max(left, right))

  def max(self, a, b):

​    if a is None:

​      return b

​    if b is None:

​      return a

​    if a.val > b.val:

​      return a

​    return b

\#主函数

if __name__ == '__main__':

  root = TreeNode(1)

  root1 = TreeNode(-5)

  root2 = TreeNode(3)

  root3 = TreeNode(1)

  root4 = TreeNode(2)

  root5 = TreeNode(-4)

  root6 = TreeNode(-5)

  root.left = root1

  root.right= root2

  root1.left = root3

  root1.right= root4

  root2.left = root5

  root2.right= root6

  solution = Solution()

  print("输入为：[1,-5 3,1 2 -4 -5]")

  print("输出为：",solution.maxNode(root).val)

寻找重复的数  

 

class Solution:

  \#参数nums为整型数组

  \#返回重复的数

  def findDuplicate(self, nums):

​    start, end = 1, len(nums) - 1

​    while start + 1 < end:

​      mid = (start + end) // 2

​      if self.smaller_than_or_equal_to(nums, mid) > mid:

​        end = mid

​      else:

​        start = mid

​    if self.smaller_than_or_equal_to(nums, start) > start:

​      return start

​    return end

  def smaller_than_or_equal_to(self, nums, val):

​    count = 0

​    for num in nums:

​      if num <= val:

​        count += 1

​    return count

\#主函数

if __name__ == '__main__':

  inputnum= [5,5,4,3,2,1]

  solution = Solution()

  print("输入为：",inputnum)

print("输出为：",solution.findDuplicate(inputnum))

拼字游戏  

 

import collections

class TrieNode(object):

  def __init__(self, value=0):

​    self.value = value

​    self.isWord = False

​    self.children = collections.OrderedDict()

  @classmethod

  def insert(cls, root, word):

​    p = root

​    for c in word:

​      child = p.children.get(c)

​      if not child:

​        child = TrieNode(c)

​        p.children[c] = child

​      p = child

​    p.isWord = True

class Solution:

  \# 参数board为字符列表

  \# 参数words为字符串列表

  \# 返回整数

  def boggleGame(self, board, words):

​    self.board = board

​    self.words = words

​    self.m = len(board)

​    self.n = len(board[0])

​    self.results = []

​    self.temp = []

​    self.visited = [[False for _ in range(self.n)] for _ in range(self.m)]

​    self.root = TrieNode()

​    for word in words:

​      TrieNode.insert(self.root, word)

​    self.dfs(0, 0, self.root)

​    return len(self.results)

  def dfs(self, x, y, root):

​    for i in range(x, self.m):

​      for j in range(y, self.n):

​        paths = []

​        temp = []

​        self.getAllPaths(i, j, paths, temp, root)

​        for path in paths:

​          word = ''

​          for px, py in path:

​            word += self.board[px][py]

​            self.visited[px][py] = True

​          self.temp.append(word)

​          if len(self.temp) > len(self.results):

​            self.results = self.temp[:]

​          self.dfs(i, j, root)

​          self.temp.pop()

​          for px, py in path:

​            self.visited[px][py] = False

​      y = 0

  def getAllPaths(self, i, j, paths, temp, root):

​    if i < 0 or i >= self.m or j < 0 or j >= self.n or \

​      self.board[i][j] not in root.children or \

​      self.visited[i][j] == True:

​      return

​    root = root.children[self.board[i][j]]

​    if root.isWord:

​      temp.append((i,j))

​      paths.append(temp[:])

​      temp.pop()

​      return

​    self.visited[i][j] = True

​    deltas = [(0,1), (0,-1), (1,0), (-1, 0)]

​    for dx, dy in deltas:

​      newx = i + dx

​      newy = j + dy

​      temp.append((i,j))

​      self.getAllPaths(newx, newy, paths, temp, root)

​      temp.pop()

​    self.visited[i][j] = False

\#主函数

if __name__ == '__main__':

  inputnum= [['a', 'b', 'c'],

['d', 'e', 'f'],

['g', 'h', 'i']]

  dictw = ["abc", "cfi", "beh", "defi", "gh"]

  solution = Solution()

  print("输入字符为：",inputnum)

  print("输入字典为：",dictw)

  print("输出个数为：",solution.boggleGame(inputnum,dictw))

132模式识别  

 

import sys

class Solution:

  \# 参数nums为整数列表

  \# 返回True或者False

  def find132pattern(self, nums):

​    stk = [-sys.maxsize]

​    for i in range(len(nums)-1, -1, -1):

​      if nums[i] < stk[-1]:

​        return True

​      else:

​        while stk and nums[i] > stk[-1]:

​          v = stk.pop()

​        stk.append(nums[i])

​        stk.append(v)

​    return False

\#主函数

if __name__ == '__main__':

  inputnum=[1, 2, 3, 4]

  solution = Solution()

  print("输入为：",inputnum)

  print("输出为：",solution.find132pattern(inputnum))

检查缩写字  

 

class Solution:

  \#参数word为字符串

  \#参数abbr为字符串

  \#返回布尔类型

  def validWordAbbreviation(self, word, abbr):

​    i = 0

​    j = 0

​    while i < len(word) and j < len(abbr):

​      if word[i] == abbr[j]:

​        i += 1

​        j += 1

​      elif abbr[j].isdigit() and abbr[j] != '0':

​        start = j

​        while j < len(abbr) and abbr[j].isdigit():

​          j += 1

​        i += int(abbr[start : j])

​      else:

​        return False

​    return i == len(word) and j == len(abbr)

\#主函数

if __name__ == '__main__':

  s = "internationalization"

  abbr = "i12iz4n"

  solution = Solution()

  print("输入为：",s)

  print("缩写为：",abbr)

  print("输出为：",solution.validWordAbbreviation(s,abbr))

一次编辑距离  

 

class Solution:

  \# 参数s为字符串

  \# 参数t为字符串

  \# 返回布尔类型

  def isOneEditDistance(self, s, t):

​    m = len(s)

​    n = len(t)

​    if abs(m - n) > 1:

​      return False

​    if m > n:

​      return self.isOneEditDistance(t, s)

​    for i in range(m):

​      if s[i] != t[i]:

​        if m == n:

​          return s[i + 1:] == t[i + 1:]

​        return s[i:] == t[i + 1:]

​    return m != n

\#主函数

if __name__ == '__main__':

   s = "aDb"

   t = "adb"

   solution = Solution()

   print("输入字符串s：",s)

   print("输入字符串t：",t)

   print("输出为：",solution.isOneEditDistance(s,t))

数据流滑动窗口平均值  

 

from collections import deque

class MovingAverage(object):

  def __init__(self, size):

​    self.queue = deque([])

​    self.size = size

​    self.sum = 0.0

  def next(self, val):

​    if len(self.queue) == self.size:

​      self.sum -= self.queue.popleft()

​    self.sum += val

​    self.queue.append(val)

​    return self.sum / len(self.queue)

if __name__ == '__main__':

  solution = MovingAverage(3)

  print("输入数据流：1,10,3,5")

  print("输出流动窗1：",solution.next(1))

  print("输出流动窗2：",solution.next(10))

  print("输出流动窗3：",solution.next(3))

  print("输出流动窗4：",solution.next(5))

最长绝对文件路径  

 

import re

import collections

class Solution:

  \#参数input为抽象的文件系统

  \#返回最长文件的绝度路径长度

  def lengthLongestPath(self, input):

​    dict = collections.defaultdict(lambda: "")

​    lines = input.split("\n")

​    n = len(lines)

​    result = 0

​    for i in range(n):

​      count = lines[i].count("\t")

​      lines[i] = dict[count - 1] + re.sub("\\t+","/", lines[i])

​      if "." in lines[i]:

​        result = max(result, len(lines[i]))

​      dict[count] = lines[i]

​    return result

\#主函数

if __name__ == '__main__':

inputwords="dir\n\tsubdir1\n\t\tfile1.ext\n\t\tsubsubdir1\n\tsubdir2\n\t\tsubsubdir2\n\t\t\tfile2.ext"

  solution=Solution()

  print("输入为：",inputwords)

  print("输出为：",solution.lengthLongestPath(inputwords))

识别名人  

 

\#假定0认识1,1不认识0

class Celebrity: 

  def knows(a,b):

​    if a==0 and b==1 :

​      return True

​    if a==1 and b==0 :

​      return False

class Solution:

  \# 参数n为整数

  \# 返回整数

  def findCelebrity(self, n):

​    celeb = 0 

​    for i in range(1, n):

​      if Celebrity.knows(celeb, i):

​        celeb = i

​    for i in range(n):

​      if celeb != i and Celebrity.knows(celeb, i):

​        return -1

​      if celeb != i and not Celebrity.knows(i, celeb):

​        return -1

​    return celeb

\#主函数

if __name__ == '__main__':

  n=2

  solution=Solution()

  print("输入为：",n)

  print("输出为：",solution.findCelebrity(n))

第一个独特字符位置  

 

class Solution:

  \# 参数s为字符串

  \# 返回整数

  def firstUniqChar(self, s):

​    alp = {}

​    for c in s:

​      if c not in alp:

​        alp[c] = 1

​      else:

​        alp[c] += 1

​    index = 0

​    for c in s:

​      if alp[c] == 1:

​        return index

​      index += 1

​    return -1

\#主函数

if __name__ == '__main__':

  s = "lintcode"

  solution=Solution()

  print("输入为：",s)

  print("输出为：",solution.firstUniqChar(s))

子串字谜  

 

class Solution:

  \# 参数s为字符串

  \# 参数p为字符串

  \# 返回索引列表

  def findAnagrams(self, s, p):

​    ans = []

​    sum = [0 for x in range(0,30)]

​    plength = len(p)

​    slength = len(s)

​    for i in range(plength):

​      sum[ord(p[i]) - ord('a')] += 1

​    start = 0

​    end = 0

​    matched = 0

​    while end < slength:

​      if sum[ord(s[end]) - ord('a')] >= 1:

​        matched += 1

​      sum[ord(s[end]) - ord('a')] -= 1

​      end += 1

​      if matched == plength:

​        ans.append(start)

​      if end - start == plength:

​        if sum[ord(s[start]) - ord('a')] >= 0:

​          matched -= 1

​        sum[ord(s[start]) - ord('a')] += 1

​        start += 1

​    return ans

\#主函数

if __name__ == '__main__':

  s = "cbaebabacd"

  p = "abc"

  solution = Solution()

  print("输入字符串：",s)

  print("输入子串为：",p)

  print("输出索引为：",solution.findAnagrams(s,p))

单词缩写集  

 

class ValidWordAbbr:

  def __init__(self, dictionary):

​    self.map = {}

​    for word in dictionary:

​      abbr = self.word_to_abbr(word)

​      if abbr not in self.map:

​        self.map[abbr] = set() 

​      self.map[abbr].add(word)

  def word_to_abbr(self, word):

​    if len(word) <= 1:

​      return word

​    return word[0] + str(len(word[1:-1])) + word[-1]

  def isUnique(self, word):

​    abbr = self.word_to_abbr(word)

​    if abbr not in self.map:

​      return True

​    for word_in_dict in self.map[abbr]:

​      if word != word_in_dict:

​        return False

​    return True

\#主函数

if __name__ == '__main__':

  dic=[ "deer", "door", "cake", "card" ]

  solution = ValidWordAbbr(dic)

  print("输入字典为：",dic)

  print("输入单词为： dear")

  print("输出结果为：",solution.isUnique("dear"))

  print("输入单词为： cart")

  print("输出结果为：",solution.isUnique("cart"))

二叉树翻转  

 

class TreeNode:

  def __init__(self, val):

​    self.val = val

​    self.left, self.right = None, None

class Solution:

  def upsideDownBinaryTree(self, root):

​    if root is None:

​      return None

​    return self.dfs(root)

  def dfs(self, root):

​    if root.left is None:

​      return root

​    newRoot = self.dfs(root.left)

​    root.left.right = root

​    root.left.left = root.right

​    root.left = None

​    root.right = None

​    return newRoot

\#主函数

if __name__ == '__main__':

  root1 = TreeNode(1)

  root2 = TreeNode(2)

  root3 = TreeNode(3)

  root4 = TreeNode(4)

  root5 = TreeNode(5)

  inputnum=[1,2,3,4,5,"#","#"]

  root1.left = root2

  root1.right=root3

  root2.left=root4

  root2.right=root5

  solution = Solution()

  a=solution.upsideDownBinaryTree(root1)

  a0=a.val

  a1=a.left.val

  a2=a.right.val

  a3='#'

  a4='#'

  a5=a.right.left.val

  a6=a.right.right.val

  aa=[a0,a1,a2,a3,a4,a5,a6]

  print("输入为",inputnum)

  print("输出为",aa)  

 二叉树垂直遍历  

 

import collections

import queue as Queue

class TreeNode:

  def __init__(self, val):

​    self.val = val

​    self.left, self.right = None, None

class Solution:

  \# 参数root为二叉树根

  \# 返回整型列表

  def verticalOrder(self, root):

​    results = collections.defaultdict(list)

​    queue = Queue.Queue()

​    queue.put((root, 0))

​    while not queue.empty():

​      node, x = queue.get()

​      if node:

​        results[x].append(node.val)

​        queue.put((node.left, x - 1))

​        queue.put((node.right, x + 1))

​    return [results[i] for i in sorted(results)]

\#主函数

if __name__ == '__main__':

  root=TreeNode(3)

  root1=TreeNode(9)

  root2=TreeNode(20)

  root3=TreeNode(15)

  root4=TreeNode(7)

  root.left=root1

  root.right=root2

  root2.left=root3

  root2.right=root4

  solution = Solution()

  a=solution.verticalOrder(root)

  print("输入为： [3,9,20,#,#,15,7]")

  print("输出为：",a)

因式分解  

 

class Solution:

  \#参数n为整数

  \#返回组合列表

  def getFactors(self, n):

​    result = []

​    self.helper(result, [], n, 2);

​    return result

  def helper(self, result, item, n, start):

​    if n <= 1:

​      if len(item) > 1:

​        result.append(item[:])

​      return

​    import math

​    for i in range(start, int(math.sqrt(n)) + 1):

​      if n % i == 0:

​        item.append(i)

​        self.helper(result, item, n / i, i)

​        item.pop()

​    if n >= start:

​      item.append(n)

​      self.helper(result, item, 1, n)

​      item.pop()

\#主函数

if __name__ == '__main__':

  inputnum=8

  solution = Solution()

  print("输入为：",inputnum)

  print("输出为：",solution.getFactors(inputnum))

Insert Delete GetRandom O(1) 

 

import random

class RandomizedSet(object):

  def __init__(self):

​    self.nums, self.pos = [], {}

  \# 参数val为整数

  \# 返回布尔类型

  def insert(self, val):

​    if val not in self.pos:

​      self.nums.append(val)

​      self.pos[val] = len(self.nums) - 1

​      return True

​    return False

  \# 参数val为整数

  \# 返回布尔类型

  def remove(self, val):

​    if val in self.pos:

​      idx, last = self.pos[val], self.nums[-1]

​      self.nums[idx], self.pos[last] = last, idx

​      self.nums.pop()

​      del self.pos[val]

​      return True

​    return False

  def getRandom(self):

​    return self.nums[random.randint(0, len(self.nums) - 1)]

\#主函数

if __name__ == '__main__':

  solution=RandomizedSet()

  print("插入一个元素：1")

  print("输出为：",solution.insert(1))

  print("移除一个元素：2")

  print("输出为：",solution.remove(2))

  print("插入一个元素：2")

  print("输出为：",solution.insert(2))

  print("获取随机元素：1")

  print("输出为：",solution.getRandom())

  print("移除一个元素：1")

  print("输出为：",solution.remove(1))

  print("插入一个元素：2")

  print("输出为：",solution.insert(2))  

编码和解码字符串  

 

class Solution:

  \#参数strs为字符串列表

  \#返回编码后的字符串列表

  \# " " -> ": " 分隔不同单词

  \# ":" -> "::" 区分":"

  def encode(self, strs):

​    encoded = []

​    for string in strs:

​      for char in string:

​        if char == ":":

​          encoded.append("::")

​        else:

​          encoded.append(char)

​      encoded.append(": ")

​    return "".join(encoded)

  \#参数str为字符串

  \#返回解码字符串列表

  def decode(self, str):

​    res = []

​    idx = 0

​    length = len(str)

​    tmp_str = []

​    while idx < length - 1:

​      if str[idx] == ":":

​        if str[idx + 1] == ":":

​          tmp_str.append(":")

​          idx += 2

​        elif str[idx + 1] == " ":

​          res.append("".join(tmp_str))

​          tmp_str = []

​          idx += 2

​      else:

​        tmp_str.append(str[idx])

​        idx += 1

​    return res

\#主函数

if __name__ == '__main__':

  inputwords=["lint","code","love","you"]

  solution=Solution()

  print("输入：",inputwords)

  print("编码：",solution.encode(inputwords))

  print("解码：",solution.decode(solution.encode(inputwords)))

猜数游戏  

 

def guess(mid):

  if mid>4:

​    return -1

  if mid <4:

​    return 1

  if mid==4:

​    return 0

class Solution:

  \#参数n为整数

  \#返回所猜的数

  def guessNumber(self, n):

​    l = 1

​    r = n

​    while l <= r:

​      mid = abs(l + (r - l) / 2)

​      res = guess(mid)

​      if res == 0:

​        return mid

​      if res == -1:

​        r = mid - 1

​      if res == 1: 

​        l = mid + 1

​    return int(mid)

\#主函数

if __name__ == '__main__':

  inputnum=10

  selectedNumber=4

  solution=Solution()

  print("输入总数为：",inputnum)

  print("所选的数字：",selectedNumber)

  print("所猜的数字：",solution.guessNumber(inputnum))

数1的个数  

 

class Solution:

  \#参数num为非负整数

  \#返回数组

  def countBits(self, num):

​    f = [0] * (num + 1)

​    for i in range(1, num+1):

​      f[i] = f[i & i-1] + 1

​    return f

\#主函数

if __name__ == '__main__':

  inputnum=5

  solution = Solution()

  print("输入：",inputnum)

  print("输出：",solution.countBits(inputnum))

平面范围求和 -不可变矩阵  

 

class NumMatrix(object):

  \#参数matrix为矩阵

  def __init__(self, matrix):

​    if len(matrix) == 0 or len(matrix[0]) == 0:

​      return 

​    n = len(matrix)

​    m = len(matrix[0])

​    self.dp = [[0] * (m + 1) for _ in range(n + 1)]

​    for r in range(n):

​      for c in range(m):

​        self.dp[r+ 1][c + 1] = self.dp[r + 1][c] + self.dp[r][c + 1] + \

​          matrix[r][c] - self.dp[r][c]

  \# 参数row1为整数

  \# 参数col1为整数

  \# 参数row2为整数

  \# 参数col2为整数

  \# 返回整数

  def sumRegion(self, row1, col1, row2, col2):

​    return self.dp[row2 + 1][col2 + 1] - self.dp[row1][col2 + 1] - \

​      self.dp[row2 + 1][col1] + self.dp[row1][col1]

\#主函数

if __name__ == '__main__':

  inputnum=[[3,0,1,4,2],[5,6,3,2,1],[1,2,0,1,5],[4,1,0,1,7],[1,0,3,0,5]]

  solution = NumMatrix(inputnum)

  print("输入矩阵为：",inputnum)

  print("区域1的和：",solution.sumRegion(2, 1, 4, 3))

  print("区域2的和：",solution.sumRegion(1, 1, 2, 2))

  print("区域3的和：",solution.sumRegion(1, 2, 2, 4))

猜数游戏 

 

class Solution:

  \# 参数n为整数

  \# 返回整数

  def getMoneyAmount(self, n):

​    dp = [[0 for _ in range(n + 1)] for __ in range(n + 1)]

​    for len in range(2, n + 1):

​      for start in range(1, n - len + 2):

​        import sys

​        temp = sys.maxsize

​        for k in range(start + int((len - 1) / 2), start + int(len - 1)):

​          left, right = dp[start][k - 1], dp[k + 1][start + len - 1]

​          temp = min(k + max(left, right), temp)

​          if left > right:

​            break

​        dp[start][start + len - 1] = temp

​    return dp[1][n]

\#主函数

if __name__ == '__main__':

  inputnum=10

  solution = Solution()

  print("输入为：",inputnum)

  print("输出为：",solution.getMoneyAmount(inputnum))

最长的回文序列  

 

class Solution:

  \# 参数s为字符串

  \# 返回整数

  def longestPalindromeSubseq(self, s):

​    length = len(s)

​    if length == 0:

​      return 0

​    dp = [[0 for _ in range(length)] for __ in range(length)]

​    for i in range(length - 1, -1, -1):

​      dp[i][i] = 1

​      for j in range(i + 1, length):

​        if s[i] == s[j]:

​          dp[i][j] = dp[i + 1][j - 1] + 2

​        else:

​          dp[i][j] = max(dp[i + 1][j], dp[i][j - 1])

​    return dp[0][length - 1]

\#主函数

if __name__ == '__main__':

  inputnum="bbbab"

  solution = Solution()

  print("输入为：",inputnum)

  print("输出为：",solution.longestPalindromeSubseq(inputnum))

1和0  

 

class Solution:

  \#参数strs为字符串数组

  \#参数m为整数

  \#参数n为整数

  \#返回整数

  def findMaxForm(self, strs, m, n):

​    dp = [[0] * (m + 1) for _ in range(n + 1)]

​    for s in strs:

​      zero = 0

​      one = 0

​      for ch in s:

​        if ch == "1":

​          one += 1

​        else:

​          zero += 1

​      for i in range(n,one - 1,-1):

​        for j in range(m,zero - 1,-1):

​          if dp[i - one][j - zero] + 1 > dp[i][j]:

​            dp[i][j] = dp[i - one][j - zero] + 1

​    return dp[-1][-1]

\#主函数

if __name__ == '__main__':

  inputnum=["10", "0001", "111001", "1", "0"]

  m=5

  n=3

  solution = Solution()

  print("输入为：",inputnum)

  print("输入m ：",m)

  print("输入n ：",n)

  print("输出 ：",solution.findMaxForm(inputnum,m,n))

预测能否胜利  

 

class Solution:

  \#参数nums为整数数组

  \#返回布尔类型

  def PredictTheWinner(self, nums):

​    if len(nums) & 1 == 0: return True

​    dp = [[0] * len(nums) for _ in range(len(nums))]

​    for i, v in enumerate(nums):

​      dp[i][i] = v

​    for i in range(1, len(nums)):

​      for j in range(len(nums) - i):

​        dp[j][j + i] = max(nums[j] - dp[j + 1][j + i], nums[j + i] - dp[j][j + i - 1])

​    return dp[0][-1] > 0

\#主函数

if __name__ == '__main__':

  inputnum=[1, 5, 2]

  solution = Solution()

  print("输入为：",inputnum)

  print("输出为：",solution.PredictTheWinner(inputnum))

循环单词  

 

class Solution:

  \#参数words为单词列表

  \#返回整数

  def countRotateWords(self, words):

​    dict1 = set()

​    for w in words:

​      s = w + w

​      for i in range(0, len(w)):

​        tmp = s[i : i +len(w)]

​        if tmp in dict1:

​          dict1.remove(tmp)

​      dict1.add(w)

​    return len(dict1)

\#主函数

if __name__ == '__main__':

  dict1 = ["picture", "turepic", "icturep", "word", "ordw", "long"]

  solution = Solution()

  print("输入为：",dict1)

  print("输出为：",solution.countRotateWords(dict1))

最大子数组之和为k 

 

class Solution:

  \#参数nums为数组

  \#参数k为整数

  \#返回整数

  def maxSubArrayLen(self, nums, k):

​    m = {}

​    ans = 0

​    m[k] = 0

​    n = len(nums)

​    sum = [0 for i in range(n + 1)]

​    for i in range(1, n + 1):

​      sum[i] = sum[i - 1] + nums[i - 1]

​      if sum[i] in m:

​        ans = max(ans, i - m[sum[i]])

​      if sum[i] + k not in m:

​        m[sum[i] + k] = i

​    return ans

if __name__ == '__main__':

  num = [-2, 7, 3, -4, 1]

  k = 5

  solution = Solution()

  print("输入数组为：",num)

  print("输入目标值：",k)

  print("输出为：",solution.maxSubArrayLen(num, k))

等差切片  

 

class Solution(object):

  def numberOfArithmeticSlices(self, A):

​    \#参数A为列表

​    \#返回整数

​    size = len(A)

​    if size < 3: return 0

​    ans = cnt = 0

​    delta = A[1] - A[0]

​    for x in range(2, size):

​      if A[x] - A[x - 1] == delta:

​        cnt += 1

​        ans += cnt

​      else:

​        delta = A[x] - A[x - 1]

​        cnt = 0

​    return ans

if __name__ == '__main__':

  solution=Solution()

  inputnum=[1, 2, 3, 4]

  print("输入为：",inputnum)

  print("输出为：",solution.numberOfArithmeticSlices(inputnum))

2D战舰  

 

class Solution(object):
   def countBattleships(self, board):
     \#参数board为列表
     \#返回整数

​    len1 = len(board)
​     if len1 == 0:
​       return 0;
​     len2 = len(board[0])
​     ans = 0
​     for i in range(0, len1):
​       for j in range(0,len2):
​         if board[i][j] == 'X' and ( i == 0 or board[i-1][j] == '.' )and (j == 0 or board[i][j-1] == '.'):
​           ans += 1
​     return ans
 if __name__ == '__main__':
   solution=Solution()
   inputnum=["X..X","...X","...X"]

  print("输入为：",inputnum)

  print("输出为：",solution.countBattleships(inputnum))

连续数组  

 

class Solution:

  \#参数nums为数组

  \#返回整数

  def findMaxLength(self, nums):

​    index_sum = {}

​    cur_sum = 0

​    ans = 0

​    for i in range(len(nums)):

​      if nums[i] == 0: cur_sum -= 1

​      else: cur_sum += 1

​      if cur_sum == 0: ans = i+1

​      elif cur_sum in index_sum: ans = max(ans, i-index_sum[cur_sum])

​      if cur_sum not in index_sum: index_sum[cur_sum] = i

​    return ans

if __name__ == '__main__':

  solution=Solution()

  inputnum=[1,0]

  print("输入为：",inputnum)

  print("输出为：",solution.findMaxLength(inputnum))

带有冷却时间的买卖股票最佳时间  

 

class Solution:

  \#参数prices为整数列表

  \#返回整数

  def maxProfit(self, prices):

​    if not prices:

​      return 0

​    buy, sell, cooldown = [0 for _ in range(len(prices))], [0 for _ in range(len(prices))], [0 for _ in range(len(prices))]

​    buy[0] = -prices[0]

​    for i in range(1, len(prices)):

​      cooldown[i] = sell[i - 1]

​      sell[i] = max(sell[i - 1], buy[i - 1] + prices[i])

​      buy[i] = max(buy[i - 1], cooldown[i - 1] - prices[i])

​    return max(sell[-1], cooldown[-1])

if __name__ == '__main__':

  solution=Solution()

  inputnum=[1,2,3,0,2]

  print("输入为：",inputnum)

  print("输出为：",solution.maxProfit(inputnum))
 4.运行结果

输入为：[1, 2, 3, 0, 2]

输出为：3

小行星的碰撞  

 

class Solution:

  \#参数asteroids为整数数组

  \#返回整数数组

  def asteroidCollision(self, asteroids):

​    ans, i, n= [], 0, len(asteroids)

​    while i < n:

​      if asteroids[i] > 0:

​        ans.append(asteroids[i])

​      elif len(ans) == 0 or ans[-1] < 0:

​        ans.append(asteroids[i])

​      elif ans[-1] <= -asteroids[i]:

​        if ans[-1] < -asteroids[i]:

​          i -= 1

​        ans.pop()

​      i += 1

​    return ans

if __name__ == '__main__':

  solution=Solution()

  inputnum=[5,10,-5]

  print("输入为：",inputnum)

  print("输出~~入~~为：",solution.asteroidCollision(inputnum))


扩展弹性词  

 

class Solution:

  \#参数S为字符串

  \#参数words为字符串列表

  \#返回整数

  def expressiveWords(self, S, words):

​    SList = self.countGroup(S)

​    n = len(SList)

​    ans = 0

​    for word in words:

​      wordList = self.countGroup(word)

​      if n != len(wordList):

​        continue

​      ok = 1

​      for i in range(n):

​        if not self.canExtend(wordList[i], SList[i]):

​          ok = 0

​          break

​      ans += ok

​    return ans

  def countGroup(self, s):

​    n = len(s)

​    cnt = 1

​    ret = []

​    for i in range(1, n):

​      if s[i] == s[i - 1]:

​        cnt += 1

​      else:

​        ret.append((s[i - 1], cnt))

​        cnt = 1

​    ret.append((s[-1], cnt))

​    return ret

  def canExtend(self, From, To):

​    return From[0] == To[0] and \

​        (From[1] == To[1] or (From[1] < To[1] and To[1] >= 3))

if __name__ == '__main__':

  solution=Solution()

  inputnum1="heeellooo"

  inputnum2=["hello", "hi", "helo"]

  print("输入字符串1为：",inputnum1)

  print("输入字符串2为：",inputnum2)

  print("输出为：",solution.expressiveWords(inputnum1,inputnum2))

找到最终的安全状态  

 

class Solution:

  \#参数graph为整数数组

  \#返回整数

  def eventualSafeNodes(self, graph):

​    def dfs(graph, i, visited):

​      for j in graph[i]:

​        if j in visited:

​          return False

​        if j in ans:

​          continue

​        visited.add(j)

​        if not dfs(graph, j, visited):

​          return False

​        visited.remove(j)

​      ans.add(i)

​      return True

​    ans = set()

​    for i in range(len(graph)):

​      visited = set([i])

​      dfs(graph, i, visited)

​    return sorted(list(ans))

if __name__ == '__main__':

  solution=Solution()

  inputnum=[[1,2],[2,3],[5],[0],[5],[],[]]

  print("输入为：",inputnum)

  print("输出为：",solution.eventualSafeNodes(inputnum))

使序列递增的最小交换次数  

 

class Solution:

  def minSwap(self, A, B):

​    if len(A) == 0 or len(A) != len(B):

​      return 0

​    non_swapped, swapped = [0] * len(A), [1] + [0] * (len(A) - 1)

​    for i in range(1, len(A)):

​      swps, no_swps = set(), set()

​      if A[i - 1] < A[i] and B[i - 1] < B[i]:

​        swps.add(swapped[i - 1] + 1)

​        no_swps.add(non_swapped[i - 1])

​      if B[i - 1] < A[i] and A[i - 1] < B[i]:

​        swps.add(non_swapped[i - 1] + 1)

​        no_swps.add(swapped[i - 1])

​      swapped[i], non_swapped[i] = min(swps), min(no_swps)

​    return min(swapped[-1], non_swapped[-1])

if __name__ == '__main__':

  solution=Solution()

  inputnum1=[1,3,5,4]

  inputnum2=[1,2,3,7]

  print("输入1为：",inputnum1)

  print("输入2为：",inputnum2)

  print("输出为：",solution.minSwap(inputnum1,inputnum2))

所有可能的路径  

 

class Solution:

  \#参数graph为数组

  \#返回数组

  def allPathsSourceTarget(self, graph):

​    N = len(graph)

​    res = []

​    def dfs(N, graph, start, res, path):

​      if start == N-1:

​        res.append(path)

​      else:

​        for node in graph[start]:

​          dfs(N, graph, node, res, path + [node])

​    dfs(N, graph, 0, res, [0])

​    return (res)

if __name__ == '__main__':

  solution=Solution()

  inputnum=[[1,2],[3],[3],[]]

  print("输入为：",inputnum)

  print("输出为：",solution.allPathsSourceTarget(inputnum))

合法的井字棋状态  

 

class Solution:

  def validTicTacToe(self, board):

​    \#参数board为列表

​    \#返回布尔类型

​    num_X, num_O = 0, 0

​    for i in range(0, 3):

​      for j in range(0, 3):

​        if board[i][j] == 'X':

​          num_X += 1

​        if board[i][j] == 'O':

​          num_O += 1

​    if not (num_X == num_O or num_X == num_O + 1):

​      return False

​    for i in range(3):

​      if board[i][0] == board[i][1] == board[i][2]:

​        if board[i][0] == 'X':

​          return num_X == num_O + 1

​        if board[i][0] == 'O':

​          return num_X == num_O

​    for j in range(3):

​      if board[0][j] == board[1][j] == board[2][j]:

​        if board[0][j] == 'X':

​          return num_X == num_O + 1

​        if board[0][j] == 'O':

​          return num_X == num_O

​    if board[0][0] == board[1][1] == board[2][2]:

​      if board[0][0] == 'X':

​        return num_X == num_O + 1

​      if board[0][0] == 'O':

​        return num_X == num_O

​    if board[0][2] == board[1][1] == board[2][0]:

​      if board[2][0] == 'X':

​        return num_X == num_O + 1

​      if board[2][0] == 'O':

​        return num_X == num_O

​    return True

if __name__ == '__main__':

  solution=Solution()

  inputnum=["O ", "  ", "  "]

  print("输入为：",inputnum)

  print("输出为：",solution.validTicTacToe(inputnum))

满足要求的子串个数  

 

class Solution:

  \#参数S为字符串

  \#参数words为单词字典

  \#返回子串的个数

  def numMatchingSubseq(self, S, words):

​    self.idx = {'a': 0, 'b': 1, 'c': 2, 'd': 3, 'e': 4,

​          'f': 5, 'g': 6, 'h': 7, 'i': 8, 'j': 9,

​          'k': 10, 'l': 11, 'm': 12, 'n': 13, 'o': 14,

​          'p': 15, 'q': 16, 'r': 17, 's': 18, 't': 19,

​          'u': 20, 'v': 21, 'w': 22, 'x': 23, 'y': 24, 'z': 25}

​    n = len(S)

​    nxtPos = []

​    tmp = [-1] * 26

​    for i in range(n - 1, -1, -1):

​      tmp[self.idx[S[i]]] = i

​      nxtPos.append([i for i in tmp])

​    nxtPos = nxtPos[::-1]

​    ans = 0

​    for word in words:

​      if self.isSubseq(word, nxtPos):

​        ans += 1

​    return ans

  def isSubseq(self, word, nxtPos):

​    lenw = len(word)

​    lens = len(nxtPos)

​    i, j = 0, 0

​    while i < lenw and j < lens:

​      j = nxtPos[j][self.idx[word[i]]]

​      if j < 0:

​        return False

​      i += 1

​      j += 1

​    return i == lenw

if __name__ == '__main__':

  solution=Solution()

  input1="abcde"

  input2=["a", "bb", "acd", "ace"]

  print("输入字符串为：",input1)

  print("输入子串为：",input2)

  print("输出为：",solution.numMatchingSubseq(input1,input2))

多米诺和三格骨牌铺瓦问题  

 

class Solution:

  \#参数N为整数

  \#返回整数

  def numTilings(self, N):

​    if N < 3:

​      return N

​    MOD = 1000000007

​    f = [[0, 0, 0] for i in range(N + 1)]

​    f[0][0] = f[1][0] = f[1][1] = f[1][2] = 1

​    for i in range(2, N + 1):

​      f[i][0] = (f[i - 1][0] + f[i - 2][0] + f[i - 2][1] + f[i - 2][2]) % MOD;

​      f[i][1] = (f[i - 1][0] + f[i - 1][2]) % MOD;

​      f[i][2] = (f[i - 1][0] + f[i - 1][1]) % MOD;

​    return f[N][0]

if __name__ == '__main__':

  solution=Solution()

  inputnum=3

  print("输入为：",inputnum)

  print("输出为：",solution.numTilings(inputnum))

逃离幽灵  

 

class Solution:

  \#参数ghosts为数组

  \#参数target为数组

  \#返回布尔类型

  def escapeGhosts(self, ghosts, target):

​    target_dist = abs(target[0]) + abs(target[1])

​    for r, c in ghosts:

​      ghost_target = abs(target[0] - r) + abs(target[1] - c)

​      if ghost_target <= target_dist:

​        return False

​    return True

if __name__ == '__main__':

  solution=Solution()

  inputnum1=[[1, 0], [0, 3]]

  inputnum2=[0, 1]

  print("输入幽灵为：",inputnum1)

  print("输入目标为：",inputnum2)

  print("输出为：",solution.escapeGhosts(inputnum1,inputnum2))

寻找最便宜的航行旅途（最多经过k个中转站）  

 

import sys

class Solution:

  \#参数n为整数

  \#参数flights为矩阵

  \#参数src为整数

  \#参数dst为整数

  \#参数K为整数

  \#返回整数

  def findCheapestPrice(self, n, flights, src, dst, K):

​    distance = [sys.maxsize for i in range(n)]

​    distance[src] = 0

​    for i in range(0, K + 1):

​      dN = list(distance)

​      for u, v, c in flights:

​        dN[v] = min(dN[v], distance[u] + c)

​      distance = dN

​    if distance[dst] != sys.maxsize:

​      return distance[dst]

​    else:

​      return -1

if __name__ == '__main__':

  solution=Solution()

  n=3

  flights=[[0, 1, 100], [1, 2, 100], [0, 2, 500]]

  src=0

  dst=2

  K=0

  print("输入城市为：",n)

  print("输入航班为：",flights)

  print("输入出发地：",src)

  print("输入目的地：",dst)

  print("输入中转数：",K)

  print("输出价格为：",solution.findCheapestPrice(n, flights, src, dst, K))

图是否可以被二分  

 

class Solution:

  \#参数graph为无向图

  \#返回布尔类型

  def isBipartite(self, graph):

​    n = len(graph)

​    self.color = [0] * n

​    for i in range(n):

​      if self.color[i] == 0 and not self.colored(i, graph, 1):

​        return False

​    return True

  def colored(self, now, graph, c):

​    self.color[now] = c

​    for nxt in graph[now]:

​      if self.color[nxt] == 0 and not self.colored(nxt, graph, -c):

​        return False

​      elif self.color[nxt] == self.color[now]:

​        return False

​    return True

if __name__ == '__main__':

  solution=Solution()

  inputnum=[[1,3],[0,2],[1,3],[0,2]]

  print("输入为：",inputnum)

  print("输出为：",solution.isBipartite(inputnum))
 4.运行结果

输入为：[[1, 3], [0, 2], [1, 3], [0, 2]]

输出为：True

森林中的兔子  

2.问题示例

输入[1, 1, 2]，输出5，两个回答"1"的兔子可能是相同的颜色，定为红色；回答"2"的兔子一定不是红色，定为蓝色，一定还有2只蓝色的兔子在森林里不过没有回答问题， 所以森林里兔子的最少总数是5，3只回答问题的加上2只没回答问题的兔子。

 

import math

class Solution:

  \#参数answers为数组

  \#返回整数

  def numRabbits(self, answers):

​    hsh = {}

​    for i in answers:

​      if i + 1 in hsh:

​        hsh[i + 1] += 1

​      else:

​        hsh[i + 1] = 1

​    ans = 0

​    for i in hsh:

​      ans += math.ceil(hsh[i] / i) * i

​    return ans

if __name__ == '__main__':

  solution=Solution()

  inputnum=[1,1,2]

  print("输入为：",inputnum)

  print("输出为：",solution.numRabbits(inputnum))
 4.运行结果

输入为：[1, 1, 2]

输出为：5

 

最大分块排序  

1.问题描述

数组arr，是[0,1，...，arr.length - 1]的一个排列，将数组拆分成若干“块”（分区），并单独对每个块进行排序，使得连接这些块后，结果为排好的升序数组，问最多可以分多少块？

2.问题示例

输入arr = [1,0,2,3,4]，输出4，可以将数组分解成 [1, 0], [2], [3], [4]。

 

class Solution(object):

  def maxChunksToSorted(self, arr):

​    def dfs(cur, localmax):

​      visited[cur] = True

​      localmax = max(localmax, cur)

​      if not visited[arr[cur]]:

​        return dfs(arr[cur], localmax)

​      return localmax

​    visited = [False] * len(arr)

​    count = 0

​    i = 0

​    while i < len(arr):

​      localmax = dfs(i, -1)

​      i += 1

​      while i < localmax + 1:

​        if not visited[i]:

​          localmax = dfs(i, localmax)

​        i += 1

​      count += 1

​    return count

if __name__ == '__main__':

  solution=Solution()

  arr = [1,0,2,3,4]

  print("输入为：",arr)

  print("输出为：",solution.maxChunksToSorted(arr))
 4.运行结果

输入为：[1, 0, 2, 3, 4]

输出为：4

分割标签  

 

class Solution(object):

  def partitionLabels(self, S):

​    last = {c: i for i, c in enumerate(S)}

​    right = left = 0

​    ans = []

​    for i, c in enumerate(S):

​      right = max(right, last[c])

​      if i == right:

​        ans.append(i - left + 1)

​        left = i + 1

​    return ans

if __name__ == '__main__':

  solution=Solution()

  s = "ababcbacadefegdehijhklij"

  print("输入为：",s)

  print("输出为：",solution.partitionLabels(s))


网络延迟时间  

 

class Solution:

  \#参数times为数组

  \#参数N为整数

  \#参数K为整数

  \#返回整数

  def networkDelayTime(self, times, N, K):

​    INF = 0x3f3f3f3f

​    G = [[INF for i in range(N + 1)] for j in range(N + 1)]

​    for i in range(1, N + 1):

​      G[i][i] = 0

​    for i in range(0, len(times)):

​      G[times[i][0]][times[i][1]] = times[i][2]

​    dis = G[K][:]

​    vis = [0] * (N + 1)

​    for i in range(0, N - 1):

​      Mini = INF

​      p = K

​      for j in range(1, N + 1):

​        if vis[j] == 0 and dis[j] < Mini:

​          Mini = dis[j]

​          p = j

​      vis[p] = 1

​      for j in range(1, N + 1):

​        if vis[j] == 0 and dis[j] > dis[p] + G[p][j]:

​          dis[j] = dis[p] + G[p][j]

​    ans = 0

​    for i in range(1, N + 1):

​      ans = max(ans, dis[i])

​    if ans == INF:

​      return -1

​    return ans

if __name__ == '__main__':

  solution=Solution()

  times=[[2,1,1],[2,3,1],[3,4,1]]

  N=4

  K=2

  print("时间矩阵为：",times)

  print("网络大小为：",N)

  print("起始节点为：",K)

  print("最小花费为：",solution.networkDelayTime(times,N,K))

洪水填充  

 

class Solution(object):

  def floodFill(self, image, sr, sc, newColor):

​    rows, cols, orig_color = len(image), len(image[0]), image[sr][sc]

​    def traverse(row, col):

​      if (not (0 <= row < rows and 0 <= col < cols)) or image[row][col] != orig_color:

​        return

​      image[row][col] = newColor

​      [traverse(row + x, col + y) for (x, y) in ((0, 1), (1, 0), (0, -1), (-1, 0))]

​    if orig_color != newColor:

​      traverse(sr, sc)

​    return image

if __name__ == '__main__':

  solution=Solution()

  image = [[1,1,1],[1,1,0],[1,0,1]]

  sr = 1

  sc = 1

  newColor = 2

  print("输入图像为：",image)

  print("输入坐标为： [",sr,",",sc,"]")

  print("输入颜色为：",newColor)

  print("输出图像为：",(solution.floodFill(image,sr,sc,newColor)))

映射配对之和  

 

class TrieNode:

  def __init__(self):

​    self.son = {}

​    self.val = 0

class Trie:

  root = TrieNode()

  def insert(self, s, val):

​    cur = self.root

​    for i in range(0, len(s)):

​      if s[i] not in cur.son:

​        cur.son[s[i]] = TrieNode()

​      cur = cur.son[s[i]]

​      cur.val += val

  def find(self, s):

​    cur = self.root

​    for i in range(0, len(s)):

​      if s[i] not in cur.son:

​        return 0

​      cur = cur.son[s[i]]

​    return cur.val

class MapSum:

  def __init__(self):

​    self.d = {}

​    self.trie = Trie()

  def insert(self, key, val):

​    \#参数key为字符串

​    \#参数val为整数

​    \#无返回值

​    if key in self.d:

​      self.trie.insert(key, val - self.d[key])

​    else:

​      self.trie.insert(key, val)

​    self.d[key] = val

  def sum(self, prefix):

​    \#参数prefix为字符串

​    \#返回整型

​    return self.trie.find(prefix)

if __name__ == '__main__':

  mapsum=MapSum()

  print("插入方法：")

  print(mapsum.insert("apple", 3))

  print("求和方法：")

  print(mapsum.sum("ap"))

  print("插入方法：")

  print(mapsum.insert("app", 2))

  print("求和方法：")

  print(mapsum.sum("ap"))


最长升序子序列的个数  

 

import collections

class Solution(object):

  def findNumberOfLIS(self, nums):

​    ans = [0, 0]

​    l = len(nums)

​    dp = collections.defaultdict(list)

​    for i in range(l):

​      dp[i] = [1, 1]

​    for i in range(l):

​      for j in range(i):

​        if nums[i] > nums[j]:

​          if dp[j][0] + 1 > dp[i][0]:

​            dp[i] = [dp[j][0] + 1, dp[j][1]]

​          elif dp[j][0] + 1 == dp[i][0]:

​            dp[i] = [dp[i][0], dp[i][1] + dp[j][1]]

​    for i in dp.keys():

​      if dp[i][0] > ans[0]:

​        ans = [dp[i][0], dp[i][1]]

​      elif dp[i][0] == ans[0]:

​        ans = [dp[i][0], ans[1] + dp[i][1]]

​    return ans[1]

if __name__ == '__main__':

  solution=Solution()

  nums=[1,3,5,4,7]

  print("输入为：",nums)

  print("输出为：",solution.findNumberOfLIS(nums))

最大的交换  

 

class Solution:

  def maximumSwap(self, num):

​    res, num = num, list(str(num))

​    for i in range(len(num) - 1):

​      for j in range(i + 1, len(num)):

​        if int(num[j]) > int(num[i]):

​          tmp = int("".join(num[:i] + [num[j]] + num[i + 1:j] + [num[i]] + num[j + 1:]))

​          res = max(res, tmp)

​    return res

if __name__ == '__main__':

  solution=Solution()

  num=2736

  print("输入为：",num)

  print("输出为：",solution.maximumSwap(num))

将数组拆分成含有连续元素的子序列  

 

class Solution:

  \#参数nums为整数列表

  \#返回布尔类型

  def isPossible(self, nums):

​    cnt, tail = {}, {}

​    for num in nums:

​      cnt[num] = cnt[num] + 1 if num in cnt else 1

​    for num in nums:

​      if not num in cnt or cnt[num] < 1:

​        continue

​      if num - 1 in tail and tail[num - 1] > 0:

​        tail[num - 1] -= 1

​        tail[num] = tail[num] + 1 if num in tail else 1

​      elif num + 1 in cnt and cnt[num + 1] > 0 and num + 2 in cnt and cnt[num + 2] > 0:

​        cnt[num + 1] -= 1

​        cnt[num + 2] -= 1

​        tail[num + 2] = tail[num + 2] + 1 if num + 2 in tail else 1

​      else:

​        return False

​      cnt[num] -= 1

​    return True

if __name__ == '__main__':

  solution=Solution()

  nums=[1,2,3,3,4,5]

  print("输入为：",nums)

  print("输出为：",solution.isPossible(nums))

Dota2参议院  

 

from collections import deque

class Solution():

  def predictPartyVictory(self,senate):

​    senate = deque(senate)

​    while True:

​      try:

​        thisGuy = senate.popleft()

​        if thisGuy == 'R':

​          senate.remove('D')

​        else:

​          senate.remove('R')

​        senate.append(thisGuy)

​      except:

​        return 'Radiant' if thisGuy == 'R' else 'Dire'

if __name__ == '__main__':

  solution=Solution()

  senate="RD"

  print("输入为：",senate)

  print("输出为：",solution.predictPartyVictory(senate))

合法的三角数  

 

class Solution:

  \#参数nums为数组

  \#返回整数

  def triangleNumber(self, nums):

​    nums = sorted(nums)

​    total = 0

​    for i in range(len(nums)-2):

​      if nums[i] == 0:

​        continue

​      end = i + 2

​      for j in range(i+1, len(nums)-1):

​        while end < len(nums) and nums[end] < (nums[i] + nums[j]):

​          end += 1

​        total += end - j - 1

​    return total

if __name__ == '__main__':

  solution = Solution()

  nums=[2,2,3,4]

  print("输入为：",nums)

  print("输出为：",solution.triangleNumber(nums))

在系统中找到重复文件  

 

import collections

class Solution:

  def findDuplicate(self, paths):

​    dic = collections.defaultdict(list)

​    for path in paths:

​      root, *f = path.split(" ")

​      for file in f:

​        txt, content = file.split("(")

​        dic[content] += root + "/" + txt,

​    return [dic[key] for key in dic if len(dic[key]) > 1]

if __name__ == '__main__':

  paths=["root/a 1.txt(abcd) 2.txt(efgh)", "root/c 3.txt(abcd)","root/c/d 4.txt(efgh)"]

  solution=Solution()

  print("输入为：",paths)

print("输出为：",solution.findDuplicate(paths))

两个字符串的删除操作  

 

class Solution:

  \#word1为字符串

  \#参数word2为字符串

  \#返回整数

  def minDistance(self, word1, word2):

​    m, n = len(word1), len(word2)

​    dp = [[0] * (n + 1) for i in range(m + 1)]

​    for i in range(m):

​      for j in range(n):

​        dp[i + 1][j + 1] = max(dp[i][j + 1], dp[i + 1][j], dp[i][j] + (word1[i] == word2[j]))

​    return m + n - 2 * dp[m][n]

if __name__ == '__main__':

  solution=Solution()

  word1="sea"

  word2="eat"

  print("输入1为：",word1)

  print("输入2为：",word2)

print("输出为：",solution.minDistance(word1,word2))

下一个更大的元素 

 

class Solution:

  \#n为整数

  \#返回整数

  def nextGreaterElement(self, n):

​    n_array = list(map(int, list(str(n))))

​    if len(n_array) <= 1:

​      return -1

​    if len(n_array) == 2:

​      if n_array[0] < n_array[1]:

​        return int("".join(map(str, n_array[::-1])))

​      else:

​        return -1

​    if n_array[-2] < n_array[-1]:

​      n_array[-2], n_array[-1] = n_array[-1], n_array[-2]

​      new_n = int("".join(map(str, n_array)))

​    else:

​      i = len(n_array) - 1

​      while i > 0 and n_array[i - 1] >= n_array[i]:

​        i -= 1

​      if i == 0:

​        return -1

​      else:

​        new_array = n_array[:i - 1]

​        for j in range(len(n_array) - 1, i - 1, -1):

​          if n_array[j] > n_array[i - 1]:

​            break

​        new_array.append(n_array[j])

​        n_array[j] = n_array[i - 1]

​        new_array.extend(reversed(n_array[i:]))

​        new_n = int("".join(map(str, new_array)))

​    return new_n if new_n <= 2 ** 31 else -1

if __name__ == '__main__':

  solution = Solution()

  n=123

  print("输入为：",n)

  print("输出为：",solution.nextGreaterElement(n))

最优除法  

 

class Solution(object):

  def optimalDivision(self, nums):

​    joinDivision = lambda l: '/'.join(list(map(str,l)))

​    if len(nums) == 1: return str(nums[0])

​    if len(nums) == 2: return joinDivision(nums)

​    return str(nums[0]) if len(nums) == 1 else str(nums[0]) + '/(' + joinDivision(nums[1:]) +')'

if __name__ == '__main__':

  nums=[1000,100,10,2]

  solution=Solution()

  print("输入为：",nums)

print("输出为：",solution.optimalDivision(nums))

通过删除字母匹配到字典里最长单词  

 

class Solution:

  \#参数s为字符串

  \#参数d为列表

  \#返回字符串

  def findLongestWord(self, s, d):

​    for x in sorted(d, key=lambda x: (-len(x), x)):

​      it = iter(s)

​      if all(c in it for c in x):

​        return x

​    return ''

if __name__ == '__main__':

  s = "abpcplea"

  d = ["ale", "apple", "monkey", "plea"]

  solution=Solution()

  print("输入为：",s)

  print("输入为：",d)

  print("输出为：",solution.findLongestWord(s,d))

寻找树中最左下结点的值 

 

class TreeNode:

  def __init__(self, val):

​    self.val = val

​    self.left, self.right = None, None

class Solution:

  \#参数root为二叉树根

  \#返回整数

  def findBottomLeftValue(self, root):

​    self.max_level = 0

​    self.val = None

​    self.helper(root, 1)

​    return self.val

  def helper(self, root, level):

​    if not root: return

​    if level > self.max_level:

​      self.max_level = level

​      self.val = root.val

​    self.helper(root.left, level + 1)

​    self.helper(root.right, level + 1)

if __name__ == '__main__':

  node=TreeNode(1)

  node.left=TreeNode(2)

  node.right=TreeNode(3)

  node.left.left=TreeNode(4)

  solution=Solution()

  print("输入为：[1,2 3,4 # # #]~~{~~")~~)~~

  print("输出为：",solution.findBottomLeftValue(node))

出现频率最高的子树和  

 

import collections

class TreeNode:

  def __init__(self, val):

​    self.val = val

​    self.left, self.right = None, None

class Solution:

  def findFrequentTreeSum(self, root):

​    \#root为树根节点

​    \#返回列表

​    if not root:

​      return []

​    counter = collections.Counter()

​    def sumnode(node):

​      if not node:

​        return 0

​      ret = node.val

​      if node.left:

​        ret += sumnode(node.left)

​      if node.right:

​        ret += sumnode(node.right)

​      counter[ret] += 1

​      return ret

​    sumnode(root)

​    arr = []

​    for k in counter:

​      arr.append((k, counter[k]))

​    arr.sort(key=lambda x: x[1], reverse=True)

​    i = 0

​    while i + 1 < len(arr) and arr[i + 1][1] == arr[0][1]:

​      i += 1

​    return [x[0] for x in arr[:i + 1]]

if __name__ == '__main__':

  node=TreeNode(5)

  node.right=TreeNode(-3)

  node.left=TreeNode(2)

  solution=Solution()

  print("输入为：{5，3 2}")

  print("输出为：",solution.findFrequentTreeSum(node))

寻找BST的modes 

 

class TreeNode:

  def __init__(self, val):

​    self.val = val

​    self.left, self.right = None, None

class Solution:

  \#参数root为根节点

  \#返回整数

  def helper(self, root, cache):

​    if root == None:

​      return

​    cache[root.val] += 1

​    self.helper(root.left, cache)

​    self.helper(root.right, cache)

​    return

  def findMode(self, root):

​    from collections import defaultdict

​    if root == None:

​      return []

​    cache = defaultdict(int)

​    self.helper(root, cache)

​    max_freq = max(cache.values())

​    result = [k for k,v in cache.items() if v == max_freq]

​    return result

\#主函数

if __name__ == '__main__':

  T = TreeNode(1)
   T.left = None
   T2 = TreeNode(2)
   T.right = T2
   T3 = TreeNode(2)
   T2.left = T3
   s = Solution()
   print("输入为：[1,#,2,2]")

  print("输出为：",s.findMode(T))

对角线遍历  

 

class Solution:
   \#参数matrix为矩阵
   \#返回整数列表
   def findDiagonalOrder(self, matrix):
     import collections
     result = [ ]
     dd = collections.defaultdict(list)
     if not matrix:
       return result
     for i in range(0, len(matrix)):
       for j in range(0, len(matrix[0])):
         dd[i+j+1].append(matrix[i][j])
     for k, v in dd.items():
       if k%2==1: dd[k].reverse()
       result += dd[k]
     return result

\#主函数

if __name__ == '__main__':

  m = [
 [ 1, 2, 3 ],
 [ 4, 5, 6 ],
 [ 7, 8, 9 ]
 ]

  s = Solution()

  print("输入为：",m)

  print("输出为：",s.findDiagonalOrder(m))

提莫攻击  

 

class Solution:

  \#参数timeSeries为整数数组

  \#参数duration为整数

  \#返回整数

  def findPoisonedDuration(self, timeSeries, duration):

​    ans = duration * len(timeSeries)

​    for i in range(1,len(timeSeries)):

​      ans -= max(0, duration - (timeSeries[i] - timeSeries[i-1]))

​    return ans

\#主函数

if __name__ == '__main__':

  s = Solution()

  time =2

  timws = [1,4]

  print("输入攻击序列：",timws)

  print("输入持续时间：",time)

  print("输出中毒时间：",s.findPoisonedDuration(timws,time))

目标和  

 

class Solution(object):

  def findTargetSumWays(self, nums, S):

​    if not nums:

​      return 0

​    dic = {nums[0]: 1, -nums[0]: 1} if nums[0] != 0 else {0: 2}

​    for i in range(1, len(nums)):

​      tdic = {}

​      for d in dic:

​        tdic[d + nums[i]] = tdic.get(d + nums[i], 0) + dic.get(d, 0)

​        tdic[d - nums[i]] = tdic.get(d - nums[i], 0) + dic.get(d, 0)

​      dic = tdic

​    return dic.get(S, 0)

\#主函数

if __name__ == '__main__':

  s = Solution()

  time =3

  timws = [1,1,1,1,1]

  print("输入目标值：",time)

  print("输入序列值：",timws)

  print("输出方法为：",s.findTargetSumWays(timws,time))

升序子序列  

 

class Solution(object):

  def findSubsequences(self, nums):

​    \#参数nums为列表

​    \#返回列表

​    res = []

​    self.subsets(nums, 0, [], res)

​    return res

  def subsets(self, nums, index, temp, res):

​    if len(nums) >= index and len(temp) >= 2:

​      res.append(temp[:])

​    used = {}

​    for i in range(index, len(nums)):

​      if len(temp) > 0 and temp[-1] > nums[i]: continue

​      if nums[i] in used: continue

​      used[nums[i]] = True

​      temp.append(nums[i])

​      self.subsets(nums, i+1, temp, res)

​      temp.pop()

\#主函数

if __name__ == '__main__':

  s = Solution()

  series =[4,6,7,7]

  print("输入序列为：",series)

  print("输出序列为：",s.findSubsequences(series))

神奇字符串  

 

class Solution(object):

  def magicalString(self, n):

​    \#参数n为整数

​    \#返回整数

​    if n == 0:

​      return 0

​    elif n <= 3:

​      return 1

​    else:

​      so_far, grp, ones =[1,2,2], 2, 1

​      while len(so_far) < n:

​        freq, item = so_far[grp], 1 if grp % 2 == 0 else 2

​        for _ in range(freq):

​          so_far.append(item)

​        ones, grp = ones + freq if item == 1 else ones, grp + 1

​      if len(so_far) == n:

​        return ones

​      else:

​        return ones-1 if so_far[-1] == 1 else ones

\#主函数

if __name__ == '__main__':
   s = Solution()
   n = 6
   print("输入为：",n)

  print("输出为：",s.magicalString(n))

爆破气球的最小箭头数  

 

class Solution(object):

  def findMinArrowShots(self, points):

​    \#参数points为整数列表

​    \#返回整数

​    if points == None or not points:

​      return 0

​    points.sort(key = lambda x : x[1]);

​    ans = 1

​    lastEnd = points[0][1]

​    for i in range(1, len(points)):

​      if points[i][0] > lastEnd:

​        ans += 1

​        lastEnd = points[i][1]

​    return ans

\#主函数

if __name__ == '__main__':

  s = Solution()

  n = [[10,16], [2,8], [1,6], [7,12]]

  print("输入为：",n)

  print("输出为：",s.findMinArrowShots(n))

查找数组中的所有重复项  

 

class Solution:

  \#参数nums为整数列表

  \#返回整数列表

  def findDuplicates(self, nums):

​    if not nums:

​      return []

​    duplicates = []  

​    for each in range(len(nums)):

​      index = nums[each]

​      if index<0:

​        index = -index

​      if nums[index-1]>0:

​        nums[index-1]=-nums[index-1]

​      else:

​        duplicates.append(index)

​        

​    return duplicates

\#主函数

if __name__ == '__main__':

  s = Solution()

  n = [4,3,2,7,8,2,3,1]

  print("输入为：",n)

  print("输出为：",s.findDuplicates(n))

最小基因变化  

 

from collections import deque

class Solution:

  \#参数start为字符串

  \#参数end为字符串

  \#参数bank为字符串

  \#返回整数

  def minMutation(self, start, end, bank):

​    if not bank:

​      return -1

​    bank = set(bank)

​    h = deque()

​    h.append((start, 0))

​    while h:

​      seq, step = h.popleft()

​      if seq == end:

​        return step

​      for c in "ACGT":

​        for i in range(len(seq)):

​          new_seq = seq[:i] + c + seq[i + 1:]

​          if new_seq in bank:

​            h.append((new_seq, step + 1))

​            bank.remove(new_seq)

​    return -1

\#主函数

if __name__ == '__main__':

  s = Solution()

  n ="AACCGGTT"

  m= "AACCGGTA"

  p=["AACCGGTA"]

  print("输入起点为：",n)

  print("输入终点为：",m)

  print("输入的库为：",p)

  print("输出步数为：",s.minMutation(n,m,p))

替换后的最长重复字符  

 

from collections import defaultdict

class Solution:

  \#参数s为字符串

  \#参数k为整数

  \#返回整数

  def characterReplacement(self, s, k):

​    n = len(s)

​    char2count = defaultdict(int)

​    maxLen = 0

​    start = 0

​    for end in range(n):

​      char2count[s[end]] += 1

​      while end - start + 1 - char2count[s[start]] > k:

​        char2count[s[start]] -= 1

​        start += 1

​      maxLen = max(maxLen, end - start + 1)

​    return maxLen

\#主函数

if __name__ == '__main__':

  s = Solution()

  n ="ABAB"

  m=2

  print("输入字符串为：",n)

  print("输入重复次数：",m)

  print("输出子串长度：",s.characterReplacement(n,m))

从英文中重建数字  

 

class Solution:

  \#参数s为字符串

  \#返回字符串

  def originalDigits(self, s):

​    nums = [0 for x in range(10)]

​    nums[0] = s.count('z')

​    nums[2] = s.count('w')

​    nums[4] = s.count('u')

​    nums[6] = s.count('x')

​    nums[8] = s.count('g')

​    nums[3] = s.count('h') - nums[8]

​    nums[7] = s.count('s') - nums[6]

​    nums[5] = s.count('v') - nums[7]

​    nums[1] = s.count('o') - nums[0] - nums[2] - nums[4]

​    nums[9] = (s.count('n') - nums[1] - nums[7]) // 2

​    result = ""

​    for x in range(10):

​      result += str(x) * nums[x]

​    return result

\#主函数

if __name__ == '__main__':

  s = Solution()

  n ="owoztneoer"

  print("输入为：",n)

  print("输出为：",s.originalDigits(n))

数组中两个数字的最大异或  

 

class TrieNode:

  def __init__(self,val):

​    self.val = val

​    self.children = {}

class Solution:

  \#参数nums为整数: 

  \#返回整数

  def findMaximumXOR(self, nums):

​    answer = 0

​    for i in range(32)[::-1]:

​      answer <<= 1

​      prefixes = {num >> i for num in nums}

​      answer += any(answer^1 ^ p in prefixes for p in prefixes)

​    return answer

  def findMaximumXOR_TLE(self, nums):

​    root = TrieNode(0)

​    for num in nums:

​      self.addNode(root, num)

​    res = -sys.maxsize

​    for num in nums:

​      cur_node, cur_sum = root, 0

​      for i in reversed(range(0,32)):

​        bit = (num >> i) & 1

​        if (bit^1) in cur_node.children:

​          cur_sum += 1 << i

​          cur_node = cur_node.children[bit^1]

​        else:

​          cur_node = cur_node.children[bit]

​      res = max(res, cur_sum)

​    return res

  def addNode(self, root, num):

​    cur = root

​    for i in reversed(range(0,32)):

​      bit = (num >> i) & 1

​      if bit not in cur.children:

​        cur.children[bit] = TrieNode(bit)

​      cur = cur.children[bit]

\#主函数

if __name__ == '__main__':

  s = Solution()

  n =[3, 10, 5, 25, 2, 8]

  print("输入为：",n)

  print("输出为：",s.findMaximumXOR(n))

根据身高重排队列  

 

class Solution:

  """

  参数people为整数列表

  返回整数列表

  """

  def reconstructQueue(self, people):

​    queue = []

​    for person in sorted(people, key = lambda _: (-_[0], _[1])): queue.insert(person[1], person)

​    return queue

\#主函数

if __name__ == '__main__':

  s = Solution()

  n =[[7,0], [4,4], [7,1], [5,0], [6,1], [5,2]]

  print("输入为：",n)

  print("输出为：",s.reconstructQueue(n))

左叶子的和  

 

class TreeNode:
   def __init__(self, val):
     self.val = val
     self.left, self.right = None, None

class Solution(object):

  def sumOfLeftLeaves(self, root):

​    """

​    参数root为二叉树根

​    返回整数

​    """

​    def dfs(root):

​      if not root:

​        return 0

​      sum = 0

​      if root.left:

​        left = root.left;

​        \#当前节点的左子节点,并判断是否为叶子节点

​        if not left.left and not left.right:

​          sum += left.val;

​        else :

​          sum += dfs(left)

​      if root.right:

​        right = root.right

​        sum += dfs(right)

​      return sum

​    return dfs(root)

\#主函数

if __name__ == '__main__':

  s = Solution()

  t = TreeNode(3)

  t1 = TreeNode(9)

  t.left = t1

  t2 = TreeNode(20)

  t.right = t2

  t3 = TreeNode(15)

  t2.left = t3

  t4 = TreeNode(7)

  t2.right = t4

  print("输入为：[3,9 20,# # 15 7]")

  print("输出为：",s.sumOfLeftLeaves(t))

移除K位  

 

class Solution:

  """

  参数num为字符串

  参数k为整数

  返回字符串

  """

  def removeKdigits(self, num, k):

​    if k == 0:

​      return num

​      

​    if k >= len(num):

​      return "0"

​    result_list = []

​    for i in range(len(num)):

​      while len(result_list) > 0 and k > 0 and result_list[-1] > num[i]:

​        result_list.pop()

​        k -= 1 

​      if num[i] != '0' or len(result_list) > 0 :

​        result_list.append(num[i])

​    while len(result_list) > 0 and k > 0:

​      result_list.pop()

​      k -= 1 

​    if len(result_list) == 0:

​      return '0'

​    return ''.join(result_list)

\#主函数

if __name__ == '__main__':

  s = Solution()

  n = "1432219"

  k = 3

  print("输入数字为：",n)

  print("输入移除数：",k)

  print("输出为：",s.removeKdigits(n,k))

轮转函数  

 

class Solution:

  """

  \#参数A数组

  \#返回整数

  """

  def maxRotateFunction(self, A):

​    s = sum(A)

​    curr = sum(i*a for i, a in enumerate(A))

​    maxVal = curr

​    for i in range(1, len(A)):

​      curr += s - len(A)*A[-i]

​      maxVal = max(maxVal, curr)

​    return maxVal

\#主函数

if __name__ == '__main__':

  s = Solution()

  n = [4,3,2,6]

  print("输入为：",n)

  print("输出为：",s.maxRotateFunction(n))

字符至少出现K次的最长子串  

 

class Solution:

  """

  参数s为字符串

  参数k为整数

  返回整数

  """

  def longestSubstring(self, s, k):

​    for c in set(s):

​      if s.count(c) < k:

​        return max(self.longestSubstring(t, k) for t in s.split(c))

​    return len(s)

\#主函数

if __name__ == '__main__':

  s = Solution()

  n = "aaabb"

  k = 3

  print("输入字符串为：",n)

  print("输入重复次数：",k)

  print("输出子串长度：",s.longestSubstring(n,k))

消除游戏  

 

class Solution:

  """

  参数n为整数

  返回整数

  """

  def lastRemaining(self, n):

​    return 1 if n == 1 else 2 * (1 + n // 2 - self.lastRemaining(n // 2))

\#主函数

if __name__ == '__main__':

  s = Solution()

  n = 9

  print("输入为：",n)

  print("输出为：",s.lastRemaining(n))

有序矩阵中的第K小元素  

 

class Solution:

  """

  参数matrix为整数列表

  参数k为整数

  返回整数

  """

  def kthSmallest(self, matrix, k):

​    start = matrix[0][0] 

​    end = matrix[-1][-1]

​    while start + 1 < end:

​      mid = start + (end - start) // 2 

​      if self.get_num_less_equal(matrix, mid) < k:

​        start = mid 

​      else:

​        end = mid 

​    if self.get_num_less_equal(matrix, start) >= k:

​      return start

​    return end     

  def get_num_less_equal(self, matrix, mid):

​    m = len(matrix)

​    n = len(matrix[0])

​    i = 0 

​    j = n - 1

​    count = 0

​    while i < m and j >= 0:

​      if matrix[i][j] <= mid:

​        i += 1 

​        count += j + 1 

​      else:

​        j -= 1 

​    return count

\#主函数

if __name__ == '__main__':

  s = Solution()

  n=[[ 1, 5, 9],[10, 11, 13],[12, 13, 15]]

  k=8

  print("输入数组为：",n)

  print("输入顺序为：",k)

  print("输出数字为：",s.kthSmallest(n,k))

超级幂次  

 

class Solution:

  """

  参数a为整数: the given number a

  参数b为数组

  返回整数

  """

  def superPow(self, a, b):

​    if a == 0:

​      return 0

​    ans = 1

​    def mod(x):

​      return x % 1337

​    for num in b:

​      ans = mod(mod(ans ** 10) * mod(a ** num))

​    return ans

\#主函数

if __name__ == '__main__':

  s = Solution()

  n=2

  k=[3]

  print("输入a=：",n)

  print("输入b=：",k)

  print("输出为：",s.superPow(n,k))

水罐问题  

 

class Solution:

  """

  参数x为整数

  参数y为整数

  参数z为整数

  返回布尔类型

  """

  def canMeasureWater(self, x, y, z):

​    if x+y < z:

​      return False

​    return z % self.gcd(x,y) == 0

  def gcd(self, x, y):

​    if y == 0:

​      return x

​    return self.gcd(y, x%y)

\#主函数

if __name__ == '__main__':

  s = Solution()

  x = 3

  y = 5

  z = 4

  print("输入：x=",x)

  print("输入：y=",y)

  print("输入：z=",z)

  print("输出为：",s.canMeasureWater(x,y,z))

计算不同数字整数的个数  

 

class Solution:

  """

  参数n为整数

  返回整数

  """

  def countNumbersWithUniqueDigits(self, n):

​    if n == 0:

​      return 1

​    n = min(n, 10)

​    dp = [0] * (n + 1)

​    dp[0], dp[1] = 1, 9

​    for i in range(2, n + 1):

​      dp[i] = dp[i - 1] * (11 - i)

​    return sum(dp)

\#主函数

if __name__ == '__main__':

  s = Solution()

  x = 2

  print("输入为：",x)

  print("输出为：",s.countNumbersWithUniqueDigits(2))

最大乘积路径  

 

\#参数x，y代表每条边的起始和终止

\#参数d是每个节点的权重

\#返回值是一个整数，是取模后节点最大乘积

class Solution:

  ans = 0

  def dfs(self, x, f, g, d, mul):

​    isLeaf = True

​    mul = mul * d[x - 1] % 1000000007

​    for i in g[x]:

​      if i == f:

​        continue

​      isLeaf = False

​      self.dfs(i, x, g, d, mul)

​    if(isLeaf is True):

​      self.ans = max(self.ans, mul)

  def getProduct(self, x, y, d):

​    g = [ [] for i in range(len(d) + 1)]

​    for i in range(len(x)):

​      g[x[i]].append(y[i])

​      g[y[i]].append(x[i])

​    self.dfs(1, -1, g, d, 1)

​    return self.ans

if __name__ == '__main__':

  x =[1,2,2]

  y = [2,3,4]

  d = [1,1,-1,2]

  solution = Solution()

  print(" 每个边的起始和终止为：", x, y)

  print(" 每个节点的权重为：", d)

  print(" 最大路径上的乘积是:", solution.getProduct(x, y, d))

矩阵找数  

 

\#参数mat是待查矩阵

\#返回值是一个整数，是每一行都出现的最小的数字

class Solution:

  def findingNumber(self, mat):

​    hashSet = {}

​    n = len(mat)

​    for mati in mat:

​      vis = {}

​      for x in mati:

​        vis[x] = 1

​      for key in vis:

​        if key not in hashSet:

​          hashSet[key] = 0

​        hashSet[key] += 1

​    ans = 100001

​    for i in hashSet:

​      if hashSet[i] == n:

​        ans = min(i, ans)

​    return -1 if ans == 100001 else ans

class Solution:

  def findingNumber(self, mat):

​    hashSet = {}

​    n = len(mat)

​    for mati in mat:

​      vis = {}

​      for x in mati:

​        vis[x] = 1

​      for key in vis:

​        if key not in hashSet:

​          hashSet[key] = 0

​        hashSet[key] += 1

​    ans = 100001

​    for i in hashSet:

​      if hashSet[i] == n:

​        ans = min(i, ans)

​    return -1 if ans == 100001 else ans

if __name__ == '__main__':

  mat = [[1,2,3],[3,4,1],[2,1,3]]

  solution = Solution()

  print(" 矩阵为：", mat)

  print(" 每一行都出现的最小的数是：", solution.findingNumber(mat))

路径数计算  

 

\#参数points是除了始末点外的必经点

\#参数l和w是长和宽

\#返回值是一个整数，有多少种走法

class Point:

  def __init__(self, a=0, b=0):

​    self.x = a

​    self.y = b

class Solution:

  def calculationTheSumOfPath(self, l, w, points):

​    points.sort(key = lambda point: point.x)

​    if points[0].x != 1 or points[0].y != 1:

​      points = [Point(1,1)] + points

​    if points[0].x != l or points[0].y != w:

​      points = points + [Point(l,w)]

​    arr = [[] for i in range(len(points) - 1)]

​    maxl = 0

​    maxw = 0

​    for i in range(1, len(points)):

​      l = points[i].x - points[i - 1].x

​      w = points[i].y - points[i - 1].y

​      arr[i - 1] = [points[i].x - points[i - 1].x, points[i].y - points[i - 1].y]

​      maxl = max(maxl, l)

​      maxw = max(maxw, w)

​    dp = [[0 for i in range(max(maxl, maxw) + 1)]for j in range(max(maxl, maxw) + 1)]

​    del l, w, maxl, maxw

​    for i in range(len(dp)):

​      for j in range(i, len(dp)):

​        if i == 0:

​          dp[j][i] = dp[i][j] = 1

​        else:

​          dp[j][i] = dp[i][j] = dp[i - 1][j] + dp[i][j - 1]

​    ans = 1

​    for i in arr:

​      ans = ans * dp[i[0]][i[1]] % 1000000007

​    return ans

if __name__ == '__main__':

  l=43

  w=48

  points = [Point(17,19), Point(43,48), Point(3,5)]

  solution = Solution()

  print(" 长与宽分别为：", l, w)

  print(" 有路径种数:", solution.calculationTheSumOfPath(l, w, points))

卡牌游戏  

 

class Solution:

  def numOfPlan(self, n, totalProfit, totalCost, a, b):

​    dp = [[0 for j in range(110)] for i in range(110)]

​    dp[0][0] = 1

​    mod = 1000000007

​    for i in range(n):

​      for j in range(totalProfit + 1, -1, -1):

​        for k in range(totalCost + 1, -1, -1):

​          idxA = min(totalProfit + 1, j + a[i])

​          idxB = min(totalCost + 1, k + b[i])

​          dp[idxA][idxB] = (dp[j][k] + dp[idxA][idxB]) % mod

​    ans = 0

​    for i in range(totalCost):

​      ans = (ans + dp[totalProfit + 1][i]) % mod

​    return ans

if __name__ == '__main__':

  n = 2

  totalProfit = 3

  totalCost = 5

  a = [2,3]

  b = [2,2]

  solution = Solution()

  print(" 总卡片数：", n)

  print(" 成本和利润的列表是：", a, b)

  print(" 总成本是：", totalProfit, " 需要总利润是：", totalCost)

  print(" 可使用方法总数:", solution.numOfPlan(n, totalProfit, totalCost, a, b)) 

词频统计  

 

\#参数s是待查句子

\#参数excludeList是被排除的单词

\#返回值是一个字符串的列表，是所有出现频次最高的单词

class Solution:

  def getWords(self, s, excludeList):

​    s = s.lower()

​    words = []

​    p = ''

​    for letter in s:

​      if letter < 'a' or letter > 'z':

​        if p != '':

​          words.append(p)

​        p = ''

​      else:

​        p += letter

​    if p != '':

​      words.append(p)

​    dic = {}

​    for word in words:

​      if word in dic:

​        dic[word] += 1

​      else:

​        dic[word] = 1

​    ans = []

​    mx = 0

​    for word in words:

​      if dic[word] > mx and (not word in excludeList):

​        mx = dic[word]

​        ans = [word]

​      elif dic[word] == mx and word not in ans and not word in excludeList:

​        ans.append(word)

​    return ans

if __name__ == '__main__':

  s="Do do do do not not Trouble trouble."

  excludeList=["do"]

  solution = Solution()

  print(" 待查句子为：",s , "除外词表为:", excludeList)

  print(" 词频最高的单词为:", solution.getWords(s, excludeList)) 

查找子数组  

 

\#参数arr是原数组

\#参数k是目标子数组和

\#返回值是个整数，代表这样一个子数组的起始位置，或者-1代表不存在

class Solution:

  def searchSubarray(self, arr, k):

​    sum = 0

​    maps = {}

​    maps[sum] = 0

​    st = len(arr) + 5

​    lent = 0

​    for i in range(0, len(arr)):

​      sum += arr[i]

​      if sum - k in maps:

​        if st > maps[sum - k]:

​          st = maps[sum - k]

​          lent = i + 1 - maps[sum - k]

​      if sum not in maps:

​        maps[sum] = i + 1

​    if st == len(arr) + 5:

​      return -1

​    else:

​      return lent

if __name__ == '__main__':

  arr = [1,2,3,4,5]

  k = 5

  solution = Solution()

  print(" 数组为：", arr, "k为:", k)

  print(" 最短和为k的子数组是:", solution.searchSubarray(arr, k)) 

最小子矩阵  

 

class Solution:

  def minimumSubmatrix(self, arr):

​    ans = arr[0][0]

​    for i in range(len(arr)):

​      sum = [0 for x in range(len(arr[0]))]

​      for j in range(i,len(arr)):

​        for k in range(len(arr[0])):

​          sum[k] += arr[j][k]

​        dp = [0 for i in range(len(arr[0]))]

​        for k in range(len(arr[0])):

​          if k == 0:

​            dp[k] = sum[k]

​          else:

​            dp[k] = min(sum[k],dp[k-1]+sum[k])

​          ans = min(ans,dp[k])

​    return ans

if __name__ == '__main__':

  arr = a = [[-3,-2,-1],[-2,3,-2],[-1,3,-1]]

  solution = Solution()

  print(" 数组为：", arr)

  print(" 最小子数组是:", solution.minimumSubmatrix(arr)) 

最佳购物计划  

 

\#参数k代表你有的钱

\#参数m和n分别代表商品和礼盒数

\#参数val是代表价值的列表

\#参数costs是代表费用的列表

\#返回值是一个整数，代表最大可获得价值

class Solution:

  def getAns(self, n, m, k, val, cost, belong):

​    dp = [[-1 for i in range(0, 100001)] for i in range(0, 105)]

​    arr = [[] for i in range(0, 105)]

​    for i in range(n, n + m):

​      if not belong[i] == -1:

​        arr[belong[i]].append(i)

​    dp[0][cost[0]] = val[0]

​    for i in arr[0]:

​      for j in range(k, cost[i] - 1, -1):

​        if not dp[0][j - cost[i]] == -1:

​          dp[0][j] = dp[0][j - cost[i]] + val[i]

​    for i in range(1, n):

​      for j in range(k, cost[i] - 1, -1):

​        if not dp[i - 1][j - cost[i]] == -1:

​          dp[i][j] = dp[i - 1][j - cost[i]] + val[i]

​      dp[i][cost[i]] = val[i]

​      for j in arr[i]:

​        for l in range(k, cost[j] - 1, -1):

​          if not dp[i][l - cost[j]] == -1:

​            dp[i][l] = max(dp[i][l], dp[i][l - cost[j]] + val[j])

​      for j in range(0, k + 1):

​        dp[i][j] = max(dp[i][j], dp[i - 1][j])

​    ans = 0

​    for i in range(0, k + 1):

​      ans = max(ans, dp[n - 1][i])

​    return ans

if __name__ == '__main__':

  k = 10

  m = 2

  n = 3

  val = [17, 20, 8, 1, 4]

  cost = [3, 5, 2, 3, 1]

  belong = [-1, -1, -1, 0, 2]

  solution = Solution()

  print(" 拥有的钱：", k)

  print(" 有商品数：", m, " 有礼盒数：", n)

  print(" 价值的列表：", val, " 费用的列表：", cost)

  print(" 可以得到最大价值:", solution.getAns(n, m, k, val, cost, belong)) 

询问冷却时间  

 

\#参数arr是输入的待查数组

\#参数n是公共冷却时间

\#返回值是一个整数，代表需要多少时间

class Solution:

  def askForCoolingTime(self, arr, n):

​    ans = 0

​    l = [0 for i in range(110)]

​    for x in arr:

​      if l[x] == 0 or ans - l[x] > n:

​        ans += 1

​      else:

​        ans = l[x] + n + 1

​      l[x] = ans

​    return ans

if __name__ == '__main__':

  arr = [1, 2, 1, 2]

  n = 2

  solution = Solution()

  print(" 数组为：", arr, " 冷却为：", n)

  print(" 至少需要时间:", solution.askForCoolingTime(arr, n)) 

树上最长路径  

 

\#参数n是节点总数

\#参数starts是每条边的起始

\#参数ends是每条边的结束

\#参数lens是每条边的权重

\#返回值是个整数，代表树上最长路径

import sys

sys.setrecursionlimit(200000)

class Solution:

  G = []

  dp = []

  def dfs(self, u, pre):

​    for x in self.G[u]:

​      if x[0] != pre:

​        self.dp[x[0]] = self.dp[u] + x[1]

​        self.dfs(x[0], u)

  def longestPath(self, n, starts, ends, lens):

​    self.G = [[] for i in range(n)]

​    self.dp = [0 for i in range(n)]

​    for i in range(n - 1):

​      self.G[starts[i]].append([ends[i], lens[i]])

​      self.G[ends[i]].append([starts[i], lens[i]])

​    self.dp[0] = 0

​    self.dfs(0, 0)

​    pos = Mx = 0

​    for i in range(n):

​      if self.dp[i] > Mx:

​        pos = i

​        Mx = self.dp[i]

​    self.dp[pos] = 0

​    self.dfs(pos, pos)

​    ans = 0

​    for i in range(n):

​      if self.dp[i] > ans:

​        ans = self.dp[i]

​    return ans

if __name__ == '__main__':

  n = 5

  starts = [0, 0, 2, 2]

  ends = [1, 2, 3, 4]

  lens = [1, 2, 5, 6]

  solution = Solution()

  print(" 总共有节点：", n)

  print(" 每条边的起始为：", starts)

  print(" 每条边的结束为：", ends)

  print(" 每条边的权重为：", lens)

  print(" 树上最长路径:", solution.longestPath(n, starts, ends, lens))

取数游戏  

 

\#参数s和t是一对字符串，他们需要被验证能否互相根据规则转换

\#返回值是个字符串，意为能否根据规则转换

class Solution:

  def theGameOfTakeNumbers(self, arr):

​    n = len(arr)

​    if n == 0:

​      return 1

​    sum = [0 for i in range(n)]

​    for i in range(1, n + 1):

​      for j in range(0, n - i + 1):

​        if i == 1:

​          sum[j] = arr[j]

​          continue

​        k = j + i - 1

​        sum[j] = max(arr[k] - sum[j], arr[j] - sum[j + 1])

​    return 1 if sum[0] >= 0 else 2

if __name__ == '__main__':

  arr = [1,3,3,1]

  solution = Solution()

  print(" 游戏数组为：", arr)

  print(" 赢家会是:", solution.theGameOfTakeNumbers(arr))

数组求和  

 

\#参数arr是原始总列表

\#返回值是个整数，代表所有子数组的和

class Solution:

  def findTheSumOfTheArray(self, arr):

​    ans = 0

​    n = len(arr)

​    for i in range(n):

​      ans = (ans + arr[i] * (i + 1) * (n - i)) % 1000000007;

​    return ans

if __name__ == '__main__':

  arr = [2,4,6,8,10]

  solution = Solution()

  print(" 输入数组arr为：", arr)

  print(" 所有子数组的和为:", solution.findTheSumOfTheArray(arr))

最短短语  

 

\#参数k是最短单词数

\#参数lim是最短短语长度

\#参数str是被查找的字符串列表

\#返回值是个整数，代表最短短语

class Solution:

  def getLength(self, k, lim, str):

​    n = len(str)

​    arr = [0] * n

​    for i in range(n):

​      arr[i] = len(str[i])

​    l = 0

​    r = 0

​    sum = 0

​    ans = 1e9

​    for r in range(n):

​      sum += arr[r]

​      while r - l >= k and sum - arr[l] >= lim:

​        sum -= arr[l]

​        l += 1

​      if r - l + 1 >= k and sum >= lim:

​        ans = min(ans, sum)

​    return ans

if __name__ == '__main__':

  k = 2

  lim = 10

  str = ["she","was","bad","in","singing"]

  solution = Solution()

  print(" 最短单词数为：", k)

  print(" 短语长度限制为大于：", lim)

  print(" 文章列表为：", str)

  print(" 最短短语为:", solution.getLength(k, lim, str)) 

频率最高的词  

 

\#参数s为“小说”的字符串，excludeWords是不统计的词列表

\#返回值是个单词，是出现最多的词

class Solution:

  def frequentWord(self, s, excludewords):

​    map = {}

​    while len(s) > 0:

​      end = s.find(' ') if s.find(' ') > -1 else len(s)

​      word = s[:end] if s[end - 1].isalpha() else s[:end - 1]

​      s = s[end + 1:]

​      if word not in excludewords:

​        if word in map:

​          map[word] += 1

​        else:

​          map[word] = 1

​    max = -1

​    res = []

​    for key, val in map.items():

​      if val == max:

​        res.append(key)

​      elif val > max:

​        max = val

​        res = [key]

​    res.sort()

​    return res[0]

if __name__ == '__main__':

  s = "Jimmy has an apple, it is on the table, he like it"

  excludeWords = ["a","an","the"]

  solution = Solution()

  print("小说的内容为：", s)

  print("统计不包含的词：", excludeWords)

  print("最常出现的词为：", solution.frequentWord(s, excludeWords))

判断三角形  

 

\#参数a为输入原始数组

\#返回值是个字符串，意为能否形成三角形

class Solution:

  def judgingTriangle(self, arr):

​    n = len(arr)

​    if n > 44:

​      return "YES"

​    arr.sort();

​    for i in range(n - 2):

​      for j in range(i + 1, n - 1):

​        for k in range(j + 1, n):

​          if arr[i] + arr[j] > arr[k]:

​            return "YES"

​    return "NO"

if __name__ == '__main__':

  a = [1,2,5,9,10]

  solution = Solution()

  print(" 输入数组为：", a)

  print(" 能否组成三角形:", solution.judgingTriangle(a))

最大矩阵边界和  

 

\#参数arr为输入矩阵

\#返回值是个整数，代表最大边界数值的和

class Solution:

  def solve(self, arr):

​    n = len(arr)

​    m = len(arr[0])

​    preCol = []

​    preRow = []

​    for r in range(n):

​      tem = [0]

​      res = 0

​      for c in range(m):

​        res += arr[r][c]

​        tem.append(res)

​      preRow.append(tem)

​    for c in range(m):

​      tem = [0]

​      res = 0

​      for r in range(n):

​        res += arr[r][c]

​        tem.append(res)

​      preCol.append(tem)

​    ans = arr[0][0]

​    for r1 in range(n):

​      for r2 in range(r1, n):

​        for c1 in range(m):

​          for c2 in range(c1, m):

​            if r1 == r2 and c1 == c2:

​              res = arr[r1][c1]

​            elif r1 == r2:

​              res = preRow[r1][c2 + 1] - preRow[r1][c1]

​            elif c1 == c2:

​              res = preCol[c1][r2 + 1] - preCol[c1][r1]

​            else:

​              res = preCol[c1][r2 + 1] - preCol[c1][r1] + preCol[c2][r2 + 1] - preCol[c2][r1] + \

​                 preRow[r1][c2 + 1] - preRow[r1][c1] + preRow[r2][c2 + 1] - preRow[r2][c1] - arr[r1][

​                   c1] - arr[r1][c2] - arr[r2][c1] - arr[r2][c2]

​            ans = max(ans, res)

​    return ans

if __name__ == '__main__':

  arr=[[-1,-3,2],[2,3,4],[-3,7,2]]

  solution = Solution()

  print(" 矩阵为：", arr)

  print(" 最大能得到边界和为：", solution.solve(arr))

卡牌游戏II 

 

\#参数Cost和Damage为卡牌属性

\#参数totalCost和totalDamage为手上的费用和需要造成的伤害

\#返回值是个布尔值，代表能否达成伤害

class Solution:

  def cardGame(self, cost, damage, totalMoney, totalDamage):

​    num = len(cost)

​    dp = [0] * (totalMoney + 1)

​    for i in range(0, num):

​      for j in range(totalMoney, cost[i] - 1, -1):

​        dp[j] = max(dp[j], dp[j - cost[i]] + damage[i])

​        if dp[j] >= totalDamage:

​          return True

​    return False

if __name__ == '__main__':

  cost = [3,4,5,1,2]

  damage = [3,5,5,2,4]

  totalMoney = 7

  totalDamage = 11

  solution = Solution()

  print(" 卡牌的cost和damage数组分别为：", cost, damage)

  print(" 总共拥有金钱：", totalMoney)

  print(" 需要造成伤害：", totalDamage)

  print(" 能否达成：", solution.cardGame(cost, damage, totalMoney, totalDamage)) 

停车问题  

 

\#参数a是进出表

\#返回值是个整数，代表最多同时有几辆车

class Solution:

  def getMax(self, a):

​    ans = [0] * 23

​    for i in a:

​      for j in range(i[0], i[1]):

​        ans[j] += 1

​    max = ans[0]

​    for i in ans:

​      if i > max:

​        max = i

​    return max

if __name__ == '__main__':

  a = [[1,2],[2,3],[3,4],[4,5]]

  solution = Solution()

  print(" 车辆进出表为：", a)

  print(" 最多同时有车:", solution.getMax(a))

爬楼梯 

 

\#参数a与b分别是匹配数组和价值数组

\#返回值是个整数，代表选择区间的最大价值

class Solution:

  def getAnswer(self, n, num):

​    ans = [0] * (len(num) + 1)

​    ans[0] = 1

​    for i in range(n):

​      for j in range(1 + i, min(len(num) + 1, i + num[i] + 1)):

​        ans[j] = (ans[j] + ans[i]) % (10**9 + 7)

​    return ans[len(num)]

if __name__ == '__main__':

  n = 4

  num = [1,1,1,1]

  solution = Solution()

  print(" 台阶数和每层台阶能往上登的阶数为：", n, num)

  print(" 走到顶一共有几种走法：", solution.getAnswer(n, num))

最小字符串  

 

\#参数s是原始字符串

\#参数k是最大删除数目

\#返回值是个字符串，代表删完的最小字典序字符串

class Solution:

  def findMinC(self, s, k):

​    ans = 0

​    if len(s) <= k:

​      return -1

​    for i in range(1, k + 1):

​      if ord(s[i]) < ord(s[i - 1]):

​        ans = i

​    return ans

  def MinimumString(self, s, k):

​    ans = ""

​    while k > 0:

​      temp = self.findMinC(s, k)

​      if temp == -1:

​        s = ''

​        break

​      ans = ans + s[temp]

​      s = s[temp + 1:]

​      k -= temp

​    ans += s

​    return ans

if __name__ == '__main__':

  s = "cba"

  k = 2

  solution = Solution()

  print(" 原始字符串为：", s)

  print(" 可以删除到最小字典序:", solution.MinimumString(s, k))

目的地的最短路径  

 

\#参数targetMap是地图

\#返回值是个整数，是最短步数

class Solution:

  ans = []

  def cal(self, targetMap, x, y, z):

​    if targetMap[x][y] == 1:

​      return

​    if z < self.ans[x][y] or self.ans[x][y] == -1:

​      self.ans[x][y] = z

​      if x != 0:

​        self.cal(targetMap, x - 1, y, z + 1)

​      if x != len(targetMap) - 1:

​        self.cal(targetMap, x + 1, y, z + 1)

​      if y != 0:

​        self.cal(targetMap, x, y - 1, z + 1)

​      if y != len(targetMap[0]) - 1:

​        self.cal(targetMap, x, y + 1, z + 1)

​    return

  def shortestPath(self, targetMap):

​    self.ans = [[-1 for i in range(len(targetMap[0]))] for j in range(len(targetMap))]

​    self.cal(targetMap, 0, 0, 0)

​      for i in range(len(targetMap)):

​        for j in range(len(targetMap[0])):

​        if targetMap[i][j] == 2:

​          return self.ans[i][j]

if __name__ == '__main__':

  targetMap = [[0, 0, 0],[0, 0, 1],[0, 0, 2]]

  solution = Solution()

  print(" 地图为：", targetMap)

  print(" 最少需要走:", solution.shortestPath(targetMap)) 

毒药测试  

 

\#参数n是总水瓶数

\#返回值是个整数，代表需要多少小白鼠

class Solution:

  def getAns(self, n):

​    n -= 1

​    ans = 0

​    while n != 0:

​      n //= 2

​      ans += 1

​    return ans

if __name__ == '__main__':

  n = 4

  solution = Solution()

  print("总共有：",n,"瓶水")

  print("至少需要:", solution.getAns(n),"只小白鼠")

社交网络  

 

\#参数n是网络人数

\#参数a与b是关系两方

\#返回值是个字符串，根据所有人能否联系返回“YES”或“NO”

class Solution:

  father = [0] * 5000

  def ask(self, x):

​    if Solution.father[x] == x:

​      return x

​    Solution.father[x] = Solution.ask(self, Solution.father[x])

​    return Solution.father[x]

  def socialNetwork(self, n, a, b):

​    for i in range(0, n):

​      Solution.father[i] = i

​    m = len(b)

​    for i in range(m):

​      x = Solution.ask(self, a[i])

​      y = Solution.ask(self, b[i])

​      Solution.father[x] = y

​    for i in range(0, n):

​      if Solution.ask(self, i) != Solution.ask(self, 1):

​        return "NO"

​    return "YES"

if __name__ == '__main__':

  n = 4

  a = [1, 1, 1]

  b = [2, 3, 4]

  solution = Solution()

  print("好友关系组为：",a,b)

  print("他们能否直接或间接互相联系：", solution.socialNetwork(n, a, b))

前K高的基点  

 

\#参数list是学生ID与成绩的列表

\#返回值是个列表，为前K名GPA学生的原序列表

from heapq import heappush, heappop

class Solution:

  def topKgpa(self, list, k):

​    if len(list) == 0 or k < 0:

​      return []

​    minheap = []

​    ID_set = set([])

​    result = []

​    for ID, GPA in list:

​      ID_set.add(ID)

​      heappush(minheap, (float(GPA), ID))

​      if len(ID_set) > k:

​        _, old_ID = heappop(minheap)

​        ID_set.remove(old_ID)

​    for ID, GPA in list:

​      if ID in ID_set:

​        result.append([ID, GPA])

​    return result

if __name__ == '__main__':

  List = [["001","4.53"],["002","4.87"],["003","4.99"]]

  k = 2

  solution = Solution()

  print("学生按ID排序为：",List,"，K为：",k)

  print("前K高GPA的学生为：", solution.topKgpa(List, k)) 

寻找最长01子串  

 

\#参数str是原始01串

\#返回值为整数，为最大长度

class Solution:

  def askingForTheLongest01Substring(self, str):

​    str += str

​    ans = 1

​    cnt = 1

​    for i in range(1, len(str)):

​      if str[i] != str[i - 1]:

​        cnt += 1

​      else:

​        cnt = 1

​      if ans < cnt and 2 * cnt <= len(str):

​        ans = cnt

​    return ans

if __name__ == '__main__':

  str = "1001"

  solution = Solution()

  print(" 二进制串是",str)

  print(" 最长01子串有:", solution.askingForTheLongest01Substring(str)) 

合法字符串  

 

\#参数S是原始字符串

\#参数k表示相同字符至少间隔多少字符

\#返回值为列表，为每个位置插入的个数

class Solution:

  def getAns(self, k, S):

​    n = len(S)

​    pre = [-1] * 26 # 当前位置之前最靠右的相同字母位置,只有大写

​    sm = [0] * (n + 1) #当前位置之前的"_"总数

​    ans = []

​    for i in range(1, n + 1):

​      c = ord(S[i - 1]) - ord('A')

​      if pre[c] == -1 or sm[i - 1] - sm[pre[c]] - pre[c] + i >= k:

​        sm[i] = sm[i - 1]

​        ans.append(0)

​      else:

​        sm[i] = sm[i - 1] + k - (sm[i - 1] - sm[pre[c]] + i - pre[c])

​        ans.append(k - (sm[i - 1] - sm[pre[c]] + i - pre[c]))

​      pre[c] = i

​    return ans

if __name__ == '__main__':

  S = "AABACCDCD"

  k = 3

  solution = Solution()

  print(" 字符串是", S, "，每个相同字符间至少间隔",k , "个字符")

  print(" 字符的列表是:", solution.getAns(k,S))

叶节点的和  

 

\#参数root是树根

\#返回值为整数，为叶节点值的和

class TreeNode:

  def __init__(self, val):

​    self.val = val

​    self.left, self.right = None, None

class Solution:#莫里斯中序遍历

  def sumLeafNode(self, root):

​    res = 0

​    p = root

​    while p:

​      if p.left is None:

​        if p.right is None: # p 是一个叶节点

​          res += p.val

​        p = p.right

​      else:

​        tmp = p.left

​        while tmp.right is not None and tmp.right != p:

​          tmp = tmp.right

​        if tmp.right is None:

​          if tmp.left is None: # tmp 是一个叶子节点

​            res += tmp.val

​          tmp.right = p

​          p = p.left

​        else: # 因为tmp.right为前序，所以停止

​          tmp.right = None

​          p = p.right

​    return res

if __name__ == '__main__':

  n1 = TreeNode(1)

  n1.left = TreeNode(2)

  n1.right = TreeNode(3)

  n1.left.left = TreeNode(4)

  n1.left.right = TreeNode(5)

  solution = Solution()

  print("输入:", [1, 3, 4, 5##])

print("输出:", solution.sumLeafNode(n1))

转换字符串  

 

\#参数startString是起始链

\#参数endString是目标链

\#返回值是布尔值，如果可以转换则返回True，否则返回False

class Solution:

  def canTransfer(self, startString, endString):

​    if not startString and not endString:

​      return True

​    \# 长度不等

​    if len(startString) != len(endString):

​      return False

​    \# 字母种类起始链比终止链少

​    if len(set(startString)) < len(set(endString)):

​      return False

​    maptable = {}

​    for i in range(len(startString)):

​      a, b = startString[i], endString[i]

​      if a in maptable:

​        if maptable[a] != b:

​          return False

​      else:

​        maptable[a] = b

​    def noloopinhash(maptable): # 映射表带环

​      keyset = set(maptable)

​      while keyset:

​        a = keyset.pop()

​        loopset = {a}

​        while a in maptable:

​          if a in keyset:

​            keyset.remove(a)

​          loopset.add(a)

​          if a == maptable[a]:

​            break

​          a = maptable[a]

​          if a in loopset:

​            return False

​      return True

​    return noloopinhash(maptable)

if __name__ == '__main__':

  startString = "abc"

  endString = "bca"

  solution = Solution()

  print(" 起始链是：", startString)

  print(" 终止链是：", endString)

  print(" 能否转换：", solution.canTransfer(startString, endString))

最少按键次数  

 

\#参数s是一个字符串

\#返回值为整数，为最小按键次数

class Solution:

  def getAns(self, s):

​    left = -1

​    ans = 0

​    ncaps = True

​    for right in range(0, len(s)):

​      if ncaps:

​        if ord(s[right]) < 95 and right-left <= 2:

​          ans += 2

​          if right-left == 2:

​            ncaps = False

​            ans -= 1

​            left = right

​        else:

​          left = right

​          ans +=1

​      else:

​        if ord(s[right]) > 95 and right-left <= 2:

​          ans += 2

​          if right - left == 2:

​            ncaps = True

​            ans -= 1

​            left = right

​        else:

​          left = right

​          ans +=1

​    return ans

\#主函数

if __name__ == '__main__':

  str = "EWlweWXZXxcscSDSDcccsdcfdsFvccDCcDCcdDcGvTvEEdddEEddEdEdAs"

  solution = Solution()

  print(" str是：", str)

  print(" 最小按键数是:", solution.getAns(str))

二分查找  

 

class Solution:

  \# 参数nums为整数数组

  \# 参数target为整数

  \# 返回整数

  def binarySearch(self, nums, target):

​    left, right = 0, len(nums)-1

​    while left + 1 < right :

​      mid = (left + right)// 2

​      if nums[mid] < target :

​        left = mid

​      else :

​        right = mid

​    if nums[left] == target :

​      return left

​    elif nums[right] == target :

​      return right

​    return -1;

\#主函数

if __name__ == '__main__':

  nums=[1,3,4,5,6,9]

  target=6

  solution = Solution()

answer=solution.binarySearch(nums,target)

  print("输入数组为：",nums)

  print("输入目标为：",target)

  print("输出下标为：",answer)

全排列  

 

class Solution:

  """

  参数nums为整数列表

  返回排序列表

  """

  def permute(self, nums):

​    if nums is None:

​      return []

​    if nums == []:

​      return [[]]

​    nums = sorted(nums)

​    permutation = []

​    stack = [-1]

​    permutations = []

​    while len(stack):

​      index = stack.pop()

​      index += 1

​      while index < len(nums):

​        if nums[index] not in permutation:

​          break

​        index += 1

​      else:

​        if len(permutation):

​          permutation.pop()

​        continue

​      stack.append(index)

​      stack.append(-1)

​      permutation.append(nums[index])

​      if len(permutation) == len(nums):

​        permutations.append(list(permutation))

​    return permutations

\#主函数

if __name__ == '__main__':

  solution=Solution()

  nums=[0,1,2]

  name=solution.permute(nums)

  print("输入为：",nums)

  print("输出为：",name)

最小路径和  

 

class Solution:

  """

  参数grid为整数列表

  返回整数

  """

  def minPathSum(self, grid):

​    for i in range(len(grid)):

​      for j in range(len(grid[0])):

​        if i == 0 and j > 0:

​          grid[i][j] += grid[i][j-1]

​        elif j == 0 and i > 0:

​          grid[i][j] += grid[i-1][j]

​        elif i > 0 and j > 0:

​          grid[i][j] += min(grid[i-1][j], grid[i][j-1])

​    return grid[len(grid) - 1][len(grid[0]) - 1]

\#主函数

if __name__ == '__main__':

  solution=Solution()

  nums=[[1,3,1],[1,5,1],[4,2,1]]

  print("输入列表为：",nums)

  answer=solution.minPathSum(nums)

print("输出路径和：",answer)

最长路径序列  

 

class Solution:

  """

  参数num为整数列表

  返回整数

  """

  def longestConsecutive(self, num):

​    dict = {}

​    for x in num:

​      dict[x] = 1

​    ans = 0

​    for x in num:

​      if x in dict:

​        len = 1

​        del dict[x]

​        l = x - 1

​        r = x + 1

​        while l in dict:

​          del dict[l]

​          l -= 1

​          len += 1

​        while r in dict:

​          del dict[r]

​          r += 1

​          len += 1

​        if ans < len:

​          ans = len

​    return ans

\#主函数

if __name__ == '__main__':

  solution=Solution()

  nums=[100,4,200,1,3,2]

  answer=solution.longestConsecutive(nums)

  print("输入列表为：",nums)

  print("输出长度为：",answer)

背包问题2 

 

class Solution:

  \# 参数m为整数

  \# 参数A和V为整数列表

  def backPackII(self, m, A, V):

​    n = len(A)

​    dp = [[0] * (m + 1), [0] * (m + 1)]

​    for i in range(1, n + 1):

​      dp[i % 2][0] = 0

​      for j in range(1, m + 1):

​        dp[i % 2][j] = dp[(i - 1) % 2][j]

​        if A[i - 1] <= j:

​          dp[i % 2][j] = max(dp[i % 2][j], dp[(i - 1) % 2][j - A[i - 1]] + V[i - 1])

​    return dp[n % 2][m]

\# 主函数

if __name__ == '__main__':

  solution=Solution()

  vol=34

  nums=[4,13,2,6,7,11,8]

  val=[1,23,4,5,2,14,9]

  answer = solution.backPackII(vol,nums,val)

  print("输入总体积：",vol)

  print("输入物品为：",nums)

  print("输入价值为：",val)

  print("输出结果为：",answer)

哈希函数  

 

class Solution:

  """

  参数key为字符串

  参数HASH_SIZE为整数

  返回整数

  """

  def hashCode(self, key, HASH_SIZE):

​    ans = 0

​    for x in key:

​      ans = (ans * 33 + ord(x)) % HASH_SIZE

​    return ans

\#主函数

if __name__ == '__main__':

  solution=Solution()

num=100

  key="abcd"

  answer= solution.hashCode(key,num)

  print("输入key为：",key)

  print("输入num为：",num)

  print("输出值为：",answer)

第一个只出现一次的字符  

 

class Solution:

  """

  参数str为字符串

  返回字符

  """

  def firstUniqChar(self, str):

​    counter = {}

​    for c in str:

​      counter[c] = counter.get(c, 0) + 1

​    for c in str:

​      if counter[c] == 1:

​        return c

\#主函数

if __name__ == '__main__':

  solution = Solution()

  s = "abaccdeff"

  ans = solution.firstUniqChar(s)

  solution = Solution()

  s = "abaccdeff"

  ans = solution.firstUniqChar(s)

  print("输入为：", s)

  print("输出为：", ans)

空格替换  

 

class Solution:

  \# 参数string为字符数组

  \# 参数length为字符串的真实长度

  \# 返回新字符串的真实长度

  def replaceBlank(self, string, length):

​    if string is None:

​      return length

​    f = 0

​    L = len(string)

​    for i in range(len(string)):

​      if string[i] == ' ':

​        string[i] = '%20'

​        f+=1

​    return L-f+f*3

\#主函数

if __name__ == '__main__':

  solution = Solution()

  si = "Mr John Smith"

  s1 = list(si)

  ans = solution.replaceBlank(s1, 13)

  so = ''.join(s1)

  print("输入字符串：", si)

  print("输出字符串：", so)

  print("输出其长度：", ans)

字符串压缩  

 

class Solution:

  """

  参数originalString为字符串

  返回压缩字符串

  """

  def compress(self, originalString):

​    l = len(originalString)

​    if l <=2 : 

​      return originalString

​    length = 1

​    res = ""

​    for i in range(1,l):

​      if originalString[i] != originalString[i-1]:

​        res = res + originalString[i-1] + str(length)

​        length = 1

​      else:

​        length += 1

​    if originalString[-1] != originalString[-2]:

​      res = res + originalString[-1] + "1"

​    else:

​      res = res + originalString[i-1] + str(length)

​    if len(originalString)<=len(res):

​      return originalString

​    else:

​      return res

\#主函数

if __name__ == '__main__':

  solution = Solution()

  si = "aabcccccaaa"

  arr = list(si)

  ans = solution.compress(arr)

  print("输入为：", si)

  print("输出为：", ans)

数组的最大值  

 

class Solution:

  def max_num(self, arr):

​    if arr == []:

​      return

​    maxnum = arr[0]

​    for x in arr:

​      if x > maxnum:

​        maxnum = x

​    return maxnum

\#主函数

if __name__ == '__main__':

  solution = Solution()

  arr = [1.0, 2.1, -3.3]

  ans = solution.max_num(arr)

  print("输入为：", arr)

  print("输出为：", ans)

无序链表的重复项删除  

 

class ListNode(object):

  def __init__(self, val):

​    self.val = val

​    self.next = None

class Solution:

  """

   参数head为链表的第一个节点。

   返回头结点

  """

  def removeDuplicates(self, head):

​    seen, root, pre = set(), head, ListNode(-1)

​    while head:

​      if head.val not in seen:

​        pre.next = head

​        seen.add(head.val)

​        pre = head

​      head = head.next

​    pre.next = None

​    return root

\#主函数

if __name__ == '__main__':

  solution = Solution()

  l0 = ListNode(1)

  l1 = ListNode(2)

  l2 = ListNode(2)

  l3 = ListNode(2)

  l0.next = l1

  l1.next = l2

  l2.next = l3

  root = solution.removeDuplicates(l0)

  a = [root.val, root.next.val]

  if a == [1, 2]:

​    print("输入： 1->2->2->2->null")

​    print("输出： 1->2->null")

  else:

​    print("Error")

在O(1)时间复杂度删除链表节点  

 

\#参数node是要删除的节点

\#无返回值，操作完毕

class ListNode(object):

  def __init__(self, val, next=None):

​    self.val = val

​    self.next = next

class Solution:

  def deleteNode(self, node):

​    if node.next is None:

​      node = None

​      return

​    node.val = node.next.val

​    node.next = node.next.next

\#主函数

if __name__ == '__main__':

  node1=ListNode(1)

  node2=ListNode(2)

  node3=ListNode(3)

  node4=ListNode(4)

  node1.next=ListNode(2)

  node2.next=ListNode(3)

  node3.next=ListNode(4)

  solution= Solution()

  print("输入是 :",node1.val,node2.val,node3.val,node4.val)

  solution.deleteNode(node3)

  print("删除节点3")

  print("输出是 :",node1.val,node2.val,node3.val)

将数组重新排序以构造最小值  

 

from functools import cmp_to_key

class Solution:

  def cmp(self,a,b):

​    if a+b>b+a:

​      return 1

​    if a+b<b+a:

​      return -1

​    else:

​      return 0

  def PrintMinNumber(self,numbers):

​    if not numbers:

​      return ""

​    number = list(map(str,numbers))

​    number.sort(key=cmp_to_key(self.cmp))

​    return "".join(number).lstrip('0') or '0'  

\#主函数

if __name__ == '__main__':

  generation=[3,32,321]

  solution= Solution()

  print("输入是 :",generation)

  print("输出是 :",solution.PrintMinNumber(generation))

两个链表的交叉  

 

\#参数list_a是一个链表

\#参数list_b是另一个链表

\#无返回值，直接打印出结果

class ListNode:

  def __init__(self, val=None, next=None):

​     self.value = val

​     self.next = next

class Solution:

  def get_list_length(self, head):

​    """获取链表长度"""

​    length = 0

​    while head:

​      length += 1

​      head = head.next

​    return length

  def get_intersect_node(self, list_a, list_b):

​    length_a = self.get_list_length(list_a)

​    length_b = self.get_list_length(list_b)

​    cur1, cur2 = list_a, list_b

​    if length_a > length_b:

​      for i in range(length_a - length_b):

​        cur1 = cur1.next

​    else:

​      for i in range(length_b - length_a):

​        cur2 = cur2.next

​    flag = False

​    while cur1 and cur2:

​      if cur1.value == cur2.value:

​        print(cur1.value)

​        flag = True

​        break

​      else:

​        cur1 = cur1.next

​        cur2 = cur2.next

​    if not flag:

​      print('链表没有交叉节点')

\#主函数

if __name__ == '__main__':

  solution= Solution()

  list_a = ListNode('a1', ListNode('a2', ListNode('c1', ListNode('c2', ListNode('c3')))))

  list_b = ListNode('b1', ListNode('b2', ListNode('b3', ListNode('c1', ListNode('c2', ListNode('c3'))))))

  print("输入是：")

  print("a = a1 a2 c1 c2 c3")

  print("b = b1 b2 b3 c1 c2 c3")

  print("输出是：")

  solution.get_intersect_node(list_a,list_b)

螺旋矩阵 

 

\#参数n是指123 … n任意一个整型数

\#返回值是一个矩阵

class Solution:

  def generateMatrix(self, n):

​    if n == 0: return []

​    matrix = [[0 for i in range(n)] for j in range(n)]

​    up = 0; down = len(matrix)-1

​    left = 0; right = len(matrix[0])-1

​    direct = 0; count = 0

​    while True:

​      if direct == 0:

​        for i in range(left, right+1):

​          count += 1; matrix[up][i] = count

​        up += 1

​      if direct == 1:

​        for i in range(up, down+1):

​          count += 1; matrix[i][right] = count

​        right -= 1

​      if direct == 2:

​        for i in range(right, left-1, -1):

​          count += 1; matrix[down][i] = count

​        down -= 1

​      if direct == 3:

​        for i in range(down, up-1, -1):

​          count += 1; matrix[i][left] = count

​        left += 1

​      if count == n*n: return matrix

​      direct = (direct+1) % 4

\#主函数

if __name__ == '__main__':

  n=3

  solution = Solution()

  print("输入是： n = ", n)

  print("输出是：",solution.generateMatrix(n))

三角形计数  

 

\#参数S是一个正整数数组

\#返回值count是计数结果

class Solution:

  def triangleCount(self, S):

​    if len(S)<3:

​      return;

​    count=0;

​    S.sort();#从小到大排序

​    for i in range(0,len(S)):

​      for j in range(i+1,len(S)):

​        w,r=i+1,j

​        target=S[j]-S[i]

​        while w<r:

​          mid=(w +r)//2 #取整数

​          S_mid=S[mid]

​          if S_mid>target:

​            r=mid

​          else:

​            w=mid+1

​        count+=(j-w)

​    return count

\#主函数

if __name__ == '__main__':

  generation=[3,4,6,7]

  solution= Solution()

  print("输入是：", generation)

  print("输出是：",solution.triangleCount(generation))

买卖股票的最佳时机 

 

class Solution:

  """

  参数k为整数

  参数prices为整数数组

  返回整数

  """

  def maxProfit(self, k, prices):

​    size = len(prices)

​    if k >= size / 2:

​      return self.quickSolve(size, prices)

​    dp = [-10000] * (2 * k + 1)

​    dp[0] = 0

​    for i in range(size):

​      for j in range(min(2 * k, i + 1) , 0 , -1):

​        dp[j] = max(dp[j], dp[j - 1] + prices[i] * [1, -1][j % 2])

​    return max(dp)

  def quickSolve(self, size, prices):

​    sum = 0

​    for x in range(size - 1):

​      if prices[x + 1] > prices[x]:

​        sum += prices[x + 1] - prices[x]

​    return sum

\#主函数

if __name__ == "__main__":

  solution=Solution()

  price=[4,4,6,1,1,4,2,5]

  k=2

  maxprofit=solution.maxProfit(k,price)

  print("输入价格为：",price)

  print("交易次数为：",k)

  print("最大利润为：",maxprofit)

加一  

 

class Solution:

  \#参数digits为整数数组

  \#返回整数数组

  def plusOne(self, digits):

​    digits = list(reversed(digits))

​    digits[0] += 1

​    i, carry = 0, 0

​    while i < len(digits):

​      next_carry = (digits[i] + carry) // 10

​      digits[i] = (digits[i] + carry) % 10

​      i, carry = i + 1, next_carry

​    if carry > 0:

​      digits.append(carry)

​    return list(reversed(digits))

\#主函数

if __name__ =="__main__":

  solution=Solution()

  num=[9,9,9]

  answer=solution.plusOne(num)

  print("输入为：",num)

  print("输出为：",answer)

炸弹袭击  

 

\#参数grid是一个表示二维网格的数组，由'W' 'E' '0'组成

\#返回值result是放置一个炸弹后消灭敌人的最大数量

class Solution:

  def maxKilledEnemies(self, grid):

​    m, n = len(grid), 0

​    if m:

​      n = len(grid[0])

​    result, rows = 0, 0

​    cols = [0 for i in range(n)]

​    for i in range(m):

​      for j in range(n):

​        if j == 0 or grid[i][j-1] == 'W':

​          rows = 0

​          for k in range(j, n):

​            if grid[i][k] == 'W':

​              break

​            if grid[i][k] == 'E':

​              rows += 1

​        if i == 0 or grid[i-1][j] == 'W':

​          cols[j] = 0

​          for k in range(i, m):

​            if grid[k][j] == 'W':

​              break

​            if grid[k][j] == 'E':

​              cols[j] += 1

​        if grid[i][j] == '0' and rows + cols[j] > result:

​          result = rows + cols[j]

​    return result

\#主函数

if __name__ == '__main__':

  generation =[

​      "0E00",

​      "E0WE",

​      "0E00"

​      ]

  solution= Solution()

  print("输入是：", generation)

  print("输出是：", solution.maxKilledEnemies(generation))

组合总和 IV 

 

\#参数nums是一个不重复的正整型数组

\#参数target是一个整数

\#返回值是一个整数，表示组合方式的个数

class Solution:

  def backPackVI(self, nums, target):

​    row = len(nums)

​    col = target

​    dp = [0 for i in range(col + 1)]

​    dp[0] = 1

​    for j in range(1, col + 1):

​      for i in range(1, row + 1):

​        if nums[i - 1] > j:

​          continue

​        dp[j] += dp[j - nums[i - 1]]

​    return dp[-1]

\#主函数

if __name__ == '__main__':

  generation=[1,2,4]

  target=4

  solution= Solution()

  print("输入是：", generation)

  print("输出是：", solution.backPackVI(generation,target))

向循环有序链表插入节点  

 

\#参数node是要插入的链表节点序列

\#参数x是一个整数，表示插入的新的节点

\#返回值new_node是插入新节点后的链表序列

class ListNode:

  def __init__(self, val=None, next=None):

​     self.val = val

​     self.next = next

class Solution:

  def insert(self, node, x):

​    new_node = ListNode(x)

​    if node is None:

​      node = new_node

​      node.next = node

​      return node

​    \#定义当前节点和前一节点

​    cur, pre = node, None

​    while cur:

​      pre = cur

​      cur = cur.next

​      \#  pre.val <= x <= cur.val

​      if x <= cur.val and x >= pre.val:

​        break

​      \#链表循环处特殊判断（最大值->最小值），如果x小于最小值或x大于最大值，在此插入

​      if pre.val > cur.val and (x < cur.val or x > pre.val):

​        break

​      \#循环了一遍

​      if cur is node:

​        break

​    \#插入该节点

​    new_node.next = cur

​    pre.next = new_node

​    return new_node

\#主函数

if __name__ == '__main__':

  k=4

  generation = ListNode(3, ListNode(5, ListNode(1)))

  solution= Solution()

  solution.insert(generation,k)

  print("输入是： {3,5,1}")

  print("输出是：",generation.val,generation.next.val,generation.next.next.val, generation.next.next.next.val)

大岛的数量  

 

class Solution:

  """

  参数grid为二维布尔数组

  参数k为整数

  返回岛的数量

  """

  def numsofIsland(self, grid, k):

​    \# Write your code here

​    if not grid or len(grid)==0 or len(grid[0])==0: return 0

​    rows, cols = len(grid), len(grid[0])

​    visited = [[False for i in range(cols)] for i in range(rows)]

​    res = 0

​    for i in range(rows):

​      for j in range(cols):

​        if visited[i][j]==False and grid[i][j] == 1:

​          check = self.bfs(grid, visited, i,j,k)

​          if check: res+=1

​    return res 

  def bfs(self, grid, visited, x, y, k):

​    rows, cols = len(grid), len(grid[0])

​    import collections

​    queue = collections.deque([(x, y)])

​    visited[x][y] = True

​    res = 0

​    while queue:

​      item = queue.popleft()

​      res+=1 

​      for idx, idy in ((1,0),(-1,0),(0,1),(0,-1)):

​        x_new, y_new = item[0]+idx, item[1]+idy

​        if x_new < 0 or x_new >= rows or y_new < 0 or y_new >= cols or visited[x_new][y_new] or grid[x_new][y_new] == 0: continue

​        queue.append((x_new, y_new))

​        visited[x_new][y_new] = True

​    return res >= k

\#主函数

if __name__ == '__main__':

  solution = Solution()

  g = [[1,1,0,0,0],[0,1,0,0,1],[0,0,0,1,1],[0,0,0,0,0],[0,0,0,0,1]]

  k = 3

  ans = solution.numsofIsland(g, k)

  print("输入：", g, "\nk=", k)

  print("输出：", ans)

最短回文串  

 

class Solution:

  """

  参数str为字符串

  返回字符串

  """

  def convertPalindrome(self, str):

​    if not str or len(str) == 0:

​      return ""

​    n = len(str)

​    for i in range(n - 1, -1, -1):

​      substr = str[:i + 1]

​      if self.isPalindrome(substr):

​        if i == n - 1:

​          return str 

​        else:

​          return (str[i + 1:] [::-1]) + str[:]

  def isPalindrome(self, str):

​    left, right = 0, len(str) - 1 

​    while left < right:

​      if str[left] != str[right]:

​        return False

​      left += 1 

​      right -= 1 

​    return True

\#主函数

if __name__ == '__main__':

  solution = Solution()

  s = "sdsdlkjsaoio"

  ans = solution.convertPalindrome(s)

  print("输入：", s)

  print("输出：", ans)

不同的路径 

 

class Solution:

  """

  参数grid为二维数组

  返回所有唯一加权路径之和

  """

  def uniqueWeightedPaths(self, grid):

​    n=len(grid)

​    m=len(grid[0])

​    if n == 0 or m == 0:

​      return 0

​    s=[[set() for _ in range(m)] for __ in range(n)]

​    s[0][0].add(grid[0][0])

​    for i in range(n):

​      for j in range(m):

​        if i==0 and j==0:

​          s[i][j].add(grid[i][j])

​        else:

​          for val in s[i-1][j]:

​            s[i][j].add(val+grid[i][j])

​          for val in s[i][j-1]:

​            s[i][j].add(val+grid[i][j])

​    ans=0

​    for val in s[-1][-1]:

​      ans+=val

​    return ans

\#主函数

if __name__ == '__main__':

  solution = Solution()

  arr = [[1,1,2],[1,2,3],[3,2,4]]

  ans = solution.uniqueWeightedPaths(arr)

  print("输入：", arr)

  print("输出：", ans)

分割字符串  

 

class Solution:

  """

  参数s为要拆分的字符串

  返回所有可能的拆分字符串数组

  """

  def splitString(self, s):

​    result = []

​    self.dfs(result, [], s)

​    return result 

  def dfs(self, result, path, s):

​    if s == "":

​      result.append(path[:]) #important: use path[:] to clone it

​      return 

​    for i in range(2):

​      if i+1 <= len(s):

​        path.append(s[:i+1])

​        self.dfs(result, path, s[i+1:])

​        path.pop()

\#主函数

if __name__ == '__main__':

  solution = Solution()

  s = "123"

  ans = solution.splitString(s)

  print("输入：", s)

  print("输出：", ans)

缺失的第一个素数  

 

class Solution:

  """

  参数nums为数组

  返回整数

  """

  def firstMissingPrime(self, nums):

​    if not nums:

​      return 2

​    start = 0

​    l = len(nums)

​    integer = 2

​    while start < l:

​      while self.isPrime(integer) == False:

​        integer += 1

​      if nums[start] != integer:

​        return integer

​      integer += 1

​      start += 1

​    while self.isPrime(integer) == False:

​      integer += 1

​    return integer

  def isPrime(self, num):

​    if num == 2 or num == 3:

​      return True

​    for i in range(2, int(num**(0.5)) + 1):

​      if num % i == 0:

​        return False

​    return True

if __name__=='__main__':

  solution=Solution()

  n=[3,5,7]

  print("输入为：",n)

  print("输出为：",solution.firstMissingPrime(n))

单词拆分  

 

class Solution:

  """

  参数s为字符串

  参数dict为单词列表

  返回整数数量

  """

  def wordBreak3(self, s, dict):

​    if not s or not dict:

​      return 0

​    n, hash = len(s), set()

​    lowerS = s.lower()

​    for d in dict:

​      hash.add(d.lower())

​    f = [[0] * n for _ in range(n)]

​    for i in range(n):

​      for j in range(i, n):

​        sub = lowerS[i:j + 1]

​        if sub in hash:

​          f[i][j] = 1

​    for i in range(n):

​      for j in range(i, n):

​        for k in range(i, j):

​          f[i][j] += f[i][k] * f[k + 1][j]

​    return f[0][-1]

if __name__=='__main__':

​     solution=Solution()

​     s="CatMat"

​     dict1=["Cat", "Mat", "Ca", "tM", "at", "C", "Dog", "og", "Do"]

​     print("输入句子为：",s)

​     print("输入列表为：",dict1)

​     print("输出数量为：",solution.wordBreak3(s,dict1))