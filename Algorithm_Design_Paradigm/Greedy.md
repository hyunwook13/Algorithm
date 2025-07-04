
# **Greedy Algorithm (탐욕 알고리즘)**

  

### **1. 개념 설명 (What is it?)**

-   Greedy는 매 순간 **현재 상태에서 가장 최선의 선택**을 하는 방식입니다.
    
-   전체 최적해를 보장하지는 않지만, 특정 조건에서는 **정확하고 빠른 해**를 제공합니다.
    
-   일반적으로 **정렬, 우선순위 큐**를 함께 사용하는 경우가 많습니다.
    

  

### **2. 사용하는 이유 (Why use it?)**

-   **빠르게 근사해 또는 최적해**를 구하고 싶을 때
    
-   **복잡한 탐색 없이도 정답을 구할 수 있는 구조**일 때
    
-   DP보다 **간단하고 빠른 구현**이 가능
    

  

### **3. 적용 조건 (When to use it?)**

-   **탐욕적 선택 속성 (Greedy Choice Property)**:
    
    항상 지역 최적 선택이 전역 최적해로 이어져야 함
    
-   **최적 부분 구조 (Optimal Substructure)**:
    
    전체 문제의 최적해가 부분 문제의 최적해로 구성되어야 함
    

  

→ 이 두 조건이 **모두 만족**해야 Greedy가 정확한 해를 보장함

  

### **4. 알고리즘 구조 (How it works)**

1.  전체 입력을 특정 기준에 따라 **정렬**
    
2.  조건을 만족하는 원소를 하나씩 선택
    
3.  선택 후 다음 단계로 이동 (선택 결과를 반영)
    
4.  더 이상 선택할 수 없을 때까지 반복
    

  

### **5. 시간 복잡도 & 공간 복잡도**

| 복잡도 종류 | 값                    | 설명                                      |
|-------------|------------------------|-------------------------------------------|
| 시간 복잡도 | O(N log N + N * D)     | N: 작업 수, D: 최대 deadline              |
| 공간 복잡도 | O(N + D)               | 정렬용 배열 + 사용된 날짜 저장용 Set       |

### **6. 예제 코드 (Code Example)**

```
struct Task {
    let deadline: Int
    let reward: Int
}

func greedyExample(_ tasks: [Task]) -> Int {
    let sorted = tasks.sorted { $0.reward > $1.reward } // 보상 기준 내림차순
    var dayUsed = Set<Int>()
    var total = 0

    for task in sorted {
        for d in stride(from: task.deadline, through: 1, by: -1) {
            if !dayUsed.contains(d) {
                dayUsed.insert(d)
                total += task.reward
                break
            }
        }
    }

    return total
}
```

### **7. 실전 문제 예시**

-   [백준 11047번 - 동전 0](https://www.acmicpc.net/problem/11047)
    
-   [백준 1931번 - 회의실 배정](https://www.acmicpc.net/problem/1931)
    
-   [프로그래머스 - 단속카메라](https://school.programmers.co.kr/learn/courses/30/lessons/42884)
    

  

### **8. 주의할 점 / 실수하기 쉬운 부분**

-   **탐욕적 선택이 항상 최적을 보장하지 않음**
    
-   **문제 조건을 면밀히 분석해야 함** — 단순히 정렬하고 선택한다고 끝이 아님
    
-   DP와의 차이를 구별하는 것이 중요
    
    → 같은 문제라도 그리디로 풀면 틀리는 경우 많음
    

  

### **9. 관련 알고리즘**

-   **DP (동적 계획법)**: 중복 계산 줄이며 정확한 해 도출
    
-   **Kruskal 알고리즘**: 최소 신장 트리 (Greedy + Union-Find)
    
-   **Dijkstra 알고리즘**: 최단 거리 (Greedy + PriorityQueue)
    
