---
title: "[자바 알고리즘 문제풀이] 단어 뒤집어서 출력하기 / StringBuilder / toCharArray()"
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

<br>

### <span style="color:#82A284">**🔑 StringBuilder**</span>
<hr>

> [String vs. StringBuilder vs. StringBuffer](https://losuif.github.io/2021/09/13/JAVA24.html)

-   - 객체 선언 : StringBuilder sb = new StringBuilder();

    - 문자열 바로 넣기 : StringBuilder sb = new StringBuilder("문자열");

- StringBuilder 메서드

    - `.append()` : 문자열 추가

    - `.insert(int n, String str)` : n 위치에 str 추가

    - `.replace(idx1, idx2, str)` : idx1 부터 idx2 까지의 값을 str로 변경

    - `.substring(int start (, int end))` : 인덱스 번호 start 부터 end 직전 까지의 값을 리턴

    - `.deleteCharAt(int n)` : n번째 인덱스의 문자 한 개 삭제

    - `.delete(int start, int end)` : start 부터 end 직전 까지의 문자 삭제

    - `.toString()` : String으로 변환 

    - `.reverse()` : 문자열 전체 뒤집기

    - `.length()` : 길이 리턴

    - `.indexOf(ch)` : ch가 위치한 인덱스 값 리턴, 여러개라면 제일 앞 인덱스 위치

    - `.setCharAt(int idx, String s)` : idx 위치의 문자 s로 변경

    - `.setLength(int len)` : len 길이만큼 자르거나, 공백으로 채우기


<br>
<br>

### <span style="color:#82A284">**🔓 toCharArray(), 값 교환 해 뒤집기**</span>
<hr>

```java
import java.util.ArrayList;
import java.util.Scanner;

class Main {

    public ArrayList<String> solution(int num, String[] str){
        ArrayList<String> answer = new ArrayList<>();

        for (String x : str) {
            char[] ch = x.toCharArray();

            int lt = 0;
            int rt = x.length() - 1;

            while (lt < rt) {
                // lt, rt 값 교환
                char temp = ch[lt];
                ch[lt] = ch[rt];
                ch[rt] = temp;
                
                lt++;
                rt--;
            }
            String temp = String.valueOf(ch);
            answer.add(temp);
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

<br>

### <span style="color:#82A284">**🔑 toCharArray()**</span>
<hr>

> [charAt() / toCharArray()](https://losuif.github.io/2022/04/27/JavaAlgorithm01.html)