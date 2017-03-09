# 22.4 创建云主机异常处理

云主机创建失败，可以点击Mevoco消息中心获得创建失败的原因。请参考下表所示的异常解决方法进行处理。

|异常信息|异常原因及解决办法|
| --- | --- |
| “code”:”HOST.1005”,”description”:”Failed to start vm on hypervisor”, “details”:”failed to start …., Libvirt error: internal error no supported architecture for os type ‘hvm’”或"details": "failed to start vm on kvm host, because unable to start vm, libvirt error: invalid argument: could not find capabilities for domaintype=kvm " | Mevoco需要物理机支持并打开了硬件虚拟化（如vmx或者svm）的支持。出现该错误的原因通常是因为BIOS中没有打开CPU虚拟化。解决办法是重启系统，并进入BIOS打开CPU相关虚拟化支持。 |
| “details”: "cannot find either 'vmx' or 'svm' in /proc/cpuinfo, please make sure you have enabled virtualization in your BIOS setting" | Mevoco需要物理机支持并打开了硬件虚拟化（如vmx或者svm）的支持。出现该错误的原因是因为用户添加的物理机的CPU不支持硬件虚拟化功能。通常是由于用户添加的物理机是一个“云主机”导致的，那么需要打开对应“云主机”的嵌套虚拟化功能。具体的打开办法，请联系“云主机”提供方。 |
| "details": "the local primary storage has no hosts with enough disk capacity[xxx bytes] required by the vm[uuid:xxx]" | 当前系统中（或者任何单独一台物理机）没有足够的主存储容量（磁盘空间）。Mevoco在分配云主机和云盘的时候使用的是thin clone模式，也就是云主机使用多少，才分配多少。但是在创建云主机的时候，会按照云主机最大申请的使用空间来扣除系统主存储的容量，以防最后云主机使用的空间超过系统可用空间。另外如果主存储为本地存储，由于云主机的磁盘不能够跨物理机存储，所以如果每台物理机的剩余空间都不足创建一台新的云主机，也会遇到此错误。解决办法是删除一些不需要使用的云主机，云盘，或者调整云主机使用的镜像大小。在理解主存储超分的原理和使用方法的前提下，也可以增大主存储超分比例以获得更多超分空间。 |
| "details": "unable to allocate hosts; due to pagination is enabled, there might be several allocation failures happened before; the error list is [{no host having cpu[x HZ], memory [xxx bytes] found}]" | 当前系统中（或者任何单独一台物理机）没有足够的内存。解决办法是删除一些不需要使用的云主机，或者调整云主机使用计算规格的大小。在理解内存超分的原理和使用方法的前提下，也可以增大存储超分比例以获得更多超分容量。 |
| "details": "failed to start vm[uuid:xxx name:xxx] on kvm host[uuid:xxx, ip:x.x.x.x], because unable to start vm[uuid:xxx, name:xxx], libvirt error: internal error: early end of file from monitor: possible problem: Cannot set up guest memory 'pc.ram': Cannot allocate memory" set up guest memory 'pc.ram':Cannot allocate memory" | 当前系统中实际可用物理内存不足以分配给需要创建的云主机。当这个错误出现的时候，就算是提高内存超分比例，也没有办法创建更大容量的内存。解决办法是减小云主机的计算规格，增加物理主机的内存，或者增加物理主机的swap分区（会降低系统性能）。 |
| "failed to migrate vm[uuid:xxx] from kvm host[uuid:xxx, ip:xxx] to dest host[ip:xxx], unable to migrate vm[uuid:xxx] to qemu+tcp://xxx/system, Unsafe migration: Migration may lead to data corruption if disks use cache != none" | 当前的基础设置中，将云主机的磁盘缓存模式设置为其他模式，例如，writethrough或writeback，系统认为带缓存模式的迁移是不安全的。需要将此基础设置的缓存模式修改为None模式才可迁移。 |

