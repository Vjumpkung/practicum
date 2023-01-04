# ประวัติของ unix
**Unix คือ**  
เป็นระบบปฏิบัติการชนิดหนึ่ง ตอบสนองการทำงานแบบระบบเปิด(Open System) ไม่ผูกติดกับระบบใดระบบหนึ่งหรือเป็นอุปกรณ์ยี่ห้อเดียวกัน ใช้งานในลักษณะผู้ใช้หลายคน(Multi-users) สามารถทำงานได้หลายงานพร้อมกันในเวลาเดียวกัน (Multi-tasking) มีความสามารถเชื่อมโยงเป็นระบบเครือข่าย และการจัดสรร ทรัพยากรร่วมกัน  
**ประวัติ Unix**

-   ในทศวรรษที่ 60 สถาบันเทคโนโลยีแมสซาชูเซตส์ (MIT) , AT&T Bell Labs และบริษัท General Electric ได้ร่วมมือกันวิจัยระบบปฏิบัติการที่ชื่อว่า Multics โดยมีจุดมุ่งหมายเพื่อทำงานบนเครื่องเมนเฟรมรุ่น GE-645
-   Ken Thompson ซึ่งเป็นหนึ่งในทีมพัฒนาได้เขียนเกมบนเครื่อง GE-645 ชื่อว่าเกม Space Travel และพบปัญหาว่าเกมทำงานได้ช้ากว่าที่ควร เขาจึงย้ายมาเขียนเกมใหม่บนเครื่อง PDP-7 ของบริษัท DEC แทนด้วยภาษาแอสเซมบลี
-   ระบบปฏิบัติการนี้มีชื่อว่า UNICS ย่อมาจาก Uniplexed Information and Computing System เนื่องจากว่าการออกเสียงสามารถสะกดได้หลายแบบ และพบปัญหาชื่อใกล้เคียงกับ Multics ภายหลังจึงเปลี่ยนชื่อเป็น Unix
-   การพัฒนายูนิกซ์ในช่วงนี้ยังไม่ได้รับความสนับสนุนจาก Bell Labs เมื่อระบบพัฒนามากขึ้น Thompson และ Ritchie จึงเพิ่มความสามารถในการประมวลผลคำบนเครื่อง PDP-11/20 และเริ่มได้รับการตอบรับจาก Bell Labs ในปีค.ศ. 1970 ระบบปฏิบัติการยูนิกซ์จึงได้รับการเรียกชื่ออย่างเป็นทางการ หนังสือ UNIX Programmer’s Manual ตีพิมพ์ครั้งแรกวันที่ 3 พฤศจิกายน ค.ศ. 1971
-   ค.ศ. 1973 ได้เขียนยูนิกซ์ขึ้นมาใหม่ด้วยภาษาซี ทำให้สะดวกต่อการนำยูนิกซ์ไปทำงานบนเครื่องชนิดอื่นมากขึ้น ทาง AT&T ได้เผยแพร่ยูนิกซ์ไปยังมหาวิทยาลัย และหน่วยงานต่างๆ ของรัฐบาล การใช้งานเปิดเผย source code ยกเว้น kernel ส่วนที่เขียนด้วยภาษาแอสเซมบลี
-   ค.ศ. 1982 AT&T นำยูนิกซ์ 7 มาพัฒนาและออกขายในชื่อ Unix System III แต่บริษัทลูกของ AT&T ชื่อว่า Western Electric ยังคงนำยูนิกซ์รุ่นเก่ามาขายอยู่เช่นกัน เพื่อยุติความสับสนทางด้านชื่อ AT&T จึงรวมการพัฒนาทั้งหมดจากบริษัทและมหาวิทยาลัยต่างๆใน Unix System V ซึ่งมีโปรแกรมอย่าง vi ที่พัฒนาโดย Berkeley Software Distribution (BSD) จากมหาวิทยาลัยแคลิฟอร์เนีย เบิร์กลีย์ รวมอยู่ด้วย ยูนิกซ์รุ่นนี้สามารถทำงานได้บนเครื่อง VAX ของบริษัท DEC
-   ยูนิกซ์รุ่นที่เป็นการค้าไม่เปิดเผย source code อีกต่อไป ทางมหาวิทยาลัยแคลิฟอร์เนีย เบิร์กลีย์ จึงพัฒนายูนิกซ์ของตัวเองต่อเพื่อเป็นทางเลือกกับ System V การพัฒนาที่สำคัญที่สุดคือเพิ่มการสนับสนุนโพรโทคอลสำหรับเครือข่าย TCP/IP เข้ามา
-   บริษัทอื่นๆ เริ่มพัฒนายูนิกซ์บนเครื่องคอมพิวเตอร์ระบบของตนเอง โดยส่วนมากใช้ยูนิกซ์ที่ซื้อสัญญามาจาก System V แต่บางบริษัทเลือกพัฒนาจาก BSD แทน
-   AT&T ยังคงพัฒนาความสามารถต่างๆ เข้าสู่ยูนิกซ์ System V และรวมเอา Xenix (ยูนิกซ์ของบริษัทไมโครซอฟท์) , BSD และ SunOS เข้ามารวมใน System V Release 4 (SVR4) เพื่อเป็นผลิตภัณฑ์หนึ่งเดียวสำหรับลูกค้า ซึ่งเพิ่มราคาขึ้นอีกมาก
-   หลังจากนั้นไม่นาน AT&T ขายสิทธิ์ในการถือครองยูนิกซ์ให้กับบริษัทโนเวลล์ และโนเวลเองได้สร้างยูนิกซ์ของตัวเองที่ชื่อ UnixWare ซึ่งพัฒนามาจากระบบปฏิบัติการ NetWare เพื่อแข่งกับระบบปฏิบัติการวินโดวส์เอ็นทีของไมโครซอฟท์
-   ค.ศ. 1995 โนเวลขายส่วนต่างๆ ของยูนิกซ์ให้กับบริษัท Santa Cruz Operation (SCO) โดยโนเวลยังถือลิขสิทธิ์ของยูนิกซ์ไว้ ค.ศ. 2000 SCO ขายสิทธิ์ส่วนของตนเองให้กับบริษัท Caldera ซึ่งเปลี่ยนชื่อภายหลังเป็น SCO Group ซึ่งเป็นสาเหตุในการดำเนินคดีละเมิดลิขสิทธิ์กับลินุกซ์

ที่มา : https://maluvly.wordpress.com/ประวัติความเป็นมาของ-unix/