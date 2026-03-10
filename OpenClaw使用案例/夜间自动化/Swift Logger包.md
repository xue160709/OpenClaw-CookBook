# Swift Logger 包

**分类:** 夜间自动化  
**编号:** #37

## 🎯 痛点
- Swift项目缺少统一的日志记录规范
- 手动添加日志代码繁琐，容易遗漏
- 不同模块的日志格式不统一，难以分析

## ⚡ 核心功能
1. 自动生成符合Swift项目规范的日志封装包
2. 支持多种日志级别（debug、info、warning、error）
3. 自动添加文件路径和行号信息
4. 支持日志输出到控制台和文件
5. 可配置的日志格式和过滤规则

## 🛠️ 所需技能
| 技能 | 用途 |
|------|------|
| Swift开发 | 编写Swift日志框架 |
| 包管理 | 创建SPM/CocoaPods包 |

## 📝 Prompt 模板
```
你是Swift开发助手。请为项目创建一个可复用的日志记录包。

要求：
1. 创建 SwiftLogger 包，包含：
   - Logger 类：主日志记录器
   - LogLevel 枚举：debug、info、warning、error、critical
   - LogDestination 协议：支持多种输出目标

2. 功能特性：
   - 线程安全
   - 支持 emoji 前缀（🔍、ℹ️、⚠️、❌、🔥）
   - 自动捕获文件名、函数名、行号
   - 可配置日志格式：[时间] [级别] [位置] 内容
   - 支持按级别过滤
   - 文件输出支持滚动（单个文件最大10MB，保留5个）

3. 使用示例：
   ```swift
   import SwiftLogger
   
   let logger = Logger(tag: "MyApp")
   
   logger.debug("调试信息")
   logger.info("普通信息")
   logger.warning("警告")
   logger.error("错误")
   ```

4. 输出为完整的 Swift 包结构：
   - Package.swift
   - Sources/SwiftLogger/Logger.swift
   - Sources/SwiftLogger/LogLevel.swift
   - Tests/SwiftLoggerTests/
   - README.md

请生成完整的代码。
```
