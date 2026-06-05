# kylin Home Assistant Add-ons

这是一个个性化的 Home Assistant Add-ons 仓库，基于官方 [home-assistant/addons](https://github.com/home-assistant/addons) 仓库进行定制化和扩展。

Add-ons for Home Assistant allow you to extend the functionality
around your Home Assistant setup. These add-ons can consist of an application
that Home Assistant can integrate with or allow access to your Home Assistant configuration.

Add-ons can be installed and configured via the Home Assistant frontend on
systems that have installed Home Assistant.

## Add-ons provided by this repository

### 🔧 当前提供的插件

- **[Let's Encrypt](/letsencrypt/README.md)**

    管理 Let's Encrypt 证书，支持多种 DNS 验证方式，**特别增加了阿里云 DNS 支持**。

### ✨ 特色功能

#### Let's Encrypt 插件增强

本仓库的 Let's Encrypt 插件基于上游最新版本 (v6.3.2)，并进行了以下增强：

- ✅ **阿里云 DNS 验证支持** (`dns-aliyun`)
  - 支持通过阿里云 DNS API 自动完成 DNS-01 挑战
  - 适用于域名在阿里云解析的用户
  - 支持通配符证书申请
  
- ✅ **完整的多架构支持**
  - aarch64, amd64
  
- ✅ **丰富的 DNS 提供商支持**（继承自上游）
  - 50+ DNS 服务商：Cloudflare, AWS Route53, DuckDNS, Cloudns 等
  - 支持 HTTP 和 DNS 两种验证方式
  - 基于 certbot-dns-multi (lego) 实现

## 📖 使用指南

### 添加本仓库到 Home Assistant

1. 打开 Home Assistant
2. 进入 **设置** → **插件** → **右上角三点菜单** → **仓库**
3. 添加仓库 URL：`https://github.com/kylin7226/addons`
4. 刷新后即可查看并安装插件

### 配置 Let's Encrypt（阿里云 DNS 示例）

```yaml
domains:
  - example.com
  - "*.example.com"
email: your-email@example.com
challenge: dns
dns:
  provider: dns-aliyun
  aliyun_access_key: LTAI5t...
  aliyun_access_key_secret: your-secret-key
  propagation_seconds: 60  # 可选，默认 60 秒
```

### 阿里云 RAM 权限配置

使用阿里云 DNS 验证需要：
1. 创建 RAM 子用户
2. 授予 `AliyunDNSFullAccess` 权限
3. 创建 AccessKey 并记录
4. 在插件配置中填写 AccessKey ID 和 Secret

## 🔄 与上游的关系

本仓库基于 [home-assistant/addons](https://github.com/home-assistant/addons) 进行定制：
- 定期同步上游 letsencrypt 插件的最新更新
- 保留自定义的阿里云 DNS 支持
- 遵循上游的代码规范和最佳实践

## 🤝 贡献

欢迎提交 Issue 和 Pull Request！

## 📝 许可证

本项目遵循 MIT 许可证 - 详见 [LICENSE](LICENSE) 文件
