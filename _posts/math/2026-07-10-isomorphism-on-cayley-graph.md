---
title: "[논문 리뷰] Isomorphism and Cayley graphs on abelian groups"
layout: single
categories:
    - math
subcategories:
    - 논문리뷰
tags:
    - graph-isomorphism
    - group-theory
    - graphs
toc: true
toc-sticky: true
mathjax: true
author_profile: true
---
2학기 연구기초세미나 주제에 관련한 논문을 조금씩 읽어보고 있습니다. 일단 지금 제 주제는 Graph Isomorphism이네요.
이 아래부터는 논문의 흐름을 따라가며 나오는 내용들을 정리한 내용입니다. 리뷰에 걸맞은 논평은.. 아직 쓸 능력이 안되네요.

## Part 1.
**Definition.** Cayley Subset은 아래의 조건을 만족시키는, 유한군 $$G$$의 부분집합 $$S$$를 나타냅니다.

(1) $$1 \notin S$$. 즉, $$S$$는 항등원을 포함하지 않습니다.

(2) $$s \in S \Leftrightarrow s^{-1} \in S$$. $$S$$의 모든 원소에 대해 그 원소의 역원은 $$S$$에 포함됩니다.

**Definition.** Cayley Graph는 Cayley Subset을 통해 정의되는 그래프입니다. 유한군 $$G$$와 $$G$$의 Cayley Subset $$S$$에 대해, Cayley Graph $$X(G;S)$$는 아래와 같이 정의됩니다.

$$V(X) = G$$, $$E(X) = \{gh \mid \exists s \in S \text{ s.t. } h = gs\}$$

즉, $$S$$의 원소를 통해 $$u$$가 $$v$$로 변할 수 있다면 $$u$$와 $$v$$ 사이 간선이 존재합니다.

**Definition.** Automorphism은 연결성을 보존하는, 그래프 $$X$$의 정점 집합에 대한 permutation입니다. 이때 $$\text{Aut}(X)$$는 $$X$$의 automorphism으로 이루어진 permuation group을 나타냅니다.