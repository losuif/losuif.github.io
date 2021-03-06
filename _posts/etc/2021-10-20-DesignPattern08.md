---
title: "[디자인패턴] 전략 패턴 (Strategy Pattern)"
author: Jinsol
categories: DesignPattern
tags: Spring Java DesignPattern
date: '2021-10-20'
# image: /assets/img/.png
---

<br>

- 객체지향의 꽃 🌼

- 같은 기능이지만 서로 다른 전략을 가진 클래스들을 각각 캡슐화하여 상호교환할 수 있도록 하는 패턴

- 객체의 행위를 바꾸고 싶은 경우 직접 변경하는 것이 아닌 전략만 변경 하여 유연하게 확장

- ex)

    - (interface) EncodingStrategy.java

        ```java
        public interface EncodingStrategy {
            String encode(String text);
        }
        ```

    - (implements EncodingStrategy) NormalStrategy.java

        ```java
        public class NormalStrategy implements EncodingStrategy{
            @Override
            public String encode(String text) {
                return text;
            }
        }
        ```

    - (implements EncodingStrategy) Base64Strategy.java

        ```java
        import java.util.Base64;

        public class Base64Strategy implements EncodingStrategy{

            @Override
            public String encode(String text) {
                return Base64.getEncoder().encodeToString(text.getBytes());
            }
        }
        ```

        - Base64 : Binary Data를 Text로 바꾸는 인코딩의 하나로, Binary Data를 ASCII 영역의 문자로만 이루어진 문자열로 바꿈

    - Encoder.java

        ```java
        public class Encoder {

            private EncodingStrategy encodingStrategy;

            public String getMessage(String message){
                return this.encodingStrategy.encode(message);
            }

            public void setEncodingStrategy(EncodingStrategy encodingStrategy) {
                this.encodingStrategy = encodingStrategy;
            }
        }
        ```

    - (implements EncodingStrategy) AppendStrategy.java

        ```java
        public class AppendStrategy implements EncodingStrategy{

            @Override
            public String encode(String text) {
                return text + " world";
            }
        }
        ```

    - Main.java

        ```java
       public class Main {

            public static void main(String[] args){

                Encoder encoder = new Encoder();

                // base64
                EncodingStrategy base64 = new Base64Strategy();

                // normal
                EncodingStrategy normal = new NormalStrategy();

                String message = "hello";

                encoder.setEncodingStrategy(base64);
                String base64Res = encoder.getMessage(message);
                System.out.println(base64Res);

                encoder.setEncodingStrategy(normal);
                String normalRes = encoder.getMessage(message);
                System.out.println(normalRes);

                encoder.setEncodingStrategy(new AppendStrategy());
                String appendRes = encoder.getMessage(message);
                System.out.println(appendRes);
            }
        }
        ```

    - 출력결과

        ```
        aGVsbG8=
        hello
        hello world
        ```
        
        원본 객체는 그대로 두고 전략만 수정해 다른 결과를 얻어냄

        - 전략 메서드를 가진 전략 객체 : NormalStrategy, Base64Strategy

        - 전략 객체를 사용하는 컨텍스트 : Encoder

        - 전략 객체를 생성해 컨텍스트에 주입하는 클라이언트 : Main method