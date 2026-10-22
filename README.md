# 冰箱账本 Fridge Book

一个家庭共用的冰箱库存（Vorrat）+ 购物清单（Einkaufsliste）+ 菜谱（Rezepte）小 App，跑在你自己的 Claude 里。数据只存在你自己的 App 里，分享包里没有任何别人的数据。

## 一、安装（5 分钟）

**需要：** Claude 付费账户（Pro / Max）。想用自动导入收据和查折扣，还需要电脑上的 Chrome + [Claude in Chrome](https://claude.com/chrome) 扩展。

1. 在这个页面点绿色的 **Code → Download ZIP**，下载后解压。
2. 打开 claude.ai（或 Claude App），新建对话，把解压出来的 **全部文件**（包括 `tasks` 文件夹里的两个）拖进去。
3. 发一句：**「按 INSTALL-for-Claude.md 帮我安装冰箱账本」**
4. Claude 会问你 3 个问题：常去的 Migros、常去的 Coop 门店、要不要装自动任务。回答就好。
5. 装好后对话里会出现「冰箱账本」卡片，点开就是 App。建议在侧边栏把它置顶（pin），以后随时打开；手机上也能用。

**想要自动导入收据的话，还要做一次：**
- 在 Chrome 里登录 [Migros 账户](https://account.migros.ch)（Cumulus）和 [Coop Supercard](https://www.supercard.ch)，保持登录。
- Migros App / Coop App 里打开「数字收据 digitaler Kassenzettel」（买东西时刷会员卡才有收据）。
- 每天晚上任务运行时，电脑要开着、Chrome 要开着。登录过期了任务会提醒你重新登录。

## 二、给家人用

在 Claude 里打开 App，用右上角的分享（Teilen）把链接发给家人（家人也需要 Claude 账户）。大家看到的是同一份库存和购物清单，谁加的东西会显示名字。

## 三、怎么用

App 有 5 个页面：

| 页面 | 干什么 |
|---|---|
| **库存 Vorrat** | 冰箱里有什么，按类别显示，快过期的标红/黄。点「✓ 吃完」或「扔掉」出库；不点也行，过了保质期会自动出库。顶部可以一句话记录（「牛奶没了，买了番茄，要买鸡蛋」）；常备品没了点一下就进购物清单。 |
| **打折 Aktionen** | 购物清单 + 「打折就囤」清单（比如咖啡豆只在 6 折时买，写上牌子、折扣条件、哪家店）。每周二、四晚上自动查 Migros / Coop / Denner 的促销，达到条件会标出来；还会根据你常买的东西推荐本周值得买的打折货，不喜欢的点「不要」，以后就不推荐了。 |
| **添加 Einkauf** | 刷了 Cumulus / Supercard 的不用管，每天晚上约 21:00 自动入库。其他地方买的（菜市场、Lidl、亚洲超市）：拍收据上传，或者直接打字「买了 3 个西葫芦、一盒鸡蛋」，Claude 会帮你识别入库。 |
| **菜谱 Rezepte** | 先点「改生日」填孩子生日（没孩子跳过），推荐会按月龄自动调整，宝宝的辅食做法单独写。可以按库存推荐今天做什么，也可以做某一天的菜单计划，缺的食材一键加进购物清单。 |
| **历史 Verlauf** | 最近吃完/扔掉了什么、家人动态、超市购买记录。 |

## 四、小提示

- **常备品 Grundvorrat**（牛奶、鸡蛋、面包这类一直有的）不进库存，在「库存」页顶部点「编辑」设置，没了点一下就进购物清单。
- 第一次用时库存是空的：等第一次自动导入，或者在「添加」页先手动加几样。
- 想改自动任务的时间、换门店：在 Claude 里说「把冰箱账本的查折扣任务改到周三」之类就行。
- 想加新功能：在 Claude 对话里说想要什么，Claude 可以直接改你的 App。

## 五、文件说明

| 文件 | 内容 |
|---|---|
| `fridge-book.html` | App 本体（Claude Artifact，单页，不含任何数据） |
| `INSTALL-for-Claude.md` | 给 Claude 看的安装步骤 |
| `tasks/task-1-daily-receipt-import.md` | 定时任务：每日导入 Migros / Coop 收据 |
| `tasks/task-2-weekly-deals.md` | 定时任务：每周二、四查 Migros / Coop / Denner 折扣 |

> 收据导入用的是 Migros / Coop 网站的内部接口，网站改版后可能失效。只在瑞士超市测试过。
