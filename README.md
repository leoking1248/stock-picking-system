# 选股系统 (Stock Picking System)

基于价值投资理念的A股智能选股系统。

## 系统架构

```
stock-picking-system/
├── scripts/          # 核心脚本
│   ├── full_market_scan.py      # 全市场扫描
│   ├── stock_screener_v2.py     # 漏斗筛选
│   ├── stock_scorer_unified.py  # 统一评分器
│   ├── bank_stock_scorer.py     # 银行股评分
│   ├── growth_stock_scorer.py   # 成长股评分
│   ├── dividend_stock_scorer.py # 高股息评分
│   ├── holdings_monitor.py      # 持仓监控
│   ├── market_sentiment.py      # 市场情绪
│   └── generate_stock_report.py # 报告生成
│
├── core/             # 核心模块
│   ├── data_source_manager.py   # 数据源管理
│   ├── cache_manager.py         # 缓存管理
│   ├── enhanced_data_fetcher.py # 数据获取
│   └── financial_health_analyzer.py # 财务分析
│
├── dashboard/        # 驾驶舱（可视化界面）
│   ├── index.html    # 主页面
│   ├── update.py     # 数据更新脚本
│   └── data/         # 数据文件
│
├── data/             # 数据缓存
│   └── cache/        # 缓存文件
│
├── tests/            # 测试脚本
│
├── utils/            # 工具脚本
│
├── docs/             # 文档
│   ├── STOCK_SYSTEM_GUIDE.md    # 系统指南
│   ├── CACHE_SYSTEM_GUIDE.md    # 缓存系统
│   ├── DATA_SOURCE_GUIDE.md     # 数据源指南
│   └── GROWTH_STOCK_GUIDE.md    # 成长股指南
│
└── market_scan_result.json  # 最新扫描结果
```

## 核心功能

### 1. 全市场扫描
- 漏斗筛选：从 5000+ 只股票筛选到 500-800 只候选股
- 多维度评分：银行股、成长股、高股息三类评分器
- 自动生成报告

### 2. 持仓监控
- 实时行情追踪
- 异常波动预警
- 相关新闻推送

### 3. 市场情绪
- 主要指数 PE 分位数
- 大宗商品价格追踪
- 情绪评分系统

### 4. 驾驶舱
- 可视化界面
- 一键更新数据
- 离线可用

## 使用方法

### 全市场扫描
```bash
cd /Users/leo/.openclaw/workspace/stock-picking-system/scripts
python3 full_market_scan.py
```

### 更新驾驶舱
```bash
cd /Users/leo/.openclaw/workspace/stock-picking-system/dashboard
python3 update.py
```

### 打开驾驶舱
```bash
open /Users/leo/.openclaw/workspace/stock-picking-system/dashboard/index.html
```

## 数据源

| 优先级 | 数据源 | 用途 |
|--------|--------|------|
| 主 | 通达信 (pytdx) | 实时行情 |
| 备1 | 新浪财经 | PE/PB 数据 |
| 备2 | 东方财富 | 财务数据 |

## 定时任务

- **早间市场推送**：每天 8:00
- **全市场扫描**：每天 18:30
- **持仓复盘**：每个交易日 15:45
- **大盘盘后总结**：每个交易日 15:30

## 相关文档

详见 `docs/` 目录。