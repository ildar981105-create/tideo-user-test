# Tideo User Test

> Web 应用用户测试完整工具链 — 被动埋点 + 主动问卷，即插即用

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![GitHub stars](https://img.shields.io/github/stars/ildar981105-create/tideo-user-test)](https://github.com/ildar981105-create/tideo-user-test/stargazers)
[![GitHub topics](https://img.shields.io/github/topics/codebuddy-skill)](https://github.com/topics/codebuddy-skill)

## 🎯 5 分钟集成

```html
<!-- 1. 引入配置 -->
<script src="survey-config.js"></script>
<script>
  window.SURVEY_CONFIG = {
    productName: '我的产品',
    tasks: [
      { id:'T1', label:'完成注册', detect:'signup_done'    },
      { id:'T2', label:'完成下单', detect:'order_done'     },
      { id:'T3', label:'完成支付', detect:'payment_done'  }
    ]
  };
</script>

<!-- 2. 引入核心文件 -->
<script src="tracker.js"></script>
<script src="survey.js"></script>
```

业务代码中触发 milestone：

```javascript
TideoTracker.milestone('signup_done');   // 注册完成 → 触发 T1 任务
TideoTracker.milestone('order_done');    // 下单完成 → 触发 T2 任务
TideoTracker.milestone('payment_done');  // 支付完成 → 触发 T3 + 总结问卷
```

## 核心模块

| 模块 | 功能 | 定制点 |
|------|------|--------|
| **tracker.js** | 6 维埋点（操作序列/犹豫/困惑/停留/里程碑/热区） | `TRACKER_CONFIG.endpoint` |
| **survey.js** | 主动问卷（任务面板 + checkpoint 微问卷 + SUS/EV/NPS） | `SURVEY_CONFIG.tasks` |

## 完整功能说明

详见 [SKILL.md](SKILL.md)

## 使用场景

- 🧪 可用性测试 — 还原用户操作路径，发现卡点
- 📋 情境问卷 — 关键步骤后即时收集用户反馈
- 📊 满意度调研 — 内置 SUS/EV/NPS 标准量表
- 🔍 犹豫/困惑检测 — 自动识别用户在页面的困惑行为

## License

MIT © Tideo
