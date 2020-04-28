# 6110613269
### Computer Architecture สถาปัตยกรรมคอมพิวเตอร์
##### สรุปเนื้อหา
  
MIPS Instruction format
ทุกคำสั่งของ MIPS จะถูกเข้ารหัสโดย binary และจะมีขนาด 32 bits
มีอยู่ 3 ประเภท

<br>
![image](https://www.google.com/url?sa=i&url=https%3A%2F%2Fwww.researchgate.net%2Ffigure%2FThe-MIPS-instruction-format_fig1_269463299&psig=AOvVaw2ZCN6lnToN01nAlnZiq36K&ust=1588139638895000&source=images&cd=vfe&ved=0CAIQjRxqFwoTCKDRg6-3iukCFQAAAAAdAAAAABAD)

* R-Format ใช้ในการคำนวณทางตรรกศาสตร์
  * ALU  =>  alu $rd,$rs,$rt
  * jr   =>  jr  $rs

* I-Format ใช้ย้ายข้อมูลเปลี่ยนข้อมูล
  * ALUi    =>  alui $rt,$rs,value
  * Data Tranfers  =>  lw $rt,offset($rs)
                     sw $rt,offset($rs)
  * Branch  =>  beq $rs,$rt,offset
  
 * J-Format ย้ายไปทำงานที่อื่น
  * Jump    =>  j address
  * Jump&Link   =>  jal address
  
  



