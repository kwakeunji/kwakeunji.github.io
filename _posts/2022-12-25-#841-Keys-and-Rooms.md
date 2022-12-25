---
layout: post
title:  "[LeetCode]2022-12-25-#841-keys-and-rooms"
date:   2022-12-25 13:01:04 +0900
categories: jekyll update
---

# [문제](https://leetcode.com/problems/keys-and-rooms/description/)

There are `n` rooms labeled from `0` to `n - 1` and all the rooms are locked except for room `0`. Your goal is to visit all the rooms. However, you cannot enter a locked room without having its key.

When you visit a room, you may find a set of **distinct keys** in it. Each key has a number on it, denoting which room it unlocks, and you can take all of them with you to unlock the other rooms.

Given an array `rooms` where `rooms[i]` is the set of keys that you can obtain if you visited room `i`, return `true` *if you can visit **all** the rooms, or* `false` *otherwise*.

[문제해석]

input: room array, set of room keys

output: room 방문할 때마다 True 반환, 다 방문할 수 있으면 False 반환

### example 1:

```
Input: rooms = [[1],[2],[3],[]]
Output: true
Explanation:
We visit room 0 and pick up key 1.
We then visit room 1 and pick up key 2.
We then visit room 2 and pick up key 3.
We then visit room 3.
Since we were able to visit every room, we return true.
```

### example 2:

```
Input: rooms = [[1,3],[3,0,1],[2],[0]]
Output: false
Explanation: We can not enter room number 2 since the only key that unlocks it is in that room.
```

### 제한조건

- `n == rooms.length`
- `2 <= n <= 1000`
- `0 <= rooms[i].length <= 1000`
- `1 <= sum(rooms[i].length) <= 3000`
- `0 <= rooms[i][j] < n`
- All the values of `rooms[i]` are **unique**.

# [풀이]

1. BFS(너비 우선 탐색

```python
class Solution:
    def canVisitAllRooms(self, rooms: List[List[int]]) -> bool:

        seen = set([False]) #set()을 씀으로써 봤던 곳을 또 보는 과정 생략
				stack = [0] #key 저장

				while stack:
					#큐 구현
					value = stack.pop()

					for i in rooms[value]:
						if i not in seen:
							seen.add(i)
	
							if len(seen) == len(rooms):
								return True
							stack.append(i)

				return len(stack) == len(rooms)
```

# [배운점]

- 큐 구현하는 방법 ⇒ 여전히 어렵다.. 자료구조를 이용한 문제를 많이 풀어봐여 할 것 같음
