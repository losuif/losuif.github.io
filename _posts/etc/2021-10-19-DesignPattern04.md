---
title: "[디자인패턴] 프록시 패턴 (Proxy Pattern)"
author: Jinsol
categories: DesignPattern
tags: Spring Java DesignPattern
date: '2021-10-19'
# image: /assets/img/.png
---

<br>

- Proxy는 대리인이라는 뜻으로, 뭔가를 대신해서 처리하는 것

- Proxy Class를 통해 대신 전달하는 형태로 설계

- 실제 Client는 Proxy로 부터 결과를 받음

- 스프링 AOP > 내가 원하는 메소드나 기능들, 흩어져있는 기능들을 동일하게 제공하는 역할을 프록시 패턴으로 사용 (AOP는 프록시 패턴을 활용 해 특정한 메소드 등에 앞뒤로 내가 원하는 기능을 넣을 수 있고, 흩어져있는 여러가지 공통된 기능을 하나로 묶어줄 수 있음)

- ex)

    - (interface) IBrowser.java

        ```java
        public interface IBrowser {
            Html show();
        }
        ```

    - Html.java

        ```java
        public class Html {
            
            private String url;

            public Html(String url){
                this.url = url;
            }
        }
        ```

    - (implements IBrowser) Browser.java

        ```java
        public class Browser implements IBrowser{

            private String url;

            public Browser(String url){
                this.url = url;
            }

            @Override
            public Html show() {
                System.out.println("browser loading html from : " + url);
                return new Html(url);
            }
        }
        ```

    - (Main Class) Main.java

        ```java
        public class Main {

            public static void main(String[] args){

                Browser browser = new Browser("https://github.com");
                browser.show();
                browser.show();
                browser.show();

            }
        }
        ```

    - 출력결과

        ```
        browser loading html from https://github.com
        browser loading html from https://github.com
        browser loading html from https://github.com
        ```

        <br>

        위 예제와 같이 cache를 구현하지 않고 같은 url에 여러 번 요청을 할 경우 요청할 때마다 같은 html을 로딩해야 한다.
        <br>
        (cache : 데이터를 디스크가 아닌 메모리에 보관 > 반복될 경우 메모리에서 불러와 사용하기 때문에 캐시 적용 시 성능 및 처리속도가 월등히 빠름)

        <br>

    - (Proxy)(implements IBrowser) BrowserProxy.java

        ```java
        public class BrowserProxy implements IBrowser{

            private String url;
            private Html html;

            public BrowserProxy(String url) {
                this.url = url;
            }

            @Override
            public Html show() {

                if (html == null){
                    this.html = new Html(url);
                    System.out.println("browser loading html from : " + url);
                }
                System.out.println("browser use cache html : " + url);
                return html;
            }
        }
        ```

    - (Main Class) Main.java

        ```java
        public class Main {

            public static void main(String[] args){

                // 구현체 자체는 건들지 않고 캐싱하는 기능을 넣음
                IBrowser iBrowser = new BrowserProxy("https://github.com");
                iBrowser.show();
                iBrowser.show();
                iBrowser.show();
            }
        }
        ```

    - 출력결과

        ```
        browser loading html from https://github.com
        browser use cache html https://github.com
        browser use cache html https://github.com
        browser use cache html https://github.com
        ```

        <br>

        프록시 패턴 적용 시 로딩은 1번만 되고 그 이후에는 cache에 저장된 html을 사용하게 된다.

