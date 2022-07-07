---
title: "[자바 알고리즘 문제풀이] 더 큰 수 출력하기"
author: Jinsol
categories: 자바알고리즘
tags: 자바알고리즘
date: '2022-07-07'
# image: /assets/img/.png
---

<br>

## <span style="color:#898AA6">**🔒 자바 알고리즘 문제풀이**</span>
<hr>
<hr>

<br>
<br>

## <span style="color:#898AA6">**🔐 더 큰 수 출력하기**</span>
<hr>

> n개의 숫자를 입력 받고, 바로 앞 숫자보다 큰 숫자만 출력하기 (첫 번째 숫자는 무조건 출력)

<br>

```java
import java.util.ArrayList;
import java.util.Scanner;

class Main {

    public ArrayList<Integer> solution(int n, int[] arr){
        ArrayList<Integer> answer = new ArrayList<>();

        answer.add(arr[0]);

        for (int i = 1; i < n; i++) {
            if (arr[i] > arr[i-1]) answer.add(arr[i]);
        }

        return answer;
    }

    public static void main(String[] args) {
        Main main = new Main();

        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();
        int[] arr = new int[n];

        for (int i = 0; i < n; i++) {
            arr[i] = scanner.nextInt();
        }
        for (int num : main.solution(n, arr)) {
            System.out.print(num + "\t");
        }
    }
}
```

<br>

```
출력결과

5
1 17 3 56 10
1	17	56	
```