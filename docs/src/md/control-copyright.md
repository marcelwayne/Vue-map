# 版权控件
`MapControlCopyright`

## 属性

|属性名|类型|默认值|描述|
|------|:---:|:---:|----|
|anchor|ControlAnchor|undefined|控件停靠位置|
|offset|Size|undefined|控件偏移值|
|copyright|Array|undefined|版权信息列表|

## 示例

### 在地图右上角加入版权信息控件

#### 代码

```html
<template>
  <baidu-map>
    <map-control-copyright
      anchor="BMAP_ANCHOR_TOP_RIGHT"
      :copyright="[{id: 1, content: 'Copyright Message', bounds: {ne: {lng: 110, lat: 40}, sw:{lng: 0, lat: 0}}}, {id: 2, content: '<a>我是版权信息</a>'}]"/>
  </baidu-map>
</template>
```

#### 预览
<baidu-map>
  <map-view class="map">
    <map-control-copyright
      anchor="BMAP_ANCHOR_TOP_RIGHT"
      :copyright="[{id: 1, content: 'Copyright Message', bounds: {ne: {lng: 110, lat: 40}, sw:{lng: 0, lat: 0}}}, {id: 2, content: '<a>我是版权信息</a>'}]"/>
  <map-view/>
</baidu-map>