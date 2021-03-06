
![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216161253.png)



IP 在 TCP/IP 参考模型中处于第三层，也就是⽹络层。

⽹络层的主要作⽤是：实现主机与主机之间的通信，也叫点对点（end to end）通信。
 

![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216161632.png)


### 4.1 ⽹络层与数据链路层有什么关系呢？

有的⼩伙伴分不清 IP（⽹络层） 和 MAC （数据链路层）之间的区别和关系。

其实很容易区分，在上⾯我们知道 IP 的作⽤是主机之间通信⽤的，⽽ MAC 的作⽤则是实现「直连」的两个设备
之间通信，⽽ IP 则负责在「没有直连」的两个⽹络之间进⾏通信传输。


举个⽣活的栗⼦，⼩林要去⼀个很远的地⽅旅⾏，制定了⼀个⾏程表，其间需先后乘坐⻜机、地铁、公交⻋才能抵
达⽬的地，为此⼩林需要买⻜机票，地铁票等。

⻜机票和地铁票都是去往特定的地点的，每张票只能够在某⼀限定区间内移动，此处的「区间内」就如同通信⽹络
中数据链路。

在区间内移动相当于数据链路层，充当区间内两个节点传输的功能，区间内的出发点好⽐源 MAC 地址，⽬标地点
好⽐⽬的 MAC 地址。


整个旅游⾏程表就相当于⽹络层，充当远程定位的功能，⾏程的开始好⽐源 IP，⾏程的终点好⽐⽬的 IP 地址。

![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216164018.png)

如果⼩林只有⾏程表⽽没有⻋票，就⽆法搭乘交通⼯具到达⽬的地。相反，如果除了⻋票⽽没有⾏程表，恐怕也很
难到达⽬的地。因为⼩林不知道该坐什么⻋，也不知道该在哪⾥换乘。


因此，只有两者兼备，既有某个区间的⻋票⼜有整个旅⾏的⾏程表，才能保证到达⽬的地。与此类似，计算机⽹络
中也需要「数据链路层」和「⽹络层」这个分层才能实现向最终⽬标地址的通信。


还有 要⼀点，旅⾏途中我们虽然不断变化了交通⼯具，但是旅⾏⾏程的起始地址和⽬的地址始终都没变。其实，
在⽹络中数据包传输中也是如此，源IP地址和⽬标IP地址在传输过程中是不会变化的，只有源 MAC 地址和⽬标
MAC ⼀直在变化。

### 4.2 IP 地址的基础知识
在 TCP/IP ⽹络通信时，为了保证能正常通信，每个设备都需要配置正确的 IP 地址，否则⽆法实现正常的通信。

IP 地址（IPv4 地址）由 32 位正整数来表示，IP 地址在计算机是以⼆进制的⽅式处理的。


⽽⼈类为了⽅便记忆采⽤了**点分⼗进制**的标记⽅式，也就是将 32 位 IP 地址以每 8 位为组，共分为 4 组，每组以.隔开，再将每组转换成⼗进制。


![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216164330.png)

也就说，最⼤允许 43 亿台计算机连接到⽹络。

实际上，IP 地址并不是根据主机台数来配置的，⽽是以⽹卡。像服务器、路由器等设备都是有 2 个以上的⽹卡，也就是它们会有 2 个以上的 IP 地址。

![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216164656.png)



因此，让 43 亿台计算机全部连⽹其实是不可能的，更何况 IP 地址是由「⽹络标识」和「主机标识」这两个部分组成的，所以实际能够连接到⽹络的计算机个数更是少了很多。

(⼀种可以更换 IP 地址的技术 NAT ，使得可连接计算机数超过 43 亿台)

### 4.3 IP 地址的分类
IP 地址分类成了 5 种类型，分别是 A 类、B 类、C 类、D 类、E 类。

![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216165824.png)

上图中⻩⾊部分为分类号，⽤以区分 IP 地址类别。


#### 什么是 A、B、C 类地址？

其中对于 A、B、C 类主要分为两个部分，分别是⽹络号和主机号。这很好理解，好⽐⼩林是 A ⼩区 1 栋 101 号，你是 B ⼩区 1 栋 101 号。

我们可以⽤下⾯这个表格， 就能很清楚的知道 A、B、C 分类对应的地址范围、最⼤主机个数。


![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216170134.png)

#### A、B、C 分类地址最⼤主机个数是如何计算的呢？
最⼤主机个数，就是要看主机号的位数，如 C 类地址的主机号占 8 位，那么 C 类地址的最⼤主机个数：

![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173152.png)

为什么要减 2 呢？
因为在 IP 地址中，有两个 IP 是特殊的，分别是主机号全为 1 和 全为 0 地址。


![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173156.png)

- 主机号全为 1 指定某个⽹络下的所有主机，⽤于⼴播

- 主机号全为 0 指定某个⽹络

因此，在分配过程中，应该去掉这两种情况。

#### ⼴播地址⽤于什么？
⼴播地址⽤于在**同⼀个链路中相互连接的主机之间发送数据包。**

学校班级中就有⼴播的例⼦，在准备上课的时候，通常班⻓会喊：“上课， 全体起⽴！”，班⾥的同学听到这句话是不是全部都站起来了？这个句话就有⼴播的含义。

当主机号全为 1 时，就表示该⽹络的⼴播地址。例如把 172.20.0.0/16 ⽤⼆进制表示如下：

10101100.00010100.00000000.00000000

将这个地址的主机部分全部改为 1，则形成⼴播地址：

10101100.00010100. 11111111.11111111


再将这个地址⽤⼗进制表示，则为 172.20.255.255 。


⼴播地址可以分为本地⼴播和直接⼴播两种。

- **在本⽹络内⼴播的叫做本地⼴播**。例如⽹络地址为 192.168.0.0/24 的情况下，⼴播地址是 192.168.0.255 。因为这个⼴播地址的 IP 包会被路由器屏蔽，所以不会到达 192.168.0.0/24 以外的其他链路上。



- **在不同⽹络之间的⼴播叫做直接⼴播**。例如⽹络地址为 192.168.0.0/24 的主机向 192.168.1.255/24 的⽬标地址发送 IP 包。收到这个包的路由器，将数据转发给 192.168.1.0/24，从⽽使得所有
192.168.1.1~192.168.1.254 的主机都能收到这个包（由于直接⼴播有⼀定的安全问题，多数情况下会在路由器上设置为不转发。） 。

![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173158.png)

![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173204.png)


#### 什么是 D、E 类地址？
⽽ D 类和 E 类地址是没有主机号的，所以不可⽤于主机 IP，D 类常被⽤于多播，E 类是预留的分类，暂时未使⽤。

![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173208.png)


#### 多播地址⽤于什么？

多播⽤于将包发送给特定组内的所有主机。

还是举班级的栗⼦，⽼师说：“最后⼀排的同学，上来做这道数学题。”，⽼师指定的是最后⼀排的同学，也就是多播的含义了。

由于⼴播⽆法穿透路由，若想给其他⽹段发送同样的包，就可以使⽤可以穿透路由的多播。



![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173211.png)

多播使⽤的 D 类地址，其前四位是 1110 就表示是多播地址，⽽剩下的 28 位是多播的组编号。

从 224.0.0.0 ~ 239.255.255.255 都是多播的可⽤范围，其划分为以下三类：

- 224.0.0.0 ~ 224.0.0.255 为预留的组播地址，只能在局域⽹中，路由器是不会进⾏转发的。

- 224.0.1.0 ~ 238.255.255.255 为⽤户可⽤的组播地址，可以⽤于 Internet 上。

- 239.0.0.0 ~ 239.255.255.255 为本地管理组播地址，可供内部⽹在内部使⽤，仅在特定的本地范围内有效。

### 4.4 IP 分类的优点
不管是路由器还是主机解析到⼀个 IP 地址时候，我们判断其 IP 地址的⾸位是否为 0，为 0 则为 A 类地址，那么就能很快的找出⽹络地址和主机地址。

其余分类判断⽅式参考如下图：

![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173215.png)



![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173218.png)


所以，这种分类地址的优点就是简单明了、选路（基于⽹络地址）简单。


### 4.5  IP 分类的缺点

##### 缺点⼀

**同⼀⽹络下没有地址层次**，⽐如⼀个公司⾥⽤了 B 类地址，但是可能需要根据⽣产环境、测试环境、开发环境来划分地址层次，⽽这种 IP 分类是没有地址层次划分的功能，所以这就**缺少地址的灵活性。**


##### 缺点二

A、B、C类有个尴尬处境，就是不能很好的与现实⽹络匹配。

- C 类地址能包含的最⼤主机数量实在太少了，只有 254 个，估计⼀个⽹吧都不够⽤。

- ⽽ B 类地址能包含的最⼤主机数量⼜太多了，6 万多台机器放在⼀个⽹络下⾯，⼀般的企业基本达不到这个规模，闲着的地址就是浪费。

这两个缺点，都可以在 **CIDR** ⽆分类地址解决。


###### ⽆分类地址 CIDR
正因为 IP 分类存在许多缺点，所以后⾯提出了⽆分类地址的⽅案，即 CIDR 。

这种⽅式不再有分类地址的概念，**32 ⽐特的 IP 地址被划分为两部分，前⾯是⽹络号，后⾯是主机号。**


### 4.6 怎么划分⽹络号和主机号的呢？

表示形式 a.b.c.d/x ，其中 /x 表示前 x 位属于⽹络号， x 的范围是 0 ~ 32 ，这就使得 IP 地址更加具有灵活性。

⽐如 10.100.122.2/24，这种地址表示形式就是 CIDR，/24 表示前 24 位是⽹络号，剩余的 8 位是主机号。

![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173221.png)


还有另⼀种划分⽹络号与主机号形式，那就是 **⼦⽹掩码**，掩码的意思就是掩盖掉主机号，剩余的就是⽹络号。

将⼦⽹掩码和 IP 地址按位计算 AND，就可得到⽹络号。

![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173223.png)


### 4.7 为什么要分离⽹络号和主机号？
因为两台计算机要通讯，⾸先要判断是否处于同⼀个⼴播域内，即⽹络地址是否相同。如果⽹络地址相同，表明接受⽅在本⽹络上，那么可以把数据包直接发送到⽬标主机。

路由器寻址⼯作中，也就是通过这样的⽅式来找到对应的⽹络号的，进⽽把数据包转发给对应的⽹络内。

![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173226.png)


### 4.8  怎么进⾏⼦⽹划分？
在上⾯我们知道可以通过⼦⽹掩码划分出⽹络号和主机号，那实际上子网掩码还有一个作用，那就是**划分子网。**

⼦⽹划分实际上是将主机地址分为两个部分：**⼦⽹⽹络地址和⼦⽹主机地址**。形式如下：

![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173230.png)


假设对 C 类地址进⾏⼦⽹划分，⽹络地址 192.168.1.0，使⽤⼦⽹掩码 255.255.255.192 对其进⾏⼦⽹划分。

C 类地址中前 24 位是⽹络号，最后 8 位是主机号，根据⼦⽹掩码可知从 8 位主机号中借⽤ 2 位作为⼦⽹号。


![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173233.png)

由于⼦⽹⽹络地址被划分成 2 位，那么⼦⽹地址就有 4 个，分别是 00、01、10、11，具体划分如下图：

![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173236.png)


![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173239.png)



![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173242.png)

划分后的 4 个⼦⽹如下表格：

![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173246.png)



### 4.9 公有 IP 地址与私有 IP 地址
在 A、B、C 分类地址，实际上有分公有 IP 地址和私有 IP 地址。

![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173250.png)


平时我们办公室、家⾥、学校⽤的 IP 地址，⼀般都是私有 IP 地址。因为这些地址允许组织内部的 IT ⼈员⾃⼰管理、⾃⼰分配，⽽且可以重复。因此，你学校的某个私有 IP 地址和我学校的可以是⼀样的。


就像每个⼩区都有⾃⼰的楼编号和⻔牌号，你⼩区家可以叫 1 栋 101 号，我⼩区家也可以叫 1 栋 101，没有任何问题。但⼀旦出了⼩区，就需要带上中⼭路 666 号（公⽹ IP 地址），是国家统⼀分配的，不能两个⼩区都叫中⼭路 666。

所以，公有 IP 地址是有个组织统⼀分配的，假设你要开⼀个博客⽹站，那么你就需要去申请购买⼀个公有 IP，这样全世界的⼈才能访问。并且公有 IP 地址基本上要在整个互联⽹范围内保持唯⼀。

![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173252.png)



### 4.10  公有 IP 地址由谁管理呢？
私有 IP 地址通常是内部的 IT ⼈员管理，公有 IP 地址是由 ICANN 组织管理，中⽂叫「互联⽹名称与数字地址分配机构」。

IANA 是 ICANN 的其中⼀个机构，它负责分配互联⽹ IP 地址，是按州的⽅式层层分配。

![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173255.png)

其中，在中国是由 CNNIC 的机构进⾏管理，它是中国国内唯⼀指定的全局 IP 地址管理的组织


### 4.11 IP 地址与路由控制

IP地址的 **⽹络地址**这⼀部分是 **⽤于进⾏路由控制。**

路由控制表中记录着⽹络地址与下⼀步应该发送⾄路由器的地址。在主机和路由器上都会有各⾃的路由器控制表。

在发送 IP 包时，⾸先要确定 IP 包⾸部中的⽬标地址，再从路由控制表中找到与该地址具有相同⽹络地址的记录，根据该记录将 IP 包转发给相应的下⼀个路由器。如果路由控制表中存在多条相同⽹络地址的记录，就选择相同位数最多的⽹络地址，也就是最⻓匹配。

下⾯以下图的⽹络链路作为例⼦说明：

![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173258.png)

- 主机 A 要发送⼀个 IP 包，其源地址是 10.1.1.30 和⽬标地址是 10.1.2.10 ，由于没有在主机 A 的路由表找到与⽬标地址 10.1.2.10 的⽹络地址，于是包被转发到默认路由（路由器 1 ）

- 路由器 1 收到 IP 包后，也在路由器 1 的路由表匹配与⽬标地址相同的⽹络地址记录，发现匹配到了，于是就把 IP 数据包转发到了 10.1.0.2 这台路由器 2

- 路由器 2 收到后，同样对⽐⾃身的路由表，发现匹配到了，于是把 IP 包从路由器 2 的 10.1.2.1 这个接⼝出去，最终经过交换机把 IP 数据包转发到了⽬标主机



### 4.12 环回地址会不会流向⽹络？

环回地址是在同⼀台计算机上的程序之间进⾏⽹络通信时所使⽤的⼀个默认地址。

计算机使⽤⼀个特殊的 IP 地址 127.0.0.1 作为环回地址。与该地址具有相同意义的是⼀个叫做localhost 的主机名。使⽤这个 IP 或主机名时，数据包不会流向⽹络。


### 4.13 IP 分⽚与重组
每种数据链路的最⼤传输单元 MTU 都是不相同的，如 FDDI 数据链路 MTU 4352、以太⽹的 MTU 是 1500 字节等。

每种数据链路的 MTU 之所以不同，是因为每个不同类型的数据链路的使⽤⽬的不同。使⽤⽬的不同，可承载的MTU 也就不同。

其中，我们最常⻅数据链路是以太⽹，它的 MTU 是 **1500** 字节。

那么当 IP 数据包⼤⼩⼤于 MTU 时， IP 数据包就会被分⽚。

经过分⽚之后的 IP 数据报在被重组的时候，只能由⽬标主机进⾏，路由器是不会进⾏重组的。

假设发送⽅发送⼀个 4000 字节的⼤数据报，若要传输在以太⽹链路，则需要把数据报分⽚成 3 个⼩数据报进⾏传输，再交由接收⽅重组成⼤数据报。


![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173301.png)

在分⽚传输中，⼀旦某个分⽚丢失，则会造成整个 IP 数据报作废，所以 TCP 引⼊了 MSS 也就是在 TCP 层进⾏分⽚不由 IP 层分⽚，那么对于 UDP 我们尽量不要发送⼀个⼤于 MTU 的数据报⽂。



### 4.14 IPv6 基本认识
IPv4 的地址是 32 位的，⼤约可以提供 42 亿个地址，但是早在 2011 年 IPv4 地址就已经被分配完了。

但是 IPv6 的地址是 128 位的，这可分配的地址数量是⼤的惊⼈，说个段⼦ IPv6 可以保证地球上的每粒沙⼦都能被分配到⼀个 IP 地址。

但 IPv6 除了有更多的地址之外，还有更好的安全性和扩展性，说简单点就是 IPv6 相⽐于 IPv4 能带来更好的⽹络体验。

但是因为 IPv4 和 IPv6 不能相互兼容，所以不但要我们电脑、⼿机之类的设备⽀持，还需要⽹络运营商对现有的设备进⾏升级，所以这可能是 IPv6 普及率⽐较慢的⼀个原因。


### 4.15 IPv6 的亮点
IPv6 不仅仅只是可分配的地址变多了，它还有⾮常多的亮点。

- IPv6 可⾃动配置，即使没有 DHCP 服务器也可以实现⾃动分配IP地址，真是便捷到即插即⽤啊。

- IPv6 包头包⾸部⻓度采⽤固定的值 40 字节，去掉了包头校验和，简化了⾸部结构，减轻了路由器负荷，⼤⼤提⾼了传输的性能。

- IPv6 有应对伪造 IP 地址的⽹络安全功能以及防⽌线路窃听的功能，⼤⼤提升了安全性。

### 4.16 IPv6 地址的标识⽅法

IPv4 地址⻓度共 32 位，是以每 8 位作为⼀组，并⽤点分⼗进制的表示⽅式。

IPv6 地址⻓度是 128 位，是以每 16 位作为⼀组，每组⽤冒号 「:」 隔开。


![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173304.png)


### 4.17 IPv6 地址的结构

IPv6 类似 IPv4，也是通过 IP 地址的前⼏位标识 IP 地址的种类。

IPv6 的地址主要有以下类型地址：

- 单播地址，⽤于⼀对⼀的通信

- 组播地址，⽤于⼀对多的通信

- 任播地址，⽤于通信最近的节点，最近的节点是由路由协议决定

- 没有⼴播地址


![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173307.png)

### 4.18 IPv6 单播地址类型

对于⼀对⼀通信的 IPv6 地址，主要划分了三类单播地址，每类地址的有效范围都不同。
- 在同⼀链路单播通信，不经过路由器，可以使⽤**链路本地单播地址**，IPv4 没有此类型。

- 在内⽹⾥单播通信，可以使⽤**唯⼀本地地址**，相当于 IPv4 的私有 IP

- 在互联⽹通信，可以使⽤**全局单播地址**，相当于 IPv4 的公有 IP

![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173310.png)

### 4.19 IPv4 ⾸部与 IPv6 ⾸部

IPv4 ⾸部与 IPv6 ⾸部的差异如下图：

![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173313.png)


IPv6 相⽐ IPv4 的⾸部改进：

- 取消了⾸部校验和字段。 因为在数据链路层和传输层都会校验，因此 IPv6 直接取消了 IP 的校验。

- 取消了分⽚/重新组装相关字段。 分⽚与重组是耗时的过程，IPv6 不允许在中间路由器进⾏分⽚与重组，这种操作只能在源与⽬标主机，这将⼤⼤提⾼了路由器转发的速度。

- 取消选项字段。 选项字段不再是标准 IP ⾸部的⼀部分了，但它并没有消失，⽽是可能出现在 IPv6 ⾸部中的「下⼀个⾸部」指出的位置上。删除该选项字段使的 IPv6 的⾸部成为固定⻓度的 40 字节。


### 4.20 IP 协议相关技术

- DNS 域名解析

- ARP 与 RARP 协议

- DHCP 动态获取 IP 地址

- NAT ⽹络地址转换

- ICMP 互联⽹控制报⽂协议

- IGMP 因特⽹组管理协议



#### DNS
我们在上⽹的时候，通常使⽤的⽅式是域名，⽽不是 IP 地址，因为域名⽅便⼈类记忆。
那么实现这⼀技术的就是 DNS 域名解析，DNS 可以将域名⽹址⾃动转换为具体的 IP 地址。

#####  域名的层级关系
DNS 中的域名都是⽤句点来分隔的，⽐如 www.server.com ，这⾥的句点代表了不同层次之间的界限。
在域名中，越靠右的位置表示其层级越⾼。

根域是在最顶层，它的下⼀层就是 com 顶级域，再下⾯是 server.com。

所以域名的层级关系类似⼀个树状结构：

- 根 DNS 服务器

- 顶级域 DNS 服务器（com）

- 权威 DNS 服务器（server.com）


![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173317.png)

根域的 DNS 服务器信息保存在互联⽹中所有的 DNS 服务器中。这样⼀来，任何 DNS 服务器就都可以找到并访问根域 DNS 服务器了。

因此，客户端只要能够找到任意⼀台 DNS 服务器，就可以通过它找到根域 DNS 服务器，然后再⼀路顺藤摸⽠找到位于下层的某台⽬标 DNS 服务器。

##### 域名解析的⼯作流程

浏览器⾸先看⼀下⾃⼰的缓存⾥有没有，如果没有就向操作系统的缓存要，还没有就检查本机域名解析⽂件
hosts ，如果还是没有，就会向 DNS 服务器进⾏查询，查询的过程如下：

- 客户端⾸先会发出⼀个 DNS 请求，问 www.server.com 的 IP 是啥，并发给本地 DNS 服务器（也就是客户端的 TCP/IP 设置中填写的 DNS 服务器地址）。

- 本地域名服务器收到客户端的请求后，如果缓存⾥的表格能找到 www.server.com，则它直接返回 IP 地址。如果没有，本地 DNS 会去问它的根域名服务器：“⽼⼤， 能告诉我 www.server.com 的 IP 地址吗？” 根域名服务器是最⾼层次的，它不直接⽤于域名解析，但能指明⼀条道路。

- 根 DNS 收到来⾃本地 DNS 的请求后，发现后置是 .com，说：“www.server.com 这个域名归 .com 区域管理”，我给你 .com 顶级域名服务器地址给你，你去问问它吧。”

- 本地 DNS 收到顶级域名服务器的地址后，发起请求问“⽼⼆， 你能告诉我 www.server.com
的 IP 地址吗？”

- 顶级域名服务器说：“我给你负责 www.server.com 区域的权威 DNS 服务器的地址，你去问它应该能问到”。

- 本地 DNS 于是转向问权威 DNS 服务器：“⽼三，www.server.com对应的IP是啥呀？” server.com 的权威DNS 服务器，它是域名解析结果的原出处。为啥叫权威呢？就是我的域名我做主。

- 权威 DNS 服务器查询后将对应的 IP 地址 X.X.X.X 告诉本地 DNS。

- 本地 DNS 再将 IP 地址返回客户端，客户端和⽬标建⽴连接。

⾄此，我们完成了 DNS 的解析过程。现在总结⼀下，整个过程我画成了⼀个图。


![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173320.png)

DNS 域名解析的过程蛮有意思的，整个过程就和我们⽇常⽣活中找⼈问路的过程类似，只指路不带路。



#### ARP
在传输⼀个 IP 数据报的时候，确定了源 IP 地址和⽬标 IP 地址后，就会通过主机「路由表」确定 IP 数据包下⼀跳。然⽽，⽹络层的下⼀层是数据链路层，所以我们还要知道「下⼀跳」的 MAC 地址。

由于主机的路由表中可以找到下⼀跳的 IP 地址，所以可以通过 ARP 协议，求得下⼀跳的 MAC 地址。

##### 那么 ARP ⼜是如何知道对⽅ MAC 地址的呢？

简单地说，ARP 是借助 ARP 请求与 ARP 响应两种类型的包确定 MAC 地址的。

![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173323.png)

- 主机会通过⼴播发送 ARP 请求，这个包中包含了想要知道的 MAC 地址的主机 IP 地址。

- 当同个链路中的所有设备收到 ARP 请求时，会去拆开 ARP 请求包⾥的内容，如果 ARP 请求包中的⽬标 IP地址与⾃⼰的 IP 地址⼀致，那么这个设备就将⾃⼰的 MAC 地址塞⼊ ARP 响应包返回给主机。


操作系统通常会把第⼀次通过 ARP 获取的 MAC 地址缓存起来，以便下次直接从缓存中找到对应 IP 地址的 MAC地址。

不过，MAC 地址的缓存是有⼀定期限的，超过这个期限，缓存的内容将被清除。


##### RARP 协议你知道是什么吗？
ARP 协议是已知 IP 地址求 MAC 地址。

RARP 协议是已知 MAC 地址求 IP 地址， 例如将打印机服务器等⼩型嵌⼊式设备接⼊到⽹络时就经常会⽤得到。


通常这需要架设⼀台 RARP 服务器，在这个服务器上注册设备的 MAC 地址及其 IP 地址。然后再将这个设备接⼊到⽹络，接着：

- 该设备会发送⼀条「我的 MAC 地址是XXXX，请告诉我，我的IP地址应该是什么」的请求信息。

- RARP 服务器接到这个消息后返回「MAC地址为 XXXX 的设备，IP地址为 XXXX」的信息给这个设备。

最后，设备就根据从 RARP 服务器所收到的应答信息设置⾃⼰的 IP 地址。

![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173326.png)



#### DHCP
DHCP 在⽣活中我们是很常⻅的了，我们的电脑通常都是通过 DHCP 动态获取 IP 地址，⼤⼤省去了配 IP 信息繁琐的过程。

接下来，我们来看看我们的电脑是如何通过 4 个步骤的过程，获取到 IP 的。

![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173329.png)



![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173332.png)



![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173335.png)

先说明⼀点，DHCP 客户端进程监听的是 68 端⼝号，DHCP 服务端进程监听的是 67 端⼝号。

这 4 个步骤：

- 客户端⾸先发起 **DHCP 发现报⽂（DHCP DISCOVER**） 的 IP 数据报，由于客户端没有 IP 地址，也不知道DHCP 服务器的地址，所以使⽤的是 **UDP ⼴播**通信，其使⽤的⼴播⽬的地址是 255.255.255.255（端⼝67） 并且使⽤ 0.0.0.0（端⼝ 68） 作为源 IP 地址。DHCP 客户端将该 IP 数据报传递给链路层，链路层然后将帧⼴播到所有的⽹络中设备。

- DHCP 服务器收到 DHCP 发现报⽂时，⽤ **DHCP 提供报⽂（DHCP OFFER）** 向客户端做出响应。该报⽂仍然使⽤ IP ⼴播地址 255.255.255.255，该报⽂信息携带服务器提供可租约的 IP 地址、⼦⽹掩码、默认⽹关、DNS 服务器以及 **IP 地址租⽤期。**



- 客户端收到⼀个或多个服务器的 DHCP 提供报⽂后，从中选择⼀个服务器，并向选中的服务器发送 **DHCP 请求报⽂（DHCP REQUEST** 进⾏响应，回显配置的参数。


- 最后，服务端⽤ **DHCP ACK 报⽂**对 DHCP 请求报⽂进⾏响应，应答所要求的参数。


⼀旦客户端收到 DHCP ACK 后，交互便完成了，并且客户端能够在租⽤期内使⽤ DHCP 服务器分配的 IP 地址。

如果租约的 DHCP IP 地址快期后，客户端会向服务器发送 DHCP 请求报⽂：

- 服务器如果同意继续租⽤，则⽤ DHCP ACK 报⽂进⾏应答，客户端就会延⻓租期。

- 服务器如果不同意继续租⽤，则⽤ DHCP NACK 报⽂，客户端就要停⽌使⽤租约的 IP 地址。


可以发现，DHCP 交互中，**全程都是使⽤ UDP ⼴播通信。**

咦，⽤的是⼴播，那如果 DHCP 服务器和客户端不是在同⼀个局域⽹内，路由器⼜不会转发⼴播包，那不是每个⽹络都要配⼀个 DHCP 服务器？


所以，为了解决这⼀问题，就出现了 DHCP 中继代理。有了 DHCP 中继代理以后，对不同⽹段的 IP 地址分配也可以由⼀个 DHCP 服务器统⼀进⾏管理。


![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173337.png)

- DHCP 客户端会向 DHCP 中继代理发送 DHCP 请求包，⽽ DHCP 中继代理在收到这个⼴播包以后，再以单
播的形式发给 DHCP 服务器。

- 服务器端收到该包以后再向 DHCP 中继代理返回应答，并由 DHCP 中继代理将此包⼴播给 DHCP 客户端 。


因此，DHCP 服务器即使不在同⼀个链路上也可以实现统⼀分配和管理IP地址。



#### NAT
IPv4 的地址是⾮常紧缺的，在前⾯我们也提到可以通过 **⽆分类地址**来减缓 IPv4 地址耗尽的速度，但是互联⽹的⽤户增速是⾮常惊⼈的，所以 IPv4 地址依然有被耗尽的危险。

于是，提出了⼀种 **⽹络地址转换 NAT** 的⽅法，再次缓解了 IPv4 地址耗尽的问题。

简单的来说 NAT 就是同个公司、家庭、教室内的主机对外部通信时，把私有 IP 地址转换成公有 IP 地址。

![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173340.png)

那不是 N 个私有 IP 地址，你就要 N 个公有 IP 地址？这怎么就缓解了 IPv4 地址耗尽的问题？这不瞎扯吗？

确实是，普通的 NAT 转换没什么意义。

由于绝⼤多数的⽹络应⽤都是使⽤传输层协议 TCP 或 UDP 来传输数据的。

因此，可以把 IP 地址 + 端⼝号⼀起进⾏转换。


这样，就⽤⼀个全球 IP 地址就可以了，这种转换技术就叫 **⽹络地址与端⼝转换 NAPT。**


![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173344.png)

图中有两个客户端 192.168.1.10 和 192.168.1.11 同时与服务器 183.232.231.172 进⾏通信，并且这两个客户端的本地端⼝都是 1025。

此时，**两个私有 IP 地址都转换 IP 地址为公有地址 120.229.175.121，但是以不同的端⼝号作为区分。**

于是，⽣成⼀个 NAPT 路由器的转换表，就可以正确地转换地址跟端⼝的组合，令客户端 A、B 能同时与服务器之间进⾏通信。

这种转换表在 NAT 路由器上⾃动⽣成。例如，在 TCP 的情况下，建⽴ TCP 连接⾸次握⼿时的 SYN 包⼀经发出，就会⽣成这个表。⽽后⼜随着收到关闭连接时发出 FIN 包的确认应答从表中被删除。



##### NAT 那么⽜逼，难道就没缺点了吗？

由于 NAT/NAPT 都依赖于⾃⼰的转换表，因此会有以下的问题：

- 外部⽆法主动与 NAT 内部服务器建⽴连接，因为 NAPT 转换表没有转换记录。

- 转换表的⽣成与转换操作都会产⽣性能开销。

- 通信过程中，如果 NAT 路由器重启了，所有的 TCP 连接都将被重置。


解决的⽅法主要有两种⽅法。

###### 第⼀种就是改⽤ IPv6
IPv6 可⽤范围⾮常⼤，以⾄于每台设备都可以配置⼀个公有 IP 地址，就不搞那么多花⾥胡哨的地址转换了，但是IPv6 普及速度还需要⼀些时间。

###### 第⼆种 NAT 穿透技术
NAT 穿越技术拥有这样的功能，它能够让⽹络应⽤程序主动发现⾃⼰位于 NAT 设备之后，并且会主动获得 NAT 设备的公有 IP，并为⾃⼰建⽴端⼝映射条⽬，注意这些都是 NAT设备后的应⽤程序⾃动完成的。

也就是说，在 NAT 穿透技术中，NAT设备后的应⽤程序处于主动地位，它已经明确地知道 NAT 设备要修改它外发的数据包，于是它主动配合 NAT 设备的操作，主动地建⽴好映射，这样就不像以前由 NAT 设备来建⽴映射了。

说⼈话，就是客户端主动从 NAT 设备获取公有 IP 地址，然后⾃⼰建⽴端⼝映射条⽬，然后⽤这个条⽬对外通信，就不需要 NAT 设备来进⾏转换了。




#### ICMP
ICMP 全称是 Internet Control Message Protocol，也就是**互联⽹控制报⽂协议。**

⾥⾯有个关键词 —— **控制**，如何控制的呢？

⽹络包在复杂的⽹络传输环境⾥，常常会遇到各种问题。

当遇到问题的时候，总不能死个不明不⽩，没头没脑的作⻛不是计算机⽹络的⻛格。所以需要传出消息，报告遇到了什么问题，这样才可以调整传输策略，以此来控制整个局⾯。


##### ICMP 功能都有啥？
ICMP 主要的功能包括：确认 IP 包是否成功送达⽬标地址、报告发送过程中 IP 包被废弃的原因和改善⽹络设置等。

在 IP 通信中如果某个 IP 包因为某种原因未能达到⽬标地址，那么这个具体的原因将由 ICMP 负责通知。



![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173347.png)

如上图例⼦，主机 A 向主机 B 发送了数据包，由于某种原因，途中的路由器 2 未能发现主机 B 的存在，
这时，路由器 2 就会向主机 A 发送⼀个 ICMP ⽬标不可达数据包，说明发往主机 B 的包未能成功。

ICMP 的这种通知消息会使⽤ IP 进⾏发送 。

因此，从路由器 2 返回的 ICMP 包会按照往常的路由控制先经过路由器 1 再转发给主机 A 。收到该 ICMP包的主机 A 则分解 ICMP 的⾸部和数据域以后得知具体发⽣问题的原因。


##### ICMP 类型

ICMP ⼤致可以分为两⼤类：

- ⼀类是⽤于诊断的查询消息，也就是「查询报⽂类型」

- 另⼀类是通知出错原因的错误消息，也就是「差错报⽂类型」


![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173349.png)



#### IGMP
ICMP 跟 IGMP 是⼀点关系都没有的，就好像周杰与周杰伦的区别，⼤家不要混淆了。

在前⾯我们知道了组播地址，也就是 D 类地址，既然是组播，那就说明是只有⼀组的主机能收到数据包，不在⼀组的主机不能收到数组包，怎么管理是否是在⼀组呢？那么，就需要 IGMP 协议了。


![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173352.png)

- IGMP 报⽂向路由器申请加⼊和退出组播组，默认情况下路由器是不会转发组播包到连接中的主机，除⾮主机通过 IGMP 加⼊到组播组，主机申请加⼊到组播组时，路由器就会记录 IGMP 路由器表，路由器后续就会转发组播包到对应的主机了。


- IGMP 报⽂采⽤ IP 封装，IP 头部的协议号为 2，⽽且 TTL 字段值通常为 1，因为 IGMP 是⼯作在主机与连接的路由器之间。


##### IGMP ⼯作机制
IGMP 分为了三个版本分别是，IGMPv1、IGMPv2、IGMPv3。

接下来，以 IGMPv2 作为例⼦，说说**常规查询与响应和离开组播组**这两个⼯作机制。

###### 常规查询与响应⼯作机制


![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173355.png)

- 路由器会周期性发送⽬的地址为 224.0.0.1 （表示同⼀⽹段内所有主机和路由器） IGMP 常规查询报⽂。


- 主机1 和 主机 3 收到这个查询，随后会启动「报告延迟计时器」，计时器的时间是随机的，通常是 0~10秒，计时器超时后主机就会发送 IGMP 成员关系报告报⽂（源 IP 地址为⾃⼰主机的 IP 地址，⽬的 IP 地址为组播地址）。如果在定时器超时之前，收到同⼀个组内的其他主机发送的成员关系报告报⽂，则⾃⼰不再发送，这样可以减少⽹络中多余的 IGMP 报⽂数 。


- 路由器收到主机的成员关系报⽂后，就会在 IGMP 路由表中加⼊该组播组，后续⽹络中⼀旦该组播地址的数据到达路由器，它会把数据包转发出去。

##### 离开组播组⼯作机制

离开组播组的情况⼀，⽹段中仍有该组播组：

![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173357.png)

-  主机 1 要离开组 224.1.1.1，发送 IGMPv2 离组报⽂，报⽂的⽬的地址是 224.0.0.2（表示发向⽹段内的所有路由器）

- 路由器 收到该报⽂后，以 1 秒为间隔连续发送 IGMP 特定组查询报⽂（共计发送 2 个），以便确认该⽹络是否还有 224.1.1.1 组的其他成员。


- 主机 3 仍然是组 224.1.1.1 的成员，因此它⽴即响应这个特定组查询。路由器知道该⽹络中仍然存在该组播组的成员，于是继续向该⽹络转发 224.1.1.1 的组播数据包。


##### 离开组播组的情况⼆，⽹段中没有该组播组：

![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173400.png)

- 主机 1 要离开组播组 224.1.1.1，发送 IGMP 离组报⽂。

- 路由器收到该报⽂后，以 1 秒为间隔连续发送 IGMP 特定组查询报⽂（共计发送 2 个）。此时在该⽹段内，组 224.1.1.1 已经没有其他成员了，因此没有主机响应这个查询。

- ⼀定时间后，路由器认为该⽹段中已经没有 224.1.1.1 组播组成员了，将不会再向这个⽹段转发该组播地址的数据包。


### 4.21 假设⼀台机器加⼊组播地址，需要把IP改成组播地址吗？如果离开某个组播地址，需要dhcp 新请求个IP吗？”

组播地址不是⽤于机器ip地址的，因为组播地址没有⽹络号和主机号，所以跟dhcp没关系。组播地址⼀般是⽤于udp协议，机器发送UDP组播数据时，⽬标地址填的是组播地址，那么在组播组内的机器都能收到数据包。

是否加⼊组播组和离开组播组，是由socket⼀个接⼝实现的，主机ip是不⽤改变的。


### 4.22  ping 的⼯作原理

在⽇常⽣活或⼯作中，我们在判断与对⽅⽹络是否畅通，使⽤的最多的莫过于 ping 命令了。

#### IP协议的助⼿ —— ICMP 协议
ping 是基于 ICMP 协议⼯作的，所以要明⽩ ping 的⼯作，⾸先我们要熟悉 ICMP 协议。


![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173406.png)


ICMP 报⽂是封装在 IP 包⾥⾯，它⼯作在⽹络层，是 IP 协议的助⼿。

![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173408.png)


ICMP 包头的类型字段，⼤致可以分为两⼤类：

- ⼀类是⽤于诊断的查询消息，也就是「查询报⽂类型」

- 另⼀类是通知出错原因的错误消息，也就是「差错报⽂类型」



![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173412.png)


#### 查询报⽂类型

##### 回送消息 —— 类型 0 和 8

回送消息⽤于进⾏通信的主机或路由器之间，判断所发送的数据包是否已经成功到达对端的⼀种消息， ping 命令就是利⽤这个消息实现的。

![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173417.png)

可以向对端主机发送回送请求的消息（ ICMP Echo Request Message ，类型 8 ），也可以接收对端主机发回来的回送应答消息（ ICMP Echo Reply Message ，类型 0 ）。


![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173420.png)

相⽐原⽣的 ICMP，这⾥多了两个字段：

- 标识符：⽤以区分是哪个应⽤程序发 ICMP 包，⽐如⽤进程 PID 作为标识符；

- 序号：序列号从 0 开始，每发送⼀次新的回送请求就会加 1 ， 可以⽤来确认⽹络包是否有丢失。


在选项数据中， ping 还会存放发送请求的时间值，来计算往返时间，说明路程的⻓短。


#### 差错报⽂类型
接下来，说明⼏个常⽤的 ICMP 差错报⽂的例⼦：

- ⽬标不可达消息 —— 类型 为 3

- 原点抑制消息 —— 类型 4

- 定向消息 —— 类型 5

- 超时消息 —— 类型 11


##### ⽬标不可达消息（Destination Unreachable Message） —— 类型为 3
IP 路由器⽆法将 IP 数据包发送给⽬标地址时，会给发送端主机返回⼀个⽬标不可达的 ICMP 消息，并在这个消息中显示不可达的具体原因，原因记录在 ICMP 包头的代码字段。

由此，根据 ICMP 不可达的具体消息，发送端主机也就可以了解此次发送不可达的具体原因。

举例 6 种常⻅的⽬标不可达类型的代码：


![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173422.png)

###### a. ⽹络不可达代码为 0

外卖版本：

⼩林第⼀次送外卖时，⼩区⾥只有 A 和 B 区两栋楼，但送餐地址写的是 C 区楼，⼩林表示头上很多问号，压根就没这个地⽅。

正常版本：

IP 地址是分为⽹络号和主机号的，所以当路由器中的路由器表匹配不到接收⽅ IP 的⽹络号，就通过 ICMP 协议以⽹络不可达（ Network Unreachable ）的原因告知主机。

⾃从不再有⽹络分类以后，⽹络不可达也渐渐不再使⽤了。

###### b. 主机不可达代码为 1

外卖版本：

⼩林第⼆次送外卖时，这次⼩区有 5 层楼⾼的 C 区楼了，找到地⽅了，但送餐地址写的是 C 区楼 601 号房 ，说明找不到这个房间。


正常版本：
当路由表中没有该主机的信息，或者该主机没有连接到⽹络，那么会通过 ICMP 协议以主机不可达（ Host
Unreachable ）的原因告知主机。

c. 协议不可达代码为 2

外卖版本：
⼩林第三次送外卖时，这次⼩区有 C 区楼，也有 601 号房，找到地⽅了，也找到房间了，但是⼀开⻔⼈家是外国⼈说的是英语，我说的是中⽂！语⾔不通，外卖送达失败~

正常版本：
当主机使⽤ TCP 协议访问对端主机时，能找到对端的主机了，可是对端主机的防⽕墙已经禁⽌ TCP 协议访问，那么会通过 ICMP 协议以协议不可达的原因告知主机。

###### d. 端⼝不可达代码为 3

外卖版本：

⼩林第四次送外卖时，这次⼩区有 C 区楼，也有 601 号房，找到地⽅了，也找到房间了，房间⾥的⼈也是说中⽂的⼈了，但是⼈家说他要的不是外卖，⽽是快递。。。


正常版本：
当主机访问对端主机 8080 端⼝时，这次能找到对端主机了，防⽕墙也没有限制，可是发现对端主机没有进程监听8080 端⼝，那么会通过 ICMP 协议以端⼝不可达的原因告知主机。


###### e. 需要进⾏分⽚但设置了不分⽚位代码为 4
外卖版本：

⼩林第五次送外卖时，这次是个吃播博主点了 100 份外卖，但是吃播博主要求⼀次性要把全部外卖送达，⼩林的⼀台电动⻋装不下呀，这样就没办法送达了。

正常版本：

发送端主机发送 IP 数据报时，将 IP ⾸部的分⽚禁⽌标志位设置为 1 。根据这个标志位，途中的路由器遇到超过MTU ⼤⼩的数据包时，不会进⾏分⽚，⽽是直接抛弃。


随后，通过⼀个 ICMP 的不可达消息类型，代码为 4 的报⽂，告知发送端主机。


##### 原点抑制消息（ICMP Source Quench Message） —— 类型 4
在使⽤低速⼴域线路的情况下，连接 WAN 的路由器可能会遇到⽹络拥堵的问题。

ICMP 原点抑制消息的⽬的就是为了**缓和这种拥堵情况。**

当路由器向低速线路发送数据时，其发送队列的缓存变为零⽽⽆法发送出去时，可以向 IP 包的源地址发送⼀个ICMP 原点抑制消息。

收到这个消息的主机借此了解在整个线路的某⼀处发⽣了拥堵的情况，从⽽增⼤ IP 包的传输间隔，减少⽹络拥堵的情况。

然⽽，由于这种 ICMP 可能会引起不公平的⽹络通信，⼀般不被使⽤。


#####  定向消息（ICMP Redirect Message） —— 类型 5

如果路由器发现发送端主机使⽤了「不是最优」的路径发送数据，那么它会返回⼀个 ICMP 重定向消息给这个主机。

在这个消息中包含了最合适的路由信息和源数据。这主要发⽣在路由器持有更好的路由信息的情况下。路由器会通过这样的 ICMP 消息告知发送端，让它下次发给另外⼀个路由器。

好⽐，⼩林本可以过条⻢路就能到的地⽅，但⼩林不知道，所以绕了⼀圈才到，后⾯⼩林知道后，下次⼩林就不会那么傻再绕⼀圈了。


##### 超时消息（ICMP Time Exceeded Message） —— 类型 11
IP 包中有⼀个字段叫做 TTL （ Time To Live ，⽣存周期），它的值随着每经过⼀次路由器就会减 1，直到减到0 时该 IP 包会被丢弃。

此时，路由器将会发送⼀个 ICMP 超时消息给发送端主机，并通知该包已被丢弃。


设置 IP 包⽣存周期的主要⽬的，是为了在路由控制遇到问题发⽣循环状况时，避免 IP 包⽆休⽌地在⽹络上被转发。


![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173425.png)

此外，有时可以⽤ TTL 控制包的到达范围，例如设置⼀个较⼩的 TTL 值。



#### ping —— 查询报⽂类型的使⽤

接下来，我们重点来看 ping 的发送和接收过程。

同个⼦⽹下的主机 A 和 主机 B，主机 A 执⾏ ping 主机 B 后，我们来看看其间发送了什么？


![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173428.png)

ping 命令执⾏的时候，源主机⾸先会构建⼀个 ICMP 回送请求消息数据包。

ICMP 数据包内包含多个字段，最重要的是两个：

- 第⼀个是类型，对于回送请求消息⽽⾔该字段为 8 ；

- 另外⼀个是序号，主要⽤于区分连续 ping 的时候发出的多个数据包。

每发出⼀个请求数据包，序号会⾃动加 1 。为了能够计算往返时间 RTT ，它会在报⽂的数据部分插⼊发送时间。

![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173431.png)

然后，由 ICMP 协议将这个数据包连同地址 192.168.1.2 ⼀起交给 IP 层。IP 层将以 192.168.1.2 作为⽬的地址，本机 IP 地址作为源地址，协议字段设置为 1 表示是 ICMP 协议，再加上⼀些其他控制信息，构建⼀个 IP 数据包。

![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173435.png)

接下来，需要加⼊ MAC 头。如果在本地 ARP 映射表中查找出 IP 地址 192.168.1.2 所对应的 MAC 地址，则可以直接使⽤；如果没有，则需要发送 ARP 协议查询 MAC 地址，获得 MAC 地址后，由数据链路层构建⼀个数据帧，⽬的地址是 IP 层传过来的 MAC 地址，源地址则是本机的 MAC 地址；还要附加上⼀些控制信息，依据以太⽹的介质访问规则，将它们传送出去。





![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173438.png)


主机 B 收到这个数据帧后，先检查它的⽬的 MAC 地址，并和本机的 MAC 地址对⽐，如符合，则接收，否则就丢弃。


接收后检查该数据帧，将 IP 数据包从帧中提取出来，交给本机的 IP 层。同样，IP 层检查后，将有⽤的信息提取后交给 ICMP 协议。

主机 B 会构建⼀个 ICMP 回送响应消息数据包，回送响应数据包的类型字段为 0 ，序号为接收到的请求数据包中的序号，然后再发送出去给主机 A。


![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173441.png)

在规定的时候间内，源主机如果没有接到 ICMP 的应答包，则说明⽬标主机不可达；如果接收到了 ICMP 回送响应消息，则说明⽬标主机可达。

此时，源主机会检查，⽤当前时刻减去该数据包最初从源主机上发出的时刻，就是 ICMP 数据包的时间延迟。


针对上⾯发送的事情，总结成了如下图：


![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173443.png)

当然这只是最简单的，同⼀个局域⽹⾥⾯的情况。如果跨⽹段的话，还会涉及⽹关的转发、路由器的转发等等。

但是对于 ICMP 的头来讲，是没什么影响的。会影响的是根据⽬标 IP 地址，选择路由的下⼀跳，还有每经过⼀个路由器到达⼀个新的局域⽹，需要换 MAC 头⾥⾯的 MAC 地址。


说了这么多，可以看出 ping 这个程序是使⽤了 ICMP ⾥⾯的 ECHO REQUEST（类型为 8 ） 和 ECHO REPLY（类型为 0）。



#### traceroute —— 差错报⽂类型的使⽤
有⼀款充分利⽤ ICMP 差错报⽂类型的应⽤叫做 traceroute （在UNIX、MacOS中是这个命令，⽽在Windows中对等的命令叫做 tracert ）。


##### 1. traceroute 作⽤⼀
traceroute 的第⼀个作⽤就是**故意设置特殊的 TTL，来追踪去往⽬的地时沿途经过的路由器。**

traceroute 的参数指向某个⽬的 IP 地址：

traceroute 192.168.1.100

这个作⽤是如何⼯作的呢？

它的原理就是利⽤ IP 包的⽣存期限 从 1 开始按照顺序递增的同时发送 UDP 包，强制接收 ICMP 超时消息的⼀种⽅法。

⽐如，将 TTL 设置 为 1 ，则遇到第⼀个路由器，就牺牲了，接着返回 ICMP 差错报⽂⽹络包，类型是时间超时。


接下来将 TTL 设置为 2 ，第⼀个路由器过了，遇到第⼆个路由器也牺牲了，也同时返回了 ICMP 差错报⽂数据包，如此往复，直到到达⽬的主机。


这样的过程，traceroute 就可以拿到了所有的路由器 IP。


当然有的路由器根本就不会返回这个 ICMP，所以对于有的公⽹地址，是看不到中间经过的路由的。



发送⽅如何知道发出的 UDP 包是否到达了⽬的主机呢？

traceroute 在发送 UDP 包时，会填⼊⼀个不可能的端⼝号值作为 UDP ⽬标端⼝号（⼤于 3000 ）。当⽬的主机，收到 UDP 包后，会返回 ICMP 差错报⽂消息，但这个差错报⽂消息的类型是「端⼝不可达」。

所以，当差错报⽂类型是端⼝不可达时，说明发送⽅发出的 UDP 包到达了⽬的主机。

###### 2. traceroute 作⽤⼆
traceroute 还有⼀个作⽤是故意设置不分⽚，从⽽确定路径的 MTU。

这样做的⽬的是为了路径MTU发现。

因为有的时候我们并不知道路由器的 MTU ⼤⼩，以太⽹的数据链路上的 MTU 通常是 1500 字节，但是⾮以
外⽹的 MTU 值就不⼀样了，所以我们要知道 MTU 的⼤⼩，从⽽控制发送的包⼤⼩。


![](https://cdn.jsdelivr.net/gh/Gpslypy/mediaImage01@master/img202111/QQ图片20211216173446.png)

它的⼯作原理如下：

- ⾸先在发送端主机发送 IP 数据报时，将 IP 包⾸部的分⽚禁⽌标志位设置为 1。根据这个标志位，途中的路由器不会对⼤数据包进⾏分⽚，⽽是将包丢弃。

- 随后，通过⼀个 ICMP 的不可达消息将数据链路上 MTU 的值⼀起给发送主机，不可达消息的类型为「需要进⾏分⽚但设置了不分⽚位」。

发送主机端每次收到 ICMP 差错报⽂时就减少包的⼤⼩，以此来定位⼀个合适的 MTU 值，以便能到达⽬标主机。