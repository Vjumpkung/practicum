# Glob Pattern

- `?` หมายถึง ตัวอักษรอะไรก็ได้ 1 ตัวอักษร
- `*` หมายถึง ข้อความอะไรก็ได้
- `[]` หมายถึง มีตัวอักษรที่อยู่ใน `[` `]` เช่น `[ABC]` หมายถึงมี A หรือ B หรือ C อยู่ในข้อความนั้น หรือเป็นช่วงก็ได้ เช่น `[A-E]` หมายถึง ตัวอักษร `A B C D E`
- `!` หมายถึง ไม่เอาตัวอักษรนี้เช่น `[!ABC]` หมายถึง ไม่เอา `A B C`
- `{}` หมายถึง list ไว้ใช้หา pattern มากกว่า 1 กรณี example `{???.conf,*.???}`
- `|` หมายถึง เครื่องหมายหรือใช้ร่วมกับ `()` ในการจะทำให้ pattern มีมากกว่า 1 กรณี

## ตัวอย่างการใช้งาน glob pattern

### ตัวอย่างที่ 1

```bash
ls /etc/*.???
```

ตัวนี้หมายถึง ข้างหน้าเป็นอะไรก็ได้และมี `.` คั่นระหว่างกลาง และ `???` หมายถึง ตัวอักษรอะไรก็ได้ 3 ตัว

### output

```bash
/etc/issue.net  /etc/locale.gen  /etc/resolv.conf.bak  /etc/vdpau_wrapper.cfg
```

### ตัวอย่างที่ 2

```
tree -L 1 -C /etc/l[io]*
```

`l[io]*` หมายความว่า ขึ้นต้นด้วย l และประกอบด้วย i หรือ o และ ต่อด้วยข้อความอะไรก็ได้

### output

```
/etc/libaudit.conf [error opening dir]
/etc/libblockdev
└── conf.d
/etc/libnl-3
├── classid
└── pktloc
/etc/libpaper.d
/etc/libreoffice
├── psprint.conf
├── registry
├── sofficerc
└── soffice.sh
/etc/lightdm
├── keys.conf
├── lightdm.conf
├── lightdm-gtk-greeter.conf
├── pi-greeter.conf
└── users.conf
/etc/lighttpd
├── conf-available
└── conf-enabled
/etc/locale.alias [error opening dir]
/etc/locale.gen [error opening dir]
/etc/localtime [error opening dir]
/etc/logcheck
├── ignore.d.server
├── violations.d
└── violations.ignore.d
/etc/login.defs [error opening dir]
/etc/logrotate.conf [error opening dir]
/etc/logrotate.d
├── alternatives
├── apt
├── bootlog
├── btmp
├── cups-daemon
├── dpkg
├── exim4-base
├── exim4-paniclog
├── rsyslog
├── sane-utils
└── wtmp

7 directories, 21 files
```

### ตัวอย่างที่ 3

```
ls /etc/{???.conf,*.???}
```

คำอธิบาย

- `???.conf` ขึ้นต้นด้วยตัวอักษร 3 ตัว และ ต่อด้วย `.conf`
- `*.???` ข้างหน้าเป็นอะไรก็ได้ และคั่นด้วย `.` และ ลงท้ายด้วย ตัวอักษร 3 ตัว

### output

```
/etc/gai.conf
/etc/issue.net
/etc/locale.gen
/etc/pam.conf
/etc/pip.conf
/etc/resolv.conf.bak
/etc/ucf.conf
/etc/vdpau_wrapper.cfg
```

### ตัวอย่างที่ 4 (กรณีพิเศษ)

```
ls -la .+(ba*|pr*)
```

`.+(ba*|pr*)` หมายถึง ขึ้นต้นด้วย `.` และ เอาที่ต่อด้วย ba หรือ pr และข้างหลังเป็นอะไรก็ได้ ซึ่งต้องเชื่อมด้วย `+` เพราะ `.` เชื่อมได้แค่กรณีเดียว

### output

```
-rw------- 1 pi pi  916 Jan  2 21:06 .bash_history
-rw-r--r-- 1 pi pi  220 Jul  1  2022 .bash_logout
-rw-r--r-- 1 pi pi 3523 Jul  1  2022 .bashrc
-rw-r--r-- 1 pi pi  807 Jul  1  2022 .profile
```

ถ้าไม่ใส่เครื่องหมาย `+` จะ error

```
-bash: syntax error near unexpected token `('
```
