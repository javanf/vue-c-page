# vue-c-page

> vue 分页组件

![vue 分页组件](http://cdn.javanx.cn/wp-content/themes/lensnews2.2/images/post/20181212113145.gif)

## 快速开始

### 安装
``` bash
npm install vue-c-page -S

```

### 引入
```javascipt
import CPage from 'vue-h5-page'
Vue.use(CPage)
```

### 调用
```html
<cPage :pageOption="pageOption" :jumpTo="jumpTo"></cPage>
```

```javascript
pageOption: {
  pageNo: 1, // 当前页码
  pageSize: 10, // 每页多少条
  total: 152, // 总共多少条
  totalPage: 16 // 总共多少页
}

jumpTo(pageNo){
  this.pageOption.pageNo = parseInt(pageNo);
  console.log('当前是第' + pageNo + '页');
  // do something
}
```


github地址： [vue-c-page](https://github.com/javanf/vue-c-page) npm地址： [vue-c-page](https://www.npmjs.com/package/vue-c-page)

## 联系我

请移驾[web秀](http://www.javanx.cn)