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
