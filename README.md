# Internship Report

รายงานการฝึกงานที่ Runnables
* ศุภณัฐ อภิกุลวณิช
* เอกดนัย สิทธิโกศล


## Runnables

บริษัท Software House  [http://runnables.co.th](http://runnables.co.th/)


## Day 1 - *01/06/2016*

ก่อนหน้านี้เคยคุยกันกับพี่ที่ทำงานที่นี่มาก่อนแล้ว
เมื่อมาที่บริษัทพี่อธิบายการทำงานเริ่มต้นของวันนี้ ก็ได้ให้งานมาชิ้นหนึ่ง
ต้องทำ Frontend ส่วนของ Admin จัดการเว็บ [Microbrik](http://microbrik.com/) ที่พี่เค้าได้ Design มาให้เรียบร้อยแล้ว
ก็ต้องโหลดโปรแกรม Sketch ซึ่งเป็นเวอร์ชันทดลอง เพื่อมาดูไฟล์ Design
และ มีอีกโปรแกรมคือ Postman เพื่อ ทดสอบ REST API ซึ่งไฟล์ทั้งสองนี้
อยู่ใน GoogleDrive ที่รวบรวมข้อมูลต่างๆเกี่ยวกับ Project นี้ไว้

พัฒนาด้วย AngularJS

โดยใช้ YEOMAN (Yo, Grunt, Bower) เป็น Generator, ใช้ [Gitlab](https://about.gitlab.com/) ของบริษัท
เป็น Source Code Version Control และติดต่อกันผ่าน [Slack](https://slack.com/)

เวลาส่วนใหญ่มักหมดไปกับอ่าน Docs นั่งหาข้อมูล ในวันนี้ได้ลองใช้ Generator `yo angular:directive myDirective`
ในการ generate route, directive หลักๆของ Project

**ศุภณัฐ**

ผมทำในส่วนของ Menu และ การ link ไปหน้าต่างๆ

**เอกดนัย**

ผมทำในส่วนของ Table โดย โดยดึงข้อมูลส่วนต่างๆมาจาก Backend เพื่อแสดงผล

## Day 2 - *02/06/2016*

วันนี้ก็ยังคงได้ทำเกี่ยวกับ AngularJS เหมือนเดิม ได้ลองใช้ Factory, Service ส่งค่าข้ามหน้าได้ มีบ้างที่ใช้ร่วมกับ $http สะดวกดี
และได้ลองเช็ก API Backend ด้วย Postman ที่พี่ๆได้เตรียมไว้ให้ ส่วนที่ทำวันนี้เริ่มดึงค่าจาก API เริ่มติดต่อกับ Backend ไปแสดงผลเป็นตารางได้แล้ว

การแสดงผล Table ก็เลือกอยู่นานว่าจะใช้ตัวไหนดี ลอง ngTable ลงด้วย bower ง่ายดี แต่สุดท้ายก็ไม่ได้ใช้อยู่ดี

**ศุภณัฐ**

ผมเขียนส่วน Table และ Pagination แบ่งหน้าเอง พอดูประกอบกับรายละเอียดที่ออกแบบไว้ ใน google sheet ที่พี่ๆเขียนไว้ กับ Postman ถึงเข้าใจ flow มากขึ้น

**เอกดนัย**

ผมทำส่วนของ หน้าแก้ไขข้อมูลของ Article จัด form ต่างๆให้ตรงกับ Design แล้วเชื่อมข้อมูลกับ controller พร้อมทั้งหา Text editor *(WYSIWYG - What You See Is What You Get)* โดยสุดท้ายใช้ CKEditor เพราะสมบูรณ์ที่สุดเท่าที่หาได้

และจึงช่วยกันหาวิธีส่งข้อมูลจากหน้าแสดงผล Articles ทั้งหมด ไปหน้า Edit Article


## Day 3 - *03/06/2016*

AngularJS เริ่มยิง API ต่างๆ แต่ก็ไปติดตรง Authentcation ที่ต้องได้ Token จาก Server หลังจากที่ Login ด้วย email และ password

ต้องแก้ header http ของฝั่ง Client หลายหน้าที่ยิงไปก็ติดปัญหา “Access-Control-Allow-Origin” ทำให้ต้องสร้าง Mock Data ใช้ในการ Test ไปก่อน

โดยเอาผลลัพธ์จาก Postman มาใช้แทนในรูปแบบของ Object ใน Javascript

ช่วยกัน Refactor และ แก้ไข File structure, Naming convention ต่างๆ ให้ดูเป็นมาตรฐานที่เข้าใจง่าย และเป็น Best practice

**ศุภณัฐ**

ผมทำหน้าแสดงผล categories orders และแก้ไข pagination ของ Table ให้ตรงตามที่ Server Response format นั้นมา (จะได้ไม่ต้อง Response ทีละมากๆ) แบ่งหน้าแล้วค่อย Request ขอทีละหน้า โดยมีส่วนของรายการ label ที่แยกตาม case status ที่ให้มา (ใช้ ng-if สะดวกดี)

**เอกดนัย**

ทำ Login Page เพิ่ม และทำส่วนที่เรียกใช้ REST API Method (PUT, POST, ...) แต่ยังไม่ได้ทดสอบเนื่องจากติดปัญหาที่ Server ไม่รับการติดต่อ (*Access-Control-Allow-Origin ที่กล่าวไว้ข้างบน*)

สรุปแล้วก็ยังเหลือเกี่ยวกับ Authentication และ ติดต่อ API ต่างๆ ได้คำแนะนำจากพี่ ให้แยก Factory ของ Event เพื่อจัดการ API ต่างๆ เพื่อให้ง่ายและโค้ดสะอาดขึ้น โดยต้องศึกษาเกี่ยวกับ ngResource, Header auth เพิ่มเติม


## Day 4 - *06/06/2016*

Authenticate สำเร็จ มีการเก็บ Token และ เช็กสถานะ Login ร่วมกับ LocalStorage

Redirect เมื่อ User ยังไม่ Login ได้ รวมทั้ง Logout ได้ด้วย

Refactor Code โดยใช้ ngResource ใน Set Header Authorization `Bearer: myToken` ใช้ร่วมกันทั้ง App

ซึ่งหลังจากแยก โค้ดเป็นส่วน `apiFactory`
แล้วจัดการ Event ต่างๆพวกนี้ แล้วทำให้ง่ายต่อการจัดการมาก
สามารถแก้ไขและ Debug ได้ง่าย จากที่เคยแยก เป็น 1 Factory ต่อ 1 ประเภทข้อมูล

ทำให้หลังจาก Delete ข้อมูล แล้ว Reload ตารางแสดงข้อมูลหลังจากเปลี่ยนแปลงแล้วได้

นอกจากนี้ยังได้แก้เกี่ยวกับ AppConstant ต่างๆใหม่ ทั้ง route menu ด้วย แยกเพื่อให้จัดการได้ง่าย แยกโค้ด authFactory ด้วย

**ศุภณัฐ**

ผมทำส่วนเกี่ยวกับ Token และ ส่วนที่ติดต่อ API เป็นส่วนมาก (apiFactory) รวมถึง LocalStorage ที่เอาไว้เก็บ Token ด้วย (authFactory) รวมหน้าส่วนที่เป็นตาราง แล้วส่งต่อให้เอกดนัยเชื่อม Edit กับ Delete ต่อไป

**เอกดนัย**

ทำส่วนเกี่ยวกับ View และ Controller ทั้งการ Delete ข้อมูลออกจากตาราง โดยมีการให้ User ต้อง Confirm Delete ก่อนเพื่อป้องกันข้อผิดพลาด โดยใช้ bootstrap (ซึ่งจัดการโดย package ชื่อ angular-confirm-modal) และทำ Locales ให้กับการ Edit article ซึ่งโค้ดยังซับซ้อนและอ่านยากมากเกินไป ต้องหาวิธี Refactor ให้ดีขึ้น

ในวันนี้สามารถ GET PUT POST DELETE ได้ครบ โดยไม่ติด Access-Control-Allow-Origin แบบวันก่อนเนื่องจากพี่ได้แก้ให้เรียบร้อย


## Day 5 - *07/06/2016*

ตอนกลางคืนวันที่ 4 ได้กลับไป Refactor ส่วนจัดการข้อมูลของ Table ให้เป็น `tableFactory` ซึ่งจัดการเกี่ยวกับ Pagination และ Render Table รวมถึง function ต่างๆที่ต้องใช้
เพื่อให้ใช้งานได้หลายๆ Controller และลด Rebundancy

ในวันนี้ จึงได้นำมาใช้ต่อ ทำให้โค้ดอ่านง่ายมากขึ้น เริ่มมี pattern ที่สามารถใช้ซ้ำๆได้ จาก factory ที่แยกออกไปอย่างเป็นระบบ ของ Angular
ที่เขียนไว้ ต่างจากวันแรกๆ ที่ยังไม่ค่อยเข้าใจมากนัก

**ศุภณัฐ**

ผมแก้ไขเกี่ยวกับ การเรียก api route และ Refactor ให้สามารถส่งตัว function callback ไปทำงานแทนที่ จะ เขียนให้ต่างกันแต่ละ controller ทำให้ผมได้ลอง get locale api มาเพื่อเก็บไว้ก่อนว่ามีกี่ภาษา แล้วจึงค่อยใช้แยกกัน เพื่อให้เอกดนัยทำงานง่ายขึ้น

**เอกดนัย**

ทำเกี่ยวกับ Locales (การแสดงผลหลายภาษา) ในส่วนที่ต้องใช้ แก้ Categories ให้สามารถ Drag&Drop ในการจัดลำดับของข้อมูลได้ โดยทันทีที่เปลี่ยนลำดับ ใน Backend ก็จะเปลี่ยนตามทันที


## Day 6 - *08/06/2016*

ได้ลองเกี่ยวกับ lodash, ui-select, modal ของ ui-bootstrap angular, angular-ui/ui-select คล้ายๆ
Angular taginput โดยมีพื้นฐานมาจาก jQuery taginput

ช่วยกันทำ page จัดการเกี่ยวกับตารางสี เพื่อให้เลือกได้ drag & drop ตารางสีแสดงผลตามค่า RGB รวมถึง save ข้อมูลส่งกลับ

**ศุภณัฐ**

ผมทำส่วนของ currencies ที่เกี่ยวกับค่าเงินต่างๆ ธนาคาร และ เลขที่บัญชี ซึ่งเป็นหน้าที่มีความซับซ้อนจึงทำให้ใช้เวลานาน

**เอกดนัย**

ทำส่วน product edit และ จัดการ categories ของสินค้า ซึ่งหน้า Product edit ถือว่าเป็นส่วนหลักของธุรกิจ ทำให้มีรายละเอียดเยอะ และแทบจะต้องใช้ทุก Components จากหน้าอื่นๆมารวมกันหมด ทำให้การ Refactor ที่เคยทำไปก่อนหน้านี้ส่งผลดีอย่างมาก เพราะหลายๆอย่างก็สามารถนำมาใช้ได้ทันทีโดยไม่ต้องเขียนซ้ำใหม่

จากที่พี่ๆแนะนำให้ลองใช้ lodash ก็พบว่าแทนที่จะวน for เพื่อจัดการ object ต่างๆ การจัดการข้อมูลใน Object ก็ทำได้ง่ายขึ้น รวมถึงโค้ดยังสื่อความหมายได้ดีขึ้นด้วย
ดังตัวอย่างเช่น
```javascript
// Old code
for (var i=0; i<myObj.array.length; i++) {
	// Use myObj.array[i] as an element
}
// Lodash
_(myObj.array).forEach(function(element) {
	// Use element
});
```
ซึ่งข้อดีอีกอย่างของ Library นี้ก็คือ Documentation เขียนได้ละเอียดและอ่านง่าย ทำให้ไม่ต้องหาตัวอย่างจากแหล่งอื่นศึกษามากนัก


## Day 7 - *09/06/2016*

ช่วยกันแก้งานตาม Issue ที่มีใน docs ที่พี่ๆช่วย List ไว้ตาม Link นี้:
[Issue Tracker spreadsheet](https://docs.google.com/spreadsheets/d/1XY-Dj-7FxyHJt-HrxuvRdgADd2YLWxxbgUqmMhcoQmE/edit#gid=0)

**ศุภณัฐ**

ผมเปลี่ยนจากการใส่ Header Authentication ทุก Function ที่เรียก Api เป็น Http Interceptor และเขียนแยกเป็น Factory
บางครั้งต้องใช้ api จากข้างนอกจึงใช้ interceptor ในการเปลี่ยนแปลงและจัดการ Header ให้ต่างกัน ซึ่งเขียนให้คอยดักจับ Request และ Response ต่างๆ เพื่อตรวจสอบ Token และ Error ต่างๆ เพื่อ Redirect ให้ User ทำการล็อกอิน นอกนั้นก็ไล่แก้งานตาม issue ซะส่วนใหญ่

**เอกดนัย**

ทำส่วนของ Product edit โดยทำให้การเลือกสีใน ui-select มีการ preview ค่าให้ผู้ใช้เห็นแบบ Real-time และทำให้การลบ/เพิ่มสีทำงานได้อย่างถูกต้อง
เพิ่มการแจ้งเตือนเมื่อ user ทำ action ต่างๆ สำเร็จ/ล้มเหลว ด้วย `toastr` ซึ่งเป็นตัว Notification ที่จะเด้งขึ้นมาบนหน้าจอ

และทำ Banner edit ซึ่งจะมีการผูกข้อมูลว่า Banner นี้ควรจะโยงไปยัง Article ไหน ซึ่งต้องใช้ ui-select อีกครั้ง แต่คราวนี้ต้องทำให้ทุกครั้งที่ User พิมพ์ข้อความ (ชื่อบทความ) ลงไปในช่องค้นหา จะต้องเรียก API เพื่อนำรายชื่อของบทความที่ตรงตามคำค้นหามาแสดง

แต่เมื่อเขียนจนเสร็จ ก็พบว่าหากพิมพ์ข้อความต่อๆกันเยอะๆ จะทำให้โดน Reject จาก Server เพราะส่ง Request ถี่เกินไป (เนื่องจากใช้วิธีเช็กว่า หากข้อความที่พิมพ์เปลี่ยน ก็ให้นำข้อความใหม่ไปค้นหาทันที) ทำให้ต้องใส่ `refresh-delay` ลงไปเป็น Attribute ของตัว ui-select ซึ่งทำให้มีการหน่วงเวลาก่อนที่จะทำข้อความที่พิมพ์ไปทำการค้นหา


## Day 8 - *10/06/2016*

สำหรับโปรเจคเก่าก็ได้ถือว่าจบเท่านั้นก่อน แล้วถ้าแก้ไขเล็กน้อยก็คงจะมีเพิ่มทีหลัง

พี่ๆได้ให้งานใหม่ โดยยังคงทำของ [Microbrik](http://microbrik.com/about) อยู่ ซึ่งรอบนี้ทำเรื่องการ Pixelate เปลี่ยนรูปของผู้ใช้ให้เป็น Pixel art โดยใช้การ Dithering

ใช้ AngularJS ES6

โดยเริ่มต้นด้วยการดูโปรเจคที่เกี่ยวกับ ES6 ต่างๆ ของใน gitlab ที่พี่เปิดสิทธิ์ให้เข้าไปดูได้ เพื่อให้เห็นแนวทางการโค้ดโดยรวม
เพราะโปรเจค ที่จะให้ทำภายหลังจะใช้ ES6 โดยรวมวันนี้ไม่ได้มีตัวงานออกมามากนัก เพราะต้องใช้เวลาศึกษาโครงสร้างของโปรเจคที่พี่ๆทำไว้แล้ว ไม่เหมือนโปรเจคเก่าที่เริ่มใหม่เองแทบทั้งหมด

ใช้ generator gulp-angular
แล้วไปเจอ gulp-angular-subtask ไว้ generate controller, factory, directive ต่างๆ ตอนแรก นึกว่าจะ gen ไม่ได้ซะอีก
ก็ต้องปรับตัวกับโปรเจคใหม่ที่พี่ให้ช่วยทำ ซึ่งพี่ๆก็ทำ Issue Tracker ไว้แบ่งงานเป็น Tasks ให้ไปเลือกเอาว่าจะทำอันไหนกันเอง

ES6 Syntax ดูสบายตากว่าเดิมมาก เพียงแต่ ไม่ค่อยคุ้นเคยหลายจุด เลยอาจจะต้องปรับตัวอีกสักพัก
ได้ใช้ `$rootScope.$emit(‘some-event’);` และ `$rootScope.$on(‘some-event’, callback);`

**ศุภณัฐ**

ผมแก้ในส่วนของการเลือกภาพ และแสดงผล การติดต่อกันระหว่าง Controller เพื่อให้ notify ไป update ได้
ระหว่างส่วน Sidebar กับ Workspace

**เอกดนัย**

แก้เรื่องการ crop ภาพ ใช้ ngCropper แล้วพบว่าติดปัญหาที่ว่า เมื่อเปลี่ยนขนาดกรอบของตัว Crop ในโค้ดแล้ว แต่ตัว Crop ไม่เปลี่ยนขนาดตาม จึง Fork ตัว ngCropper มาจากผู้พัฒนา
ปรับปรุง แล้ว แก้ไขไฟล์ `bower.json` ของโปรเจคที่ทำ ให้ใช้ของตัวเองแทน พร้อมส่ง Pull request กลับไปยังโปรเจคหลักด้วย


## Day 9 - *13/06/2016*

เริ่มต้นด้วยการลอง Build Project ที่ทำเว็บ Admin ด้วย AngularJS เอาไปทดสอบ บน Server ของบริษัท แล้วพบว่ามีปัญหามากมาย จากการใช้ grunt build โดยเวลา Uglify Minify แค่พิมพ์ `/views/mydirective.html` จากที่จริงๆ ต้องใช้  `views/mydirective.html`

ซึ่งแค่นี้ ก็ส่งผลให้ build ไม่ผ่านแล้ว

ปัญหาที่พบอีกอย่างคือ CKEditor ที่ใช้ เกิดปัญหาตอน Build เพราะ import ไฟล์ที่ต้องใช้มาไม่ครบ ซึ่งมีทางแก้หลายวิธี เช่น
* ignore การ build ตัว ckeditor จากนั้นดึงผ่าน CDN เข้ามาตรงๆ
* Import ไฟล์ที่ขาดไปด้วยตัวเอง
* ฯลฯ

การแก้ก็ต้องคิดถึง Dependency ต่างๆ ว่า คนอื่นในทีมที่ pull git ไป จะใช้งานได้ปกติ เผื่อต้องแก้ในอนาคต เลยค่อนข้างใช้เวลา พี่ๆ ที่บริษัท ก็ให้คำแนะนำหลายๆแบบ บอกวิธีแก้ที่เคยทำ ช่วยกันหาวิธีจากแหล่งต่างๆ จนสุดท้ายก็ Build ให้รันบน server ได้เรียบร้อยแล้ว

เมื่อแก้ปัญหาเสร็จ ก็กลับมาทำงาน Pixelate ต่อ

**ศุภณัฐ**

ผมได้แก้เพิ่มให้สามารถ Crop รูปแล้วส่งไปขั้นตอนต่อไปในการจัดการรูปได้ ซึ่งพี่ที่บริษัทได้เขียนให้แล้วคือ Dithering

**เอกดนัย**

แก้เกี่ยวกับ Menu ให้ Layout ถูกต้อง เพราะส่วนนี้พี่ๆยังไม่ได้แก้ให้เป็นไปตาม Design ใหม่ ยังใช้โค้ดจาก Design เวอร์ชั่นก่อนอยู่


## Day 10 - *14/06/2016*

**ศุภณัฐ**

ผมทำในส่วนของหน้า Output รูปภาพ จะมีรายการบอกว่าต้องใช้วัสดุจำนวนเท่าไรและราคาด้วย ในส่วนของหน้า Retouch ผม get ค่าสีต่างๆจาก API มาเพื่อใช้ต่อในส่วนของ Retouch ที่จำเป็นต้องแบ่ง Pixel เป็น Box ที่ใหญ่ขึ้น เพื่อนำไปแก้ไขสีในบริเวณจุดต่างๆ ของภาพ

**เอกดนัย**

ได้ทำเกี่ยวกับส่วน Pixelation suggestion แนะนำรายการ Preset ที่จะได้รูปผลลัพธ์แตกต่างกันออกไป

ซึ่งตอนแรกเจอปัญหา Dithering stack exceed เพราะสั่งให้ Dither ทุกๆ Presets พร้อมกัน จนประมวลผลเยอะเกินไป เลยใช้วิธี Timeout หน่วงเวลาการทำงานเอาไว้ ให้รอระยะเวลาหนึ่งก่อนค่อยสั่งให้ Preset ถัดไปทำ

ทำ loading modal ระหว่างรอประมวลผล dithering เพราะหากขนาดรูปที่ต้องการละเอียดมากๆแล้ว ก็จะใช้เวลาประมวลผลนานตามไป จึงควรมีการบอกผู้ใช้ว่ากำลังประมวลผลอยู่

## Day 11 - *15/06/2016*

**ศุภณัฐ**

วันนี้พี่ในบริษัทไปคุยกับลูกค้า ผมเลยไปด้วย โดยเรื่องที่คุยเกี่ยวกับ Datastructure และ วิธีการ Implement ต่างๆ

หลังจากกลับมาแล้ว ได้แก้ส่วนของ Retouch ต่อ ให้ Notify Subscribe ได้ เพื่อให้เชื่อมต่อกับส่วนที่แต่งรูป ที่พี่จะทำเป็น Directive แล้วเอามาประกอบกัน

**เอกดนัย**

วันนี้ลากิจเนื่องจากติดภารกิจเข้าร่วมงานฌาปณกิจศพของญาติ

ตอนกลางคืนได้ทำให้ CamanJS สามารถใช้ร่วมกับโปรเจคได้ แต่ก็ติดปัญหาที่ตัว Caman จะนำรูปจากผลลัพธ์การแต่งก่อนหน้ามาใช้เป็นฐานในการแต่งครั้งถัดไป เช่นเคยปรับความสว่างเพิ่มขึ้นเป็น 80 จาก 50 ไปแล้ว พอไปปรับขึ้นเป็น 90 ก็จะเหมือนกับมองรูปที่ผ่านการปรับเป็น 80 มาใช้เป็นรูปต้น ทำให้ค่าแสงที่ควรจะเป็น 90 กลายเป็นค่าที่ผิดเพี้ยนไป

ลองใช้ `caman.revert(false);` ซึ่งเป็นวิธีที่มีคนแนะนำมา แต่ก็ยังแก้ปัญหาไม่ได้ พรุ่งนี้จะต้องศึกษาต่อ

## Day 12 - *16/06/2016*

**ศุภณัฐ**

ส่วนมากทำเกี่ยวกับการ Retouch Image, และ Pixel Paint Tool บน Canvas ในวันนี้ได้ Directive AngularJS ในการวาดรูปเป็นช่องๆ เหมือน box pixel จากพี่ที่บริษัท ของงานเก่า แล้วนำมาใช้ต่อ ซึ่งจริงๆ Directive นี้ มาจากของเดิมที่เขียนด้วย jQuery แต่เพื่อให้ใช้ง่ายในการ ตกแต่งภาพใน Canvas ตอนนี้สามารถวาดรูปตกแต่งภาพใส่ข้อความได้แล้ว รวมถึงสามารถ Zoom In และ Zoom Out ได้ด้วย

ปัญหาที่เจอในตอนแรกคือรูปภาพที่ถูกส่งมาจากหน้าก่อน เมื่อไป Render บน Canvas ที่ทำเป็น Directive ไม่ยอมเปลี่ยนขนาดตามเนื่องจาก ค่าขนาดภาพที่ส่งไปในตอนแรก ไม่ได้เข้าไปด้วยที่เป็น Option แต่จะเริ่มทำงาน หลังจากที่มี action บางอย่างเกิดขึ้น จึงจะ update ซึ่งก็แก้ได้จากตัว Directive หรือใช้ `$timeout` เพื่อหน่วงไว้ก่อน

ช่วยกันกับเอกดนัย ทำ Page Output และ การสั่งซื้อสินค้าที่เป็นวัสดุในการทำตามรูปที่ Generate นั้น โดยผมได้ Mock View ไว้ส่วนเอกดนัยได้ทำต่อในส่วนของ Controller

ซึ่งระหว่างแยกกันทำนี้ ก็ตกลงกันไว้ ว่าจะคุยผ่าน Factory ที่กำหนดรูปแบบ Function Get Set และ รูปแบบข้อมูลคร่าวๆ ที่จะส่งให้ไปใช้ต่อ

**เอกดนัย**

ทำให้ Caman ใช้รูปตั้งต้นมาเป็นรูปในการประมวลผลได้แล้ว โดยการสั่งเปลี่ยนรูปทุกครั้งที่ทำการ adjust image

แต่เนื่องจากตัวที่ปรับเป็น Slider จึงทำให้ฟังก์ชั่น onChange ถูกเรียกถี่เกินไป ประมวลผลไม่ทัน จึงต้องใส่ Debounce เพื่อหน่วงเวลาในการเรียกฟังก์ชั่น onChange ให้เรียกทุกๆ 500ms แทน

ทำให้สามารถเลือก Algorithm ที่ใช้ในการ Dither ได้ระหว่าง `Atkinson` กับ `Error diffusion` ซึ่งจะได้ผลลัพธ์ที่ต่างกันพอสมควร และยังทำให้เลือกสีที่ต้องการได้อย่างอิสระ จากที่เคยต้องเลือกจาก Preset อย่างเดียว

เมื่อทำหน้า Pixelate เสร็จ ก็ไปรับช่วงต่อการทำหน้า Output จากศุภณัฐ โดยเป็นหน้าที่ไว้ทำการสั่งสินค้า และดาวน์โหลดไฟล์​ Instruction ในการต่อรูป ซึ่งส่วน Instruction ต้องรอ API ในส่วนนั้นก่อนจึงยังไม่ได้ทำ และคิดว่าจะไปทำส่วน Transaction ก่อน แต่เนื่องจากเห็นว่าหน้าจัดการตะกร้าสินค้า(Cart)มีพี่ทำไว้แล้ว แม้จะไม่ใช่ของสำหรับ DIY แต่เป็นสำหรับสินค้าธรรมดา ก็คิดว่าน่าจะใช้หน้าดังกล่าวได้เลย จึงปรึกษากับพี่ว่าสามารถนำมาใช้ได้เลยมั้ย โดยใช้วิธีเพิ่มตัว Brick ที่เกิดจากการ DIY ของผู้ใช้ ไปเป็นหนึ่งในสินค้าใน Cart ซึ่งก็จะมีข้อดีที่ว่า สามารถสั่งซื้อทั้งสินค้า DIY และสินค้าธรรมดาได้พร้อมๆกันเลย ซึ่งพี็่เห็นด้วย จึงจะใช้วิธีแปลงจากภาพ DIY ไปเป็นสินค้าแล้วไปเรียกหน้า Cart แทน

## Day 13 - *17/06/2016*

**ศุกณัฐ**

ทำเกี่ยวกับ Retouch Image, Pixel Paint Tool โดย fork มาแก้ Directive [https://github.com/zugarzeeker/angular-pixelpaint](https://github.com/zugarzeeker/angular-pixelpaint)

ทำให้สามารถ Move ได้ Select Tool (Paint, Text, Move) การ Zoom In, Zoom Out
Deactive Layer อื่นๆ เมื่อเข้าสู่ Mode Move และ Set Style (width & height)

ปัญหาที่เจอคือตอนแรกขยับแล้วเด้งกลับจุดเดิม เนื่องจากไม่ได้เก็บค่า Offset ไว้
อีกปัญหาคือขยับทั้งกล่อง แต่ จริงๆ ตั้งใจให้ขยับได้แค่ในกล่อง เพราะว่า เลือก element ผิดตัว

<img src="http://i.giphy.com/3o72EVmXObQFuEP768.gif" width="540" height="auto" />

[https://youtu.be/I4z1_VwUmcI](https://youtu.be/I4z1_VwUmcI)

**เอกดนัย**

วันนี้ได้ทำส่วนการส่งข้อมูลสินค้าทำได้มาจากการส่งข้อมูลของรูปไป Estimate ที่ Server ซึ่งจะได้ข้อมูลของ Product ทั้งหมดที่ต้องใช้คืนมา แล้วก็นำมาคำนวณราคารวม ซึ่งโค้ดหลายจุดก็ Reuse ของพี่ที่เคยเขียนประมาณนี้ไว้แล้ว ทำให้สามารถทำงานได้เร็ว และทำการส่งรูปไปยังฟังก์ชั่นการ Generate instruction ที่จะได้ไฟล์ PDF ออกมา ซึ่งพี่ได้เขียนโครงสร้างของฟังก์ชั่นดังกล่าวเตรียมไว้แล้ว

จากนั้นแก้ให้ขึ้น Modal แสดงวีดีโอวิธีใช้งาน DIY ที่มี Link youtube อยู่แล้ว ที่จะมีปุ่ม Help ขึ้นอยู่ในทุกๆหน้า

เมื่องานส่วนของตัวเองหลักๆเสร็จหมด ก็ไล่เก็บรายละเอียดงาน จัดการ Layout ต่างๆที่ยังผิดอยู่ให้เสร็จ

ที่เหลือคือรอ API ที่ยังขาดไป เพื่อปิดงานให้เสร็จ และพี่บอกว่าสัปดาห์หน้าจะเริ่มการ Debugging งานนี้ ที่พี่ๆจะลิสต์หา Bug ที่เจอไว้ให้

## Day 14 - *20/06/2016*

**ศุกณัฐ**

แก้ไขตาม issue ทั้งงาน Admin, Frontend ของส่วนที่เหลือ ได้ลองใช้ ui-select [https://github.com/angular-ui/ui-select](https://github.com/angular-ui/ui-select) ของ AngularJS ใช้ค่อนข้างง่ายดี และ ได้แก้ไขส่วน Retouch Image ให้สามารถปรับ font-family font-size font-color ได้

ปัญหาตรงส่วน Directive ซึ่งข้อความมีส่วนที่โดนตัดหายไป เมื่อเลยขอบแล้ว ในตอนที่ Render บน Canvas ซึ่งกำลังแก้ไขอยู่

**เอกดนัย**

แก้ไข Issues เรื่องขนาด Font, Style ต่างๆ และแก้ตัว Image size preset ให้รูปขึ้นอย่างถูกต้อง

เพิ่ม Shipping estimation สำหรับตะกร้าสินค้า ที่จะสามารถประเมินค่าขนส่งทั้งในและต่างประเทศได้ โดยดึงข้อมูลมาจาก API

เมื่อแก้ Issues จนหมดแล้ว พี่จึงบอกให้เริ่มงานเกี่ยวกับ Social Monitoring (หลังจากนี้ขอเรียกว่า **SMM**) ได้เลย โดยมอบหมายให้ไปศึกษาการทำ TDD ซึ่งก็ได้ใช้เวลาที่เหลือในวันนั้นอ่านศึกษาวิธีต่างๆของผู้พัฒนาอื่นๆ ซึ่งแหล่งที่เห็นว่าอ่านเข้าใจง่ายที่สุดคือ [React Redux TDD Tutorial - Theodo](http://www.theodo.fr/blog/2016/03/getting-started-with-react-redux-and-immutable-a-test-driven-tutorial-part-1/)


## Day 15 - *21/06/2016*

#### แหล่งศึกษา
[http://stackoverflow.com/questions/300855/javascript-unit-test-tools-for-tdd](http://stackoverflow.com/questions/300855/javascript-unit-test-tools-for-tdd)

**ศุกณัฐ**

ศึกษาเกี่ยวกับ ReactJS Redux และ TDD เพื่อเตรียมตัวสำหรับงานใหม่ จึงต้องศึกษาเครื่องมือเพิ่ม ซึ่งจะใช้ MERN Stack และมีการใช้งานร่วมกับ Circle CI

จึงมีข้อสงสัยว่า ถ้าหากเราจะ Test ผลที่ต้องรอจาก Backend API ต่างๆ จะต้องทำยังไง ซึ่งได้ไปเจอในกรณีที่ใกล้เคียงกัน ของ “จะทดสอบ Facebook API กันอย่างไรดี ?” จาก [http://www.somkiat.cc/how-to-test-facebook-api](http://www.somkiat.cc/how-to-test-facebook-api)
จริงๆแล้วหากรู้รูปแบบของ Request Response ก็สามารถ Mock เพื่อทดสอบได้ง่ายขึ้น

**เอกดนัย**

วันนี้เน้นศึกษาเกี่ยวกับ TDD ทั้งวัน ซึ่งจากลิ้งก์ข้างต้นที่ศึกษา ก็เริ่มอ่าน Part 2 ต่อ
โดยแต่ละ Part พูดถึงเรื่องต่างกันดังนี้
* Part 1: การ Test React
* Part 2: การ Test Redux (Reducer, State)

และยังศึกษาวีดีโอสอนเขียน Javascript จากเว็บ [Egghead](https://egghead.io/courses/learn-es6-ecmascript-2015) อีกด้วย (ซึ่งเว็บนี้ยังมีวีดีโอสอนสิ่งอื่นๆอีกมากมาย)


## Day 16 - *22/06/2016*

ได้รวบรวมแหล่งศึกษาไว้ในลิงค์ [TDD ReactJS Redux Javascript](https://docs.google.com/document/d/1Ut-9xIpUiGgpsu6GKUFnB6QZNiZbSL9pC-YpXR-NP9k/edit)

เริ่มต้นศึกษาเกี่ยวกับ การ Test ต่างๆ และ เครื่องมือที่ใช้สำหรับ Javascript ในการทำ TDD
โดยปรึกษากับพี่ที่บริษัทและได้ข้อสรุปว่า จะใช้ [Mocha](https://mochajs.org) และ [Chai](http://chaijs.com)
เหมือน Backend Node.js ที่พี่ๆใช้กัน เพื่อให้การใช้งานไปในทางเดียวกัน และ ปรึกษากันได้ง่าย

พี่ได้ Brief เกี่ยวกับงานใหม่ โดยให้ดูการออกแบบของไฟล์ Sketch และ Docs API ต่างๆ
รวมถึง Tech ที่ต้องใช้ในการทำงานนี้

ตอนค่ำๆพี่ได้แนะนำเรื่องวิธีการแก้ปัญหาของการเขียน Single page application คือการที่ Crawler ของเว็บต่างๆ (Google, Facebook, Slack, etc.) จะพยายามดึงข้อมูลจากเว็บเราไป แต่ข้อมูลที่ได้ไปอาจจะผิดจากที่ต้องการ เช่นการใช้ AngularJS สมมติใช้ `<meta property="og:title" content="{{myApp.seo.title}}" />` สิ่งที่ Crawler ได้ไปจะไม่ใช่ค่าของตัว `myApp.seo.title` ที่เป็นชื่อเว็บ แต่เป็น String `{{myApp.seo.title}}` ที่ยังไม่ทันได้ Render

ซึ่งปัญหาเกิดจากการที่ Crawler ส่วนมาก จะดึงไปแค่ HTML แต่ไม่ดึง JS ที่เป็นตัวประมวลผลไปด้วย ทำให้ได้ String ที่เป็นโค้ดไป ไม่ใช่ข้อความที่ต้องการ

วิธีแก้วิธีแรก ที่ง่ายที่สุดที่พี่แนะนำคือใช้ [Prerender.io](https://prerender.io/) ในการจัดการ Prerender หน้าเว็บก่อนส่งให้ Crawler (~~แต่เสียเงิน~~ (ถ้าใช้เยอะ))

พี่จึงแนะนำอีกวิธี คือการใช้ [Angular-SEO](https://github.com/steeve/angular-seo) ที่จะเป็นการดักของ Angular ว่าหากเป็น Crawler ที่เรียกใช้ จะทำการนำหน้าเว็บส่งไปยัง [PhantomJS](http://phantomjs.org/) ที่เป็น Browser แบบไม่มี UI ให้ทำการ Render หน้าเว็บก่อน แล้วจึงนำหน้าเว็บที่ Render เสร็จส่งไปให้ Crawler

แต่ปกติแล้ว หน้าเว็บใช้เวลาในการเรนเดอร์ ทำให้ตัว seo ไม่รู้ว่าจะต้องนำหน้าเว็บตอนไหนตอบไปยัง Crawler จึงมีฟังก์ชั่น `$scope.htmlReady();` ให้เรียกใช้เป็นการบอกว่า หน้าเว็บพร้อมแล้ว ให้คืนไปยัง Crawler ได้


## Day 17 - *23/06/2016*

#### แหล่งศึกษา
* [Exploring ES2016 Decorators](https://medium.com/google-developers/exploring-es7-decorators-76ecb65fb841#.720b4r5x4)
* [The Ducks File Structure for Redux](https://medium.com/@scbarrus/the-ducks-file-structure-for-redux-d63c41b7035c#.9b6z4o7je)
* [Ducks: Redux Reducer Bundles](https://github.com/erikras/ducks-modular-redux)
* [React Redux Universal Hot Example](https://github.com/erikras/react-redux-universal-hot-example)
* [Getting start with redux-form](http://redux-form.com/5.2.5/#/getting-started?_k=kbzqb2)
* [Doc รวมความรู้ React Redux](https://docs.google.com/document/d/1kdMQi_K8xtn_P4dMQGw03YPosCU2halVqvnoGlNlSZA/edit)

วันนี้เริ่มศึกษาเกี่ยวกับ Decorators `@myDecorators` ซึ่งเป็นการขยายความสามารถของ Class ให้มีฟังก์ชั่น/Property ต่างๆเพิ่มขึ้นได้ และยังสามารถนำ Decorators นั้นไปใช้กับตัวอื่นๆได้ด้วย ถือเป็นการจัดการ Code ให้มี Reusability สูงขึ้นที่ดีอย่างหนึ่ง

ตอนบ่ายได้ออกไปข้างนอกกับพี่ซัน ไปประชุมกับลูกค้าที่สนใจ IoT (Internet of Things) ทำให้ได้เห็นวิธีการพรีเซนต์ วิธีการคุยงานในระดับหนึ่ง

เมื่อกลับมาก็ศึกษาเกี่ยวกับ Redux ต่อ และ โครงสร้างของโปรเจ็กต์ ว่า Flow การทำงานเป็นอย่างไร ต้องเขียนโค้ดตรงไหน เรียกใช้อย่างไร

และได้เซ็ตตัว Editor ให้ทำการ Lint (การตรวจ Format โค้ดให้ถูกต้องตามมาตรฐาน) โดยใช้ ESLint และทดลองเขียน Test เพื่อลองทำ TDD โดยใช้ Mocha และ Chai ตามที่วางแผนไว้ และใช้ [WallabyJS](https://wallabyjs.com/) เป็นตัว Continuous testing คอย Test ตลอดเวลาที่โค้ด (โดยใช้ Mocha ในการ test) โดย Wallaby จะบอก Code coverage ว่าโค้ดส่วนไหนถูกTest ส่วนไหนไม่ถูกTestบ้าง และส่วนไหนทำให้เทสไม่ผ่าน

ซึ่งจากการลองใช้ นับว่าเป็น Plugin ที่มีประโยชน์มากๆ เพราะทำให้เห็นคุณภาพของการทำ Test ของตัวเองได้ทันที ว่า Test โค้ดครบทุกส่วนหรือไม่ และยังทำให้เห็นผลการเทสต์ได้ทันทีด้วย ว่าผ่านหรือไม่ผ่าน (แต่ถ้าไม่ผ่านก็จะเห็นเป็นแค่จุดสีแดงตรงบรรทัดนั้นเฉยๆ)

โดยจุดขายของ Plugin นี้คือ **เร็ว** เพราะมีวิธีการเทสเฉพาะส่วนที่ถูกแก้อยู่ ไม่ได้ไล่เทสใหม่ทั้งโปรเจ็กต์

ซึ่งขณะนี้ได้ใช้แบบ Trial อยู่ (สามารถใช้ได้ 30 วัน) โดยหากใช้แล้วรู้สึกว่าคุ้มค่า มีประโยชน์สมกับราคาที่ต้องจ่าย อาจจะซื้อ License ใช้เลยก็เป็นได้


## Day 18 - *24/06/2016*

เขียน TDD ของ Redux ในส่วน Reducer ของ Action ต่างๆ และ ได้ศึกษาเกี่ยวกับ [React Router](https://github.com/reactjs/react-router)
ได้แก่ การ Route, Link ร่วมกับ Component ต่างๆ

พี่พรูฟได้ช่วยอธิบาย โครงของ redux structure และการทำงานต่างๆ ของ project เพื่อให้เข้าใจมากขึ้น

มีเรื่องที่น่าสนใจคือ ในการทำ Endpoint Document API ต่างๆ ปกติ ถ้าทำใน google sheet
ในการทำ Doc ต่างๆ แล้วพี่ซันได้กล่าวถึง [Swagger](http://swagger.io/specification)
ซึ่งสามารถที่จะเขียน Spec ต่างๆ ของ API ได้

เมื่อลองหาๆดู ที่เกี่ยวข้องกับ Node.js จริงๆ แล้วมี [Swagger JSDoc](https://www.npmjs.com/package/swagger-jsdoc)
ซึ่งช่วยได้มากในการทำ Doc

นอกจากนี้ยังมีวิธีในการแยกไฟล์ย่อยๆ เพื่อความง่าย [Split Swagger](http://azimi.me/2015/07/16/split-swagger-into-smaller-files.html)
ลักษณะเป็นโครงสร้างหลายๆชั้น แบ่ง Directory และหลายๆไฟล์

เมื่อลองศึกษาดูพบว่า จริงๆ แล้ว [Swagger Server](https://github.com/BigstickCarpet/swagger-server) สามารถช่วยในการ Mock API Server ได้
และ Postman สามารถ [Import Swagger files](https://www.getpostman.com/docs/importing_swagger) ได้

วิธีในการ Mock API มีอีกวิธีคือการใช้ [JSON Server](https://github.com/typicode/json-server) ศึกษาได้จาก
["มาจำลอง REST API ไว้ใช้งานกันเถอะ"](https://www.babelcoder.com/blog/posts/mock-your-rest-api-with-json-server)


## Day 19 - *27/06/2016*

**ศุภณัฐ**

แก้ไข Route path ของ ReactRouter ของหน้า Create Project ใน Step ต่างๆ
Mockup UI ใน บาง Step และ ส่วนของ Project Settings


ลองใช้ `IndexRedirect` ของ ReactRouter เมื่อ Set เพื่อให้
เข้าถึงได้โดยแสดงแต่ละ step `/xyz/somepath1`

```javascript
<IndexRedirect to="somepath1" />
<Route path="somepath1" component={SomeComponent} />
<Route path="somepath2" component={SomeComponent2} />
```

การใช้ ReactRouter ทำให้จัดการกับ path ได้อย่างเป็นระเบียบ
มีการแบ่งเป็น หลายระดับ และส่ง parameter ได้ง่าย


ได้ลองใช้งาน SCSS โดย import ไปใช้ใน Component ของ ReactJS
```javascript
import classes from './SomeStyle.scss'
```

**เอกดนัย**

ทำ Route หน้า Feed messages ขึ้นมา

ศึกษาเรื่องการทำ State, Store ของ Redux
* [Store as global variable](https://github.com/reactjs/redux/issues/776)
* [Redux state tree design](http://codeloveandboards.com/blog/2015/10/16/react-state-management-fun-with-redux/)

Mockup data เพิ่มเติมบน JSON server สำหรับการทดลองใช้กับ API


## Day 20 - *28/06/2016*

**ศุภณัฐ**

Mock UI ของส่วน ProjectPermissions (ไว้สำหรับจัดการเกี่ยวกับ User และ บทบาทต่างๆ)
และ ProjectCreate ในส่วนของ ในการกำหนดค่า Filter ต่างๆ

ได้ลองใช้ TagsInput ของ React จาก [https://github.com/olahol/react-tagsinput](https://github.com/olahol/react-tagsinput)
นำ TagsInput ไปใช้แยกเป็น `component` เพื่อนำมา Reuse ได้

และ แก้ไข webpack ในส่วนของ Style Loader เพื่อให้ตอนที่ import ไฟล์ css ใน Javascript ทำงานได้ปกติกับ TagsInput
```javascript
import 'xyz/somestyles.css';
```

เมื่อ import ไฟล์ css มาแล้วเกิดปัญหา เนื่องจาก เมื่อ run แล้วถูกเข้าใจว่า เป็น `*.js` โดยจะขึ้นมาว่า

`[require-hook] Trying   to load "somestyles.css" as a "*.js"` ได้ช่วยกันหากับเอกดนัยจนเจอวิธีแก้ไข


โดยวิธีแก้คือให้เพิ่ม `css` เข้าไปในส่วนของ extensions ในไฟล์ของ `webpack-isomorphic-tools.js`
```javascript
style_modules: {
  extensions: ['less','scss', 'css'],
  ...
}
```

และเพิ่ม loader ของ `css` เข้าไปในไฟล์ config ของ `dev.config.js` และ `prod.config.js`
```javascript
module: {
  loaders: [
    { test: /\.css$/, loader: "style!css" },
    ...
  ],
  ...
}
```
โดย config ตามโครงสร้างของ [React Redux Universal Hot Example](https://github.com/erikras/react-redux-universal-hot-example)

**เอกดนัย**

สร้าง Components สำหรับจัดการ Breadcrumb เพราะว่าต้องใช้ร่วมกันหลายแห่ง ทำให้การดึง Component มาใช้จะทำได้ง่ายกว่า

Mockup UI สำหรับหน้า Messages, Message card, Breadcrumb


## Day 21 - *29/06/2016*

* [React Bootstrap](https://react-bootstrap.github.io/): เป็นการนำ Components ต่างๆของ Bootstrap มาเขียนให้เป็น React component เพื่อความสะดวกในการใช้งาน


**ศุภณัฐ**

Mock UI ของหน้า ProjectMeta ได้ใช้งานร่วมกับ Modal ของ `React Bootstrap` โดยแยกออกมาเป็น Component
เพื่อให้สามารถใช้งานได้แตกต่างกัน ยืดหยุ่นมากขึ้น เพื่อให้ reuse ได้ง่าย

**เอกดนัย**

Mockup UI สำหรับหน้า Filter ซึ่งใช้ Expand/Collapse และ Dropdown ร่วมด้วย

## Day 22 - *30/06/2016*

แหล่งศึกษา
* [react-bootstrap-modal-plus](https://github.com/zugarzeeker/react-bootstrap-modal-plus)
* [multiple-entry-points](https://webpack.github.io/docs/multiple-entry-points.html)
* [Webpack - Error: a dependency to an entry point is not allowed](https://github.com/webpack/webpack/issues/300)
* [Angular Pixel Paint](https://github.com/zugarzeeker/angular-pixelpaint)

พี่ได้ Brief เกี่ยวกับ Flow การทำงานของการติดต่อกับ API ซึ่งจะผ่าน API Gateway ที่เป็นตัว Route ไปยัง Microservice ต่างๆ และยังพูดถึงการทำ Authentcation และการ Publish/Subscribe ข้อมูลที่จะ Stream ตลอดเวลาด้วย ซึ่งงานนี้จะใช้ Google AppEngine, DataStore และ BigQuery

ศึกษาวิธีการ Build component `react-bootstrap-modal-plus` ที่สร้างขึ้นเอง เนื่องจากพอลงด้วยวิธี `npm install react-bootstrap-modal-plus` แล้วไม่สามารถใช้งานได้

เก็บ Issues ของ Microbrik ที่ยังเหลืออยู่ เช่นหน้า Retouch ที่มีปัญหาเกี่ยวกับการ Zoom, การ Move และหน้า Output ที่มีปัญหาเกี่ยวกับการ Download

* ปัญหาเกี่ยวกับการ Zoom คือ เวลา Zoom แล้ว Offset(ตำแหน่งภาพ) จะไม่ปรับตาม ทำให้ตำแหน่งภาพเลื่อนไปจากที่ควรจะเป็น ก็ต้องทำให้คำนวณ​ Offset ใหม่ให้ถูกต้องทุกครั้งที่ทำการ Zoom
* ปัญหาการ Move ใช้วิธีลิมิต offset ของการ Move ไม่ให้เกินขอบ
* ปัญหาการ Download เกิดจากไปดึงข้อมูลผิดที่ ทำให้ได้ข้อมูลเปล่ามา Generate รูป ส่งผลให้รูปพัง ก็แก้โดยการเขียนให้ไปดึงรูปให้ถูกที่


## Day 23 - *01/07/2016*

ศึกษา TDD
* https://semaphoreci.com/community/tutorials/getting-started-with-node-js-and-mocha
* https://github.com/nelsonic/practical-js-tdd

ทดลองใช้ Supertest
* https://github.com/visionmedia/supertest
* https://github.com/WhoopInc/supertest-as-promised
* https://www.codementor.io/nodejs/tutorial/testing-express-apis-with-supertest

โดยที่ Supertest ต่อยอดมาจาก Superagent อีกที
* https://github.com/visionmedia/superagent

แหล่งศึกษาอื่นๆ
* http://www.designsuperbuild.com/blog/unit_testing_controllers_in_express/
* https://glebbahmutov.com/blog/how-to-correctly-unit-test-express-server/
* http://blog.martroutine.com/2013/09/mock-%E0%B8%81%E0%B8%B1%E0%B8%9A-stub-%E0%B9%81%E0%B8%95%E0%B8%81%E0%B8%95%E0%B9%88%E0%B8%B2%E0%B8%87%E0%B8%81%E0%B8%B1%E0%B8%99%E0%B8%A2%E0%B8%B1%E0%B8%87%E0%B9%84%E0%B8%87/
* http://www.somkiat.cc/test-double-mock-stub-and-dummy/
* https://semaphoreci.com/community/tutorials/best-practices-for-spies-stubs-and-mocks-in-sinon-js
* http://blog.testdouble.com/posts/2016-03-13-testdouble-vs-sinon.html
* https://www.youtube.com/watch?v=E9Fmewoe5L4
* https://www.robotlovesyou.com/bdd-tdd/

ซึ่งพยายามลองใช้ Sinon เป็น Fake server สำหรับการ Test แล้ว แต่เห็นว่ามีความซับซ้อน และ Doc ของ Sinon ก็อ่านเข้าใจยาก รวมถึงได้ปรึกษารุ่นพี่ที่รู้จัก และเห็นว่าการเทสต์แบบนั้นจะเปลือง Effort เหมือนกับต้องขียนโปรแกรมสองครั้ง

###### Let's encrypt

การที่เว็บเราจะใช้ `https://` ได้ ต้องมี Certificate รับรองว่าเว็บเราปลอดภัยก่อน ซึ่ง Certificate จะได้จากองค์กรที่รับออกใบ Cert. แต่การจะได้ใบ Cert. ก็มักจะต้องเสียเงินค่า Cert. ให้ทางนั้นมาตรวจสอบเว็บและออกใบให้

แต่พี่ๆได้แนะนำเว็บ letsencrypt ซึ่งจะทำการออกใบ Cert. ให้ฟรี แต่จะ Renew ใหม่ทุกๆสามเดือน ซึ่งเราต้องไป Generate certificate เองอีกครั้ง แล้วเว็บเราก็จะสามารถใช้ `https://` ได้

* https://letsencrypt.org/
* https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-14-04
* https://certbot.eff.org/docs/using.html


## Day 24 - *04/07/2016*

แหล่งศึกษา
* https://www.babelcoder.com/blog/posts/avoid-callback-hell-using-promise-async-await
* https://github.com/acdlite/redux-actions
* https://github.com/yelouafi/redux-saga
* http://engineering.pivotal.io/post/tdding-react-and-redux/
* http://teropa.info/blog/2015/09/10/full-stack-redux-tutorial.html
* https://www.codementor.io/reactjs/tutorial/redux-unit-test-mocha-mocking
​* https://github.com/reactjs/redux/issues/1367
​* http://programmers.stackexchange.com/questions/278778/why-are-native-es6-promises-slower-and-more-memory-intensive-than-bluebird

[Clean Javascript using use-case interactors](https://medium.com/@dtinth/clean-javascript-using-use-case-interactors-f3a50c138154#.azz8l6nap)

ควรแยก Business logic ออกจาก Framework

เพราะการที่ตัวจัดการ Logic ต่างๆ ต้องผูกอยู่กับการเรียก Framework ต่างๆแบบ Specific (หรือการเรียก Service ต่างๆ ที่เขียนขึ้นเอง โดยเรียกแบบ Hard-code) จะทำให้มี Dependency สูงเกินไป เวลาจะเทสต์อะไรก็ยาก เพราะต้องทำ Stub กับทุก Service ที่ใช้ใน Logic นั้นๆ เพื่อให้รู้ได้ว่า หากเทสต์ไม่ผ่าน ส่วนไหนกันแน่ที่ทำให้ไม่ผ่าน (เช่น Logic อาจจะไม่ผิด แต่ไปผิดที่ Service ที่เรียกใช้แทน)

จึงควรทำการให้ฟังก์ชั่นที่ดูแล Logic ดูแลแค่ส่วน Logic ไม่ผูกกับอะไรอื่นๆอีก ซึ่งทำได้โดยการ ส่งผ่าน "Ports" หรือก็คือ Parameters นั่นเอง ว่าจะใช้อะไรบ้าง ซึ่งนับเป็นข้อดีของ Javascript ที่สามารถส่งอะไรก็ได้มา (Object, Function, Array, etc.) ทำให้การเรียกใช้ตัว Logic นี้จากที่ต่างๆสามารถทำได้สะดวก และตัว Logic นี้เองก็เทสต์ได้ง่ายด้วย โดยเพียงส่งค่าต่างๆไปจาก Test case ไม่ต้องไปกังวลถึง Framework ที่ต้องใช้
