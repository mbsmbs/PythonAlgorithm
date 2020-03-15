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
  
   
   <hr/>

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
       
        - O(1)        : 입력되는 테이터양과 관계없이 한번의 실행 시간을 가진다.
        - O(n)        : 데이터양에 따라 시간이 정비례한다.
        - O(n^2)      : 데이터양에 따라 걸리는 시간은 제곱에 비례한다.
        - O(log n)    : 데이터양이 많아져도 시간은 조금씩 늘어난다.
        - O(n log n)  : 데이터양이 n배 많아지면 실행 시간은 n배보다 조금더 많아진다.
        
| First Header  | Second Header |
| ------------- | ------------- |
| Content Cell  | Content Cell  |
| Content Cell  | Content Cell  |

