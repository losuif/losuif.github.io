---
title: "[자바 알고리즘 문제풀이] 뒤집어도 똑같은 문자열"
author: Jinsol
categories: 자바알고리즘
tags: 자바알고리즘
date: '2022-06-24'
# image: /assets/img/.png
---

<br>

## <span style="color:#937DC2">**🔒 자바 알고리즘 문제풀이**</span>
<hr>
<hr>

<br>
<br>

## <span style="color:#937DC2">**🔐 뒤집어도 똑같은 문자열**</span>
<hr>

> 대소문자에 관계없이 문자열을 앞뒤로 뒤집었을 때 같으면 SUCCESS, 다르면 FAIL을 출력해보자. 

```java
import java.util.Scanner;

class Main {

    public String solution(String str){
        String answer = "SUCCESS";
        str = str.toUpperCase();
        int len = str.length();

        for (int i = 0; i < len / 2; i++) {
            if (str.charAt(i) != str.charAt(len - i - 1)) return "FAIL";
        }

        return answer;
    }

    public static void main(String[] args) {
        Main main = new Main();

        Scanner scanner = new Scanner(System.in);
        String str = scanner.nextLine();

        System.out.println(main.solution(str));
    }
}
```

<br>

```
출력결과

java
FAIL

ABcba
SUCCESS
```