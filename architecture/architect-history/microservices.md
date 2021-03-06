# 微服务时代

:::tip 微服务架构（Microservices）

微服务是一种通过多个小型服务组合来构建单个应用的架构风格，这些服务围绕业务能力而非特定的技术标准来构建。各个服务可以采用不同的编程语言，不同的数据存储技术，运行在不同的进程之中。服务采取轻量级的通讯机制和自动化的部署机制实现通讯与运维。

:::

“微服务”这个技术名词最早在2005年就已经被提出，它是由Peter Rodgers博士在2005年度的云计算博览会（Web Services Edge 2005）上首次使用，当时的说法是“Micro-Web-Service”，指的是一种专注于单一职责的、语言无关的、细粒度Web服务（Granular Web Services）。“微服务”一词并不是Peter Rodgers直接凭空创造出来的概念，初生的微服务可以说是SOA发展时催生的产物，就如同EJB推广过程中催生了Spring和Hibernate那样。这一阶段的微服务是作为一种SOA的轻量化的补救方案而被提出的。时至今日，在英文版的维基百科上，仍然将微服务定义为一种SOA的变种形式，所以微服务在最初阶段与SOA、Web Service这些概念有所牵扯也完全可以理解，但现在来看，维基百科对微服务的定义已经颇有些过时了。

:::quote What is microservices 

Microservices is a software development technique — a variant of the service-oriented architecture (SOA) structural style.

:::right

 —— Wikipedia，[Microservices](https://en.wikipedia.org/wiki/Microservices) 

:::

微服务的概念提出后，将近10年的时间里面，都并没有受到太多的追捧，如果只是对现有SOA架构的修修补补，确实是难以唤起广大技术人员的更多激情了。不过，在这10年时间里，微服务本身也在思考、蜕变。2012年，在波兰克拉科夫举行的“33rd Degree Conference”大会上，Thoughtworks首席咨询师James Lewis做了题为《[Microservices - Java, the Unix Way](http://2012.33degree.org/talk/show/67)》的主题演讲，其中提到了单一服务职责、[康威定律](https://en.wikipedia.org/wiki/Conway%27s_law)、自动扩展、领域驱动设计等原则，却只字未提SOA，反而提倡应该重拾Unix的设计哲学（The Unix Philosophy），这点仿佛与笔者在前一节所说的“初心与自省”在遥相呼应。微服务已经迫不及待地要脱离SOA的附庸，成为一种独立的架构风格，也许，还将会是SOA的革命者。

微服务真正的崛起是在2014年，相信阅读此文的大多数读者，也是从Martin Flower与James Lewis合写的文章《[Microservices:a definition of this new architectural term](https://martinfowler.com/articles/microservices.html)》中首次了解到微服务的，并不是指各位一定读过这篇文章，或者准确地说，今天各位所了解的“微服务”是这篇文章中提出的“微服务”。在此文中，定义了现代微服务的概念：“**微服务是一种通过多个小型服务组合来构建单个应用的架构风格，这些服务围绕业务能力而非特定的技术标准来构建。各个服务可以采用不同的编程语言，不同的数据存储技术，运行在不同的进程之中。服务采取轻量级的通讯机制和自动化的部署机制实现通讯与运维**”。此外，文中给出了微服务的九个核心的业务与技术特征，包括：

- **围绕业务能力构建**（Organized around Business Capabilities），这里再次强调了康威定律的重要性
- **分散治理**（Decentralized Governance），这是表达“谁家孩子谁来管”的意思，服务对应的开发团队有直接对服务运行质量负责的责任，也有着不受干预地掌控服务各个方面的权力，譬如选择与其他服务异构的技术来实现自己的服务
- **可独立替换升级的组件**（Componentization via Services），之所以通过“服务”（Service）而不是“类库”（Library）来构建组件，就是为了获得独立升级替换的能力
- **产品化思维**（Products not Projects），避免把软件研发视作要完成某种功能，而是视作一种持续改进、提升的过程
- **数据去中心化**（Decentralized Data Management），提倡数据按领域分散管理、更新、维护、存储
- **基础设施自动化**（Infrastructure Automation），由于服务变多且分散，微服务对CI/CD等基础设施的依赖程度更高，这一点在后续出现的“云原生”概念中，甚至被提升到与微服务本身平行的程度
- **轻量级通讯机制**（Smart Endpoints and Dumb Pipes），弱管道（Dumb Pipes）直接指名道姓地批评ESB那种复杂而刻板的管道通讯机制
- **容错性设计**（Design for Failure），不再虚幻地追求服务永远稳定，而是接受服务会出错的现实，笔者认为这是微服务最大的价值所在，也是这部开源文档标题“The Fenix Project”的含义
- **演进式设计**（Evolutionary Design），承认要设计一个靠谱的微服务，对架构者的能力与经验要求会比单体系统更高，因此建议依赖微服务所获得的灵活性，在有必要“微服务”的地方再进行“微服务”处理

此文中定义的微服务已经明确地与SOA划清了界线，拒绝再贴上任何SOA的标签。如此，微服务的概念才算是一种真正丰满、独立、具体的架构风格，为它在未来的几年时间里如明星一般闪耀崛起于技术舞台铺下了厚实基础。

:::quote Microservices and SOA

This common manifestation of SOA has led some microservice advocates to reject the SOA label entirely, although others consider microservices to be one form of SOA , perhaps service orientation done right. 

:::right

—— Martin Flower / James Lewis，[Microservices](https://martinfowler.com/articles/microservices.html)

:::

从以上微服务的定义和特征中还可以明显地感觉到，微服务是相对自由的架构风格，摒弃了几乎所有可以抛弃的约束和规定，提倡以“实践标准”代替“规范标准”。可是，如果没有了统一的规范和约束，以前SOA所解决的那些分布式服务的问题，不也就一下子都重新都出现了吗？的确如此，服务的注册发现、跟踪治理、负载均衡、故障隔离、认证授权、伸缩扩展、传输通讯、事务处理，等等，这些问题，微服务中不再会有统一的解决方案，即使只讨论Java范围内会使用到的微服务，光一个服务间通讯问题，可以列入解决方案的候选清单的就有：RMI（Sun/Oracle）、Thrift（Facebook）、Dubbo（阿里巴巴）、gRPC（Google）、Motan2（新浪）、Finagle（Twitter）、brpc（百度）、Arvo（Hadoop）、JSON-RPC、REST，等等；光一个服务发现问题，可以选择的就有：Eureka（Netflix）、Consul（HashiCorp）、Nacos（阿里巴巴）、Zookeeper（Apache）、etcd（CoreOS）、CoreDNS（CNCF），等等。其他领域的情况也是与此类似，总之，完全是八仙过海，各显神通的局面。

微服务所带来的自由是一把双刃开锋的宝剑，当软件架构者拿起这把宝剑，一刃指向SOA定下的复杂技术标准，将选择的权力夺回的同一时刻，另外一刃也正朝向着自己映出冷冷的寒光。微服务时代中，软件研发本身的复杂度应该说是有所降低，一个简单服务，并不见得就会同时面临分布式中所有的问题，也就没有必要背上SOA那百宝袋般沉重的技术包袱。需要解决什么问题，就引入什么工具；团队熟悉什么技术，就使用什么框架。此外，像Spring Cloud这样的胶水式的全家桶工具集，通过一致的接口、声明和配置，进一步屏蔽了源自于具体工具、框架的复杂性，降低了在不同工具、框架之间切换的成本，所以，作为一个普通的服务开发者，作为一个“螺丝钉”式的程序员，微服务架构是友善的。可是，微服务对架构者是满满的恶意，对架构能力要求已提升到史无前例的程度，笔者在这部文档的多处反复强调过，技术架构者的第一职责就是做决策权衡，有利有弊才需要决策，有取有舍才需要权衡，如果架构者本身的知识面不足以覆盖所需要决策的内容，不清楚其中利弊，恐怕也就无可避免地陷入选择困难症的困境之中。

微服务时代充满着自由的气息，微服务时代充斥着迷茫的选择。软件架构不会止步于自由，微服务仍不是架构探索终点，如果有下一个时代，我希望是信息系统能同时拥有微服务的自由权利，围绕业务能力构建自己的服务而不受技术规范管束，但同时又不必以承担自行解决分布式的问题的责任为代价。管他什么利弊权衡！小孩子才做选择题，成年人全部都要！