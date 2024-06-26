## Conclusion Week1

- ### Firewall Fortigate 60e

<div align="center">

![Fortigate 60e](https://img5.pic.in.th/file/secure-sv1/Screenshot-2024-04-06-195913.png)

-- [Datasheet Firewall] --

[Datasheet Firewall]: https://www.firewalls.com/pub/media/wysiwyg/datasheets/Fortinet/FG-FW-60E.pdf

</div>

# How to configure the Firewall
* เชื่อมต่อ PC/Notebook เข้ากับ Firewall ผ่านพอร์ตใดพอร์ตหนึ่ง ใน 1-7 พอร์ต
* เข้า Browser จากนั้นเข้า Url >> https://192.168.1.99/ (Default IP Address)
* เข้าสู่ระบบด้วย Username >> admin ไม่ต้องใส่ password แล้วเข้าสู่ระบบ

![img_fwlogin](https://img5.pic.in.th/file/secure-sv1/Screenshot-2024-04-06-234327.png)
* สร้าง User โดยเข้า User Authentication > User Definition จากนั้นกด Create New
    * กรอก Username / Password จาก นั้นกด Next จนจบ
    * สร้าง Group แล้วเพิ่ม user ที่สร้างเข้าไป
* เข้า Network > Interface
    * เข้าไปแก้ไขในส่วน
    ![img_fwInf](https://i.postimg.cc/fLDDX915/Screenshot-2024-04-07-002414.png)
    * ลบ Port Internal ที่เราจะใช้ออก
* ทำการสร้าง Interface ของ Service 1-4
    * กำหนด Type: Hardware Switch
    * กำหนด IP: 10.80.x.0/25 โดย x จะเปลี่ยนตามเลข Service ที่สร้าง
    * IPv4 เลือก
    - [x] PING
* ทำการสร้าง Interface ชื่อ mgmt
    * กำหนด Type: Hardware Switch
    * กำหนด IP: 0.0.0.0/0.0.0.0
* ทำการสร้าง Interface ชื่อ Inf851
    * กำหนด Type: Vlan
    * กำหนด Vlan ID: 1
    * เลือก Addressing mode เป็น DHCP เพื่อให้อุปกรณ์ทำการจัดสรร IP ให้ และกำหนด IP: 10.85.1.0
    * IPv4 เลือก
    - [x] HTTP
    - [x] HTTPS
    - [x] PING
    - [x] SSH
* ตั้งค่า VPN
* สร้าง Policy ของ Interface,VPN

Credits: [YouTube_FireWall]

[YouTube_FireWall]: https://www.youtube.com/watch?v=XcghOBrZANc&list=PLlEVCBdM7ELOSd9zLJNE3FrIMzZiWlSkm

---

- ### Switch FortiSwitch 424d

<div align="center">

![Switch FortiSwitch 424d](https://www.avfirewalls.com.au/images/FortiSwitch/FortiSwitch-424D.png)

-- [Datasheet Switch] --

[Datasheet Switch]: https://www.avfirewalls.com.au/FortiSwitch-424D.asp

![Port Connectors](https://img2.pic.in.th/pic/Screenshot-2024-04-06-201851.png)

</div>

- SW1 (Service)
    * Reset Switch(รีให้เป็นค่าเริ่มต้น)
    * Setup IP/Host จาก Firewall
    * Create config trunk server1(1,2), server2(3,4) ** ทำการมัดรวม lacp **
    * Create config Vlan 801,802,803,804

- SW2 (mgmt)
    * Reset Switch(รีให้เป็นค่าเริ่มต้น)
    * Setup IP/Host จาก Firewall
    * Create config trunk server1(1,2), server2(3,4) ** ทำการมัดรวม lacp **
    * Create config Vlan 851,852

---

- ### Server Dell PowerEdge R330

<div align="center">

![Dell r330](https://img2.pic.in.th/pic/h3t89sll.png)

-- [Datasheet Dell PowerEdge R330] --

[Datasheet Dell PowerEdge R330]:https://i.dell.com/sites/csdocuments/Shared-Content_data-Sheets_Documents/en/aa/Dell_PowerEdge_R330_SpecSheet_final.pdf

</div>
