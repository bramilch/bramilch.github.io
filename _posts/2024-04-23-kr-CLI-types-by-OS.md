---
layout: post
title: "Linux, Windows, macOS 운영체제별 CLI 종류와 차이"
author: bramilch
date: 2024-04-23 18:00:00 +0900
categories: [Backend, Data Engineering]
tags: [Backend, Data Engineering]
pin: true
math: true
toc: true
comments: false
mermaid:
  false
  # alt: Responsive rendering of Chirpy theme on multiple devices.
image:
  path: ./assets/img/posts/2024-04-23-kr-CLI-types-by-OS/os-cli-comparison.png
---

<br>

> 2024/04/23: 초안 작성

※ 내용에 오류가 있을 수 있습니다.

<br>

**목차**

- [CLI, Shell, Terminal emulator 용어 차이](#cli-shell-terminal-emulator-용어-차이)
- [Linux, Windows, MacOS 운영체제별 CLI 종류와 차이](#linux-windows-macos-운영체제별-cli-종류와-차이)
- [참고자료](#참고자료)

<br>

## CLI, Shell, Terminal emulator 용어 차이

- CLI는 어디에 구현되어 있든지 텍스트 기반 인터페이스를 모두 지칭할 수 있는 용어이고, 셸 Shell은 어떤 인터페이스 내의 특정한 명령 해석기, 터미널 에뮬레이터는 CLI 및 셸 Shell과 상호 작용하기 위한 ~~GUI가 아니라~~ 그래픽 인터페이스를 제공하는 소프트웨어 애플리케이션

  - Computing에서의 Shell은 운영 체제 의 서비스를 인간 사용자나 다른 프로그램에 노출하는 컴퓨터 프로그램
  - Unix Shell은 Unix 계열 운영 체제에 CLI를 제공하는 명령줄 해석기
  - Unix Shell은 대화형 명령 언어이자 스크립팅 언어. 운영 체제에서 셸 스크립트를 사용하여 시스템 실행을 제어하는 ​​데 사용
  - Shell script는 명령줄 해석기 command-line interpreter인 Unix 셸 에 의해 실행되도록 설계된 컴퓨터 프로그램. 파일 조작, 프로그램 실행, 인쇄 등을 함. 환경을 설정하고, 프로그램을 실행하고, 필요한 정리, 로깅을 수행하는 스크립트를 Wrapper라고 함.

- CLI(Command-Line Interface)란 CLI는 컴퓨터의 운영 체제 또는 소프트웨어 애플리케이션과 상호 작용하기 위한 텍스트 기반 인터페이스

  > CLI는 모든 텍스트 기반 인터페이스를 나타낼 수 있는 일반적인 용어

- Shell은 명령 해석기 또는 명령 프로세서를 제공하는 특정 유형의 CLI를 모두 지칭함.

  - 사용자가 입력한 명령을 해석하고 운영 체제의 커널과 상호 작용하여 실행
  - 셸에는 스크립팅 기능, 변수, 제어 구조(예: 루프 및 조건), 환경 설정과 같은 기능이 포함되는 경우가 많음.
  - Shell의 예로 Bash(Bourne Again Shell), Zsh(Z Shell), PowerShell 및 명령 프롬프트 Command Prompt

- 터미널 에뮬레이터 Terminal emulator란 GUI 내에서 물리적 컴퓨터 터미널의 기능을 복제하는 소프트웨어 응용 프로그램을 지칭
  - 명령 입력 및 출력 보기 등 사용자가 CLI와 상호 작용할 수 있는 창 또는 인터페이스를 제공
  - 터미널 에뮬레이터를 사용하면 사용자는 전용 물리적 터미널 없이도 운영 체제의 명령줄 인터페이스에 액세스할 수 있음.
  - 여러 탭이나 창, 사용자 정의 가능한 색 구성표, 다양한 터미널 프로토콜(예: SSH) 지원과 같은 추가 기능 제공

<br>

## Linux, Windows, MacOS 운영체제별 CLI 종류와 차이

<br>

**Windows 11 22H2(2022년 9월 20일부터) 윈도우의 모든 콘솔은 Windows Terminal이 dafault가 됨.**

<br>

![CLI Comparision](/assets/img/posts/2024-04-23-kr-CLI-types-by-OS/os-cli-comparison.png)

<br>

| 터미널 에뮬레이터 | Linux                                                                                                                 | Windows                                                                                                                 | macOS                                                                                         |
| :---------------- | :-------------------------------------------------------------------------------------------------------------------- | :---------------------------------------------------------------------------------------------------------------------- | :-------------------------------------------------------------------------------------------- |
| Shell 셸 ~~쉘~~   | Bash, Zsh, Dash, etc.                                                                                                 | 명령 프롬프트 Command Prompt (cmd.exe), PowerShell, Windows Terminal                                                    | 터미널 Terminal (bash, zsh, etc.)                                                             |
| 주 용도           | 운영 체제와 상호 작용, 명령 및 스크립트 실행 (공통)                                                                   |
| 기본 셸           | 일반적으로 Bash이지만 사용자 정의 가능                                                                                | 명령 프롬프트 Command Prompt (cmd.exe), PowerShell                                                                      | 일반적으로 Bash 또는 Zsh이지만 사용자 정의 가능                                               |
| 스크립팅 기능     | 조건부, 루프, 함수 등과 같은 기능으로 강력한 스크립팅 기능을 지원                                                     | 객체 지향 프로그래밍, 파이프라이닝 및 고급 스크립팅 기능과 같은 기능을 갖춘 강력한 스크립팅 언어                        | Linux와 유사한 강력한 스크립팅 기능 지원                                                      |
| 특징              | 탭 완성, 기록 탐색, 작업 제어(백그라운드/포그라운드 프로세스), 별칭, 사용자 정의 옵션                                 | 파일 관리, 디렉터리 탐색 및 시스템 구성을 위한 기본 명령, 고급 스크립팅을 위한 PowerShell 지원, 제한된 사용자 정의 옵션 | 탭 완성, 기록 탐색, 작업 제어(백그라운드/포그라운드 프로세스), 별칭, 사용자 정의 옵션         |
| 파일 경로 구문    | 파일 경로에 슬래시(/) 사용                                                                                            | 파일 경로에 백슬래시(\)를 사용                                                                                          | 파일 경로에 슬래시(/) 사용                                                                    |
| 사용환경          | 다양한 기본 설정에 따라 다양한 셸을 사용할 수 있는 오픈 소스 및 고도로 사용자 정의 가능                               | Linux에 비해 폐쇄적인 소스, 사용자 정의 제한적, 여러 셸을 지원                                                          | Linux에 비해 폐쇄적인 소스, 사용자 정의 제한적이지만 다양한 Unix 기반 유틸리티 및 도구를 지원 |
| 호환성            | Linux 기반 시스템 및 소프트웨어와 잘 작동                                                                             | Windows 기반 시스템 및 소프트웨어와 잘 작동                                                                             | macOS 기반 시스템 및 소프트웨어와 잘 작동                                                     |
| 특징              | 탭 인터페이스, 사용자 정의 가능한 색 구성표 및 테마, 여러 셸 지원(명령 프롬프트, PowerShell, WSL 등), GPU 가속 렌더링 | 탭 인터페이스, 사용자 정의 가능한 색 구성표 및 테마, 여러 셸 지원(명령 프롬프트, PowerShell, WSL 등), GPU 가속 렌더링   | 탭 인터페이스, 사용자 정의 가능한 색상 구성표 및 테마, 다중 셸 지원(bash, zsh 등)             |

<br>
<br>

## 참고자료

[Wikipedia] Shell (computing)
<https://en.wikipedia.org/wiki/Shell_(computing)>

[Wikipedia] Unix shell
<https://en.wikipedia.org/wiki/Unix_shell>

[Wikipedia] Shell script
<https://en.wikipedia.org/wiki/Shell_script>

[Wikipedia] Bash (Unix*shell)
<https://en.wikipedia.org/wiki/Bash*(Unix_shell)>

[Wikipedia] Z shell zsh
<https://en.wikipedia.org/wiki/Z_shell>

[Wikipedia] Terminal (macOS)
<https://en.wikipedia.org/wiki/Terminal_(macOS)>

[Wikipedia] Command Prompt cmd
<https://en.wikipedia.org/wiki/Cmd.exe>

[Wikipedia] Powershell
<https://en.wikipedia.org/wiki/PowerShell>

[Wikipedia] Windows Terminal
<https://en.wikipedia.org/wiki/Windows_Terminal>

[Devblogs Microsoft] Windows Terminal is now the Default in Windows 11
<https://devblogs.microsoft.com/commandline/windows-terminal-is-now-the-default-in-windows-11/>
