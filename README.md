# url-to-qrcode · 链接/邮件转二维码工具

纯前端、单文件、离线可用的二维码生成与目录管理工具。双击 `url-to-qrcode.html` 即可使用，无需服务器、无外部依赖。

A pure-frontend, single-file, offline QR code generator with a built-in catalog manager. Just open `url-to-qrcode.html` in a browser — no server, no CDN, no dependencies.

## 功能 Features

### 生成器（链接二维码）
- 链接 / 文本转二维码，支持中文与 emoji（UTF-8）
- 可调尺寸、静区边距、前景/背景色、容错级别（L/M/Q/H）
- 无协议链接自动补全 `https://`
- **中心 Logo**：上传图片显示在二维码正中，带 Logo 自动强制 H 级容错保证可扫描
- 点击「生成二维码」按钮才生成（非输入即生成）
- 下载 PNG / SVG，复制图片到剪贴板

### 邮件二维码
- 扫码即用客户本机邮件客户端预填新邮件（`mailto:` URI）
- 必填：收件邮箱、Product Model、Product Name；可选：邮件标题（留空默认 `Product Support Request – [Model] – [Name]`）
- 邮件正文模板预填，客户只需补 Order Number 与问题描述
- 邮件内容支持实时预览与手动编辑（以编辑后内容生成）
- 同样支持中心 Logo / 下载 PNG / SVG / 复制图片

### 目录页
- 下载或复制图片时自动存入目录（localStorage 持久化，键 `qr_catalog_v1`）
- 卡片网格展示缩略图，支持搜索、单条删除、清空
- 每张卡片：下载 PNG/SVG、复制图片、复制链接、删除
- 链接条目显示「标题 / 产品类型 / 内容类型」标记（内容类型为下拉框：操作视频 / 电子说明书 / 社媒 / 其他）
- 邮件条目显示「收件邮箱 / Product Model / Product Name」
- **导出备份**：整份目录打包为 JSON（含 Logo base64）
- **导入备份**：按 ID 去重合并，可跨浏览器/设备迁移
- 存储配额超限（约 5MB）时给出明确警告，不再静默失败

### 其他
- 所有页面禁用右键另存二维码图片
- 二维码存储的是「生成参数 JSON」而非位图，占用极小

## 技术说明

- 基于 [qrcode-generator](https://github.com/kazuhikoarase/qrcode-generator)（Kazuhiko Arase），库内嵌于单文件
- 存储：浏览器 `localStorage`（纯本地，无云端）
- 剪贴板 API 需要 `http(s)` 或受支持的浏览器环境；直接双击以 `file://` 打开时生成/下载/存储均可用

## 使用 Usage

直接用浏览器打开 `url-to-qrcode.html` 即可。
