# 冰箱账本 · 安装说明（给 Claude 看）

用户把这个压缩包上传给你，并说「按 INSTALL-for-Claude.md 帮我安装冰箱账本」。请按顺序执行：

## 1. 发布 App
- 先读完 `fridge-book.html`（这是一个自带的单页 App，数据都存在 Artifact 数据库里，页面里没有任何数据）。
- 用 Artifact 工具把它发布成新的 Artifact，title「冰箱账本」，icon「fridge」，并声明 capabilities：
  ```json
  {"db": {}, "user": {"scopes": ["profile"]}, "sample": {"images": true}}
  ```
  - `db`：库存、购物清单、收据、菜单都存在这里，新发布 = 空数据库
  - `user`：显示是谁加的（家人共用时）
  - `sample`：菜谱推荐、拍照/文字识别入库要调用 Claude
- 不要往数据库写任何示例数据。
- 发布后用 ArtifactData `list` 读一下 `items` 确认是空的、能访问。

## 2. 问用户 3 件事（一次问完）
1. 常去的 Migros 门店，以及所属地区（Migros Zürich / Aare / Luzern / Ostschweiz…）
2. 常去的一家 Coop 门店全名（Coop 每家门店促销册子不同）
3. 要不要装两个自动任务（需要电脑上的 Chrome + Claude in Chrome 扩展，并在 Chrome 里登录 Migros Cumulus 和 Coop Supercard 账户）：
   - 每日自动导入超市收据
   - 每周二、四自动查折扣

## 3. 创建定时任务（scheduled tasks）
- 读 `tasks/task-1-daily-receipt-import.md` 和 `tasks/task-2-weekly-deals.md`。
- 取 `---PROMPT START---` 和 `---PROMPT END---` 之间的文字作为任务 prompt，把 `{{APP_URL}}`、`{{MIGROS_REGION}}`、`{{MIGROS_STORES}}`、`{{COOP_STORE}}` 换成第 1、2 步的结果。
- 用 create_trigger 创建，cron 和名称见各文件开头；`requires_local_device: true`（要用用户电脑上的 Chrome）。
- 用户时区不是 Europe/Zurich 的话，改 cron 里的 CRON_TZ。

## 4. 收尾
- 告诉用户：App 已发布（卡片里有链接）、建了哪些定时任务、每个任务的审批设置。
- 提醒用户：打开 App 先在「菜谱 Rezepte」页点「改生日」填孩子生日（没孩子可跳过），再按 README.md 里的说明用。
