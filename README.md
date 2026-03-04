# RustChain v2 API 文档

本仓库包含 RustChain v2 节点的完整 OpenAPI 3.0.3 规范。

## 📋 概览

- **API 版本**: 2.1.0-rip8
- **端点数量**: 73 个
- **规范格式**: OpenAPI 3.0.3 (JSON)

## 🎯 功能分类

| 分类 | 端点 | 说明 |
|------|------|------|
| Epoch | `/epoch`, `/epoch/enroll` | Epoch 和 slot 管理 |
| Withdraw | `/withdraw/*` | RTC 提现操作 |
| Attest | `/attest/*` | 硬件证明 |
| API | `/api/*` | 通用 API 端点 |
| Admin | `/admin/*` | 管理操作 |
| Gov | `/gov/*` | 治理操作 |
| Miner | `/miner/*`, `/api/miner/*` | 矿工操作 |
| Hall of Fame | `/hall-of-fame/*` | 名人堂页面 |
| Museum | `/museum/*` | 硬件博物馆 |
| Health | `/health`, `/ready` | 健康检查 |
| Metrics | `/metrics*` | Prometheus 指标 |
| Explorer | `/explorer`, `/openapi.json` | 区块链浏览器 |

## 📄 文件

- [`openapi-full.json`](./openapi-full.json) - 完整的 OpenAPI 3.0.3 规范

## 🔍 使用方式

### 1. 直接在节点访问

启动节点后，访问：
```
http://localhost:8099/openapi.json
```

### 2. 使用 Swagger UI

可以使用 Swagger UI 在线查看：
```bash
# 使用 Docker 运行 Swagger UI
docker run -p 8080:8080 -e SWAGGER_JSON=/api/openapi-full.json \
  -v $(pwd):/api swaggerapi/swagger-ui
```

然后访问：http://localhost:8080

### 3. 使用 Postman

导入 `openapi-full.json` 到 Postman 自动生成 Collection。

### 4. 使用 VS Code

安装 [OpenAPI (Swagger) Editor](https://marketplace.visualstudio.com/items?itemName=42Crunch.vscode-openapi) 插件，
直接打开 `openapi-full.json` 查看和编辑。

## 🛠️ 生成工具

OpenAPI 规范通过 [`generate_openapi.py`](../generate_openapi.py) 自动生成：

```bash
python3 generate_openapi.py
```

该脚本会：
1. 扫描节点代码中的所有 `@app.route` 装饰器
2. 提取路径和 HTTP 方法
3. 生成标准化的 OpenAPI 3.0.3 规范
4. 输出到 `rustchain-api-docs/openapi-full.json`

## 📊 端点统计

```
总计：73 个唯一端点

按方法分类:
- GET:    45 个
- POST:   25 个
- PUT:     2 个
- DELETE:  1 个

按标签分类:
- api:              15 个
- admin:            10 个
- withdraw:          8 个
- gov:               6 个
- attest:            4 个
- epoch:             4 个
- miner:             4 个
- hall-of-fame:      3 个
- museum:            3 个
- health:            3 个
- metrics:           2 个
- explorer:          2 个
- general:           9 个
```

## 🔗 相关资源

- [RustChain 主仓库](https://github.com/Scottcjn/Rustchain)
- [RustChain Bounties](https://github.com/Scottcjn/rustchain-bounties)
- [OpenAPI 规范](https://swagger.io/specification/)

## 📝 更新日志

### 2026-03-04
- ✅ 初始版本：73 个端点完整覆盖
- ✅ 包含所有核心功能：Epoch、Withdraw、Attest、Governance 等
- ✅ 添加 Swagger UI 支持说明

---

**Bounty Issue**: [#502 OpenAPI/Swagger documentation](https://github.com/Scottcjn/rustchain-bounties/issues/502)

**钱包地址**: `joshualover-dev`
