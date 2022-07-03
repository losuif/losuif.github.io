---
title: "[자바 알고리즘 문제풀이] 뒤집어도 똑같은 문자열 / replaceAll()"
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

## <span style="color:#937DC2">**🔐 뒤집어도 똑같은 문자열 ☝**</span>
<hr>

> 대소문자에 관계없이 문자열을 앞뒤로 뒤집었을 때 같으면 SUCCESS, 다르면 FAIL을 출력해보자. 

<br>

### <span style="color:#937DC2">**🔓 .charAt()**</span>
<hr>

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
<br>

### <span style="color:#937DC2">**🔓 StringBuilder()**</span>
<hr>

```java
import java.util.Scanner;

class Main {

    public String solution(String str){
        String answer = "FAIL";
        String temp = new StringBuilder(str).reverse().toString();

        if (str.equalsIgnoreCase(temp)) answer = "SUCCESS";

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

<br>
<hr>
<hr>
<br>
<br>

## <span style="color:#937DC2">**🔐 뒤집어도 똑같은 문자열 ✌**</span>
<hr>

> 숫자나 특수문자는 무시하고 알파벳만 따졌을 때, 대소문자에 관계없이 문자열을 앞뒤로 뒤집어서 같으면 SUCCESS, 다르면 FAIL을 출력해보자.

<br>

```java
import java.util.Locale;
import java.util.Scanner;

class Main {

    public String solution(String str){
        String answer = "FAIL";
        str = str.toUpperCase().replaceAll("[^A-Z]", "");

        String tmp = new StringBuilder(str).reverse().toString();
        if (str.equals(tmp)) answer = "SUCCESS";

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

A12$(#)BC459p5cba
SUCCESS

ab!2#4Bc
FAIL
```

<br>

### <span style="color:#A084CF">**🔑 .replaceAll()**</span>
<hr>

- `String replaceAll(String regex, String replacement)` : 첫번째 인자값 - 변환하고자 하는 대상, 두번째 인자값 - 변환할 문자 값

- [Character classes](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/regex/Pattern.html#sum)
    
    - `[abc]` :	a, b, or c (simple class)

    - `[^abc]` : Any character except a, b, or c (negation)

    - `[a-zA-Z]` : a through z or A through Z, inclusive (range)

    - `[a-d[m-p]]` : a through d, or m through p: `[a-dm-p]` (union)

    - `[a-z&&[def]]` : d, e, or f (intersection)

    - `[a-z&&[^bc]]` : a through z, except for b and c: `[ad-z]` (subtraction)

    - `[a-z&&[^m-p]]` : a through z, and not m through p: `[a-lq-z]`(subtraction)