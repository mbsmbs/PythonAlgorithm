# PythonAlgorithm
Study algorithms with python

# 1. 컴퓨터 알고리즘이란?

  - 컴퓨터가 어떤 문제를 해결하기 위해서 컴퓨터가 이해할 수 있는 방식으로 정리되어 있는 해결 방법입니다. 
  
  ## 팔린드롬(Palindrome) 정리
  
    거꾸로 읽어도 똑같은 문자를 팔린드롬이라 한다.
    
   ```
    # 팔린드롬을 확인하는 함수입니다.
    # check palindrome or not
    def is_palinfrome(word):
      reversed_wprd = word[::-1]
      return reverses_word == word


    # test codes
    print(is_palindrome("racecar"))   // True
    print(is_palindrome("hello"))     // False
    print(is_palindrome("world"))     // False
    print(is_palindrome("tomato"))    // True
    print(is_palindrome("stars"))     // True
   ```
