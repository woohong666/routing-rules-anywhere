# routing-rules-anywhere

> Anywhere 专用路由规则模板库。  
> 当前仅维护 **Meta 系列**，仓库保持 Private，用作长期版本源。

## 当前规则

| 规则 | 文件 | 用途 |
|---|---|---|
| Meta Fixed | `anywhere/Meta-Fixed.arrs` | Facebook / Instagram / Threads / Messenger / WhatsApp / Meta AI / Llama / Quest / Oculus |

---

## 推荐用法：Subscription 订阅模式

Anywhere 官方支持直接订阅一个 `.arrs` URL。订阅后，远端规则更新时可以在 Anywhere 内刷新，不需要每次重新导入文件。

订阅文件必须满足：

```text
HTTP/HTTPS URL
URL 路径以 .arrs 结尾
服务器返回 HTTP 2xx
文件内容为 UTF-8
```

### 订阅地址格式

公开可访问时，地址形式类似：

```text
https://raw.githubusercontent.com/<GitHub用户名>/<仓库名>/main/anywhere/Meta-Fixed.arrs
```

本仓库对应的路径是：

```text
woohong666/routing-rules-anywhere
└── anywhere/Meta-Fixed.arrs
```

### 重要：当前仓库是 Private

**Private GitHub Repository 的 raw 文件不能被 Anywhere 匿名直接订阅。**

因此当前不要把下面这个地址直接填进 Anywhere：

```text
https://raw.githubusercontent.com/woohong666/routing-rules-anywhere/main/anywhere/Meta-Fixed.arrs
```

在仓库保持 Private 的前提下，如果要使用 Subscription 模式，建议采用：

```text
Private Repository
        ↓
作为源文件 / 版本历史
        ↓
公开只读的 .arrs 镜像
        ↓
Anywhere Subscription
```

推荐的公开只读镜像可以是：

```text
GitHub Secret Gist / Public Gist
或
单独的公开 rules 仓库
```

规则文件本身不包含节点密码、订阅链接、UUID、API Key 等秘密，因此可以只把 `.arrs` 规则文件作为公开镜像；源码管理与历史仍保留在这个 Private Repository。

---

## Anywhere 中的订阅设置

当获得一个可公开访问的 `.arrs` URL 后：

```text
Anywhere
→ Routing
→ Add / Subscribe
→ 填入 .arrs URL
→ 创建订阅
→ 将规则集绑定到需要的 Proxy / Chain
```

Meta 模板的目标逻辑：

```text
Meta Fixed
→ 绑定你的 Meta 专用出口
```

注意：

```text
.arrs 文件只负责“匹配哪些域名”
具体走哪个代理 / Chain，需要在 Anywhere 的 Routing 界面里绑定
```

订阅刷新时：

```text
远端规则：整体替换
本地规则名称：保留
本地绑定的代理 / Chain：保留
routing 头：刷新时不会覆盖你本地选择的动作
```

---

## Meta-Fixed.arrs

当前模板内容可直接复制：

```text
name = Meta Fixed

# Meta / Facebook
2, meta.com
2, meta.ai
2, atmeta.com
2, llama.com
2, metaaivm.com
2, muse.ai
2, facebook.com
2, facebook.net
2, fb.com
2, fb.me
2, fbcdn.com
2, fbcdn.net
2, fbsbx.com
2, fbsbx.net
2, tfbnw.net

# Instagram
2, instagram.com
2, cdninstagram.com
2, instagr.am
2, ig.me
2, igcdn.com

# Threads
2, threads.com
2, threads.net

# Messenger
2, messenger.com
2, fbmessenger.com
2, m.me

# WhatsApp
2, whatsapp.com
2, whatsapp.net
2, whatsapp.biz
2, wa.me

# Quest / Oculus
2, oculus.com
2, oculuscdn.com
2, ocul.us
```

Anywhere 规则类型：

```text
2, example.com
```

表示 **Domain Suffix**，会匹配：

```text
example.com
www.example.com
api.example.com
a.b.example.com
```

但不会误匹配：

```text
myexample.com
```

---

## Built-in 与 User Rule 冲突

Anywhere 当前匹配层级：

```text
ADBlock
→ Built-in
→ User
→ Neutral
→ Country Bypass
```

所以如果 Anywhere 内置的 Facebook / Instagram / WhatsApp 规则已经绑定了一个明确的代理，它可能优先于订阅进来的 `Meta Fixed`。

当你希望 `Meta Fixed` 接管 Meta 流量时，应检查冲突的 Built-in 服务组，必要时将其设置为：

```text
Default
```

然后由：

```text
Meta Fixed
→ 指定 Meta 专用出口
```

负责实际分流。

---

## 更新流程

以后修改 Meta 规则，只维护这一份源文件：

```text
anywhere/Meta-Fixed.arrs
```

建议流程：

```text
发现新域名 / 失效域名
        ↓
核验用途
        ↓
修改 Meta-Fixed.arrs
        ↓
更新 CHANGELOG.md
        ↓
Commit
        ↓
同步公开订阅镜像
        ↓
Anywhere 刷新 Subscription
```

不要为了“看起来更全”无限增加域名。优先保留能够明确归属 Meta 服务的根域和关键基础设施。

---

## 安全原则

仓库即使是 Private，也不要提交：

```text
代理订阅 URL
节点密码
UUID
Private Key
证书
API Key
Cookie
Session Token
账号密码
带凭据的完整客户端导出配置
```

本仓库只保存：

```text
.arrs 路由模板
域名规则
说明文档
版本记录
非敏感示例
```

详细说明见：

```text
docs/SECURITY.md
```

---

## 版本

当前版本：

```text
v1.0.1
```

变更记录：

```text
CHANGELOG.md
```

## Scope

这个仓库只维护 **Anywhere**。

NekoBox 规则以后单独维护，不与本仓库混合。
