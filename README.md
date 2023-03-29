# Python challenges

## 1. Digram finder

We are given a string S consisting of N lowercase letters. A sequence of two adjacent letters inside a string called digram. The distance
between two digrams is the distance between the first letter of the first digram and the first letter of the second digram. For example, in
string S = "akcm" the distance between digrams "kc" and "mz" is 2.

We want to find the distance between the furthest identical digrams inside string S.

Write a function:
	
	def solutions(S)

that, given a string S of N letters, returns the distance between the two identical
digrams iin the string that lie firthest away fromn each other. If there are no two
identical digrams inside S, your function should return -1.

Examples:

1. Given S = "aakmaakmakda" your function should return 7. The furthest identical digrams are "ak"s,
starting in positions 2 and 9 (enumering from 1): "aakmaakmakda".

2. Given S = "aaa" your function should return 1. The furthest identical digrams are "aa"s starting at 
positions 1 and 2.

3. Given S = "casade" your function should return -1. There are no identical digrams in S.

Write an efficient algorithm for the following assumptions:

- N is an integer within the range [2..300,000];
- String S is made only of lowercase letters (a-z).
  
### Solution:
    def solutions(word):

      i = 0
      j = 2

      digrams = []
      positions = {}
      while j <= len(word):
          x = j
          y = x+2
          digrams.append(word[i:j])
          while y <= len(word):
            
              if word[x:y] == word[i:j]:
                  positions.setdefault(word[x:y],x-i)
                
                  if x-i >= positions[word[x:y]]:                
                      positions.update({word[x:y]:x-i})
                      x = x+1
                      y = y+1
                  else:
                      x = x+1
                      y = y+1
              else:
                  x = x+1
                  y = y+1
          i=i+1
          j=j+1
        
     indexes = sorted(positions.values())
     print(indexes[-1])
    

  
 
