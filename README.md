# jquery-tag
简单易用的jquery tag plugin.

源代码来twitter的 [typeahead.js](http://twitter.github.com/bootstrap/javascript.html#typeahead) 和 [bootstrap-tag.js](https://github.com/fdeschenes/bootstrap-tag)，做了部分改动，添加一些示例。

## 特点

1. 基于jquery，简单易用，可自定义css样式
2. 支持模糊匹配，支持静态数据和Ajax动态查询数据

## 使用

1、确保系统中引入了jquery

2、引入css：
```html
<link rel="stylesheet" href="assets/css/default.css"/>
```

3、引入如下js：
```javascript
<script src="assets/js/typeahead.js"></script>
<script src="assets/js/jquery-tag.js"></script>
```

4、使用：

(1) 添加`input`：
```html
 <input type="text" name="tags" id="tag1" placeholder="请输入标签..."/>
```
(2) 静态数据
```javascript
var $tag1 = $('#tag1');
$tag1.tag({
    placeholder: $tag1.attr('placeholder'),
    source: ["北京", "上海", "深圳", "广州", "杭州", "成都", "other"]
});
```

(3) Ajax数据
```javascript
var $tag3 = $('#tag3');
$tag3.tag({
    placeholder: $tag1.attr('placeholder'),
    source: function (v, f) {
        console.log(v);
        console.log(f);
        let data = [];
        // query data from URL
        $.ajax({
            url: 'demo.json',
            data: {},
            type: 'get',
            async: false,
            success: function (d) {
                data = d;
            }
        });
        return data;
    }
});
```

(4) 获取输入的`tag`：
```javascript
$(this).next().text('Tag values: ' + $tag1.val());
```

## Demo

更多示例参见`demo.html`，示例如下：
![示例图片](demo.png)
