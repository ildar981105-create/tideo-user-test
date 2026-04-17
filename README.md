# tideo-user-test

即插即用的用户测试工具包：被动埋点（tracker.js）+ 主动问卷（survey.js），可配置化适用于任何 Web 产品。

## 文件结构

```
assets/
├── tracker.js          # 埋点核心（读取 TRACKER_CONFIG）
├── tracker-config.js    # Tracker 配置模板
├── survey.js           # 问卷核心（读取 SURVEY_CONFIG）
└── survey-config.js    # Survey 配置模板

references/
├── tracker-spec.md     # tracker API 规范
└── survey-spec.md      # survey API 规范
```

## 快速使用

### 零配置引入（使用 Tideo 默认配置）

```html
<script src="assets/tracker-config.js"></script>
<script>window.TRACKER_CONFIG.endpoint = 'https://your-server.com/track';</script>
<script src="assets/tracker.js"></script>
<script src="assets/survey.js"></script>
```

### 深度定制

```html
<script src="assets/survey-config.js"></script>
<script>
  window.SURVEY_CONFIG.productName = '我的产品';
  window.SURVEY_CONFIG.tasks = [
    { id:'T1', label:'完成注册', detect:'signup_done' },
    { id:'T2', label:'完成下单', detect:'order_done' }
  ];
  window.SURVEY_CONFIG.checkpoints = [
    { id:'ease', trigger:'signup_done', type:'rating', question:'注册顺利吗？', scale:5, labels:['很难','很顺'] }
  ];
</script>
<script src="assets/tracker.js"></script>
<script src="assets/survey.js"></script>
```

## 核心 API

### Tracker

- `TideoTracker.record(action)` — 手动埋点
- `TideoTracker.milestone(name)` — 标记里程碑
- `TideoTracker.phaseStart/End(name)` — 阶段边界

### Survey

- `window.SURVEY_CONFIG.tasks` — 任务列表
- `window.SURVEY_CONFIG.checkpoints` — 检查点触发器
- `window.SURVEY_CONFIG.sus` — SUS 题目自定义
