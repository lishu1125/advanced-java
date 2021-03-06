## 分布式系统 CAP 定理 P 代表什么含义

作者之前在看 CAP 定理时抱有很大的疑惑，CAP 定理的定义是指在分布式系统中三者只能满足其二，也就是存在分布式 CA 系统的。作者在网络上查阅了很多关于 CAP 文章，虽然这些文章对于 P 的解释五花八门，但总结下来这些观点大多都是指 P 是不可缺少的，也就是说在分布式系统只能是 AP 或者 CP，这种理论与我之前所认识的理论（存在分布式 CA 系统）是冲突的，所以才有了疑惑。

> 这个定理起源于加州大学柏克莱分校（University of California, Berkeley）的计算机科学家埃里克·布鲁尔在 2000 年的分布式计算原理研讨会（PODC）上提出的一个猜想。 在 2002 年，麻省理工学院（MIT）的赛斯·吉尔伯特和南希·林奇发表了布鲁尔猜想的证明，使之成为一个定理。

### 什么是 CAP 定理（CAP theorem）

在理论计算机科学中，CAP 定理（CAP theorem），又被称作布鲁尔定理（Brewer's theorem），它指出对于一个分布式计算系统来说，不可能同时满足以下三点：

- 一致性（Consistency） （等同于所有节点访问同一份最新的数据副本）
- 可用性（Availability）（每次请求都能获取到非错的响应——但是不保证获取的数据为最新数据）
- 分区容错性（Partition tolerance）（以实际效果而言，分区相当于对通信的时限要求。系统如果不能在时限内达成数据一致性，就意味着发生了分区的情况，必须就当前操作在 C 和 A 之间做出选择。）

### 分区容错性（Partition tolerance）

理解 CAP 理论的最简单方式是想象两个节点分处分区两侧。允许至少一个节点更新状态会导致数据不一致，即丧失了 C 性质。如果为了保证数据一致性，将分区一侧的节点设置为不可用，那么又丧失了 A 性质。除非两个节点可以互相通信，才能既保证 C 又保证 A，这又会导致丧失 P 性质。

- P 指的是分区容错性，分区现象产生后需要容错，容错是指在 A 与 C 之间选择。如果分布式系统没有分区现象（没有出现不一致不可用情况） 本身就没有分区 ，既然没有分区则就更没有分区容错性 P。
- 无论我设计的系统是 AP 还是 CP 系统如果没有出现不一致不可用。 则该系统就处于 CA 状态
- P 的体现前提是得有分区情况存在

> 文章来源：[维基百科 CAP 定理](https://zh.wikipedia.org/wiki/CAP%E5%AE%9A%E7%90%86)
