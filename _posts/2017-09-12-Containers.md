---
layout: post
title: Containers - to contain your complex environment dependencies 
categories: journal 
tags: [phoenix,intermediate,coding]
comments: true
image:  
  feature: Container.jpg
  teaser:  Container-teaser.jpg
  credit:  Cloud Academy
  creditlink: "cloudacademy.com"
---

## Preface
Is your code complex and have a lot of dependencies? Are you frastrated by the fact that your code
is not compiling and complaining about the version conflict? This is the situation you will need the
support of a contained environment. 
\\
Containers have a simple goal in mind, that is to
isolate an application and its dependencies into a self-contained unit that can run anywhere
regardless of hardware and shell environment etc. Form this perspective, VMs serves a similar
function, which you may be more familier. Nevertheless, container is regarded as superior approach
compare to VM, which removes the needs for physical hardware emulator and have performance
superiority.  
\\
To understand why container is more superior, we have to understand more about architectural
underline the container and VMs.

### Virtual Machines
A VM is essentially an emulation of a physical computer and the execution of applications follows
the same procedures as a physical computer would. This is because VMs run on top of a physical
machine using a layer so called "hypervisor" or "virtual machine monitor" (VMM). A "hypervisor" is a
piece of software, firmware and
hardware emulator bundle that run directly on physical computers (which is called __host machine__
under this context). The __host machine__ provides physical resources like RAM and CPU etc.
Hypervisors present the guest operating systems with a
virtual operating platform and manages the execution of the guest operating systems. The
resources provided by the __host machine__ can be divided and distributed and multiple instances of
a variety of operating systems may share the distributed resources after virtualisation by
hypervisors. The name __hypervisor__  also reflects its nature as a controller of the operating
system _kernel_, where __hyper__ is a stronger term
than _super_ and __hypervisor__ is translated as the __supervisor__ of the __supervisor__. (If you
are interested in the incarnation of term __hypervisor__, you may find following two items
intersting: [original paper by Harry
Katzan, 1970](https://www.google.com.au/url?sa=t&rct=j&q=&esrc=s&source=web&cd=3&cad=rja&uact=8&ved=
0ahUKEwi03Me_0p7WAhWLjLwKHb1yAPUQFggrMAI&url=https%3A%2F%2Fwww.computer.org%2Fcsdl%2Fproceedings%
2Fafips%2F1970%2F5075%2F00%2F50750109.pdf&usg=AFQjCNEjSj3yIa3LUEJth_4vfO150T1y9g) and [a book by
Clinton McIntosh,
1970](https://www.amazon.de/Analysis-Major-Computer-Operating-Systems/dp/B00B06YA18).)  
\\
A VM contains both the applications (i.e. the part you will be interested as
bioinformatician) and whatever the supports are required to run that application (e.g. system
binaries and varies dependency libraries). In addition, a VM also carries an entire
virtualised hardware stack of its own (e.g. virtualised CPU, network adaptors and storage) VM is a
fully fledged guest operating system with its own dedicated resources (virtualised from host
machine's distribution). VM can run on __host machine__ in one of two modes: as a _hosted
hypervisor__ or as a __bare-metal hypervisor__. They are fundamentally different. 

#### Hosted Hypervisor 
A _hosted hypervisor_ runs through the operating sstem of the _host machine_. The benefit of a
_hosted hypervisor_ is largely sweep away the importance of the underlying hardware, this is due to
the fact that the host operating system is handling the hardware communications. Therefore the
_hosted hypervisor_ is useful in the situation where the hardware compatibility is high on the
priority list. On the flip side, _hosted hypervisor_ inevitably invert an additional layer between
hardware and application, the consequences can be more resource overhead and result a resource
hungry application, lower VM performace.  
#### Bare-metal Hypervisor
Contrary to _hosted hypervisor_, a _bare metal hypervisor_ environment improves performance by
directly run on host machine's hardware. In turn, a _bare-metal hypervisor_ needs its own operating
system and own device drivers to be able to interact with underline hardware (e.g. I/O, kernel
processes etc.). Therefore _bare-metal hypervisor_ can perform better, have better scalability and
enhanced stability. Nevertheless, this also comes a cost of compatibility given that only limited
device drivers can be implemented at a single time.  
\\
In summary, although VM contains everything we need to run an application (bioinformatics
application) and is independent to certain degree, it also need to compromise either performance or
compatibility.  
\\
<code data-gist-id="fe0b1428d6fff82984c51ffe6430216f" data-gist-file="VM_Arch.png"></code>

### Containers
As oppose to VMs' virtualisation at hardware level, __Containers__ provides virtualisation at
operating-system-level by abstracting the so-called "user space". Like VM, Containers also have
private processing space, private network interface, IP address (allow customised routes and iptable
rules), full control of mount file systems and also have "root" privilege when executing shell
commands. The one big difference between Containers and VM is that Containers utilise host system's
kernel directly. 
\\
<code data-gist-id="fe0b1428d6fff82984c51ffe6430216f" data-gist-file="Container_Arch.png"></code>
\\
Given that "Containers" only package up the user space but not the kernel (only bins and libs
packaged independently) and virtual hardware like VM does, this makes containers typically
"lightweight". 
\\
If you are a programmer or have been tech nerd, you may have already heard of Docker. Docker is a
helpful tools for packaging, shipping and running applications within "containers". It is somewhat
important to have a mindful understanding about Docker. Docker is an open-source project based on Linux containers (like LXC), therefore Docker naturally uses Linux Kernel features like namespaces and control groups in creating containers.  
\\
Docker containers have several advantages: 
1. Easy implementation. 
1. Speed. Docker containers are very lightweight and light fast. Typically Docker containers take only seconds to start, whereas spawn VM takes a full boot of virtual operating system every time.  
1. Docker Hub. Rich ecosystem of Docker Hub, there is almost certain to have an docker image to suit your needs. 
1. Modularity and Scalability. 

In the next post, we will be talking through the fundamentals of Docker concepts and implementation. Stay tuned. 
<br><br>
From Robert 
