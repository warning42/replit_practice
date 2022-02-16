### 그리디 알고리즘
#### Gready Algorithm은 현재 상황에서 지금 당장 좋은 것만 고르는 방법을 의미한다.

기준에 따라 좋은 것을 선택하는 알고리즘이므로 문제에서 '가장 큰 순서대로', '가장 작은 순서대로'와 같은 기준을 알게 모르게 제시해준다.

그리디 알고리즘 문제는 주로 정렬 알고리즘과 짝을 이뤄 출제된다.

- 대표적인 문제 : 거스름돈 문제 - **가장 큰 화폐 단위**부터 돈을 거슬러 줘야 가장 적은 양의 동전을 주게 된다.

##### 예) 가장 적은 동전으로 거스름돈 걸러 주기
```python
n = 1260
count = 0

# 큰 단위의 화폐부터 차례대로 확인
coin_types = [500, 100, 50, 10]

for coin in coin_types:
  count += n // coin # 해당 화폐로 거슬러 줄 수 있는 동전의 개수 세기
  n %= coin

print(count)
```

단순히 가장 큰 돈에서 가장 작은 돈까지 차례대로 거슬러 주면 된다.
- 그리디 알고리즘 : 정답에 도달할 때까지 선택의 순간마다 최적인 답을 선택한다. 이 예에서는 500원을 2개 고르는 선택, 이후 100원을 2개, 50원 1개, 10원을 1개 고르는 과정이 해당한다.
<br><br>

for 문을 보면 시간 복잡도가 화폐 종류(K)에 관계되어 있음을 알 수 있다.
- 시간 복잡도 - O(K)
<Br><br>

대부분의 그리디 알고리즘 문제는 이렇게 최소한의 아이디어로 이것이 정당한지 검토할 수 있어야 답을 도출할 수 있다.
- 만약 그리디 알고리즘을 쓰다 답을 찾기 힘들다면 다이나믹 프로그래밍이나 그래프 알고리즘 등 다른 방법을 이용하자.
- 화폐 단위가 위처럼 10의 배수 형태가 아니라 무작위로 주어진 경우는 그리디 알고리즘으로는 해결할 수 없고 다이나믹 프로그래밍으로 해결해야 한다.

-----
