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

### การบ้านครั้งที่ 1
<br>[คลิปอธิบายคำสั่ง JUMP in MIPS](https://www.youtube.com/watch?v=t2JYzAhNM5A)

