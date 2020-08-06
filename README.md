# detectmood
ตรวจจับอารมณ์ ผ่านทางใบหน้า


ชื่อโครงงาน	ภาษาไทย : ตรวจจับอารมรณ์ผ่านทางใบหน้า
	      English :  Facial Expression Recognition
	      
ชื่อนักศึกษา นาย ณัฐดนัย จำปาศรี 

สรุปสาระสำคัญที่เกี่ยวข้อง

1.	ความเป็นมาของปัญหา
เนื่องจากในสถานที่ทำงานในบริษัทบางแห่ง ไม่มีการดูแลหรือเอาใจใส่พนักงานเพียงพอและไม่รู้ว่าพนักงานแต่ละคนเครียดหรือเศร้าหรือไม่ซึ่งอาจส่งผลกระทบต่อหน้าที่การงานโดยในระบบตรวจจับอารมณ์นี้สามารถช่วยให้รู้อารมณ์และทำการเก็บข้อมูลของแต่ละบุคคลก่อนนำไปเก็บข้อมูลสถิติและดูแลคนเหล่านั้นได้
2.	วัตถุประสงค์ของโครงงาน
1)	เพื่อศึกษาการทำงานของอัลกอริทึม
2)	เพื่อศึกษาการเขียนโปรแกรมรับรู้อารมณ์ผ่านใบหน้า
3)	เพื่อแสดงอารมณ์ผ่านใบหน้าที่ตรวจจับ
3.	ขอบเขตของโครงงาน
1)	สามารถแสดงอารมณ์ได้ 7 รูปแบบประกอบด้วย
1.1	 Angry ( โกรธ )
1.2	 Disgust ( รังเกียจ )
1.3	 Fear ( กลัว )
1.4	 Happy ( มีความสุข )
1.5	 Sad ( เศร้า )
1.6	 Surprise ( ประหลาดใจ )
1.7	 Neutral ( เป็นกลาง )
2)	สามารถแสดงอารมณ์ในรูปแบบเรียลไทม์
3)	สามารถตรวจจับได้หลายใบหน้าพร้อมกัน

4.	แนวคิดการทำงาน
การแสดงอารมณ์ผ่านทางใบหน้ามี 3 ขั้นตอนหลักๆ คือ ตรวจจับใบหน้า , CNN , แสดงผลลัพท์
1.	ตรวจจับใบหน้า ( Face Detection )
ตรวจจับใบหน้าที่ต้องการนำไปวิเคราะห์ผ่านทางกล้องต่างๆ หรือจะตรวจจับผ่านทางรูปภาพและวีดีโอก็ได้โดยจะทำการตัดเฉพาะรูปภาพใบหน้าออกมาขนาด 48x48 ก่อนนำไปเข้า CNN
 
รูปที่ 1 ตรวจจับใบหน้า

2.	CNN ( convolutional neural networks )
ในขั้นตอนนี้จะทำการแยกองค์ประกอบของรูปภาพก่อนนำไปตรวจสอบภายใน hidden layer เพื่อดูค่าจาก Weight ว่าอารมณ์ประเภทไหนที่มีความน่าจะเป็นสูงที่สุด
 
รูปที่ 2 ตัวอย่างการทำงานของ CNN


https://lh5.googleusercontent.com/Jx7rkVYWs5zCTlYFBpJwis3oYc4VAfa3i29FyUE3mwaY0YbFThbAusmtzbx6Pqg6G2xgiqgX2X0kEg=w1920-h969-rw

3.	แสดงผลลัพท์ ( Output )
สามารถแสดงผ่านกล้องในรูปแบบ Realtime หรือแสดงโดยใช้รูปภาพก็ได้
 
รูปที่ 3 แสดงผ่านรูปภาพโดยแสดงความน่าจะเป็นของอารมณ์แต่ละประเภท

 
รูปที่ 4 แสดงผ่านกล้องในรูปแบบ Realtime 




5.	ขั้นตอนและโครงสร้างของระบบ
5.1 Flowchart แสดงการทำงานของระบบตรวจจับอารมณ์
 
รูปที่ 5 Flowchart แสดงการทำงานของระบบตรวจจับอารมณ์ผ่านทางใบหน้า
5.2 ส่วนประกอบภายใน Dataset
	โดยแต่ละรูปภาพมีขนาด 48x48 Pixel 
อารมณ์	จำนวนรูปภาพ
0.	Angry	4,593
1.	Disgust	547
2.	Fear	5,121
3.	Happy	8,989
4.	Sad	6,077
5.	Surprise	4,002
6.	Neutral	6,198
รวม	35,527

ตารางที่ 1 แสดงรูปจำนวนรูปภาพของแต่ละประเภทภายใน dataset
 
รูปที่ 6 แสดงข้อมูลใน dataset
โดยภายใน dataset นั้นประกอบไปด้วย emotion และ pixels โดย emotion นั้นเป็นผลลัพท์ของอารมณ์แต่ละประเภทในรูปแบบนี้จะแสดงเป็น 0 ถึง 6 ตามตารางและ pixels ซึ่งก็คือรูปภาพที่จะนำไป Train โดยแสดงในรูปแบบ Pixels ก่อนจะให้โปรแกรมแยกออกมาแสดงเป็นรูปภาพก่อนนำไป Train

6.	การทำงานของระบบ
Train รูปภาพภายใน Dataset โดยแบ่งออกเป็น 2 ส่วน
-	Train Image 28,709 รูป
-	Test Image 2,304 รูป
โดยจะทำการ Run โดยใช้ Anaconda
 
รูปที่ 7 แสดงการ Train รูปภาพภายใน dataset

หลังจากทำการ Train เสร็จลองนำรูปภาพไปเข้า modal จะแสดงความน่าจะเป็นของอารมณ์แต่ละประเภทในรูปแบบกราฟแท่ง

 
รูปที่ 8 แสดงผลลัพท์ของอารมณ์แต่ละประเภท

 
รูปที่ 8 แสดงไฟล์หลังจาก Train โดย haarcascade มีไว้สำหรับ face detection
เปลี่ยนรูปแบบจากรูปภาพเป็น Real-Time Data Streaming โดยแสดงอารมณ์ออกมาทั้งหมด 7 รูปแบบและความน่าจะเป็นของแต่ละรูปแบบ
 
รูปที่ 9 แสดงอารมณ์ประเภทต่างๆ ในรูปแบบ Real-Time Data Streaming 
		ประมวลผลโดยนำเฉพาะการแสดงออกทางอารมณ์ที่มีค่าสูงที่สุดออกมาแสดงเพื่อให้ดูง่ายขึ้น
    
รูปที่ 10 ตัวอย่างการแสดงอารมณ์ประเภทต่างๆ

7.	สรุปผล
ในการทำระบบตรวจจับอารมณ์นั้น ในขั้นตอนแรกจะหารูปภาพที่จะนำไป Train โดยในส่วนนี้จะใช้ รูปภาพภายใน Dataset fer2013 ซึ่งเคยมีคนทำไปแล้วเพื่อไม่ให้เสียเวลาโดยทำการสร้าง CNN โดยใช้ Keras และ Tensorflow Backend ก่อนจะนำไป Train รูปภาพหลังจากทำทั้งหมดเสร็จแล้วก็จะทำเป็น Real-Time Data Streaming เพื่อจับภาพตลอดเวลาโดยนำรูปภาพแต่ละ Frame เข้า CNN เพื่อประมวลผลและแสดงออกทางจอภาพ  


8.	เอกสารอ้างอิง
 Sefik Serengil, (2018). Facial Expression Recognition with Keras. สืบค้นเมื่อ 13 กุมภาพันธ์ 2562, จากเว็บไซต์: https://sefiks.com/2018/01/01/facial-expression-recognition-with-keras/?fbclid=IwAR1y-NYpIRT_EV7CMi-LjVyn7nnY3LFx4a3GnIZNFSCUCwHga8zOcpZmDr0

Sefik Serengil, (2018). Real Time Facial Expression Recognition on Streaming Data. สืบค้นเมื่อ 15 กุมภาพันธ์ 2562, จากเว็บไซต์: https://sefiks.com/2018/01/10/real-time-facial-expression-recognition-on-streaming-data/

Furkan Kınlı, (2018). Real Time Facial Expression Recognition on Streaming Data. สืบค้นเมื่อ 18 กุมภาพันธ์ 2562, จากเว็บไซต์: https://medium.com/deep-learning-turkey/deep-learning-lab-episode-3-fer2013-c38f2e052280
