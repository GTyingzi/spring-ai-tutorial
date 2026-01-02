本教程将采用2025年5月20日正式的GA版，给出如下内容
1. 核心功能模块的快速上手教程
2. 核心功能模块的源码级解读
3. Spring ai alibaba增强的快速上手教程 + 源码级解读

版本：
- JDK21
- SpringBoot 3.4.5
- SpringAI 1.1.0-M3：https://github.com/spring-projects/spring-ai
- SpringAI Alibaba(SAA) 1.0.0.4：https://github.com/alibaba/spring-ai-alibaba
- Spring AI Extensions 1.1.0.0-M3：https://github.com/spring-ai-alibaba/spring-ai-extensions

### 项目目录结构
```text
chat目录                            
    - alibaba-chat                      # 基于alibaba实现chat案例
    - openai-chat                       # 基于openai实现chat案例
    - deepseek-chat                     # 基于deepseek实现chat案例
    - chat-setting                      # chat client的连接、请求时间设置
image目录
    - alibaba-image                     # 基于alibaba实现image生成案例
video目录
    - alibaba-video                     # 基于alibaba实现video生成案例
advisor目录                         
    - advisor-base                  # advisor绑定内存记忆案例
    - advisor-deep-think            # 基于advisor的深度思考案例
    - advisor-memory-sqlite         # 基于sqlite的advisor绑定内存记忆案例
    - advisor-memory-mysql          # 基于mysql的advisor绑定内存记忆案例
    - advisor-memory-redis          # 基于redis的advisor绑定内存记忆案例
    - advisor-memory-mem0           # 基于mem0的advisor绑定内存记忆案例
tool-calling                        # 时间、天气两个工具的Method版、Function版实现、internalToolExecutionEnabled、returnDirect设置
structured-output                   # map、list、实例对象类型的格式化输出案例
vector目录                         
    - vector-simple                 # 基于内存的向量数据库案例
    - vecotr-redis                  # 基于redis的向量数据库案例
    - vector-elasticsearch          # 基于ES的向量数据库案例
    - vector-pgvector               # 基于pgvector的向量数据库案例
    - vector-neo4j                  # 基于neo4j的向量数据库案例
rag目录                             
    - rag-simple                    # 基于内存的rag效果对比、模块化rag案例
    - rag-etl-pipeline              # 提取文档、转换文档、写出文档的案例   
    - rag-evaluation                # 多模型评估，模型响应结果，结合RAG的案例
    - rag-elasticsearch             # 基于ES的rag案例
mcp目录
    - mcp-auth                           # MCP认证相关模块
        - client目录
            - mcp-auth-client                # MCP基于请求头的授权客户端
            - mcp-security-client            # MCP安全认证客户端
        - server目录
            - mcp-auth-server               # MCP基于请求头的授权服务端-工具粒度
            - mcp-auth-web-server           # MCP基于请求头的授权服务端-页面粒度
            - mcp-security-server           # MCP安全认证服务端
        - authorization-server           # MCP授权服务端
    - mcp-starter                        # MCP基础功能模块
        - client目录
            - mcp-stdio-client              # MCP的stdio客户端案例
            - mcp-webflux-client            # MCP的webflux客户端案例
            - mcp-streamable-client         # MCP的streamable客户端案例
            - mcp-streamable-webflux-client # MCP的streamable webflux客户端案例
            - mcp-annotation-client         # MCP基于注解的客户端案例
        - server目录
            - mcp-stdio-server              # MCP的stdio服务端案例
            - mcp-webflux-server            # MCP的webflux服务端案例
            - mcp-streamable-webmvc-server  # MCP的streamable webmvc案例
            - mcp-streamable-webflux-server # MCP的streamable webflux案例
            - mcp-annotation-server         # MCP基于注解的服务端案例
    - mcp-supple                         # MCP扩展功能模块
        - client目录
            - mcp-nacos3-client             # MCP基于Nacos3.*实现分布式部署客户端案例
            - mcp-recovery-client           # MCP的SSE连接断开，自动重连案例
            - mcp-return-direct-client      # MCP的结果直接返回给客户端案例
        - server目录
            - mcp-nacos3-server             # MCP基于Nacos3.*实现分布式部署服务端案例
            - mcp-gateway-server            # SAA的gateway服务零代码实现存量应用转换MCP案例
            - mcp-nacos-parse-swagger-server # MCP基于nacos动态解析swagger的restful服务端案例
ovservation目录
    - observabilty                              # ObservationHandler下的client、model、tool、embedding的观测案例
    - observability-langfuse                    # 基于langfuse的观测案例
graph目录  # 基于spring ai alibaba graph内核
    - simple                        # 最简单的graph案例
    - stream-node                   # 节点中AI模型的流式输出案例
    - human-node                    # 流式返回结果，中断等待用户反馈，继续执行人类输入之后的工作案例
    - paraller-node                 # 多节点并行的案例
    - parallel-stream-node          # 多节点并行的流式输出案例
    - mcp-node                      # 配置指定mcp给指定node的案例
    - observe-langfuse              # 基于langfuse观测graph案例
    agent目录
        - react-agent               # 基于时间工具的React Agent案例
        - reflection-agent          # 基于反思机制的Reflection Agent案例
other目录
    - restful服务                           # 提供接口调用服务，模拟存量接口
    - nacos-swagger-restful(待补充)         # 基于nacos+swagger的接口
    - nacos-restful                        # 基于nacos3.*的接口    
    
deepresearch(待补充)                        # 基于spring ai alibaba graph实现深度研究案例
```
视频讲解地址：[B站-视频讲解](https://www.bilibili.com/video/BV17NMsziEqp?vd_source=8393ba8b4463e2acda959f2ff2c792f6&spm_id_from=333.788.videopod.sections)

微信推文系列：[微信推文版](https://mp.weixin.qq.com/s/9iLebKR8HNwalOVeDz5PXQ)

deepresearch是简化版：https://github.com/spring-ai-alibaba/deepresearch
[![](https://yingziimage.oss-cn-beijing.aliyuncs.com/img/image-20251001121713795.png)](https://yingziimage.oss-cn-beijing.aliyuncs.com/video/deep_research.mov)
video：https://yingziimage.oss-cn-beijing.aliyuncs.com/video/deep_research.mov
