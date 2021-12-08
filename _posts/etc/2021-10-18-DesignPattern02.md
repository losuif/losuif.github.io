---
title: "[디자인패텬] 싱글톤 패턴 (Singleton Pattern)"
author: Jinsol
categories: Spring
tags: Spring
date: '2021-10-18'
# image: /assets/img/.png
---

<br>

- 객체의 인스턴스가 유일하게 1개만 생성되어야 하는 경우에 사용되는 패턴

- 생성자가 여러 차례 호출되더라도 실제 생성되는 객체는 하나이고, 최초 생성 이후에 호출된 생성자는 최초에 생성한 객체를 반환

- 싱글톤으로 만들어진 클래스의 인스턴스는 전역 인스턴스 > 다른 클래스의 인스턴스들이 데이터를 공유하기 쉬움

- 공통된 객체를 여러개 생성해서 사용해야 하는 상황에서 많이 사용

- Spring에서 Bean은 기본적으로 싱글톤으로 관리됨

<br>

![](/assets/img/singleton.PNG)

-   - Singleton은 자기 자신을 객체로 가지고 있어야 함

    - private static으로 인스턴스 변수 생성

    - private 생성자로 외부에서 생성 막기

    - static => getInstance 메소드 제공

- ex)

    - SocketClient.java

        ```java
        public class SocketClient {

            // 싱글톤은 자기 자신을 객체로 가지고 있어야 함
            private static SocketClient socketClient = null;

            // 기본 생성자로 생성할 수 없도록 private으로 막아줘야함
            private SocketClient(){

            }

            // static 메소드를 통해 getInstance 메소드 제공해야함
            // static 메소드 > 변수도 static
            public static SocketClient getInstance(){

                // 객체가 null인지 여부 체크
                // null인 경우 객체 새로 생성
                if (socketClient == null){
                    socketClient = new SocketClient();
                }
                return socketClient;
            }

            public void connect(){
                System.out.println("connect");
            }
        }
        ```

    - AClazz.java

        ```java
        public class AClazz {

            private SocketClient socketClient;

            public AClazz(){
                this.socketClient = SocketClient.getInstance();
                // private > new 해서 생성 못함
            }

            public SocketClient getSocketClient(){
                return this.socketClient;
            }
        }
        ```

    - BClazz.java

        ```java
        public class BClazz {

            private SocketClient socketClient;

            public BClazz(){
                this.socketClient = SocketClient.getInstance();
            }

            public SocketClient getSocketClient(){
                return this.socketClient;
            }

        }
        ```

    - Main.java

        ```java
        public class Main {

            public static void main(String[] args) {

                AClazz aClazz = new AClazz();
                BClazz bClazz = new BClazz();

                // 두 개의 객체가 동일한지 확인
                System.out.println(aClazz.getSocketClient().equals(bClazz.getSocketClient()));

            }
        }

        // 출력결과
        // true
        ```