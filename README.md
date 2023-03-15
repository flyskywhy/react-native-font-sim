# react-native-font-sim
React Native font SimSun &lt;宋体> SimHei &lt;黑体> KaiTi&lt;楷体> , support iOS and Android both.

## Installation

    npm install react-native-font-sim
    react-native link react-native-font-sim
    cd android/app/src/main/assets/fonts/
    rm SimSun.ttf SimHei.ttf KaiTi.ttf
    ln -s ../../../../../../node_modules/react-native-font-sim/fonts/* ./
    cd -

## Usage

```javascript
<Text style={{fontFamily: SimSun}}>I'm 宋体.</Text>
<Text style={{fontFamily: SimHei}}>I'm 黑体.</Text>
<Text style={{fontFamily: KaiTi}}>I'm 楷体.</Text>

```
