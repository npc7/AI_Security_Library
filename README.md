AI_And_Web_Security_Library

Ai与Web安全相关资料的总结库，包括认为写的比较好的一些博客、项目、数据等

## 资料

1. [华为AI安全白皮书]https://github.com/AnchoretY/AI_And_Web_Security_Library/blob/master/book/ai-security-white-paper-cn.pdf





## Webshell 

### 项目

#### 1. [WebShell-Detector](https://github.com/flykingmz/WebShell-Detector)

​	全称《基于深度学习与集成学习的可配置webshell检测系统》，是08年大学生信息安全竞赛的一个Webshell检测系统，主要是是**针对Webshell文件**进行检测，采用的方式基本上是比较传统的**静态检测（正则+机器学习）+动态检测技术（深度学习）**的进行检测，然后使用**加权的方式对模型进行组合**，是一个比较基础的实现。

2. #### [CloudWalker](https://github.com/chaitin/cloudwalker)

   **长亭科技在线的Webshell文件检测项目**，可以本地检测也可以线上检测。

### 数据集

1. #### [webshell-sample](https://github.com/ysrc/webshell-sample)

   各种webshell文件数据，根据webshell文件类型进行分类，量很大。



## XSS

###  项目



### 数据集

1. #### [xss_payload_2016](https://github.com/7ioSecurity/XSS-Payloads)

​	纯xss payload总结，不带任何其他信息

2. #### [xssdb](http://xssdb.net/)

​	一个xss payload网络数据库，数据量比较大而且除payload外，还包含了每条payload的相关信息，例如注入名称、描述等，并支持以csv、txt、json等多种形式进行导出。

### 检测规则



## DGA域名检测



### Paper&Blog

1. Hyrum S. Anderson, Jonathan Woodbridge, Bobby Filar. "DeepDGA: Adversarially-Tuned Domain Generation and Detection" [[pdf\]](https://arxiv.org/abs/1610.01969),6 Oct 2016 **(生成对抗网络，DGA检测)** 
2. Jonathan Woodbridge, Hyrum S. Anderson, Anjum Ahuja, Daniel Grant. "Predicting Domain Generation Algorithms with Long Short-Term Memory Networks" [[pdf\]](https://arxiv.org/abs/1611.00791),2 Nov 2016 **(LSTM,DGA检测)**



## 入侵检测

### 项目

1. #### [Seq2Seq for Web Attack Detection](https://github.com/flykingmz/seq2seq-web-attack-detection)

​	使用某银行应用中的数据集进行HTTP Web攻击检测模型项目。该项目检测对象为**HTTP流量**，具有的一个比较特别的点是在**训练阶段不使用攻击样本，而只使用正常样本**，是一种类似异常检测思路，而不是大部分人使用的分类的方式。

在该文章中提出Web攻击检测的基本问题：

​	1. 类别的选择问题。选定一个	



改文章中也采用了和我们系统中一样的字符级别的embedding,使用attention机制使模型具备了可解释性，模型输包含标签和每个字符的注意力系数。

声称与人类专家的工作方式相同



2. #### [Sharly](https://github.com/SparkSharly/Sharly)

​	**基于HMM的Web异常参数检测项目**。



### 数据集

1. ####  [Vulnbank_dataset](https://github.com/AnchoretY/AI_And_Web_Security_Library/tree/master/dataset/vulnbank_dataset)

​	KDD大赛的一个竞赛项目，主要目的是使用机器学习得手段建立一个入侵检测器。其中的入侵行为主要包括：DDOS、密码暴力破解、缓冲区溢出、扫描等多种攻击行为。**数据格式为一些基本的统计信息**。

2. #### [KDD CUP 1999 Data]()

3. #### [SecRepo.com](https://www.secrepo.com/)

​	一个总结各种与安全数据相关的数据集的网站。**数据格式也非常多样**。





### Blog

1. ####[Web日志安全分析系统实践](https://xz.aliyun.com/t/2136#toc-110)

   ​	该博客一个比较全面的HTTP流量日志分析系统，是一个比较详细的系统设计，检测部分包括了规则匹配、统计特征检测、机器学习检测三种方法，**机器学习部分采用了tf-idf+ngram等方式进行向量化然后使用SVM进行检测**。是一种非常基础非常简单的安全和AI结合的实践。

2. #### [数据科学在Web威胁感知中的应用](https://www.jianshu.com/p/942d1beb7fdd)

   楚安大佬在AI安全领域的一篇非常经典的博客。

3. #### [学点算法搞安全之HMM](https://www.freebuf.com/column/132796.html)

   ​	兜哥写的一篇关于**HMM用于Web参数异常检测**的一篇论述性的文章，并附带了一些基本实现。HMM应用于Web参数异常检测核心思想为使用大量白样本构建HMM模型，使模型能够正确识别正常参数的形式，然后对于新的请求参数使用该HMM模型进行判别，根据得出的概率值判断是否为异常参数。在实际使用中存在的问题也比较明显，**HMM模型要每个URL都要训练一个HMM模型，因此检测的成本巨大，只能用于小站点的防护。**

4. #### [机器学习在Web攻击检测中的应用](https://mp.weixin.qq.com/s/Fuu70rPWyYP5mQSOK3J9_Q)

     该博客为写成在**将机器学习应用到携程的恶意攻击检测系统中的企业实践**，整个文章论述了将机器学习应用到入侵检测系统中的整体思路以及遇到的各种问题及解决方法。里面一些比较精彩的点：

   - 该文章**将机器学习模型主要用来做效率优化**，构建低误报的模型来进行数据的过滤，然后再使用正则进行确定是否为攻击。

   - 整个系统先使用白名单机制来过滤掉97%的流量。在**param的value部分不包含符号、控制符以及白名单IP的流量都可直接视为白数据**。

   - 机器学习和正则都判为黑的发送到**自动化验证系统验证能否攻击成功**。

5. #### [企业安全数据分析实践与思考]()

      阿里cdxy大神关于阿里巴巴在将数据分析技术应用到企业安全中的一些思路的分享ppt，里面有一些做法还是比较特别的。

### Paper

1. Davide, Ariu, and, et al. "HMMPayl: An intrusion detection system based on Hidden Markov Models[J]" [pdf](https://www.sciencedirect.com/science/article/pii/S0167404811000022).**(HMM用于Web参数检测**)

   



## 渗透测试

### 项目

1. #### [GyoiThon](https://github.com/gyoisamurai/GyoiThon)

   ​	一款**基于机器学习得自动化渗透测试工具**，该工具可以根据**响应包中的cookie、Etag、特定HTML标签等方面训练一个机器学习模型识别出服务器端软件**，然后调用**Metasploit**进行渗透测试。这里还有一篇详细的[使用介绍](https://www.freebuf.com/sectool/173476.html)

2. #### [Deep Exploit](https://github.com/13o-bbr-bbq/machine_learning_security/tree/master/DeepExploit)

   使用深度强化学习进行自动化渗透测试工具。

### Paper









