# AnsibleOps Platform (FMS)

> **基于 Ansible 的自动化运维平台设计与实现**
## 📋 项目简介
> 本项目是一个自动化运维平台，通过 Django 构建 Web 界面，结合 MySQL 和 Docker 容器技术，实现了虚拟化环境中服务器的主机管理、批量部署、邮件报警及性能监视等功能。
> 某位学生的毕业设计

## ✨ 主要功能

### 基础功能

| 功能模块 | 说明 |
|---------|------|
| 🔐 用户登录 | 支持用户认证与权限管理 |
| 👥 用户管理 | 创建用户、修改密码、权限分配 |
| 🔑 权限管理 | 细粒度的用户权限控制 |

### Ansible 核心功能

| 功能模块 | 说明 |
|---------|------|
| 🖥️ 主机管理 | 服务器信息管理、状态监控（开机/关机） |
| 📦 批量部署 | 基于 Ansible playbook 的批量任务执行 |
| 📧 邮件报警 | SMTP 协议实现服务器异常邮件预警 |
| 📊 性能监控 | CPU、GPU、内存使用实时监控与图表展示 |
| 📁 文件传输 | 批量文件分发与任务结果汇总 |

## 🛠️ 技术栈

| 技术 | 用途 |
|------|------|
| **Python 3.7** | 后端开发语言 |
| **Django 1.11** | Web 框架（MVT 架构） |
| **Ansible** | 自动化运维核心工具 |
| **Docker** | 容器化模拟服务器环境 |
| **MySQL** | 数据存储 |
| **ECharts** | 数据可视化图表 |
| **jieba** | 中文分词（用于红楼梦词频统计演示） |

## 🏗️ 系统架构

```text
┌─────────────────────────────────────────────┐
│              Web 管理界面                     │
│  (Django MTV 架构：Model-View-Template)       │
├─────────────────────────────────────────────┤
│              Ansible 核心引擎                 │
│  ┌──────────┬──────────┬────────────────┐   │
│  │ Playbook │  Modules │  Plugins       │   │
│  └──────────┴──────────┴────────────────┘   │
├─────────────────────────────────────────────┤
│            SSH 连接层（Paramiko）            │
├─────────────────────────────────────────────┤
│    Docker 容器集群（模拟 5 台服务器）         │
│  host_1  host_2  host_3  host_4  host_5    │
└─────────────────────────────────────────────┘


##🚀 快速开始
环境要求

Python 3.7+
Docker Desktop
MySQL 5.7+

安装步骤
# 1. 克隆项目
git clone https://github.com/yourusername/ansible-ops-platform.git
cd ansible-ops-platform

# 2. 安装依赖
pip install -r requirements.txt

# 3. 创建数据库
# 登录 MySQL 并创建名为 'fms' 的数据库

# 4. 修改数据库配置 (fms/settings.py)
# DATABASES = {
#     'default': {
#         'ENGINE': 'django.db.backends.mysql',
#         'NAME': 'fms',
#         'USER': 'root',
#         'PASSWORD': 'your_password',
#         'HOST': '127.0.0.1',
#         'PORT': '3306',
#     }
# }

# 5. 初始化数据库
python manage.py makemigrations
python manage.py migrate

# 6. 创建超级管理员
python manage.py createsuperuser

# 7. 启动开发服务器
python manage.py runserver
# 访问 http://127.0.0.1:8000

Docker 容器创建（模拟服务器）
# 批量创建 Docker 容器
docker run -itv /path/to/host_1:/home/host_1 --name=host_1 <image_id> bash
docker run -itv /path/to/host_2:/home/host_2 --name=host_2 <image_id> bash
docker run -itv /path/to/host_3:/home/host_3 --name=host_3 <image_id> bash
docker run -itv /path/to/host_4:/home/host_4 --name=host_4 <image_id> bash
docker run -itv /path/to/host_5:/home/host_5 --name=host_5 <image_id> bash

📸 功能演示
主机管理界面
展示服务器名称、IP 地址、CPU/GPU 配置、运行状态（开机/关机），支持添加、编辑、删除服务器。

截图占位：请将截图命名为 screenshot_host.png 并放在 docs/screenshots/ 目录下

批量部署演示（《红楼梦》词频统计）
本功能演示了如何利用 Ansible 进行分布式任务处理。

将《红楼梦》文本切分为 5 份
通过 Ansible 分发到 5 台 Docker 容器
每台容器使用 jieba 库独立进行词频统计
汇总结果并展示 TOP 单词

统计结果示例（host_1）：
人物出现次数贾宝玉2316王熙凤1071贾母740林黛玉673王夫人437
性能监控

CPU 使用率（最近 10 小时平均值）柱状图
最高负载服务器近 10 小时变化折线图
各主机资源占比饼状图

邮件报警

基于 SMTP 协议的邮件发送
服务器负载异常自动触发邮件预警

📊 数据库设计
核心数据表
表名说明关键字段accounts_host服务器信息hostname, ip_address, cpu_name, gpu_name, statusaccounts_user用户信息username, email, mobile, is_superuseraccounts_file文件传输记录name, url, start_time, end_time, resultaccounts_listen资源监控cpu_use, gpu_use, men_use
🧪 系统不足与改进方向

安全性优化：增加登录密码错误锁定机制（3 次错误锁定账户）
IP 校验：添加 IP 地址格式合法校验
Windows 支持：优化 Ansible 对 Windows Server 的支持
大规模并发：改进 Ansible 在大规模集群下的并发处理效率

📚 参考文档

Ansible 官方文档
Django 官方文档
Docker 官方文档

📄 许可证
本项目为毕业设计作品，仅供学习交流使用。

你可以将上述内容复制，并保存为一个名为 `README.md` 的文件，然后直接上传到你的 GitHub 仓库中。
