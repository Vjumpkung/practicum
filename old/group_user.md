# การจัดการ user และ group

### วิธีการดูรายชื่อ group,user และ password ที่ตั้งไว้(hash แล้ว)

1. print รายชื่อ group ทั้งหมด
```bash
cat /etc/group
```

2. print รายชื่อ user ทั้งหมด
```bash
cat /etc/passwd
```

3. print รายการ password ทั้งหมด (ต้องใช้สิทธิ์ root ในการเข้าถึง)
```bash
cat /etc/shadow
```

# การสร้าง Group และ User

ก่อนอื่น login เป็น root ก่อนเสมอด้วยคำสั่งตามนี้

```bash
sudo su
```

ผลลัพธ์

```bash
root@practicum:/home/pi#
```

### คำสั่งเพิ่ม group ที่ชื่อว่า practice และมี id คือ 10000

```bash
groupadd -g 10000 practice
```

เมื่อ `cat /etc/group` แล้วจะเห็น group practice แล้ว
```bash
.
.
.
avahi-autoipd:x:125:
Debian-exim:x:126:
uuidd:x:127:
systemd-coredump:x:996:
practice:x:10000: <--- ตรงนี้
```

### คำสั่งเพิ่ม user ใหม่เข้าไปใน group ที่ได้สร้างขึ้นมา
```bash
useradd -g 10000 -u 10001 -m user01
```
ในที่นี้คือเพิ่ม user เข้าไปใน group ที่มี gid = 10000 และ uid คือ 10001 และมีชื่อว่า user01

### คำสั่งดูข้อมูล user01 ว่าอยู่ group อะไรและมี uid คืออะไร
```bash
id user01
```
output
```bash
uid=10001(user01) gid=10000(practice) groups=10000(practice)
```

### ตั้ง password เริ่มต้นสำหรับ user01
```bash
passwd user01
```
เมื่อทำคำสั่งนี้และ admin จะสามารถตั้ง password เริ่มต้นได้
```
New password:
Retype new password:
passwd: password updated successfully
```

### ตั้งเวลาหมดอายุของ password ที่ใช้อยู่เป็นหมดอายุแล้ว หมายความว่า user01 จะต้องตั้ง password ใหม่
```bash
chage -d 0 user01
```

เมื่อ user01 login เข้ามาแล้ว จะเจอคำสั่งแบบนี้
```
You are required to change your password immediately (administrator enforced).
Changing password for user01.
Current password:
```
ให้กรอก password เดิมก่อนแล้ว จะมีให้มากรอก password ที่ต้องการจะเปลี่ยนเข้าไปแทน
```
New password:
Retype new password:
```

### คำสั่งที่จะให้ user กรอกข้อมูลเบื้องต้นได้ (optional)
```bash
chfn
```