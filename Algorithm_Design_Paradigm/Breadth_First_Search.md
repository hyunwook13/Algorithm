# **BFS (Breadth-First Search) - 너비 우선 탐색**

  

### **1. 개념 설명 (What is it?)**

-   BFS는 그래프나 트리에서 **가까운 노드부터 차례대로** 탐색하는 알고리즘입니다.
    
-   **큐(Queue)** 자료구조를 사용해 구현하며, 한 노드의 모든 인접 노드를 방문한 뒤 다음 레벨로 이동합니다.
    


### **2. 사용하는 이유 (Why use it?)**

-   **최단 거리** 탐색에 유리 (가중치 없는 그래프에서)
    
-   **트리의 레벨 탐색**, **최소 이동 횟수 계산** 등에서 활용
    
-   DFS보다 **메모리 효율적**일 수 있음 (재귀 깊이 제한 없음)
    


### **3. 적용 조건 (When to use it?)**

-   최단 거리, 최소 단계 등 **거리 개념이 있는 문제**
    
-   모든 노드의 **방문 순서가 중요**한 경우
    
-   **재귀 제한** 없이 구현하고 싶을 때
    

  

> 제한: 큐 크기 증가로 인한 **메모리 부담** 가능 (노드가 매우 많을 경우)


### **4. 알고리즘 구조 (How it works)**

1.  시작 노드를 큐에 삽입하고 방문 처리
    
2.  큐가 빌 때까지 반복:
    
    -   현재 노드를 큐에서 꺼냄
        
    -   연결된 노드 중 방문하지 않은 노드를 큐에 넣고 방문 처리
        
    
3.  모든 노드를 탐색할 때까지 반복
    


### **5. 시간 복잡도 & 공간 복잡도**


| 복잡도 종류 | 값                  |
|-------------|---------------------|
| 시간 복잡도 | O(V + E)            | // V: 정점 수, E: 간선 수
| 공간 복잡도 | O(V)                | // 방문 배열 + 큐 or 스택


### **6. 예제 코드 (Code Example)**

```
func bfs(_ graph: [[Int]], _ start: Int) {
    var visited = Array(repeating: false, count: graph.count)
    var queue = [start]
    visited[start] = true

    while !queue.isEmpty {
        let node = queue.removeFirst()
        print("방문:", node)

        for next in graph[node] {
            if !visited[next] {
                visited[next] = true
                queue.append(next)
            }
        }
    }
}

let graph = [
    [],         // 0번 노드 사용 안 함
    [2, 3],
    [1, 4],
    [1, 5],
    [2],
    [3]
]

bfs(graph, 1)

// 출력 예시: 1 → 2 → 3 → 4 → 5
```

### **7. 실전 문제 예시**

-   [백준 1260번 - DFS와 BFS](https://www.acmicpc.net/problem/1260)
    
-   [백준 7576번 - 토마토](https://www.acmicpc.net/problem/7576)
    
-   [LeetCode 102 - Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/)
    


### **8. 주의할 점 / 실수하기 쉬운 부분**

-   **방문 처리를 큐에 넣을 때 해야 함** → 중복 방문 방지
    
-   DFS와 달리 큐이므로 **방문 순서가 정해짐**
    
-   **큐 크기 증가**에 따른 메모리 사용 주의
    


### **9. 관련 알고리즘**

-   **DFS (깊이 우선 탐색)**: 깊게 먼저 들어가며 탐색 (스택 기반/재귀)
    
-   **다익스트라 알고리즘**: BFS에서 가중치를 고려한 형태
    
-   **A***: BFS + 휴리스틱 = 최적 경로 탐색에 특화
    

