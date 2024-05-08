# DNS-tunnelling-detection-by-fusing-encoding-feature-and-behavioral-feature

## 1. 整体介绍(Overview)
这是文章《DNS tunnelling detection by fusing encoding feature and behavioral feature》 (DOI: https://doi.org/10.1016/j.cose.2023.103357) 用到的数据集，本数据集由天津大学可信软件实验室联合企业内部安全实验室共同构建。  
This is the article "DNS tunneling detection by fusing encoding feature and behavioral feature" (DOI: https://doi.org/10.1016/j.cose.2023.103357 ）The dataset used was jointly constructed by the Trusted Software Laboratory of Tianjin University and the Internal Security Laboratory of the enterprise.


## 2. 数据集说明(Dataset description)
这里公开的数据集包含论文工作中的基础数据集和泛化测试集两部分。我们采用了pcap这类格式来存储这些数据，同时这些pcap文件中的IP仅为独立组网环境中的IP，与现实网络中的IP无关。  
The publicly available dataset here includes two parts: the basic dataset and the generalization test set used in the paper work. We use formats like PCAP to store this data, and the IP addresses in these PCAP files are only those in independent networking environments, independent of the IP addresses in the real network.

### 2.1 基础数据集说明(Dataset description)
我们使用透明证书查询Alexa排名前1K网站的子域名，来获取10万个可信站点子网站，并通过在校内实验室环境中访问这些网站来采集良性的DNS样本。同时为了保证样本的随机性，我们还对实验室网络中的DNS流量使用手动筛选的方式，来扩展我们的良性样本集。  
We use transparent certificates to query the subdomains of Alexa's top 1K websites, in order to obtain 100000 trusted website subdomains, and collect benign DNS samples by accessing these websites in the campus laboratory environment. At the same time, in order to ensure the randomness of the samples, we also manually filtered the DNS traffic in the laboratory network to expand our benign sample set.
 

我们采用了开源贡献的DNS隧道流量，作为我们基本数据集中恶意样本部分。该流量是在模拟环境中使用8种不同的DNS隧道工具收集的，其包含iodine, dnscat2, dns2tcp, ozymandns, dnshell v1.7, cobaltstrike, det, dnsexfiltrator的上行、下行方向流量。  
We adopted DNS tunnel traffic contributed by open source as the malicious sample portion of our basic dataset. This traffic was collected using 8 different DNS tunneling tools in a simulated environment, including uplink and downlink traffic of iodine, dnscat2, dns2TCP, ozymandns, dnshell v1.7, cobaltstrike, det, and dnsexfiltrator.

### 2.2 泛化测试数据集说明(Dataset description)
基础良性样本数据集是从高度限制的校园环境中获取的，该环境很难代表需要与DNS隧道对抗的环境。为了在更复杂的环境中测试模型的鲁棒性，我们从一家安全企业的办公网络中获取了手动筛选的DNS数据包，作为良性样本的泛化测试集。  
The basic benign sample dataset was obtained from a highly restricted campus environment, which is difficult to represent the environment that needs to compete with DNS tunnels. To test the robustness of the model in more complex environments, we obtained manually filtered DNS packets from the office network of a secure enterprise as a generalization test set for benign samples.

基础恶意样本数据集中的大多数DNS隧道数据包都是心跳数据包，用于维护连接，没有实际的攻击负载。为了更好地模拟真实的攻击，我们收集了150个黑客常用的命令，用于Linux和Windows系统上的内网渗透，并在不同的DNS隧道工具中使用这些命令来获取恶意样本，用于我们更具挑战性的泛化测试。   
Most DNS tunnel packets in the basic malicious sample dataset are heartbeat packets used to maintain connections without actual attack load. In order to better simulate real attacks, we collected 150 commonly used commands by hackers for intranet penetration on Linux and Windows systems, and used these commands in different DNS tunneling tools to obtain malicious samples for our more challenging generalization testing.

## 3. 引用(Reference)
如使用该数据集，请添加对我们文章的引用。  
If used this dataset, please cite our paper.  
```
Tu Y , Liu S , Sun Q .DNS tunnelling detection by fusing encoding feature and behavioral feature[J].Computers & Security, 2023:132.
```

## 4. 其他说明(Other instructions)
这些pcap文件中可能包含少量非DNS协议的packets，在解析的时候需注意过滤。  
These pcap files may contain a small number of packets of non-DNS protocols, so please filter them when parsing. 
