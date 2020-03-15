# PythonAlgorithm
Study algorithms with python

# 1. 컴퓨터 알고리즘이란?

  - 컴퓨터가 어떤 문제를 해결하기 위해서 컴퓨터가 이해할 수 있는 방식으로 정리되어 있는 해결 방법입니다. 
  
  ## 팔린드롬(Palindrome) 정리
  
    거꾸로 읽어도 똑같은 문자를 팔린드롬이라 한다.
   
   <pre>
   <code>
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
   </code>
   </pre>
    

  ## 선형 탐색 (Linear Search)
  
    - 모든 요소를 확인하는 탐색
    
     <pre>
     <code>
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
     </code>
     </pre>
    
    
  ## 이진 탐색 (Binary Search)
  
    - 반씩 제거하며 탐색
    
     <pre>
     <code>
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
     </code>
     </pre>
    
