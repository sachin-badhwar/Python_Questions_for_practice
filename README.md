# Python_Questions_for_practice
Question 1.
A city skyline can be represented as a 2-D list with 1s representing buildings. In the example below, the height of the tallest building is 4 (second-most right column).

[[0, 0, 0, 0, 0, 0],
[0, 0, 0, 0, 1, 0],
[0, 0, 1, 0, 1, 0],
[0, 1, 1, 1, 1, 0],
[1, 1, 1, 1, 1, 1]]
Create a function that takes a skyline (2-D list of 0's and 1's) and returns the height of the tallest skyscraper.

Examples
tallest_skyscraper([
  [0, 0, 0, 0],
  [0, 1, 0, 0],
  [0, 1, 1, 0],
  [1, 1, 1, 1]
]) ➞ 3

Solution 1:
def test1(twoDimensionalList):
  a = 0
  for i in range(0,len(twoDimensionalList)):
    if 1 in twoDimensionalList[i]:
      a = i
      break  
  height = len(twoDimensionalList) - a
  return height     
    
a =[[0,1],
   [1,1]]

print(test1(a))

Solution 2
def test2(twoDimensionalList):
  height = 0
  s = filter(lambda x : 1 in x,twoDimensionalList)   
  print(s)  
  for i in s:
    height = height+1
  return height 

a1 =[[0,0],
  [0,1],
   [1,1]]

print(test2(a1))


Question 2.
Create a function that returns the majority vote in a list. A majority vote is an element that occurs > N/2 times in a list (where N is the length of the list).

Examples
majority_vote(["A", "A", "B"]) ➞ "A"

majority_vote(["A", "A", "A", "B", "C", "A"]) ➞ "A"

majority_vote(["A", "B", "B", "A", "C", "C"]) ➞ None
Notes
The frequency of the majority element must be strictly greater than 1/2.
If there is no majority element, return None.
If the list is empty, return None.

Solution:
def majority_vote(lst):
  a = set(lst)
  b = [i for i in a if lst.count(i) > len(lst)/2]
  if len(b)>0:
    return b[0]
  else:
    return None  

Question 3.
Create a function that takes a list and returns a new list containing only prime numbers.

Examples
filter_primes([7, 9, 3, 9, 10, 11, 27]) ➞ [7, 3, 11]

filter_primes([10007, 1009, 1007, 27, 147, 77, 1001, 70]) ➞ [10007, 1009]

filter_primes([1009, 10, 10, 10, 3, 33, 9, 4, 1, 61, 63, 69, 1087, 1091, 1093, 1097]) ➞ [1009, 3, 61, 1087, 1091, 1093, 1097]

Solution:
def filter_primes(num):
    return [n for n in num if n > 1 and all(n % i != 0 for i in range(2,int(n**0.5) + 1))]


no = [7, 9, 3, 9, 10, 11, 27]
print(filter_primes(no))

Question 4.
A robot has been given a list of movement instructions. Each instruction is either left, right, up or down, followed by a distance to move. The robot starts at [0, 0]. You want to calculate where the robot will end up and return its final position as a list.

To illustrate, if the robot is given the following instructions:

["right 10", "up 50", "left 30", "down 10"]
It will end up 20 left and 40 up from where it started, so we return [-20, 40].
Solution:
def track_robot(instructions):
  total = {'right':0,'left':0,'up':0,'down':0}
  for i in instructions:
    i = i.split()
    total[i[0]]+=int(i[1])
    
  return [total['right']-total['left'],total['up']-total['down']]
	

