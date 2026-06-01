# 座位选座系统

一个基于 Firebase 的多人在线实时选座系统，类似飞机选座模式。

## 🎯 功能特点

- ✅ **多人实时同步** - 基于 Firebase 实时数据库
- ✅ **座位锁定机制** - 防止多人同时选择
- ✅ **60秒超时** - 未确认自动释放
- ✅ **日期分页** - 每个日期独立座位数据
- ✅ **管理员模式** - 可修改/释放任何座位
- ✅ **响应式设计** - 支持手机和电脑
- ✅ **GitHub Pages 部署** - 纯静态网页，无需服务器

## 🚀 快速部署到 GitHub Pages

### 方式一：Fork 项目（推荐）

1. **点击右上角 "Fork"** - 将项目复制到你的 GitHub 账户
2. **配置 Firebase**（见下方）
3. **开启 GitHub Pages**
   - 进入 Settings → Pages
   - Source 选择 `main` 分支和 `/ (root)`
   - 点击 Save
4. **访问你的网站** - `https://你的用户名.github.io/seat-selection/`

### 方式二：上传到你的仓库

1. 下载本项目所有文件
2. 上传到你的 GitHub 仓库
3. 配置 Firebase（见下方）
4. 开启 GitHub Pages

## 🔥 配置 Firebase

### 步骤 1：创建 Firebase 项目

1. 访问 [Firebase Console](https://console.firebase.google.com/)
2. 点击「添加项目」
3. 输入项目名称，点击继续
4. 关闭 Google Analytics，点击创建项目
5. 等待项目创建完成

### 步骤 2：添加 Web 应用

1. 在项目概览页面，点击「</>」图标（添加应用）
2. 输入应用名称
3. **复制 Firebase 配置信息**
4. 点击「注册应用」

### 步骤 3：替换配置

打开 `index.html` 文件，找到：

```javascript
// 🔥 请在这里替换为你的 Firebase 配置
const firebaseConfig = {
    apiKey: "YOUR_API_KEY",
    authDomain: "YOUR_AUTH_DOMAIN",
    projectId: "YOUR_PROJECT_ID",
    storageBucket: "YOUR_STORAGE_BUCKET",
    messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
    appId: "YOUR_APP_ID"
};
```

替换为你在步骤 2 复制的配置。

### 步骤 4：启用 Firestore 数据库

1. 在左侧菜单选择「构建」→「Firestore Database」
2. 点击「创建数据库」
3. 选择「测试模式」或「生产模式」
4. 选择最近的位置，点击启用

**测试模式安全规则（可直接使用）：**

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read, write: if true;
    }
  }
}
```

### 步骤 5：启用匿名登录

1. 在左侧菜单选择「构建」→「Authentication」
2. 点击「开始使用」
3. 选择「登录方式」标签
4. 找到「匿名」，点击启用
5. 点击保存

## 📱 使用说明

### 座位状态

| 状态 | 颜色 | 说明 |
|------|------|------|
| 🟥 可选择 | 红色 | 空闲座位，任何人可以选择 |
| 🟨 锁定中 | 橙色 | 座位被锁定，60秒内未确认将自动释放 |
| 🟩 已占用 | 绿色 | 座位已被占用，仅管理员可修改 |

### 基本操作

1. **选择座位** - 点击空闲座位 → 输入姓名 → 确认
2. **切换日期** - 点击顶部日期标签（今天/明天/后天）
3. **管理员模式** - 点击右上角切换

### 管理员功能

- 密码：`19111911`（可在代码中修改）
- 可修改任何已占用的座位
- 可释放任何座位

## ⚙️ 自定义配置

### 修改管理员密码

在 `index.html` 中搜索 `19111911`，替换为新密码。

### 修改座位配置

编辑 `SEAT_CONFIG` 对象，自定义座位布局。

### 修改锁定时间

在 `LOCK_TIMEOUT` 变量中修改（毫秒）。

## 🌐 在线演示

**演示地址**：https://seat-selection-demo.web.app/

## 📂 项目结构

```
seat-selection/
├── index.html      # 主页面（包含所有代码）
├── README.md       # 说明文档
└── LICENSE         # MIT 许可证
```

## 💡 技术栈

- **Firebase** - 后端即服务
  - Firestore - 实时数据库
  - Anonymous Auth - 匿名登录
- **原生 JavaScript** - 无需框架
- **Socket.IO** - 实时同步（通过 Firebase）

## 🔒 安全建议

### 生产环境

1. **修改 Firestore 安全规则：**

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /seats/{date} {
      allow read: if true;
      allow write: if request.auth != null;
    }
  }
}
```

2. **启用 Firebase 身份验证**
   - 使用 Google 登录或邮箱登录
   - 添加用户角色集合

## 📄 许可证

MIT License - 可以自由使用、修改和分发。

## 🙏 致谢

- Firebase - 强大的后端即服务
- Google Fonts - 漂亮的字体

---

**有问题？** 提交 Issue 或 Pull Request！

**喜欢这个项目？** 点个 Star ⭐️
