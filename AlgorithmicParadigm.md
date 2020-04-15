# 3. 알고리즘 패러다임 (Algorithmic Paradigm)
  
## A. Brute Force
    
   - 모든 경우의 수를 시도해본다.
   - 경우의 수가 너무 많아지면 비효율적이다.

   -  Example Code : 최고의 조합을 찾는다.
      
  ```
  def max_product(left_cards, right_cards):
      max = 0

      for l in left_cards:
          for r in right_cards:
              if l*r > max:
                  max = l*r

      return max    

      print(max_product([1, 6, 5], [4, 2, 3]))
      print(max_product([1, -9, 3, 4], [2, 8, 3, 1]))
      print(max_product([-1, -7, 3], [-4, 3, 6]))
  ```
              
## B. Divide and Conquer (분할 정복)
     
   1. Divide : 문제를 부분 문제로 나눈다.
   2. Conquer : 각 부분 문제를 정복한다.
   3. Combine : 부분 문제들의 솔루션을 합쳐서 기존문제를 해결한다.
        
## Divide and Conquer Examples
     
   1. Sum of 1 ~ n
        
  ```
  def consecutive_sum(start, end):
      if start == end:      // base case
          return start

      mid = (start + end) // 2    // for Divide

      return consecutive_sum(start, mid) + consecutive_sum(mid+1, end)    // Divide & Conquer &Combine

      print(consecutive_sum(1, 10))   // Tests
      print(consecutive_sum(1, 100))
      print(consecutive_sum(1, 253))
      print(consecutive_sum(1, 388))
  ```
  <hr/>
        
   2. Merge Sort
        
     1. Divide : 리스트를 반으로 나눈다.
     2. Conquer : 왼쪽 리스트와 오른쪽 리스트를 각각 정렬한다.
     3. Combine : 정렬된 두 리스트를 하나의 정렬된 리스트로 합병한다.
        
  ```
  def merge(list1, list2):
    merged_list = []

    i = 0
    j = 0

    while i < len(list1) and j < len(list2):
      if list1[i] < list2[j]:
        merged_list.append(list[1])
        i += 1
      else:
        merged_list.append(list2[j])
        j +=1

    if i == len(list1):
      merged_list += list2[j:]
    else:
      merged_list += list1[i:]

     return merged_list

   def merge_sort(some_list):
      if len(some_list) < 2:                                            // Base Case
         return some_list

      left_list = some_list[:(len(some_list)//2)]                       // Divide
      right_list = some_list[(lensome_list)//2:]

      return merge(merge(left_list), merge(right_list))                 // Conquer & Combine


   print(merge_sort([1, 3, 5, 7, 9, 11, 13, 11]))     // Tests
   print(merge_sort([28, 13, 9, 30, 1, 48, 5, 7, 15]))
   print(merge_sort([2, 5, 6, 7, 1, 2, 4, 7, 10, 11, 4, 15, 13, 1, 6, 4]))
  ```
  <hr/>
        
   3. Quick Sort     
      - Divide : Partition을 한다. pivot값을 설정 후 피봇보다 작으면 왼쪽 크면 오른쪽으로 놓는다.
      - Conquer : pivot의 왼쪽에 있는 것과 오른쪽에 있는 것을 각각 정렬해준다.
      - Comebine : Conquer단계에서 이미 정렬이 되기 때문에 사실상 할일이 없다.
      
 ```
  def swap_elements(some_list, index1, index2):
      temp = some_list[index1]
      some_list[index1] = some_list[index2]
      some_list[index2] = temp
      
  def partition(some_list, start, end):       //  Divide
      i = start             // 비교할 요소
      bigger = start        // 요소보다 큰 수들
      pivot = end           // 피벗 값 설정
      
      while i < p:
          if some_list[i] <= some_list[pivot]:      // 피벗값과 비교하여 작거나 같으면
              swap_elements(some_list, i, bigger)   // 큰수의 첫번째 요소와 바꾼다.
              bigger += 1                           // 큰 수들 범위 재정의
          i += 1                                    // 그 다음 비교할 값으로 이동
          
      swap_elements(some_list, bigger, pivot)       // 끝에 도달하면 피벗값과 큰수들의 첫요소와 자리 바꿈
      pivot = bigger                                // 피벗을 중간으로
      
      return pivot                                  // 피벗의 인덱스를 리턴
      
  def quicksort(some_list, start = 0, end = None):
      if end == None:
          end = len(some_list) - 1
          
      if end = start < 1:
          return
          
      pivot = partition(some_list, start, end)
      
      quicksort(some_list, start, pivot - 1)
      quicksort(some_list, pivot + 1, end)
      
      
  list1 = [1, 3, 5, 7, 9, 11, 13, 11]                     // Tests
  quicksort(list1) # start, end 파라미터 없이 호출
  print(list1)


  list2 = [28, 13, 9, 30, 1, 48, 5, 7, 15]
  quicksort(list2) # start, end 파라미터 없이 호출
  print(list2)


  list3 = [2, 5, 6, 7, 1, 2, 4, 7, 10, 11, 4, 15, 13, 1, 6, 4]
  quicksort(list3) # start, end 파라미터 없이 호출
  print(list3)
 ```
 <hr/>

## C. Dynamic Programming

  1. 최적 부분 구조 (Optimal Substructure): 부분 문제들의 최적의 답을 이용해서 기존 문제의 최적의 답을 구할 수 있다는 것.
  2. 중복되는 부분 문제 (Overlapping Subproblems)
  
  - 이 2가지의 조건이 충족되면 Dynamic Programming으로 문제를 해결할 수 있다.
  - 한 번 계산한 결과를 재활용하는 방식: 이것도 2가지 방법이 있다.
  - Memoization (재귀): 중복되는 계산은 한 번만 계산 후 값을 cache에 메모하고 또 같은 계산을 사용해야 할 경우 메모해 놓은 것을 다시 가져다 쓴다. Top-down.
  ```
  # fibonacci memoization
  def fib_memo(n, cache):
      if n < 3:
          return 1
          
      if n in cache:
          return cache[n]
          
      cache[n] = fib_memo(n - 1, cache) + fib_memo(n - 2, cache)
      
      return cache[n]
      
  def fib(n):
      fib_cache = {}
      
      return fib_memo(n, fib_cache)
      
  print(fib(10))    // tests
  print(fib(50))
  print(fib(100))
  ```

  - Tabulation (반복문) : Table 방식으로 정리. Bottom-up
  ```
    def fib_tabluation(n):
        fib_table = [0, 1, 1]
        
        for i in range(3, n+1):
            fib_table.append(fib_table[i-2] + fib_table[i-1])
            
        return fib_table[n]
        
    print(fib_tab(10))    // tests
    print(fib_tab(56))
    print(fib_tab(132))
  ```
  
  - Memoization는 Call Stack에 쌓이는 것을 신경쓰면서 사용해야 한다. 너무 많으면 과부하가 걸리기 때문.
  - Tabulation은 하나씩 차례대로 계산해야 되기 때문에 가끔은 필요없는 것도 계산한다.
  - Dynamic Programming을 사용할때 공간 최적화에 신경쓰자.
  ```
  def fib_optimized(n):
    # 코드를 작성하세요. 
    current = 1
    previous = 0
    
    for i in range(1, n):
        current, previous = current + previous, current     // Python Swap
        /* 
        temp = current                                      // Basic Swap
        current = current + previous
        previous = temp
        */
         
    return current

    # 테스트
    print(fib_optimized(16))
    print(fib_optimized(53))
    print(fib_optimized(213))
  ```
  ```
    # Memoization example
    def max_profit_memo(price_list, count, cache):
        if count < 2:
            cache[count] = price_list[count]

        if count in cache:
            return cache[count]

        if count < len(price_list):
            profit = price_list[count]
        else:
            profit = 0

        for i in range(1, count // 2 + 1):
            profit = max(profit, max_profit_memo(price_list, i,cache) + max_profit_memo(price_list, count - i, cache))

        cache[count] = profit

        return profit
    
    def max_profit(price_list, count):
        max_profit_cache = {}

        return max_profit_memo(price_list, count, max_profit_cache)


    print(max_profit([0, 100, 400, 800, 900, 1000], 5))
    print(max_profit([0, 100, 400, 800, 900, 1000], 10))
    print(max_profit([0, 100, 400, 800, 900, 1000, 1400, 1600, 2100, 2200], 9))

  ```
  ```
  # Tabulation example
  def max_profit(price_list, count):
      profit_table = [0]

      for i in range(1, count + 1):
          if i < len(price_list):
              profit = price_list[i]
          else:
              profit = 0

          for j in range(1, i // 2 + 1):
              profit = max(profit, profit_table[j] + profit_table[i - j])

          profit_table.append(profit)

      return profit_table[count]

  print(max_profit([0, 200, 600, 900, 1200, 2000], 5))        // tests
  print(max_profit([0, 300, 600, 700, 1100, 1400], 8))
  print(max_profit([0, 100, 200, 400, 600, 900, 1200, 1300, 1500, 1800], 9))

  ```

## D. Greedy Algorithm
  - 미래를 내다보지 않고 당장 눈 앞에 보이는 최적의 선택을 하는 방식
  - 구현하기 쉽지만 최적의 답을 보장하지 않는다.
  - 최적 부분 구조 (Data Substructure) & 탐욕적 선택 속성 (Greedy Choice Property) -> Greedy가 최적의 답을 보장해 줄때
  - 최적 부분 구조 (Data Substructure) : 부분 문제들의 최적의 답을 이용해서 기존 문제의 최적의 답을 구할 수 있는 것.
  - 탐욕적 선택 속성 (Greedy Choice Property): 각 단계에서의 탐욕스런 선택이 최종 답을 구하기 위한 최적의 선택

```
# Minimum Coin Example

def min_coin_count(value, coin_list):
    coint_count = 0
    
    for coin in sorted(coin_list, reverse = True):
        coin_count += (value // coin)
        
        value %= coin
        
    rturn coin_count
    
default_coin_list = [100, 500, 10, 50]            # tests
print(min_coin_count(1440, default_coin_list))
print(min_coin_count(1700, default_coin_list))
print(min_coin_count(23520, default_coin_list))
print(min_coin_count(32590, default_coin_list))
```

```
# Max Product Example

def max_product(card_lists):
    product = 1
    
    for card in card_list:
      product *= max(card)
      
test_cards1 = [[1, 6, 5], [4, 2, 3]]        # Tests
print(max_product(test_cards1))

test_cards2 = [[9, 7, 8], [9, 2, 3], [9, 8, 1], [2, 8, 3], [1, 3, 6], [7, 7, 4]]
print(max_product(test_cards2))

test_cards3 = [[1, 2, 3], [4, 6, 1], [8, 2, 4], [3, 2, 5], [5, 2, 3], [3, 2, 1]]
print(max_product(test_cards3))

test_cards4 = [[5, 5, 5], [4, 3, 5], [1, 1, 1], [9, 8, 3], [2, 8, 4], [5, 7, 4]]
print(max_product(test_cards4))
```
```
# 지각 벌금 최소화

def min_fee(pages_to_print):
    fee = 0
    pages_sorted = sorted(pages_to_print)
    
    for i in range(len(pages_sorted)):
        fee += pages_sorted[i] * (len(pages_sorted)-i)
        
    return fee
    
print(min_fee([6, 11, 4, 1]))       ## Tests
print(min_fee([3, 2, 1]))
print(min_fee([3, 1, 4, 3, 2]))
print(min_fee([8, 4, 2, 3, 9, 23, 6, 8]))
```
```
# 수강 신청
def course_selection(course_list):
    sorted_list = sorted(course_list, key = lambda x: x[1])
    
    my_selection = [sorted_list[0]]
    
    for course in sorted_list:
        if course[0] > my_selection[-1][1]:
            my_selection.append(course)
            
    return my_selection
    

print(course_selection([(6, 10), (2, 3), (4, 5), (1, 7), (6, 8), (9, 10)]))       # Tests
print(course_selection([(1, 2), (3, 4), (0, 6), (5, 7), (8, 9), (5, 9)]))
print(course_selection([(4, 7), (2, 5), (1, 3), (8, 10), (5, 9), (2, 5), (13, 16), (9, 11), (1, 8)]))

```
