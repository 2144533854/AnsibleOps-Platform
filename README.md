# AnsibleOps-Platform
基于Ansible的自动化运维平台设计与实现
基于Ansible的自动化运维平台设计与实现
📋 项目简介
本项目是一个基于 Ansible 的自动化运维平台，旨在解决云计算环境下大规模服务器集群的自动化部署、配置管理和监控问题。通过将虚拟化技术与自动化技术相融合，构建了一套高效的云数据中心运维解决方案。
项目来源：南京邮电大学通达学院 毕业设计  
作者：郭佳佳
指导教师：冯政军、李鹏  

✨ 主要功能
基础功能
功能模块说明🔐 用户登录支持用户认证与权限管理👥 用户管理创建用户、修改密码、权限分配🔑 权限管理细粒度的用户权限控制
Ansible核心功能
功能模块说明🖥️ 主机管理服务器信息管理、状态监控（开机/关机）📦 批量部署基于Ansible playbook的批量任务执行📧 邮件报警SMTP协议实现服务器异常邮件预警 📊 性能监控CPU、GPU、内存使用实时监控与图表展示 📁 文件传输批量文件分发与任务结果汇总

🛠️ 技术栈
技术用途Python 3.7后端开发语言Django 1.11Web框架（MVT架构） Ansible自动化运维核心工具Docker容器化模拟服务器环境MySQL数据存储PyCharm开发IDEECharts数据可视化图表jieba中文分词（用于红楼梦词频统计演示） 

🏗️ 系统架构
┌─────────────────────────────────────────────┐
│              Web 管理界面                     │
│  (Django MTV架构：Model-View-Template)       │
├─────────────────────────────────────────────┤
│              Ansible 核心引擎                 │
│  ┌──────────┬──────────┬────────────────┐   │
│  │ Playbook │  Modules │  Plugins       │   │
│  └──────────┴──────────┴────────────────┘   │
├─────────────────────────────────────────────┤
│            SSH 连接层（Paramiko）            │
├─────────────────────────────────────────────┤
│    Docker 容器集群（模拟5台服务器）           │
│  host_1  host_2  host_3  host_4  host_5    │
└─────────────────────────────────────────────┘

🚀 快速开始
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

# 3. 配置数据库（修改 fms/settings.py）
# DATABASES = {
#     'default': {
#         'ENGINE': 'django.db.backends.mysql',
#         'NAME': 'fms',
#         'USER': 'root',
#         'PASSWORD': '1234',
#         'HOST': '127.0.0.1',
#         'PORT': '3305',
#     }
# }

# 4. 初始化数据库
python manage.py makemigrations
python manage.py migrate

# 5. 创建超级管理员
python manage.py createsuperuser

# 6. 启动开发服务器
python manage.py runserver
# 访问 http://127.0.0.1:8000

Docker容器创建（模拟服务器）
# 批量创建Docker容器
docker run -itv C:\path\host_1:/home/host_1 --name=host_1 <image_id> bash
docker run -itv C:\path\host_2:/home/host_2 --name=host_2 <image_id> bash
# ... 以此类推创建5个容器

📸 功能演示截图
1. 主机管理界面

展示服务器名称、IP地址、CPU/GPU配置、运行状态
支持添加、编辑、删除服务器
一键开关机控制

2. 批量部署演示
以《红楼梦》人物出场词频统计为例：

将《红楼梦》文本切分为5份
通过Ansible分发到5台Docker容器
每台容器使用jieba库独立进行词频统计
汇总结果并展示TOP单词

统计结果示例（host_1）：

贾宝玉：2316次
王熙凤：1071次
贾母：740次
林黛玉：673次
王夫人：437次

3. 性能监控

CPU使用率（最近10小时平均值）柱状图
最高负载服务器近10小时变化折线图
各主机资源占比饼状图

4. 邮件报警

基于SMTP协议的邮件发送
服务器负载异常自动触发邮件预警

📊 数据库设计
核心数据表
表名说明关键字段accounts_host服务器信息hostname, ip_address, cpu_name, gpu_name, statusaccounts_user用户信息username, email, mobile, is_superuseraccounts_file文件传输记录name, url, start_time, end_time, resultaccounts_listen资源监控cpu_use, gpu_use, men_use

🔧 系统不足与改进方向

安全性优化：增加登录密码错误锁定机制（3次错误锁定账户）
IP校验：添加IP地址格式合法校验
Windows支持：优化Ansible对Windows Server的支持
大规模并发：改进Ansible在大规模集群下的并发处理效率

📚 参考技术文档

Ansible官方文档
Django官方文档
Docker官方文档

📄 许可证
本项目为毕业设计作品，仅供学习交流使用。

关键词：虚拟化、云数据中心、自动化运维、Ansible、Django、Docker
