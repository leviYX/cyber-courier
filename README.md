# Cyber Courier

一个融合了真实地理导航与武侠RPG元素的LBS（基于位置服务）游戏。在钢筋水泥的现代都市中，化身“赛博镖师(镖人)”，通过搜索与导航完成各种行脚任务，体验一场“大隐隐于市”的江湖冒险。

## 核心特性

### 游戏化导航体验

- **真实世界即地图**：基于 OpenStreetMap 数据，将你身边的街道、公园和建筑无缝转化为游戏地图。
- **沉浸式行脚**：不再是枯燥的点对点导航。接取“镖局”任务，在真实的徒步或骑行中运送物资，每一步移动都在为江湖传说添砖加瓦。
- **动态路障系统**：导航途中会随机遭遇“泥石流”、“关卡检查”等虚拟障碍，需通过搜索特定关键词或到达指定地点来解锁，让通勤之路充满变数。

### 搜索驱动玩法

- **万物皆可搜**：Elasticsearch 驱动的智能搜索是游戏的核心。搜索“客栈”寻找任务点，搜索“干粮”补充体力，甚至搜索“破障符”来清除路障。
- **语义理解**：支持模糊搜索，输入“能睡觉的地方”也能精准匹配到附近的酒店或青年旅舍，让搜索成为探索世界的钥匙。

### 赛博商城

- **物资补给**：出发前前往商城，购买“高清地图”（解锁详细图层）、“能量饮料”（恢复体力）或“传送符”（付费道具）。
- **品牌植入**：商城支持真实品牌广告植入，让“能量饮料”不仅仅是游戏道具，更是现实商品的优惠券。

### 智能江湖

- **AI NPC 互动**：基于大语言模型（LLM）的 NPC 拥有独立性格与记忆。他们不仅是任务发布者，更是能用“江湖黑话”与你谈笑风生的江湖中人。
- **动态剧情生成**：遭遇突发事件时，AI 会根据当前情境生成独一无二的剧情描述，确保每次游戏体验都截然不同。

## ️ 技术栈

### 前端 (游戏客户端)

- **Phaser 3**：轻量级、高性能的 2D 游戏框架，负责渲染游戏世界与处理用户交互。
- **HTML5 Geolocation API**：获取用户真实 GPS 坐标，驱动游戏角色在虚拟地图上同步移动。
- **Socket.IO Client**：与后端建立 WebSocket 长连接，实现位置同步与实时事件推送。

### 后端 (Go 核心)

- **Go (Golang)**：利用 Goroutine 的高并发特性，处理海量玩家的实时位置同步与游戏逻辑运算。
- **Gin**：高性能 HTTP Web 框架，构建 RESTful API 接口。
- **Gorilla WebSocket**：处理全双工实时通信，如聊天、战斗与事件广播。

### 数据与智能

- **Elasticsearch**：核心搜索引擎，负责 POI 检索、商品搜索及语义匹配。
- **PostgreSQL + PostGIS**：存储用户数据与地理空间信息，利用 PostGIS 进行高效的地理围栏判定。
- **Redis**：高速缓存，用于排行榜、玩家实时状态及分布式锁。
- **Ollama**：本地部署的大语言模型，为 NPC 提供智能对话与动态文案生成能力。
- **ChromaDB**：向量数据库，存储 POI 向量数据以支持模糊搜索。

### 地理基建

- **OpenStreetMap (OSM)**：提供免费的全球矢量地图数据，构建游戏世界的基石。
- **GraphHopper**：强大的路径规划引擎，计算真实世界的导航路线，并将其游戏化。

### 运维

- **Docker & Docker Compose**：一键容器化部署，轻松管理 Go、数据库、搜索引擎等所有服务。
- **Nginx**：反向代理与静态资源服务器，确保前端资源的高效加载。

## 快速开始

### 环境要求

- Go 1.20+
- Node.js 18+
- Docker & Docker Compose

### 1. 克隆项目

```
git clone https://github.com/yourusername/cyber-courier.git
cd cyber-courier
```

### 2. 启动后端服务

```
cd backend
go mod download
go run cmd/main.go
```

### 3. 启动前端开发服务器

```
cd frontend
npm install
npm run dev
```

### 4. 一键部署 (生产环境)

```
cd deploy
docker-compose up -d
```

## 项目结构

```
cyber-courier/
├── backend/                 # Go 后端代码
│   ├── cmd/                 # 入口文件
│   ├── internal/            # 核心业务逻辑 (API, Service, Model)
│   └── pkg/                 # 公共库 (ES, MapEngine, Redis)
├── frontend/                # Phaser 前端代码
│   ├── src/                 # 游戏源码 (Scenes, Entities, UI)
│   └── public/              # 静态资源
├── deploy/                  # Docker 部署配置
└── README.md
```

## 贡献

欢迎提交 Issue 或 Pull Request！让我们一起构建这个独特的赛博江湖。

## 许可证

MIT License

