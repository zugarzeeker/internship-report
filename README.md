# Internship Report
รายงานการฝึกงานที่ Runnables

## Runnables
บริษัท Software House [http://runnables.co.th](http://runnables.co.th/)


### Day 1 - 01/06/2016
ก่อนหน้านี้เคยคุยกันกับพี่ที่ทำงานที่นี่มาก่อนแล้ว 
เมื่อมาที่บริษัทพี่อธิบายการทำงานเริ่มต้นของวันนี้ ก็ได้ให้งานมาชิ้นหนึ่ง
ต้องทำหน้าเว็บส่วนของ Admin ที่พี่เค้าได้ Design มาให้เรียบร้อยแล้ว
ก็ต้องโหลดโปรแกรม Sketch ซึ่งเป็นเวอร์ชันทดลอง เพื่อมาดูไฟล์ Design
และ มีอีกโปรแกรมคือ Postman เพื่อ ทดสอบ REST ซึ่งไฟล์ทั้งสองนี้
อยู่ใน GoogleDrive

ให้พัฒนาด้วย AngularJS ซึ่งผมและเอกดนัยก็ได้ช่วยกันสองคน
ได้ใช้ YEOMAN (Yo, Grunt, Bower) โดยใช้ Gitlab ของบริษัท
เป็น Source Code Version Control และติดต่อกันด้วย Slack

เวลาส่วนใหญ่มักหมดไปกับอ่าน Docs นั่งหาข้อมุล ในวันนี้ผมได้ลองใช้ Generator `yo angular:directive exDirective`
gen route directive ต่างๆ

ในวันนี้ เอกดนัยได้ทำในส่วนของ Table ส่วนผมทำในส่วนของ Menu และ การ link ไปหน้าต่างๆ


### Day 2 - 02/06/2016
วันนี้ก็ยังคงได้ทำเกี่ยวกับ AngularJS เหมือนเดิม ได้ลองใช้ Factory, Service ส่งค่าข้ามหน้าได้ มีบ้างที่ใช้ร่วมกับ $http สะดวกดี
และได้ลองเช็ก API Backend ด้วย Postman ที่พี่ๆได้เตรียมไว้ให้ ส่วนที่ทำวันนี้เริ่มดึงค่าจาก API เริ่มติดต่อกับ Backend ไปแสดงผลเป็นตารางได้แล้ว

การแสดงผล Table ก็เลือกอยู่นานว่าจะใช้ตัวไหนดี ลอง ngTable ลงด้วย bower ง่ายดี แต่สุดท้ายก็ไม่ได้ใช้อยู่ดี ผมเขียนส่วน Table และ Pagination แบ่งหน้าเอง พอดูประกอบกับรายละเอียดที่ออกแบบไว้ ใน google sheet ที่พี่ๆเขียนไว้ กับ Postman ถึงเข้าใจ flow มากขึ้น
ส่วนเอกดนัย ทำส่วนของ หน้าแก้ไขข้อมูลของ article จัด form ต่างๆ เชื่อมกับ controller และช่วยกันกับผมในการรวมกันจากหน้า Table ของ Article ไปหน้า แก้ไข ของเอกดนัย 


### Day 3 - 03/06/2016
AngularJS เริ่มยิง API ต่างๆ แต่ก็ไปติดตรง Authentcation ที่ต้องได้ Token จาก Server หลังจากที่ Login ด้วย user และ password
ก็ต้องแก้ header http ของฝั่ง AngularJS หลายหน้าที่ยิงไปก็ติดปัญหา “Access Allow Origin...” ทำให้ต้อง Mock Data ไปก่อน
โดยเอาผลลัพธ์จาก Postman มาใช้แทนในรูปแบบของ Object ใน Javascript

ได้ช่วยกัน Refactor และ แก้ไข filestructure naming convention ต่างๆ ให้ดูเป็นมาตรฐานที่เข้าใจง่าย และเป็น best practice

เอกดนัยทำ Login Page เพิ่ม และทำส่วนที่เรียกใช้ REST API Method (put, post, ...) แต่ยังไม่ได้ทดสอบเนื่องจากติดปัญหา ก็เก็บ Token ไว้กะจะไปใช้ในการ set header ต่อไป 

ส่วนผมทำหน้าแสดงผล categories orders และแก้ไข pagination ของ Table ให้ตรงตามที่ Server Response format นั้นมา (จะได้ไม่ต้อง Response ทีละมากๆ) แบ่งหน้าแล้วค่อย Request ขอทีละหน้า โดยมีส่วนของรายการ label ที่แยกตาม case status ที่ให้มา (ใช้ ng-if สะดวกดี)

สรุปแล้วก็ยังเหลือเกี่ยวกับ Authentication และ ติดต่อ API ต่างๆ ได้คำแนะนำจากพี่ ให้แยก Factory ของ Event เพื่อจัดการ API ต่างๆ เพื่อให้ง่ายขึ้น ก็เดี๋ยวคงต้องศึกษา ngResource, header auth และทำส่วนที่เหลือต่อไป : )
