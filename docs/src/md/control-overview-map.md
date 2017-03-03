# 缩略图控件

`MapControlOverviewMap`

## 属性

|属性名|类型|默认值|描述|
|------|:---:|:---:|----|
|anchor|ControlAnchor|undefined|控件停靠位置|
|offset|Size|undefined|控件偏移值|
|size|Size|undefined|缩略地图控件的大小|
|isOpen|Boolean|false|缩略地图添加到地图后的开合状态|

## 事件
|事件名|参数|描述|
|------|:---:|----|
|viewchanged|event{type, target, isOpen}|缩略地图开合状态发生变化后触发此事件|
|viewchanging|event{type, target}|缩略地图开合状态发生变化过程中触发此事件|

## 示例

### 在地图右下角加入缩略图控件

#### 代码

```html
<template>
  <baidu-map class="map">
    <map-control-overview-map anchor="BMAP_ANCHOR_BOTTOM_RIGHT"/>
  </baidu-map>
</template>
```

#### 预览
<doc-preview>
  <baidu-map slot="map" class="map">
    <map-control-overview-map anchor="BMAP_ANCHOR_BOTTOM_RIGHT"/>
  </baidu-map>
</doc-preview>