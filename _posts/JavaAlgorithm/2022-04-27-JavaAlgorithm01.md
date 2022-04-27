---
title: "[자바 알고리즘 문제풀이] 특정 문자 개수 찾기"
author: Jinsol
categories: 자바알고리즘
tags: 자바알고리즘
date: '2022-04-27'
# image: /assets/img/.png
---

<br>

## <span style="color:#E04D01">**🔒 자바 알고리즘 문제풀이**</span>
<hr>
<hr>

<br>
<br>

## <span style="color:#E04D01">**🔐 특정 문자 개수 찾기**</span>
<hr>

> ### 문자열을 입력 받고, 특정 문자의 개수를 찾아보자. (+ [향상된 for문](https://losuif.github.io/2021/08/16/JAVA04.html) 사용)

<br>

```java
import java.util.Scanner;

public class Main {

    public int solution(String str, char ch){

        int answer = 0;

        str = str.toUpperCase();
        ch = Character.toUpperCase(ch);

        for(char x : str.toCharArray()) {
            if (x == ch) answer ++;
        }

        return answer;
    }
    
    public static void main(String[] args){

        Main main = new Main();

        Scanner scanner = new Scanner(System.in);
        String str = scanner.next();

        char ch = scanner.next().charAt(0);

        System.out.println(main.solution(str, ch));
    }

}
```

<br>

```
// 출력결과
JavaAlgorithm
a
3
```

<br>

### <span style="color:#E04D01">**🔑 next() vs. nextLine()**</span>
<hr>

- next() : 공백(스페이스) 전까지의 입력받은 문자열

- nextLine() : 엔터 치기 전까지의 모든 문자열

<br>

### <span style="color:#E04D01">**🔑 charAt() / toCharArray()**</span>
<hr>

- charAt() : String 타입의 데이터(문자열)에서 특정 문자를 char 타입으로 변환하는 함수

- charAt(i) : i번째 문자 가져오기

- toCharArray() : 문자열을 char형 배열로 바꿔주는 함수로, 반환되는 배열의 길이는 문자열의 길이와 같음 (문자열의 공백 또한 인덱스에 포함!)