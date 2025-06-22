# CXSS - 辰星智能分流规则

[![GitHub stars](https://img.shields.io/github/stars/3377/cxss.svg)](https://github.com/3377/cxss/stargazers)
[![GitHub license](https://img.shields.io/github/license/3377/cxss.svg)](https://github.com/3377/cxss/blob/main/LICENSE)
[![GitHub release](https://img.shields.io/github/release/3377/cxss.svg)](https://github.com/3377/cxss/releases)

## 📋 项目简介

CXSS（ChenXing Smart Split）是基于 ACL4SSR 规则优化的 Clash 智能分流配置，专为辰星服务生态设计，提供高效、稳定的网络代理分流解决方案。

### ✨ 主要特性

- 🌟 **辰星服务优先级**：三层辰星服务分流（直连/AI/翻墙）
- 🚀 **智能负载均衡**：支持自动选择和负载均衡策略
- 🛡️ **安全防护**：内置广告拦截和应用净化
- 🌍 **全球分流**：优化的国内外服务分流规则
- 🤖 **AI服务支持**：专门优化的AI平台访问规则
- 📱 **多平台兼容**：支持各种Clash客户端

## 🗂️ 项目结构

```
cxss/
├── cxss.ini                    # 主配置文件
├── rule/                       # 规则文件目录
│   ├── 辰星直连.list           # 辰星直连规则
│   ├── 辰星AI.list             # 辰星AI服务规则
│   └── 辰星翻墙.list           # 辰星翻墙规则
└── README.md                   # 项目说明文档
```

## 🚀 快速开始

### 1. 获取配置文件

**方法一：直接使用在线地址**
```
https://raw.githubusercontent.com/3377/cxss/main/cxss.ini
```

**方法二：下载到本地**
```bash
git clone https://github.com/3377/cxss.git
```

### 2. 导入到Clash客户端

1. 复制配置文件地址
2. 在Clash客户端中添加配置
3. 选择合适的策略组
4. 开始使用

## 📊 策略组说明

### 🌟 辰星服务（最高优先级）

| 策略组 | 用途 | 推荐节点 |
|--------|------|----------|
| 🌟 辰星直连 | 辰星本地化服务 | 直连/负载均衡 |
| 🤖 辰星AI | 辰星AI平台服务 | 美国节点 |
| 🌍 辰星翻墙 | 辰星国际化服务 | 香港/美国节点 |

### 🚀 核心策略组

| 策略组 | 类型 | 说明 |
|--------|------|------|
| 🚀 节点选择 | select | 主要代理选择策略 |
| ♻️ 自动选择 | url-test | 自动测速选择最快节点 |
| ⚖️ 负载均衡 | load-balance | 分散流量到多个节点 |
| ☑️ 手动切换 | select | 手动选择具体节点 |

### 🎯 功能策略组

| 策略组 | 用途 | 默认策略 |
|--------|------|----------|
| 📱 谷歌账户 | Google账户服务 | 代理优先 |
| 🤖 OpenAI | AI服务平台 | 美国节点 |
| 📹 油管视频 | YouTube视频 | 代理访问 |
| 🎥 奈飞视频 | Netflix流媒体 | 专用节点 |
| Ⓜ️ 微软服务 | Microsoft服务 | 直连优先 |
| 🍎 苹果服务 | Apple服务 | 直连优先 |

## 🔧 自定义配置

### 修改辰星规则

1. 编辑 `rule/` 目录下的对应文件
2. 添加您的域名或IP规则
3. 提交更改并推送到仓库

### 规则格式说明

```ini
# 域名规则
DOMAIN,example.com                    # 精确匹配域名
DOMAIN-SUFFIX,example.com             # 匹配域名及其子域名
DOMAIN-KEYWORD,keyword                # 匹配包含关键词的域名

# IP规则
IP-CIDR,192.168.1.0/24               # IP段规则
IP-CIDR6,2001:db8::/32               # IPv6段规则

# 地理位置规则
GEOIP,CN                             # 中国IP
GEOIP,US                             # 美国IP
```

### 策略组类型

```ini
# 手动选择
custom_proxy_group=组名`select`选择器

# 自动测速
custom_proxy_group=组名`url-test`筛选条件`测试URL`间隔`延迟容差`超时

# 负载均衡
custom_proxy_group=组名`load-balance`筛选条件`测试URL`间隔`延迟容差`超时
```

## 📈 更新频率

| 规则类型 | 更新间隔 | 说明 |
|----------|----------|------|
| 辰星服务规则 | 6小时 | 根据服务变化及时更新 |
| 基础网络规则 | 24小时 | 相对稳定，定期更新 |
| 安全防护规则 | 12小时 | 广告拦截需要及时更新 |
| AI服务规则 | 3小时 | 新兴服务，变化较快 |

## 🛠️ 高级配置

### 可选功能

```ini
# 节点过滤
exclude_remarks=(到期|剩余|流量|时间)  # 排除特定关键词节点
emoji=true                           # 启用国旗表情
udp=true                            # 启用UDP转发
```

### 测试参数优化

- **延迟容差**：50ms（平衡稳定性与速度）
- **测试间隔**：300秒（5分钟）
- **测试URL**：`http://www.gstatic.com/generate_204`

## 🤝 贡献指南

1. Fork 本仓库
2. 创建特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 创建 Pull Request

## 📄 许可证

本项目基于 MIT 许可证开源 - 查看 [LICENSE](LICENSE) 文件了解详情。

## 🙏 致谢

- [ACL4SSR](https://github.com/ACL4SSR/ACL4SSR) - 提供基础规则集
- [Clash](https://github.com/Dreamacro/clash) - 优秀的代理工具
- 所有贡献者和用户的支持

## 📞 联系方式

- GitHub Issues: [提交问题](https://github.com/3377/cxss/issues)
- Email: 35794406@qq.com

## 🔄 更新日志

### v1.0.0 (2025-01-XX)
- 🎉 初始版本发布
- ✨ 实现辰星服务三层分流
- 🚀 优化策略组配置
- 📝 完善文档说明

---

⭐ 如果这个项目对您有帮助，请给我们一个 Star！ 