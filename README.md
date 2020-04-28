# 6110613269
### Computer Architecture สถาปัตยกรรมคอมพิวเตอร์
##### สรุปเนื้อหา
  
MIPS Instruction format

ทุกคำสั่งของ MIPS จะถูกเข้ารหัสโดย binary และจะมีขนาด 32 bits

มีอยู่ 3 ประเภท

<br>![image](https://www.researchgate.net/profile/Flavio_Padua/publication/269463299/figure/fig1/AS:392119614230533@1470500009360/The-MIPS-instruction-format.png)

* R-Format ใช้ในการคำนวณทางตรรกศาสตร์
  * ALU  =>  alu $rd,$rs,$rt
  * jr   =>  jr  $rs

* I-Format ใช้ย้ายข้อมูลเปลี่ยนข้อมูล
  * ALUi    =>  alui $rt,$rs,value
  * Data Tranfers  =>  lw $rt,offset($rs) |
                       sw $rt,offset($rs)
  * Branch  =>  beq $rs,$rt,offset

* J-Format ย้ายไปทำงานที่อื่น
   * Jump    =>  j address
   * Jump&Link   =>  jal address
  
  
## การบ้านครั้งที่ 1
### คำสั่ง JUMP ในคอมพิวเตอร์ MIPS
เป็นคำสั่งประเภท J-Format

การทำงานคือ นำ address มาเขียนในรูปเลขฐาน 2

และนำเลขฐาน 2 ที่ได้มา ตัด2เลขหลักสุดท้าย ไปเติมที่หลักแรก

ตัวอย่าง      
            
            1100 0001 1111 1100 0000 1000 0100 11(00) >> นำออก

            เติมเข้า   >> (00)11 0000 0111 1111 0000 0010 0001 0011

และนำมาเขียนเป็นเลขฐาน 16 ในที่นี้จะได้เท่ากับ 27f0223

ซึ่ง opcode ของ jump = 000010

### คลิปการบ้านครั้งที่ 1
<br>[คลิปอธิบายคำสั่ง JUMP in MIPS](https://www.youtube.com/watch?v=t2JYzAhNM5A)

## การบ้านครั้งที่ 2
### การทำงานของ CPU

ยกตัวอย่างคำสั่งที่มนุษย์เข้าใจ 

    public static void main(String[] args){

        int a = 10;
    
        int b = 20;
    
        int c = a+b;
    
    }
เมื่อแปลเป็นภาษาคอมพิวเตอร์

    00000000:           08400000        //j  01000000
    00000004:           1A000000        //data
    ...
    01000000:           8C090004        //lw $9,$0(4)
    01000004:           8D210000       //lw $1,$9(0)
    01000008:           8D220004       //lw $2,$9(4)
    0100000C:           00221820        //add $3,$1,$2
    01000010:           AD230008        //sw $9,$0(4)
    ...
    1A000000:           0000000A        //a = 10
    1A000004:           00000014        //b = 20
    1A000008:           0000001E        //c = 30
    
### คลิปการบ้านครั้งที่ 2
<br>[คลิปอธิบายการทำงานของ CPU](https://www.youtube.com/watch?v=NIl0aoX2EJg&t=4s)

## การบ้านครั้งที่ 3
### เปรียบเทียบ Single Cycle และ Multi Cycle
single cycle

<br>![image](https://i.stack.imgur.com/vCvw1.png)
* คุณสมบัติของ single cycle
  * มี 3 ALU
  * มี 2 Memory
  * คำสั่งจบใน Cycle เดียว
  * เวลาแต่ละคำสั่งเท่ากัน(เป็นเวลาของคำสั่งที่นานที่สุด)
  
multi cycle
<br>[image](https://imagecloud.nos-eastchina1.126.net/Computer%20Engineering/Multi-cycle%20Datapath.PNG)
* คุณสมบัติของ multi cycle
  * มี 1 ALU
  * มี 1 Memory 
  * แต่ละคำสั่ง ไม่จบใน cycle เดียว
  * เวลาแต่ละคำสั่ง ไม่เท่ากัน
 
 ### คลิปการบ้านครั้งที่ 3
 <br>[คลิปเปรียบเทียบ Single cycle และ Multi cycle](https://www.youtube.com/watch?v=Gck7U_8bayQ&t=3s)
 
 ## การบ้านครั้งที่ 4
 ### การทำงานของ multi cycle ในคำสั่ง lw
 <br>[image](https://imagecloud.nos-eastchina1.126.net/Computer%20Engineering/Multi-cycle%20Datapath.PNG)
 lw => $rt,offset($rs)
 
 มีการทำงาน 5 ขั้นตอน
 
 1.PC ส่งคำสั่งมาเก็บที่ memory ส่งต่อไปยัง instruction register ขณะเดียวกันนำ PC + 4
 
 2.แปลงคำสั่ง นำค่า rs กับ rt เก็บที่ A,B นำค่า offset(แปลงเป็น 32 bits และทำการ shiftซ้าย 2 หลัก) มาที่ ALU และนำมาบวกกับ PC(PC+4) และไปเก็บที่ ALUout
 
 3.นำค่า จาก A เข้ามาบวกกับ offset และนำค่าไปไว้ที่ ALUout
 
 4.ค่าที่ได้จาก ALUout คือ address มันจะไปชี้ address นี้ที่ memory และก็อ่านค่าออกมา
 
 5.ค่าที่อ่านออกมานำไปใส่ใน register rt
 
 ### คลิปการบ้านครั้งที่ 4
 <br>[คลิปอธิบายการทำงานของ multi cycle ในคำสั่ง lw](https://www.youtube.com/watch?v=y4UWtdeEvj0&t=50s)
 
 ## การบ้านครั้งที่ 5
 ### การทำงานของ multi cycle ในคำสั่ง beq
 <br>[image](https://imagecloud.nos-eastchina1.126.net/Computer%20Engineering/Multi-cycle%20Datapath.PNG)
 beq => $rs,$rt,$offset
