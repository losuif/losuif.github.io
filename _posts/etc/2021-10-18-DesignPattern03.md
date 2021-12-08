---
title: "[디자인패턴] 어댑터 패턴 (Adapter Pattern)"
author: Jinsol
categories: DesignPattern
tags: Spring Java DesignPattern
date: '2021-10-18'
# image: /assets/img/.png
---

<br>

- 서로 다른 인터페이스를 가진 두 클래스를 어댑터 클래스로 인터페이스를 통일 시켜 사용하는 방법 (호환성이 없는 인터페이스 때문에 함께 동작할 수 없는 클래스들이 함께 작동하도록 해줌)

- ex)

    - (interface) Electronic110V.java

        ```java
        public interface Electronic110V {
            void powerOn();
        }
        ```

    - (interface) Electronic220V.java

        ```java
        public interface Electronic220V {
            void connect();
        }
        ```

    - (implements Electronic110V) HairDryer.java

        ```java
        public class HairDryer implements Electronic110V{

            @Override
            public void powerOn() {
                System.out.println("110v 헤어 드라이기 ON");
            }
        }
        ```

    - (implements Electronic220V) AirConditioner.java

        ```java
        public class AirConditioner implements Electronic220V{

            @Override
            public void connect() {
                System.out.println("220v 에어컨 ON");
            }
        }
        ```

    - (adapter class) SocketAdapter.java

        ```java
        public class SocketAdapter implements Electronic110V{

            private Electronic220V electronic220V;

            public SocketAdapter(Electronic220V electronic220V){
                this.electronic220V = electronic220V;
            }

            @Override
            public void powerOn() {
                electronic220V.connect();
            }
        }
        ```

    - (main class) Main.java

        ```java
        public class Main {

            public static void connect(Electronic110V electronic110V){
                electronic110V.powerOn();
            }

            public static void main(String[] args){

                HairDryer hairDryer = new HairDryer();
                connect(hairDryer);

                AirConditioner airConditioner =  new AirConditioner();
                Electronic110V adapter = new SocketAdapter(airConditioner);
                connect(adapter);
            }
        }
        ```

    - 출력결과

        ```
        110v 헤어 드라이기 ON
        220v 에어컨 ON
        ```