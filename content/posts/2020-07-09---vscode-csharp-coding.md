---
title: "코드 성능 개선"
date: "2020-07-06T21:12:00+09"
template: "post"
draft: true
slug: "/posts/enhancing-code-performance/"
category: "Tech"
tags:
  - "Tech"
  - "code performance"
description: "."
---

VSCode를 인스톨

dotnet sdk를 인스톨

터미널에서 작업
- mkdir testproject && cd testproject
- dotnet new console

프로젝트에 nuget 패키지 추가

하지만 dotnet 커맨드는 nuget 패키지 검색 기능을 아직 지원하지 않음. [dotnet-search](https://github.com/billpratt/dotnet-search)을 인스톨하여 CLI에서 nuget package를 검색할 수 있다.

Json.Net 인스톨하기
- dotnet tool install --global dotnet-search
- dotnet-search json
- dotnet add package Newtonsoft.Json
