เพื่อให้เห็นความหลากหลาย ผมขอเสนอหนึ่งฟังก์ชันใหม่ที่ชื่อว่า **`analyze_scores`** ครับ

ฟังก์ชันนี้จะไม่ได้แค่คำนวณเกรดเฉลี่ย แต่จะ **สรุปภาพรวม** ของคะแนนทั้งหมดออกมา (เช่น คะแนนสูงสุด, คะแนนต่ำสุด และบอกว่าผ่านหรือไม่ผ่าน) โดยใช้คำสั่ง Python ที่กระชับขึ้น (Built-in functions) ครับ

```python
def analyze_scores(score_list):
    if not score_list:
        return "ไม่มีข้อมูลคะแนน"

    # ใช้ sum() และ len() แทนการใช้ for loop เพื่อความรวดเร็ว
    average = sum(score_list) / len(score_list)
    
    # หาคะแนนสูงสุดและต่ำสุดด้วย max() และ min()
    highest = max(score_list)
    lowest = min(score_list)
    
    # กำหนดสถานะการผ่าน (เช่น ถ้าเฉลี่ยเกิน 50 คือผ่าน)
    status = "Pass" if average >= 50 else "Fail"
    
    # ส่งค่ากลับเป็น Dictionary เพื่อให้อ่านเข้าใจง่าย
    return {
        "Average": round(average, 2),
        "Max": highest,
        "Min": lowest,
        "Status": status
    }

# --- วิธีการใช้งาน ---
my_scores = [85, 92, 78, 88, 95]
result = analyze_scores(my_scores)

print("สรุปผลคะแนน:")
print(f"คะแนนเฉลี่ย: {result['Average']}")
print(f"คะแนนสูงสุด: {result['Max']}")
print(f"คะแนนต่ำสุด: {result['Min']}")
print(f"สถานะ: {result['Status']}")
```.

### สิ่งที่ฟังก์ชันนี้พัฒนาขึ้นจากเดิม:
1.  **ใช้ `sum()` และ `len()`**: แทนการสร้างตัวแปร `total = 0` แล้ววน Loop ซึ่งช่วยให้ Code สั้นลงและอ่านง่ายขึ้น
2.  **ใช้ `max()` และ `min()`**: ช่วยให้รู้ช่วงคะแนนของนักเรียนได้ทันที
3.  **การใช้ Dictionary**: การ return ค่ากลับเป็น Dictionary ช่วยให้เราเรียกใช้งานข้อมูลตามชื่อ Key ได้เลย (เช่น `result['Max']`) ทำให้ Code ส่วนอื่นที่จะเอาไปใช้ต่อไม่สับสน
4.  **Round Function**: มีการใช้ `round(average, 2)` เพื่อคุมทศนิยมให้เหลือ 2 ตำแหน่งครับ
