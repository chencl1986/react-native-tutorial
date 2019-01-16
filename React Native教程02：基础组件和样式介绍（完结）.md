
 > 本教程适合已有React开发经验的朋友阅读哦~

可以通过npm run android或npm run ios启动并在模拟器查看效果。

## React Native基础组件

> 示例代码：/lesson01/App.js

 1. View：View在React Native中的作用类似于Web中的div标签，是最基础的组件。
 2. Text：Text在React Native中用来显示文本，其作用类似于Web中的span标签，但它并不是inline元素。
值得注意的是，在React Native中所有的文本都必须放在Text中，而不能单独显示。
 3. Image：Image类似于Web端的img标签，可在source属性中设置引用图片的路径。在React Native中，Image组件不支持onPress（点击）事件。

```
<View>
  <Image
    source={require('/react-native/img/favicon.png')}
  />
  <Image
    source={{ uri: 'https://facebook.github.io/react-native/docs/assets/favicon.png' }}
  />
  <Image
    source={{ uri: 'data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADMAAAAzCAYAAAA6oTAqAAAAEXRFWHRTb2Z0d2FyZQBwbmdjcnVzaEB1SfMAAABQSURBVGje7dSxCQBACARB+2/ab8BEeQNhFi6WSYzYLYudDQYGBgYGBgYGBgYGBgYGBgZmcvDqYGBgmhivGQYGBgYGBgYGBgYGBgYGBgbmQw+P/eMrC5UTVAAAAABJRU5ErkJggg==' }}
  />
</View>
```

 4. ScrollView：在React Native中，内容如果超出一定高度，是不会像Web端一样自动触发滚动条，而是需要将要滚动的内容放在ScrollView组件中，内容高度超出ScrollView时就会触发滚动。需要注意的是，ScrollView必须通过style设定一个高度。
若是需要渲染长列表，如一个商品列表，则可以使用FlatList组件，因为ScrollView会将列表组件一次性渲染出，这样容易造成过多内存占用，而FlatList则只会渲染将要出现在屏幕中的元素。
虽然FlatList在使用上更加复杂，但为了提升性能，我们应该优先使用ScrollView。
 5. Button：在React Native中，Button调用的是原生的按钮，它的缺点是只支持少量的定制。
如color，在Android中，它修改的是背景色，在iOS中，它修改的是字体颜色。
在开发中，若需要用到Button，在GitHub上搜索是一个好选择：[https://github.com/search?utf8=%E2%9C%93&q=react+native+button&ref=simplesearch](https://github.com/search?utf8=%E2%9C%93&q=react%20native%20button&ref=simplesearch)

## React Native样式介绍

> 示例代码：/lesson01/App.js

 1. React Native中的样式写法与CSS类似，支持直接用style属性写在组件上，而且因为是运行在原生环境中，所以仅支持部分CSS样式。
 2. React Native也支持类似于类名的写法，但React Native不支持.css文件，因此样式需要写在const styles = StyleSheet.create({})中，其属性名就作为类名使用。使用时也写在组件的style属性中，\<View style={styles.container}>\</View>。
 3. 布局方式：标签没有inline类型，全部都相当于block类型。支持flex布局和position（enum('absolute', 'relative')），但不支持浮动。布局方式：标签没有inline类型，全部都相当于block类型。支持flex布局和position（enum('absolute', 'relative')），但不支持浮动。
 4. 支持的单位：数字（与设备像素密度无关的逻辑像素点，相当于PX）和百分比。
为了适配各尺寸屏幕，可以通过设定基础屏幕宽度，如750，与当前屏幕宽度换算出当前实际需要的尺寸。

```
// 引入Dimensions，用于获取设备的尺寸
import { Dimensions } from 'react-native';

// 设置基础宽度为750
const BASE_WIDTH=750;

export function calc(size){
  // 获取当前窗口宽度，支持参数为window和screen
  let { width } = Dimensions.get('window');

  // 换算出当前需要显示的尺寸
  return size * width / BASE_WIDTH;
}
```
