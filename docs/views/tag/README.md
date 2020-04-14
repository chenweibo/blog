---
title: 标签速查
date: 2020-04-14
---

## 数据库相关

### 数据迁移(强制恢复)

```bash
   php artisan migrate:reset  //强制重新生成表结构
```

### 数据迁移

```bash
   php artisan migrate //强制重新生成表结构
```

### 数据填充

```bash
   php artisan db:seed  //生成默认数据
```
## PSR规范

### 格式化

```bash
   composer run-script phpcs  //自动修复php文件为行业规范
```

## 数据缓存

::: tip 介绍
1.如项目需要切换操作系统需清除各项缓存<br>
:::



### 清除配置信息缓存

```bash
   php artisan config:clear
```
### 清除路由缓存

```bash
   php artisan route:clear
```

### 清除视图缓存

```bash
   php artisan view:clear
```

## blade模版语法



### 全局栏目

``` blade
{{ $globalMenu }}
```

### 站点信息
$site 为数组
``` blade
{{ $site['title'] }}
```
