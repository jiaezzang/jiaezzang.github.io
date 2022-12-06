---
layout: single
title: "[React Native] 모바일 컴포넌트"
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

# HTML 엘리먼트와의 유사성

React Native에서는 HTML 엘리먼트가 아닌 이와 유사한 컴포넌트를 사용환다.

| React        | React Native           |
| ------------ | ---------------------- |
| \<div>       | \<View>                |
| \<span>      | \<Text>                |
| \<li>, \<ul> | \<FlatList>, 자식 요소 |
| \<img>       | \<Image>               |

<br />

## \<Text> 컴포넌트

- 리액트 네이티브에서는 `<text>` 컴포넌트만이 플레인 텍스트 노드를 자식으로 가질 수 있다.
- `<text>` 컴포넌트는 하위 태그를 사용할 수 업쇼으나 **fontWeight**나 **fontStyle** 등의 속성을 이용할 수 있다.

```
<Text>
  Hello, I'm <Text style={{fontWeight: "bold"}}>JIAEZZANG</Text>
  <Text style{{fontStyle: "italic"}}>https://jiaezzang.github.io</Text>
</Text>
```

- 하지만 위와 같이 작성할 경우 코드가 지저분해지기 때문에 아래와 같이 스타일 컴포넌트를 만들어 사용하는 것이 좋다.

```
const styles = StyleSheet.create({
  bold: {
    fontWeight: "bold"
  },
  italic: {
    fontStyle: "italic"
  }
});

class Strong extends Component {
  render(){
    return (
      <Text style={styles.bold}>
        {this.props.children}
      </Text>);
  }
}

class Em extends Component {
  render(){
    return (
      <Text style={styles.italic}>
        {this.props.children}
      </Text>);
  }
}
```

```
<Text>
  Hello, I'm <Strong>JIAEZZANG</Strong>
  <Em}>https://jiaezzang.github.io</Em>
</Text>
```

- 같은 스타일을 반복적으로 적용해야 할 경우 스타일이 적용된 컴포넌트의 재사용을 더 권장하는데 이는 제작 시 시간이 많이 들기는 하지만 코드 분리가 명확히 되어 컴포넌트가 사용되는 곳이 어디든지 똑같은 결과물을 만들어 낸다.

<br />

## \<Image> 컴포넌트

- `<Image>` 컴포넌트는 source 속성을 지정해야 하며 이미지 경로는 자바스크립트 모듈을 불러올 때와 같다.
- 만약 **jiaezzang.png**라는 이미지를 불러오고자 할 때, **jiaezzang.ios.png**와 **jiaezzang.android.png**와 같이 플랫폼에 따라 파일을 따로 준비해 두면 각 플랫폼에 해당하는 이미지가 사용된다.
- 웹에 있는 이미지 소스를 사용할 경우에는 **style 속성**을 사용해 이미지 사이즈를 따로 지정해야 한다.
- 리액트 네이티브에서는 화면에 보여줄 이미지를 스타일로 지정하지 않고 컴포넌트로서 지정해야 한다.
  <br /><br />

# 터치와 제스처 다루기

## \<button>을 이용한 기본 인터렉션

- 가장 기본적인 방법으로 버튼을 만드는 방식이지만 시각적 피드백이 없어 잘 사용하지 않는다

<br />

## \<tochableHighlight> 컴포넌트

- `<tochableHighlight>` 컴포넌트는 뷰가 터치될 때 오버레이를 추가해 사용자에게 시각적 피드백을 준다.
- 사용자가 눌렀을 때 간단한 오버레이가 추가되길 원하는 컴포넌트를 `<tochableHighlight>`로 감싸서 사용한다.
- **onPressIn**, **onPressOut**, **onLongPress**와 같은 콜백을 지정하여 이벤트를 다룰 수 있다.
- 사용자에게 특정 엘리먼트가 탭이 가능하다는 것을 알려주는 기본적인 피드백을 주고 싶을 때 사용할 수 있다.

<br />

## PanResponder 클래스

- **PanResponder**는 컴포넌트가 아닌 리액트 네이티브에서 제공하는 클래스이다.
- **PanResponder gesture State** 객체를 통해 현재 제스처의 속도, 누적 이동거리 등과 같은 원시 위치 데이터에 접근할 수 있다.
- 자체적인 터치 인터페이스를 구현하고 싶을 때 사용한다.

<br /><br />

# 리스트 관련 컴포넌트

> 리액트 네이티브에서는 두 가지 리스트 컴포넌트가 있는데 하나는 데이터 구조가 비슷한 경우 사용할 수 있는 `<FlatList>` 컴포넌트이고, 또 다른 하나는 데이터를 섹션으로 구분해서 보여주어야 하는 경우 유용하게 사용할 수 있는 `<SectionList>` 컴포넌트이다. 또 리스트 내부적으로 기능을 넣거나 독특하게 리스트를 다뤄야하는 경우 `<VirtualizedList>`를 사용할 수 있다.

## \<FlatList> 컴포넌트

- 사용법

  - **props로 data와 renderItem을 지정**해야 한다.
  - **data**는 해당 컴포넌트에서 렌더링할 배열 타입의 데이터를 의미하는데 각 엘리먼트는 고유의 key값을 가지고 있어야 한다.
  - **renderItem** 함수는 data 배열에 속한 하나의 엘리먼트 데이터를 바탕으로 해당하는 컴포넌트를 리턴하도록 구현한다.

  ```
  <FlatList data={this.state.data} renderItem={this._renderItem} />
  ```

- 장점

  - 데이터 목록을 짜임새 있게 보여주어야 할 때 손쉽게 적용할 수 있다
  - 스크롤과 터치 인터렉션을 다루는 것이 가능하다
  - 렌더링 스피드와 메모리 사용량을 줄이기 위해 성능 최적화 기술이 많이 적용되어 있다.
    <br />

## \<SectionList> 컴포넌트

- 사용법

  - **sections, renderItem과 renderSectionHeader를 지정**한다.
  - **sections**는 섹션 데이터를 가지고 있는 객체의 배열이며 각 섹션 객체는 title과 data 속성을 가진다.
  - **data**는 해당 컴포넌트에서 렌더링할 배열 타입의 데이터를 의미하는데 각 엘리먼트는 고유의 key값을 가지고 있어야 한다.

- 장점

  - 대부분 비슷한 형태의 아이템을 가지고 있는 목록을 섹션 헤더와 함께 표시하기 위해 만들어진 컴포넌트로, 데이터를 섹션으로 구분하여 보여줄 때 유용하다.

<br /><br />

# 네비게이션

- 네비게이션이란 일반적으로 한 화면에서 다른 화면으로 이동시키는 코드를 말한다.
- 이를 구현하기 위해서 리액트 네이티브는 기본적으로 `<Navigator>`, `<NavigationIOS>`를 제공하며, react-navigation 라이브러리에서 제공하는 `<StackNavigator>`도 이들과 함꼐 많이 사용된다.

<br /><br />

# 짜임새를 위한 컴포넌트

- 짜임새를 위한 컴포넌트는 앞서 설명한 것 이외에도 다양한데 컴포넌트 이름에 특정 플랫폼을 의미하는 접미사가 붙는 것이 많다.
- 플랫폼 특유의 UI 엘리먼트를 렌더링하기 위해 네이티브 API를 사용하고 있기 때문인데 이러한 컴포넌트들은 앱을 여러 화면으로 구성할 때 유용하다.
  <br/>  
  <br/>

---

![빠른 모바일 앱 개발을 위한 리액트 네이티브(React Native)](https://shopping-phinf.pstatic.net/main_3243613/32436133726.20220527062949.jpg?type=w300)

바니 아이젠먼, 「빠른 모바일 앱 개발을 위한 React Native」, 이종은 옮김, 인사이트, 2016
