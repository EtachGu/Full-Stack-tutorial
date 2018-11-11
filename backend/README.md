# Back End Technology


|               | [Node](#node) ([deno](https://github.com/ry/deno))      | [Go](#go)          | [Python](#python)  | [Java](#java)      |
| ------------- | ------------------ | ------------------ | ------------------ | ------------------ |
| Multi-Threads | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
|When to use|

- [Back End Technology](#back-end-technology)
    - [Architecture knowledge](#architecture-knowledge)
    - [Node](#node)
        - [Koa](#koa)
    - [Go language](#go-language)
    - [Python](#python)
    - [Java](#java)
    - [RESTful API](#restful-api)
    - [Authentication & authorization](#authentication--authorization)
    - [Lua](#lua)
    - [Microservices Architecture 微服务](#microservices-architecture-%E5%BE%AE%E6%9C%8D%E5%8A%A1)
        - [12 Factors](#12-factors)
    - [Load/Stree Test](#loadstree-test)
    - [Theory fo distributed system](#theory-fo-distributed-system)
    - [Database](#database)
    - [Caching](#caching)
    - [Desgin Pattern 23种设计模式](#desgin-pattern-23%E7%A7%8D%E8%AE%BE%E8%AE%A1%E6%A8%A1%E5%BC%8F)
        - [创建型](#%E5%88%9B%E5%BB%BA%E5%9E%8B)
        - [结构型](#%E7%BB%93%E6%9E%84%E5%9E%8B)
        - [行为模式](#%E8%A1%8C%E4%B8%BA%E6%A8%A1%E5%BC%8F)
    - [FMEA(Failure mode and effects analysis) 故障模式与影响分析](#fmeafailure-mode-and-effects-analysis-%E6%95%85%E9%9A%9C%E6%A8%A1%E5%BC%8F%E4%B8%8E%E5%BD%B1%E5%93%8D%E5%88%86%E6%9E%90)
    - [Search](#search)

## Architecture knowledge

[architect-awesome](https://github.com/xingshaocheng/architect-awesome)

## Node
----
| Node                                                                                     | Article                                                                                |
| ---------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| [node技巧](https://github.com/Wscats/Good-text-Share/issues/44)                          | [NodeJs静态服务器](https://github.com/Wscats/angular-demo/tree/gh-pages/diyNodeServer) |
| **Reference**                                                                            | **Reference**                                                                          |
| [Node.js 包教不包会](https://github.com/alsotang/node-lessons)                           | [七天学会NodeJS](http://nqdeng.github.io/7-days-nodejs/)                               |
| [从零开始nodejs系列文章](http://blog.fens.me/series-nodejs)                              | [Node入门](http://www.nodebeginner.org/index-zh-cn.html)                               |
| [Node初学者入门，一本全面的NodeJS教程](http://ourjs.com/detail/529ca5950cb6498814000005) |

###  Koa
next generation web framework for node.js
[Koa](https://github.com/koajs)
[koa middleware](https://github.com/koajs/koa/wiki)

## Go language
----
| Article                                             | Article |
| --------------------------------------------------- | ------- |
| [Go Books](https://github.com/dariubs/GoBooks)      |
| [awesome-go](https://github.com/avelino/awesome-go) |
| [Go kit](https://github.com/go-kit/kit)             |

## [Python](https://www.python.org)
-----
| Article                                                                       | Article                                                                                 |
| ----------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| [awesome-python](https://github.com/vinta/awesome-python)                     |
| [Web 框架 Django](https://github.com/django/django)                           | [Django rest framework ](http://www.django-rest-framework.org/)                         |
| [django-debug-toolbar](https://github.com/jazzband/django-debug-toolbar/)     | [django db optimization](https://docs.djangoproject.com/en/2.0/topics/db/optimization/) |
| [Flask](http://flask.pocoo.org/)                                              |
| [Full Stack Python ](https://www.fullstackpython.com)                         | [microservices](https://www.fullstackpython.com/microservices.html)                     |
| [Pika RabbitMQ](https://github.com/pika/pika)                                 |
| [Green python Color, also for Djnago Test](https://github.com/CleanCut/green) |

**[Celery](http://docs.celeryproject.org/en/latest/index.html)**
is a task queue with focus on real-time processing, while also supporting task scheduling.

Why we need Task Queue in Web Context?

These are some common use cases:

- Running something in the background. For example, to finish the web request as soon as possible, then update the users page incrementally. This gives the user the impression of good performance and “snappiness”, even though the real work might actually take some time.
- Running something after the web request has finished.
- Making sure something is done, by executing it asynchronously and using retries.
- Scheduling periodic work.

| tool                                      |
| ----------------------------------------- |
| [virtualenv](https://virtualenv.pypa.io/) |

## Java
---


![spring cloud](../images/diagram-distributed-systems.svg)
[Java Spring](https://spring.io/)
[Spring boot优缺点](https://www.zhihu.com/question/39483566)
[Netlfix Eureka](https://github.com/Netflix/eureka) is a REST (Representational State Transfer) based service that is primarily used in the AWS cloud for locating services for the purpose of load balancing and failover of middle-tier servers

[spring cloud netflix](https://github.com/spring-cloud/spring-cloud-netflix)
Service Discovery (Eureka), Circuit Breaker (Hystrix), Intelligent Routing (Zuul) and Client Side Load Balancing (Ribbon)

[DTO VO POJO JavaBean](https://stackoverflow.com/questions/1612334/difference-between-dto-vo-pojo-javabeans)

[**Sample** Rest.js and Spring Data REST ](https://spring.io/guides/tutorials/react-and-spring-data-rest/)

[Playframework is based on a lightweight, stateless, web-friendly architecture](https://github.com/playframework/playframework)
|tool|
[Maven](https://maven.apache.org/what-is-maven.html) is a tool that can now be used for building and managing any Java-based project.
[Google guava](https://github.com/google/guava) is a set of core libraries that includes new collection types (such as multimap and multiset), immutable collections, a graph library, functional types, an in-memory cache, and APIs/utilities for concurrency, I/O, hashing, primitives, reflection, string processing, and much more!

## RESTful API

[Best practies for a pragmatic RESTful API](https://www.vinaysahni.com/best-practices-for-a-pragmatic-restful-api)

[HTTP API Design](https://github.com/interagent/http-api-design)

[OpenAPI](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/3.0.0.md)

[RESTful API design](https://github.com/aisuhua/restful-api-design-references)

[RESTful API introductions](https://idratherbewriting.com/learnapidoc/index.html)

[HATEOAS ( Hypermedia as Engine of Application State)](https://en.wikipedia.org/wiki/HATEOAS)

[Microsoft RESTful API guidelines](https://github.com/Microsoft/api-guidelines)

[API Style book](http://apistylebook.com/design/guidelines/)


## Authentication & authorization
OAuth
[OAuth 2](https://oauth.net/2/)

Basic 

tokn

JWT(JSON Web Token) https://jwt.io/

OpenID https://openid.net

Spring Security Domain Object Security (ACLs)
https://www.concretepage.com/spring/spring-security/

LDAP [OpenLDAP](http://www.zytrax.com/books/ldap/)
LDAP is often used by organizations as a central repository for user information and as an authentication service. It can also be used to store the role information for application users.

IAM (identity and access management)
all forms of access control can ultimately be mapped back to one of four classic models:
- Discretionary Access Control (DAC), 
- Mandatory Access Control (MAC), 
- Role-based Access Control (RBAC), 
- Attribute-based Access Control (ABAC)

http://blog.identityautomation.com/rbac-vs-abac-access-control-models-iam-explained

|Article|
|---|
|[Four Authentication & authorization ](https://blog.csdn.net/gdp12315_gu/article/details/79905424)|

|OpenSource|
|---|
|[Keycloak an open source Identity and Access Management solution](https://github.com/keycloak/keycloak)|
|[An OpenID Connect reference implementation in Java on the Spring platform](https://github.com/mitreid-connect/OpenID-Connect-Java-Spring-Server)|

## Lua

[kong](https://github.com/Kong/kong)基于OpenResty的 API 网关服务和网关服务管理层.


## Microservices Architecture 微服务

- [What is microservice](https://martinfowler.com/articles/microservices.html)
- [《微服务：从设计到部署》中文版](https://legacy.gitbook.com/book/docshome/microservices/details)


Tools for Microservices
|名称|  说明 |
|---|---|
|[API Fortress](https://apifortress.com/)|API 测试和健康检测工具，为企业级 API 提供自动化的功能测试、健康检测和负载测试。它的设计原则是无代码，完全基于现代 API 架构实践和模式而构建  **收费**|
|[Graylog](https://www.graylog.org/)|Security Incident and Event Management Report|
|[Istio](https://github.com/istio/istio)|它支持在 Kubernetes 上进行服务部署，其服务网格技术为微服务通信带来了可靠性、安全性和可管理性。其中，服务网格技术可以用于改善应用程序和微服务之间的关系和交互。**开源**|
|[Conductor](https://netflix.github.io/conductor/)|Netflix 的微服务编排引擎，是 Netflix OSS 生态系统的一部分。它可以运行在云端，并实现了微服务的流程编配。它还能够用于控制和可视化微服务之间的交互。|
|[Seneca](https://github.com/senecajs/seneca)|开发人员可以使用 Seneca，来轻松构建基于消息的微服务，它是 Node.js 的微服务工具包，可以用它写出干净而且结构良好的代码，并系统化应用程序的业务逻辑。|
|[Elixir](https://elixir-lang.org/)|Elixir is a dynamic, functional language designed for building scalable and maintainable applications.|


### [12 Factors](https://12factor.net/)

The factors represent a set of guidelines or best practices for portable, resilient applications that will thrive in cloud environments(specifically software as a service applications)

1. There should be a one-to-one association between a versioned codebase (for example,an IT repository) and a deployed service. The same codebase is used for many deployments.
2. Services should explicitly declare all dependencies, and should not rely on the presence of system-level tools or libraries.
3. Configuration that varies between deployment environments should be stored in the environment (specifically in environment variables).
4. All backing services are treated as attached resources, which are managed (attached and detached) by the execution environment.
5. The delivery pipeline should have strictly separate stages: Build, release, and run.
6. Applications should be deployed as one or more stateless processes. Specifically, transient processes must be stateless and share nothing. Persisted data should be stored in an appropriate backing service.
7. Self-contained services should make themselves available to other services by listening on a specified port.
8. Concurrency is achieved by scaling individual processes (horizontal scaling).
9. Processes must be disposable: Fast startup and graceful shutdown behaviors lead to a more robust and resilient system.
10. All environments, from local development to production, should be as similar as possible.
11. 11.Applications should produce logs as event streams (for example, writing to stdout and stderr), and trust the execution environment to aggregate streams.
12. If admin tasks are needed, they should be kept in source control and packaged alongside the application to ensure that it is run with the same environment as the application.

## Load/Stree Test

|Load/Stress Test|
|---|
|[ab - Apache HTTP server benchmarking tool](http://httpd.apache.org/docs/2.0/programs/ab.html)|
|[Apache JMeter](http://jmeter.apache.org/)|
|[Siege](http://freshmeat.sourceforge.net/projects/siege/)|
|[FunkLoad](http://funkload.nuxeo.org/#)|
|[loader.io](https://loader.io/)|


## Theory fo distributed system

- [CAP定理（CAP theorem, Consistency, Availability, Partition tolerance）](https://en.wikipedia.org/wiki/CAP_theorem)
- [Distributed Systems for fun and profit](http://book.mixu.net/distsys/)
- [8 fallacies of distributed computing](https://en.wikipedia.org/wiki/Fallacies_of_distributed_computing)
- [FLP 不可能性的](https://groups.csail.mit.edu/tds/papers/Lynch/jacm85.pdf)


## Database

|                     | Oracle             | Postgresql                                                                                                   | Mysql                                                                                         | SQLite                                                                            |
| ------------------- | ------------------ | ------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| Introduction        |                    |                                                                                                              |                                                                                               | A very powerful, embedded relational database management system                   |
| Relational Database | :heavy_check_mark: | :heavy_check_mark:                                                                                           | :heavy_check_mark:                                                                            | :heavy_check_mark:                                                                |
| Advantage           |                    | An open-source SQL standard compliant RDBMS,Strong community,Strong third-party support,Extensible,Objective | Easy to work,Feature rich,Secure, Scalabel, Speedy                                            | File based, Standards-aware                                                       |
| Disadvantage        |                    | Performance,Hosting                                                                                          | Function limitations, Reliability issues, Stagnated development                                                                                               | No user management, Lack of possibility to tinker with for additional performance |
| When to use         |                    | Data Integrity, Complex custom procedures,Integration,complex design                                         | Distributed operations, Hight security,Web site or Web app, Custom solution                   | Embedded app, Disk access replacement, Testing                                    |
| When not to use     |                    | Speed,Simple set ups,Replication                                                                             | [SQL Compliance](https://en.wikipedia.org/wiki/SQL_compliance), Concurrency, Full-text search | Multi-User App, High write volumes                                                |

|postgresql|
|---|
|[postgresql](https://www.postgresql.org/)|
|[pgAdmin GUI for Postgresql](https://www.pgadmin.org/)|


![mysql](../images/mysql.png)

|MySQL|
|---|
|[MySQL8.0 new feature支持文档存储](https://www.mysql.com/why-mysql/white-papers/whats-new-mysql-8-0/)|


reference:
[1]https://www.digitalocean.com/community/tutorials/sqlite-vs-mysql-vs-postgresql-a-comparison-of-relational-database-management-systems




## Caching

[Memcached VS Redis](https://stackoverflow.com/questions/10558465/memcached-vs-redis)

[System Properties Comparison Memcached vs. Redis](https://db-engines.com/en/system/Memcached%3BRedis)

Redis is better than Memcache


[Redis 中文网](http://www.redis.net.cn/tutorial/3502.html)

## Desgin Pattern 23种设计模式

### 创建型

- Abstract Factory 抽象工厂
- Builder 构建器
- Factory Method 工厂方法
- Prototype 原型
- Singleton 单例

### 结构型

- Adapter 适配器
- Bridge 桥接
- Composite 组合
- Decorator 装饰器
- Facade 外观模式
- Flyweight 享元模式
- Proxy 代理

### 行为模式

- Chain of Responsiblity 责任链
- Command 命令
- Iterpreter 解释器
- Iterator 迭代器
- Mediator 中介者
- Memento 备忘录
- Observer 观察者
- State 状态
- Strategy 策略
- Template Method 模板方法
- Visitor 访问者



## FMEA(Failure mode and effects analysis) 故障模式与影响分析

又称失效模式与后果分析、失效模式与效应分析、故障模式与后果分析等。

1. 找出产品或过程中潜在的故障模式
2. 根据相应的评价体系对找出的潜在故障模式进行风险量化评估
3. 列出故障的起因/机理，寻找预防或改进措施

## Search

ElasticSearch
https://www.elastic.co/guide/en/elasticsearch/reference/current/_basic_concepts.html

Apache Solr

Sphinx

Apache lucene