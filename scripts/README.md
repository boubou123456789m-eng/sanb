# 🛠️ 项目脚本

本目录包含用于构建、设置和维护项目的实用脚本。

## 📁 脚本分类

### 🔨 [build/](./build/) - 构建脚本
用于构建发布版本的脚本

- **build_release.bat** / **build_release.sh** - 完整的发布构建流程
  - 清理旧构建
  - 获取依赖
  - 运行代码生成
  - 构建 APK 和 AAB
  - 使用代码混淆和符号分离

**使用方法**：
```bash
# Windows
scripts\build\build_release.bat

# Linux/Mac
./scripts/build/build_release.sh
```

---

### 🎨 [setup/](./setup/) - 设置脚本
用于配置应用图标和启动屏幕

- **setup_icons.bat** / **setup_icons.sh** - 生成应用图标和启动屏幕
  - 安装依赖
  - 生成应用图标
  - 生成启动屏幕

**使用方法**：
```bash
# Windows
scripts\setup\setup_icons.bat

# Linux/Mac
./scripts/setup/setup_icons.sh
```

**注意**：确保 `assets/icon/` 和 `assets/splash/` 目录中有相应的图片文件。

---

### 🔢 [version/](./version/) - 版本管理脚本
用于更新应用版本号

- **update_version.bat** / **update_version.sh** - 更新 pubspec.yaml 中的版本号

**使用方法**：
```bash
# Windows
scripts\version\update_version.bat 1.0.3 4

# Linux/Mac
./scripts/version/update_version.sh 1.0.3 4
```

参数说明：
- 第一个参数：版本名称（如 1.0.3）
- 第二个参数：构建号（如 4）

---

## 🚀 快速开始

### 首次设置
1. 运行图标设置脚本：`scripts/setup/setup_icons.bat`
2. 运行应用：`flutter run`

### 发布新版本
1. 更新版本号：`scripts/version/update_version.bat 1.0.3 4`
2. 构建发布版本：`scripts/build/build_release.bat`
3. 测试 APK
4. 创建 GitHub Release 并上传 APK

---

## 📝 注意事项

- Windows 用户使用 `.bat` 文件
- Linux/Mac 用户使用 `.sh` 文件（需要先添加执行权限：`chmod +x *.sh`）
- 所有脚本都应该从项目根目录运行
