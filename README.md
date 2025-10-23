# smgttma-utils

一个实用的 JavaScript/TypeScript 工具库

## 📦 安装

```bash
npm install smgttma-utils
# 或
pnpm add smgttma-utils
# 或
yarn add smgttma-utils
```

## 🚀 使用方法

### ES Module
```javascript
import { random } from 'smgttma-utils';

const num = random(1, 100); // 生成 1-100 之间的随机整数
```

### CommonJS
```javascript
const { random } = require('smgttma-utils');

const num = random(1, 100);
```

### 浏览器直接引入
```html
<script src="node_modules/smgttma-utils/dist/smgttma-utils.umd.js"></script>
<script>
  const num = smgttmaUtils.random(1, 100);
</script>
```

## 📤 NPM 包发布完整流程

### 1️⃣ **首次发布准备**

#### 检查包名是否可用
```bash
npm search smgttma-utils
```

#### 注册 npm 账号
访问：https://www.npmjs.com/signup

#### 登录 npm
```bash
npm login
# 或
pnpm login
```

输入：
- Username（用户名）
- Password（密码）
- Email（邮箱）
- OTP（如果启用了双因素认证）

#### 验证登录状态
```bash
npm whoami
# 或
pnpm whoami
```

### 2️⃣ **发布前检查清单**

✅ 确保 `package.json` 配置正确：
- `name`: 包名（必须唯一）
- `version`: 版本号
- `main`, `module`, `browser`: 入口文件
- `types`: TypeScript 类型文件
- `files`: 要发布的文件列表

✅ 检查要发布的文件：
```bash
npm pack --dry-run
```
这会列出所有将被发布的文件，但不会实际创建压缩包

### 3️⃣ **发布包**

#### 首次发布
```bash
npm publish
# 或
pnpm publish
```

#### 如果包名带有作用域（如 @username/package）
```bash
npm publish --access public
```

### 4️⃣ **版本管理**

#### 更新版本号
```bash
# 补丁版本 (1.0.0 -> 1.0.1) - 用于 bug 修复
npm version patch

# 次版本 (1.0.0 -> 1.1.0) - 用于新功能
npm version minor

# 主版本 (1.0.0 -> 2.0.0) - 用于破坏性变更
npm version major
```

#### 发布新版本
```bash
# 1. 更新版本号
npm version patch

# 2. 构建代码
pnpm build

# 3. 发布
npm publish
```

### 5️⃣ **其他常用命令**

#### 查看包信息
```bash
npm view smgttma-utils
```

#### 查看所有已发布的版本
```bash
npm view smgttma-utils versions
```

#### 废弃某个版本
```bash
npm deprecate smgttma-utils@1.0.0 "这个版本已废弃，请使用最新版本"
```

#### 撤销发布（仅限发布后 72 小时内）
```bash
npm unpublish smgttma-utils@1.0.0
```

⚠️ **注意：** 不建议使用 `unpublish`，会影响依赖该包的用户

#### 查看本地 npm 配置
```bash
npm config list
```

#### 切换回默认 npm 源
```bash
npm config set registry https://registry.npmjs.org/
```

## 📝 发布注意事项

1. **首次发布前**：确保包名在 npmjs.org 上未被占用
2. **版本号规则**：遵循语义化版本（Semantic Versioning）
3. **测试通过**：发布前确保所有测试通过
4. **构建产物**：确保 `dist` 目录存在且包含最新构建
5. **敏感信息**：不要在代码中包含密钥、token 等敏感信息
6. **文件控制**：使用 `files` 字段或 `.npmignore` 控制发布的文件
7. **README 文档**：确保 README 包含清晰的使用说明
8. **.gitignore**：确保 `node_modules` 和 `dist` 在 `.gitignore` 中

---

## 🔒 使用 Access Token（推荐）

相比密码登录，使用 Token 更安全：

1. 访问：https://www.npmjs.com/settings/YOUR_USERNAME/tokens
2. 点击 "Generate New Token"
3. 选择 "Automation" 或 "Publish" 类型
4. 复制生成的 Token
5. 在项目或用户目录的 `.npmrc` 文件中添加：

```ini
//registry.npmjs.org/:_authToken=YOUR_TOKEN_HERE
```

---

