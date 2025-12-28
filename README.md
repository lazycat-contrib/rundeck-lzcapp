# Rundeck 懒猫应用

Rundeck 是一个开源的自动化运维平台，专为解决IT运维自动化而设计。

## 应用特点

- **作业调度与编排**: 强大的作业管理和工作流编排能力
- **灵活的节点管理**: 支持多种节点源和远程执行
- **细粒度权限控制**: 精确的访问控制和安全管理
- **全面的审计日志**: 详细的操作记录和追踪
- **开箱即用**: 使用内置H2数据库，无需额外配置
- **CSP优化**: 已禁用过于严格的CSP策略，确保登录和使用正常

## 版本信息

- **应用版本**: 5.18.0
- **包名**: cloud.lazycat.app.rundeck
- **最低系统版本**: 1.3.8

## 默认登录信息

- **用户名**: admin
- **密码**: admin
- **⚠️ 重要**: 请在首次登录后立即修改密码

## 数据存储

应用使用以下目录存储数据：

- `/lzcapp/var/rundeck/data` - 数据库和配置文件
- `/lzcapp/var/rundeck/plugins` - 插件目录
- `/lzcapp/var/rundeck/logs` - 应用日志

## 构建和发布

### 前提条件

1. 安装 `lzc-cli` 工具
2. 准备 512x512 PNG 格式的图标文件 `icon.png`
3. 登录懒猫应用商店: `lzc-cli appstore login`

### 使用构建脚本

运行交互式构建脚本：

```bash
./build.sh
```

菜单选项：

1. **构建应用** - 生成 .lpk 安装包
2. **镜像复制** - 复制Docker镜像到懒猫仓库
3. **发布应用** - 发布到应用商店
4. **一键发布** - 自动完成全部流程
5. **查看信息** - 显示应用详细信息
6. **验证配置** - 检查配置文件格式
7. **退出**

### 手动构建步骤

#### 1. 本地测试安装

```bash
# 构建应用包
lzc-cli project build -o rundeck-5.18.0.lpk

# 本地安装测试
lzc-cli app install rundeck-5.18.0.lpk
```

#### 2. 发布到应用商店

```bash
# 步骤1: 复制镜像到懒猫仓库
lzc-cli appstore copy-image rundeck/rundeck:5.18.0

# 步骤2: 更新 lzc-manifest.yml 中的镜像地址
# 将输出的新镜像地址替换到 manifest 文件中

# 步骤3: 重新构建
lzc-cli project build -o rundeck-5.18.0.lpk

# 步骤4: 发布到应用商店
lzc-cli appstore publish rundeck-5.18.0.lpk
```

## 文件说明

- `lzc-manifest.yml` - 应用配置清单
- `lzc-build.yml` - 构建配置文件
- `build.sh` - 自动化构建脚本
- `icon.png` - 应用图标（需自行提供）
- `README.md` - 本说明文档

## 使用 Rundeck

安装成功后，通过懒猫应用的访问地址打开 Rundeck Web 界面。

### 首次使用

1. 使用 admin/admin 登录
2. 修改管理员密码（User Profile → Edit Profile）
3. 创建新项目（Projects → New Project）
4. 添加节点和作业
5. 开始自动化运维

### 主要功能

- **项目管理**: 创建和管理多个项目
- **作业定义**: 定义自动化任务和工作流
- **节点管理**: 管理执行节点
- **调度执行**: 定时或手动触发作业
- **日志查看**: 查看执行历史和日志
- **权限管理**: 配置用户和访问权限

## 注意事项

1. **数据备份**: 定期备份 `/lzcapp/var/rundeck/data` 目录
2. **密码安全**: 首次登录后立即修改默认密码
3. **资源配置**: 建议至少分配 2GB 内存
4. **启动时间**: 首次启动可能需要 1-2 分钟，请耐心等待
5. **安全策略**: 
   - 已禁用CSP(Content Security Policy)以避免登录问题
   - 如需启用CSP，请在环境变量中设置 `RUNDECK_SECURITY_HTTPHEADERS_PROVIDER_CSP_ENABLED=true`
   - 并配置适当的CSP策略: `RUNDECK_SECURITY_HTTPHEADERS_PROVIDER_CSP_CONFIG_POLICY`

## 参考资源

- [Rundeck 官方文档](https://docs.rundeck.com)
- [Rundeck Docker 配置](https://docs.rundeck.com/docs/administration/configuration/docker.html)
- [懒猫云开发者文档](https://developer.lazycat.cloud)

## 许可证

本应用基于 Rundeck 开源项目，遵循 Apache-2.0 许可证。

---

如有问题或建议，欢迎反馈！
