# 🔥 Firebase 配置

本目录包含 Firebase 安全规则配置文件。

## 📄 文件说明

### firestore.rules
Firestore 数据库安全规则，定义了数据访问权限。

**规则概述**：
- ✅ 用户只能访问自己的数据
- ✅ 每个用户有独立的 notes、vault、keys 子集合
- ✅ 防止未授权访问
- ❌ 禁止删除加密密钥参数（安全考虑）

**数据结构**：
```
users/{uid}/
  ├── notes/{noteId}      - 笔记数据
  ├── vault/{itemId}      - 密码保险库
  └── keys/{keyId}        - 加密密钥参数
```

### storage.rules
Firebase Storage 安全规则，定义了文件存储权限。

**规则概述**：
- ✅ 用户只能访问自己的文件
- ✅ 文件大小限制：10MB
- ✅ 文件路径：`users/{uid}/files/{filename}`
- ❌ 禁止未授权访问

---

## 🚀 部署规则

### 使用 Firebase CLI

1. **安装 Firebase CLI**：
   ```bash
   npm install -g firebase-tools
   ```

2. **登录 Firebase**：
   ```bash
   firebase login
   ```

3. **初始化项目**（如果还没有）：
   ```bash
   firebase init
   ```
   选择：
   - Firestore
   - Storage

4. **部署规则**：
   ```bash
   # 部署所有规则
   firebase deploy --only firestore:rules,storage:rules
   
   # 或单独部署
   firebase deploy --only firestore:rules
   firebase deploy --only storage:rules
   ```

### 使用 Firebase Console

1. 访问 [Firebase Console](https://console.firebase.google.com/)
2. 选择你的项目
3. **Firestore 规则**：
   - 进入 Firestore Database → Rules
   - 复制 `firestore.rules` 的内容
   - 点击"发布"
4. **Storage 规则**：
   - 进入 Storage → Rules
   - 复制 `storage.rules` 的内容
   - 点击"发布"

---

## 🔒 安全注意事项

- ⚠️ **不要**在生产环境使用测试模式规则
- ⚠️ **始终**验证规则是否正确部署
- ⚠️ **定期**审查和更新安全规则
- ✅ 使用 Firebase Emulator 本地测试规则

### 测试规则

```bash
# 启动 Firebase Emulator
firebase emulators:start

# 在另一个终端运行应用
flutter run
```

---

## 📚 相关文档

- [Firestore 安全规则文档](https://firebase.google.com/docs/firestore/security/get-started)
- [Storage 安全规则文档](https://firebase.google.com/docs/storage/security)
- [Firebase CLI 文档](https://firebase.google.com/docs/cli)
