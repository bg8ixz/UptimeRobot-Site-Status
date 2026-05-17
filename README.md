简体中文 | [English](./README.en.md)

<div align="center">
<h1>UptimeRobot-Site-Status</h1>
<p>一个基于 UptimeRobot API 的在线状态面板(基于 Nuxt 3 + Vue 3 + TypeScript + SCSS)。</p>
<p>本项目基于 <a href="https://github.com/imsyy/site-status">Site-Status</a> 项目，进行了一些修改和优化。</p>
<br />
<img src="https://img.shields.io/github/last-commit/bg8ixz/UptimeRobot-Site-Status" alt="last commit"/>
<img src="https://img.shields.io/github/languages/code-size/bg8ixz/UptimeRobot-Site-Status" alt="code size"/>
<img src="https://img.shields.io/github/stars/bg8ixz/UptimeRobot-Site-Status?style=full" alt="GitHub stars"/>
<img src="https://img.shields.io/github/forks/bg8ixz/UptimeRobot-Site-Status?style=full&color=orange" alt="GitHub followers"/>
<br />
<br />
<img src="https://s41.ax1x.com/2026/05/16/pevDAW6.png" alt="demo"/>
</div>

## 👀 Demo

> Demo password: `123456`

- [IMSYY-站点监测](https://status.imsyy.top/)

## 🎉 特色

- 🌍 多平台部署支持
- ✨ 优雅且流畅的浏览体验
- 🔐 支持站点密码加密（JWT + Hash）
- 👀 全站状态预览
- ⏲️ 数据定时刷新
- 📱 移动端适配
- 🔗 支持自定义 Github、主页、邮箱链接

## 事先准备

- 您需要先到 [UptimeRobot](https://dashboard.uptimerobot.com/monitors) 添加站点监控，并在 `Integrations & API` 页面或者 [API 管理](https://dashboard.uptimerobot.com/integrations) 页面 `API` 中的 `Main API keys` 创建类型为 `Read-Only API Key` 的 `API Key`，或者使用用于单独监视器的 `Monitor-specific API keys`（ 不要使用 `Main API key` ）。

## 部署

### Cloudflare

本项目默认使用 [Cloudflare Pages](https://pages.cloudflare.com/) 部署，且目前只测试过 `Cloudflare Pages` 部署，其他托管平台请自行测试，可以使用全新的 [NuxtHub](https://hub.nuxt.com/) 来快捷的部署本项目，如果您有在 Vercel 上部署项目的经历，那么过程是大致相同的。

1. `star` 并 `fork` 本项目 😘
2. 使用 [Cloudflare Pages](https://pages.cloudflare.com/) 来部署，进入 `Workers 和 Pages` 创建应用程序。
[![创建应用程序](https://s41.ax1x.com/2026/05/16/pevDtOg.png)]()

3. 开始使用 `Pages` 部署。
[![pevD0kn.png](https://s41.ax1x.com/2026/05/16/pevD0kn.png)]()

4. 导入现有Git存储库。
[![pevDDf0.png](https://s41.ax1x.com/2026/05/16/pevDDf0.png)]()

5. 选择你 `fork` 的项目。

6. 设置项目名称（随意），框架预设选择 `Nuxt.js` ，构建命令填写 `npm run build`，输出目录填写 `dist` ，然后添加环境变量（ 重要 ）。
[![pevD2m4.png](https://s41.ax1x.com/2026/05/16/pevD2m4.png)]()

7. 在点击 `保存并部署` 之前请先配置好环境变量，具体内容请参考 `.env.example` 文件中的内容，其中 `API_KEY` 为必填项。

8. 在设置里面定义 Pages 函数的运行时配置，`兼容性标志` 选择 `nodejs_compat` ，然后`兼容日期`选择 `
Nov 11, 2024` 。
[![pevrJ41.png](https://s41.ax1x.com/2026/05/17/pevrJ41.png)]()

9. 若进展顺利，部署完毕后你就可看到项目主页面了。

### Cloudflare Pages 环境变量

- 在环境变量中添加下方的内容（ 重要 ）

  | **变量名称**             | **值**                  | **说明**                    |
  | ------------------------ | ----------------------- | --------------------------- |
  | DEPLOYMENT_PLATFORM      | auto                   | 部署平台（如：cloudflare）                    |
  | NPM_FLAGS                | --legacy-peer-deps     | 忽略 npm 依赖版本冲突      |
  | NUXT_TELEMETRY_DISABLED  | 1                      | 禁用 Nuxt 遥测数据收集       |
  | NODE_VERSION             | 20                     | Node.js 版本                |
  | API_KEY                  |                        | UptimeRobot API 密钥（必填）  |
  | API_URL                  |https://api.uptimerobot.com/v2/| API 地址                    |
  | COUNT_DAYS               |  60                      | 统计天数 30/60/90                  |
  | SHOW_LINKS               | false                  | 是否显示站点链接             |
  | SHOW_OVERALL_UPTIME      | true                   | 是否显示总体在线率，默认不显示           |
  | SITE_TITLE               |Kee's Server Status| 网站标题                    |
  | SITE_LOGO                |/favicon.ico| 网站 Logo                   |
  | SITE_DESCRIPTION         |一个基于 UptimeRobot 的简约站点监测 | a simple site-status pages, power by uptimerobot.| 网站描述                    |
  | SITE_KEYWORDS            |站点监测,监测,监控| 网站关键词                  |
  | SITE_ICP                 |                        | 网站备案号                  |
  | SITE_SECRE_KEY           |自己生成一个随机字符串即可| 网站加密密钥                |
  | GITHUB_URL               |                        | 可选                       |
  | HOME_URL                 |                        | 可选                       |
  | EMAIL                    |                        | 可选                       |

### 其他托管平台

请参考官方文档：[部署 Nuxt 应用](https://nuxtjs.org.cn/deploy)

## Q & A

### 如何开启站点加密

在环境变量中添加 `SITE_PASSWORD` 和 `SITE_SECRE_KEY`，都必须填写，缺一不可，其中 `SITE_PASSWORD`是站点密码，`SITE_SECRE_KEY` 是加密密钥，可随意填写。

## 鸣谢

- [uptime-status](https://github.com/yb/uptime-status) 受此项目启发

- [site-status](https://github.com/imsyy/site-status) 基于此项目修改
