## 功能介绍
通过 BOT 与业务安全，用户可以在 BOT 管理中开启并配置对应模块内容，并结合 BOT 流量分析与访问日志进行观察和分析。根据流量分析提供的会话状态信息进行精细化策略设置，保护网站核心接口和业务免受 BOT 侵害。

BOT 管理设置支持配置 BOT 场景类型、客户端风险识别（前端对抗）、威胁情报、AI 评估、智能统计、动作分数、自定义规则、Token 配置、合法爬虫模块，通过配置这些模块，实现对 BOT 的精细化管理。BOT 最佳实践流程图如下所示：
![](https://qcloudimg.tencent-cloud.cn/raw/8f80bd7286dd6a1131c14caac08b5412.png)

## 前提条件
- BOT 流量管理需要购买 WAF [对应实例的扩展包](https://cloud.tencent.com/document/product/627/11730#bot-.E6.B5.81.E9.87.8F.E7.AE.A1.E7.90.86.3Ca-id.3D.22bot.22.3E.3C.2Fa.3E)。
- 已在 [BOT 与业务安全页面](https://console.cloud.tencent.com/guanjia/tea-botconfig)，选择需要防护的域名，并开启 BOT 流量开关。
![](https://qcloudimg.tencent-cloud.cn/raw/642d93faac4b01d62cf0b84583318040.png)

## BOT 场景化配置
该功能依托腾讯多年 BOT 治理的专家经验，针对 BOT 中常见的秒杀、爬价格/爬内容和登录等场景，从客户端风险识别（前端对抗）、威胁情报、AI 策略、智能分析、动作得分、会话管理、合法爬虫和自定义规则等维度基于专家经验进行设置，解决客户配置难的问题，简单易用，轻松上手。
1. 登录 [Web 应用防火墙控制台](https://console.cloud.tencent.com/guanjia/tea-botconfig)，在左侧导航栏中，选择**配置中心** > **BOT 与业务安全**。
2. 在 BOT 与业务安全页面，左上角选择需要防护的域名，单击 **BOT 管理**。
3. 在 BOT 管理页面，单击**新建场景**。
4. 在新建场景弹窗中，配置相关参数，单击**立即创建**。
>!选中秒杀、登录和爬文案/爬内容 中的任意一个场景与自定义场景互斥。
>
**参数说明：**
 - **场景名称**：描述场景的名称，不可超过50个字符
 - **业务场景类型**：支持多选，可选择秒杀、登录、爬文案/爬内容和自定义场景。
 - **客户端类型**：访问防护目标的客户端类型。
 - **优先级**：该场景的执行优先级，输入范围为1-100的整数，数字越小，优先级越高；
 - **生效范围**：该场景在该域名下的生效范围，支持全部范围和自定义范围
5. 场景化管理列表中，将出现创建完成的场景卡片数据，即可进一步对其进行配置。

## 会话管理
用户可通过配置该功能，配置会话 Token 所在的位置，实现在同一 IP 下区分识别不同用户的访问行为，实现不影响其他用户的情况下，精准处置存在异常访问行为的用户。
1. 登录 [Web 应用防火墙控制台](https://console.cloud.tencent.com/guanjia/tea-botconfig)，在左侧导航栏中，选择**配置中心** > **BOT 与业务安全**。
2. 在 BOT 与业务安全页面，左上角选择需要防护的域名，单击 **BOT 管理**。
![](https://qcloudimg.tencent-cloud.cn/raw/642d93faac4b01d62cf0b84583318040.png)

2. 在 BOT 管理页面，在全局设置中，单击会话管理模块的**前往配置**。
![](https://qcloudimg.tencent-cloud.cn/raw/6f10bb1aa3317797f6fb1cc0c34c4a3d.png)
4. 在会话管理页面，单击**添加配置**，配置相关参数，单击**确定**。
![](https://qcloudimg.tencent-cloud.cn/raw/12b301e5c52657b8a3fade644668bf00.png)
**参数说明：**
 - **Token 名称**：自定义名称，最多128个字符。
 - **Token 描述**：自定义描述，最多128个字符。
 - **Token 位置**：可选择 HEADER、COOKIE、GET 或 POST，其中 GET 或 POST 是指 HTTP 请求内容参数，非 HTTP 头部信息。
 - **Token 标识**：取值标识。
 

## 客户端风险识别（前端对抗）
客户端风险识别功能通过客户端动态安全验证技术，对业务请求的每个客户端生成唯一 ID，检测客户端对 Web 或 H5页面访问中可能存在机器人和恶意爬虫行为，保护网站业务安全。
>?本功能**不支持 CLB-WAF，泛域名，以及 App/小程序**，只适用与 Web 或 H5页面，如果有非动态认证，自动化接口脚本需要优先加入白名单。

### 添加白名单
添加白名单主要用于对不需要进行设置的接口放行处理。
1. 登录 [Web 应用防火墙控制台](https://console.cloud.tencent.com/guanjia/tea-botconfig)，在左侧导航栏中，选择**配置中心** > **BOT 与业务安全**。
2. 在 BOT 与业务安全页面，左上角选择需要防护的域名，单击 **BOT 管理**。
![](https://qcloudimg.tencent-cloud.cn/raw/642d93faac4b01d62cf0b84583318040.png)
2. 在 BOT 管理页面，在全局设置中，单击前端对抗模块的**前往配置**。
3. 在前端对抗页面，单击**添加规则**，弹出添加白名单规则窗口。
![](https://qcloudimg.tencent-cloud.cn/raw/fa8b1398f2bbf8247c1786fe426e3f40.png)
4. 在添加白名单规则窗口中，配置相关参数，单击**确定**即可。
![](https://qcloudimg.tencent-cloud.cn/raw/ffee9c1a69fe9e400dbd5de8684f85a6.png)

### 案例一：大量机器自动化脚本请求服务
有大量机器自动化脚本请求服务，禁止类似 CURL，SOAPUI、JMETER、POSTMAN 访问请求。

1. 登录 [Web 应用防火墙控制台](https://console.cloud.tencent.com/guanjia/tea-botconfig)，在左侧导航栏中，选择**配置中心** > **BOT 与业务安全**。
2. 在 BOT 与业务安全页面，左上角选择需要防护的域名，单击 **BOT 管理**。
![](https://qcloudimg.tencent-cloud.cn/raw/642d93faac4b01d62cf0b84583318040.png)
2. 在 BOT 管理页面，在全局设置中，单击前端对抗模块的**前往配置**。
4. 单击自动化工具识别的![](https://qcloudimg.tencent-cloud.cn/raw/5be282efe2247c29686330d3810c4acc.png)，确认白名单。
5. 单击某场景配置页，单击**前端对抗**，单击该场景下前端对抗模块的![](https://qcloudimg.tencent-cloud.cn/raw/8257e4baf0c410e6765732438db68c70.png)，防护模式选择**拦截**，开启该前端对抗功能。
5. 使用 CURL、SELENIUM、POSTMAN 请求结果分别如下所示：
![](https://qcloudimg.tencent-cloud.cn/raw/582fddd3ed6b0916dc438f06f755ed14.png)
![](https://qcloudimg.tencent-cloud.cn/raw/ddaf3356a3fc45199cab550f5342b8ba.png)
![](https://qcloudimg.tencent-cloud.cn/raw/38bff2fb67783a718c022173faceef18.png)

### 案例二：禁止网页调试
禁止用户打开网页调试，避免针对性爬虫编写。
1. 登录 [Web 应用防火墙控制台](https://console.cloud.tencent.com/guanjia/tea-botconfig)，在左侧导航栏中，选择**配置中心** > **BOT 与业务安全**。
2. 在 BOT 与业务安全页面，左上角选择需要防护的域名，单击 **BOT 管理**。
![](https://qcloudimg.tencent-cloud.cn/raw/642d93faac4b01d62cf0b84583318040.png)
3. 在 BOT 管理页面，在全局设置中，单击前端对抗模块的**前往配置**。
4. 单击页面防调试的![](https://qcloudimg.tencent-cloud.cn/raw/5be282efe2247c29686330d3810c4acc.png)，确认白名单。![](https://qcloudimg.tencent-cloud.cn/raw/dd6203a9aca9ec7b7eaaaf3942a84549.png)

5. 单击某场景配置页，单击**前端对抗**，单击该场景下前端对抗模块的![](https://qcloudimg.tencent-cloud.cn/raw/8257e4baf0c410e6765732438db68c70.png)，防护模式选择**拦截**，开启该前端对抗功能。
6. 使用 Chrome 请求结果如下所示：
![](https://qcloudimg.tencent-cloud.cn/raw/2123f885e0677cc1896172c628ff6528.png)

## 威胁情报
威胁情报功能依托腾讯近二十年的网络安全经验和大数据情报，将通过实时判定 IP 状态，采取打分机制，量化风险值，精准识别来自恶意动态 IP、IDC 的访问，同时智能识别恶意爬虫特征，解决来自恶意爬虫、分布式爬虫、代理、撞库、薅羊毛等风险访问。
>?开启威胁情报功能时需要确认业务是否有 IDC 侧的用户访问，确认业务有 IDC 流量访问时，需要先关闭 ID 后，再开启威胁情报功能。
>
1. 登录 [Web 应用防火墙控制台](https://console.cloud.tencent.com/guanjia/tea-botconfig)，在左侧导航栏中，选择**配置中心** > **BOT 与业务安全**。
2. 在 BOT 与业务安全页面，左上角选择需要防护的域名，单击 **BOT 管理**。
![](https://qcloudimg.tencent-cloud.cn/raw/642d93faac4b01d62cf0b84583318040.png)
2. 在 BOT 管理页面，在全局设置中，单击威胁情报模块的**前往配置**。
3. 在威胁情报页面，如果有 IDC 流量访问，单击 IDC 网络的**一键关闭**，关闭功能。
![](https://qcloudimg.tencent-cloud.cn/raw/0846cc848cd1ba8d808843b4fe4d602e.png)
4. 如果没有 IDC 流量访问， 单击某场景配置页，单击**智能统计**，单击该场景下威胁情报模块的![](https://qcloudimg.tencent-cloud.cn/raw/8257e4baf0c410e6765732438db68c70.png)，直接开启威胁情报功能即可。
![](https://qcloudimg.tencent-cloud.cn/raw/7eab997dccb4fa003972f73c0553bcd0.png)

## AI 评估
AI 评估功能基于人工智能技术和腾讯风控实战沉淀，将风控特征和黑灰产对抗经验转化为 AI 评估模型，通过访问流量进行大数据分析与 AI 建模，实现快速识别恶意访问者、深层次恶意访问者，解决来自高级持续性威胁 BOT、隐蔽性威胁 BOT 的风险访问行为。
>?AI 评估是根据 AI 建模自动学习，可直接开启；如果有误评估，将对相应 URL 加白即可。

### 开启 AI 评估
1. 登录 [Web 应用防火墙控制台](https://console.cloud.tencent.com/guanjia/tea-botconfig)，在左侧导航栏中，选择**配置中心** > **BOT 与业务安全**。
2. 在 BOT 与业务安全页面，左上角选择需要防护的域名，单击 **BOT 管理**。
![](https://qcloudimg.tencent-cloud.cn/raw/642d93faac4b01d62cf0b84583318040.png)
2. 在 BOT 管理页面，在全局设置中，单击AI策略模块的**前往配置**。

### 添加白名单
#### 背景信息
在 AI 评估页面，该请求为正常请求，但是被 AI 误报。
![](https://qcloudimg.tencent-cloud.cn/raw/031bafaadb1f2acac2124a6e5c3d48b3.png)
#### 操作步骤
1. 登录 [Web 应用防火墙控制台](https://console.cloud.tencent.com/guanjia/tea-botconfig)，在左侧导航栏中，选择**配置中心** > **BOT 与业务安全**。
2. 在 BOT 与业务安全页面，左上角选择需要防护的域名，单击 **BOT 管理**。
![](https://qcloudimg.tencent-cloud.cn/raw/642d93faac4b01d62cf0b84583318040.png)
3. 在 BOT 管理页面，在全局设置中，单击 AI 评估模块的**前往配置**。
4. 在 AI 评估页面，单击**添加白名单**，输入名称、描述和加白 URL，单击**确定**。
![](https://qcloudimg.tencent-cloud.cn/raw/2250a8847f6e110e13b55b1bf9a70045.png)
5. 单击某场景配置页，单击**智能统计**，单击该场景下 AI 策略模块的![](https://qcloudimg.tencent-cloud.cn/raw/8257e4baf0c410e6765732438db68c70.png)，直接开启 AI 策略功能即可。


## 智能统计
智能统计功能基于大数据分析统计，根据用户群体的流量特征自动分类，自动识别存在异常的恶意流量，通过大数据分析，自动调整恶意流量阈值，解决来自常规 BOT、高频 BOT 的风险访问，并通过自动调整统计模型，解决大部分的 BOT 行为绕过问题。
>?可直接开启智能统计，推荐使用智能模式。
>
1. 登录 [Web 应用防火墙控制台](https://console.cloud.tencent.com/guanjia/tea-botconfig)，在左侧导航栏中，选择**配置中心** > **BOT 与业务安全**。
2. 在 BOT 与业务安全页面，左上角选择需要防护的域名，单击 **BOT 管理**。
![](https://qcloudimg.tencent-cloud.cn/raw/642d93faac4b01d62cf0b84583318040.png)
2. 在 BOT 管理页面，在全局设置中，单击 AI 评估模块的**前往配置**。

## 动作策略
动作设置功能通过威胁情报、AI 评估、智能统计对网站的访问请求进行综合性打分。打分范围在0-100分范围内，分数越高 BOT 的可能性越高、其访问对网站产生的危害/压力则越大。通过分数智能识别访问行为的风险程度，用户可配置不同动作策略和每个动作策略相应的生效范围和不同分数段的动作实现风险访问的精准拦截。

#### 背景信息
当威胁情报，AI 评估以及智能统计标记出了大量流量，默认配置无法做到更加详细的拦截，需要自定义动作如何分析配置。

#### 操作步骤
1. 登录 [Web 应用防火墙控制台](https://console.cloud.tencent.com/guanjia/tea-botconfig)，在左侧导航栏中，选择 **BOT 流量分析**。
2. 在 BOT流量分析页面，左上角选择需要防护的域名，选择所需访问源，单击**查看详情**。
![](https://qcloudimg.tencent-cloud.cn/raw/bffd30f0ad69ae1dfe41a9f7b01a9f9e.png)
2. 在 BOT 流量详情页面的基础会话信息模块，查看城市和 IP 地区。
![](https://qcloudimg.tencent-cloud.cn/raw/afecbe9db7580b55cade4f48f1ecb880.png)
3. 当业务没有该地区的流量时，则表明此处评分为异常，可以自定义动作设置，进行一个更加细化的设置。
4. 在 BOT 与业务安全页面，左上角选择需要防护的域名，单击 **BOT 管理**。
![](https://qcloudimg.tencent-cloud.cn/raw/642d93faac4b01d62cf0b84583318040.png)
4. 点击某场景配置页，单击**智能统计**，单击该场景下动作策略模块的**新增动作策略**。
6. 在动作策略页面，配置相关参数，单击**立即发布**。
![](https://qcloudimg.tencent-cloud.cn/raw/5915d2e122111c99a6022c317203333e.png)
**参数说明：**
 - **策略名称**：填写动作策略名称
 -  **生效开关**：当前动作策略是否生效
 -   **生效范围**：当前动作策略的生效范围
 -   **优先级**：当前动作策略的执行优先级，请输入1-100的整数，数字越小，代表这条策略的执行优先级越高；
 - **模式设置**： 提供宽松模式、中等模式、严格模式、自定义模式这四种默认处置模式，宽松、中等、严格这三种模式为预设模式，分别代表 BOT 流量管理针对不同危害程度的 BOT 的推荐分类及处置策略。这三种预设模式可进行修改，修改后为自定义模式。
 - **分数段设置**：分数段区间总分数为 0-100 分，每个分数段总共可以添加10条，配置的分数区间范围左闭右开，分数段不可重合，分数区间可设置为空，设置为空时，空的分数段不处置动作。
 - **动作设置**：可设置为信任、监控、重定向（重定向至特定网站 URL）、人机识别（验证码）或拦截。
 - **标签设置**：可设置为友好 BOT、恶意 BOT、正常流量或疑似 BOT。
    - 友好 BOT：为默认对网站友好/合法的 BOT。
    - 疑似 BOT：为识别出该访问源流量疑似 BOT，但无法判断其对网站的是否有害。
    - 正常流量：为认为访问的流量为正常人类。
    - 恶意 BOT：为对网站产生恶意流量/访问请求不友好的 BOT。


## 合法爬虫
通过配置合法爬虫（如：搜索引擎、订阅机器人）可以正常获取网站数据，使网站可以正常被索引。
1. 登录 [Web 应用防火墙控制台](https://console.cloud.tencent.com/guanjia/tea-botconfig)，在左侧导航栏中，选择**配置中心** > **BOT 与业务安全**。
2. 在 BOT 与业务安全页面，左上角选择需要防护的域名，单击 **BOT 管理**。
![](https://qcloudimg.tencent-cloud.cn/raw/642d93faac4b01d62cf0b84583318040.png)
2. 在 BOT 管理页面，在全局设置中，单击合法爬虫模块的**前往配置**。
![](https://qcloudimg.tencent-cloud.cn/raw/d3399683644bb87a974989b6f6417521.png)
4. 在合法爬虫页面，可单击![](https://qcloudimg.tencent-cloud.cn/raw/048eef2465cde85cf20de21900d6f37d.png)，开启对应功能。
![](https://qcloudimg.tencent-cloud.cn/raw/ed676c141de7c834819188dbc90cf8b3.png)

## 自定义规则
通过配置自定义规则功能，可精准处置符合行为配置的爬虫，精准处置对应特征的访问特征请求。
>!
>- 目前在创建 BOT 场景化时，已经根据场景类型内置相应场景的自定义规则集。
>- 本功能主要分析数据来源于 [BOT 流量分析](https://console.cloud.tencent.com/guanjia/tea-flowanalysis)。
>- 该内容**只做使用分析参考，不能当做业务标准配置**，网络爬虫分为很多种，基本都是随着业务类型而变。

### 案例详情
目前已经无法通过动作得分进行拦截，需要对异常行为特征进行设置，在 BOT 流量分析进行查看出大概异常后，单击**详情**，可查看异常数据指标，并结合实际业务情况进行对比。

例如：URL 重复性是1，会话次数100次分钟，UA 滥用等，就需要结合业务是否有访问相同的请求或者是代理等业务，如果没有就说明有人恶意攻击。那么就可以根据以下方式查看并配置拦截策略。

### 分析案例
1. 登录 [Web 应用防火墙控制台](https://console.cloud.tencent.com/guanjia/tea-botconfig)，在左侧导航栏中，选择**BOT 流量分析**。
2. 在 BOT流量分析页面，左上角选择需要防护的域名，选择所需访问源，目前根据展示，能看到该 IP 请求速度很快，URL 单一，并且是 IDC 类。
![](https://qcloudimg.tencent-cloud.cn/raw/8ff4e8e7e42a97d9d140a6ff3dfeb84d.png)
3. 单击**查看详情**，通过基础会话信息可以看出，会话速度平均次数，总次数。也可以直接根据该条件进行设置。
![](https://qcloudimg.tencent-cloud.cn/raw/0df8e38b430747acd5ce198d475afa50.png)
4. 在威胁情报页面，可以根据情报数据判断该 IP 是否有正常用户使用过。
![](https://qcloudimg.tencent-cloud.cn/raw/175eafa0efa18d578a688ab9764de774.png)
5. 在请求特征信息页面，可以查看请求详情。
![](https://qcloudimg.tencent-cloud.cn/raw/8eb574df138e42f7fdbf51acb23e495a.png)

### 策略配置
1. 登录 [Web 应用防火墙控制台](https://console.cloud.tencent.com/guanjia/tea-botconfig)，在左侧导航栏中，选择**配置中心** > **BOT 与业务安全**。
2. 在 BOT 与业务安全页面，左上角选择需要防护的域名，单击 **BOT 管理**。
![](https://qcloudimg.tencent-cloud.cn/raw/642d93faac4b01d62cf0b84583318040.png)
4. 单击某场景配置页，单击**自定义规则**。
3. 在自定义规则页面，单击**添加配置**，根据上述分析，将设置 URL 重复比大于0.7（70%在这过程中，除该数据外没有大于70%的），将会话速度设置为大于500次分钟，单击**确定**。
![](https://qcloudimg.tencent-cloud.cn/raw/eb7644dd8145317899c7746da1f74853.png)
>!目前在创建 BOT 场景化时，已经根据场景类型内置相应场景的自定义规则集。
