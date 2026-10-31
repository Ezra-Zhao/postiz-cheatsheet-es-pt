# Postiz 速查表 | Postiz Cheatsheet | Guía rápida de Postiz

> 一页看懂 Postiz：开源、可自托管的社媒排期工具（Buffer/Hootsuite 的免费平替）——一个日历管 14+ 平台的发帖、排期与数据分析，团队协作齐全，还能让 Claude/ChatGPT/Codex 等 agent 通过 MCP/CLI 直接帮你发帖。

- 上游项目：[gitroomhq/postiz-app](https://github.com/gitroomhq/postiz-app)（2026-10-29 实测 40,077 ★ / 7,598 forks，204 个 release）
- 覆盖平台：Instagram、YouTube、TikTok、X、LinkedIn、Facebook、Threads、Reddit、Pinterest、Discord、Slack、Mastodon、Bluesky、Dribbble 等 14+
- 本页结构：中文主文 → English → Español → Português

---

Apoyo y más: [GitHub Sponsors](https://github.com/sponsors/Ezra-Zhao) · [Gumroad — plantillas y cuadernos que uso](https://ezraflow28.gumroad.com) · [Ko-fi](https://ko-fi.com/ezra777zhao)

## 云端版 vs 自托管版（诚实对照）

| 维度 | 云端版（官方托管） | 自托管版（自己部署） |
|---|---|---|
| 价格 | 按档订阅 | 软件免费，只付服务器钱 |
| 渠道/帖数/成员 | 按档设上限 | 无上限 |
| 上手速度 | 注册就能用 | 要自己部署+维护 |
| 平台开发者 app | 官方已配好 | **每个平台要自建开发者 app 并过审** |
| 更新/备份/安全 | 官方负责 | **全是自己的活** |
| 数据 | 在官方云上 | 在自己服务器上，自己说了算 |

一句话：怕折腾用云端版；量大、想省订阅费、数据想自己攥着——自托管。

## 自托管五步卡

1. **部署**：Docker、Coolify、Railway 任选一条路把 Postiz 跑起来（新手优先 Docker Compose，照上游文档的环境变量清单走）。
2. **配齐底座**：PostgreSQL + Redis + 文件存储，三样缺一不可；环境变量逐项填，别漏改默认密钥类字段。
3. **必须 HTTPS**：绑域名+上 HTTPS——各平台 OAuth 回调基本只认 https，没有这一步后面全卡住。
4. **逐个平台建开发者 app**：到 Meta、YouTube、TikTok 等各平台开发者后台自建 app、填回调、提交审核。**这是全流程最耗时的一步，审核要数周**，先并行提交、别等部署完才开始。
5. **接 AI 发帖**：自带 key 接入 AI 功能后，可让 Claude/ChatGPT/Codex 等 agent 经 MCP/CLI 排期发帖——给 agent 的权限范围想清楚再开。

## 成本账（一行版，第三方评测口径，证据 B）

自托管约 **$6/月 VPS** 一台跑全套，对 Buffer 约 $18/月、Hootsuite 约 $99/月（且都按档限量）。账要算全：省下的订阅费 vs 你维护服务器的时间——帖子量小，云端版未必贵；量一大，自托管的边际成本优势立刻出来。

## 诚实标注区

- **最大的坑是平台审核，不是部署本身**：Meta/YouTube/TikTok 的开发者 app 审核要数周且可能被打回，原仓自己也把这点写在明处。排期上线时间时把审核周期算进去。
- **自托管=自己当运维**：版本更新、数据备份、安全补丁、宕机排查都是你的活；没备份习惯的先想清楚再自托管。
- **平台规则会变**：各平台 API 政策与审核口径时有调整，某个平台突然连不上，先查平台侧变更，再怀疑自己的部署。

---

## English (summary)

Postiz (by gitroomhq, ~40k stars and 7,598 forks as of 2026-10-29) is an open-source, self-hostable social-media scheduler — a free alternative to Buffer/Hootsuite. One calendar covers scheduling, analytics and team collaboration across 14+ platforms (Instagram, YouTube, TikTok, X, LinkedIn, Facebook, Threads, Reddit, Pinterest, Discord, Slack, Mastodon, Bluesky, Dribbble), and agents like Claude/ChatGPT/Codex can post through its MCP/CLI.

Cloud vs self-hosted, honestly: the cloud plans cap channels/posts/members per tier but work out of the box; self-hosting is free and unlimited, but you run the server. Self-hosting takes five steps: deploy (Docker/Coolify/Railway), wire up PostgreSQL + Redis + storage, **HTTPS is mandatory** (OAuth callbacks demand it), create and submit a developer app on every platform, then connect AI posting with your own keys. The cost line from third-party reviews: ~$6/month VPS vs Buffer ~$18/month and Hootsuite ~$99/month.

The real bottleneck is not deployment — it is platform review: Meta/YouTube/TikTok developer-app approval takes weeks. And self-hosting means updates, backups and security patches are your job now.

---

## Español (guía rápida — traducción de estudio, pendiente de revisión por un hablante nativo)

Postiz (de gitroomhq, ~40 mil estrellas y 7.598 forks en octubre de 2026) es un programador de redes sociales de código abierto y autoalojable: la alternativa gratuita a Buffer y Hootsuite. Un solo calendario para programar, analizar y colaborar en equipo en más de 14 plataformas (Instagram, YouTube, TikTok, X, LinkedIn, Facebook, Threads, Reddit, Pinterest, Discord, Slack, Mastodon, Bluesky, Dribbble), y los agentes como Claude, ChatGPT o Codex pueden publicar por MCP/CLI.

**Nube o autoalojado, sin humo**:

- **Nube**: pagas por nivel, con límites de canales, publicaciones y miembros; funciona al instante y las apps de desarrollador ya están aprobadas.
- **Autoalojado**: software gratis y sin límites, pero el servidor, las copias de seguridad y las actualizaciones corren por tu cuenta.

**Autoalojar en 5 pasos**: 1) despliega con Docker, Coolify o Railway; 2) configura PostgreSQL, Redis y almacenamiento; 3) **HTTPS obligatorio** (sin él, los inicios de sesión de las plataformas no funcionan); 4) crea tu propia app de desarrollador en cada plataforma y pasa su revisión; 5) conecta la publicación con IA usando tus propias claves.

**La cuenta**: un VPS de ~6 $/mes frente a ~18 $/mes de Buffer y ~99 $/mes de Hootsuite (cifras de reseñas de terceros).

**Notas honestas**: el cuello de botella no es instalar — es la revisión de apps de Meta, YouTube y TikTok, que tarda semanas. Y autoalojar significa ser tu propio equipo de sistemas: actualizaciones, respaldos y parches de seguridad incluidos.

---

## Português (guia rápido — tradução de estudo, aguardando revisão de um falante nativo)

O Postiz (do gitroomhq, ~40 mil estrelas e 7.598 forks em outubro de 2026) é um agendador de redes sociais open source e auto-hospedável: a alternativa gratuita ao Buffer e ao Hootsuite. Um único calendário para agendar, analisar e colaborar em equipe em mais de 14 plataformas (Instagram, YouTube, TikTok, X, LinkedIn, Facebook, Threads, Reddit, Pinterest, Discord, Slack, Mastodon, Bluesky, Dribbble), e agentes como Claude, ChatGPT e Codex podem postar via MCP/CLI.

**Nuvem ou auto-hospedado, sem enrolação**:

- **Nuvem**: você paga por plano, com limites de canais, posts e membros; funciona na hora e os apps de desenvolvedor já estão aprovados.
- **Auto-hospedado**: software grátis e sem limites, mas servidor, backup e atualizações são por sua conta.

**Auto-hospedar em 5 passos**: 1) suba com Docker, Coolify ou Railway; 2) configure PostgreSQL, Redis e armazenamento; 3) **HTTPS obrigatório** (sem ele, os logins das plataformas não funcionam); 4) crie seu próprio app de desenvolvedor em cada plataforma e passe na revisão; 5) conecte a postagem com IA usando suas próprias chaves.

**A conta**: um VPS de ~US$ 6/mês contra ~US$ 18/mês do Buffer e ~US$ 99/mês do Hootsuite (números de reviews de terceiros).

**Notas honestas**: o gargalo não é instalar — é a revisão dos apps da Meta, do YouTube e do TikTok, que leva semanas. E auto-hospedar significa virar seu próprio time de infraestrutura: atualizações, backups e correções de segurança inclusos. Para agências pequenas e criadores solo no Brasil e na América Latina, é justamente aí que a economia aparece.

---

## 来源与声明

- 灵感来源 / Source / Fuente / Fonte: [gitroomhq/postiz-app](https://github.com/gitroomhq/postiz-app)
- 本仓是个人学习整理：内容用我自己的话总结自上游公开文档，不搬运原文；成本数字为第三方评测口径；功能与部署细节以 2026-10-29 的上游 README 与官方文档为准，请以官方文档为最终依据。
- 西语、葡语部分为学习译稿，待母语校对。Las secciones en español y portugués son traducciones de estudio pendientes de revisión nativa.
- License: MIT © 2026 Guangyi Zhao
