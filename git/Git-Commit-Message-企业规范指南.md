# Git Commit Message 企业规范指南

## 目录
- [1. 概述](#1-概述)
- [2. 标准格式](#2-标准格式)
- [3. Type 类型说明](#3-type-类型说明)
- [4. Scope 范围说明](#4-scope-范围说明)
- [5. Subject 主题写作规则](#5-subject-主题写作规则)
- [6. 详细规范要求](#6-详细规范要求)
- [7. 实际示例](#7-实际示例)
- [8. 团队协作建议](#8-团队协作建议)
- [9. 工具推荐](#9-工具推荐)
- [10. 企业定制化规范](#10-企业定制化规范)
- [11. 常见问题](#11-常见问题)

---

## 1. 概述

规范的Git commit message是团队协作的重要基础，它能够：
- 提高代码历史的可读性
- 便于快速定位问题
- 支持自动化工具生成CHANGELOG
- 提升团队协作效率

本文档基于 [Conventional Commits](https://www.conventionalcommits.org/) 规范，结合企业实际需求制定。

## 2. 标准格式

### 基本结构
```
<type>(<scope>): <subject>

<body>

<footer>
```

### 完整示例
```
feat(user): 添加用户登录功能

- 实现JWT token认证
- 添加登录状态验证
- 完善错误处理机制

Closes #123
```

## 3. Type 类型说明

| 类型 | 描述 | 使用场景 | 示例 |
|------|------|----------|------|
| **feat** | 新功能 | 添加新的功能特性 | `feat(auth): 添加用户注册功能` |
| **fix** | 修复bug | 修复代码中的错误 | `fix(login): 修复登录失败的问题` |
| **docs** | 文档更新 | 更新文档、注释等 | `docs(api): 更新接口文档` |
| **style** | 代码格式化 | 不影响代码逻辑的格式调整 | `style(css): 统一代码缩进格式` |
| **refactor** | 重构代码 | 代码重构，不添加功能不修复bug | `refactor(service): 重构用户服务层` |
| **test** | 测试相关 | 添加、修改测试用例 | `test(unit): 添加用户模块单元测试` |
| **chore** | 构建/工具变动 | 构建工具、依赖更新等 | `chore(deps): 升级依赖版本` |
| **perf** | 性能优化 | 提升性能的代码修改 | `perf(db): 优化数据库查询性能` |
| **ci** | CI/CD配置 | 持续集成配置修改 | `ci(jenkins): 添加自动化部署脚本` |
| **build** | 构建系统 | 构建工具配置修改 | `build(webpack): 优化打包配置` |
| **revert** | 回退代码 | 回退之前的提交 | `revert: 回退feat(user): 添加用户功能` |

## 4. Scope 范围说明

### 常见的scope分类

#### 4.1 按模块名称
- `user` - 用户模块
- `order` - 订单模块
- `payment` - 支付模块
- `auth` - 认证模块

#### 4.2 按层级结构
- `controller` - 控制器层
- `service` - 服务层
- `dao` - 数据访问层
- `model` - 数据模型

#### 4.3 按功能领域
- `login` - 登录功能
- `register` - 注册功能
- `profile` - 个人资料
- `dashboard` - 仪表盘

#### 4.4 按技术组件
- `redis` - Redis相关
- `mysql` - MySQL相关
- `kafka` - Kafka相关
- `docker` - Docker相关

## 5. Subject 主题写作规则

### ✅ 好的写法
```
feat(auth): 添加JWT token验证机制
fix(payment): 修复支付回调处理异常
docs(readme): 完善项目安装说明
refactor(service): 优化用户数据查询逻辑
```

### ❌ 避免的写法
```
fix bug          # 太模糊，没有说明具体问题
update code      # 没有说明具体修改内容
修改了一些文件    # 中英文混用，不够具体
fix             # 缺少具体描述
```

### 写作要点
- 使用现在时态："添加"而不是"添加了"
- 保持简洁明了，突出核心内容
- 首字母小写
- 结尾不要句号
- 长度不超过50个字符

## 6. 详细规范要求

### 6.1 主题行(Subject)规范
- **长度限制**：不超过50个字符
- **时态要求**：使用现在时态
- **大小写**：首字母小写
- **标点符号**：结尾不要句号
- **语言统一**：团队内保持一致，推荐中文

### 6.2 正文(Body)规范
- **换行要求**：主题和正文之间必须空一行
- **长度限制**：每行不超过72个字符
- **内容要求**：说明修改的原因和内容，而不是具体实现
- **格式建议**：使用列表形式更清晰

### 6.3 页脚(Footer)规范
- **关闭issue**：`Closes #123`, `Fixes #456`
- **破坏性变更**：`BREAKING CHANGE: 详细说明`
- **协作信息**：`Co-authored-by: 姓名 <email@example.com>`

## 7. 实际示例

### 7.1 新功能提交
```
feat(practice): 添加章节练习功能

- 实现章节列表接口
- 添加用户进度跟踪
- 支持练习记录保存
- 完善错误处理和日志记录

Closes #PRD-001
```

### 7.2 Bug修复提交
```
fix(user): 修复用户登录JWT token过期问题

问题描述：
- 用户登录后token在30分钟后过期
- 过期后用户需要重新登录

解决方案：
- 延长token有效期至2小时
- 添加token自动刷新机制
- 优化过期提示用户体验

Fixes #BUG-456
```

### 7.3 重构代码提交
```
refactor(service): 重构用户服务层代码结构

- 提取公共方法到工具类
- 优化数据库查询逻辑
- 统一异常处理机制
- 改善代码可读性和维护性

Co-authored-by: 张三 <zhangsan@company.com>
```

### 7.4 文档更新提交
```
docs(api): 更新用户接口文档

- 添加新增接口的参数说明
- 完善错误码说明
- 更新请求示例
- 修正文档格式问题
```

### 7.5 性能优化提交
```
perf(db): 优化用户查询性能

- 添加用户表索引
- 优化复杂查询SQL
- 引入Redis缓存机制
- 减少数据库查询次数

性能提升：查询时间从200ms降低到50ms
```

## 8. 团队协作建议

### 8.1 创建提交模板

#### 设置全局模板
```bash
# 创建模板文件
touch ~/.gitmessage

# 设置为默认模板
git config --global commit.template ~/.gitmessage
```

#### 模板内容示例
```
# <type>(<scope>): <subject>
# 
# <body>
# 
# <footer>

# ==================== 提交规范说明 ====================
# type: feat, fix, docs, style, refactor, test, chore, perf, ci, build, revert
# scope: 模块名称或影响范围
# subject: 简短描述（不超过50字符）
# body: 详细描述（可选）
# footer: 关闭issue或破坏性变更说明（可选）
# ====================================================
```

### 8.2 提交前检查清单
- [ ] 类型(type)选择是否正确
- [ ] 范围(scope)是否明确
- [ ] 主题(subject)是否简洁明了
- [ ] 是否需要详细说明(body)
- [ ] 是否关联相关issue
- [ ] 是否有破坏性变更需要说明
- [ ] 拼写和语法是否正确

### 8.3 团队约定建议
1. **统一语言**：团队内统一使用中文或英文
2. **定期回顾**：定期检查提交质量，持续改进
3. **工具统一**：团队使用相同的提交工具和配置
4. **培训机制**：新成员入职时进行规范培训

## 9. 工具推荐

### 9.1 Commitizen - 交互式提交工具

#### 安装
```bash
# 全局安装
npm install -g commitizen cz-conventional-changelog

# 项目中安装
npm install --save-dev commitizen cz-conventional-changelog
```

#### 配置
```bash
# 全局配置
echo '{ "path": "cz-conventional-changelog" }' > ~/.czrc

# 项目配置 package.json
{
  "config": {
    "commitizen": {
      "path": "cz-conventional-changelog"
    }
  }
}
```

#### 使用
```bash
# 代替 git commit
git cz
```

### 9.2 Commitlint - 提交信息校验

#### 安装
```bash
npm install --save-dev @commitlint/cli @commitlint/config-conventional
```

#### 配置 commitlint.config.js
```javascript
module.exports = {
  extends: ['@commitlint/config-conventional'],
  rules: {
    'type-enum': [2, 'always', [
      'feat', 'fix', 'docs', 'style', 'refactor', 
      'test', 'chore', 'perf', 'ci', 'build', 'revert'
    ]],
    'subject-max-length': [2, 'always', 50],
    'body-max-line-length': [2, 'always', 72]
  }
}
```

#### 集成到Git Hook
```bash
# 安装 husky
npm install --save-dev husky

# 添加 hook
npx husky add .husky/commit-msg 'npx --no-install commitlint --edit $1'
```

### 9.3 其他有用工具

#### conventional-changelog - 自动生成CHANGELOG
```bash
npm install --save-dev conventional-changelog-cli
npx conventional-changelog -p angular -i CHANGELOG.md -s
```

#### Git别名设置
```bash
# 设置常用别名
git config --global alias.cm 'commit -m'
git config --global alias.co 'checkout'
git config --global alias.st 'status'
git config --global alias.br 'branch'
```

## 10. 企业定制化规范

### 10.1 自定义Type类型
根据企业需求，可以添加特定类型：
```javascript
// commitlint.config.js
module.exports = {
  extends: ['@commitlint/config-conventional'],
  rules: {
    'type-enum': [2, 'always', [
      'feat', 'fix', 'docs', 'style', 'refactor', 
      'test', 'chore', 'perf', 'ci', 'build', 'revert',
      'hotfix',    // 紧急修复
      'release',   // 发布相关
      'merge',     // 合并相关
      'wip'        // 工作进行中
    ]]
  }
}
```

### 10.2 自定义Scope规则
```javascript
// commitlint.config.js
module.exports = {
  extends: ['@commitlint/config-conventional'],
  rules: {
    'scope-enum': [2, 'always', [
      'user', 'order', 'payment', 'auth',
      'controller', 'service', 'dao', 'model',
      'config', 'utils', 'deps'
    ]]
  }
}
```

### 10.3 多语言支持
```javascript
// commitlint.config.js
module.exports = {
  extends: ['@commitlint/config-conventional'],
  rules: {
    'subject-case': [0], // 禁用大小写检查，支持中文
    'type-enum': [2, 'always', [
      'feat', '功能',
      'fix', '修复',
      'docs', '文档',
      'style', '格式',
      'refactor', '重构',
      'test', '测试',
      'chore', '构建'
    ]]
  }
}
```

## 11. 常见问题

### Q1: 一次提交包含多个类型的修改怎么办？
**A:** 建议拆分成多次提交，每次提交只做一件事。如果确实需要在一次提交中包含多个修改，选择最主要的类型，并在body中详细说明。

### Q2: 紧急修复可以简化commit message吗？
**A:** 即使是紧急修复，也应该遵循基本格式。可以使用`hotfix`类型或`fix`类型，但要确保信息清晰，便于后续追踪。

### Q3: 如何处理合并提交？
**A:** 使用有意义的合并信息：
```
merge: 合并feature/user-login分支到develop

- 新增用户登录功能
- 包含单元测试
- 已通过代码审查
```

### Q4: 回退提交如何编写？
**A:** 使用`revert`类型，并说明回退的原因：
```
revert: 回退feat(payment): 添加支付宝支付功能

回退原因：支付宝接口调整，需要重新实现

This reverts commit a1b2c3d4e5f6g7h8i9j0k1l2m3n4o5p6q7r8s9t0.
```

### Q5: 如何处理破坏性变更？
**A:** 在footer中明确标注：
```
feat(api): 重构用户接口

- 统一返回格式
- 优化错误处理
- 提升接口性能

BREAKING CHANGE: 用户接口返回格式已变更，请更新客户端代码
```

---

## 总结

规范的Git commit message是团队协作的重要基础。通过遵循标准格式、使用合适的工具、建立团队约定，可以大大提升代码管理的效率和质量。

建议团队：
1. 统一采用本规范
2. 配置相应的工具链
3. 定期检查和优化
4. 持续培训和改进

**记住：好的commit message是写给未来的自己和团队成员的，它应该清晰、准确、有意义。**

---

*最后更新时间：2024年*
*版本：v1.0* 