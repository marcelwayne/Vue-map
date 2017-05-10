<template lang="md">

# 多边形

`BmPolygon`

## 属性

|属性名|类型|默认值|描述|
|------|:---:|:---:|----|
|path|Array[Point]|[]|构成折线的点|
|strokeColor|String|undefined|折线颜色|
|strokeWeight|Number|undefined|折线的宽度，以像素为单位|
|strokeOpacity|Number|undefined|折线的透明度，取值范围0 - 1|
|strokeStyle|String|'solid'|折线的样式，solid或dashed|
|fillColor|String|undefined|填充颜色。当参数为空时，折线覆盖物将没有填充效果|
|fillOpacity|Number|undefined|填充的透明度，取值范围0 - 1|
|enableMassClear|Boolean|true|是否在调用map.clearOverlays清除此覆盖物|
|enableEditing|Boolean|false|是否启用线编辑|
|enableClicking|Boolean|true|是否响应点击事件|

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

### 在地图中添加可编辑的多边形

#### 代码

```html
<template>
  <baidu-map class="map" :center="{lng: 116.404, lat: 39.915}" :zoom="15">
    <bm-polygon :path="polygonPath" stroke-color="blue" :stroke-opacity="0.5" :stroke-weight="2" :editing="true" @lineupdate="updatePolygonPath"/>
  </baidu-map>
</template>

<script>
export default {
  data () {
    return {
      polygonPath: [
        {lng: 116.412732, lat: 39.911707},
        {lng: 116.39455, lat: 39.910932},
        {lng: 116.403461, lat: 39.921336}
      ]
    }
  },
  methods: {
    updatePolygonPath (e) {
      this.polygonPath = e.target.getPath()
    },
    addPolygonPoint () {
      this.polygonPath.push({lng: 116.404, lat: 39.915})
    }
  }
}
</script>
```

#### 预览

<doc-preview>
  <baidu-map class="map" :center="{lng: 116.404, lat: 39.915}" :zoom="15">
    <bm-polygon :path="polygonPath" stroke-color="blue" :stroke-opacity="0.5" :fill-opacity="0.5" :editing="true" @lineupdate="updatePolygonPath"></bm-polygon>
  </baidu-map>
  <div class="toolbar">
    <table>
      <thead>
        <tr>
          <th></th>
          <th>经度</th>
          <th>纬度</th>
        <tr>
      </thead>
      <tbody>
        <tr v-for="(point, index) in polygonPath" class="list-line">
          <td v-text="`坐标${index + 1}`"></td>
          <td><text-field label="经度" pattern="-?[0-9]*(\.[0-9]+)?" v-model.number="point.lng"></text-field></td>
          <td><text-field label="纬度" pattern="-?[0-9]*(\.[0-9]+)?"v-model.number="point.lat"></text-field></td>
        </tr>
      </tbody>
    </table>
    <button class="mdl-button mdl-js-button mdl-button--raised mdl-js-ripple-effect" @click="addPolygonPoint">
      添加一个坐标
    </button>
  </div>
</doc-preview>
</template>

<script>
export default {
  data () {
    return {
      polygonPath: [
        {lng: 116.412732, lat: 39.911707},
        {lng: 116.39455, lat: 39.910932},
        {lng: 116.403461, lat: 39.921336}
      ]
    }
  },
  methods: {
    updatePolygonPath (e) {
      this.polygonPath = e.target.getPath()
    },
    addPolygonPoint () {
      this.polygonPath.push({lng: 116.404, lat: 39.915})
      this.$nextTick(global.componentHandler.upgradeDom)
    }
  }
}
</script>