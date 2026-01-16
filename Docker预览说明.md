# 使用 Docker 预览网站

## 📋 前提条件

1. **确保 Docker Desktop 正在运行**
   - 在 Windows 任务栏查看 Docker 图标
   - 如果 Docker Desktop 未运行，请先启动它
   - 等待 Docker Desktop 完全启动（图标不再闪烁）

## 🚀 启动步骤

### 方法 1：使用 Docker Compose（推荐）

在项目根目录下运行：

```powershell
docker compose up
```

**首次运行时会自动构建镜像**，可能需要几分钟时间。

### 方法 2：后台运行

如果您想让 Docker 在后台运行：

```powershell
docker compose up -d
```

### 方法 3：重新构建（如果遇到问题）

如果之前构建过但有问题，可以强制重新构建：

```powershell
docker compose up --build
```

## 🌐 访问网站

启动成功后，在浏览器中访问：

**http://localhost:4000**

## 📝 常用命令

### 查看运行状态
```powershell
docker compose ps
```

### 停止服务
```powershell
docker compose down
```

### 查看日志
```powershell
docker compose logs
```

### 实时查看日志
```powershell
docker compose logs -f
```

### 停止并删除容器
```powershell
docker compose down
```

### 停止并删除容器和镜像
```powershell
docker compose down --rmi local
```

## ⚠️ 注意事项

1. **首次启动较慢**：第一次运行需要下载 Ruby 镜像和安装依赖，可能需要 5-10 分钟
2. **文件修改自动刷新**：修改 Markdown 文件（`.md`）后，网站会自动更新
3. **配置文件修改**：修改 `_config.yml` 后，需要重启容器：
   ```powershell
   docker compose restart
   ```
4. **端口占用**：如果 4000 端口被占用，可以修改 `docker-compose.yaml` 中的端口映射

## 🔧 故障排除

### 问题 1：Docker Desktop 未运行
**错误信息**：`error during connect: ... The system cannot find the file specified`

**解决方法**：
1. 启动 Docker Desktop
2. 等待 Docker Desktop 完全启动（图标不再闪烁）
3. 重新运行 `docker compose up`

### 问题 2：端口被占用
**错误信息**：`port is already allocated`

**解决方法**：
修改 `docker-compose.yaml` 文件，将端口改为其他端口（如 4001）：
```yaml
ports: [ 4001:4000 ]
```
然后访问 `http://localhost:4001`

### 问题 3：权限问题（Windows 通常不会有）
如果遇到权限问题，可以尝试：
```powershell
docker compose up --user 1000:1000
```

### 问题 4：需要重新构建
如果容器有问题，可以删除并重新构建：
```powershell
docker compose down
docker compose up --build
```

## 📌 快速开始命令

```powershell
# 1. 确保 Docker Desktop 正在运行

# 2. 启动服务（首次会自动构建）
docker compose up

# 3. 在浏览器中访问
# http://localhost:4000

# 4. 停止服务（在另一个终端窗口）
docker compose down
```

