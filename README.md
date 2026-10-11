# routing-rules-anywhere

> Anywhere 专用路由规则模板库。  
> 当前仅维护 **Meta 系列**，仓库已设为 **Public**，用于 Anywhere 直接订阅。

## 当前规则

| 规则 | 文件 | 用途 |
|---|---|---|
| Meta Fixed | `anywhere/Meta-Fixed.arrs` | Facebook / Instagram / Threads / Messenger / WhatsApp / Meta AI / Llama / Quest / Oculus |

---

## 直接订阅

Anywhere 可以直接订阅当前规则文件：

```text
https://raw.githubusercontent.com/woohong666/routing-rules-anywhere/main/anywhere/Meta-Fixed.arrs
```

在 Anywhere 中：

```text
Routing
→ Add / Subscribe
→ 粘贴上面的 .arrs URL
→ 创建 Subscription
→ 给 Meta Fixed 绑定你的 Meta 专用 Proxy / Chain
```

以后规则更新后，只需要在 Anywhere 中刷新 Subscription，不需要重新下载和导入本地文件。

---

## 订阅模式说明

Anywhere 订阅的是一个通过 HTTP/HTTPS 提供的 `.arrs` 文件。

当前结构：

```text
GitHub Public Repository
        ↓
raw.githubusercontent.com
        ↓
Meta-Fixed.arrs
        ↓
Anywhere Subscription
```

规则文件只负责定义“哪些目标属于 Meta”。

具体走哪个节点、代理或 Chain，不写在 `.arrs` 里，需要在 Anywhere 的 **Routing** 页面中绑定。

例如：

```text
Meta Fixed
→ USA-VZ / 你的 Meta 专用出口
```

订阅刷新时：

```text
远端规则内容：更新
本地规则名称：保留
本地 Proxy / Chain 绑定：保留
```

---

## Meta-Fixed.arrs

规则文件位置：

```text
anywhere/Meta-Fixed.arrs
```

当前主要覆盖：

```text
Meta
Facebook
Instagram
Threads
Messenger
WhatsApp
Meta AI / Llama
Quest / Oculus
```

规则示例：

```text
name = Meta Fixed

2, meta.com
2, facebook.com
2, instagram.com
2, threads.com
2, whatsapp.com
2, messenger.com
```

其中：

```text
2, example.com
```

表示 **Domain Suffix**。

会匹配：

```text
example.com
www.example.com
api.example.com
a.b.example.com
```

不会匹配：

```text
myexample.com
```

---

## 图标

`Meta-Fixed.arrs` 已内嵌规则集图标。

Anywhere 的 `.arrs` 支持：

```text
icon-light = <Base64 image>
icon-dark  = <Base64 image>
```

一个有效图标即可使用；如果同时提供 light / dark 两个版本，Anywhere 可以根据界面外观选择对应图标。

图标只影响规则集在 Anywhere 中的显示，不影响路由匹配。

---

## Built-in 与 User Rule 冲突

Anywhere 当前规则优先级：

```text
ADBlock
→ Built-in
→ User
→ Neutral
→ Country Bypass
```

如果 Anywhere 内置的 Facebook、Instagram、WhatsApp 等 Built-in 规则已经被绑定为明确动作，它们可能优先于订阅的 `Meta Fixed`。

如果希望 `Meta Fixed` 统一接管 Meta 流量，检查相关 Built-in 项，必要时设置为：

```text
Default
```

然后使用：

```text
Meta Fixed
→ 你的 Meta 专用出口
```

---

## 更新流程

以后只维护 GitHub 中这一份源文件：

```text
anywhere/Meta-Fixed.arrs
```

流程：

```text
发现新域名 / 失效域名
        ↓
核验
        ↓
修改 Meta-Fixed.arrs
        ↓
Commit 到 main
        ↓
Anywhere 刷新 Subscription
        ↓
新规则生效
```

不需要再维护第二份公开镜像，也不需要重复本地导入。

---

## 安全原则

本仓库现在是 **Public**，因此只允许提交非敏感规则和文档。

禁止提交：

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
带凭据的完整客户端配置
```

允许提交：

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
v1.0.2
```

## Scope

本仓库只维护 **Anywhere** 路由规则。

NekoBox 规则单独维护，不与本仓库混合。
