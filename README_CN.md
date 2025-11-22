# 安全高级笔记本 (SANB)

一个安全的、离线优先的加密笔记应用，采用端到端加密技术，使用 Flutter 构建。

## ✨ 功能特性

### ✅ 当前已实现
- 📝 **笔记管理**：创建、编辑、删除和组织笔记
- 🔐 **密码保险库**：使用 AES-256-GCM 加密安全存储密码和凭证
- 🔒 **零知识架构**：主密码永不离开您的设备
- 📱 **完全离线**：无需网络连接即可完整使用
- 🌓 **深色模式**：精美的浅色和深色主题
- 🔍 **搜索功能**：全文搜索所有笔记
- 💾 **本地存储**：加密的 SQLite 数据库
- 🔑 **安全密钥存储**：使用设备钥匙串管理密钥

### 🚧 计划中的功能（尚未实现）
- ☁️ **云同步**：使用 Firebase 跨设备自动同步 *（即将推出）*
- 📄 **Markdown 渲染**：Markdown 内容的富文本预览 *（即将推出）*
- 🌍 **多语言**：支持多语言国际化 *（即将推出）*
- 📤 **导出/导入**：备份和恢复功能 *（即将推出）*

## 🔒 安全性

- **加密算法**：AES-256-GCM 数据加密
- **密钥派生**：PBKDF2-HMAC-SHA256，210,000 次迭代
- **安全存储**：使用 flutter_secure_storage 管理密钥
- **零知识架构**：主密码永不传输或存储
- **离线优先**：所有数据保存在您的设备上

## 🏗️ 架构设计

应用采用清晰的分层架构：

- **表现层**：UI 组件和状态管理（Riverpod）
- **应用层**：用例和业务逻辑
- **领域层**：实体和仓储接口
- **数据层**：本地数据库（Drift + SQLite）
- **核心层**：加密、工具和错误处理

## 📦 安装使用

### 普通用户
从 [Releases](https://github.com/2h0000/sanb/releases) 下载最新的 APK 文件

**系统要求**：
- Android 5.0（API 21）或更高版本
- 约 60MB 存储空间

**安装步骤**：
1. 下载 APK 文件
2. 在 Android 设备上启用"未知来源"安装
3. 打开 APK 文件进行安装
4. 首次打开时设置主密码

### 开发者

**前置要求**：
- Flutter SDK 3.0 或更高版本
- Dart SDK 3.0 或更高版本

**设置步骤**：
```bash
# 克隆仓库
git clone https://github.com/2h0000/sanb.git
cd sanb

# 安装依赖
flutter pub get

# 生成代码（Drift 和 Riverpod）
dart run build_runner build

# 运行应用
flutter run
```

## 📚 文档

- 📖 [完整文档](./docs/) - 完整的项目文档
- 🚀 [设置指南](./docs/setup/SETUP.md) - 快速开始
- 🔨 [构建指南](./docs/build/BUILD_RELEASE_GUIDE.md) - 构建发布版本
- 💻 [开发文档](./docs/development/) - 架构和开发指南

## 🛠️ 开发

### 代码生成
当修改 Drift 表或 Riverpod providers 时运行：
```bash
dart run build_runner watch
```

### 测试
```bash
flutter test
```

### 构建发布版本
```bash
# Windows
scripts\build\build_release.bat

# Linux/Mac
./scripts/build/build_release.sh
```

详见 [scripts/README.md](./scripts/README.md) 了解更多脚本。

## 📂 项目结构

```
├── lib/                    # 源代码
│   ├── app/               # 应用配置、路由、主题
│   ├── core/              # 核心工具和加密
│   ├── data/              # 数据层（本地数据库）
│   ├── domain/            # 领域层（实体、仓储）
│   └── features/          # 功能模块
│       ├── notes/         # 笔记功能
│       ├── vault/         # 密码保险库
│       ├── auth/          # 认证
│       └── settings/      # 设置
├── docs/                   # 文档
│   ├── setup/             # 设置指南
│   ├── build/             # 构建和发布指南
│   ├── development/       # 开发文档
│   └── history/           # 变更历史
├── scripts/                # 实用脚本
│   ├── build/             # 构建脚本
│   ├── setup/             # 设置脚本
│   └── version/           # 版本管理脚本
├── firebase/               # Firebase 配置（未来使用）
├── assets/                 # 应用资源（图标、图片）
├── android/                # Android 平台代码
└── test/                   # 单元测试和组件测试
```

## 🔧 技术栈

### 核心依赖
- `flutter_riverpod` - 状态管理
- `go_router` - 导航和路由
- `drift` - 本地数据库
- `cryptography` - 加密库
- `flutter_secure_storage` - 安全密钥存储

### 工具库
- `uuid` - UUID 生成
- `intl` - 国际化
- `file_picker` - 文件选择
- `share_plus` - 文件分享

## ❓ 常见问题

### 忘记主密码怎么办？
由于采用零知识架构，主密码无法恢复。如果忘记密码，需要卸载应用重新安装（会丢失所有数据）。请务必牢记您的主密码！

### 数据存储在哪里？
所有数据都加密存储在您的设备本地，使用 SQLite 数据库。应用不会将数据发送到任何服务器。

### 可以在多个设备上使用吗？
当前版本是完全离线的，不支持跨设备同步。云同步功能正在开发中。

### 如何备份数据？
当前版本暂不支持导出/导入功能。建议定期使用 Android 备份功能备份应用数据。

## 🤝 贡献

欢迎贡献代码、报告问题或提出建议！

1. Fork 本仓库
2. 创建您的特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交您的更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 开启一个 Pull Request

## 📄 许可证

本项目采用 MIT 许可证 - 详见 [LICENSE](LICENSE) 文件

## 📮 联系方式

- GitHub Issues: [https://github.com/2h0000/sanb/issues](https://github.com/2h0000/sanb/issues)
- 项目主页: [https://github.com/2h0000/sanb](https://github.com/2h0000/sanb)

## 🙏 致谢

感谢所有开源项目的贡献者，特别是：
- Flutter 团队
- Drift 数据库
- Riverpod 状态管理

---

## 🌟 如果这个项目对你有帮助，请给个 Star ⭐

**English Version**: See [README.md](./README.md)
