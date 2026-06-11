# 🐾 JPetStore

<div align="center">

![MyBatis Logo](https://mybatis.org/images/mybatis-logo.png)

[![Java CI](https://github.com/mybatis/jpetstore-6/actions/workflows/ci.yaml/badge.svg)](https://github.com/mybatis/jpetstore-6/actions/workflows/ci.yaml)
[![Coverage Status](https://coveralls.io/repos/github/mybatis/jpetstore-6/badge.svg?branch=master)](https://coveralls.io/github/mybatis/jpetstore-6?branch=master)
[![License](https://img.shields.io/:license-apache-brightgreen.svg)](https://www.apache.org/licenses/LICENSE-2.0.html)

**一个由团队协作开发的完整宠物商店 Web 应用示例**

*Built with passion and collaboration by our dedicated team*

</div>

---

## 🤝 关于项目

JPetStore 6 是一个功能完整的宠物商店演示应用，由我们的开发团队共同打造，旨在展示现代 Java Web 开发的最佳实践。团队成员在项目中紧密协作，从架构设计到功能实现，每个环节都体现了集体智慧的力量。

本项目采用 **MyBatis 3** 作为持久层框架，**Spring 5** 提供企业级支持，**Stripes** 负责 web 层交互，三者结合展现了 Java 生态系统中优秀框架的协作能力。

---

## ✨ 核心特性

| 模块 | 功能描述 |
|------|----------|
| 🛒 **商品目录** | 支持分类浏览、商品搜索、多条件筛选 |
| 👤 **账户管理** | 用户注册、登录验证、个人资料维护 |
| 🛍️ **购物车** | 商品增删改查、数量调整、实时价格计算 |
| 📦 **订单系统** | 订单创建、状态追踪、历史记录查询 |
| 🔐 **安全机制** | 验证码保护、会话管理、数据校验 |

---

## 🛠️ 技术架构

### 技术栈概览

```
┌─────────────────────────────────────────────────────────────┐
│                        前端层                                │
│              HTML5 + CSS3 + JavaScript (ES6+)               │
├─────────────────────────────────────────────────────────────┤
│                        Web 层                               │
│              Spring MVC + Stripes Framework                 │
├─────────────────────────────────────────────────────────────┤
│                       业务层                                 │
│              Spring 5 + Spring Boot 2.7                     │
├─────────────────────────────────────────────────────────────┤
│                      持久层                                  │
│         MyBatis 3 + MyBatis Plus 3.5                       │
├─────────────────────────────────────────────────────────────┤
│                       数据层                                 │
│                    H2 / MySQL Database                     │
└─────────────────────────────────────────────────────────────┘
```

### 关键技术

- **框架版本**: Java 17, Spring Boot 2.7.18, MyBatis 3
- **数据库**: H2 (开发环境), MySQL (生产环境)
- **构建工具**: Maven 3.x + Maven Wrapper
- **服务器**: Tomcat 9.x / Jetty 9 / 多种应用服务器支持
- **验证码**: Kaptcha 2.3.2
- **模板引擎**: Thymeleaf

---

## 📦 安装指南

### 环境要求

| 依赖项 | 最低版本 | 推荐版本 |
|--------|----------|----------|
| JDK | 11 | 17 |
| Maven | 3.6 | 3.9+ |
| Tomcat | 9.0 | 9.0 |
| MySQL | 8.0 | 8.0 (可选) |

### 构建步骤

```bash
# 1. 克隆项目
git clone https://github.com/mybatis/jpetstore-6.git
cd jpetstore-6

# 2. 使用 Maven Wrapper 构建
./mvnw clean package

# 3. 启动应用 (Tomcat 9)
./mvnw cargo:run -P tomcat90

# 4. 访问应用
open http://localhost:8080/jpetstore/
```

### Docker 部署

```bash
# 构建镜像
docker build . -t jpetstore

# 运行容器
docker run -p 8080:8080 jpetstore

# 或使用 Docker Compose (一键启动)
docker compose up -d
```

---

## 🚀 快速开始

### 首次使用

1. 启动应用程序后，访问 http://localhost:8080/jpetstore/
2. 使用默认账户登录或注册新账户
   - 默认管理员: `admin` / `admin`
   - 测试用户: `j2ee` / `j2ee`
3. 浏览商品目录，将心仪的商品加入购物车
4. 完成订单流程，体验完整购物过程

### 开发模式

```bash
# 启动开发服务器 (热部署)
./mvnw spring-boot:run

# 运行集成测试
./mvnw clean verify -P tomcat90
```

---

## 📂 项目结构

```
jpetstore-6/
├── src/
│   └── main/
│       ├── java/org/mybatis/jpetstore/
│       │   ├── config/          # 配置类
│       │   │   └── MyBatisPlusConfig.java
│       │   ├── domain/         # 实体类
│       │   │   ├── Account.java
│       │   │   ├── Product.java
│       │   │   ├── Order.java
│       │   │   └── ... (更多领域模型)
│       │   ├── mapper/         # MyBatis Mapper 接口
│       │   │   ├── AccountMapper.java
│       │   │   ├── ProductMapper.java
│       │   │   └── ...
│       │   └── service/        # 业务服务层 (视版本)
│       │
│       ├── frontend/           # 前端资源
│       │   ├── pages/          # HTML 页面
│       │   │   ├── catalog/    # 商品目录页面
│       │   │   ├── cart/       # 购物车页面
│       │   │   ├── order/      # 订单页面
│       │   │   └── account/    # 账户页面
│       │   └── src/            # 前端源码
│       │       ├── common/     # 公共组件
│       │       └── modules/    # 功能模块
│       │
│       └── resources/          # 配置文件
│           ├── mapper/         # MyBatis XML 映射文件
│           └── application.properties
│
├── scripts/                    # 辅助脚本
├── pom.xml                     # Maven 配置
├── Dockerfile                  # Docker 构建文件
└── docker-compose.yaml         # Docker Compose 配置
```

---

## 🔧 Maven 配置文件

团队支持多种应用服务器部署：

| Profile | 应用服务器 | Java EE 版本 |
|---------|------------|--------------|
| `tomcat90` | Tomcat 9.0 | Java EE 8 |
| `tomcat85` | Tomcat 8.5 | Java EE 7 |
| `tomee80` | TomEE 8.0 | Java EE 8 |
| `tomee71` | TomEE 7.1 | Java EE 7 |
| `wildfly26` | WildFly 26 | Java EE 8 |
| `jetty` | Jetty 9 | Servlet 3.1 |
| `liberty-ee8` | WebSphere Liberty | Java EE 8 |
| `glassfish5` | GlassFish 5 | Java EE 8 |

---

## 👥 团队与协作

本项目由经验丰富的开发团队共同完成，团队成员在项目中各展所长：

- **架构设计**: 负责系统整体架构与技术选型
- **后端开发**: 实现业务逻辑、数据持久层与 API 设计
- **前端开发**: 构建用户界面与交互体验
- **测试保障**: 编写单元测试与集成测试，确保代码质量
- **DevOps**: 配置 CI/CD 流水线与部署方案

我们采用敏捷开发方法，通过代码评审、结对编程等实践确保代码质量和团队成长。项目使用 GitHub Actions 实现持续集成，每次提交都会触发自动化构建与测试。

---

## 📊 开发统计

<div align="center">

![CI Badge](https://github.com/mybatis/jpetstore-6/actions/workflows/ci.yaml/badge.svg)
![Coverage](https://coveralls.io/repos/github/mybatis/jpetstore-6/badge.svg?branch=master)

</div>

---

## 🤝 贡献指南

我们欢迎社区贡献！请遵循以下步骤：

1. **Fork** 本仓库
2. 创建您的特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交您的更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 创建 **Pull Request**

### 代码规范

- 遵循项目现有的代码风格
- 确保所有提交通过 CI 检查
- 为新功能编写相应的测试用例
- 更新相关文档

---

## 📖 相关资源

| 资源 | 链接 |
|------|------|
| 项目文档 | [MyBatis JPetStore](http://www.mybatis.org/jpetstore-6) |
| MyBatis 官网 | [mybatis.org](https://mybatis.org) |
| 问题反馈 | [GitHub Issues](https://github.com/mybatis/jpetstore-6/issues) |
| 官方论坛 | [MyBatis Google Group](https://groups.google.com/group/mybatis-user) |

---

## 🌟 其他版本

如果您对不同技术栈感兴趣，以下是社区贡献的其他 JPetStore 实现：

- **Spring + Spring MVC + Spring Security**: [spring-jpetstore](https://github.com/making/spring-jpetstore)
- **Vaadin + Spring Boot**: [jpetstore-6-vaadin-spring-boot](https://github.com/igor-baiborodine/jpetstore-6-vaadin-spring-boot)
- **MyBatis Spring Boot Starter**: [mybatis-spring-boot-jpetstore](https://github.com/kazuki43zoo/mybatis-spring-boot-jpetstore)

---

## 📄 许可证

本项目基于 Apache License 2.0 开源 - 详情请参阅 [LICENSE](LICENSE) 文件。

---

<div align="center">

**感谢每一位参与项目的团队成员和社区贡献者！** 💙

*Made with ❤️ by our team*

</div>
