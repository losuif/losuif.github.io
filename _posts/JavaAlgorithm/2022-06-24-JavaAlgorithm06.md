---
title: "[자바 알고리즘 문제풀이] 중복 문자 제거 / .indexOf()"
author: Jinsol
categories: 자바알고리즘
tags: 자바알고리즘
date: '2022-06-24'
# image: /assets/img/.png
---

<br>

## <span style="color:#A084CF">**🔒 자바 알고리즘 문제풀이**</span>
<hr>
<hr>

<br>
<br>

## <span style="color:#A084CF">**🔐 중복 문자 제거하기**</span>
<hr>

> ### 입력받은 문자열 중 중복되는 문자는 제거하고 출력해보자. ex) hello -> helo

<br>

### <span style="color:#A084CF">**🔑 .indexOf()**</span>
<hr>

- 매개값으로 주어진 문자열이 시작되는 인덱스를 리턴

- 주어진 문자열이 포함되어 있지 않으면 -1 리턴

- [indexOf()와 substring()를 이용한 가장 긴 단어 찾기](https://losuif.github.io/2022/04/30/JavaAlgorithm03.html)


```java
import java.util.Scanner;

class Main {

    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);
        String str = scanner.nextLine();

        for (int i = 0; i < str.length(); i++) {
            System.out.println(str.charAt(i) + "\t" + i + "\t" + str.indexOf(str.charAt(i)));
        }
    }
}
```

<br>

```
출력결과

java
j	0	0
a	1	1
v	2	2
a	3	1
```

<br>
<br>

### <span style="color:#A084CF">**🔓 .indexOf()를 이용한 중복 문자 제거**</span>
<hr>

```java
import java.util.Scanner;

class Main {

    public String solution(String str){
        String answer = "";

        for (int i = 0; i < str.length(); i++) {

            if (i == str.indexOf(str.charAt(i))){
                answer += str.charAt(i);
            } else continue;
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

Strawberry
Strawbey
```