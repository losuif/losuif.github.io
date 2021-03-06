---
title: "[디자인패턴] 파사드 패턴 (Facade Pattern)"
author: Jinsol
categories: DesignPattern
tags: Spring Java DesignPattern
date: '2021-10-20'
# image: /assets/img/.png
---

<br>

- Facade는 '건물의 정면'을 의미하는 단어로 어떤 소프트웨어의 다른 커다란 코드 부분에 대하여 간략화된 인터페이스를 제공해주는 디자인 패턴 / 여러 개의 객체와 실제 사용하는 서브 객체의 사이에 복잡한 의존 관계가 있을 때, 중간에 facade라는 객체를 두고, 여기서 제공하는 interface만을 활용한여 기능을 사용하는 방식

- 여러 개의 객체를 합쳐서 특정한 기능을 만들 때 사용

- 파사드 객체는 복잡한 소프트웨어 바깥쪽의 코드가 라이브러리의 안쪽 코드에 의존하는 일을 감소시켜 주고, 복잡한 소프트웨어를 사용 할 수 있게 간단한 인터페이스를 제공해줌

- ex)

    - Ftp.java

        ```java
        public class Ftp {

            private String host;
            private int port;
            private String path;

            public Ftp(String host, int port, String path) {
                this.host = host;
                this.port = port;
                this.path = path;
            }

            // 원격체에 연결
            public void connect(){
                System.out.println("FTP Host : " + host + " Port : " + port + "로 연결합니다.");
            }

            // 해당 디렉토리로 이동
            public void moveDirectory(){
                System.out.println("path : " + path + "로 이동합니다.");
            }

            // 연결 종료
            public void disConnect(){
                System.out.println("FTP 연결을 종료합니다.");
            }
        }
        ```

    - Reader.java

        ```java
        public class Reader {

            private String fileName;

            // 파일 받기
            public Reader(String fileName) {
                this.fileName = fileName;
            }

            // 파일 연결
            public void fileConnect(){
                String msg = String.format("Reader %s로 연결 합니다.", fileName);
                System.out.println(msg);
            }

            // 파일 읽어오기
            public void fileRead(){
                String msg = String.format("Reader %s의 내용을 읽어옵니다.", fileName);
                System.out.println(msg);
            }

            // 파일 연결 종료
            public void fileDisconnect(){
                String msg = String.format("Reader %s로 연결 종료 합니다.", fileName);
                System.out.println(msg);
            }
        }
        ```

    - Writer.java

        ```java
        public class Writer {

            private String fileName;

            // 파일 이름 받기
            public Writer(String fileName) {
                this.fileName = fileName;
            }

            // 파일 생성 or 이어쓰기
            public void fileConnect(){
                String msg = String.format("Writer %s로 연결 합니다.", fileName);
                System.out.println(msg);
            }

            // 파일 쓰기
            public void write(){
                String msg = String.format("Writer %s로 파일쓰기 합니다.", fileName);
                System.out.println(msg);
            }

            // 파일 다 쓰면 종료
            public void fileDisconnect(){
                String msg = String.format("Writer %s로 연결 종료 합니다.", fileName);
                System.out.println(msg);
            }
        }
        ```

     - Main.java

        ```java
        public class Main {
            public static void main(String[] args){

                Ftp ftp = new Ftp("https://losuif.github.io/", 22, "/home/etc");
                ftp.connect();
                ftp.moveDirectory();

                Writer writer = new Writer("text.tmp");
                writer.fileConnect();
                writer.write();

                Reader reader = new Reader("text.tmp");
                reader.fileConnect();
                reader.fileRead();

                reader.fileDisconnect();
                writer.fileDisconnect();
                ftp.disConnect();
            }
        }
        ```

    - 출력결과

        ```
        FTP Host : https://losuif.github.io/ Port : 22로 연결합니다.
        path : /home/etc로 이동합니다.
        Writer text.tmp로 연결 합니다.
        Writer text.tmp로 파일쓰기 합니다.
        Reader text.tmp로 연결 합니다.
        Reader text.tmp의 내용을 읽어옵니다.
        Reader text.tmp로 연결 종료 합니다.
        Writer text.tmp로 연결 종료 합니다.
        FTP 연결을 종료합니다.
        ```

    <br>

    => Facade Pattern 사용하기

    <br>

    - SftpClient.java

        ```java
        public class SftpClient {

            private Ftp ftp;
            private Reader reader;
            private Writer writer;

            public SftpClient(Ftp ftp, Reader reader, Writer writer) {
                this.ftp = ftp;
                this.reader = reader;
                this.writer = writer;
            }

            public SftpClient(String host, int port, String path, String fileName) {
                this.ftp = new Ftp(host, port, path);
                this.reader = new Reader(fileName);
                this.writer = new Writer(fileName);
            }

            public void connect(){
                ftp.connect();
                ftp.moveDirectory();
                writer.fileConnect();
                reader.fileConnect();
            }

            public void disconnect(){
                writer.fileDisconnect();
                reader.fileDisconnect();
                ftp.disConnect();
            }

            public void read(){
                reader.fileRead();
            }

            public void write(){
                writer.write();
            }
        }
        ```

    - Main.java

        ```java
        public class Main {
            public static void main(String[] args){

                SftpClient sftpClient = new SftpClient("https://losuif.github.io/", 22, "/home/etc", "text.tmp");
                sftpClient.connect();
                sftpClient.write();
                sftpClient.read();
                sftpClient.disconnect();
            }
        }
        ```

    - 출력결과

        ```
        FTP Host : https://losuif.github.io/ Port : 22로 연결합니다.
        path : /home/etc로 이동합니다.
        Writer text.tmp로 연결 합니다.
        Reader text.tmp로 연결 합니다.
        Writer text.tmp로 파일쓰기 합니다.
        Reader text.tmp의 내용을 읽어옵니다.
        Writer text.tmp로 연결 종료 합니다.
        Reader text.tmp로 연결 종료 합니다.
        FTP 연결을 종료합니다.
        ```

        파사드 패턴을 사용한 클래스의 사용으로 안쪽 코드에 의존하는 일을 감소시켜주며, 코드를 간결하게 만들어준다. 