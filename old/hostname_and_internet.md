# Hostname

login เป็น root ก่อนเสมอ

```
sudo su
```

```bash
root@raspberry:~ $
```

ตอนนี้จะเห็นว่า username คือ pi และ hostname คิอ raspberry

## คำสั่งเปลี่ยนชื่อ hostname

```bash
hostnamectl set-hostname <ชื่อ hostname>
```

เมื่อเปลี่ยนชื่อแล้ว ให้ logout แล้ว remote ssh ใหม่
ก็จะเห็นชื่อ hostname ใหม่แล้ว

```bash
pi@practicum:~ $
```

## วิธีตรวจสอบ hostname

```bash
pi@practicum:~ $ cat /etc/hostname
practicum
pi@practicum:~ $ hostname
practicum
pi@practicum:~ $ echo $HOSTNAME
practicum
```

จากคำสั่งข้างบนจะเห็นว่า มีอยู่ 3 คำสั่งที่จะได้ hostname ของเรากลับมา

```bash
cat /etc/hostname
hostname
echo $HOSTNAME
```

# วิธีตรวจสอบว่าเชื่อมต่อ internet แล้วยัง?

## วิธีที่ 1

```bash
ping google.com
```

ผลลัพธ์

```
pi@practicum:~ $ ping google.com
PING google.com (74.125.24.113) 56(84) bytes of data.
64 bytes from sf-in-f113.1e100.net (74.125.24.113): icmp_seq=1 ttl=51 time=36.5 ms
64 bytes from sf-in-f113.1e100.net (74.125.24.113): icmp_seq=2 ttl=51 time=38.2 ms
64 bytes from sf-in-f113.1e100.net (74.125.24.113): icmp_seq=3 ttl=51 time=41.6 ms
64 bytes from sf-in-f113.1e100.net (74.125.24.113): icmp_seq=4 ttl=51 time=36.3 ms
64 bytes from sf-in-f113.1e100.net (74.125.24.113): icmp_seq=5 ttl=51 time=36.4 ms
.
.
.
```

เมื่อกด ctrl + c ก็จะหยุดทำงานทันที แล้วจะได้ข้อความนี้มา

```
--- google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4007ms
rtt min/avg/max/mdev = 36.334/37.819/41.626/2.025 ms
```

## วิธีที่ 2

```
curl ipinfo.io
```

ผลลัพธ์

```
{
  "ip": "xxx.xxx.xxx.xxx",
  "hostname": "YOURHOSTNAME",
  "city": "YOURCITY",
  "region": "YOURREGION",
  "country": "TH",
  "loc": "XX.XXXXX,XXX.XXXX",
  "org": "Your ISP",
  "postal": "XXXXX",
  "timezone": "Asia/Bangkok",
  "readme": "https://ipinfo.io/missingauth"
}
```
