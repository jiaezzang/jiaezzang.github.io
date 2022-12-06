---
layout: single
title: "[React Native] 2. React Native 개발 환경 설정"
folder: "react-native"
categories:
  - Rn
tags: [React Native]

author_profile: true
sidebar:
  nav: "docs"

toc: true
toc_label: "목록"
toc_icon: "bars"
toc_sticky: true

date: 2022-12-06
---

# React Native의 환경설정

> 리액트 네이티브 개발 환경 설정 방법은 두 가지로 나눌 수 있는데 하나는 **Create React Native App**이라는 도구를 사용하느 것이고, 또 다른 하나는 **리액트 네이티브와 그 디펜던시(dependency)까지 모두 설치하는 전형적인 방법**이 있다.

<br />

## Create React Native App

- Create React Native App은 빠르고 쉽게 설정 가능하며, 손쉽게 테스트 및 프로토타이핑 할 수 있게 해준다.
- Xcode나 안드로이드 스튜디오를 설치할 필요 없이 리액트 네이티브 앱을 생성하고 실행할 수 있게 해주는 커맨드 라인 도구이다.
- `npm install -g create-react-native-app` 명령어를 사용해 패키지를 설치할 수 있다.

```
npm install -g create-react-native-app
```

### 앱 생성하기

![img](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbWQsvC%2FbtrSZ4vf0j1%2FIGYlEGdTxKRCkkx1W40Id1%2Fimg.png)

- `create-react-native-app [프로젝트명]` 명령어를 사용해 새로운 프로젝트를 생성할 수 있는데 이는 애플리케이션 프로젝트를 생성하고 보일러 플레이트 코드와 함께 자바스크립트 디펜던시를 설치한다.

```
create-react-native-app [프로젝트명]
```

 <br />

### iOS와 Android에서 앱 실행하기

![npm-start](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdDLMKn%2FbtrSW6gC4nR%2FqSdDbgZvbTNkDSAZe9oCsK%2Fimg.png)

- `npm start` 명령어 실행 시 위와 같이 QR코드가 나타난다. 우선 Expo Go 어플을 설치한 후 진행해야 하는데, 아이폰의 경우 카메라앱으로 해당 QR을 스캔 할 경우 Expo GO 어플로 연결 되지 않아 아래 방법을 사용했다.

```
npm start
```

<br />

![expo-start](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FvYT5K%2FbtrS1KJt90C%2FTvwfwpVUBtYSkK5CuAfUz1%2Fimg.png)

- `npm install -g expo-cli` 패키지 설치 후 `expo start` 명령어를 통해 앱을 실행한다. 이 경우 아이폰 카메라로 QR코드를 스캔했을 때 Expo Go 어플로 바로 연결이 된다.

```
npm install -g expo-cli
expo start
```

<br />

![phone-screen](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FePXyTG%2FbtrS0EXkQpm%2FTeXJZGEAoPNSpWPJyh7tuk%2Fimg.png)

- App.js의 코드를 수정할 경우 위 스크린샷과 같이 수정 내역이 바로 반영되어 보여지는 것을 확인할 수 있다.

  <br />

## 전형적인 방법

- `react-native init` 명령어를 이용하여 프로젝트를 생성하는 방법이다.
- 버전에 따라 설치 방법에 차이가 있으나 공통적으로 다음 항목들이 준비되어야 한다.
  - node.js
  - React Native
  - iOS 개발 환경(Xcode)
  - Android 개발 환경(JDK, 안드로이드 JDK, 안드로이드 스튜디오)

### iOS에서 앱 실행하기

- 리액트 네이티브 커맨드 라인 도구를 이용하여 앱을 제작할 수 있는데, 이 도구를 설치하기 위해 다음 명령어를 실행한다

```
npm install -g create-native-cli
```

<br />
-설치 후 iOS와 Android 보일러 플레이트가 포함된 새로운 리액트 네이티브 프로젝트를 생성하기 위해 다음 명령어를 사용한다.
```
react-native init [프로젝트명]
```

<br />

### iOS에서 앱 실행하기

- iOS에서 생성한 앱을 실행하기 위해서는 먼저 생성한 프로젝트의 디렉터리로 이동한 후 `react-native run-ios`명령어를 실행한다.

```
react-native run-ios
```

- `open ios/[프로젝트명].xcodeproj` 명령어를 사용해 iOS 시뮬레이터를 켜고 앱을 실행하는 방법도 사용 가능하다.

```
open ios/[프로젝트명].xcodeproj
```

<br />

### Android에서 앱 실행하기

- 마찬가지로 `react-native run-android` 명령어를 통해 리액트 네이티브 앱을 안드로이드에서 실행할 수 있다.

```
react-native run-android
```

- 안드로이드 상에서 앱을 실행하기 위해서는 안드로이드 스튜디오와 안드로이드 SDK를 포함한 안드로이드 개발에 필요한 모든 설정이 완료되어 있어야 한다. [🔗](https://facebook.github.io/react-native/docs/getting-started.html)

<br/>  
<br/>

---

![빠른 모바일 앱 개발을 위한 리액트 네이티브(React Native)](https://shopping-phinf.pstatic.net/main_3243613/32436133726.20220527062949.jpg?type=w300)

바니 아이젠먼, 「빠른 모바일 앱 개발을 위한 React Native」, 이종은 옮김, 인사이트, 2016
