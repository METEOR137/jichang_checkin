# 通用机场签到脚本部署指南

> **适用条件**：仅适用于网站底部注明 **“Powered by SSPANEL”** 的机场。可以在机场首页的页脚处进行确认。
 例如:
> ![Y0}SY$J`8837H8T5GXM1DZY](https://github.com/METEOR137/jichang_checkin/blob/main/%E7%A4%BA%E4%BE%8B.png)

## 脚本作用

每日自动执行签到任务，为您的账户获取额外的流量奖励。

## 消息推送(可选)

脚本支持通过以下两种推送服务，**二者任选其一即可**。如果不需要推送功能，将对应的密钥参数留空。

| 推送服务 | 文档链接 |
| :--- | :--- |
| **Server酱** | [Server酱官网](https://sct.ftqq.com/) |
| **WxPusher** | [WxPusher官网](https://wxpusher.zjiecode.com) |

> **提示**：根据上方链接的官方文档，分别注册并获取所需的密钥（SCKEY 或 WP_APP_TOKEN、WXPUSHER_UID）。

---

## 详细部署步骤

请按顺序完成以下操作以启用自动签到。

### 步骤一：Fork 项目仓库

点击此项目页面的右上角 **`Fork`** 按钮，将仓库复制到自己的GitHub账户下。

### 步骤二：配置机密(Secrets)

在您Fork后的仓库中，依次进入 `Settings` → `Secrets and variables` → `Actions` 页面。

点击 **`New repository secret`** 按钮，新建以下机密：

| 参数名 | 是否必须 | 说明 |
| :--- | :--- | :--- |
| `CONFIG` | **是** | 机场账号和密码。**格式为：一行账号，一行密码。** 例如：<br>`your-email@example.com`<br>`your-password` |
| `URL` | **是** | 机场网站地址。<br>**⚠️ 重要：地址末尾不要添加 `/` 斜杠。** 例如:`https://airport.example.com` |
| `PUSH_METHOD` | 否 | ** 推送方式:<br>`serverchan`<br>`wxpusher`<br>`both` |
| `SCKEY` | 否 | Server酱推送必须 |
| `WP_APP_TOKEN` | 否 | WxPusher推送必须 |
| `WXPUSHER_UID` | 否 | WxPusher推送必须 |

### 步骤三：手动运行并启用工作流

1.  进入仓库的 **`Actions`** 页面。
2.  在左侧选择签到脚本对应的工作流（例如 `main.yml`）。
3.  点击 **`Run workflow`** 按钮，手动触发一次执行，以启用该工作流。

### 步骤四：查看运行结果

-   此后，脚本将**每天自动运行**。
-   您可以在 `Actions` 页面查看每次运行的详细日志和签到状态。
-   如配置了推送服务，签到详情也会发送到所配置的服务。
