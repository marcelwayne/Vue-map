<template lang="md">

# 标签

`MapOverlayLabel`

## 属性

|属性名|类型|默认值|描述|
|------|:---:|:---:|----|
|content|String||文本标注的内容|
|title|String||当鼠标移至标注上时显示此字段|
|labelStyle|Object||文本标注的样式|
|offset|Size||文本标注的位置偏移值|
|position|Point||文本标注的地理位置|
|zIndex|Number||文本标注的z轴位置|
|massClear|Boolean|true|是否在调用map.clearOverlays清除此覆盖物|

## 事件

|事件名|参数|描述|
|------|:--:|----|
|click|event{type, target, point, pixel}|点击折线后会触发此事件|
|dblclick|event{type, target, point, pixel}|双击折线后会触发此事件|
|mousedown|event{type, target, point, pixel}|鼠标在折线上按下触发此事件|
|mouseup|event{type, target, point, pixel}|鼠标在折线释放触发此事件|
|mouseout|event{type, target, point, pixel}|鼠标离开折线时触发此事件|
|mouseover|event{type, target, point, pixel}|当鼠标进入折线区域时会触发此事件|
|remove|event{type, target}|移除折线时触发|
|lineupdate|event{type, target}|覆盖物的属性发生变化时触发|


## 示例

### 在地图中添加一个红色24号字的文本标签

#### 代码

```html
<template>
  <baidu-map>
    <map-view class="map" :center="{lng: 116.404, lat: 39.915}" :zoom="15">
      <map-overlay-label content="This is a label" :position="{lng: 116.404, lat: 39.915}" :labelStyle="{color: 'red', fontSize : '24px'}" title="Hover me"/>
  </map-view>
  </baidu-map>
</template>
```

#### 预览
<baidu-map>
  <map-view class="map" :center="{lng: 116.404, lat: 39.915}" :zoom="15">
    <map-overlay-label content="This is a label" :position="{lng: 116.404, lat: 39.915}" :labelStyle="labelStyle" title="Hover me"/>
  </map-view>
</baidu-map>
</template>

<script>
export default {
  data () {
    return {
      labelStyle: {color: 'red', fontSize : '24px'}
    }
  }
}
</script>