# Data Analysis of PM2.5 in Thailand(Y2019-Y2021)
## DADS5001 Mini-Project
## Name : Porrakit Jansoontornravee  /  Student ID : 6420422014

## Source of Data 
ข้อมูลคุณภาพอากาศจากจุดตรวจวัดคุณภาพอากาศอัตโนมัติพื้นที่ทั่วประเทศ ปี 2554 - 2564
- File : https://data.go.th/dataset/airpollution
- รายละเอียด : ข้อมูลฝุ่นละอองขนาดไม่เกิน 2.5 ไมครอน (PM2.5) รายวัน จำแนกรายจังหวัด
- หน่วยวัด : ความเข้มข้นของ PM2.5 ในบรรยากาศโดยทั่วไป (µg/m3)

## Research Question
1. ลักษณะของปริมาณ PM2.5 ในภาพรวมของปี 2019 - 2021 มีแนวโน้มเป็นอย่างไร 
2. ในปี 2021 บริเวณใดของประเทศไทยที่มีค่าเฉลี่ยปริมาณ PM2.5 สูงที่สุด 5 ลำดับแรก 
3. ในปี 2021 บริเวณใดของประเทศไทยที่มีปริมาณ PM2.5 อยู่ในระดับที่อันตรายต่อสุขภาพและมีระยะเวลานานที่สุด 10 ลำดับแรก 
4. ในปี 2021 บริเวณใดของประเทศไทยที่มีปริมาณ PM2.5 อยู่ในระดับที่ดีและมีระยะเวลานานที่สุด 10 ลำดับแรก 
5. ในปี 2021 ลักษณะของปริมาณ PM2.5 ในบริเวณภาพเหนือและภาคกลางมีความแตกต่างกันหรือไม่และมีลักษณะอย่างไร

## Data Journey 
1. Import library ที่ต้องใช้ในการวิเคราะห์ข้อมูล เช่น pandas,numpy และ matplotlib. Download dataset ที่ต้องการวิเคราะห์โดยประกอบด้วยข้อมูลปริมาณ PM2.5 ประจำปี 2019,2020 และ 2021 ที่ได้ download มาจาก website Opendata โดยข้อมูลทั้งหมดมีจำนวน 1098 rows และ 79 columns แบ่งเป็น 3 ชุดดังนี้
- ข้อมูลปริมาณ PM2.5 ประจำปี 2019 : 365 rows / 67 columns
- ข้อมูลปริมาณ PM2.5 ประจำปี 2020 : 366 rows / 69 columns
- ข้อมูลปริมาณ PM2.5 ประจำปี 2021 : 365 rows / 79 columns

2. ทำการวิเคราะห์ข้อมูลปริมาณ PM2.5 ในภาพรวมของ 3 ปีย้อนหลังเพื่อดูลักษณะแนวโน้มของค่าปริมาณ PM2.5  
   พบว่าค่าปริมาณ PM2.5 ในปี 2019,2020 และ 2021 มีแนวโน้มอยู่ในระดับที่ใกล้เคียงกัน โดยสังเกตจากกราฟ Box Plot และค่าเฉลี่ยปริมาณ PM2.5 ของทั้ง 3 ปี เมื่อเปรียบเทียบกับประเทศอื่นๆในภูมิภาคเอเซีย        ประเทศไทยมีค่าเฉลี่ยปริมาณ PM2.5 อยู่ในระดับที่ดีกว่าประเทศจีนและมองโกเลียแต่ยังเป็นรองประเทศเกาหลีใต้,มาเก๊าและญี่ปุ่น เป็นต้น

![image](https://user-images.githubusercontent.com/91737677/195993535-d77fd87f-cc77-4cca-838e-3119330d8805.png)  


![image](https://user-images.githubusercontent.com/91737677/195993507-6fcef7b1-0fde-4957-942e-3f12b31682e6.png)

   โดยสัดส่วนของระดับ PM2.5 ของแต่ละปี(คำนวณจากค่าเฉลี่ยของแต่ละสถานีและแยกตามเกณฑ์ของ US AQI Level) มีแนวโน้มดังกราฟแท่งต่อไปนี้ จากกราฟแท่งพบว่าสัดส่วนของบริเวณที่มีระดับ PM2.5 ในเกณฑ์ Unhealthy for Sensitive Groups มีจำนวนลดลงจากปี 2019 และคงที่ในปี    2020 และ 2021 สำหรับบริเวณที่อยู่ในเกณฑ์ Moderate มีจำนวนเพิ่มขึ้นจากปี 2019 จนถึงปี 2021 ส่วนบริเวณที่มีระดับ PM2.5 อยู่ในเกณฑ์ Good นั้นมีจำนวนคงที่ตลอดระยะเวลา 3 ปี
   
![image](https://user-images.githubusercontent.com/91737677/196212747-c51f646c-c32e-4fbc-9f34-5946b78bdfe2.png)

![image](https://user-images.githubusercontent.com/91737677/196212891-2c042b99-c742-47fb-9891-8d48fd60bf6b.png)




3. เนื่องจากข้อมูลในแต่ละปีมีลักษณะที่คล้ายกันจึงเลือกทำการวิเคราะห์ข้อมูลในรายละเอียดของปี 2021 เป็นตัวแทนของปีอื่นๆ 

4. ทำการหาเกณฑ์อ้างอิงของระดับปริมาณคุณภาพอากาศ(PM2.5)พบว่า US AQI Level เป็นเกณฑ์ที่มีการนำไปใช้อ้างอิงในหลายๆประเทศ จึงทำการใช้เกณฑ์นี้ในการอ้างอิงในการวิเคราะห์

![image](https://user-images.githubusercontent.com/91737677/195874286-2b1b80f9-a0b9-451d-b96e-e7fb85e7c821.png)

5. ทำการ merge ข้อมูลสถานีวัดปริมาณ PM2.5 จากข้อมูลอีก 1 sheet โดยมีจำนวนสถานีวัดปริมาณ PM2.5 ทั่วประเทศอยู่ทั้งหมด 78 จุด

![image](https://user-images.githubusercontent.com/91737677/195875137-7f4aa45f-cb2d-4e1b-927d-15f7a960b252.png)

6. จากข้อมูลของปี 2021 พบว่าในบางสถานีมีข้อมูลปริมาณ PM2.5 ที่ค่อนข้างน้อยจึงทำการตัดข้อมูลสถานีวัดที่มีจำนวนข้อมูลการวัดน้อยกว่า 1 เดือนออก พบว่ามี 2 สถานีที่มีข้อมูลน้อยกว่า 30 วัน

7. ทำการคำนวณหาค่าเฉลี่ยปริมาณ PM2.5 ของแต่ละสถานีและทำการจัดลำดับค่าเฉลี่ยปริมาณ PM2.5 จากมากไปน้อยพบว่าสามารถจัดลำดับข้อมูลได้ ดังรูปด้านล่าง โดยใน 5 ลำดับแรก พบว่า
มีจุดวัดที่อยู่ในพื้นที่ภาพเหนือ,ภาคตะวันออกเฉียงเหนือและภาคกลาง โดยได้แก่ พื้นที่ในจังหวัด เชียงราย,สมุทรปราการ,กทม.และขอนแก่น

![image](https://user-images.githubusercontent.com/91737677/195879745-135096f6-6267-4e0a-b718-9db41a21fd41.png)

![image](https://user-images.githubusercontent.com/91737677/195879458-ee73df3b-e698-4f98-abe2-8f014e6864fa.png)

8. หลังจากที่ได้ทำการวิเคราะห์ข้อมูลเพื่อดูว่าพื้นที่ใดที่มีค่าเฉลี่ยปริมาณ PM2.5 อยู่ในระดับที่สูงสุด 5 ลำดับแรก เพื่อป้องกันการวิเคราะห์ข้อมูลที่ผิดพลาดจากการใช้ค่าเฉลี่ย จึงทำการวิเคราะห์ข้อมูลในมิติอื่นๆ
   โดยทำการนับจำนวนวันใน 1 ปีที่มีระดับปริมาณ PM2.5 อยู่ในระดับ Unhealthy ตามเกณฑ์ของ US AQI Level ของแต่ละสถานี และคำนวณเป็น %Unhealthy โดยเทียบกับผลการวัดที่มีทั้งหมดของสถานีนั้นๆ 
   และจัดเรียงลำดับข้อมูลจากมากไปน้อยเพื่อดูว่าบริเวณใดของประเทศไทยที่มีปริมาณ PM2.5 อยู่ในระดับที่อันตรายต่อสุขภาพและมีระยะเวลานานที่สุด 10 ลำดับแรก ดังรูปด้านล่าง
   จากข้อมูลพบว่าพื้นที่ส่วนใหญ่ของประเทศไทยที่มีปริมาณ PM2.5 อยู่ในระดับที่อันตรายต่อสุขภาพและมีระยะเวลานานที่สุดอยู่ในพื้นที่ภาคเหนือซึ่งค่อนข้างสอดคล้องกับการจัดลำดับค่าเฉลี่ยของปริมาณ PM2.5

![image](https://user-images.githubusercontent.com/91737677/195994535-cf7fe143-de0e-4f00-b4bb-3160ed8a5603.png)

![image](https://user-images.githubusercontent.com/91737677/196106997-e52cda2c-a224-4926-9072-de78f5b70efc.png)

9. ในทางกลับกันจึงมีความสนใจว่าบริเวณใดของประเทศไทยที่มีปริมาณ PM2.5 อยู่ในระดับที่ดีและมีระยะเวลานานที่สุดจึงทำการวิเคราะห์ข้อมูลโดยคัดเลือกพื้นที่ที่มีผลวัดปริมาณ PM2.5 ในอากาศที่อยู่ใน
   ระดับ Good ตามเกณฑ์ของ US AQI Level และจัดลำดับจากจำนวนวันที่มากที่สุด 10 ลำดับแรก ดังรูปด้านล่าง

   พบว่าส่วนใหญ่ของบริเวณที่มีปริมาณ PM2.5 อยู่ในระดับที่ดีและมีระยะเวลานานที่สุด จะอยู่ในบริเวณชายแดนของประเทศที่อาจจะมีปริมาณการสัญจรของรถน้อยและไม่ค่อยมีการทำเกี่ยวกับอุตสาหกรรมหนัก เช่น 
   จ.ยะลา, จ.สระแก้ว และ จ.หนองคาย เป็นต้น

![image](https://user-images.githubusercontent.com/91737677/195994550-7b37f9ab-eb0f-4a3c-b859-397c3b580e1c.png)

![image](https://user-images.githubusercontent.com/91737677/196106871-fec8f197-57f2-484e-aa9b-b8d9de16855a.png)

10. จากข้อมูลในทั้ง 2 ด้านพบว่ามี 1 บริเวณ คือ ต.บ้านดง อ.แม่เมาะ จ.ลำปาง ที่เข้ามาอยู่ใน list ของทั้งบริเวณที่มี PM2.5 น้อยและมาก ทำให้เกิดความสงสัยว่าลักษณะของปริมาณ PM2.5 อาจจะมีความแตกต่างกัน
    ในแต่ละช่วงเวลาในปีนั้นๆ จึงทำการวิเคราะห์โดยเน้นไปที่กลุ่มจังหวัดในพื้นที่ภาคเหนือโดยได้นำจังหวัดในพื้นที่ภาคเหนือที่อยู่ใน list ของจังหวัดที่มีปริมาณ PM2.5 สูงในระดับ unhealthy และมีจำนวนหลายวันมา         plot กราฟปริมาณ PM2.5 รายวันในปี 2021 ได้ข้อมูลดังกราฟด้านล่าง 

    พบว่าจากการ plot กราฟเป็นรายวัน ปริมาณ PM2.5 ของพื้นที่ภาคเหนือจะมีค่าที่ค่อนข้างสูงโดดขึ้นมาในช่วงตั้งแต่กลางเดือน ก.พ - ปลายเดือน เม.ย สูงกว่าช่วงอื่นๆของปี ซึ่งอาจจะมีปัจจัยเร่งที่เข้ามาในช่วงเวลาดัง     กล่างทำให้มีค่าที่สูงขึ้นมา

![image](https://user-images.githubusercontent.com/91737677/196109372-f0dcfa84-a3fe-4a51-9a6d-f6e67594d467.png)

11. เนื่องจากค่าเฉลี่ยของบริเวณพื้นที่ในภาคกลางและภาคเหนืออยู่ในระดับที่ใกล้เคียงกันจึงต้องการเปรียบเทียบลักษณะของปริมาณ PM2.5 ในรายวันว่ามีลักษณะแตกต่างหรือเหมือนกันอย่างไรจึงทำการ plot กราฟวิเคราะห์       ข้อมูลรายวันของทั้ง 2 ภูมิภาค ได้ข้อมูลดังรูปด้านล่าง 

    พบว่าลักษณะของข้อมูลปริมาณของ PM2.5 ของ 2 พื้นที่จะแตกต่างกันในช่วงต้นของปีที่บริเวณภาคเหนือจะมีค่าปริมาณ PM2.5 ที่สูงแตกต่างจากเดือนอื่นๆค่อนข้างชัดเจนในขณะที่ปริมาณ PM2.5 ของพื้นที่ภาคกลางจะอยู่     ในระดับที่แตกต่างกันไม่มากและไม่มีสูงที่มีปริมาณ PM2.5 สูงโดดออกมา

![image](https://user-images.githubusercontent.com/91737677/196109437-c16ce894-676b-41b6-8f69-e5e92e65f2b9.png)



## Summary
1. ลักษณะของปริมาณ PM2.5 ในภาพรวมของปี 2019 - 2021 มีแนวโน้มเป็นอย่างไร 
> Ans: ข้อมูลค่าปริมาณคุณภาพอากาศ(PM2.5)ในปี 2019,2020 และ 2021 มีลักษณะที่คล้ายกันและมีปริมาณคุณภาพอากาศ(PM2.5)ที่สูงแตกต่างจากข้อมูลส่วนใหญ่อยู่มาก
2. ในปี 2021 บริเวณใดของประเทศไทยที่มีค่าเฉลี่ยปริมาณ PM2.5 สูงที่สุด 5 ลำดับแรก  
> Ans: พื้นที่ภาพเหนือ,ภาคตะวันออกเฉียงเหนือและภาคกลาง โดยได้แก่ พื้นที่ในจังหวัด เชียงราย,สมุทรปราการ,กทม.และขอนแก่น
3. ในปี 2021 บริเวณใดของประเทศไทยที่มีปริมาณ PM2.5 อยู่ในระดับที่อันตรายต่อสุขภาพและมีระยะเวลานานที่สุด 10 ลำดับแรก 
> Ans: พื้นที่ส่วนใหญ่ของประเทศไทยที่มีปริมาณ PM2.5 อยู่ในระดับที่อันตรายต่อสุขภาพและมีระยะเวลานานที่สุดอยู่ในพื้นที่ภาคเหนือซึ่งค่อนข้างสอดคล้องกับการจัดลำดับค่าเฉลี่ยของปริมาณ PM2.5
4. ในปี 2021 บริเวณใดของประเทศไทยที่มีปริมาณ PM2.5 อยู่ในระดับที่ดีและมีระยะเวลานานที่สุด 10 ลำดับแรก 
> Ans: ส่วนใหญ่ของบริเวณที่มีปริมาณคุณภาพอากาศ(PM2.5)อยู่ในระดับที่ดีและมีระยะเวลานานที่สุด จะอยู่ในบริเวณชายแดนของประเทศที่อาจจะมีปริมาณการสัญจรของรถน้อยและไม่ค่อยมีการทำเกี่ยวกับอุตสาหกรรมหนัก เช่น 
จ.สระแก้ว,จ.ยะลา
5. ในปี 2021 ลักษณะของปริมาณ PM2.5 ในพื้นที่บริเวณภาพเหนือและภาคกลางมีความแตกต่างกันหรือไม่และมีลักษณะอย่างไร
> Ans: ลักษณะของข้อมูลปริมาณของ PM2.5 ของ 2 พื้นที่จะแตกต่างกันในช่วงต้นของปีที่บริเวณภาคเหนือจะมีค่าปริมาณ PM2.5 ที่สูงแตกต่างจากเดือนอื่นๆค่อนข้างชัดเจนในขณะที่ปริมาณ PM2.5 ของพื้นที่ภาคกลางจะอยู่        ในระดับที่แตกต่างกันไม่มากและไม่มีสูงที่มีปริมาณ PM2.5 สูงโดดออกมา





