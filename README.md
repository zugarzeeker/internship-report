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


### Day 4 - 06/06/2016
Auth ได้แล้ว มีการเก็บ Token และ เช็กสถานะ Login ร่วมกับ LocalStorage Redirect ได้ Logout ได้ด้วย
Refactor Code ใช้ ngResource -> Set Header Authorization Bearer + Token พอแยก โค้ดเป็นส่วน apiFactory
แล้วจัดการ Event ต่างๆพวกนี้ แล้วทำให้ง่ายต่อการจัดการมาก แก้ไขและ Debug ได้ง่าย แต่ก่อนแยก เป็น 1 Factory ต่อ การจัดเตรียมข้อมูลสำหรับ Controller การ Delete ข้อมูล แล้ว Load ข้อมูลแสดงตารางใหม่ได้ นอกจากนี้ยังได้แก้เกี่ยวกับ AppConstant ต่างๆใหม่ ทั้ง route menu ด้วย แยกเพื่อให้จัดการได้ง่าย แยกโค้ด authFactory ด้วย

ผมทำส่วนเกี่ยวกับ Token และ ส่วนที่ติดต่อ API เป็นส่วนมาก (apiFactory) รวมถึง LocalStorage ที่เอาไว้เก็บ Token ด้วย (authFactory) รวมหน้าส่วนที่เป็นตาราง แล้วส่งต่อให้เอกดนัยเชื่อม Edit กับ Delete ต่อไป

เอกดนัยทำส่วนเกี่ยวกับ View และ Controller เป็นส่วนมากทั้งการ Delete Confirm Delete ร่วมกับ UI bootstrap (+Angular Confirm) และ Locales แสดงหลายภาษาตามที่ได้จาก API

ในวันนี้สามารถ GET PUT POST DELETE ได้ครบแล้ว โดยไม่ติด Access Allow Origin แบบวันก่อนเนื่องจากพี่ที่บริษัทได้แก้ให้เรียบร้อยแล้ว : )


### Day 5 - 07/06/2016
เมื่อคืนได้ Refactor เป็น tableFactory จัดการเกี่ยวกับ Pagination และ Render Table รวมถึง function ต่างๆด้วยที่ต้องใช้
เพื่อให้ใช้งานได้หลายๆ controller จะได้นำไปใช้คล้ายๆกัน โค้ดแก้ไขง่ายขึ้น

ในวันนี้ จึงได้นำมาใช้ต่อ และ เขียนโค้ดอ่านง่ายมากขึ้น เริ่มมี pattern ที่สามารถใช้ซ้ำๆได้ จาก factory ที่แยกออกไป ของ Angular 
ที่เขียนไว้ ต่างจากวันแรกๆ ที่ยังไม่ค่อยเข้าใจมากนัก

เอกดนัยทำเกี่ยวกับ Locales ซะส่วนใหญ่ในวันนี้ การแสดงผลหลายภาษา จำพวก content ต่างๆ แก้ categories ให้สามารถ drag drop ได้ จัดลำดับ และ ส่งค่ากลับไปยัง api ได้

ผมแก้ไขเกี่ยวกับ การเรียก api route และ Refactor ให้สามารถส่งตัว function callback ไปทำงานแทนที่ จะ เขียนให้ต่างกันแต่ละ controller ทำให้ผมได้ลอง get locale api มาเพื่อเก็บไว้ก่อนว่ามีกี่ภาษา แล้วจึงค่อยใช้แยกกัน เพื่อให้เอกดนัยทำงานง่ายขึ้น


### Day 6 - 08/06/2016
ผมและเอกดนัยได้ลองเกี่ยวกับ lodash, ui-select, modal ของ ui-bootstrap angular, angular-ui/ui-select คล้ายๆ
Angular taginput

ช่วยกันทำ page จัดการเกี่ยวกับตารางสี เพื่อให้เลือกได้ drag & drop ตารางสีแสดงผลตามค่า RGB รวมถึง save ข้อมูลส่งกลับ 

เอกดนัยทำส่วน product edit และ จัดการ categories ของสินค้า

ผมทำส่วนของ currencies ที่เกี่ยวกับค่าเงินต่างๆ ธนาคาร และ เลขที่บัญชี

ซึ่ง product-edit และ currencies เป็น page ด้วยความซับซ้อนจึงทำให้ใช้เวลานาน

จากที่พี่ๆแนะนำมาพอได้ลองใช้ lodash กันจริงๆ แล้ว แทนที่จะวน for เพื่อจัดการ object ต่างๆ ก็ง่ายขึ้น
code ก็ซับซ้อนน้อยลง แถม Doc ของ lodash อ่านง่ายด้วย : )


### Day 7 - 09/06/2016
ช่วยกันแก้งานตาม Issue ที่มีใน docs ที่พี่เค้าเตรียมไว้ให้ https://docs.google.com/spreadsheets/d/1XY-Dj-7FxyHJt-HrxuvRdgADd2YLWxxbgUqmMhcoQmE/edit#gid=0

ผมเปลี่ยนจากการใส่ Header Authentication ทุก Function ที่เรียก Api เป็น Http Interceptor และเขียนแยกเป็น Factory
บางครั้งต้องใช้ api จากข้างนอกจึงใช้ interceptor ในการเปลี่ยนแปลงและจัดการ Header ให้ต่างกัน ซึ่งเขียนให้คอยดักจับ Request และ Response ต่างๆ เพื่อตรวจสอบ Token และ Error ต่างๆ เพื่อ Redirect ให้ User ทำการล็อกอิน นอกนั้นก็ไล่แก้งานตาม issue ซะส่วนใหญ่

เอกดนัย ทำส่วนของ Product edit โดยทำให้การเลือกสีใน UI Select  มีการ preview ค่าให้ผู้ใช้เห็นแบบ Real-time และทำให้การลบ/เพิ่มสีทำงานได้อย่างถูกต้อง
เพิ่มการแจ้งเตือนเมื่อ user ทำ action ต่างๆ สำเร็จ/ล้มเหลว ด้วย toastr ซึ่งเป็นตัว Notification ที่จะเด้งขึ้นมาบนหน้าจอ
