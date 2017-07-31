# Looped carousel for React Native
[![NPM version](http://img.shields.io/npm/v/react-native-looped-carousel.svg?style=flat)](https://www.npmjs.com/package/react-native-looped-carousel)
[![Build Status](https://travis-ci.org/appintheair/react-native-looped-carousel.svg)](https://travis-ci.org/appintheair/react-native-looped-carousel)
[![Dependency Status](https://david-dm.org/appintheair/react-native-looped-carousel.svg)](https://david-dm.org/appintheair/react-native-looped-carousel)
[![devDependency Status](https://david-dm.org/appintheair/react-native-looped-carousel/dev-status.svg)](https://david-dm.org/appintheair/react-native-looped-carousel#info=devDependencies)

Full-fledged "infinite" carousel for your next [react-native](https://github.com/facebook/react-native/) project. Supports iOS and Android.

Based on [react-native framework](https://github.com/facebook/react-native/) by Facebook.

## Demo
![](http://spronin.github.io/img/react.gif)

## 安装

```sh
npm install react-native-looped-carousel --save
```

## 属性

Name | propType | default value | description
--- | --- | --- | ---
autoplay | boolean | true | 是否自动轮播
delay | number | 4000 | 多少毫秒切换一次
currentPage | number | 0 | 设置初始页
pageStyle | style | null | 页面的样式
contentContainerStyle | style | null | `contentContainerStyle` for the scrollView
onAnimateNextPage | func | null | 切换轮播图时的回调方法
swipe | bool | true | 是否允许手势滑动也换页面
**分页** | --- | --- | ---
pageInfo | boolean | false | 是否在底部显示`当前页面下标 / 页面个数` 
pageInfoBackgroundColor | string | 'rgba(0, 0, 0, 0.25)' | 分页的背景色
pageInfoBottomContainerStyle | style | null | pageInfo容器的样式
pageInfoTextStyle | style | null | pageInfo中的文本样式
pageInfoTextSeparator | string | ' / ' | 在 `当前页面下标` 和 `页面个数`之间的分隔符
**小圆点** | --- | --- | ---
bullets | bool | false | 是否在轮播的底部显示小圆点
bulletStyle | style | null | bullet（小圆点）的样式
bulletsContainerStyle | style | null | style for the bullets container
chosenBulletStyle | stlye | null | bullet的容器的样式
**导航箭头** | --- | --- | ---
arrows | bool | false | 是否显示轮播的导航箭头
arrowsStyle | style | null | 导航箭头的样式
arrowsContainerStyle | style | null | 导航箭头的容器样式
leftArrowText | string / element | 'Left' | 左箭头的文字或图片
rightArrowText | string / element | 'Right' | label / icon for right navigation arrow

## 使用
```js
import React, { Component } from 'react';
import {
  Text,
  View,
  Dimensions,
} from 'react-native';
import Carousel from 'react-native-looped-carousel';

const { width, height } = Dimensions.get('window');

export default class CarouselExample extends Component {

  constructor(props) {
    super(props);

    this.state = {
      size: { width, height },
    };
  }

  _onLayoutDidChange = (e) => {
    const layout = e.nativeEvent.layout;
    this.setState({ size: { width: layout.width, height: layout.height } });
  }

  render() {
    return (
      <View style={{ flex: 1 }} onLayout={this._onLayoutDidChange}>
        <Carousel
          delay={2000}
          style={this.state.size}
          autoplay
          pageInfo
          onAnimateNextPage={(p) => console.log(p)}
        >
          <View style={[{ backgroundColor: '#BADA55' }, this.state.size]}><Text>1</Text></View>
          <View style={[{ backgroundColor: 'red' }, this.state.size]}><Text>2</Text></View>
          <View style={[{ backgroundColor: 'blue' }, this.state.size]}><Text>3</Text></View>
        </Carousel>
      </View>
    );
  }
}
```

[Full example code](Examples/Simple)

## Used in
 - [React Native Buyscreen](https://github.com/appintheair/react-native-buyscreen)

## See also
 - [React Native Grid Component](https://github.com/phil-r/react-native-grid-component)

----

More on react-native here: http://facebook.github.io/react-native/docs/getting-started.html#content
