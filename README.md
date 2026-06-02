# AnsibleOps Platform

> **基于 Ansible 的自动化运维平台设计与实现**
## 📋 项目简介
> 本项目是一个自动化运维平台，通过 Django 构建 Web 界面，结合 MySQL 和 Docker 容器技术，实现了虚拟化环境中服务器的主机管理、批量部署、邮件报警及性能监视等功能。
> 
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


### 安装步骤

1.  **克隆项目**
    ```bash
    git clone https://github.com/yourusername/ansible-ops-platform.git
    cd ansible-ops-platform
    ```

2.  **安装依赖**
    ```bash
    pip install -r requirements.txt
    ```

3.  **创建数据库**
    登录 MySQL 并创建名为 `fms` 的数据库。

4.  **修改数据库配置**
    编辑 `fms/settings.py` 文件：
    ```python
    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.mysql',
            'NAME': 'fms',
            'USER': 'root',
            'PASSWORD': 'your_password',
            'HOST': '127.0.0.1',
            'PORT': '3306',
        }
    }
    ```

5.  **初始化数据库**
    ```bash
    python manage.py makemigrations
    python manage.py migrate
    ```

6.  **创建超级管理员**
    ```bash
    python manage.py createsuperuser
    ```

7.  **启动开发服务器**
    ```bash
    python manage.py runserver
    ```
    访问 [http://127.0.0.1:8000](http://127.0.0.1:8000)

### Docker 容器创建（模拟服务器）

批量创建 Docker 容器：
```bash
docker run -itv /path/to/host_1:/home/host_1 --name=host_1 <image_id> bash
docker run -itv /path/to/host_2:/home/host_2 --name=host_2 <image_id> bash
docker run -itv /path/to/host_3:/home/host_3 --name=host_3 <image_id> bash
docker run -itv /path/to/host_4:/home/host_4 --name=host_4 <image_id> bash
docker run -itv /path/to/host_5:/home/host_5 --name=host_5 <image_id> bash
```
<img width="363" height="154" alt="image" src="https://github.com/user-attachments/assets/daa2d71b-cbfd-4b3b-a0d8-b588bab590a6" />
<img width="377" height="144" alt="image" src="https://github.com/user-attachments/assets/ea8e51e5-4653-457a-a2a4-5b21f3bdc6a1" />
<img width="415" height="152" alt="image" src="https://github.com/user-attachments/assets/9e9a2417-71cc-4c73-a97b-6cab9322f28f" />
<img width="340" height="239" alt="image" src="https://github.com/user-attachments/assets/026659c1-fa5e-4bdf-a72b-bf8d23bf1f29" />
<img width="377" height="159" alt="image" src="https://github.com/user-attachments/assets/01815e83-9d5a-47f1-a94b-20fe65e8e277" />
<img width="381" height="188" alt="image" src="https://github.com/user-attachments/assets/17e19b7a-15d9-4116-a4ce-1d14f4df1e63" />
<img width="303" height="175" alt="image" src="https://github.com/user-attachments/assets/11e86a7d-17a6-4ac9-8c80-fbb1ebfef91a" />
<img width="325" height="196" alt="image" src="https://github.com/user-attachments/assets/8e749050-24cd-4ec7-90a7-c9deb94dcf16" />
<img width="416" height="105" alt="image" src="https://github.com/user-attachments/assets/c3229378-672d-4ff0-97ed-1faecef9875c" />
<img width="415" height="237" alt="image" src="https://github.com/user-attachments/assets/3370bd30-8a86-4b61-bee1-2d41169faffb" />











