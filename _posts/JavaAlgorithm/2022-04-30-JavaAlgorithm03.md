---
title: "[자바 알고리즘 문제풀이] 가장 긴 단어 찾기"
author: Jinsol
categories: 자바알고리즘
tags: 자바알고리즘
date: '2022-04-30'
# image: /assets/img/.png
---

<br>

## <span style="color:#7FB5FF">**🔒 자바 알고리즘 문제풀이**</span>
<hr>
<hr>

<br>
<br>

## <span style="color:#7FB5FF">**🔐 가장 긴 단어 찾기**</span>
<hr>

> ### 문장을 입력 받고, 가장 긴 단어를 찾아보자.

<br>

### <span style="color:#7FB5FF">**🔓 split() 이용하기**</span>
<hr>

```java
import java.util.Scanner;

public class Main {

    public String solution(String str){

        String answer = "";
        int max = 0;
        String[] s = str.split(" ");

        for (String x : s) {
            int len = x.length();
            
            if (len > max) {
                max = len;
                answer = x;
            }
        }

        return answer;
    }

    public static void main(String[] args){

        Main main = new Main();

        Scanner scanner = new Scanner(System.in);
        String str = scanner.nextLine();

        System.out.println(main.solution(str));
    }
}
```

<br>
<br>

### <span style="color:#7FB5FF">**🔓 indexOf() / substring() 이용하기**</span>
<hr>
<br>

```java
import java.util.Scanner;

public class Main {

    public String solution(String str){

        String answer = "";
        int max = 0;
        int pos;

        while ((pos = str.indexOf(" ")) != -1){
            String tmp = str.substring(0, pos);
            int len = tmp.length();

            if (len > max) {
                max = len;
                answer = tmp;
            }

            str = str.substring(pos + 1);
        }

        if (str.length() > max) answer = str;

        return answer;
    }

    public static void main(String[] args){

        Main main = new Main();

        Scanner scanner = new Scanner(System.in);
        String str = scanner.nextLine();

        System.out.println(main.solution(str));
    }
}
```

<br>

```
// 출력결과
Java C JavaScript Python
JavaScript
```

<br>
<br>
<hr>
<hr>
<br>
<br>

### <span style="color:#7FB5FF">**🔑 String[] .split()**</span>
<hr>

- 문자열을 구분자를 기준으로 나누어 배열에 저장해 리턴하는 함수

- 구분자 사이에 `|`를 사용하여 여러개의 구분자 사용 가능

- split()[n] : split 후 n번째 값만 리턴

<br>

### <span style="color:#7FB5FF">**🔑 String .indexOf()**</span>
<hr>

- 특정 문자나 문자열이 앞에서부터 처음 발견되는 인덱스를 리턴하는 함수

- 찾지 못할 경우 -1 반환

- .indexOf(찾을문자, 시작위치) / 시작 위치는 생략 가능, 생략할 경우 0번째(처음)부터 찾음

<br>

### <span style="color:#7FB5FF">**🔑 String .substring()**</span>
<hr>

- 문자열을 자를 때 사용하는 함수

- .substring(start) : 문자열의 start 위치부터 끝까지의 모든 문자열 리턴

- .substring(start, end) : 문자열의 start 위치부터 end 위치 전까지의 문자열을 잘라 리턴