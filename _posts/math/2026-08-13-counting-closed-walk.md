---
title: "Using graph spectrums to count number of closed walks"
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
이번에도 Spectra of Graphs입니다. 네. 또 증명 없는 뭔가가 있어서 들고왔어요. Spectra of Graphs의 Chapter 1.3.3 ‘Walks'는 proposition 하나로 이루어진 짧은 챕터입니다. 그런데 이 proposition의 증명이 없어요.

> 음이 아닌 정수 $h$에 대해, $(A^h)_{xy}$는 $x$에서 $y$로 가는 길이 $h$의 walk의 수이다. (여기서 $A$는 그래프 $\Gamma$의 adjacency matrix)

이 내용은 백준 ‘본대 산책' 시리즈의 핵심적인 내용으로 쓰이기도 합니다. 그럼 증명으로 들어갑시다. $h$에 대한 수학적 귀납법을 통해 증명할 수 있습니다.

가장 먼저, $h = 0$일 때는 자명하게 $A^0 = I$입니다. 여기서 어떤 서로 다른 $x$와 $y$에 대해서도 $x$에서 $y$로 가는 길이 $0$의 walk 개수는 0입니다. 따라서 성립하네요.

또, $h = 1$일 때는 ‘길이 $1$의 walk’ 조건이 ‘서로 인접한가'와 동치임을 간단하게 알 수 있습니다. 따라서 $A^1 = A$이므로, 여기서도 성립하겠네요.

이제 $h ≥ 2$에 대해, $h - 1$이 성립한다고 가정해보고 $h$일 때를 증명해봅시다. 귀납가정에 따라 $(A^{h - 1})\_{xz}$는 $x$에서 $z$로 가는 길이 $h-1$의 walk 수입니다. 또한, $(A^h)\_{xy} = \sum\_{z}{(A^{h-1})\_{xz}}$입니다. 여기서 각 $z$에 대해 $A\_{zy} = 1$이면 $x \rightarrow z$의 길이 $h - 1$ walk에 $y$를 더할 수 있으므로 $x$에서 출발해 $z$를 거쳐 $y$로 가는 길이 $h$짜리 walk가 됩니다. 이를 가능한 모든 정점 $z$에 대해 더해주니 $x \rightarrow y$의 길이 $h$짜리 walk의 개수가 되는 것이죠.

여기서는 $\Gamma$가 undirected simple graph라고 생각했지만, 자연스럽게 directed graph 및 multigraph로도 확장될 수 있음을 알 수 있습니다.

이제 이를 이용해 closed walk의 수를 세 봅시다.

> 음이 아닌 정수 $h$에 대해, $\text{tr}A^h$는 $\Gamma$에서의 길이 $h$의 closed walk의 개수이다.

위의(처음의) Proposition에 따라, $(A^h\)_{xx}$는 $x$에서 출발해 다시 $x$로 돌아오는 closed walk의 수임을 알 수 있습니다. 이를 모든 정점에 대해 더해주면 그래프 $\Gamma$에 포함되는 closed walk의 수가 됩니다. 또한, 이 값은 $\text{tr}A^h = \sum\_i {\theta\_i}^h$를 통해 graph spectrum으로부터 얻을 수 있습니다.