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

ซึ่งพยายามลองใช้ Sinon ในการ stub, mock ของ request, response สำหรับการ Test แล้ว แต่เห็นว่ามีความซับซ้อน และ Doc ของ Sinon ก็อ่านเข้าใจยาก รวมถึงได้ปรึกษารุ่นพี่ที่รู้จัก และเห็นว่าการเทสต์แบบนั้นจะเปลือง Effort เหมือนกับต้องเขียนโปรแกรมสองครั้ง

###### Let's encrypt

การที่เว็บเราจะใช้ `https://` ได้ ต้องมี Certificate รับรองว่าเว็บเราปลอดภัยก่อน ซึ่ง Certificate จะได้จากองค์กรที่รับออกใบ Cert. แต่การจะได้ใบ Cert. ก็มักจะต้องเสียเงินค่า Cert. ให้ทางนั้นมาตรวจสอบเว็บและออกใบให้

แต่พี่ๆที่บริษัทได้แนะนำเว็บ letsencrypt ซึ่งจะทำการออกใบ Cert. ให้ฟรี แต่จะ Renew ใหม่ทุกๆสามเดือน ซึ่งเราต้องไป Generate certificate เองอีกครั้ง แล้วเว็บเราก็จะสามารถใช้ `https://` ได้

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
* https://github.com/reactjs/redux/issues/1367
* http://programmers.stackexchange.com/questions/278778/why-are-native-es6-promises-slower-and-more-memory-intensive-than-bluebird

[Clean Javascript using use-case interactors](https://medium.com/@dtinth/clean-javascript-using-use-case-interactors-f3a50c138154#.azz8l6nap)

ควรแยก Business logic ออกจาก Framework

เพราะการที่ตัวจัดการ Logic ต่างๆ ต้องผูกอยู่กับการเรียก Framework ต่างๆแบบ Specific (หรือการเรียก Service ต่างๆ ที่เขียนขึ้นเอง โดยเรียกแบบ Hard-code) จะทำให้มี Dependency สูงเกินไป เวลาจะเทสต์อะไรก็ยาก เพราะต้องทำ Stub กับทุก Service ที่ใช้ใน Logic นั้นๆ เพื่อให้รู้ได้ว่า หากเทสต์ไม่ผ่าน ส่วนไหนกันแน่ที่ทำให้ไม่ผ่าน (เช่น Logic อาจจะไม่ผิด แต่ไปผิดที่ Service ที่เรียกใช้แทน)

จึงควรทำการให้ฟังก์ชั่นที่ดูแล Logic ดูแลแค่ส่วน Logic ไม่ผูกกับอะไรอื่นๆอีก ซึ่งทำได้โดยการ ส่งผ่าน "Ports" หรือก็คือ Parameters นั่นเอง ว่าจะใช้อะไรบ้าง ซึ่งนับเป็นข้อดีของ Javascript ที่สามารถส่งอะไรก็ได้มา (Object, Function, Array, etc.) ทำให้การเรียกใช้ตัว Logic นี้จากที่ต่างๆสามารถทำได้สะดวก และตัว Logic นี้เองก็เทสต์ได้ง่ายด้วย โดยเพียงส่งค่าต่างๆไปจาก Test case ไม่ต้องไปกังวลถึง Framework ที่ต้องใช้


## Day 25 - *05/07/2016*

#### แหล่งศึกษา

Babel
* https://babeljs.io/docs/setup/#installation
* http://babeljs.io/docs/plugins/preset-stage-0
* https://babeljs.io/docs/plugins/transform-runtime/

Asynchronous ES7
* http://stackabuse.com/node-js-async-await-in-es7/
* http://blog.shaunxu.me/2016-06-14-es7-async-await-in-node-with-bebel/
* http://yannickloriot.com/2016/05/async-functions-in-es7/
* https://www.babelcoder.com/blog/posts/avoid-callback-hell-using-promise-async-await

CircleCI
* https://circleci.com/

GoogleCloudPlatform
* https://cloud.google.com/nodejs/getting-started/hello-world
* https://github.com/GoogleCloudPlatform/cloud-debug-nodejs
* https://github.com/GoogleCloudPlatform/nodejs-docker

Setup Project Backend API Node.js ที่ทำอยู่ ให้ใช้ async, await เพื่อให้เขียนได้ง่ายขึ้น
ซึ่งเป็นของ ES7 ได้ แต่ปัจจุบันตอนนี้ ยังต้องใช้งาน ES7 ผ่าน babel

จึงต้อง set `.babelrc` (stage-0 มีทั้ง stage-1, stage2, stage-3)

ไฟล์ `.babelrc` เกี่ยวกับการตั้งค่าเมื่อใช้งาน babel
```javascript
{
  "presets" : ["es2015", "stage-0"],
  "plugins": [
    ["transform-runtime", {
      "polyfill": false,
      "regenerator": true
    }]
  ]
}
```

เมื่อตัดสินใจเปลี่ยนไปใช้ ES7 จึงต้องแก้ไข `package.json`, `ESLint`, `Mocha` เพื่อให้ใช้งานร่วมกันได้

ตัวอย่างคำสั่ง วิธีการ run ผ่าน babel (ต้องติดตั้ง babel-cli ก่อน จึงจะใช้ babel-node ได้)
```bash
./node_modules/babel-node app.js
```

ไฟล์ `package.json` คำสั่งที่ใช้ในการ run และ dependencies ต่างๆ
```javascript
"scripts": {
  "eslint": "eslint **/*.js **.js",
  "test": "mocha ./tests/**/*.spec.js --compilers js:babel-register",
  "test-watch": "mocha --watch ./tests/**/*.spec.js --compilers js:babel-register",
  "start": "./node_modules/.bin/babel-node app.js",
  ...
},
"dependencies": {
  "babel-cli": "^6.10.1",
  "babel-core": "^6.10.4",
  "babel-eslint": "^6.1.0",
  "babel-loader": "^6.2.4",
  "babel-polyfill": "^6.9.1",
  "babel-preset-es2015": "^6.9.0",
  "babel-preset-stage-0": "^6.5.0",
  "babel-register": "^6.9.0",
  "babel-runtime": "^6.9.2",
  "babel-plugin-transform-runtime": "^6.9.0",
  ...
}
```

ต้องตรวจสอบกับ CircleCI ว่ายังคง run ได้เป็นปกติ ผ่านหรือไม่
ซึ่ง CircleCI พี่ที่บริษัทได้ Set ไว้ว่า ถ้าหาก test ผ่าน จะนำไป Deploy บน google cloud platform ต่อ

ก่อนกลับพี่ๆที่บริษัท ให้ลองประเมินเวลาที่จะควรจะใช้ในการทำงานของงานที่จะได้ทำถัดไป
โดยเปรียบเทียบกัน ของ effort manday ที่ควรจะใช้ ใน GoogleSheet ที่ช่วยๆกันประเมิน

## Day 26 - *06/07/2016*

ทดลอง Deploy แอพลงบน Google Cloud Platform Node.js ซึ่งตอนแรกคิดว่าอาจจะมีปัญหาที่การใช้ babel-node มาเป็นตัวรัน

> **Not meant for production use**
>
> You should not be using `babel-node` in production. It is unnecessarily heavy, with high memory usage due to the cache being stored in memory. You will also always experience a startup performance penalty as the entire app needs to be compiled on the fly.
>
> *Ref: [babeljs.io/cli](https://babeljs.io/docs/usage/cli/#babel-node)*


เลยพยายามหาวิธีที่ไม่ต้องใช้ Babel
* ลอง ssh ขึ้นไป Build บน CI แล้วค่อยส่งขึ้น Google Cloud
* ไม่ใช้ async/await ของ ES7 แต่ไปใช้ Library ที่ทำงานได้คล้ายกันแทนของ [yortus/asyncawait](
https://github.com/yortus/asyncawait)
* กลับไปเขียน Promise แบบ ES6 ซึ่งก็ได้ศึกษาการพัฒนาของการเขียน Callback จาก [ES 5-6-7: From Callbacks to Promises to Generators to Async/await](https://medium.com/@rdsubhas/es6-from-callbacks-to-promises-to-generators-87f1c0cd8f2e#.ocsiahf7z)
* ศึกษาว่าแต่ละ Stage ว่ามีรายละเอียดอย่างไรบ้างจาก [hemanth/es-next](https://github.com/hemanth/es-next)
* กำหนด Engine ที่ Google cloud ใช้ โดยระบุใน package.json เพราะนึกว่าเป็นปัญหาเรื่องเวอร์ชั่นของ Node, npm ที่ทำงานไม่ได้
```javascript
"engines": {
   "node": ">=6.0.0 <7.0.0"
 }
```

แต่เมื่อพยายามช่วยกันหาร่วมกับพี่ๆ ก็ไปพบว่า ปัญหาที่แท้จริงมาจาก Server npm ซึ่งนักพัฒนาทั่วโลกเจอกันเยอะมาก (เพิ่งเกิดขึ้นไม่กี่วัน) ตาม Issue ด้านล่าง

https://github.com/npm/npm/issues/13284

ซึ่งทำให้การ Deploy ลงที่ๆต้องการ npm ช่วย ไม่สามารถทำได้ ทั้ง Heroku, TravisCI, CircleCI, etc.

ในประเทศไทย จริงๆแล้วยังสามารถใช้ npm ได้อยู่ แต่ปัญหาที่เกิดกับงานที่ทำอยู่คือต้องการ Deploy ไปยัง Google Cloud ซึ่งอยู่ต่างประเทศ จึงไม่สามารถทำได้

เมื่อเห็นว่าไม่สามารถทำงานส่วนที่ต้องใช้ Google Cloud ต่อได้ จึงกลับไปทำ Mockup UI ที่ยังไม่เสร็จต่อ

_แหล่งศึกษาเพิ่มเติมเกี่ยวกับ Asynchronous บน Javascript_
* https://github.com/laverdet/node-fibers
* https://github.com/tj/co
* https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Statements/function*


## Day 27 - *07/07/2016*

https://medium.com/javascript-scene/5-common-misconceptions-about-tdd-unit-tests-863d5beb3ce9#.t2ikwgs42

https://medium.com/javascript-scene/what-every-unit-test-needs-f6cd34d9836d#.x1l0wyysf

http://stackoverflow.com/questions/8776567/unit-test-business-logic-layer

http://pm2.keymetrics.io/

https://github.com/Unitech/pm2/issues/1167

https://github.com/bootprint/bootprint-openapi

https://medium.com/wdstack/bootstrap-4-whats-new-visual-guide-c84dd81d8387#.tsyglmmsd

http://www.tutorialspoint.com/software_testing/software_testing_myths.htm

http://www.tutorialspoint.com/software_testing/software_testing_levels.htm

http://sqa.stackexchange.com/questions/1014/ui-and-business-logic-testing-am-i-doing-it-right-should-i-unit-test-anything


## Day 28 - *08/07/2016*

**ศุภณัฐ**

ได้ลองทำ route-proxy ให้ติดต่อกันระหว่าง server ผ่าน gateway server กับ user-services โดยยังลองใน localhost อยู่ และเขียน test ในส่วนของ Business Logic ของโค้ด Backend แยกการทำงานเป็นส่วนๆมาประกอบกัน ทำให้สามารถ Test ได้ง่ายขึ้น

พีกอล์ฟได้แนะนำ [https://github.com/jfrazelle/dotfiles](https://github.com/jfrazelle/dotfiles) เป็น Repo เกี่ยวกับ ไฟล์ config ต่างๆ
พี่ซันได้ fork bootprint-api (นำ Swagger มา gen doc ในรูปแบบ html) มาแก้ไขเพิ่มเติม ทำให้ดูได้ง่ายขึ้น
ดูได้ที่ [https://github.com/5un/bootprint-openapi](https://github.com/5un/bootprint-openapi)


## Day 29 - *11/07/2016*

#### แหล่งศึกษา
* [Write Unit Test 101 — Simple test](https://medium.com/@chrisza/write-unit-test-101-simple-test-8f4d76dead54#.dl3o1if1g)
* [Refactor เมื่อไหร่ดี?](https://medium.com/@chrisza/refactor-%E0%B9%80%E0%B8%A1%E0%B8%B7%E0%B9%88%E0%B8%AD%E0%B9%84%E0%B8%AB%E0%B8%A3%E0%B9%88%E0%B8%94%E0%B8%B5-9913f9e2b240#.xwwv6nbum)
* [TDD Misconception](https://medium.com/@chrisza/tdd-misconception-7c1ecf990758#.pm5yelcvn)

**ศุภณัฐ**

เขียน Business Logic และ Test ได้แก่ organization, roles, feeds, บางส่วนของ users ในส่วนของ Backend (Node.js)
โดยวันนี้ได้พบกับความง่ายอย่างนึงคือ Slack ที่ใช้อยู่พี่กอล์ฟได้ Integrate เข้ากับ CircleCI ทำให้ตอน push code ไม่ต้องตามดูว่าผ่านหรือไม่ ใน CircleCI
แต่ดูตอนแจ้งเตือนขึ้นมาใน channel ของ Slack แทน


## Day 30 - *12/07/2016*

https://googlecloudplatform.github.io/gcloud-node/#/docs/v0.36.0/datastore

Route & CircleCI Deploy Google App Engine 2 instance (= 2 services) Learn DS and Create Utility function


## Day 31 - *13/07/2016*

**ศุภณัฐ**

- Route, Google Datastore
- Set ReactJS & Redux CircleCI & Deploy on GoogleAppEngine

**เอกดนัย**

- gg frontend
- Fixed Style Loader ReactJS & Redux

## Day 32 - *14/07/2016*

**ศุภณัฐ**

- Backend gateway proxy Superagent (get put post delete)
- Backend เชื่อม Route กับ BL
- Build & Test CircleCI --> Deploy Frontend Redux --> Google App Engine
- Datastore Utility (Promise --> resolve and reject)

**เอกดนัย**

- gg frontend (Style)


## Day 33 - *15/07/2016*

**ศุภณัฐ**

http://visionmedia.github.io/superagent/

exception
https://www.babelcoder.com/blog/posts/avoid-callback-hell-using-promise-async-await

query datastore
https://cloud.google.com/datastore/docs/concepts/queries

- Refactor Datastore Utility
- Route users, BL login
- Route proxy & Postman
- test & BL handle exceptions


## Day 34 - *20/07/2016*



## Day 35 - *21/07/2016*



## Day 36 - *22/07/2016*



## Day 37 - *25/07/2016*



## Day 38 - *26/07/2016*



## Day 39 - *27/07/2016*



## Day 40 - *28/07/2016*



## Day 41 - *29/07/2016*
