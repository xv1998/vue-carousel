# 轮播图组件

组件名字为carousel，实现了基本的自动播放，左右选择和底部点选择的功能。
（路径为src/components/common/carousel）

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```

## 参数说明
| 参数     | 类型   | 说明                                                 |
| -------- | ------ | ---------------------------------------------------- |
| options  | Object | 基本配置（默认width=600，height=400，interval=4000） |
| btnStyle | String | 点击按钮设置（默认normal）                           |
| slides   | Array  | 图片列表                                             |



#### options说明

| 参数     | 类型   | 说明          |
| -------- | ------ | :------------ |
| width    | number | 容器宽度      |
| height   | number | 容器高度      |
| interval | number | 轮播速度(/ms) |



#### btnStyle说明

| 参数   | 说明                 |
| ------ | -------------------- |
| normal | 会出现两旁和底部按钮 |
| dot    | 只出现底部按钮       |
| side   | 只出现两旁按钮       |



#### slides说明

```
slides:[{
		id:0,
		src: require('@/assets/1.png'),
		title:'background'
	},{
		id:1,
		src: require('@/assets/2.png'),
		title:'logo'
	}]
```

