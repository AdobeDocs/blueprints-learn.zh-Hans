---
source-git-commit: ef1c207922c1079117d8bd255dbfa32a1527b014
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 3%

---
# 用例图标样式指南

## 概述

用例图标用作用例目录表中的可视化标识符。 它们必须能够立即以40px显示宽度进行识别，同时保持原始分辨率1024x1024的品质。

## 技术规范

| 属性 | 值 |
| --- | --- |
| 维度 | 1024 x 1024像素 |
| 格式化 | PNG（8位RGB或RGBA） |
| 文件大小 | 900KB - 1.4MB典型值 |
| 显示大小 | 目录表中的40px宽度 |
| 命名 | `icon-{kebab-case-name}.png` |
| 存储路径 | `/help/blueprints/industry-use-cases/assets/use-case-icons/{industry}/` |

## 视觉风格指南

### 合成
- **单个中心主题** — 每个图标应具有一个表示用例概念的清晰可视隐喻
- **居中的合成** — 主主题应以平衡的空格居中
- **无文本** — 文本在40px时无法辨认；完全依赖视觉隐喻
- **没有复杂场景** — 避免使用多元素合成、具有多个对象的背景或叙述性场景
- **粗体剪影** — 图标的形状应该可以被识别为小剪影

### 颜色和色调
- **干净的现代调色板** — 使用专业的、适合公司的颜色
- **行业凝聚力** — 同一行业内的图标应该感觉像是属于一起
- **高对比度** — 确保主主题在背景中清晰可见
- **避免使用霓虹色或过度饱和的颜色** — 使调色板保持精致和专业

### 样式
- **现代和专业** — 线条干净，表面光洁
- **一致的呈现** — 所有图标应该看起来都来自同一设计系统
- **3D或平面是可接受的** — 但在垂直行业中是一致的
- **避免照片逼真** — 为了保持一致性，首选使用插图或渲染样式
- **没有品牌徽标或商标图像** — 使用通用的视觉隐喻

### 小尺寸易读性测试
在最终确定之前，请在心理上将图像缩放到40像素：
- 你能辨认出主旨吗？
- 前景和背景之间的对比度是否足够？
- 是否有细微的细节会变成视觉噪音？
- 形状是否清晰易读，没有颜色（在辅助功能的情况下）？

## 按行业划分的可视化隐喻示例

### 零售
| 用例 | 视觉隐喻 |
| --- | --- |
| 已放弃的购物车 | 包含商品的购物车 |
| 产品推荐 | 礼品盒或策划的产品 |
| 交叉销售追加销售 | 连接的购物项目 |
| 欢迎系列 | 欢迎卡或礼品 |
| 价格下降 | 带向下箭头的价格标签 |

### 汽车
| 用例 | 视觉隐喻 |
| --- | --- |
| 服务提醒 | 扳手或服务日历 |
| 车辆购买 | 带钥匙的车 |
| 以旧换新 | 汽车更换箭头 |
| 联网汽车 | 具有数字连接的汽车 |

### 医疗保健
| 用例 | 视觉隐喻 |
| --- | --- |
| 约会提醒 | 带有听诊器的日历 |
| 药物依从性 | 药瓶或处方 |
| 预防性护理 | 带有健康标志的防护罩 |

### 金融服务
| 用例 | 视觉隐喻 |
| --- | --- |
| 潜在客户培养 | 生长图或育苗 |
| 流失预防 | 屏蔽或固定符号 |
| 生命阶段 | 生命周期里程碑时间线 |

### B2B
| 用例 | 视觉隐喻 |
| --- | --- |
| ABM | 通过构建定位 |
| 商机评分 | 计分仪或温度计 |
| 合同续订 | 具有刷新符号的文档 |

### 旅游和酒店业
| 用例 | 视觉隐喻 |
| --- | --- |
| 放弃购买 | 行李箱或预订 |
| 忠诚度计划 | 会员卡或星级徽章 |
| 预订提醒 | 带有飞机/酒店的日历 |

### 保险
| 用例 | 视觉隐喻 |
| --- | --- |
| 策略续订 | 具有续订箭头的文档 |
| 索赔流程 | 带有复选标记的剪贴板 |
| 交叉销售 | 连接的策略文档 |

### 媒体和娱乐
| 用例 | 视觉隐喻 |
| --- | --- |
| 新内容 | 播放按钮或焦点 |
| 内容推荐 | 精选播放列表或星级内容 |
| 订阅流失 | 已中断的订阅卡 |

### 电信
| 用例 | 视觉隐喻 |
| --- | --- |
| 计划优化 | 带齿轮的信号条 |
| 设备升级 | 带向上箭头的电话 |
| 流失预防 | 带有信号的屏蔽 |

## 图像生成提示模板

使用此模板作为起点，为每个用例自定义主题和详细信息：

```
A clean, modern icon illustration of {visual metaphor} representing {use case concept}. Professional corporate design style with bold shapes and clean lines. Single centered subject on a {solid/gradient} background. High contrast, vibrant but refined color palette. No text, no fine details, no complex backgrounds. The icon must be clearly recognizable when scaled down to 40 pixels. Square format, 1024x1024 pixels.
```

### 提示自定义提示

- **请具体说明主题** — “内装两个彩色礼盒的鲜红色购物车”好于“购物车”
- **指定背景处理** — “在柔和的蓝色渐变背景上”或“在带有细微阴影的干净白色背景上”
- **提及照明** — “柔和的工作室照明”或“柔和的环境光晕”有助于实现一致性
- **添加样式修饰符** — “极简型”、“几何”、“等角型”或“平面设计”以引导美学
- **如果支持则包含负面提示** — “无文本、无水印、无边框、无照片级逼真元素”

## 现有图标库存

### 按行业

**零售业（9个图标）：**
icon-abandoned-cart、icon-inventory-urgency、icon-price-drop、icon-product-recommendations、icon-category-pages、icon-welcome-series、icon-replication、icon-post-purchase、icon-cross-sell-upsell

**汽车（12个图标）：**
图标 — 服务 — 提醒、图标 — 召回 — 通知、图标 — test-drive、图标 — 模型 — 启动、图标 — 交易 — in、图标 — 部件 — 附件、图标 — 保修、图标 — connected-car、图标 — 经销商 — 网络、图标 — 车辆 — 购买、图标融资、图标 — 所有者 — 忠诚度

**金融服务（6个图标）：**
图标 — 潜在客户培养、图标 — 帐户 — 仪表板、图标 — 产品推荐、图标流失预防、图标 — 生命阶段

**医疗保健（4个图标）：**
图标预约提醒、图标访问后、图标预防性护理、图标药物遵守

**保险（3个图标）：**
icon-policy-renewal， icon-claims-process， icon-cross-sell

**媒体和娱乐（3个图标）：**
icon-new-content， icon-content-recommendations， icon-subscription-churn

**电信（3个图标）：**
icon-plan-optimization、icon-device-upgrade、icon-churn-prevention

**旅游和酒店业（12个图标）：**
icon-cart-abandonment， icon-booking-reminers， icon-sequential-campaigns， icon-personalized-homepage， icon-high-intent， icon-post-booking-upsell， icon-win-back， icon-dynamic-itinerary， icon-recwed-browsed， icon-group-booking， icon-exit-intent， icon-loyalty-program

**B2B（11个图标）：**
icon-webinar-demo， icon-abm， icon-lead-scoring， icon-content-personalization， icon-event-registration， icon-trial-conversion， icon-customer-onboarding， icon-competitive-replacement， icon-case-study， icon-contract-renewal， icon-upsell-expansion
