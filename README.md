# Setup RESTORE

- ดาวน์โหลดไฟล์ SQL/BAK ของส่วนกลางทั้งหมดจากลิงค์ด้านบน
- แตกไฟล์ที่ดาวน์โหลดมา
- เปิด Navicat SQL Server Management Studio (SSMS) หรือเครื่องมือจัดการฐานข้อมูล SQL Server อื่น ๆ ที่คุณใช้งาน
- เชื่อมต่อกับ MySQL
- สร้างฐานข้อมูลใหม่สำหรับการนำเข้าข้อมูล

```docker-compose
version: '3.8'

services:
  mysql:
    image: mysql:8.0
    container_name: rid_mysql_db
    restart: unless-stopped
    environment:
      MYSQL_ROOT_PASSWORD: rootpassword
      MYSQL_DATABASE: rid_web_db_new
      MYSQL_USER: rid_user
      MYSQL_PASSWORD: rid_password
    ports:
      - "3306:3306"
    volumes:
      - mysql_data:/var/lib/mysql
    command: --default-authentication-plugin=mysql_native_password

volumes:
  mysql_data:
```

- เชื่อมด้วย Root user และรหัสผ่านที่คุณตั้งไว้ในไฟล์ `docker-compose.yml` (ในตัวอย่างนี้คือ `rootpassword`)
- ใช้คำสั่ง SQL หรือเครื่องมือที่คุณเลือกเพื่อนำเข้าข้อมูลจากไฟล์ SQL/BAK ที่ดาวน์โหลดมา
  - หากใช้ Navicat หรือ SSMS ให้เลือกฐานข้อมูลที่สร้างขึ้นแล้วคลิกขวา เลือก "Import" หรือ "Restore" แล้วเลือกไฟล์ BAK ที่ต้องการนำเข้า (ตัวอย่างคือ Navicat) (ใน BAK นามสกุล .nb3 ดีกว่า)
  - หากใช้คำสั่ง SQL ให้ใช้คำสั่ง `SOURCE` หรือ `RESTORE DATABASE` ตามที่มีหรือเครื่องมือที่คุณใช้งาน

ไฟล์ vdo ใหญ่ไป
<div align="center">
  <video src="vdo/restoreDB.mp4" controls width="600" style="margin-top: 10px;">
    Your browser does not support the video tag.
  </video>
</div>

### มาต่อที่ DB rid เรา

- เรามี docker-compose ที่รันไว้แล้ว
- Restore จาก rid_web_db_new (.nb3)

<div align="center">
<video src="vdo/rid-new.mp4" controls width="600">
  Your browser does not support the video tag.
</video>
</div>

# Setup เสร็จ เริ่มทำ

- สร้าง folder ของตัวเองตามที่ต้องทำ
- Copy script มาเลย Script ที่สมบูรณ์ที่สุดของแต่ละ schema :
  - Joomla : rio17
  - WordPress : rio7
### Check ก่อนทำ
  - ถามพี่มาร์ท
  - Check ใน Lark

### เปิด CHAT มา!!!
คำสั่งแก้ sql script (ตัวอย่าง) เอามาจากตาราง all-central **ลบ passed fail ออก**
- prompt
- ตาราง
- site id

```text
this is the migration menu i copies from rio17 : [D:\Mart\Project\rid\database_migration_02\fad],
now make it for migrate fad website,

this is the menu i want to migrate : [cms	ข่าวกิจกรรม	https://link-1	catid = 11
document	หนังสือเวียน	https://link-2	catid = 22
document	คำสั่งกองการเงินและบัญชี	https://link-3	catid = 12
document	รายงานการประชุม	https://link-4	catid = 14
document	รายงานการเงิน กรมชลประทาน	https://link-5	catid = 21]
, 

site id = 4
```

<div align="center">
  <img src="img/diagram.png" controls style="margin-top: 10px;">
    Your browser does not support the video tag.
  </img>
</div>
