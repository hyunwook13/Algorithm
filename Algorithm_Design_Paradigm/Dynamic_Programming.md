# 🧠 Dynamic Programming

### 1. 개념 설명 (What is it?)

- 큰 문제를 작은 문제로 나누고, 부분 문제의 결과를 저장해 중복 계산 없이 전체 문제를 해결하는 최적화 알고리즘 기법.

### 2. 사용하는 이유 (Why use it?)

- 중복 계산을 줄여 시간 복잡도를 획기적으로 개선할 수 있음
- 완전 탐색보다 훨씬 효율적이며, 탐욕법으로는 해결 불가능한 최적화 문제에도 사용 가능

### 3. 적용 조건 (When to use it?)

- Optimal Substructure (최적 부분 구조)
    - 큰 문제의 최적해가 작은 문제의 최적해로부터 구성될 수 있어야 함
- Overlapping Subproblems (중복 부분 문제
    - 동일한 하위 문제가 여러 번 반복해서 등장

### 4. 알고리즘 구조 (How it works)

1. 하향식 (Top-Down) – 재귀 + 메모이제이션
- f(n) = f(n-1) + f(n-2)처럼 재귀적으로 문제를 나눔
    - 계산된 결과는 memo[n]에 저장해 중복 계산 방지
1. 상향식 (Bottom-Up) – 반복문 + DP 테이블
- 작은 문제부터 차례로 해결하며 **테이블(dp 배열)**을 채움
    - 초기 조건부터 시작해, 반복문으로 점진적으로 확장

### 5. 시간 복잡도 & 공간 복잡도

- 시간 복잡도: 문제마다 다르지만 일반적으로 O(n) 또는 O(n * m)
- 공간 복잡도: O(n) 이상 (테이블 또는 캐시의 크기에 따라 다름)
- 상향식에서는 **공간 최적화 (2개의 변수로 축소)**도 가능

### 6. 예제 코드 (Code Example)

- 피보나치 수열 – Top-Down with Memoization

```swift
var memo = [Int](repeating: -1, count: 100)

func fib(_ n: Int) -> Int {
    if n <= 1 { return n }
    if memo[n] != -1 {
        return memo[n]
    }
    memo[n] = fib(n - 1) + fib(n - 2)
    return memo[n]
}
```

- 피보나치 수열 – Bottom-Up

```swift
func fib(_ n: Int) -> Int {
    if n <= 1 { return n }
    var dp = [Int](repeating: 0, count: n + 1)
    dp[1] = 1

    for i in 2...n {
        dp[i] = dp[i - 1] + dp[i - 2]
    }

    return dp[n]
}
```

### 7. 실전 문제 예시 (Practice Problems)

- 백준 1463 – 1로 만들기
- LeetCode 198 – House Robber
- 프로그래머스 – 정수 삼각형

### 8. 주의할 점 / 실수하기 쉬운 부분

- 경계 조건(초기값) 설정이 틀리면 전체 DP가 무너질 수 있음
- 재귀로 할 경우 최대 호출 깊이 초과 주의
- 반복문 범위 설정을 잘못하면 off-by-one 오류 발생

### 9. 관련 알고리즘 / 패턴

- DFS + Memoization (탑다운 DP의 또 다른 형태)
- Knapsack Problem
- Divide and Conquer DP
- Bitmask DP, LIS(Longest Increasing Subsequence)
