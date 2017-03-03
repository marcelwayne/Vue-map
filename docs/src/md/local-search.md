<template lang="md">

# 本地检索

## 属性

|属性名|类型 |默认值|描述|
|------|:---:|:----:|----|
|location|String, Bounds, None|undefined|location表示检索区域，其类型可为空、坐标点或城市名称的字符串。当参数为空时，检索位置由当前地图中心点确定，且搜索结果的标注将自动加载到地图上，并支持调整地图视野层级；当参数为坐标时，检索位置由该点所在位置确定；当参数为城市名称时，检索会在该城市内进行。|
|keyword|String, Array|搜索关键字。当keyword为数组时将同时执行多关键字的查询，最多支持10个关键字。|
|forceLocal|Boolean|表示是否将搜索范围约束在当前城市|
|customData|CustomData|表示检索lbs云服务的数据|
|pageCapacity|Number|设置每页容量，取值范围：1 - 100，对于多关键字检索，每页容量表示每个关键字返回结果的数量（例如当用2个关键字检索时，实际结果数量范围为：2 - 200）。此值只对下一次检索有效|
|autoViewport|Boolean|检索结束后是否自动调整地图视野。|
|selectFirstResult|Boolean|是否选择第一个检索结果。|

## 事件

|事件名|参数|描述|
|------|:--:|----|
|markersset|{pois: Array}|标注添加完成后的回调函数。|
|infohtmlset|{poi: LocalResultPoi}|标注气泡内容创建后的回调函数。|
|resultshtmlset|{container: HTMLElement}|结果列表添加完成后的回调函数。|
|searchcomplete|{results: [LocalResult]}|检索完成后的回调函数。如果是多关键字检索，回调函数参数返回一个LocalResult的数组，数组中的结果顺序和检索中多关键字数组中顺序一致|

## 示例
<input v-model="keyword">
<input v-model="location">
<doc-preview>
  <baidu-map slot="map">
    <map-view class="map">
      <map-local-search :keyword="keyword" :auto-viewport="true" :location="location"></map-local-search>
    </map-view>
  </baidu-map>
</doc-preview>
</template>

<script>
export default {
  data () {
    return {
      location: '北京',
      keyword: '百度'
    }
  }
}
</script>