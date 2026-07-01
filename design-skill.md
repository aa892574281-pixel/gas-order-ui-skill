# 加油订单详情页 Design Skill

> 适用场景：移动端小程序 / App 内的加油订单详情页、支付订单详情页、消费明细页。  
> 目标：让 AI 根据 Figma 截图或源文件，高还原生成页面设计稿、HTML/CSS、React 页面或可复用 UI 组件。

---

## 1. 页面定位

这是一个移动端订单详情页，核心任务是展示用户的加油消费结果。

页面重点不是营销转化，而是：

- 金额清晰
- 状态明确
- 信息分组清楚
- 费用明细易读
- 底部操作入口明确

整体风格应保持工具型、清爽、克制、可信赖。

---

## 2. 页面基础规格

```yaml
page_type: mobile_order_detail
platform: mini_program_or_mobile_app
canvas_width: 375px
canvas_height: 812px 或按内容纵向延展
background_color: "#F5F6F7"
main_color: 青绿色
layout_direction: vertical
style_keywords:
  - 清爽
  - 克制
  - 工具型
  - 信息清晰
  - 支付订单感
```

页面从上到下依次为：

```text
1. iOS 状态栏
2. 小程序导航栏
3. 顶部绿色订单状态区
4. 加油站信息卡片
5. 金额明细卡片
6. 订单编号卡片
7. 底部固定操作栏
```

---

## 3. 顶部绿色状态区

顶部为页面主视觉区域，使用青绿色渐变背景。

```yaml
header:
  background: vertical_gradient
  gradient_start: "#35C2A8"
  gradient_end: "#36C7AD"
  text_color: "#FFFFFF"
  height: 330px 左右
```

顶部区域包含：

```text
左上角：返回箭头
中间：订单详情
右上角：小程序胶囊按钮
左侧：订单金额 ￥283.8
右侧：订单状态 已加油
```

### 3.1 导航栏规则

```yaml
navigation:
  title: "订单详情"
  title_position: center
  title_font_size: 20px
  title_font_weight: 500-600
  title_color: "#FFFFFF"
  back_icon:
    type: line
    color: "#FFFFFF"
    size: 28px
  mini_program_capsule:
    position: top_right
    style: semi_transparent_dark_green
```

要求：

```text
标题必须水平居中。
返回箭头必须为白色线性图标。
右上角胶囊按钮透明度要轻，不要抢视觉。
```

### 3.2 金额与状态规则

```yaml
amount_status:
  amount_text: "￥283.8"
  amount_font_size: 42px
  amount_font_weight: 500-600
  amount_color: "#FFFFFF"
  amount_position:
    left: 28-32px
    top: navigation_below
  status_text: "已加油"
  status_font_size: 24px
  status_font_weight: 500
  status_color: "#FFFFFF"
  status_position: right
```

要求：

```text
顶部金额是全页最高视觉优先级。
金额必须大于所有正文和卡片标题。
“已加油”与金额保持同一视觉水平。
顶部留白要充足，不要拥挤。
```

---

## 4. 卡片通用规则

所有信息模块使用白色圆角卡片。

```yaml
card:
  background_color: "#FFFFFF"
  border_radius: 8-10px
  margin_left: 14-16px
  margin_right: 14-16px
  padding: 18-20px
  spacing_between_cards: 14-16px
  shadow: none_or_very_light
```

要求：

```text
卡片宽度必须统一。
卡片内部左右 padding 必须统一。
卡片之间间距保持一致。
整体不要使用厚重阴影。
卡片风格应轻量、克制、干净。
```

禁止：

```text
禁止厚重阴影。
禁止彩色描边。
禁止复杂渐变卡片。
禁止营销海报式装饰。
禁止每张卡片圆角不一致。
```

---

## 5. 加油站信息卡片

第一张卡片展示加油站信息与加油参数。

结构：

```text
上半部分：加油站图片 + 加油站名称 + 地址
中间：浅灰分割线
下半部分：油品型号 / 加油枪号 / 加油升数
```

### 5.1 加油站信息区域

```yaml
station_info:
  image:
    size: 50px
    border_radius: 3-4px
    position: left
  title:
    font_size: 18px
    font_weight: 500-600
    color: "#333333"
    max_lines: 1
  address:
    font_size: 14-15px
    color: "#777777"
    max_lines: 1
    overflow: ellipsis
```

要求：

```text
图片在左，文字在右。
加油站名称必须比地址更突出。
地址需要单行省略，不要换行撑高卡片。
```

### 5.2 加油参数区域

字段示例：

```text
油品型号      95#
加油枪号      3号
加油升数      34.5L
```

样式规则：

```yaml
fuel_detail_rows:
  row_height: 36-40px
  label_font_size: 16px
  label_color: "#666666"
  value_font_size: 16px
  value_color: "#333333"
  value_align: right
```

要求：

```text
字段名左对齐。
字段值右对齐。
每一行上下间距保持一致。
不要给字段额外添加图标。
```

---

## 6. 金额明细卡片

第二张卡片是页面核心信息之一，用于展示费用明细。

结构：

```text
费用明细列表
浅灰分割线
实际支付总金额
```

字段示例：

```text
加油金额        ￥200
会员费          ￥99
服务费          ￥1.52
ETC立减         -￥6.72
优惠券抵扣      -￥10
会员加油券      会员优惠    -￥10
实际支付        ￥283.8
```

### 6.1 普通费用行

```yaml
normal_fee_row:
  label_color: "#666666"
  value_color: "#333333"
  font_size: 16px
  row_spacing: 24-28px
  value_align: right
```

### 6.2 优惠费用行

```yaml
discount_fee_row:
  label_color: "#666666"
  value_color: "#FF4B3E"
  font_size: 16px
  value_align: right
  negative_sign: required
```

要求：

```text
优惠金额必须使用红橙色。
优惠金额必须保留负号。
优惠金额不能显示为黑色。
所有金额右对齐。
```

### 6.3 会员优惠标签

```yaml
discount_tag:
  text: "会员优惠"
  background_color: "#F8EFE3"
  text_color: "#9A6A35"
  font_size: 13-14px
  border_radius: 5-6px
  padding_horizontal: 8-10px
  padding_vertical: 4-5px
```

要求：

```text
标签应靠近“会员加油券”对应金额区域。
标签颜色要轻，不要变成强按钮。
标签不能抢过实际支付金额。
```

### 6.4 实际支付行

```yaml
actual_payment:
  label: "实际支付"
  label_font_size: 17px
  label_color: "#333333"
  amount_font_size: 28px
  amount_font_weight: 600
  amount_color: "#333333"
  divider_color: "#EDEDED"
  divider_position: above
```

要求：

```text
实际支付金额是卡片底部最高优先级。
实际支付金额必须与顶部金额一致。
实际支付行上方必须有浅灰分割线。
```

---

## 7. 订单编号卡片

第三张卡片展示订单基础信息。

```yaml
order_info_card:
  background_color: "#FFFFFF"
  border_radius: 8-10px
  row_height: 56-64px
```

字段示例：

```text
订单编号      129381792837981
```

样式规则：

```yaml
order_row:
  label_color: "#666666"
  label_font_size: 16px
  value_color: "#333333"
  value_font_size: 16px
  value_align: right
```

要求：

```text
如果原图只有订单编号，不要主动新增其他字段。
如需扩展，可加入下单时间、支付时间、加油时间、支付方式，但必须由用户明确要求。
```

---

## 8. 底部固定操作栏

底部为白色固定操作栏，始终贴底。

结构：

```text
左侧：加油遇到问题 点击反馈 + 编辑图标
右侧：查看会员按钮
底部：iPhone Home Indicator
```

样式规则：

```yaml
bottom_bar:
  position: fixed_bottom
  background_color: "#FFFFFF"
  height: 78-88px
  border_top: "1px solid #EAEAEA"
  padding_left: 16-28px
  padding_right: 28px
```

### 8.1 左侧反馈入口

```yaml
feedback:
  normal_text: "加油遇到问题"
  normal_text_color: "#666666"
  link_text: "点击反馈"
  link_color: "#2F8DFF"
  icon_color: "#2F8DFF"
  font_size: 16px
```

要求：

```text
反馈入口为辅助操作，不能抢主按钮。
“点击反馈”和编辑图标保持蓝色。
文字应在底部栏内垂直居中。
```

### 8.2 右侧主按钮

```yaml
primary_button:
  text: "查看会员"
  background_color: "#1FCB8B"
  text_color: "#FFFFFF"
  font_size: 16px
  height: 48px
  width: 90-100px
  border_radius: 999px
```

要求：

```text
按钮为绿色胶囊形。
按钮必须在右侧。
按钮文字居中。
按钮不能使用红色、蓝色或紫色。
```

---

## 9. 字体层级

```yaml
typography:
  nav_title:
    size: 20px
    weight: 500-600
    color: "#FFFFFF"
  header_amount:
    size: 42px
    weight: 500-600
    color: "#FFFFFF"
  header_status:
    size: 24px
    weight: 500
    color: "#FFFFFF"
  card_title:
    size: 18px
    weight: 500-600
    color: "#333333"
  body_label:
    size: 16px
    weight: 400
    color: "#666666"
  body_value:
    size: 16px
    weight: 400-500
    color: "#333333"
  weak_text:
    size: 14-15px
    weight: 400
    color: "#777777"
  actual_payment:
    size: 28px
    weight: 600
    color: "#333333"
  bottom_button:
    size: 16px
    weight: 500
    color: "#FFFFFF"
```

要求：

```text
移动端支付类页面文字必须清晰可读。
不要使用过细字体。
金额类文字应比普通字段更突出。
```

---

## 10. 色彩系统

```yaml
colors:
  primary_green: "#32C3A8"
  primary_button_green: "#1FCB8B"
  page_background: "#F5F6F7"
  card_background: "#FFFFFF"
  text_primary: "#333333"
  text_secondary: "#666666"
  text_weak: "#999999"
  text_white: "#FFFFFF"
  discount_red: "#FF4B3E"
  link_blue: "#2F8DFF"
  tag_background: "#F8EFE3"
  tag_text: "#9A6A35"
  divider: "#EDEDED"
```

禁止：

```text
禁止大面积红色。
禁止蓝紫渐变。
禁止改变青绿色主色调。
禁止让优惠红色面积过大。
禁止使用过脏的灰色背景。
```

---

## 11. 对齐与间距规则

```yaml
alignment:
  card_margin_horizontal: 14-16px
  card_padding_horizontal: 18-20px
  label_align: left
  value_align: right
  amount_align: right
  divider_align: content_area
  bottom_button_align: right
```

要求：

```text
所有卡片左右边距一致。
卡片内部字段名左对齐，字段值右对齐。
金额小数点视觉上尽量对齐。
分割线不要贴边，应与内容区对齐。
底部按钮垂直居中。
```

---

## 12. 还原优先级

当无法完全还原时，按以下优先级处理：

```text
第一优先级：页面结构和信息层级
第二优先级：顶部绿色渐变和金额突出
第三优先级：卡片圆角、间距、左右对齐
第四优先级：费用明细颜色和实际支付金额
第五优先级：加油站图片、胶囊按钮、图标细节
```

不要为了细节图标牺牲整体信息层级。

---

## 13. AI 禁止事项

```text
不得新增原图没有的文案。
不得改变订单金额。
不得改变费用字段顺序。
不得把订单详情页做成营销海报。
不得使用厚重阴影。
不得使用复杂插画背景。
不得使用过多图标。
不得让卡片宽度不一致。
不得让底部操作栏漂浮在页面中间。
不得把优惠金额显示为黑色。
不得遗漏 iOS 状态栏。
不得遗漏底部 Home Indicator。
不得擅自增加促销 Banner。
不得把会员优惠标签做成强按钮。
```

---

## 14. 输出检查清单

AI 输出后，必须逐项检查：

```text
[ ] 页面是否为 375px 移动端竖屏？
[ ] 顶部是否为青绿色渐变？
[ ] 标题“订单详情”是否居中？
[ ] 顶部金额是否最大、最醒目？
[ ] “已加油”是否在右侧？
[ ] 卡片左右边距是否统一？
[ ] 加油站图片、名称、地址是否正确分组？
[ ] 油品型号、加油枪号、加油升数是否右对齐？
[ ] 费用明细字段顺序是否正确？
[ ] 优惠金额是否为红橙色并保留负号？
[ ] “会员优惠”标签是否为浅米色？
[ ] 实际支付金额是否放大并与顶部金额一致？
[ ] 底部操作栏是否固定在底部？
[ ] “点击反馈”是否为蓝色？
[ ] “查看会员”按钮是否为绿色胶囊按钮？
[ ] 是否没有新增无关文案或装饰？
```

---

## 15. 推荐给 AI 的执行 Prompt

```text
请根据上传的加油订单详情页截图，生成高还原移动端 UI 页面。

必须遵守以下 Design Skill：
1. 页面为移动端小程序订单详情页，宽度 375px。
2. 顶部为青绿色渐变状态区，包含 iOS 状态栏、小程序导航栏、订单金额和订单状态。
3. 中部为白色圆角卡片，展示加油站信息、加油参数、费用明细和订单编号。
4. 底部为固定白色操作栏，左侧为反馈入口，右侧为绿色胶囊按钮。
5. 保持原图的信息层级、边距、圆角、字体大小和颜色关系。
6. 不得新增文案，不得改变金额，不得改变字段顺序。
7. 优惠金额必须为红橙色并保留负号。
8. 实际支付金额必须与顶部金额保持一致。
9. 优先保证布局、对齐、金额突出和卡片分组清晰。
```

---

## 16. 一句话总结

这个界面的设计核心是：

> 青绿色状态头部突出订单金额，白色圆角卡片承载订单分组信息，费用明细右对齐，优惠用红橙色弱强调，底部固定操作栏提供反馈与会员入口。
