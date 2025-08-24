# gin-template


## project stucture

```Markdown
gin-template
├── api               # 对外暴露的协议层（proto、openapi、graphql schema）
│   ├── proto
│   └── openapi.yaml
├── build             # 构建脚本与 Dockerfile
│   ├── Dockerfile
│   └── ci/
├── cmd               # 可执行程序的 main 包（每个服务一个子目录）
│   ├── api-server
│   │   └── main.go
│   └── job-worker
│       └── main.go
├── configs           # 不同环境的配置模板
│   ├── dev.yaml
│   └── prod.yaml
├── deployments       # K8s/Helm/Compose 部署文件
│   ├── k8s/
│   └── docker-compose.yml
├── docs              # Swagger、API 说明文档
├── internal          # 业务核心私有代码（不允许被外部 import）
│   ├── app
│   │   ├── api-server
│   │   │   ├── handler      # HTTP/gin handler
│   │   │   ├── router       # 路由+中间件注册
│   │   │   └── middleware   # 如 auth、logger、trace、recovery、rate-limit
│   │   └── job-worker
│   ├── biz            # 业务用例/服务编排层（依赖 repo、rpc、cache…）
│   ├── dal            # Data Access Layer
│   │   ├── query      # sqlc/gorm 生成的查询代码
│   │   ├── cache      # redis 封装
│   │   └── mq         # kafka/rabbit 封装
│   ├── service        # 领域服务（聚合根、领域事件）
│   ├── model          # 数据库/缓存/消息模型
│   └── pkg            # 内部公共库（防止循环依赖）
│       ├── errors     # 业务错误码
│       ├── logger
│       └── validator
├── pkg               # 可被外部项目 import 的公共库
│   ├── util
│   ├── snowflake
│   └── xgin          # 对 gin 的二次封装（含通用中间件）
├── scripts           # 本地开发脚本（migrate、mock、codegen）
├── test              # 集成测试、e2e 测试
├── third_party       # 第三方 proto 或工具
├── go.mod
├── go.sum
└── README.md
```