---
title: "[디자인패턴] 옵저버 패턴 (Observer Pattern)"
author: Jinsol
categories: DesignPattern
tags: Spring Java DesignPattern
date: '2021-10-19'
# image: /assets/img/.png
---

<br>

- 한 객체의 상태 변화에 따라 다른 객체의 상태도 연동되도록 일대다 객체 의존 관계를 구성

- 데이터의 변경이 발생했을 경우 상대 클래스나 객체에 의존하지 않으면서 데이터 변경을 통보하고자 할 때 사용
(ex) 새로운 파일이 추가되거나 기존 파일이 삭제되었을 때 다른 탐색기에 즉시 변경 통보해야 함)

- ex)

    - (interface) IButtonListener.java

        ```java
        public interface IButtonListener {
            void clickEvent(String event);
        }
        ```

    - Button.java

        ```java
        public class Button {

            private String name;
            private IButtonListener buttonListener;

            public Button(String name) {
                this.name = name;
            }

            // 클릭시 버튼 리스너에게 이벤트 넘겨줌
            public void click(String message){
                buttonListener.clickEvent(message);
            }

            public void addListener(IButtonListener buttonListener){
                this.buttonListener = buttonListener;
            }
        }
        ```

    - (main class) Main.java

        ```java
        public class Main{

            public static void main(String[] args) {

                // 버튼 생성
                Button button = new Button("버튼");

                // 버튼에 리스너 등록 
                // 익명클래스
                button.addListener(new IButtonListener() {
                    
                    @Override
                    public void clickEvent(String event) {
                        System.out.println(event);
                    }
                    
                });

                // 버튼 클릭 시 위 event에 메시지 전달 > 출력
                button.click("메시지 전달: click1");
                button.click("메시지 전달: click2");
                button.click("메시지 전달: click3");
                button.click("메시지 전달: click4");

            }
        }
        ```

    - 출력결과

        ```
        메시지 전달: click1
        메시지 전달: click2
        메시지 전달: click3
        메시지 전달: click4
        ```