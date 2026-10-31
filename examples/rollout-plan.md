# 自托管上线顺序 | Self-host rollout plan

审核最慢，所以顺序要倒过来排：

1. 第 1 天：先去 Meta / YouTube / TikTok 等平台提交开发者 app 审核（要数周）。
2. 等审核期间：Docker 部署 Postiz，配 PostgreSQL / Redis / 存储，绑域名上 HTTPS。
3. 用能直连的平台（如 Mastodon / Bluesky）先跑通排期全流程。
4. 审核逐个通过后逐个接入平台，不要等全部到齐才上线。
5. 上线第一周就设好自动备份；更新节奏固定，别攒大版本跳跃升级。
