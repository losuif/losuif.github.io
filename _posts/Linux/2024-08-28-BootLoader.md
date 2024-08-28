---
title: "[Linux] 부트로더(Bootloader)"
author: Jinsol
categories: Linux 리눅스
tags: Linux 리눅스
date: '2024-08-28'
# image: /assets/img/.png
---

<br>

# <span style="color:#387F39">🐧 부트로더(BootLloader)</span>
<hr>

- = 부트스트랩 로더(Bootstrap Loader) = 부트 매니저(Boot Manager)

- 컴퓨터를 처음 시작했을 때 가장 먼저 실행되어 부팅을 도와주는 역할을 하는 소프트웨어 프로그램

- 운영체제가 시동되기 이전에 커널이 올바르게 시동되기 위해 필요한 모든 관련 작업을 마무리하고 최종적으로 운영체제를 시동시키기 위한 프로그램 (시스템에 여러 운영체제가 설치되어 있으면 선택하여 부팅할 수 있도록 함)

- 운영체제 실행에 필요한 환경을 설정하고 운영체제 이미지를 메모리에 복사

- <span style="color:#387F39">하드디스크의 첫 번째 섹터인 MBR(Master Boot Record)에 위치</span>하며, MBR은 부트 매니저 프로그램과 파티션 정보를 저장

- 주 파티션마다 부트 섹터(boot sector, 디스크의 다른 부분에 저장되는 부팅 프로그램을 담을 수 있는 기억 장치의 섹터)가 할당됨

- 리눅스 운영체제에 한정되어 사용되는 <span style="color:#387F39">LILO(LInux LOader)</span>와 리눅스 운영체제 외 다른 운영체제에서도 사용 가능한 <span style="color:#387F39">GRUB(GRand Unified Bootloader)</span>

<br>
<br>

# <span style="color:#387F39">🐧 GRUB(GRand Unified Bootloader)</span>
<hr>

- 리눅스 부팅 시 처음 나오는 선택 화면

- LILO에 비해 사용 및 설정 편리

- 부트 정보를 사용자가 임의로 변경해 부팅할 수 있기 때문에 부트 정보가 올바르지 않더라도 부팅 시 바로 수정하여 부팅할 수 있음

- 다른 운영체제와 멀티부팅 가능

- 대화형 설정 → 커널의 경로와 파일 이름만 알면 부팅 가능

- ROM-BIOS에서 사용하는 정보를 사용하며, IDE, SCSI 장치명을 별도로 구분 짓지 않고 시스템에 정착된 순서대로 hd0, hd1로 표기

- <span style="color:#387F39">디스크와 파티션 번호는 모두 0부터 시작</span>하며, (디스크장치명,파티션명) 형식으로 표기