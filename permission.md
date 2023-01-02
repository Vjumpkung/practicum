# การจัดการ Permission ของ File และ Directory

ก่อนอื่น login เป็น root ก่อนเสมอด้วยคำสั่งตามนี้

```bash
sudo su
```

ในที่นี้จะสร้าง directory ที่มีชื่อว่า basket ไว้ที่ /home และสร้าง user02 ลงไปใน group practice (gid : 10000)

```bash
mkdir /home/basket
```

เมื่อ `ls -l` ที่ /home แล้วจะพบ directory ดังนี้
```bash
drwxr-xr-x  2 root   root     4096 Jan  2 15:14 basket
drwxr-xr-x 14 pi     pi       4096 Jan  2 14:38 pi
drwxr-xr-x  2 user01 practice 4096 Jan  2 14:48 user01
```

ซึ่งจะพบว่า directory basket นั้น user ที่ชื่อ root และ group ที่ชื่อ root มีสิทธิ์ `อ่าน(r)/เขียน(w)/execute(x)` ได้เท่านั้น ที่เหลือมีสิทธิ์แค่ `อ่าน(r)/execute(x)`

### การเปลี่ยนเจ้าของ (owner) กับสิทธิ์ของ directory/file นั้นๆ

directory ที่มีชื่อว่า basket นั้นจะต้องการให้ group basket มีสิทธิ์อ่าน/เขียน/execute ได้ มีขั้นตอนดังนี้

```bash
chown -R :practice basket/
```
คำสั่งนี้จำทำให้ basket ให้ group practice เป็นเจ้าของแบบกลุ่ม แต่ root ยังเป็นเจ้าของที่เป็น user อยู่
```
drwxr-xr-x  2 root   practice 4096 Jan  2 15:14 basket
```

แต่เมื่อได้ทำการ login เข้าไปยัง user ที่อยู่ใน group practice แล้วพบว่า ยังไม่สามารถสร้างไฟล์ได้ เพราะว่า directory นั้นยังไม่ให้สิทธิ์ในการเขียนสำหรับ group practice
```bash
user02@practicum:/home/basket $ touch file2
touch: cannot touch 'file2': Permission denied
```

**วิธีแก้**
ให้ใช้คำสั่ง chmod ในการแก้ไขสิทธิ์ในการเข้าถึง directory basket โดยมีโครงสร้างคำสั่งดังนี้
```
chmod -R <สิทธิ์เลขฐาน8> <directory>
```
โดยเลขสิทธิ์ฐาน 8 สามารถลองได้จากเว็บนี้ https://chmod-calculator.com

โดย directory ที่ต้องการจะให้ group practice มีสิทธิ์ในการเขียนได้ โดยทำตามคำสั่งนี้

```
chmod -R 775 basket
```

เมื่อ `ls -l` แล้วจะได้ผลลัพธ์ดังนี้
```
.
.
.
drwxrwxr-x  2 root   practice 4096 Jan  2 15:14 basket
```

ในที่นี้จะพบว่าไฟล์ที่อยู่ใน group เดียวกันยังสามารถถูกลบได้โดย user คนอื่นที่อยู่ใน group practice ได้

### **EXAMPLE**

user02 ได้สร้างไฟล์ที่ชื่อว่า delete_me_2 ขึ้นมา
``` 
-rw-r--r-- 1 user02 practice 0 Jan  2 15:34 delete_me_2
```

แต่จะให้ user01 ทำการลบ delete_me_2
ซึ่งจะสามารถลบได้

```bash
user01@practicum:/home/basket $ ls -l
total 0
-rw-r--r-- 1 user02 practice 0 Jan  2 15:34 delete_me_2
user01@practicum:/home/basket $ rm -f delete_me_2
user01@practicum:/home/basket $
```

### วิธีการแก้ปัญหาคือใช้ sticky bit ใน directory basket

ขั้นตอนที่ 1 ปรับ permission ของ directory basket ให้เป็น 777 ก่อน
```
chmod 777 basket/
```

ขั้นตอนที่ 2 ปรับ permission ของ directory basket โดยใส่ +t ลงไป
```
chmod +t basket/
```
ตอนนี้ basket จะมี t ขึ้นมาแล้ว
```
drwxrwxrwt  2 root   practice 4096 Jan  2 15:36 basket
```

สมมติว่าไฟล์ test สร้างโดย user01 และ user02 ไม่มีสิทธิ์ที่จะแก้ไขหรือลบได้เลย ถึงแม้ว่าจะอยู่ใน group เดียวกัน
```bash
user02@practicum:/home/basket $ ls
test
user02@practicum:/home/basket $ rm -f test
rm: cannot remove 'test': Operation not permitted
```

# การสร้าง shortcut สำหรับ directory ใดๆ

ในที่นี้เราจะสร้าง shortcut /home/basket/ ไว้ที่ home ของ user01 และ user02 ซึ่งจะทำได้ 2 คำสั่ง

```bash
ln -s ../basket
```

```bash
ln -s /home/basket
```
คำสั่งแรกจะมีผลลัพธ์เหมือนกับคำสั่งที่ 2 เมื่ออยู่ที่ directory /home/userxx เท่านั้น


ผลลัพธ์เมื่อสร้าง shortcut เรียบร้อยแล้ว
```bash
user01@practicum:~ $ ls
basket
```