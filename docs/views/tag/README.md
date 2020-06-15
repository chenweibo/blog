---
title: 标签速查
date: 2020-04-14
---

## 数据库相关

### 数据迁移(强制恢复)

```bash
   php artisan rest:db  //强制重新生成表结构,填充数据
```


## PSR规范

```bash
   composer run-script phpcs  //自动修复php文件为行业规范
```





## blade模版语法


### 站点信息

``` php
//防止报没键值错误
{{ check('title',$site) }}
```

### 栏目

``` php
<ul>
@foreach($globalMenu as $v)
     //栏目url                              标题
    <li href="{{$v['blade_url']}}"> {{$v['title']}} </li>
    // $globalMenu 树形结构 如有子集
    @if(count($v['children']))
        <ul class="mchildren">
            @foreach($v['children'] as $vo)
             <a href="{{$vo['blade_url']}}">{{$vo['title']}}</a>
            @endforeach
        </ul>
    @endif
    ...
    @endforeach
</ul>
```

### 列表页

| **变量**| **类型**  | **一句话描述** |
| ---- | ---- |---- |
| $menu | model|栏目信息
| $content['data'] | model| 列表页关联的内容
| $content['hasChildren'] | bool| 是否还有子类


#### example1

>获取列表页内容

``` php
@foreach($content['data'] as $v)
    <dd class="col-lg-3 col-xs-6">
        <div class="boxP">
                  //url
            <a href="{{$vo['blade_url']}}">
                 //缩略图
                <img src="{{url(check('thumbnail',$v->data))}}"/>
            </a>
            <div class="hoverLayer">
                <div class="yCenter">
                    <h3>{{$v->title}}</h3>
                </div>
            </div>
        </div>
    </dd>
@endforeach

//分页
{{$content['data']->links('vendor.pagination.default')}}
```


### 详情页

| **变量**| **类型**  | **一句话描述** |
| ---- | ---- |---- |
| $menu | model|栏目信息
| $content | model| 内容
| $content->prew | model| 上一页
| $content->next | model| 下一页
| $content->data | array| 自定义标签
| $content->menu | model| 获取关联的栏目