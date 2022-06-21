---
title: "[자바 알고리즘 문제풀이] 특정문자 뒤집기"
author: Jinsol
categories: 자바알고리즘
tags: 자바알고리즘
date: '2022-06-21'
# image: /assets/img/.png
---

<br>

## <span style="color:#3AB0FF">**🔒 자바 알고리즘 문제풀이**</span>
<hr>
<hr>

<br>
<br>

## <span style="color:#3AB0FF">**🔐 특정 문자 뒤집어서 출력하기**</span>
<hr>

> ### 문자열을 입력 받은 후, 특수문자를 제외한 알파벳만 뒤집어서(역으로) 출력해보자. 

toCharArray()를 이용한 [[자바 알고리즘 문제풀이] 단어 뒤집어서 출력하기](https://losuif.github.io/2022/05/03/JavaAlgorithm04.html) 두 번째 풀이방법 참고!!

<br>

```java
import java.util.ArrayList;
import java.util.Scanner;

class Main {

    public String solution(String str){
        String answer;

        char[] ch = str.toCharArray();
        int lt = 0;
        int rt = str.length() - 1;

        while (lt < rt) {
            if (!Character.isAlphabetic(ch[lt])) lt++;
            else if (!Character.isAlphabetic(ch[rt])) rt--;
            else {
                char temp = ch[lt];
                ch[lt] = ch[rt];
                ch[rt] = temp;
                lt++;
                rt--;
            }
        }

        answer = String.valueOf(ch);
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
// a~!bc@#d$e%^
// e~!dc@#b$a%^
```