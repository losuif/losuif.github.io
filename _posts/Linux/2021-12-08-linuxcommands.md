---
title: "리눅스 명령어"
author: Jinsol
categories: Linux
tags: Linux
date: "2021-12-08"
# image: /assets/img/
---

<br>

- **pwd**

    - print working directory

    - 현재 작업중인 디렉토리 정보

    - window > `cd ,`

- **cd** 

    - change directory

    - 경로 이동

    -   - cd .. : 한 단계 위 디렉토리로 이동

        - cd : 해당 디렉토리로 바로 이동

        - cd- : 이전 디렉토리로 이동

    - C드라이브에서 D드라이브로 이동 : `D:`

- **ls**

    - list segments

    - 디렉토리 목록 조회

    - window > `dir`

    - 윈도우에서 ls 사용하기

        - `doskey 바꿀명령어 = 기존명령어`

        - doskey ls = dir

        - 다시 dir로 바꾸기 : doskey dir = dir

    - ls -l : 자세히 보기

    - ls -a : 숨긴파일까지 보기
    
- **cp**

    - copy

    - 파일 복사

- **cp -r**

    - 폴더 복사

- **mv**

    - move

    - 파일, 디렉토리 이동

- **mkdir**

    - make directory

    - 디렉토리 생성

    - mkdir -p 디렉토리명1/디렉토리명2/... : 부모디렉토리가 없을 경우 만들고 자식디렉토리 생성

- **rm**

    - remove

    -   - rm : 파일 삭제

        - rm -r : 디렉토리 삭제

- **touch**

    - 파일, 디렉토리 생성

    - 이미 존재하는 파일이나 디렉토리라면 업데이트 일자를 현재 시간으로 변경

- **open .**

    - 해당 폴더의 파일 탐색기 열기

    - window > `start .`

- **clear**

    - 터미널의 모든 내용을 지움