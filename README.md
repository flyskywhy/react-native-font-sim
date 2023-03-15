# react-native-font-sim
[![npm version](http://img.shields.io/npm/v/react-native-font-sim.svg?style=flat-square)](https://npmjs.org/package/react-native-font-sim "View this project on npm")
[![npm downloads](http://img.shields.io/npm/dm/react-native-font-sim.svg?style=flat-square)](https://npmjs.org/package/react-native-font-sim "View this project on npm")
[![npm licence](http://img.shields.io/npm/l/react-native-font-sim.svg?style=flat-square)](https://npmjs.org/package/react-native-font-sim "View this project on npm")
[![Platform](https://img.shields.io/badge/platform-ios%20%7C%20android-989898.svg?style=flat-square)](https://npmjs.org/package/react-native-font-sim "View this project on npm")

Font `SimSun(宋体)`, `SimHei(黑体)` and `KaiTi(楷体)`, can work with `<Text/>` or `<GCanvasView/>` or [react-native-font-picker](https://github.com/flyskywhy/react-native-font-picker).

## Installation
    npm install react-native-font-sim
    npx react-native-asset -a ./node_modules/react-native-font-sim/fonts

optional:

    cd android/app/src/main/assets/fonts/
    rm SimSun.ttf SimHei.ttf KaiTi.ttf
    ln -s ../../../../../../node_modules/react-native-font-sim/fonts/* ./
    cd -

If use `ln -s` above optional, run `react-native-asset` next time will got error, then need manually `cp` them before run `react-native-asset`.

PS: The same steps can also install ttf files in e.g. [react-native-vector-icons](https://github.com/oblador/react-native-vector-icons).

## Usage
### `<Text/>`
```
<Text style={{fontFamily: SimSun}}>I'm 宋体.</Text>
<Text style={{fontFamily: SimHei}}>I'm 黑体.</Text>
<Text style={{fontFamily: KaiTi}}>I'm 楷体.</Text>

```

### `<GCanvasView/>`
```
import {GCanvasView, registerFont} from '@flyskywhy/react-native-gcanvas';
if (Platform.OS !== 'web') {
  var RNFS = require('react-native-fs');
}
...
if (Platform.OS === 'android') {
  const destFontsPath = `${RNFS.ExternalDirectoryPath}/fonts`;
  if (!(await RNFS.exists(destFontsPath))) {
    await RNFS.mkdir(destFontsPath);
  }
  const dest = `${destFontsPath}/KaiTi.ttf`;
  await RNFS.copyFileAssets('fonts/KaiTi.ttf', dest);
  registerFont(dest);
}

const ctx = this.canvas.getContext('2d');
ctx.font = '50px KaiTi';
ctx.fillText('原生画布NativeCanvas', 20, 100);
...
<GCanvasView
 onCanvasCreate={canvas => this.canvas = canvas}
 style={styles.gcanvas}
/>
```

### as custom fonts of [react-native-font-picker](https://github.com/flyskywhy/react-native-font-picker)
Thus can let e.g. `KaiTi` be choosed just like `times new roman` as [Font Picker to fillText](https://github.com/flyskywhy/GCanvasRNExamples/blob/master/app/components/FontPicker2FillText.js) on [@flyskywhy/react-native-gcanvas](https://github.com/flyskywhy/react-native-gcanvas) by [react-native-font-picker](https://github.com/flyskywhy/react-native-font-picker).

<img src="https://raw.githubusercontent.com/flyskywhy/GCanvasRNExamples/master/assets/FontPicker2FillText.gif" width="480">

## Donate
To support my work, please consider donate.

- ETH: 0xd02fa2738dcbba988904b5a9ef123f7a957dbb3e

- <img src="https://raw.githubusercontent.com/flyskywhy/flyskywhy/main/assets/alipay_weixin.png" width="500">
