# Table of Contents

1. [vSphere 8 & 8u1 Announcements & Documentation](#v8announcementsanddocs)  
   a. [Helpful Videos & Blog Posts](#videosandblogs)  
   b. [General Documentation](#generaldocumentation)  
   c. [Useful Links](#usefullinks)  
2. [vSphere 8 & 8u1 New Features](#newfeatures)  
   a. [vSphere Distributed Services Engine](#vspheredistributedservicesengine)  
   b. [vSphere with Tanzu](#vspheretanzu)  
   c. [Lifecycle Management](#lifecyclemgmt)  
   d. [Artificial Intelligence & Machine Learning](#aiml)  
   e. [Guest OS & Workloads](#osworkloads)  
   f. [vSAN 8 Express Storage Architecture (ESA)](#vsan8esa)  
   g. [Resource Management](#resourcemgmt)  
   h. [Security & Compliance](#seccompliance)  
3. [vSphere 8u1 Upgrade Tips](#8u1upgradetips)  
   a. [TAM Customer Webinars](#tamcustomerwebinars)  
   b. [Important Dates](#importantdates)  
   c. [General Documentation on Upgrade Process & Recommendations](#genupgradeproc)  
   d. [Highlights from vCenter & ESXi 8u1 Release Notes](#highlightsreleasenotes)
4. [Upgrade Planning](#upgradeplanning)  
   a. [Minimizing Unknown Risk](#minimizerisk)  
   b. [Backups](#backups)  
   c. [Target Environments with Less Risk First](#target)  
   d. [dVS Upgrades Carry Some Risk](#dvsrisk)  
   e. [Use GSS & TAM Services to Assist Prior to the Upgrade](#usetamgss)  
   f. [Hardware Considerations](#hwconsiderations)  
   g. [Licensing](#licensing)  
   h. [Security Hardening](#sechardening)  
   i. [Follow Recommended Order for All VMware Component Upgrades](#followrecorder)  
   j. [Check vCenter Integration Dependencies](#checkvcenterdep)  
   k. [VCSA Free Space](@vcsafreespace)  
   l. [vSphere Diagnostic Tool](#diagnostictool)  
5. [Upgrade Execution](#upgradeexecution)  
   a. [Upgrade Day Preparation Checklist](#prepchecklist)  
   b. [Upgrade Order List](#orderlist)  
   c. [dVS v8 New Functionality](#dvs8newfunctionality)  
6. [Post-Upgrade Considerations](#postupgradeconsiderations)  

# vSphere 8 & 8u1 Announcements & Documentation <a name="v8announcementsanddocs"></a>  

## Helpful Videos & Blog Posts <a name="videosandblogs"></a>  

[Video] Why Upgrade to vSphere 8 - https://www.youtube.com/watch?v=4Z3sTJdXOjg  
New Release Model for vSphere 8 - https://blogs.vmware.com/vsphere/2022/10/new-release-model-for-vsphere-8.html  
Introducing vSphere 8: The Enterprise Workload Platform - https://blogs.vmware.com/vsphere/2022/08/introducing-vsphere-8-the-enterprise-workload-platform.html  
What's New in vSphere 8 - https://core.vmware.com/resource/whats-new-vsphere-8  
[Video] vSphere 8 What's New - https://core.vmware.com/?share=video3697&title=video-vsphere-8-whats-new  
vSphere on DPUs: NOW Available on vSphere 8 - https://core.vmware.com/blog/vsphere-dpus-now-available-vsphere-8  
Introducing vSphere 8 Update 1 - https://blogs.vmware.com/vsphere/2023/03/announcing-vsphere-8-update-1.html  
What's New in vSphere 8 Update 1 - https://core.vmware.com/resource/whats-new-vsphere-8-update-1  
[Video] vSphere 8 Update 1 What's New - https://core.vmware.com/?share=video4042&title=video-vsphere-8-update-1-whats-new  
What's New with vSphere 8 (and 8u1) Core Storage - https://core.vmware.com/resource/whats-new-vsphere-8-core-storage#section1  
vSphere LIVE YouTube Channel - The monthly show where we talk about vSphere-related topics and answer everyone's questions live on the air - https://www.youtube.com/playlist?list=PLymLY4xJSThqJY4iPo2jhklqYbDr5RtW6  

## General Documentation <a name="generaldocumentation"></a>  

vSphere 8 Release Notes - https://docs.vmware.com/en/VMware-vSphere/8.0/rn/vmware-vsphere-80-release-notes/index.html  
vSphere Documentation - https://docs.vmware.com/en/VMware-vSphere/index.html  
Configuration Maximums - https://configmax.esp.vmware.com/guest?vmwareproduct=vSphere&release=vSphere%208.0&categories=1-0  
VMware Firewall Ports & Protocols - https://ports.esp.vmware.com/  
Product Interoperability Matrix - https://interopmatrix.vmware.com/Interoperability  
VMware Security Advisories - https://www.vmware.com/security/advisories.html  

## Useful Links <a name="usefullinks"></a>  

__core.vmware.com__: The home for technical guidance on the core technologies that provide modern cloud infrastructure - https://core.vmware.com/vSphere  
__vSphere LIVE YouTube Channel__: The monthly show where they talk about vSphere-related topics and answer everyone's questions live on the air - https://www.youtube.com/playlist?list=PLymLY4xJSThqJY4iPo2jhklqYbDr5RtW6  
__General VMware YouTube Channel__: Anything and everything VMware videos - https://www.youtube.com/user/vmwaretv  
__VMware vSphere YouTube Channel__: Videos related to vSphere - https://www.youtube.com/channel/UCN8FHFshMw-15AtFKWSLczA  
__[Main KB] List of vSphere 8.0 Knowledge base articles and Important Links (89756)__ - https://kb.vmware.com/s/article/89756 

# vSphere 8 & 8u1 New Features <a name="newfeatures"></a>  

## vSphere Distributed Services Engine <a name="vspheredistributedservicesengine"></a>  

- Improves infrastructure performance   
- Simplifies DPU lifecycle management  
- Boosts infrastructure security  

### Prior to the Data Processing Unit Isolation  
Data Processing Units do exist in versions previous to vSphere 8.  They live in the hardware layer, similar to a PCIe device like a NIC or GPU. Networking, storage and host management services run in the instance of ESXi virtualizing the x86 compute layer    
<img width="727" alt="image" src="https://github.com/vSphere8upgrade/7u3-to-8u1/assets/135248193/a38fad20-5c47-4cd2-ad88-a415b518e3cb">

### Emergence of the Data Processing Unit - Isolation Layer
In vSphere 8, an additional instance of ESXi is installed directly on the Data Processing Unit. This allows ESXi services to be offloaded to the DPU for increased performance  
<img width="727" alt="image" src="https://github.com/vSphere8upgrade/7u3-to-8u1/assets/135248193/390fd0b9-7889-4b2d-a049-f2de4a1bb354">  

## vSphere with Tanzu <a name="vspheretanzu"></a>  

<img width="584" alt="image" src="https://github.com/vSphere8upgrade/7u3-to-8u1/assets/135248193/667f409f-962f-4fcf-8812-6a7e6a880a06">

- Unified Tanzu Kubernetes Grid  
- Increased availability with vSphere Zones  
- Declarative cluster lifecycle with ClusterClass  
- Customize PhotonOS or Ubuntu images  
- Pinniped Integration

## Lifecycle Management <a name="lifecyclemgmt"></a>  

### Deprecation Awareness - vSphere 8 last version of vSphere Update Manager (VUM)  
- DPU Support  
- Faster Cluster Remediation with Staging Support and Parallel Remediation  
<img width="586" alt="image" src="https://github.com/vSphere8upgrade/7u3-to-8u1/assets/135248193/6d54bb6a-3844-4513-a6b8-cf183b4d91d8"> <img width="310" alt="image" src="https://github.com/vSphere8upgrade/7u3-to-8u1/assets/135248193/99013fcb-3e37-4db6-8f66-45ede84e634b">  
<img width="586" alt="image" src="https://github.com/vSphere8upgrade/7u3-to-8u1/assets/135248193/06a31e6e-5baf-4611-94eb-fc7c015de755"> <img width="310" alt="image" src="https://github.com/vSphere8upgrade/7u3-to-8u1/assets/135248193/6aa295a9-7800-4532-97f3-aea46d9df2c6">  

- Enhanced Recovery of vCenter - Recover vCenter without data loss & Reconcile Cluster Membership After Restore  
<img width="440" alt="image" src="https://github.com/vSphere8upgrade/7u3-to-8u1/assets/135248193/1eca31e3-2724-49f3-bd32-df3145a4e6a7"> <img width="310" alt="image" src="https://github.com/vSphere8upgrade/7u3-to-8u1/assets/135248193/3f55ceb3-12f9-4692-ae3a-845997f13bc0">  
<img width="373" alt="image" src="https://github.com/vSphere8upgrade/7u3-to-8u1/assets/135248193/75a423e5-7ee6-428c-ad94-72eb822fa14c"> <img width="310" alt="image" src="https://github.com/vSphere8upgrade/7u3-to-8u1/assets/135248193/349ebed1-bf5c-4a99-8bb0-2b64073f996d">  

- vSphere Configuration Profiles - Configuration Management at Scale

<img width="565" alt="image" src="https://github.com/vSphere8upgrade/7u3-to-8u1/assets/135248193/ec9cd842-1a97-4538-9874-646ce0b59d73"> <img width="310" alt="image" src="https://github.com/vSphere8upgrade/7u3-to-8u1/assets/135248193/a743103e-1d5a-4208-b1cf-acd98985f3c8">  

## Artificial Intelligence & Machine Learning <a name="aiml"></a> 

- Unified Management for AI/ML Hardware Accelerators
<img width="548" alt="image" src="https://github.com/vSphere8upgrade/7u3-to-8u1/assets/135248193/b849d683-f7b4-413a-a628-310492285b5b">

- Simplified Hardware Consumption with Device Groups
<img width="876" alt="image" src="https://github.com/vSphere8upgrade/7u3-to-8u1/assets/135248193/08237491-228d-4a5b-96ac-a858b9a7616b">

- Introducing Next-Generation of Virtual Hardware Devices - Device Virtualization Extensions (DVX)
<img width="829" alt="image" src="https://github.com/vSphere8upgrade/7u3-to-8u1/assets/135248193/efb68d61-e16f-4724-8ac7-3e4750ef9752">    

## Guest OS & Workloads <a name="osworkloads"></a>  

- Virtual Hardware Version 20  
<img width="897" alt="image" src="https://github.com/vSphere8upgrade/7u3-to-8u1/assets/135248193/8c7d29d4-1181-4c5f-9b73-d2fc40c2a14a">  

- Virtual TPM Provisioning Policy - Deploy Windows 11 at Scale  
<img width="915" alt="image" src="https://github.com/vSphere8upgrade/7u3-to-8u1/assets/135248193/3f2b4248-0a88-4e3d-a242-5cee0fe22c68">  
  
- Migration-aware Applications - Introducing vSphere vMotion Notifications  
<img width="829" alt="image" src="https://github.com/vSphere8upgrade/7u3-to-8u1/assets/135248193/78800a28-aa7e-4eda-8b7f-d1509b95744e">  

- High latency sensitivity with hyper-threading  
<img width="913" alt="image" src="https://github.com/vSphere8upgrade/7u3-to-8u1/assets/135248193/272572d0-8063-4e36-9502-b3de79dc3785">  
  
- Simplified vNUMA configuration  
<img width="926" alt="image" src="https://github.com/vSphere8upgrade/7u3-to-8u1/assets/135248193/8efd0672-9039-45ed-b0e2-1954646ababf">  

- Compute Maximums  
<img width="571" alt="image" src="https://github.com/vSphere8upgrade/7u3-to-8u1/assets/135248193/f74a6390-f24b-491d-ab03-d27c20eb8ed6">  

## vSAN 8 Express Storage Architecture (ESA) <a name="vsan8esa"></a> 

- Optional Next Generation Architecture built into vSAN
<img width="850" alt="image" src="https://github.com/vSphere8upgrade/7u3-to-8u1/assets/135248193/0d3823d6-8f18-4908-9784-bdc6ecc7835c">  

- A New Way to Process and Store Data Efficiently
<img width="850" alt="image" src="https://github.com/vSphere8upgrade/7u3-to-8u1/assets/135248193/566af2d6-b9ef-42f7-a63b-2f90a1a8b0d5">  

## Resource Management <a name="resourcemgmt"></a> 

- Enhanced DRS Performance - vSphere Memory Monitoring and Remediation v2 (vMMR2)
Uses Memory Stats for better VM placement  
<img width="581" alt="image" src="https://github.com/vSphere8upgrade/7u3-to-8u1/assets/135248193/98d962f5-b19b-4056-919e-9d4a72158e24">  

- Monitor Energy and Carbon Emissions - vSphere Green Metrics  
<img width="889" alt="image" src="https://github.com/vSphere8upgrade/7u3-to-8u1/assets/135248193/ae098b36-5682-4002-9112-1af8be4373a7">  

## Security & Compliance <a name="seccompliance"></a>  

- Improvements to SGX  
- TLS 1.2 & Better Cipher Suites  
- Prevent Untrusted Binaries  
- More Secure Product Defaults  
<img width="802" alt="image" src="https://github.com/vSphere8upgrade/7u3-to-8u1/assets/135248193/74979d47-59b2-401c-9035-d0f26b69f617">  

# vSphere 8u1 Upgrade Tips <a name="8u1upgradetips"></a>  

## TAM Customer Webinars <a name="tamcustomerwebinars"></a>  

vSphere 8 - What's New - https://www.youtube.com/watch?v=bXabKxGOAP4&list=PLXw1EF8ZER1gvH_YBBZ6N9xujJXT6E9eh  
What's New with vSAN 8 including Express Storage Architecture - https://www.youtube.com/watch?v=fa8Ax6sPmps  
vSphere Lifecycle Management - https://www.youtube.com/watch?v=IUENQZeHalw&list=PLXw1EF8ZER1hPcEdIju9_hnzlMCbBgvRw&index=9   

## Important dates <a name="importantdates"></a>  

### End of General Support for vSphere 7 - April 2, 2025  
 
What does End of General Support mean?  
https://www.vmware.com/support/policies.html  

![image](https://github.com/vSphere8upgrade/7u3-to-8u1/assets/16085267/b36d7a3e-2f8b-49de-8300-f65d74f7a08b)

## General Documentation on Upgrade Process & Recommendations <a name="genupgradeproc"></a>  

Upgrading to vSphere 8  
https://core.vmware.com/resource/upgrading-vsphere-8#:~:text=On%20the%20vSphere%20Client%20Home,host%20compatibility%20and%20click%20Next  

vSphere 8v Upgrade Scenarios  
https://core.vmware.com/resource/vsphere-8-upgrade-scenarios?path=/vsphere-8-upgrade-activity-path  

It is **very important** to read the release notes for your version:  

vSphere ESXi 8 Update 1 Release Notes  
https://docs.vmware.com/en/VMware-vSphere/8.0/rn/vsphere-esxi-801-release-notes/index.html

vCenter Server 8 Update 1 Release Notes  
https://docs.vmware.com/en/VMware-vSphere/8.0/rn/vsphere-vcenter-server-801-release-notes/index.html

*__Note:__ There have been additional releases to vSphere and ESXi 8 u1 (ESXi - u1a, u1c; vCenter - u1a, u1b, u1c)*

## Highlights from vCenter & ESXi 8u1 Release Notes <a name="highlightsreleasenotes"></a>  

- vSphere Configuration Profiles
- With vSphere 8.0 Update 1, vSphere Distributed Services Engine adds support for:  
NVIDIA BlueField-2 DPUs to server designs from Lenovo (Lenovo ThinkSystem SR650 V2)  
100G NVIDIA BlueField-2 DPUs to server designs from Dell  
UPTv2 for NVIDIA BlueField-2 DPUs  
AMD Genoa CPU based server designs from Dell
- Recorder for required privileges on vCenter Server workflows
- Support for heterogenous virtual graphics processing unit (vGPU) profiles on the same GPU hardware
- Integration of VMware Skyline™ Health Diagnostics™ with vCenter
- VM-level power consumption metrics
- NVSwitch support
- Okta Identity Federation for vCenter
- Support for Fault Tolerance of virtual machines that use a virtual TPM (vTPM) module
- Quick Boot support for servers with TPM 2.0 chips
- vSphere API for Storage Awareness (VASA) version 5 for vSphere Virtual Volumes
- Sidecar files become regular files in Config-vVol instead of vSphere Virtual Volumes objects  
After updating to ESXi 8.0 Update 1, new virtual machines, or virtual disks in the Config-vVol namespace are not supported on ESXi hosts of earlier versions. For more information and resolution, see VMware knowledge base article 90791
- Increased default capacity for vSphere Virtual Volumes objects of type Config-vVol
- NVMe over TCP support for vSphere Virtual Volumes
- Extended XCOPY support
- New file type for OSDATA volumes on SSD devices
- NFS traffic isolation enhancements
- Fourfold increase in NVMe-oF namespace capacity
- Support for end-to-end NVMe stack without protocol translation  
vSphere 8.0 Update 1 also extends NVMe functionality by adding support for third-party multi-pathing plug-ins to control and manage NVMe arrays
- Increased maximum for Windows Server Failover Clusters (WSFC)
- Scale the number of NVMe over TCP adapters
- Support hot-add and hot-remove for VMDirectPath I/O devices
- Increased number of PCI passthrough devices per VM
- Local depot overrides for Remote Office and Branch Office (ROBO) standalone ESXi hosts
- Advanced filters in the vSphere Client
- Increased maximum number of NFSv3 datastores that can be mounted with multiple connections
- HTTP/JSON-based wire protocol as an alternative to SOAP/XML  
  
- This release resolves CVE-2023-1017. VMware has evaluated the severity of this issue to be in the low severity range with a maximum CVSSv3 base score of 3.3  
- This release resolves CVE-2023-1018. VMware has evaluated the severity of this issue to be in the low severity range with a maximum CVSSv3 base score of 3.3  


# Upgrade Planning <a name="upgradeplanning"></a>  

## Minimizing Unknown Risk <a name="minimizerisk"></a>  

History teaches that no amount of planning will consider all use cases. Thus, it’s best to introduce strategies meant at minimizing risk.  

It’s important to develop company-specific documentation for the upgrade process. This will allow many colleagues to collaborate on upgrades and lessons learned to be communicated.  

The following are considerations that should be addressed before deciding on a date for the upgrades.

## Backups <a name="backups"></a>  

The first step is to have reliable backups. Confirm and test your backups are in good working order before upgrading.  

Types of backups to check and verify before attempting upgrades:  

- vCenter (https://kb.vmware.com/s/article/2149237)  
- Distributed virtual switches (https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere.networking.doc/GUID-BE48C292-F222-4095-BCF8-D6444A785E16.html)    
- ESXi config (https://kb.vmware.com/s/article/2042141)  

Also check for re-installation media for the current versions of vSphere, as well as any vendor drivers/firmware that would be needed for a rollback situation.  

## Target Environments with Less Risk First <a name="target"></a>  

One way to minimize risk is to have several independent environments where upgrades can be tested in order from least impactful up to production. For example:  

Start with a true test environment, that can be down at any time, and can be rebuilt several times with different drivers, firmware and hardware configurations. The biggest concern is that it may not have the same exact integrations and hardware as production. The biggest advantage is practice and speed.  

Next should be any development environment that is not tied to production workloads. Hopefully this environment has some integrations, such as backup or monitoring, and hardware is in line with production.  

A point of conflict could be environments that are in linked mode. vCenter upgrades require all vCenters in linked mode to be upgraded at the same time. These upgrades must be planned very carefully.  

Production environment upgrades should consider the level of impact, hardware and number of integrations. A VDI environment, for example, has more considerations than a server environment. If possible, develop or simulate these integrations in test or dev.  


## dVS Upgrades Carry Some Risk <a name="dvsrisk"></a>  

Distributed virtual switch upgrades should be done off hours as they can cause a network “blip”. Please read and understand the following KB  

https://kb.vmware.com/s/article/52621  

## Use GSS & TAM Services to Assist Prior to the Upgrade <a name="usetamgss"></a>  

Always open a proactive GSS ticket prior to upgrades. Present your plan to GSS and ask them to verify it. You may require 5 business days or more, depending on many factors, so open with time. Of course, your TAM will also verify to the best of their ability.


## Hardware Considerations <a name="hwconsiderations"></a>

Hardware compatibility should be checked for all types of hardware currently deployed in the environment using the VMware Compatibility Guide  

https://www.vmware.com/resources/compatibility/search.php  

Several filters can be applied. Sometimes the same server model can have different family CPUs, so this should also be checked (the following screenshot is not comprehensive, but has selected the 8u1 ESXi version and a manufacturer to see all supported servers by that vendor)  

<img width="936" alt="image" src="https://github.com/vSphere8upgrade/7u3-to-8u1/assets/135248193/3fb8fd7d-0421-49ad-adc0-56c107ba6372">  
<img width="937" alt="image" src="https://github.com/vSphere8upgrade/7u3-to-8u1/assets/135248193/6306e91f-f5fa-400f-8de4-730ec7dd1140">  

Develop and **document** a hardware plan, both for software and hardware firmware and drivers versions. It’s important to verify the hardware vendor’s website for their recommended ESXi installation ISO image, which should include all drivers needed, and related firmware upgrade CD. They typically include release notes or “recipe” documentation to make sure you are aligned; the VMware hardware compatibility web page can also be used to verify IO device driver and firmware combinations.  

![image](https://github.com/vSphere8upgrade/7u3-to-8u1/assets/135248193/aed9f938-65e3-4b52-8651-e34c34b9e8e0)  

### vSphere Lifecycle Manager (VUM Replacement) 

It’s important to get familiarized with the replacement for VUM (vSphere Upgrade Manager) called vSphere Lifecycle Management (vLCM). VUM is deprecated in vSphere 8 which means vSphere 8 is going to be the last vSphere release that supports baseline lifecycle management. If you have not switched to vSphere Lifecycle Manager single image, Please review the Switching from Using Baselines to Using Images links below.

__Introduction to vLCM__  

https://core.vmware.com/resource/introducing-vsphere-lifecycle-management-vlcm  

https://docs.vmware.com/en/VMware-vSphere/8.0/vsphere-lifecycle-manager/GUID-74295A37-E8BB-4EB9-BFBA-47B78F0C570D.html  

__Switching from Using Baselines to Using Images__  

vSphere 7 Environment  
https://docs.vmware.com/en/VMware-vSphere/8.0/vsphere-lifecycle-manager/GUID-B54663AB-B1D1-4E87-8B8C-76FF2998A477.html  

vSphere 8 Environment  
https://docs.vmware.com/en/VMware-vSphere/8.0/vsphere-lifecycle-manager/GUID-B54663AB-B1D1-4E87-8B8C-76FF2998A477.html  

__*Note:*__ The best practice is to use your test environments to familiarize yourself with the new interface.  

## Licensing <a name="licensing"></a>  

An upgrade from v7 to v8 will require updating licenses. Document old license keys and their location, and upgrade license keys as you upgrade environments. You will need licenses for all upgraded components, including individual hosts and vSAN.  

## Security Hardening <a name="sechardening"></a>  

A complete review of hardening steps has to be done with this upgrade. The steps that were used to harden v6.7 will be different in v7, although many will be similar. Always refer to the official hardening guide link to find the best recommendation:  

https://www.vmware.com/security/hardening-guides.html  

https://blogs.vmware.com/vsphere/2020/10/announcing-the-vsphere-security-configuration-guide-7.html    

## Follow Recommended Order for All VMware Component Upgrades <a name="followrecorder"></a>

There is a specific upgrade order when several VMware products are installed together. Familiarize yourself with this KB and follow the order in your upgrade plan document.  

https://kb.vmware.com/s/article/89745  

## Check vCenter Integration Dependencies <a name="checkvcenterdep"></a>

vSphere integrates with many solutions. Most of the integrations are done at the vCenter level. These include both VMware and 3rd party solutions.  

Develop a list of all the environments and what software integrations exist. Common ones include backups, monitoring, automation, hardware and storage plugins. You can use this table as an example of the documentation that you should create:  

![image](https://github.com/vSphere8upgrade/7u3-to-8u1/assets/16085267/d39babe1-c30f-483c-bb9b-e476a2f5adb2)

Use the product interoperability matrix to check applicable versions  

https://interopmatrix.vmware.com/Interoperability  

For example, NSX is required to be at version 4.x to be compatible with vSphere 8u1:  

![SRM and vCenter version dependencies](https://raw.githubusercontent.com/arielsanchezmora/vSphere-67-Upgrade-to-7u3/main/images/vSphere67-Upgrade-7u3-image8.jpg)  

Develop this list _before_ starting upgrades. It will bring clarity of what systems share integrations (for example, the same backup platform may service both dev and production environments) and will save many avoidable headaches.

## VCSA Free Space <a name="vcsafreespace"></a>  

You will get an option to migrate the most essential data, or to also include tasks, events and performance metrics. You can compare the size of the data with the available free space in the source vCenter. When the data is larger than available free space, you will be asked for a different location than / . Typically, you will find the VUM partition has large free space (using the command _df -h_) and can provide that, check this [blog post by Luciano Patrao](https://www.provirtualzone.com/how-to-add-extra-space-to-vcenter-for-the-upgrade/) or consult with GSS.

![VCSA upgrade data option](https://raw.githubusercontent.com/arielsanchezmora/vSphere-67-Upgrade-to-7u3/main/images/vSphere67-Upgrade-7u3-image10.jpg)

## vSphere Diagnostic Tool <a name="diagnostictool"></a>  

A tool that VMware GSS has made available to the public in fling form is able to catch many problems in vCenter environments before they become an issue mid-upgrade. It is a good idea you run this and share the output in your proactive GSS ticket, as it may show some tasks that need to be performed before you attempt the upgrade.  

https://flings.vmware.com/vsphere-diagnostic-tool   

# Upgrade Execution <a name="upgradeexecution"></a>  

__*Note:*__ This section is a good start, but you will have to adjust and expand to your environment and conditions.  Place the VCSA VM in a known host and stop automatic movement of VMs by putting DRS in manual mode. You may also clone the VCSA VM as an extra backup, or create a snapshot, but be aware that linked mode vCenters need a cold snapshot of all vCenters linked, and this is something you should be doing in coordination with GSS.

## Upgrade Day Preparation Checklist <a name="prepchecklist"></a>  

1.	Finish upgrade documentation plan  
2.	Gather temporary IP address for vCenter(s)  
3.	Gather needed software and hardware ISOs (confirm md5/sha-1 checksums to make sure they aren't corrupted)  
4.	Test ESXi host remote access credentials  
5.	Set a longer maintenance window than needed  
6.	Have a proactive GSS ticket handy  

## Upgrade Order List <a name="orderlist"></a>  

An actual execution order should be in your upgrade documentation plan. The below is an example (which is not meant to be comprehensive):  

1. Backup the environment  
2. Upgrade vCenter server  
3. Install vCenter Plugins  
4. Upgrade ESXi Hosts  
5. Upgrade the vSphere Distributed Switches
6. Upgrade vSAN on-disk Format to 8.0 Compatibility
7. Upgrade VMware Host Profiles
8. Upgrade VMware Tools  
9. Upgrade VMware Virtual Hardware    
10. Upgrade Cisco UCS Infrastructure  
11. Upgrade the Cisco UCS C-Series Servers with HUU  
12. Upgrade storage array infrastructure  


## dVS v8 New Functionality <a name="dvs8newfunctionality"></a>  

v8 includes new functionalities for the distributed virtual switch, which can be reviewed here:

https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere.networking.doc/GUID-330A0689-574A-4589-9462-14CA03F3F2F4.html  

<img width="984" alt="image" src="https://github.com/vSphere8upgrade/7u3-to-8u1/assets/135248193/1a469a9d-7c80-45de-89ea-54ae3d6c54c3">


# Post-Upgrade Considerations <a name="postupgradeconsiderations"></a>  

Check that all integrations, users, monitoring, and automations are working. Perform tests. As you work out any issues in each environment, document the fixes as lessons learned for the next environment.  

If you created snapshots, don't hold them for too long. Snapshots can stress the storage system, and they are only useful for a few hours; if you must, 2 days should be more than enough of a time window to have taken a good backup.  

Great resource for vSphere 8 performance:  
https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/techpaper/performance/vsphere-esxi-vcenter-server-80-performance-best-practices.pdf  

https://kb.vmware.com/s/article/80472  

Enjoy vCenter 8u1!
