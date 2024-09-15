**pfSense** is a popular open-source firewall and router software based on the FreeBSD operating system. It's designed to provide robust network security and traffic management capabilities.

In this demo, I will walk you through the step-by-step installation of the `pfSense`firewall.

To download pfsense, go to their website https://www.pfsense.org/, and find `Download`

![image01](https://github.com/user-attachments/assets/f984e477-b3b2-442d-925e-2b0aa4986338)
![image02](https://github.com/user-attachments/assets/6a204558-6d72-4aa5-b974-68c4dd5b9c96)

You will be redirected to [shop.netgate.com](http://shop.netgate.com), here choose `iso` image since we will be running on the VM.

![image03](https://github.com/user-attachments/assets/073e9ee2-89c8-41e3-9973-26b34637344f)

You will have to create Netgate account to download your iso file. Once everything is set up, they will provide you the download link to your email.

![image04](https://github.com/user-attachments/assets/6b5a0862-1d29-4deb-b4f1-c03aa1c45208)

Download from the link Netgate provided.

![image05](https://github.com/user-attachments/assets/28c2e5e7-f1a7-4f4e-866b-7afce9faa94e)

Once your downloaded is completed, create a New Virtual Machine on your VMware Workstation.

![image06](https://github.com/user-attachments/assets/c06c0cf8-4536-4da2-8861-4ae0c2d3a693)

Choose `Custom (advanced)` and hit `Next`

![image07](https://github.com/user-attachments/assets/868c4d07-ecd2-4c55-894a-fbeaec47a350)

You can leave it as default and go `Next`

![image08](https://github.com/user-attachments/assets/850aa741-728d-45eb-8326-1c69b34e56c0)

Select the directory where your `pfSense.iso` file is located

![image09](https://github.com/user-attachments/assets/c1a4e784-ff32-4ce7-90ac-f1b3a810cf37)

Give it a name `pfSense` and enter location where this VM will be stored.

![image10](https://github.com/user-attachments/assets/f75b9aa1-24e9-4b07-b494-7ca79ddf8b46)

Configure your processors and memory according to your system resources.

![image11](https://github.com/user-attachments/assets/4738deba-e04c-4c15-a2f8-2582c03e98c0)
![image12](https://github.com/user-attachments/assets/d7f22a3a-43bb-4e5b-a8e3-e11a006ae26e)

For Network setting, we can skip for now since we will configure it later.

![image13](https://github.com/user-attachments/assets/fd001693-b82c-4728-9afe-2d3102fb40d3)

We can keep recommended settings for controller types and disk types

![image14](https://github.com/user-attachments/assets/844640de-a882-49cf-a4f9-f45e1a3c9bf2)
![image15](https://github.com/user-attachments/assets/e7c6400b-fb47-4ed3-9074-7746f2b1afef)
![image16](https://github.com/user-attachments/assets/060f8539-7f74-43ed-b87c-4783b7ff3eb9)

For disk storage, you can specify according to your needs. (I set 20GB for this lab)

![image17](https://github.com/user-attachments/assets/eac66ad2-0f61-4c83-9a3d-c753a311e7ac)

Select a directory where `pfSense` will be stored.

![image18](https://github.com/user-attachments/assets/5cdf00b3-b9d8-464d-8072-d03309fc7b0f)

Uncheck `Power on this virtual machine after creation` since we still need to configure network adapters for `pfSense` firewall.

![image19](https://github.com/user-attachments/assets/bd0b3854-4f7e-40a8-80ed-075b6efa6ce4)

Once we’ve created `pfSense` VM, we will need to add a network adapter because firewalls use two interfaces (one for WAN port and one for LAN) since we only have one interface.

![image20](https://github.com/user-attachments/assets/b9341135-fad3-4de8-a983-750fefd3f8fc)

Add a new network adapter.

![image21](https://github.com/user-attachments/assets/8fda65f1-f07e-4e94-8e21-bed82f66d3ff)


Configure `Network Adapter 1` to `Bridged(WAN interface)` and Network Adapter 2 to Custom(VMnet8) which is `192.168.17.0/24 (LAN subnet)`. If you are using Virtual box, it might be different.

![image22](https://github.com/user-attachments/assets/0f3bb6e1-5c44-4e29-9710-18bb03f917c3)
![image23](https://github.com/user-attachments/assets/62c1bfea-0a59-444f-a799-6dfb911bdbe9)


Start your `pfSense` VM to boot

![image24](https://github.com/user-attachments/assets/5ec80379-630b-4356-9fb7-22b322ddba0d)

Accept the license terms and continue

![image25](https://github.com/user-attachments/assets/cf329d57-ef3b-4007-a8a8-b3303f241187)

Install `pfSense` and select your WAN and LAN interfaces.

![image26](https://github.com/user-attachments/assets/ff75fc53-4641-4b1f-880d-8753afd36f1a)
![image27](https://github.com/user-attachments/assets/724b01bf-ef46-432f-b198-8d46e672d09b)

You can know which one is WAN or LAN interface by checking their **MAC addresses** in `Network Adapters advanced settings`

![image28](https://github.com/user-attachments/assets/1b9ca7f8-c751-4ea6-b7e2-0086cda49895)

We can leave `WAN Network Mode Setup` and press `OK`

![image29](https://github.com/user-attachments/assets/df3adbbc-4b2d-4a3d-9814-6f1690cdbc08)

Select `em1` as LAN interface and hit `ok`

![image30](https://github.com/user-attachments/assets/6ecb149c-bdb8-4630-ac4c-34f108830e50)

In LAN interface, you might notice the IP address range is wrong as we’ve configured in VMware settings. So we have to change it to our LAN subnet (which is 192.168.17.0)  

![image31](https://github.com/user-attachments/assets/ebbc8f7d-11cd-485b-b81b-e3f9b6971d38)
![image32](https://github.com/user-attachments/assets/0a3752a2-7e69-4a24-a1d7-856652f51221)
![image33](https://github.com/user-attachments/assets/e7b40580-7254-4bdf-80fa-b20e33b7f246)

Wait for verifying connectivity set up to finish

![image34](https://github.com/user-attachments/assets/1778a059-1591-4b6b-9e81-9c44414951cb)

Install community edition subscription

![image35](https://github.com/user-attachments/assets/d792b5cc-013c-427a-b094-35f7a0a8724d)

You can select file system as you want. (I continue with default installation in this case)

![image36](https://github.com/user-attachments/assets/8b530a2d-e2f5-44f4-a87e-8f7e19bb1d8d)
![image37](https://github.com/user-attachments/assets/827686c7-030f-49d3-a63e-584b62232d22)
![image38](https://github.com/user-attachments/assets/57d6996f-3793-4c8c-ae7f-8d7d0dfc1a0f)

Here choose `Current Stable Relase` CE version.

![image39](https://github.com/user-attachments/assets/13f22f4a-4c56-4bdf-8dca-9689bc9f37be)

Wait for `pfSense` to finish installation. Once it has finished installing, remove your `pfSense iso` file drive and reboot your `pfSense`

![image40](https://github.com/user-attachments/assets/9a3985a7-df49-4fc0-9d26-a59a19417eb9)

After rebooting, you can see `pfSense firewall` is successfully installed.

![image41](https://github.com/user-attachments/assets/a67f6543-49dc-4743-832f-14a47044f7d6)

