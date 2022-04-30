---
title: "[자바 알고리즘 문제풀이] 대소문자 변환하기"
author: Jinsol
categories: 자바알고리즘
tags: 자바알고리즘
date: '2022-04-29'
# image: /assets/img/.png
---

<br>

## <span style="color:#006E7F">**🔒 자바 알고리즘 문제풀이**</span>
<hr>
<hr>

<br>
<br>

## <span style="color:#006E7F">**🔐 대소문자 변환하기**</span>
<hr>

> ### 입력받은 대문자를 소문자로, 소문자를 대문자로 바꿔보자.

<br>

### <span style="color:#006E7F">**🔓 toUpperCase() / to LowerCase() 이용하기**</span>
<hr>

```java
import java.util.Scanner;

public class Main {

    public String solution(String str){

        String answer = "";

        for (char ch : str.toCharArray()) {

            if (Character.isLowerCase(ch)){
                answer += Character.toUpperCase(ch);

            } else {
                answer += Character.toLowerCase(ch);
            }
        }

        return answer;
    }

    public static void main(String[] args){

        Main main = new Main();

        Scanner scanner = new Scanner(System.in);
        String str = scanner.next();

        System.out.println(main.solution(str));
    }
}
```

<br>
<br>

### <span style="color:#006E7F">**🔓 아스키코드 이용하기**</span>
<hr>

```java
import java.util.Scanner;

public class Main {

    public String solution(String str){
        String answer = "";

        //대문자 : 65~90
        //소문자 : 97~122
        for (char ch: str.toCharArray()) {

            if (ch >= 65 && ch <= 90){
                answer += (char)(ch + 32);

            } else if (ch >= 97 && ch <= 122){
                answer += (char)(ch - 32);
            }
        }

        return answer;
    }

    public static void main(String[] args){

        Main main = new Main();

        Scanner scanner = new Scanner(System.in);
        String str = scanner.next();
        System.out.println(main.solution(str));
    }
}
```

<br>

```
// 출력결과
JAVA
java

// 출력결과
algorithm
ALGORITHM
```

