---
title: "什么是CDN"
date: 2020-08-04T18:17:15+08:00
draft: false
---

转载于：https://www.cloudflare.com/zh-cn/learning/cdn/what-is-a-cdn/
##### 什么是CDN？
内容交付网络（CDN）是指一组在地理上分散的服务器，它们协同工作以提供互联网内容的快速交付。

CDN允许快速转移加载互联网内容所需的资产，包括HTML页面、javascript 文件、样式表、图像和视频。 CDN服务的受欢迎程度持续增长。如今，大多数网页流量都通过CDN提供服务，包括来自Facebook、奈飞和亚马逊等主要网站的流量。

正确配置的 CDN 还可帮助保护网站免受某些常见的恶意攻击，例如分布式拒绝服务（DDOS）攻击 。

##### CDN是否与网络主机相同？
虽然 CDN 不承载内容，也不能取代对适当网页托管的需求，但它确实有助于在网络边缘缓存内容，从而提高了网站性能。许多网站很难通过传统的主机服务满足其性能需求，这就是为什么他们选择 CDN 的原因。

通过利用缓存来减少托管带宽， 帮助防止服务中断 ，以及提高安全性 ，CDN是为减轻传统网页托管所导致的一些主要痛点的流行选择。

##### 使用CDN有什么好处？
尽管使用CDN的好处取决于互联网属性的大小和需求，但对于大多数用户而言，主要优势有以下四个不同的组成部分：

缩短网站加载时间 – 通过使用附近的CDN服务器（以及其他优化措施），将内容分发到网站访问者附近，访问者将能体验到更快的页面加载时间。由于访问者更倾向于离开加载缓慢的网站，CDN 可以降低跳出率并增加人们在该网站上停留的时间。换句话说，网站速度越快，意味着更强的用户粘性。

减少带宽成本 – 网站托管的带宽消耗成本是网站的主要费用。通过缓存和其他优化，CDN能够减少源站必须提供的数据量，从而降低网站所有者的托管成本。

增加内容可用性和冗余 – 大流量或硬件故障可能会扰乱正常的网站功能。由于CDN具有分布式特性，因此与许多源站相比，CDN 可以更好地处理更多流量并承受硬件故障。

改善网站安全性 – CDN可以通过提供 DDoS防护、安全证书的改进以及其他优化措施来提高安全性。

##### CDN如何工作？
CDN的核心是连接在一起的服务器网络，其目标是尽可能快速、低价、可靠和安全地交付内容。为了提高速度和连接性，CDN会将服务器放置在不同网络之间的交换点。

这些 互联网交换点（IXP）是不同互联网提供商连接的主要位置，以便彼此提供对来自其不同网络的流量的访问。通过连接到这些高速且高度互连的位置，CDN 提供商可以减少高速数据传递中的成本和传输时间。

除了在 IXP 中放置服务器之外，CDN 还对标准客户端/服务器数据传输进行了诸多优化。 CDN 将数据中心放置在全球的战略位置，以增强安全性，并设计用于承受各种类型的故障和互联网拥塞。

##### 延迟 – CDN如何改善网站加载时间？
关于网站加载内容，用户的耐心会随着网站速度变慢而快速下降。 CDN服务可以通过以下方式帮助减少加载时间：

CDN 的全球分布意味着减少用户与网站资源之间的距离。 CDN 使得用户不必连接到网站源站的所在地，而可以连接到地理位置更近的数据中心 。更少的传输时间意味着更快的服务。

硬件和软件优化，例如有效的负载均衡和固态硬盘驱动器，可以帮助数据更快地到达用户。

CDN可以使用极简化和文件压缩之类的策略来减小文件大小，从而减少传输的数据量。较小的文件意味着更快的加载时间。

CDN还可以通过优化连接重用和启用TLS假开始证书来加快使用 TLS / SSL 的站点。

##### 可靠性和冗余 – CDN如何使网站始终保持在线状态？
对于拥有互联网资产的任何人来说，正常运行时间都是至关重要的组成部分。由于恶意攻击或流行性增加而导致的硬件故障和流量激增，有可能使网页服务器停机并阻止用户访问站点或服务。完善的 CDN 具有可最大程度减少停机时间的多项功能：

负载均衡可在多个服务器之间平均分配网络流量，从而更容易扩展流量的快速增长。
即使一台或多台CDN服务器由于硬件故障而脱机，智能故障切换也可提供不间断的服务；故障转移可以将流量重新分配给其他运行服务器。

如果整个数据中心都遇到技术问题，那么 Anycast 路由会将流量转移到另一个可用的数据中心，以确保没有用户失去对网站的访问权限。

##### 数据安全性 – CDN如何保护数据？
信息安全是CDN不可或缺的一部分。 CDN可以使用新的 TLS / SSL证书保护站点的安全，这将确保高标准的身份验证、加密和完整性。调查围绕CDN的安全问题，并探索可以采取哪些措施安全地交付内容。
