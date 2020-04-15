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
