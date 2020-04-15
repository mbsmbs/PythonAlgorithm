# 연습 1 : 투자 귀재 규식이 I : Brute Force
  - 우선 함수 sublist_max는 파라미터로 리스트 profits를 받는데요. profits에는 며칠 동안의 수익이 담겨 있습니다. 
    예를 들어서 profits가 [7, -3, 4, -8]이라면 
    첫 날에는 7달러를 벌었고, 둘째 날에는 3달러를 잃었고, 셋째 날에는 4달러를 벌었고, 마지막 날에는 8달러를 잃은 거죠.

    sublist_max 함수는 profits에서 최대 수익을 내는 구간의 수익을 리턴합니다.

    profits가 [7, -3, 4, -8]이라면 무엇을 리턴해야 할까요? 
    profits에서 가장 많은 수익을 낸 구간은 [7, -3, 4]입니다. 이 구간에서 낸 수익은 8달러이니, 8을 리턴하면 되겠죠!

    만약 profits가 [-2, -3, 4, -1, -2, 1, 5, -3]이라면? 
    profits에서 수익이 가장 큰 구간은 [4, -1, -2, 1, 5]입니다. 이 구간에서 낸 수익은 7달러이니, 7을 리턴하겠죠?
```
def sublist_max(profits):
    max_profit = profits[0] # 최대 수익
    
    for i in range(len(profits)):
        # 인덱스 i부터 j까지 수익의 합을 보관하는 변수
        total = 0
        
        for j in range(i, len(profits)):
            # i부터 j까지 수익의 합을 계산
            total += profits[j]
            
            # i부터 j까지 수익의 합이 최대 수익이라면, max_profit 업데이트
            max_profit = max(max_profit, total)

    return max_profit


# 테스트
print(sublist_max([4, 3, 8, -2, -5, -3, -5, -3]))
print(sublist_max([2, 3, 1, -1, -2, 5, -1, -1]))
print(sublist_max([7, -3, 14, -8, -5, 6, 8, -5, -4, 10, -1, 8]))
```

# 연습 2 : 거듭 제곱 빠르게 계산하기
```
def power(x, y):
    if y == 0:
        return 1

    # 계산을 한 번만 하기 위해서 변수에 저장
    subresult = power(x, y // 2)
    
    # 문제를 최대한 똑같은 크기의 문제 두 개로 나눠준다 (짝수, 홀수 경우 따로)
    if y % 2 == 0:
        return subresult * subresult
    else:
        return x * subresult * subresult


# 테스트
print(power(3, 5))
print(power(5, 6))
print(power(7, 9))
```

# 3. 연습 3 : 빠르게 산 오르기
  - 신입 사원 장그래는 마부장님을 따라 등산을 가게 되었습니다.

    탈수를 방지하기 위해서 1km당 1L의 물을 반드시 마셔야 하는데요. 다행히 등산길 곳곳에는 물통을 채울 수 있는 약수터가 마련되어 있습니다.     다만 매번 줄서 기다려야 한다는 번거로움이 있기 때문에, 시간을 아끼기 위해서는 최대한 적은 약수터를 들르고 싶습니다.

    함수 select_stops는 파라미터로 약수터 위치 리스트 water_stops와 물통 용량 capacity를 받고,  
    장그래가 들를 약수터 위치 리스트를 리턴합니다. 앞서 설명한 대로 약수터는 최대한 적게 들러야겠죠.

    참고로 모든 위치는 km 단위이고 용량은 L 단위입니다. 그리고 등산하기 전에는 이미 물통이 가득 채워져 있으며, 
    약수터에 들르면 늘 물통을 가득 채운다고 가정합시다.
    
    처음에 4L의 물통이 채워져 있기 때문에, 장그래는 약수터에 들르지 않고 최대 4km 지점까지 올라갈 수 있습니다. 
    탈수 없이 계속 올라가기 위해서는 1km 지점이나 4km 지점에서 물통을 채워야겠죠?

    최대한 적은 약수터를 들르면서 올라가야 하고, 마지막에 산 정상인 26km 지점의 약수터를 들르면 성공적인 등산입니다.
```
def select_stops(water_stops, capacity):
    # 코드를 작성하세요. 
    stop_list = []

    # 마지막 들른 약수터 위치
    prev_stop = 0

    for i in range(len(water_stops)):
        # i 지점까지 갈 수 없으면, i - 1 지점 약수터를 들른다
        if water_stops[i] - prev_stop > capacity:
            stop_list.append(water_stops[i - 1])
            prev_stop = water_stops[i - 1]

    # 마지막 약수터는 무조건 간다
    stop_list.append(water_stops[-1])

    return stop_list

# 테스트
list1 = [1, 4, 5, 7, 11, 12, 13, 16, 18, 20, 22, 24, 26]
print(select_stops(list1, 4))

list2 = [5, 8, 12, 17, 20, 22, 23, 24, 28, 32, 38, 42, 44, 47]
print(select_stops(list2, 6))
```

# 4. 중복되는 항목 찾기 I
  - (N + 1)의 크기인 리스트에, 1부터 N까지의 임의의 자연수가 요소로 할당되어 있습니다. 그렇다면 어떤 수는 꼭 한 번은 반복되겠지요.

    예를 들어 [1, 3, 4, 2, 5, 4]와 같은 리스트 있을 수도 있고, [1, 1, 1, 6, 2, 2, 3]과 같은 리스트가 있을 수도 있습니다. 
    (몇 개의 수가 여러 번 중복되어 있을 수도 있습니다.)

    이런 리스트에서 반복되는 요소를 찾아내려고 합니다.

    중복되는 어떠한 수 ‘하나’만 찾아내도 됩니다. 
    즉 [1, 1, 1, 6, 2, 2, 3] 예시에서 1, 2를 모두 리턴하지 않고, 1 또는 2 하나만 리턴하게 하면 됩니다.

    중복되는 수를 찾는 시간 효율적인 함수를 설계해보세요.
```
def find_same_number(some_list):
    elements_seen_so_far = {}

    for element in some_list:
        # 이미 나온 요소인지 확인하고 맞으면 요소를 리턴한다
        if element in elements_seen_so_far:
            return element

        # 해당 요소를 사전에 저장시킨다
        elements_seen_so_far[element] = True
    

# 중복되는 수 ‘하나’만 리턴합니다.
print(find_same_number([1, 4, 3, 5, 3, 2]))
print(find_same_number([4, 1, 5, 2, 3, 5]))
print(find_same_number([5, 2, 3, 4, 1, 6, 7, 8, 9, 3]))

```

# 5. 투자 귀재 규식이 II : Divide and Conquer
    - 저번 챕터에서 sublist_max 함수를 Brute Force 방식으로 작성했습니다. 
      이번에는 같은 문제를 Divide and Conquer 방식으로 풀어볼 텐데요. 시간 복잡도는 O(n\lg{n})O(nlgn)이 되어야 합니다.
      
      이번 sublist_max 함수는 3개의 파라미터를 받습니다.

      profits: 며칠 동안의 수익이 담겨 있는 리스트
      start: 살펴볼 구간의 시작 인덱스
      end: 살펴볼 구간의 끝 인덱스

      sublist_max는 profits의 start부터 end까지 구간에서 가능한 가장 큰 수익을 리턴합니다.

      합병 정렬을 구현할 때 merge_sort 함수를 깔끔하게 작성하기 위해 추가로 merge 함수를 작성했던 것 기억 나시나요? 
      마찬가지로 퀵 정렬을 구현할 때 quicksort 함수에 추가로 partition 함수를 작성했습니다. 
      이번에도 sublist_max 함수에 추가로 새로운 함수를 작성하면 도움이 되실 겁니다.
      
```
def max_crossing_sum(profits, start, end):
    mid = (start + end) // 2      # 중간 인덱스

    '''
    왼쪽에서의 가장 큰 수익 계산
    인덱스 mid부터 인덱스 0까지 범위를 넓혀가며 최대 수익을 찾는다
    '''
    left_sum = 0                  # 왼쪽 누적 수익
    left_max = profits[mid]       # 왼쪽 최고 수익; 왼쪽 반 중 가장 오른쪽 값으로 초기화

    for i in range(mid, start - 1, -1):
        left_sum += profits[i]
        left_max = max(left_max, left_sum)

    '''
    오른쪽에서의 가장 큰 수익 계산
    인덱스 mid+1부터 인덱스 end까지 범위를 넓혀가며 최대 수익을 찾는다
    '''
    right_sum = 0                 # 오른쪽 누적 수익
    right_max = profits[mid + 1]  # 오른쪽 최고 수익; 오른쪽 반 중 가장 왼쪽 값으로 초기화

    for i in range(mid + 1, end + 1):
        right_sum += profits[i]
        right_max = max(right_max, right_sum)

    return left_max + right_max


def sublist_max(profits, start, end):
    # 범위에 하나의 항목밖에 없으면, 그 항목을 리턴한다
    if start == end:
        return profits[start]

    # 중간 인덱스
    mid = (start + end) // 2

    # 상황별로 최대 수익을 구한다
    max_left = sublist_max(profits, start, mid)
    max_right = sublist_max(profits, mid + 1, end)
    max_cross = max_crossing_sum(profits, start, end)

    # 위 세 경우 중 가장 큰 결괏값을 리턴한다
    return max(max_left, max_right, max_cross)


# 테스트
list1 = [-2, -3, 4, -1, -2, 1, 5, -3]
print(sublist_max(list1, 0, len(list1) - 1))

list2 = [4, 7, -6, 9, 2, 6, -5, 7, 3, 1, -1, -7, 2]
print(sublist_max(list2, 0, len(list2) - 1))

list3 = [9, -8, 0, -7, 8, -6, -3, -8, 9, 2, 8, 3, -5, 1, -7, -1, 10, -1, -9, -5]
print(sublist_max(list3, 0, len(list3) - 1))

list4 = [-9, -8, -8, 6, -4, 6, -2, -3, -10, -8, -9, -9, 6, 2, 8, -1, -1]
print(sublist_max(list4, 0, len(list4) - 1))
```