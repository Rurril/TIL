# 세그먼트 트리(Segment Tree)


## 정의

구간들을 보존하고 있는 트리다.

![](https://leetcode.com/articles/Figures/segtree_intro_1.png)

위의 그림들을 기준으로 리프 노드들은 배열 하나의 값들을 가지고, 그 위의 부모는 자식 노드들의 구간의 합 만큼의 구간에 대한 값을 가진다. 

## 특징

주어진 쿼리에 대해 빠르게 응답하기 위해서 만들어진 자료구조다.

[백준 문제 : 구간 합 구하기](https://www.acmicpc.net/problem/2042) 에서 각 구간에 대한 합을 구해야 하는데, 중간에 요소에 대한 UPDATE 쿼리가 일어나고, 최대 100만번까지 변경이 이루어진다. 

이때 변경에 대한 쿼리와 구간 합을 구하는 쿼리가 시간복잡도가 높은 연산으로 이루어지게 된다면 문제는 시간초과가 나게 된다.

각 구간을 배열로 구현하게 된다면, 수를 바꾸는 데 O(1), 수를 더하는 부분합의 구현에는 O(N)이 걸리고, M번의 쿼리를 실행하게 된다면, O(MN + M) = O(MN)의 시간이 걸리게 된다.

이 때, 세그먼트 트리를 이용한다면 각 연산(변경, 부분합)을 O(logN)으로 해결할 수 있다. 

세그먼트 트리의 루트 노드의 높이 h = 0 이라고 할 때, 

> 세그먼트 트리의 높이는 리프 노드(배열의 크기) N개일 때, log2(N)_의 올림 값이 된다. 

> 또한, 세그먼트 트리의 최대 크기는 2^(h+1)이 된다. 

> 루트 노드의 index를 1로 설정함으로써 부모 노드와 자식 노드의 관계를 표현하게 쉽게 구현한다.

>> 부모 노드의 (index * 2) 와 (index * 2 + 1)이 자식 노드의 index가 된다. 


대표적인 세그먼트 트리의 구간 정보로 **구간에 속한 원소들의 합**이 되겠다. 

위에 링크를 걸어놓은 문제가 세그먼트 트리의 기본적인 문제고, 이외에도 구간의 정보를 구하는 문제들을 응용으로 하여 구현할 수 있다. 

### [문제 구현한 것 정리한 것 참고](https://github.com/Rurril/Problem-Solving/blob/Test/Problem-Solving/PS/SegmentTree/N2042.java)

## 🤭 참고 문제

> [백준 온라인 저지 - 세그먼트 트리](https://github.com/Rurril/Problem-Solving/tree/Test/Problem-Solving/PS/SegmentTree)


## 💌 참고자료

1. [Ries 마법의 슈퍼마리오](http://blog.naver.com/PostView.nhn?blogId=kks227&logNo=220791986409&categoryNo=299&parentCategoryNo=299&viewDate=&currentPage=10&postListTopCurrentPage=1&from=postList&userTopListOpen=true&userTopListCount=5&userTopListManageOpen=false&userTopListCurrentPage=10)
2. [LeetCode](https://leetcode.com/articles/a-recursive-approach-to-segment-trees-range-sum-queries-lazy-propagation/)