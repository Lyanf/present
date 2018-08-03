# 学习总结
## openstack是什么
openstack本质上是 **云操作系统**的 **内核**：
- 操作系统：一般操作系统应该具有的能力（很大的一个框架，整合了很多功能，进行资源分配与调度等操作系统的工作）他都有
- 内核：仍然需要进行修修剪剪、增加一些工具链之类的东西才能叫做完整的操作系统（用户需要进行一定的定制）

和通常的操作系统（linux、windows）相比，他的作用是对各个虚拟主机及整个集群系统进行管理，并且他的上方不是各种具体的应用，那个是linux、windows这些操作系统的事情，openstack管理的东西要更加底层，例如给不同的虚拟机分配内存、CPU等。
openstack处于虚拟化出来的主机之上，用户操作系统之下。

## 云计算、虚拟化相关
- 云计算：**使用计算机的一种方式，着重点在于途径**是指把计算机的使用当成一种服务提供出来，通过网络随时随地可以使用计算资源，质上是一种使用计算机的方式，并不一定要求必须要虚拟化，如果我每次连接到云上，都是一台实际存在的物理机，那么这时候的云计算就和虚拟化及openstack都无关了。
- 虚拟化：**把硬件资源进行分割，一个当成多个用**（VMware和KVM都是做这个事情的）例如一个CPU虚拟化为3个，供3个人使用。主要关注于如何 **隔离**的更加彻底、如何有更小的 **损耗**、怎么隔离一些新的设备
- **云计算&虚拟化**为什么云计算一般要使用虚拟化技术：
    + 弹性资源模式，最大限度利用资源。
    + 方便进行逻辑架构的组网，本身就是一个集群进行软件分割，若真的是多台物理机，网络连接还需要连接网线。

## openstack的结构
- nova：最重要的部分，计算控制中心，中心部件，调控全局
- glance：镜像管理，可以在这个里面加载windows、linux或其他自定义镜像，在openstack的基础上面安装
- ironic：本来是nova的一部分，现在分离出来，配合nova进行裸机服务
- cinder：存储管理
- neutron：网络相关的管理
- ceilometer：日志、信息记录相关
----------------------分层

- heat：系统自动化，进行模板编排，从而可以把虚拟机进行自定义的部署。
- horizon：ui相关

## ManageOne
用户友好的管理整合：
私有云的构建，需要对多个虚拟机进行管理，构建逻辑结构等，虽然openstack就是做这个的，但是他对用户不够友好，而且都是从技术层面提供基础的API，不能直接投入商用。ManageOne接收用户语言，调用openstack的API完成相应的构建、管理（SC）功能。另外，ManageOne可以直接从应用场景出发，提供额外的用户工具，构建相应的应用场景模板（例如VDC的分级），提供更加友好的用户体验。
另外，在运维（OC）方面也可以进行整合，即在多方面对于整个云系统进行管理、维护等。
