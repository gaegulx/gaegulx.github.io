---
title: "Laplace Expansion and Leibniz formula for determinants"
layout: single
categories:
    - math
tags:
    - linear algebra
    - graph theory
    - spectral graph theory
toc: true
toc-sticky: true
mathjax: true
author_profile: true
---
얼마 전 ‘Spectra of Graphs’라는 자료를 읽던 중 다음과 같은 내용을 발견하게 됩니다.

> $\Gamma$가 $n$개 정점의 유향그래프일 때, 유향 사이클의 union으로 이루어진 유향 부분 그래프 $C$에 대해 $c(C)$를 사이클 개수라 하자. 이때 $\Gamma$의 특성다항식 $p_A(t) = \text{det}(tI - A)$는 $\sum c_it^{n - i}$로 전개될 수 있다. (여기서 $c_i = \sum_C (-1)^{c(C)}$이다.)

근데 이게 왜 될까요? 증명은요? 다행히도, 바로 다음 문단에서 그걸 다루는 것처럼 보입니다.

> 사실, 이것은 행렬식의 정의 중 $\text{det}(M) = \sum_{\sigma} \text{sgn}(\sigma)M_{1\sigma(1)}\cdots M_{n\sigma(n)}$을 고쳐 쓴 것 뿐이다.

제가 원하던 증명이 아니었습니다. 저 정의는 ’Leibniz formula for determinants’라 하는 것 같은데, 저게 왜 성립하는지도 전 몰라요. 그래서 증명을 해보려고 합니다.

일단 임의의 $n \times n$ 행렬의 행렬식을 구하는 방법은 크게 두 가지가 있습니다. Gauss Elimination과 Laplace Expansion이죠. 이 중 Laplace Expansion은 ‘여인수 전개’라고도 알려져 있습니다. 이 중 Laplace Expansion이 더 다루기 간단할 거 같아 Laplace Expansion을 사용했습니다.

$i$번째 행에 대한 Laplace Expansion은 다음의 식으로 나타낼 수 있습니다.

$$
\text{det}(M) = \sum_{j = 1}^{n}{(-1)^{i + j}M_{i, j}\text{det}(M^{(i, j)}))}
$$

이때 $M^{(i, j)}$는 $M$에서 $i$번째 행과 $j$번째 열을 제거함으로서 얻어진 submatrix입니다.

즉, 첫 행에 대해 Laplace Expansion을 진행하면 $\text{det}(M) = \sum_{j = 1}^{n}{(-1)^{j + 1}M_{1,j}\text{det}(M^{(1,j)})}$임을 알 수 있습니다. 여기서 각각의 ‘작은’ 행렬식 $\text{det}(M^{(i, j)})$에 다시 한번 Laplace Expansion을 적용해 봅시다. 여기서도 첫 행에 대해 적용하면, 원래의 $M$에 대해서는 둘째 행이 되겠네요.

이를 계속 진행하면 첫 행에서는 열 $j$를 고르고, 둘째 행에서는 남은 열 중 하나를 고르고, 하는 식으로 이어진다는 것을 알 수 있습니다. 즉 최종적으로 선택되는 열들의 순서를 $\sigma$로 나타낼 수 있게 되죠. 따라서 계속 전개하면 식의 내부가 $f(\sigma)M_{1,\sigma(1)} \cdots M_{n, \sigma(n)}$이 됨을 알 수 있습니다. (여기서 $f(\sigma)$는 각 전개마다 생기는 상수항들의 묶음입니다) 이때 $\sum$ 기호가 쌓이는 것은 중첩된 합을 하나의 ‘모든 순열에 대한 합’으로 바꿔 쓰는 식으로 동시에 없앨 수 있습니다. 즉 $\text{det}(M) = \sum_{\sigma}{f(\sigma)}M_{1,\sigma(1)} \cdots M_{n, \sigma(n)}$이 됩니다.

이제 $f(\sigma)$에 대해 더 알아봅시다. 각 전개에 대해 $(-1)$의 지수는 $($선택한 열을 처음으로 옮기기 위해 필요한 인접 교환 수 $)$가 됩니다. 이를 $q_i$라 합시다. 이때 $f(\sigma) = \prod_{i = 1}^{n}{(-1)^{q_i}} = (-1)^{q_1 + \cdots + q_n}$이 되죠. 이때 간단한 과정을 거쳐 $q_1 + \cdots + q_n = \text{inv}(\sigma)$임을 알 수 있습니다. 따라서 $f(\sigma) = (-1)^{\text{inv}(\sigma)} = \text{sgn}(\sigma)$가 됩니다.

이로서 Leibniz formula를 증명했으니 이것으로 처음 주어진, 사이클 관련 식을 증명해 봅시다.

먼저 $\sigma$의 cycle decomposition이, Adjacency Matrix에서는 실제 그래프 내의 directed cycle이 됨을 알 수 있습니다. 이는 $(tI - A)\_{i, \sigma(i)}$에서 $\sigma(i) \neq i$라면 $(tI - A)\_{i, \sigma(i)} = -A\_{i, \sigma(i)}$이며, 이 항이 0이 아니려면 $i \rightarrow \sigma(i)$의 간선이 있어야 함을 알 수 있습니다. 즉 순열의 사이클에 대해, 해당 Leibniz 항이 결과에 영향을 미치려면 그 사이클에 대응되는 directed cycle이 존재해야 합니다.

여기서 fixed point, 즉 $\sigma(i) = i$인 $i$의 경우 $(tI - A)\_{i,i} = t - A\_{i, i}$이고, loop가 없을 경우 $A_{i, i} = 0$이므로 $(tI - A)_{i, i} = t$가 됩니다. 이것이 모든 fixed point에 대해 성립하므로, cycle들의 union이 총 $i$개의 점을 차지하는 경우 fixed point는 $n - i$개이고 $t^{n - i}$항으로 반영되게 됩니다.

이제 앞의 부호 부분을 봅시다. 사이클 길이가 각각 $l_1, l_2, \cdots, l_{c(C)}$라면 $\sum_{i = 1}^{c(C)}{l_i} = k$이고, 길이 $l$인 사이클 하나의 부호는 $(-1)^{l - 1}$으로 볼 수 있습니다. 따라서 $\text{sgn}(\sigma) = (-1)^{k - c(C)}$이고, fixed point를 제외한 정점은 모두 off-diagonal entry를 사용하므로 각각 $-1$이 하나씩 나오게 됩니다. 여기서 나온 $-1$들을 모두 곱해주면 $(-1)^{2k - c(C)}$가 되고, 이는 $(-1)^{c(C)}$와 같은 값이 됩니다.

따라서 우리는 $\Gamma$의 특성다항식 $p_A(t) = \text{det}(tI - A)$는 $\sum c_it^{n - i}$로 전개될 수 있음을 알 수 있습니다!