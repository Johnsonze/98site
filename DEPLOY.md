# 🚀 5分钟部署到 GitHub Pages

## 第一步：Fork 项目

1. 点击本仓库右上角的 **Fork** 按钮
2. 选择你的 GitHub 账户
3. 等待复制完成

## 第二步：配置 Firebase

### 2.1 创建 Firebase 项目
1. 访问 https://console.firebase.google.com/
2. 点击「添加项目」→ 输入名称 → 继续
3. 关闭 Google Analytics → 创建项目

### 2.2 添加 Web 应用
1. 点击「</>」图标添加应用
2. 输入应用名称
3. **复制 Firebase 配置**

### 2.3 替换配置
打开 `index.html`，找到以下代码并替换：

```javascript
// 🔥 请在这里替换为你的 Firebase 配置
const firebaseConfig = {
    apiKey: "你的API_KEY",
    authDomain: "你的AUTH_DOMAIN",
    projectId: "你的PROJECT_ID",
    storageBucket: "你的STORAGE_BUCKET",
    messagingSenderId: "你的MESSAGING_SENDER_ID",
    appId: "你的APP_ID"
};
```

### 2.4 启用 Firestore
1. 左侧菜单 → 构建 → Firestore Database
2. 点击「创建数据库」
3. 选择「测试模式」→ 启用

### 2.5 启用匿名登录
1. 左侧菜单 → 构建 → Authentication
2. 点击「开始使用」
3. 登录方式 → 匿名 → 启用 → 保存

## 第三步：开启 GitHub Pages

1. 进入你的 Fork 仓库
2. 点击 **Settings** → 左侧 **Pages**
3. Source 选择 **Deploy from a branch**
4. Branch 选择 **main** 和 **/ (root)**
5. 点击 **Save**

## 第四步：等待部署

1. 进入 **Actions** 标签
2. 等待 "Deploy to GitHub Pages" 工作流完成
3. 访问 `https://你的用户名.github.io/你的仓库名/`

## ✅ 完成！

现在你可以：
- 多人同时访问同一个网址
- 实时同步座位状态
- 管理座位和用户

## 🔧 修改代码后

修改代码后会自动部署，或者手动：
1. 提交并推送代码
2. 进入 Actions → 等待部署完成

## 📝 注意事项

- **管理员密码**：`19111911`（可在 index.html 中修改）
- Firebase 免费套餐足够个人使用
- 数据保存在 Firestore 数据库中

## 🆘 遇到问题？

1. 检查 Firebase 配置是否正确
2. 确认 Firestore 和 Authentication 已启用
3. 查看 Actions 日志排查错误
