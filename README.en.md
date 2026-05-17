English | [简体中文](./README.md)

<div align="center">
<h1>UptimeRobot-Site-Status</h1>
<p>An online status panel based on UptimeRobot API (Built with Nuxt 3 + Vue 3 + TypeScript + SCSS).</p>
<p>This project is based on <a href="https://github.com/imsyy/site-status">Site-Status</a> with some modifications and optimizations.</p>
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

- [IMSYY-Site Monitoring](https://status.imsyy.top/)

## 🎉 Features

- 🌍 Multi-platform deployment support
- ✨ Elegant and smooth browsing experience
- 🔐 Supports site password encryption (JWT + Hash)
- 👀 Overall site status preview
- ⏲️ Data auto-refresh
- 📱 Mobile-friendly design
- 🔗 Supports custom Github, homepage, and email links

## Prerequisites

- You need to first add site monitors on [UptimeRobot](https://dashboard.uptimerobot.com/monitors) and create a `Read-Only API Key` from the `Integrations & API` page or the `API` section in [API Management](https://dashboard.uptimerobot.com/integrations) under `Main API keys`. You can also use `Monitor-specific API keys` for individual monitors (Do not use the `Main API key`).

## Deployment

### Cloudflare

This project is deployed by default using [Cloudflare Pages](https://pages.cloudflare.com/). Currently only `Cloudflare Pages` deployment has been tested. Other hosting platforms can be tested by yourself. You can use the new [NuxtHub](https://hub.nuxt.com/) to quickly deploy this project. If you have experience deploying on Vercel, the process is quite similar.

1. `star` and `fork` this project 😘
2. Deploy using [Cloudflare Pages](https://pages.cloudflare.com/). Go to `Workers and Pages` to create an application.
[![创建应用程序](https://s41.ax1x.com/2026/05/16/pevDtOg.png)]()

3. Start deploying with `Pages`.
[![pevD0kn.png](https://s41.ax1x.com/2026/05/16/pevD0kn.png)]()

4. Import existing Git repository.
[![pevDDf0.png](https://s41.ax1x.com/2026/05/16/pevDDf0.png)]()

5. Select your `forked` project.

6. Set the project name (any name), select `Nuxt.js` as the framework preset, fill in `npm run build` for the build command, fill in `dist` for the output directory, and then add environment variables (Important).
[![pevD2m4.png](https://s41.ax1x.com/2026/05/16/pevD2m4.png)]()

7. Before clicking `Save and Deploy`, please configure the environment variables. For specific content, please refer to the `.env.example` file. The `API_KEY` is a required field.

8. In Settings, define the runtime configuration for Pages Functions. Select `nodejs_compat` for `Compatibility Flag`, and select `Nov 11, 2024` for `Compatibility Date`.
[![pevrJ41.png](https://s41.ax1x.com/2026/05/17/pevrJ41.png)]()

9. If everything goes smoothly, you should be able to see the project's main page after deployment.

### Cloudflare Pages Environment Variables

- Add the following content to environment variables (Important)

  | **Variable Name**           | **Value**                               | **Description**                                  |
  | ---------------------------- | --------------------------------------- | ------------------------------------------------ |
  | DEPLOYMENT_PLATFORM          | auto                                    | Deployment platform (e.g., cloudflare)           |
  | NPM_FLAGS                    | --legacy-peer-deps                      | Ignore npm dependency version conflicts          |
  | NUXT_TELEMETRY_DISABLED      | 1                                       | Disable Nuxt telemetry data collection           |
  | NODE_VERSION                | 20                                      | Node.js version                                  |
  | API_KEY                     |                                         | UptimeRobot API Key (Required)                   |
  | API_URL                     | https://api.uptimerobot.com/v2/         | API URL                                          |
  | COUNT_DAYS                  | 60                                      | Statistics days (30/60/90)                       |
  | SHOW_LINKS                  | false                                   | Show site links                                  |
  | SHOW_OVERALL_UPTIME         | true                                    | Show overall uptime, hidden by default           |
  | SITE_TITLE                  | Kee's Server Status                     | Site title                                       |
  | SITE_LOGO                   | /favicon.ico                            | Site logo                                        |
  | SITE_DESCRIPTION            | A simple site-status page, powered by UptimeRobot | Site description                         |
  | SITE_KEYWORDS               | site monitor, monitoring, uptime        | Site keywords                                    |
  | SITE_ICP                    |                                         | Site ICP filing number                           |
  | SITE_SECRE_KEY              | Generate a random string yourself        | Site encryption key                              |
  | GITHUB_URL                  |                                         | Optional                                         |
  | HOME_URL                    |                                         | Optional                                         |
  | EMAIL                       |                                         | Optional                                         |

### Other Hosting Platforms

For deployment guides, refer to the official documentation: [Deploy Nuxt Apps](https://nuxtjs.org.cn/deploy)

## Q & A

### How to Enable Site Encryption

Add `SITE_PASSWORD` and `SITE_SECRE_KEY` to environment variables. Both are required. `SITE_PASSWORD` is the site password, and `SITE_SECRE_KEY` is the encryption key, which you can fill in freely.

## Thanks

- [uptime-status](https://github.com/yb/uptime-status) inspired this project

- [site-status](https://github.com/imsyy/site-status) based on this project modified
