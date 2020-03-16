# PythonAlgorithm
Study algorithms with python

# 1. 컴퓨터 알고리즘이란?

- 컴퓨터가 어떤 문제를 해결하기 위해서 컴퓨터가 이해할 수 있는 방식으로 정리되어 있는 해결 방법입니다. 

  ## 팔린드롬(Palindrome) 정리

      거꾸로 읽어도 똑같은 문자를 팔린드롬이라 한다. 

      # 팔린드롬을 확인하는 함수입니다.
      # check palindrome or not
      def is_palinfrome(word):
        reversed_word = word[::-1]
        return reverses_word == word

      # test codes
      print(is_palindrome("racecar"))   // True
      print(is_palindrome("hello"))     // False
      print(is_palindrome("world"))     // False
      print(is_palindrome("tomato"))    // True
      print(is_palindrome("stars"))     // True


  ## 선형 탐색 (Linear Search)
  
     모든 요소를 확인하는 탐색.
     정렬이 안되어도 됨.
     
      # 요소가 리스트에 있는지 확인하는 함수
      # Check if 'element'  is in 'some_list' or not
      def linear_search(element, some_list):
        for i in range(len(some_list)):
          if element == some_list[i]:
            return i

        return None

      #test codes
      print(linear_search(2, [2, 3, 5, 7, 11]))
      print(linear_search(0, [2, 3, 5, 7, 11]))
      print(linear_search(5, [2, 3, 5, 7, 11]))
      print(linear_search(3, [2, 3, 5, 7, 11]))
      print(linear_search(11, [2, 3, 5, 7, 11]))
    
    
  ## 이진 탐색 (Binary Search)
  
     반씩 제거하며 탐색.
     졍렬된 리스트여야 함.
    
      def binary_search(element, some_list):
        first = 0                               // 리스트의 첫번째 요소를 가리킨다.
        last = len(some_list)                   // 리스트의 마지막 요소를 가리킨다.
        middle = None                           // 중간 값

        while first <= last:                    // 첫번째 인덱스를 가르키던 포인터와 마지막 인덱스를 가르키던 포인터가 만날때까지 반복
            middle = (first + last)//2          // 중간값 계산
            if element == some_list[middle]:    // 요소가 중간인덱스의 값과 같으면
                return middle                   
            elif element < some_list[middle]:   // 요소가 중간 인덱스의 값보다 작으면 큰 값들을 제거
                last = middle - 1
            else:                               // 요소가 중간 인덱스의 값보다 크면 작은 값들을 제거
                first = middle + 1

      # Test codes
      print(binary_search(2, [2, 3, 5, 7, 11]))
      print(binary_search(0, [2, 3, 5, 7, 11]))
      print(binary_search(5, [2, 3, 5, 7, 11]))
      print(binary_search(3, [2, 3, 5, 7, 11]))
      print(binary_search(11, [2, 3, 5, 7, 11]))
     
  ## 정렬 (Sort)
    * 선택정렬 (Selection Sort)
    
          - 가장 작은 값을 맨처음부터 순서대로 정렬한다.
      
    * 삽입 정렬 (Insertion Sort)
    
          - 각 값이 어떤 위치에 들어갈지 찾는다. 
            선택된 값을 다른값들과 비교하여 크면 그 값의 오른쪽 작으면 더 앞의 값들과 계속 비교하여 찾는다.
        
        
  ## 시간과 공간 
  
    * 시간 복잡도 (Time Complexity)
      
          * 점근 표기법 (Big-O Notation)
        
        알고리즘의 효율성을 표기해주는 표기법이다.
        데이터 n개가 주어졌을때의 연산 횟수를 나타낸다.
       
          - O(1)        : 인풋의 크기가 소요 시간에 영향이 없다.
          - O(n)        : 데이터양에 따라 시간이 정비례한다.
          - O(n^2)      : 데이터양에 따라 걸리는 시간은 제곱에 비례한다.
          - O(log n)    : 데이터양이 많아져도 시간은 조금씩 늘어난다.
          - O(n log n)  : 데이터양이 n배 많아지면 실행 시간은 n배보다 조금더 많아진다.
        
        List Operations
        
        | Operation | Code | Average Case |
        | --------- | ---- | ------------ |
        | Indexing | some_list[index] | O(1) |
        | Sort | some_list.sort(), sorted(some_list) | O(n lg n) |
        | Reverse | some_list.reverse() | O(n) |
        | Search | element in  some_list | O(n) |
        | Append | some_list.append(index) | O(1) |
        | Insert | some_list.insert(index, element) | O(n) |
        | Delete | del some_list[index] | O(n) |
        | Minimum | min(some_list) | O(n) |
        | Maximum | max(some_list) | O(n) |
        
        Dictionary
        
        | Opertion | Code | Average Case |
        | -------- | ---- | ------------ |
        | Get | some_dict[key] | O(1) |
        | Set | some_dict[key] = value | O(1) |
        | Delete | del some_dict[key] | O(1) |

# 2. 재귀함수 (Recursion)

   - 자기 자신을 호출하는 함수

   - Base Case와 Recursive Case를 구분해야 한다.

   - Example : Factorial

  ```

  def factorial(n):

      if n == 0:                  // Base Case
          return 1     
      return factorial(n-1) * n   // Recursive Case

  print(factorial(4))             // Test Codes

  ```

   - 재귀 함수의 단점 : 재귀 함수 호출이 너무 많으면 call stack에 너무 많은 데이터가 쌓여 과부하로 인해 프로그램이 중단 될 수 있다.
            
  ## Recursion Examples
  
  1. Fibonacci

          ```
          def fib(n):
          if n < 3 :                        // Base Case
              return 1
          return fib(n - 1) + fib(n - 2)    // Recursive Case

          for i in range(1, 11):            // Test
          print(fib(i))
          ```

  2. Sum of 1 ~ n
  
          ```
          def triangle_number(n):
            if n == 1:                        // Base Case
                return 1                      
            return n + triangle_number(n-1)   // Recursive Case 

          for i in range(1, 11):              // Test
            print(triangle_number(i))
          ```
  
  3. sum of digits
  
          ```
          def sum_digits(n):
            if n < 10:                            // Base Case
                return n
            return (n % 10) + sum_digits(n//10)   // Recursive Case

            print(sum_digits(22541))              // Tests
            print(sum_digits(92130))
            print(sum_digits(12634))
            print(sum_digits(704))
            print(sum_digits(3755))
          ```
  4. Reverse list
  
          ```
          def flip(some_list):
            if len(some_list) < 2:                          // Base Case
                return some_list

            return some_list[-1:] + flip(some_list[:-1])    // Recursive Case

            some_list = [1, 2, 3, 4, 5, 6, 7, 8, 9]         // test
            some_list = flip(some_list)
            print(some_list)
          ```
  
  5. Binary Search with Recursion

          ```
          def binary_search(element, some_list, start_index=0, end_index=None):
            if end_index == None:                                                 // end_index가 따로 주어지지 않은 경우에는 리스트의 마지막 인덱스
                end_index = len(some_list) - 1

            if start_index > end_index:                                           // start_index가 end_index보다 크면 some_list안에 element는 없다
                return None

            mid = (start_index + end_index) // 2                                  // 범위의 중간 인덱스를 찾는다

            if some_list[mid] == element:                                         // 이 인덱스의 값이 찾는 값인지 확인을 해준다
                return mid

            if element < some_list[mid]:                                          // 찾는 항목이 중간 값보다 작으면 리스트 왼쪽을 탐색해준다
                return binary_search(element, some_list, start_index, mid - 1)    
            else:                                                                 // 찾는 항목이 중간 값보다 크면 리스트 오른쪽을 탐색해준다
                return binary_search(element, some_list, mid + 1, end_index)        

            print(binary_search(2, [2, 3, 5, 7, 11]))
            print(binary_search(0, [2, 3, 5, 7, 11]))
            print(binary_search(5, [2, 3, 5, 7, 11]))
            print(binary_search(3, [2, 3, 5, 7, 11]))
            print(binary_search(11, [2, 3, 5, 7, 11]))
          ```
  
  6. Tower of Hanoi
  
          ```
          def move_disk(disk_num, start_peg, end_peg):
              print("%d번 원판을 %d번 기둥에서 %d번 기둥으로 이동" % (disk_num, start_peg, end_peg))

          def hanoi(num_disks, start_peg, end_peg):
              if num_disks == 0:                                  // base case: 옮길 원판이 없으면 끝
                  return
              else:
                  other_peg = 6 - start_peg - end_peg

                  hanoi(num_disks - 1, start_peg, other_peg)      // 1. 가장 큰 원판을 제외하고 나머지 원판들을 start_peg에서 other_peg로 이동
                  move_disk(num_disks, start_peg, end_peg)        // 2. 가장 큰 원판을 start_peg에서 end_peg로 이동

                  hanoi(num_disks - 1, other_peg, end_peg)        // 3. 나머지 원판들을 other_peg에서 end_peg로 이동

          hanoi(3, 1, 3)
          ```

  # 3. 알고리즘 패러다임 (Algorithmic Paradigm)
  
    ## Brute Force
    
          - 가능한 모든 경우의 수를 시도해본다.
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
              
     ## Divide and Conquer (분할 정복)
     
        1. Divide : 문제를 부분 문제로 나눈다.
        2. Conquer : 각 부분 문제를 정복한다.
        3. Combine : 부분 문제들의 솔루션을 합쳐서 기존문제를 해결한다.
        
     ## Divide and Conquer Examples
     
        - Sum of 1 ~ n
        
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
        
        - Merge Sort
        
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
        
        
