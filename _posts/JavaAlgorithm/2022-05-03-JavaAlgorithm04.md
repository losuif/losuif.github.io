---
title: "[자바 알고리즘 문제풀이] 단어 뒤집어서 출력하기"
author: Jinsol
categories: 자바알고리즘
tags: 자바알고리즘
date: '2022-05-03'
# image: /assets/img/.png
---

<br>

## <span style="color:#82A284">**🔒 자바 알고리즘 문제풀이**</span>
<hr>
<hr>

<br>
<br>

## <span style="color:#82A284">**🔐 단어 뒤집어서 출력하기**</span>
<hr>

> ### n개의 단어를 입력받은 후, 입력 받은 단어들을 뒤집어서(역으로) 출력해보자.

<br>

```
// 출력결과

3
hello
java
salut
olleh
avaj
tulas
```

<br>

### <span style="color:#82A284">**🔓 문자 뒤집기**</span>
<hr>

> ### 본 문제 풀기 전에 문자열 한 개를 입력받아 뒤집어서 출력해보기.

```java
import java.util.Scanner;

public class Main {
   public static void main(String[] args){

       Scanner scanner = new Scanner(System.in);
       String str = scanner.nextLine();

       String reverse = "";

       for (int i = str.length() - 1; i >= 0; i--) {
           reverse = reverse + str.charAt(i);
       }

       System.out.println(reverse);
   }
}
```

<br>

### <span style="color:#82A284">**🔓 StringBuilder() 사용하기**</span>
<hr>

```java
import java.util.ArrayList;
import java.util.Scanner;

class Main {

    public ArrayList<String> solution(int num, String[] str){
        ArrayList<String> answer = new ArrayList<>();

        for (String x : str) {
            String tmp = new StringBuilder(x).reverse().toString();
            answer.add(tmp);
        }

        return answer;
    }

    public static void main(String[] args) {
        Main main = new Main();
        Scanner scanner = new Scanner(System.in);
        int num = scanner.nextInt();
        String[] str = new String[num];

        for (int i = 0; i < num; i++) {
            str[i] = scanner.next();
        }

        for (String x : main.solution(num, str)) {
            System.out.println(x);
        }
    }
}
```