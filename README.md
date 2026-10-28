# IBKR Loon Rules

给 Interactive Brokers / IBKR 手机 App 用的 Loon 远程分流规则。

## 订阅地址

```text
https://raw.githubusercontent.com/cobaltfern/ibkr-loon-rules/main/ibkr.list
```

## Loon 配置示例

把下面这一行放到 Loon 配置的 `[Rule]` 里，最后的策略名按你的配置改成 `PROXY`、`国外节点`、`DIRECT` 等。

```ini
RULE-SET,https://raw.githubusercontent.com/cobaltfern/ibkr-loon-rules/main/ibkr.list,PROXY
```

建议把这条规则放在 `GEOIP,CN,DIRECT`、兜底规则之前。

## 说明

- 覆盖 IBKR App 常见登录、行情、账户、通知和网页鉴权域名。
- 规则只匹配 IBKR/Interactive Brokers 相关主域，不包含 Apple/Google 推送等系统域名。
- 如果登录一直转圈，先确认这条 `RULE-SET` 放在广告拦截、`REJECT`、`GEOIP,CN,DIRECT` 和兜底规则之前。
- 建议不要对 IBKR 开启 MITM、重写、脚本或去广告规则，金融 App 登录很容易被证书检查卡住。
- 如果 App 里某个页面仍然不走预期路线，可以在 Loon 日志里过滤 `ibkr`、`interactivebrokers`、`clientam`，把没命中的域名补到 `ibkr.list`。
