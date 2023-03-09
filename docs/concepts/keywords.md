---
title: 名词介绍
slug: /docs/concepts/keywords
---

## 概述

在开发中，我们经常提到一些名词 “单体”、“微服务”、“API”、“gRPC”、“gRPC stub”，”Protobuf“、“rest”、“负载均衡”，“服务发现” 等名词，这些名词后后续文档中也会经常提到，为了保证大家对这些名词有初步概念，我们将针对一些高频名词进行说明。

## 单体

单体又称单体架构模式，单体架构采用分层架构模式设计，在单体架构设计中，业务逻辑全部集中在单个服务中，换句话来说就是，整个应用包含了各个模块的业务逻辑，单体架构有一些特性：

1. 开发效率低

单体架构（Monolithic Architecture）是一种将所有功能打包在一个容器中运行的设计风格，一个实例中集成了一个系统的所有功能。通过负载均衡软件/设备实现多实例调用。

2. 可维护性差

业务逻辑都集中在一个服务里面，单个开发者不太可能完全掌控整个业务，因此业务修改和问题追查定位都非常困难。由于很少有人能够对业务非常熟悉，增加新功能或者修改原有功能时更多像是在打补丁，导致代码质量和可维护性越来越差，各种功能耦合在一起，新人接手的时候都不知道从何下手。

3. 架构扩展性差

不同模块可能有不同的架构要求，单体服务很难照顾到大家的差异化需求，如果想针对某个模块进行新架构和新语言的调整与支持，也比较困难

4. 部署不灵活

任何一处很小的改动，都需要对整个服务进行编译、部署和上线，这可能会影响整个系统的稳定性，同时很难对某个特定的模块进行单独的容量规划和部署设计。

5. 健壮性差

单体服务的所有模块都在一起，某个模块出现严重问题，会导致整个业务不可用。当业务代码规模很庞大时，系统的故障点会很多，严重影响业务的健壮性和可用性。

## 微服务

微服务（Microservices）是一种软件架构风格，它是以专注于单一责任与功能的小型功能区块 (Small Building Blocks) 为基础，利用模块化的方式组合出复杂的大型应用程序，各功能区块使用与语言无关 (Language-Independent/Language agnostic）的API集相互通信。

微服务就是为了解决单体服务的上述问题而生的，按照微服务权威专家Martin Fowler的定义，微服务架构是将单个服务拆分成一系列小服务，这些小服务都拥有独立的进程，通过HTTP RESTful API之类的轻量级通信方式进行通信，而作为独立的业务服务，则可采用一些自动化部署机制独立部署，每个服务可以使用不同的开发语言和数据存储技术，实现去中心化的服务管理。

在当前微服务盛行的时代，好像设计微服务开发是一件很简单的事情，但是在实际的开发过程中，微服务的设计并不是一件容易的事情，微服务的设计需要考虑的问题有很多，比如服务的拆分、服务的通信、服务的部署、服务的监控、服务的治理等等，这些问题都需要我们在设计微服务的时候进行考虑。

## API

应用程序接口（英語：application programming interface），缩写为API，是一种计算接口，它定义多个软件中介之间的交互，以及可以进行的调用（call）或请求（request）的种类，如何进行调用或发出请求，应使用的数据格式，应遵循的惯例等。它还可以提供扩展机制，以便用户可以通过各种方式对现有功能进行不同程度的扩展[3]。一个API可以是完全定制的，针对某个组件的，也可以是基于行业标准设计的以确保互操作性。通过信息隐藏，API实现了模块化编程，从而允许用户实现独立地使用接口。

API 分系统级 API（如：Windows、macOS、Linux 操作系统层面的接口）和非系统级接口，我们在前后端开发中提到的 API 特指 Web API，是前后端进行数据传输的一种方式，前端通过 HTTP 请求的方式向后端发送请求，后端通过 HTTP 响应的方式向前端返回数据。

## gRPC

在理解 gRPC 之前，应该先了解 RPC 的概念，RPC 即远程过程调用，是一种计算机通信协议，它允许运行在不同计算机上的程序调用彼此的子程序，而程序员无需额外地为这个交互作用编程。RPC 通常是通过网络来实现，但也可以通过本地进程间的通信来实现。

gRPC 是 Google 开源的一款高性能、通用的开源 RPC 框架，基于 HTTP/2 协议，支持多种语言，包括 C++、Java、Python、Go、Ruby、C#、Node.js、PHP、Objective-C、Swift 等。

gRPC 通过 Protocol Buffers 定义服务接口，通过 HTTP/2 协议进行数据传输，支持双向流式传输，支持客户端流式传输，支持服务端流式传输，支持元数据传输，支持流控制，支持身份验证，支持负载均衡，支持跨语言调用，支持跨平台调用，支持多种语言的客户端和服务端。

## Protocol Buffers

Protocol Buffers 是 Google 开源的一种数据交换格式，它以二进制格式存储，比 XML、JSON 等文本格式更小、更快，同时也更加简单。Protocol Buffers 以 .proto 文件作为定义文件，通过 Protocol Buffers 编译器将 .proto 文件编译成对应的语言文件，如 Java、Python、Go 等。

Protocol Buffers 有以下特点：

* 二进制格式，比 XML、JSON 等文本格式更小、更快，同时也更加简单。
* 支持自动代码生成，支持多种语言，包括 C++、Java、Python、Go、Ruby、C#、Node.js、PHP、Objective-C、Swift 等。
* 支持跨平台。
* 支持跨语言。
* 支持自定义序列化。

## RESTful API

Restful API 是一种软件架构风格，它提供了一组设计原则和约束条件，用于创建 Web 服务。Restful API 通过 HTTP 协议进行数据传输，通过 URL 定义资源，通过 HTTP 方法定义操作，通过 HTTP 状态码定义操作结果。

## gRPC Stub

gRPC Stub 是 gRPC 的客户端和服务端，它们通过 gRPC Stub 与 gRPC Server 进行通信，gRPC Stub 通过 Protocol Buffers 定义服务接口，通过 HTTP/2 协议进行数据传输，支持双向流式传输，支持客户端流式传输，支持服务端流式传输，支持元数据传输，支持流控制，支持身份验证，支持负载均衡，支持跨语言调用，支持跨平台调用，支持多种语言的客户端和服务端。

## ETCD

ETCD 是 CoreOS 开源的一款分布式键值对存储系统，它提供了一系列的 API，用于实现分布式系统中的数据共享和服务发现。

## Nacos

Nacos 是阿里巴巴开源的一款分布式服务发现和配置管理系统，它提供了一系列的 API，用于实现分布式系统中的数据共享和服务发现。

## 服务注册与发现

服务注册与发现是分布式系统中的一种常见模式，它通过服务注册中心来管理服务实例，服务实例在启动时向服务注册中心注册自己提供的服务，服务实例在停止时向服务注册中心注销自己提供的服务，服务消费者通过服务注册中心来发现服务提供者。

常见的服务注册与发现组件有 Etcd、Consul、Eureka、Nacos 等。

## 负载均衡

负载均衡是分布式系统中的一种常见模式，它通过负载均衡器来管理服务实例，负载均衡器通过负载均衡算法将请求分发到服务实例上，常见的负载均衡算法有轮询、随机、加权轮询、加权随机、一致性哈希等。

## API 网关

API 网关是分布式系统中的一种常见模式，它通过 API 网关来管理服务实例，API 网关通过路由规则将请求分发到服务实例上，常见的 API 网关有 Kong、Nginx、Traefik、Envoy 等。

## gRPC 网关

gRPC 网关是 gRPC 的一种实现，它通过 gRPC 网关来管理 gRPC 服务实例，gRPC 网关通过路由规则将请求分发到 gRPC 服务实例上，常见的 gRPC 网关有 Envoy、Kong、Nginx、Traefik 等。

## 服务治理

服务治理是分布式系统中的一种常见模式，它通过服务治理组件来管理服务实例，服务治理组件通过服务治理算法来管理服务实例，常见的服务治理算法有熔断、限流、降级、隔离、重试、超时等。

熔断采用的是断路器模式，当服务实例出现故障时，断路器将会打开，断路器打开后，服务实例将不再接收请求，断路器打开后，服务实例将会进入半开状态，半开状态下，服务实例将会接收少量请求，如果请求成功，则断路器将会关闭，如果请求失败，则断路器将会继续打开，常见的熔断组件有 Hystrix、Sentinel、Envoy 等。

限流是一种流量控制的手段，它通过限流器来管理服务实例，限流器通过限流算法来管理服务实例，常见的限流算法有计数器、漏桶、令牌桶等。

降级是一种流量控制的手段，它通过降级器来管理服务实例，降级器通过降级算法来管理服务实例，常见的降级算法有直接返回、缓存、降级服务等。

隔离是一种流量控制的手段，它通过隔离器来管理服务实例，隔离器通过隔离算法来管理服务实例，常见的隔离算法有线程池、信号量、信号量隔离、线程池隔离等。

重试是一种流量控制的手段，它通过重试器来管理服务实例，重试器通过重试算法来管理服务实例，常见的重试算法有重试一次、重试两次、重试三次等。

超时是一种流量控制的手段，可以通过超时时长来控制服务实例的响应时间，超时时长越短，服务实例的响应时间越短，超时时长越长，服务实例的响应时间越长。

## 上下游

服务上下游有多种说法，有的称服务上游是指服务调用方，服务下游是指服务提供方；而有的则成服务上游是靠近数据源（数据库）的服务，服务下游是靠近数据消费方的服务。
 
## 服务监控

服务监控是分布式系统中的一种常见模式，它通过服务监控组件来监控服务实例，服务监控组件通过服务监控算法来监控服务实例，常见的服务监控算法有链路追踪、日志、指标、事件等。

## 事务

事务是分布式系统中的一种常见模式，它通过事务组件来管理服务实例，事务组件通过事务算法来管理服务实例，常见的事务算法有本地事务、分布式事务、TCC 事务、Saga 事务等。

## 健康检查

健康检查是分布式系统中的一种常见模式，它通过健康检查组件来检查服务实例，健康检查组件通过健康检查算法来检查服务实例，常见的健康检查算法有心跳检查、健康检查、健康检查等。

## 服务认证

服务认证是分布式系统中的一种常见模式，它通过服务认证组件来认证服务实例，服务认证组件通过服务认证算法来认证服务实例，常见的服务认证算法有用户名密码认证、OAuth2 认证、JWT 认证等。

## 消息队列

消息队列是用来解耦的一种常见模式，它通过消息队列组件来解耦服务实例，常见的消息队列组件有 Kafka、RabbitMQ、RocketMQ 等。
 
## 参考文献

- <a href="https://weread.qq.com/web/bookDetail/42932ba07195510b429d842" target="_blank">《Service Mesh 微服务架构设计》</a>
- <a href="https://zh.wikipedia.org/zh-sg/%E5%BE%AE%E6%9C%8D%E5%8B%99" target="_blank">《微服务•维基百科》</a>
- <a href="https://zh.wikipedia.org/wiki/%E5%BA%94%E7%94%A8%E7%A8%8B%E5%BA%8F%E6%8E%A5%E5%8F%A3" target="_blank">《应用程序接口•维基百科》</a>