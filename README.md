# Leetcode-python-solutions
```python
# 455. Assign Cookies
def findContentChildren(children,cake) -> int:
    children.sort()
    cake.sort()
    start = len(cake)-1
    res = 0
    for i in range(len(children)-1, -1, -1):
        if start>=0 and cake[start]>= children[i]:
            res+=1
            start-=1
    return res

# 135. Candy
def findcandy(child):
    candy = [1 for i in range(len(child))]
    for i in range(1, len(child)):
        if child[i-1] < child[i]:
            candy[i] = candy[i-1] + 1
    for i in range(len(child)-1, 0, -1):
        if child[i-1] > child[i]:
            candy[i-1] = max(candy[i-1], candy[i] + 1)
    return sum(candy)

# 435. Non-overlapping Intervals
def eraseOverlapIntervals(intervals):
    intervals.sort(key = lambda x:x[1])
    end = intervals[0][1]
    counter = 1
    for i in range(1, len(intervals)):
        if end <= intervals[i][0]:
            counter += 1
            end = intervals[i][1]
    return len(intervals) - counter

# 55. Jump Game
def canJump(nums) -> bool:
    cover = 0
    i = 0
    while i <= cover:
        cover = max(cover, nums[i]+i)
        i += 1
        if cover >= len(nums) -1:
            return True
    return False

#re = findContentChildren([1,2,7,10], [1,3,5,9])
#re = candy([1,0,2])
re =  eraseOverlapIntervals([ [1,2], [2,3], [3,4], [1,3] ])
print(re)
```
