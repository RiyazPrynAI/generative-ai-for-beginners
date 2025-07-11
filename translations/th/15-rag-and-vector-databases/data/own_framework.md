<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "df98b2c59f87d8543135301e87969f70",
  "translation_date": "2025-05-20T02:20:21+00:00",
  "source_file": "15-rag-and-vector-databases/data/own_framework.md",
  "language_code": "th"
}
-->
# บทนำเกี่ยวกับเครือข่ายประสาทเทียม. Perceptron หลายชั้น

ในส่วนก่อนหน้านี้ คุณได้เรียนรู้เกี่ยวกับแบบจำลองเครือข่ายประสาทที่ง่ายที่สุด - perceptron หนึ่งชั้น ซึ่งเป็นแบบจำลองการจำแนกประเภทสองชั้นเชิงเส้น

ในส่วนนี้เราจะขยายแบบจำลองนี้ไปสู่กรอบการทำงานที่ยืดหยุ่นมากขึ้น ซึ่งจะช่วยให้เรา:

* ทำ **การจำแนกประเภทหลายชั้น** นอกเหนือจากสองชั้น
* แก้ปัญหา **การถดถอย** นอกเหนือจากการจำแนกประเภท
* แยกประเภทที่ไม่สามารถแยกเชิงเส้นได้

เราจะพัฒนากรอบการทำงานแบบโมดูลของเราเองใน Python ที่จะช่วยให้เราสร้างสถาปัตยกรรมเครือข่ายประสาทที่แตกต่างกันได้

## การกำหนดปัญหาการเรียนรู้ของเครื่อง

เริ่มต้นด้วยการกำหนดปัญหาการเรียนรู้ของเครื่อง สมมติว่าเรามีชุดข้อมูลการฝึก **X** พร้อมป้ายกำกับ **Y** และเราจำเป็นต้องสร้างแบบจำลอง *f* ที่จะทำให้การทำนายมีความแม่นยำมากที่สุด คุณภาพของการทำนายจะถูกวัดโดย **ฟังก์ชันการสูญเสีย** ℒ ฟังก์ชันการสูญเสียต่อไปนี้มักใช้:

* สำหรับปัญหาการถดถอย เมื่อเราต้องการทำนายตัวเลข เราสามารถใช้ **ข้อผิดพลาดสัมบูรณ์** ∑<sub>i</sub>|f(x<sup>(i)</sup>)-y<sup>(i)</sup>| หรือ **ข้อผิดพลาดกำลังสอง** ∑<sub>i</sub>(f(x<sup>(i)</sup>)-y<sup>(i)</sup>)<sup>2</sup>
* สำหรับการจำแนกประเภท เราใช้ **การสูญเสีย 0-1** (ซึ่งโดยทั่วไปคือ **ความแม่นยำ** ของแบบจำลอง) หรือ **การสูญเสียเชิงลอจิสติก**

สำหรับ perceptron หนึ่งระดับ ฟังก์ชัน *f* ถูกกำหนดเป็นฟังก์ชันเชิงเส้น *f(x)=wx+b* (ที่นี่ *w* คือเมทริกซ์น้ำหนัก *x* คือเวกเตอร์ของคุณลักษณะนำเข้า และ *b* คือเวกเตอร์ไบแอส) สำหรับสถาปัตยกรรมเครือข่ายประสาทที่แตกต่างกัน ฟังก์ชันนี้สามารถมีรูปแบบที่ซับซ้อนมากขึ้นได้

> ในกรณีของการจำแนกประเภท มักจะต้องการให้ได้ความน่าจะเป็นของประเภทที่สอดคล้องกันเป็นผลลัพธ์ของเครือข่าย เพื่อแปลงตัวเลขใดๆ ให้เป็นความน่าจะเป็น (เช่น เพื่อปรับผลลัพธ์ให้เป็นปกติ) เรามักใช้ **ฟังก์ชัน softmax** σ และฟังก์ชัน *f* กลายเป็น *f(x)=σ(wx+b)*

ในการกำหนด *f* ข้างต้น *w* และ *b* เรียกว่า **พารามิเตอร์** θ=⟨*w,b*⟩ เมื่อให้ชุดข้อมูล ⟨**X**,**Y**⟩ เราสามารถคำนวณข้อผิดพลาดโดยรวมในชุดข้อมูลทั้งหมดเป็นฟังก์ชันของพารามิเตอร์ θ

> ✅ **เป้าหมายของการฝึกเครือข่ายประสาทคือการลดข้อผิดพลาดโดยการเปลี่ยนแปลงพารามิเตอร์ θ**

## การปรับแต่ง Gradient Descent

มีวิธีการที่รู้จักกันดีในการปรับแต่งฟังก์ชันที่เรียกว่า **gradient descent** แนวคิดคือเราสามารถคำนวณอนุพันธ์ (ในกรณีหลายมิติเรียกว่า **gradient**) ของฟังก์ชันการสูญเสียด้วยความเคารพต่อพารามิเตอร์ และเปลี่ยนแปลงพารามิเตอร์ในลักษณะที่ข้อผิดพลาดจะลดลง สิ่งนี้สามารถกำหนดเป็นรูปแบบดังนี้:

* เริ่มต้นพารามิเตอร์ด้วยค่าบางอย่างแบบสุ่ม w<sup>(0)</sup>, b<sup>(0)</sup>
* ทำซ้ำขั้นตอนต่อไปนี้หลายครั้ง:
    - w<sup>(i+1)</sup> = w<sup>(i)</sup>-η∂ℒ/∂w
    - b<sup>(i+1)</sup> = b<sup>(i)</sup>-η∂ℒ/∂b

ระหว่างการฝึก ขั้นตอนการปรับแต่งจะคำนวณโดยพิจารณาจากชุดข้อมูลทั้งหมด (จำไว้ว่าการสูญเสียคำนวณเป็นผลรวมผ่านตัวอย่างการฝึกทั้งหมด) อย่างไรก็ตาม ในชีวิตจริง เราจะใช้ส่วนเล็กๆ ของชุดข้อมูลที่เรียกว่า **minibatches** และคำนวณ gradients ตามชุดย่อยของข้อมูล เนื่องจากชุดย่อยถูกสุ่มเลือกในแต่ละครั้ง วิธีนี้เรียกว่า **stochastic gradient descent** (SGD)

## Perceptrons หลายชั้นและการถดถอยหลัง

เครือข่ายหนึ่งชั้น ตามที่เราเห็นข้างต้น สามารถจำแนกประเภทที่แยกเชิงเส้นได้ เพื่อสร้างแบบจำลองที่ร่ำรวยมากขึ้น เราสามารถรวมหลายชั้นของเครือข่ายเข้าด้วยกัน ในทางคณิตศาสตร์หมายความว่าฟังก์ชัน *f* จะมีรูปแบบที่ซับซ้อนมากขึ้น และจะคำนวณในหลายขั้นตอน:
* z<sub>1</sub>=w<sub>1</sub>x+b<sub>1</sub>
* z<sub>2</sub>=w<sub>2</sub>α(z<sub>1</sub>)+b<sub>2</sub>
* f = σ(z<sub>2</sub>)

ที่นี่, α คือ **ฟังก์ชันการกระตุ้นที่ไม่เชิงเส้น**, σ คือฟังก์ชัน softmax, และพารามิเตอร์ θ=<*w<sub>1</sub>,b<sub>1</sub>,w<sub>2</sub>,b<sub>2</sub>*>

อัลกอริธึม gradient descent จะยังคงเหมือนเดิม แต่จะยากขึ้นในการคำนวณ gradients ด้วยกฎการแยกโซ่ เราสามารถคำนวณอนุพันธ์เป็น:

* ∂ℒ/∂w<sub>2</sub> = (∂ℒ/∂σ)(∂σ/∂z<sub>2</sub>)(∂z<sub>2</sub>/∂w<sub>2</sub>)
* ∂ℒ/∂w<sub>1</sub> = (∂ℒ/∂σ)(∂σ/∂z<sub>2</sub>)(∂z<sub>2</sub>/∂α)(∂α/∂z<sub>1</sub>)(∂z<sub>1</sub>/∂w<sub>1</sub>)

> ✅ กฎการแยกโซ่ใช้ในการคำนวณอนุพันธ์ของฟังก์ชันการสูญเสียด้วยความเคารพต่อพารามิเตอร์

โปรดทราบว่าฝั่งซ้ายสุดของนิพจน์เหล่านั้นทั้งหมดเหมือนกัน และดังนั้นเราจึงสามารถคำนวณอนุพันธ์ได้อย่างมีประสิทธิภาพโดยเริ่มจากฟังก์ชันการสูญเสียและไป "ย้อนกลับ" ผ่านกราฟการคำนวณ ดังนั้นวิธีการฝึก perceptron หลายชั้นจึงเรียกว่า **การถดถอยหลัง**, หรือ 'backprop'

> ✅ เราจะครอบคลุม backprop ในรายละเอียดเพิ่มเติมในตัวอย่าง notebook ของเรา

## สรุป

ในบทเรียนนี้ เราได้สร้างไลบรารีเครือข่ายประสาทของเราเอง และเราได้ใช้มันสำหรับงานการจำแนกประเภทสองมิติที่ง่าย

## 🚀 ท้าทาย

ใน notebook ที่มาพร้อมนี้ คุณจะสร้างกรอบการทำงานของคุณเองสำหรับการสร้างและฝึก perceptrons หลายชั้น คุณจะสามารถเห็นรายละเอียดว่าเครือข่ายประสาทสมัยใหม่ทำงานอย่างไร

ดำเนินการไปยัง notebook OwnFramework และทำงานผ่านมัน

## การทบทวนและการศึกษาเอง

การถดถอยหลังเป็นอัลกอริธึมทั่วไปที่ใช้ใน AI และ ML ควรศึกษาในรายละเอียดเพิ่มเติม

## การมอบหมาย

ในห้องปฏิบัติการนี้ คุณถูกขอให้ใช้กรอบการทำงานที่คุณสร้างในบทเรียนนี้เพื่อแก้ปัญหาการจำแนกประเภทตัวเลขที่เขียนด้วยมือ MNIST

* คำแนะนำ
* Notebook

**ข้อจำกัดความรับผิดชอบ**:  
เอกสารนี้ได้รับการแปลโดยใช้บริการแปลภาษา AI [Co-op Translator](https://github.com/Azure/co-op-translator) แม้ว่าเราจะพยายามให้การแปลมีความถูกต้อง แต่โปรดทราบว่าการแปลโดยอัตโนมัติอาจมีข้อผิดพลาดหรือความไม่ถูกต้อง เอกสารต้นฉบับในภาษาต้นทางควรถือเป็นแหล่งข้อมูลที่เชื่อถือได้ สำหรับข้อมูลที่สำคัญ แนะนำให้ใช้บริการแปลภาษามนุษย์มืออาชีพ เราจะไม่รับผิดชอบต่อความเข้าใจผิดหรือการตีความที่เกิดจากการใช้การแปลนี้