### Description:  
Given a string, find the length of the longest substring without repeating characters.

Example 1:
```
Input: "abcabcbb"
Output: 3 
Explanation: The answer is "abc", with the length of 3. 
```
Example 2:
```
Input: "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```
Example 3:
```
Input: "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3. 
             Note that the answer must be a substring, "pwke" is a subsequence and not a substring.
```
### Solution:  
```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        '''
        Note that the length of each space is 1.
        '''
        MAX_LEN = 0
        queue = [] 
        if len(s) == 0:
            return 0
        elif s.isspace():
            return 1        
        for item in s:
            if item not in queue:
                queue.append(item)
            elif item in queue:
                if MAX_LEN < len(queue):
                    MAX_LEN = len(queue)
                # See below for explanation
                index = queue.index(item) 
                if index == len(queue) - 1: # item is the final element of the queue
                    queue = []
                else:
                    queue = queue[index+1:]
                queue.append(item)
        return max(MAX_LEN, len(queue))            
```

### Explanation
```python
when input: "pwwkew"
queue changes as follows:
1. ['p']
2. ['p', 'w']
3. ['w']  # 'w' in ['p', 'w'], ['p', 'w'].index('w') == len(['p', 'w']) - 1 , so queue=[], then append('w') 
4. ['w', 'k']
5. ['w', 'k', 'e']
6. ['k', 'e', 'w'] # 'w' in ['w', 'k', 'e'], ['w', 'k', 'e'].index('w') < len(['p', 'w']) - 1 , so queue=['k', 'e'], then append('w') 
```
