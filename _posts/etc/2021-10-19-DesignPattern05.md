---
title: "[디자인패턴] 데코레이터 패턴 (Decorator Pattern)"
author: Jinsol
categories: DesignPattern
tags: Spring Java DesignPattern
date: '2021-10-19'
# image: /assets/img/.png
---

<br>

- 기존 뼈대(클래스)는 유지하되, 이후 필요한 형태로 꾸밀 때 사용

- 확장이 필요한 경우 상속의 대안으로도 활용함

- ex)

    - (interface) ICar.java

        ```java
        public interface ICar {
            int getPrice();
            void showPrice();
        }
        ```

    - (implements ICar) Audi.java

        ```java
        public class Audi implements ICar{

            private int price;

            public Audi(int price){
                this.price = price;
            }

            @Override
            public int getPrice() {
                return price;
            }

            @Override
            public void showPrice() {
                System.out.println("audi의 가격은 " + this.price + "원 입니다.");
            }
        }
        ```

    - (Decorator)(implements ICar)AudiDecorator.java

        ```java
        public class AudiDecorator implements ICar{

            protected ICar audi;
            protected String modelName;
            protected int modelPrice;

            public AudiDecorator(ICar audi, String modelName, int modelPrice){
                this.audi = audi;
                this.modelName = modelName;
                this.modelPrice = modelPrice;
            }

            // 기본 가격에 모델이 올라갈수록 가격 추가
            @Override
            public int getPrice() {
                return audi.getPrice() + modelPrice;
            }

            @Override
            public void showPrice() {
                System.out.println(modelName + "의 가격은 " + getPrice() + "원 입니다.");
            }
        }
        ```

    - (extends AudiDecorator) A3.java

        ```java
        public class A3 extends AudiDecorator{

            public A3(ICar audi, String modelName) {
                super(audi, modelName, 1000);
            }
        }
        ```

    - (extends AudiDecorator) A4.java

        ```java
        public class A4 extends AudiDecorator{

            public A4(ICar audi, String modelName) {

                super(audi, modelName, 2000);
            }
        }
        ```

    - (extends AudiDecorator) A5.java

        ```java
        public class A5 extends AudiDecorator{

            public A5(ICar audi, String modelName) {

                super(audi, modelName, 3000);
            }
        }
        ```

    - (Main Class) Main.java

        ```java
        public class Main {

            public static void main(String[] args){

                ICar audi = new Audi(1000);
                audi.showPrice();

                // a3
                ICar audi3 = new A3(audi, "A3");
                audi3.showPrice();

                // a4
                ICar audi4 = new A4(audi, "A4");
                audi4.showPrice();

                // a5
                ICar audi5 = new A5(audi, "A5");
                audi5.showPrice();
            }
        }
        ```

    - 출력결과

        ```java
        audi의 가격은 1000원 입니다.
        A3의 가격은 2000원 입니다.
        A4의 가격은 3000원 입니다.
        A5의 가격은 4000원 입니다.
        ```