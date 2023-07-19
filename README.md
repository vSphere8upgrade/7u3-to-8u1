# vSphere 8 - What's New?! 



# vSphere-7u3-Upgrade-to-8u1 - WIP

Tips, tricks, gotchas and important dates collected by a friendly VMware TAM

## vSphere 8 u1 highlights

Share blog posts and videos highlighting the new features/capabilities of vSphere 8u1


### TAM customer webinars  

Provide TAM customer webinars related to vSphere 8u1


### Known issues in 8u1
As of right now I don't see any KB articles with details   


## Important dates:
List EOGS for vSphere 7u3   
 
What does End of General Support mean?  
https://www.vmware.com/support/policies.html#lifecyclepolicies  

![general support explanation](https://raw.githubusercontent.com/arielsanchezmora/vSphere-67-Upgrade-to-7u3/main/images/vSphere67-Upgrade-7u3-image2.jpg)  


## General documentation on upgrade process and recommendations

Provide links to upgrade process

It is **very important** to read the release notes for your version:  

vSphere ESXi 8 Update 1x Release Notes  
https://docs.vmware.com/en/VMware-vSphere/8.0/rn/vsphere-esxi-801-release-notes/index.html - this is for 8u1, 8u1a is now available 

vCenter Server 8 Update 1x Release Notes  
https://docs.vmware.com/en/VMware-vSphere/8.0/rn/vsphere-vcenter-server-801-release-notes/index.html - this is for 8u1, 8u1b is now available


## Highlights from ESXi 8u1 release notes

Provide highlights of ESXi 8u1 release notes


## Highlights from vCenter Server 8u1 release notes

Provide highlights of vCenter Server 8u1 release notes


# Upgrade planning


## Minimizing unknown risk

History teaches that no amount of planning will consider all use cases. Thus, it’s best to introduce strategies meant at minimizing risk.  

It’s important to develop company-specific documentation for the upgrade process. This will allow many colleagues to collaborate on upgrades and lessons learned to be communicated.  

The following are considerations that should be addressed before deciding on a date for the upgrades.


## Backups

The first step is to have reliable backups. Confirm and test your backups are in good working order before upgrading.  

Types of backups to check and verify before attempting upgrades:  

- vCenter  
- Distributed virtual switches  
- ESXi config (especially important as v7 uses a new format and wipes the previous installation) https://kb.vmware.com/s/article/2042141  

Also check for re-installation media for the current versions of vSphere, as well as any vendor drivers/firmware that would be needed for a rollback situation.  


## Target environments with less risk first

One way to minimize risk is to have several independent environments where upgrades can be tested in order from least impactful up to production. For example:  

Start with a true test environment, that can be down at any time, and can be rebuilt several times with different drivers, firmware and hardware configurations. The biggest concern is that it may not have the same exact integrations and hardware as production. The biggest advantage is practice and speed.  

Next should be any development environment that is not tied to production workloads. Hopefully this environment has some integrations, such as backup or monitoring, and hardware is in line with production.  

A point of conflict could be environments that are in linked mode. vCenter upgrades require all vCenters in linked mode to be upgraded at the same time. These upgrades must be planned very carefully.  

Production environment upgrades should consider the level of impact, hardware and number of integrations. A VDI environment, for example, has more considerations than a server environment. If possible, develop or simulate these integrations in test or dev.  


## dVS Upgrades carry some risk

Distributed virtual switch upgrades should be done off hours as they can cause a network “blip”. Please read and understand the following KB  
https://kb.vmware.com/s/article/52621  


## Use GSS and TAM services to assist prior to the upgrade

Always open a proactive GSS ticket prior to upgrades. Present your plan to GSS and ask them to verify it. You may require 5 business days or more, depending on many factors, so open with time. Of course, your TAM will also verify to the best of their ability.


## Hardware considerations

Hardware compatibility should be checked for all types of hardware currently deployed in the environment using the VMware Compatibility Guide  

https://www.vmware.com/resources/compatibility/search.php  

Several filters can be applied. Sometimes the same server model can have different family CPUs, so this should also be checked (the following screenshot is not comprehensive, but has selected the 7u3 ESXi version and a manufacturer to see all supported servers by that vendor)  

![VMware Compatibility Guide](https://raw.githubusercontent.com/arielsanchezmora/vSphere-67-Upgrade-to-7u3/main/images/vSphere67-Upgrade-7u3-image5.jpg)  

Develop and **document** a hardware plan, both for software and hardware firmware and drivers versions. It’s important to verify the hardware vendor’s website for their recommended ESXi installation ISO image, which should include all drivers needed, and related firmware upgrade CD. They typically include release notes or “recipe” documentation to make sure you are aligned; the VMware hardware compatibility web page can also be used to verify IO device driver and firmware combinations.  

![software, firmware and driver version documentation](https://raw.githubusercontent.com/arielsanchezmora/vSphere-67-Upgrade-to-7u3/main/images/vSphere67-Upgrade-7u3-image6.jpg)  

It’s important to get familiarized with the replacement for VUM (vSphere Upgrade Manager) called vSphere Lifecycle Management. It is similar but introduces new features. These two links are a great start:  

https://core.vmware.com/resource/introducing-vsphere-lifecycle-management-vlcm  

https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere-lifecycle-manager.doc/GUID-74295A37-E8BB-4EB9-BFBA-47B78F0C570D.html  

The best practice is to use your test environments to familiarize yourself with the new interface.  


## Licensing

An upgrade from v6 to v7 will require updating licenses. Document old license keys and their location, and upgrade license keys as you upgrade environments. You will need licenses for all upgraded components, including individual hosts and vSAN.  


## Security hardening

A complete review of hardening steps has to be done with this upgrade. The steps that were used to harden v6.7 will be different in v7, although many will be similar. Always refer to the official hardening guide link to find the best recommendation:  

https://www.vmware.com/security/hardening-guides.html  

https://blogs.vmware.com/vsphere/2020/10/announcing-the-vsphere-security-configuration-guide-7.html  


## Follow recommended order for all VMware component upgrades

There is a specific upgrade order when several VMware products are installed together. Familiarize yourself with this KB and follow the order in your upgrade plan document.  

https://kb.vmware.com/s/article/89745 - link has been updated for vSphere 8 


## Checking vCenter integration dependencies

vSphere integrates with many solutions. Most of the integrations are done at the vCenter level. These include both VMware and 3rd party solutions.  

Develop a list of all the environments and what software integrations exist. Common ones include backups, monitoring, automation, hardware and storage plugins. You can use this table as an example of the documentation that you should create:  

![vCenter integration documentation](https://raw.githubusercontent.com/arielsanchezmora/vSphere-67-Upgrade-to-7u3/main/images/vSphere67-Upgrade-7u3-image7.jpg)  

Use the product interoperability matrix to check applicable versions  

https://interopmatrix.vmware.com/Interoperability  

For example, SRM is required to be at version 8.5 to be compatible with vSphere 7u3:  

![SRM and vCenter version dependencies](https://raw.githubusercontent.com/arielsanchezmora/vSphere-67-Upgrade-to-7u3/main/images/vSphere67-Upgrade-7u3-image8.jpg)  

Develop this list _before_ starting upgrades. It will bring clarity of what systems share integrations (for example, the same backup platform may service both dev and production environments) and will save many avoidable headaches.


## VCSA free space

You will get an option to migrate the most essential data, or to also include tasks, events and performance metrics. You can compare the size of the data with the available free space in the source vCenter. When the data is larger than available free space, you will be asked for a different location than / . Typically, you will find the VUM partition has large free space (using the command _df -h_) and can provide that, check this [blog post by Luciano Patrao](https://www.provirtualzone.com/how-to-add-extra-space-to-vcenter-for-the-upgrade/) or consult with GSS.

![VCSA upgrade data option](https://raw.githubusercontent.com/arielsanchezmora/vSphere-67-Upgrade-to-7u3/main/images/vSphere67-Upgrade-7u3-image10.jpg)


## vSphere Diagnostic Tool 

A tool that VMware GSS has made available to the public in fling form is able to catch many problems in vCenter environments before they become an issue mid-upgrade. It is a good idea you run this and share the output in your proactive GSS ticket, as it may show some tasks that need to be performed before you attempt the upgrade.  

https://flings.vmware.com/vsphere-diagnostic-tool - confirmed that this is updated to support v8u1 


## Further Reading

I want to link to several of [Lucho DeLorenzi](https://twitter.com/lgdelorenzi)'s blog posts, which are very useful especially when you want to get your hands dirty and check the health of your vCenters yourself. This should be covered during your proactive ticket with VMware GSS, but just in case :)

https://luchodelorenzi.com/2021/04/05/how-do-i-get-to-vsphere-7-0-without-dying-in-the-process/  
_video is in Spanish, courtesy of the Argentina VMUG_  

https://luchodelorenzi.com/2020/04/10/pre-upgrade-considerations-in-multi-vcenter-environments/  

https://luchodelorenzi.com/2020/05/28/proactively-checking-and-replacing-sts-certificate-on-vsphere-6-x-7-x/  

# Upgrade execution


This section is a good start, but you will have to adjust and expand to your environment and conditions.  Place the VCSA VM in a known host and stop automatic movement of VMs by putting DRS in manual mode. You may also clone the VCSA VM as an extra backup, or create a snapshot, but be aware that linked mode vCenters need a cold snapshot of all vCenters linked, and this is something you should be doing in coordination with GSS.

## Upgrade day preparation checklist

1.	Finish upgrade documentation plan  
2.	Gather temporary IP address for vCenter(s)  
3.	Gather needed software and hardware ISOs (confirm md5/sha-1 checksums to make sure they aren't corrupted)  
4.	Test ESXi host remote access credentials  
5.	Set a longer maintenance window than needed  
6.	Have proactive GSS ticket handy  

## Upgrade order list

An actual execution order should be in your upgrade documentation plan. The below is an example (which is not meant to be comprehensive):  

1. Backup the environment  
2. Upgrade vCenter server  
3. Install vCenter Plugins  
4. Upgrade ESXi Hosts  
5. Upgrade the vSphere Distributed Switches  
6. Upgrade VMware Tools  
7. Upgrade VMware Virtual Hardware  
8. Upgrade vSAN on-disk Format to 7.0 Compatibility  
9. Upgrade Cisco UCS Infrastructure  
10. Upgrade the Cisco UCS C-Series Servers with HUU  
11. Upgrade storage array infrastructure  


## dVS v7 new functionality

v7 includes new functionalities for the distributed virtual switch, which can be reviewed here:

https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere.networking.doc/GUID-330A0689-574A-4589-9462-14CA03F3F2F4.html  

![vSphere 7 new functionality](https://raw.githubusercontent.com/arielsanchezmora/vSphere-67-Upgrade-to-7u3/main/images/vSphere67-Upgrade-7u3-image9.jpg)




# Post upgrade considerations

Check that all integrations, users, monitoring and automations are working. Perform tests. As you work out any issues in each environment, document the fixes as lessons learned for the next environment.  

If you created snapshots, don't hold them for too long. Snapshots can stress the storage system, and they are only useful for a few hours; if you must, 2 days should be more than enough of a time window to have taken a good backup.  

Great resource for vCenter performance:  

https://blogs.vmware.com/performance/2021/09/extreme-performance-video-blog-series.html  

vCenter now uses vCLS (vSphere Clustering Service):

https://core.vmware.com/resource/introduction-vsphere-clustering-service-vcls  

https://kb.vmware.com/s/article/80472  

Enjoy vCenter 7!
