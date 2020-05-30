---
title: Whisper, TTS utility
date: "2019-07-08T22:26:12-07"
template: "post"
draft: false
slug: "/posts/whisper-tts-utility/"
category: "Tech"
tags:
  - "Tech"
  - "text-to-speech utility"
description: "텍스트를 음성으로 읽어주는 윈도우 유틸리티 Whisper입니다."
---

macOS에는 OS의 기본 기능으로 텍스트를 음성으로 읽어주는 기능이 있는데(참고: http://osxdaily.com/2012/09/15/speak-selected-text-with-a-keystroke-in-mac-os-x/), 이 기능을 유용하게 써먹다가 '왜 윈도우에는 이런 기능이 없지?'하고 10년 전에 (...) 후다닥 만들었던 윈도우 유틸리티입니다. 소스 코드를 어디다가 저장해놨는지 잊어버리고 실행 파일만 예전 블로그에 남아있었는데, 조그만 코드라도 공개해 놓으면 누가 또 재사용을 하겠지 하는 마음에 decompile하고 정리해서 git repo도 공개합니다.

<iframe width="560" height="315" src="https://www.youtube.com/embed/q6P4hJxHcII" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

텍스트를 드래그해 선택한 상태에서 `` Ctrl + ` ``를 누르면 선택된 텍스트를 읽기 시작하고, `` Ctrl + Shift + ` ``를 누르면 텍스트에서 wav 파일을 생성해 바탕 화면에 저장합니다.

링크
  - https://github.com/kenial/Whisper
  - [실행파일 다운로드 링크](https://github.com/kenial/Whisper/raw/master/download/Whisper.exe)

