# Numerito
ESP32 Arduino Project in 01204322 Embedded System. Kesetsart U.

* NODE MCU ESP32
* LCD
* LED RGB 
* OLED
* 7 SEGMENT 4 DIGITS
* BUTTON

<ins>USED LIBRARY</ins>
* LiquidCrystal_I2C
* SevSeg 
* Adafruit_BusIO 
* Adafruit_GFX_Library 
* Adafruit_SSD1306
* MFRC522 

* รายละเอียด 
โครงงานนี้เป็นผลงานที่ได้แรงบันดาลใจมาจากบอร์ดเกมหนึ่ง ซึ่งทางกลุ่มของเราได้นำมาประยุกต์เข้ากับความรู้ที่ได้เรียนไป โดยจะมีการเพิ่มอุปกรณ์ที่เป็นฮาร์ดแวร์เป็นอุปกรณ์ที่จับต้องได้สำหรับการทำกิจกรรมภายในเกม อุปกรณ์และกติกาของเกมจะเป็นดังนี้ เกมเรียงลำดับเลข แจกการ์ดหมายเลข 1 ถึง 6 และ 9 (7 ใบ) ให้ผู้เล่นแต่ละคน โดยจะเริ่มจากการโชว์หมายเลขจำนวน 4 หลัก [7 segment] ที่จอหลักตรงกลาง พร้อมกับจอ OLED แสดงสี โดยจะมี 2 สี คือ น้ำเงิน และแดง ผู้เล่นต้องนำการ์ดไปแตะที่เครื่องอ่าน RFID ที่อยู่บนบอร์ดของตนเอง โดยเรียงตามหมายเลขที่ปรากฎบนจอ ถ้าไฟเป็นสีน้ำเงินให้เรียงการ์ดหมายเลขจากหน้าไปหลัง แต่ถ้าไฟเป็นสีแดงให้เรียงการ์ดหมายเลขจากหลังไปหน้า เมื่อเรียงเสร็จให้กดปุ่มบนบอร์ด และผู้เล่นคนอื่นสามารถกดปุ่มเพื่อขอตรวจสอบลำดับการ์ดที่ลงไปได้ และจะแสดงผลลัพธ์ว่าถูกต้องหรือไม่ที่จอ OLED ตรงกลาง และมีไฟ LED บนบอร์ดผู้เล่นเพื่อนับคะแนน ผู้เล่นจะได้รับคะแนนจากกรณีต่อไปนี้ 1. เรียงการ์ดและกดปุ่มเป็นคนแรก โดยไม่มีคนขอตรวจสอบ 2. เรียงการ์ดและกดปุ่มเป็นคนแรก มีคนขอตรวจสอบ แต่ลำดับการ์ดถูก ส่วนกรณีที่ลำดับการ์ดผิดจะโดนหักคะแนน และผู้ที่ขอตรวจสอบจะเป็นฝ่ายได้คะแนนไป

* ฟีเจอร์ที่สำคัญ
	-มีบอร์ดกลางสำหรับการสุ่มเลขและไฟLED เพื่อเป็นฟังก์ชันสำหรับการเรียงเลข
	-จอ LCD บอกสถานะระหว่างดำเนินเกม
	-ESP-NOW สำหรับการเชื่อมต่อไร้สาย
	-กล่องควบคุมผู้เล่นทั้งหมด 3กล่อง มีRFIDสำหรับการอ่านการ์ดในแต่ละกล่อง
  
* แนวคิดและหลักการ
ทุกบอร์ดที่ใช้จะมี ESP32(NodeMCU) สำหรับการสื่อสารระหว่างบอร์ด โดยบอร์ดจะมี3ประเภท คือ บอร์ดกลางสำหรับการสุ่มเลข , บอร์ดกลางสำหรับแสดงสถานะผู้เล่น , บอร์ดผู้เล่น 3 บอร์ด
		
 - บอร์ดกลางสำหรับการสุ่มเลข
			- 7-Segment
			- LED แสดง mode เกมซึ่งมี 2 สีคือ สีฟ้า(หน้า-หลัง) สีแดง(หลัง-หน้า)
		
 - บอร์ดกลางสำหรับแสดงสถานะผู้เล่น
			- จอ LCD แสดงสถานะ(เฟสผู้เล่น)
			- หลอด LED ของแต่ละผู้เล่น(3หลอด)
		
 - บอร์ดผู้เล่น 3 บอร์ด (3 ผู้เล่น)
			- ตัวอ่าน RFID 
			- ปุ่มกด Accept
			- จอ OLED บอกคะแนนหรือสถานะ




