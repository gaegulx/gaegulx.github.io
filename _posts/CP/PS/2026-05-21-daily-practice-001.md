---
title: "2026/05/21 PS 일지"
layout: single
categories:
    - cp
subcategories:
    - ps
tags:
    - atcoder
    - combinatorics
    - union_find
toc: true
toc-sticky: true
mathjax: true
author_profile: true
---
오늘은 kenkooo에서 Atcoder 추천 문제를 풀어봤습니다. 계정 생성 후 첫 대회에서 운 좋게 E까지 풀어내면서 블루 퍼포가 나왔는데 그래서인지 Easy 추천에서도 민트가 나옵니다(...)
뭐 그래도 생각보다 풀만했어요!

# ABC151 E. Max-Min Sums
Kenkoo 기준 1344의 난이도를 가지고 있는, 민트 초입의 문제입니다. 태그는 조합론 정도일 거 같네요.

정수집합 $$X$$에 대해, $$f(X) = \text{max} X - \text{min} X$$로 정의합시다. $$N$$개의 정수 $$A_1, \cdots, A_N$$이 주어졌고, 그 중 $$K$$개를 고르고자 합니다.
$$S = \{X \mid X \subset A \And |X| = K\}$$에 대해, $$\sum_{s \in S}{f(S)} \pmod 10^9+7$$을 구하는 문제입니다.

각각의 원소 $$A_i$$에 대해, $$A_i$$가 최대값이 되게 하는 경우의 수는 $$\binom{i}{K - 1}$$이고, $$A_i$$가 최소값이 되게 하는 경우의 수는 $$\binom{N - i}{K - 1}$$입니다.
따라서 팩토리얼 전처리를 통해 $$O(1)$$에 조합을 구할 수 있게 되면, $$O(N)$$에 문제를 해결할 수 있습니다.

```python
import sys
input = lambda: sys.stdin.readline().rstrip()
n, k = map(int, input().split())
a = list(map(int, input().split()))
fact = [1] * (n + 1)
invfact = [1] * (n + 1)
mod = 10**9 + 7
for i in range(1, n+1):
    fact[i] = fact[i - 1] * i % mod
invfact[n] = pow(fact[n], mod - 2, mod)
for i in range(n, 0, -1):
    invfact[i - 1] = invfact[i] * i % mod
def c(n, r):
    if r < 0 or r > n: return 0
    return fact[n] * invfact[r] % mod * invfact[n - r] % mod
a.sort()
res = 0
for i in range(n):
    res += - a[i] * c(n - i - 1, k - 1) % mod
    res += a[i] * c(i, k - 1) % mod
    res %= mod
print(res)
```

# ABC126 E. 1 or 2
이것 또한 Kenkooo 기준 1340을 가지고 있는, 민트 초입의 문제입니다. 태그는 Union-Find고요.

$$N$$개의 카드가 탁자 위에 놓여 있습니다. 각각의 카드에는 1 혹은 2가 적혀 있죠. $$A_i$$가 $$i$$번째 카드의 숫자라 할 때, 우리는 '$$A_X + A_Y + Z$$가 짝수이다'라는 정보를 $$M$$개 받습니다.

마법으로 카드 하나의 숫자를 알아낼 수 있지만 비용 1이 든다고 가정할 때, 모든 카드의 숫자를 알기 위한 최소 비용을 구하는 문제입니다.

매 정보마다 $$Z$$는 임의의 상수이기에, $$A_X + A_Y$$의 parity에 대한 정보를 주는 것으로 볼 수 있습니다. 이때 하나가 정해지면 다른 하나가 정해질 수 있죠.
따라서 정점을 각각의 카드, 간선을 주어진 관계로 놓은 그래프를 만들고, 해당 그래프에서의 connected component 개수를 구하는 방식으로 해결이 가능합니다.
그리고 이를 해결하는 가장 단순한 방법은 Union-Find 알고리즘이죠. (일단 개인적으로는 그렇게 생각합니다.)

이제 Union-Find를 슥슥 짜주면 맞을 수 있습니다.

```python
import sys
input = lambda: sys.stdin.readline().rstrip()
n, m = map(int, input().split())
parent = [i for i in range(n + 2)]
def find(x):
    while parent[x] != x:
        parent[x] = parent[parent[x]]
        x = parent[x]
    return x
def union(x, y):
    x = find(x)
    y = find(y)
    parent[y] = x
for _ in range(m):
    x, y, z = map(int, input().split())
    union(x, y)
res = set()
for x in range(1, n+1):
    res.add(find(x))
print(len(res))
```