---
title: "[그래프이론] Preliminaries & 그래프"
layout: single
categories:
    - math
subcategories:
    - 그래프이론
tags:
    - graphs
toc: true
toc-sticky: true
mathjax: true
author_profile: true
---

그래프 이론은 정점과 간선이라는 단순한 구조를 기반으로 하는 분야입니다. 하지만 그럼에도 조합론, 선형대수학, 위상수학 등과 밀접한 관련이 있죠.
그런 면에서 오히려 '대상들이 어떻게 연결되어 있는가'를 수학적으로 다루는 언어에 가깝다고 봐도 좋습니다. 또한 그래프 이론은 현대 컴퓨터 과학과 수학의 기반 중 하나이죠.  

PS를 하시던 분들이라면 그래프에 익숙하실 것입니다. 그러나 이번에는 피상적으로 다루던 내용들을 넘어, 조금 더 수학적으로 접근해보려고 합니다.
물론 저도 공부 중인 분야기에 잘못된 정보가 있을 수 있습니다. 수정사항이 있다면 언제든 메일 보내주세요!

책은 Springer 출판사에서 출판한 Reinhard Diestel의 \<Graph Theory\>를 사용합니다.

# Preliminaries
본격적으로 그래프를 살펴보기 전에, 저희가 사용할 몇 가지 기본적인 표기법에 대해 알아봅시다.

$$\mathbf{N}$$은 **0을 포함한** 자연수 집합을 말합니다. 정수 모듈로 $$n$$의 집합 $$\mathbf{Z}/n\mathbf{Z}$$은 $$\mathbf{Z}_n$$으로 표기되고, 그 원소는
$$\bar{i} = i + n\mathbf{Z}$$로 나타냅니다. $$\mathbf{Z}_2 = \{0, 1\}$$을 체로서 다룰 때는, $$\mathbf{F}_2 = \{0, 1\}$$으로 표기하기도 합니다.