## Vue组件--仿淘宝商品放大镜效果
---
### 效果图
![avatar](https://cdn.nlark.com/yuque/0/2021/png/1280868/1620311108900-953b0c32-fee3-47c0-b569-4abf1fd5e17f.png)
---
### 可配置项
|    参数名    | 类型     | 功能                |
| ----------  | ---     | ---                |
| boxSize     |  Number | 配置主图图片框大小    |
| hoverBoxSize|  Number | 主图中hover阴影框大小 |
| picURL      |  String | 引入图片地址         |

---
### 右侧放大倍数由  boxSize / hoverBoxSize 计算得出