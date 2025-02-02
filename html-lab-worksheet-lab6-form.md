# ใบงานการทดลอง HTML

## การทดลองที่ 6: การสร้างฟอร์ม
### วัตถุประสงค์
- สร้างฟอร์มรับข้อมูลได้ตามกำหนด
- เลือกใช้ประเภทของ input แบบต่างๆ ได้เหมาะสม
- สามารถใช้งาน form validation ได้

### ขั้นตอนการทดลอง
1. สร้างฟอร์มลงทะเบียนนักศึกษา:
```html
    <!-- กำหนดรูปแบบของฟอร์มบางส่วน -->
  <style>
        .form-group {
            margin-bottom: 15px;
        }
        
        .input-wrapper {
            display: flex;
            align-items: center;
        }
        
        .required-mark {
            color: red;
            margin-left: 5px;
        }
    </style>

    <body>
        <form action="/register" method="post">
            <!-- ส่วนข้อมูลส่วนตัว -->
            <fieldset>
                <legend>ข้อมูลส่วนตัว</legend>
                
                <div class="form-group">
                    <label for="studentId">รหัสนักศึกษา:</label>
                    <input type="text" id="studentId" name="studentId" 
                           pattern="[0-9]{8}" required>
                </div>
        
                <div class="form-group">
                    <label for="prefix">คำนำหน้า:</label>
                     <select id="prefix" name="prefix" required>
                        <option value="">เลือกคำนำหน้า</option>
                        <option value="mr">นาย</option>
                        <option value="ms">นางสาว</option>
                        <option value="mrs">นาง</option>
                    </select>
                </div>
        
                <div class="form-group">
                    <label for="firstName">ชื่อ:</label>
                    <input type="text" id="firstName" name="firstName" required>
                </div>
        
                <div class="form-group">
                    <label for="lastName">นามสกุล:</label>
                    <input type="text" id="lastName" name="lastName" required>
                </div>
        
                <div class="form-group">
                    <label for="birthdate">วันเกิด:</label>
                    <input type="date" id="birthdate" name="birthdate" required>
                </div>
        
                <div class="form-group">
                    <label>เพศ:</label>
                    <input type="radio" id="male" name="gender" value="male" required>
                    <label for="male">ชาย</label>
                    <input type="radio" id="female" name="gender" value="female">
                    <label for="female">หญิง</label>
                </div>
            </fieldset>
        
            <!-- ส่วนข้อมูลการติดต่อ -->
            <fieldset>
                <legend>ข้อมูลการติดต่อ</legend>
        
                <div class="form-group">
                    <label for="email">อีเมล:</label>
                    <input type="email" id="email" name="email" required>
                </div>
        
                <div class="form-group">
                    <label for="phone">เบอร์โทรศัพท์:</label>
                    <input type="tel" id="phone" name="phone" 
                           pattern="[0-9]{10}" required>
                </div>
        
                <div class="form-group">
                    <label for="address">ที่อยู่:</label>
                    <textarea id="address" name="address" 
                              rows="3" required></textarea> <span class="required-mark">*</span>
                </div>
            </fieldset>
        
            <!-- ส่วนข้อมูลการศึกษา -->
            <fieldset>
                <legend>ข้อมูลการศึกษา</legend>
        
                <div class="form-group">
                    <label for="faculty">คณะ:</label>
                    <select id="faculty" name="faculty" required>
                        <option value="">เลือกคณะ</option>
                        <option value="siet">ครุศาสตร์อุตสาหกรรมและเทคโนโลยี</option>
                        <option value="engineering">วิศวกรรมศาสตร์</option>
                        <option value="science">วิทยาศาสตร์</option>
                    </select> <span class="required-mark">*</span>
                </div>
        
                <div class="form-group">
                    <label for="major">สาขาวิชา:</label>
                    <select id="major" name="major" required>
                        <option value="">เลือกสาขาวิชา</option>
                        <!-- ตัวเลือกจะเปลี่ยนตามคณะที่เลือก ส่วนนี้ Code ยังไม่สมบูรณ์-->
                    </select> <span class="required-mark">*</span>
                </div>
        
                <div class="form-group">
                    <label for="gpa">เกรดเฉลี่ยสะสม:</label>
                    <input type="number" id="gpa" name="gpa" 
                           min="0" max="4" step="0.01" required> <span class="required-mark">*</span>
                </div>
            </fieldset>
        
            <!-- ส่วนความสนใจและกิจกรรม -->
            <fieldset>
                <legend>ความสนใจและกิจกรรม</legend>
        
                <div class="form-group">
                    <label>ความสนใจ:</label>
                    <input type="checkbox" id="sport" name="interests" value="sport">
                    <label for="sport">กีฬา</label>
                    <input type="checkbox" id="music" name="interests" value="music">
                    <label for="music">ดนตรี</label>
                    <input type="checkbox" id="art" name="interests" value="art">
                    <label for="art">ศิลปะ</label>
                    <input type="checkbox" id="tech" name="interests" value="tech">
                    <label for="tech">เทคโนโลยี</label>
                </div>
        
                <div class="form-group">
                    <label for="club">ชมรมที่สนใจ:</label>
                    <select id="club" name="club" multiple>
                        <option value="computer">ชมรมคอมพิวเตอร์</option>
                        <option value="robot">ชมรมหุ่นยนต์</option>
                        <option value="sport">ชมรมกีฬา</option>
                        <option value="music">ชมรมดนตรี</option>
                    </select>
                </div>
            </fieldset>
        
            <!-- ส่วนอัพโหลดเอกสาร -->
            <fieldset>
                <legend>เอกสารประกอบ</legend>
                <div class="form-group">
                    <label for="photo">รูปถ่าย:</label>
                    <input type="file" id="photo" name="photo" 
                           accept="image/*" required><span class="required-mark">*</span>
                </div>
        
                <div class="form-group">
                    <label for="transcript">ใบแสดงผลการเรียน:</label>
                    <input type="file" id="transcript" name="transcript" 
                           accept=".pdf,.doc,.docx" required>
                           <span class="required-mark">*</span>
                </div>
            </fieldset>
        
            <!-- ส่วนยืนยันข้อมูล -->
            <fieldset>
                <legend>การยืนยัน</legend>
        
                <div class="form-group">
                    <input type="checkbox" id="agree" name="agree" required>
                    <label for="agree">
                        ข้าพเจ้ายืนยันว่าข้อมูลทั้งหมดเป็นความจริง
                    </label>
                </div>
        
                <div class="form-group">
                    <button type="submit">ลงทะเบียน</button>
                    <button type="reset">ล้างข้อมูล</button>
                </div>
            </fieldset>
        </form>
```

### คำอธิบายเพิ่มเติม
1. Input Types ที่ใช้:
   - text: สำหรับข้อความทั่วไป
   - email: สำหรับอีเมล (มีการตรวจสอบรูปแบบอัตโนมัติ)
   - tel: สำหรับเบอร์โทรศัพท์
   - date: สำหรับวันที่
   - number: สำหรับตัวเลข
   - radio: สำหรับตัวเลือกเดียว
   - checkbox: สำหรับหลายตัวเลือก
   - file: สำหรับอัพโหลดไฟล์
   - select: สำหรับรายการแบบเลือก
   - textarea: สำหรับข้อความหลายบรรทัด

2. Attributes ที่สำคัญ:
   - required: จำเป็นต้องกรอก
   - pattern: กำหนดรูปแบบข้อมูล
   - min/max: กำหนดค่าต่ำสุด/สูงสุด
   - accept: กำหนดประเภทไฟล์ที่ยอมรับ
   - multiple: เลือกได้หลายตัวเลือก

### แบบฝึกหัด
1. สร้างฟอร์มสมัครสมาชิกร้านค้าออนไลน์ที่มี:
   - ข้อมูลส่วนตัว (ชื่อ-นามสกุล, วันเกิด, เพศ)
   - ข้อมูลการติดต่อ (อีเมล, เบอร์โทร, ที่อยู่จัดส่ง)
   - รูปโปรไฟล์
   - การยืนยันรหัสผ่าน
   - ความสนใจในหมวดหมู่สินค้า
   - การยอมรับเงื่อนไขการใช้งาน

2. เพิ่ม validation ที่เหมาะสม:
   - ตรวจสอบรูปแบบอีเมล
   - ตรวจสอบความยาวรหัสผ่าน
   - ตรวจสอบรูปแบบเบอร์โทร
   - ตรวจสอบขนาดไฟล์รูปภาพ

### บันทึกผลการทดลอง
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ฟอร์มสมัครสมาชิก</title>
    <style>
        body { font-family: Arial, sans-serif; background-color: #f4f4f9; margin: 20px; }
        form { background-color: #fff; padding: 20px; border-radius: 8px; box-shadow: 0 0 10px rgba(0, 0, 0, 0.1); }
        label { display: block; margin: 10px 0 5px; }
        input, select, textarea { width: 100%; padding: 8px; margin: 8px 0 15px; border: 1px solid #ddd; border-radius: 4px; }
        .error { color: red; font-size: 0.9em; }
        .submit-btn { background-color: #4CAF50; color: white; border: none; padding: 10px 20px; cursor: pointer; }
        .submit-btn:hover { background-color: #45a049; }
    </style>
</head>
<body>

    <h1>ฟอร์มสมัครสมาชิกร้านค้าออนไลน์</h1>
    
    <form id="registrationForm" action="#" method="POST" enctype="multipart/form-data">
        <!-- ข้อมูลส่วนตัว -->
        <fieldset>
            <legend>ข้อมูลส่วนตัว</legend>
            
            <label for="name">ชื่อ-นามสกุล</label>
            <input type="text" id="name" name="name" required>

            <label for="dob">วันเกิด</label>
            <input type="date" id="dob" name="dob" required>

            <label for="gender">เพศ</label>
            <select id="gender" name="gender" required>
                <option value="">เลือกเพศ</option>
                <option value="male">ชาย</option>
                <option value="female">หญิง</option>
                <option value="other">อื่นๆ</option>
            </select>
        </fieldset>
        
        <!-- ข้อมูลการติดต่อ -->
        <fieldset>
            <legend>ข้อมูลการติดต่อ</legend>
            
            <label for="email">อีเมล</label>
            <input type="email" id="email" name="email" required>
            <div id="emailError" class="error"></div>

            <label for="phone">เบอร์โทร</label>
            <input type="tel" id="phone" name="phone" required pattern="^[0-9]{10}$">
            <div id="phoneError" class="error"></div>

            <label for="address">ที่อยู่จัดส่ง</label>
            <textarea id="address" name="address" rows="4" required></textarea>
        </fieldset>

        <!-- รูปโปรไฟล์ -->
        <fieldset>
            <legend>รูปโปรไฟล์</legend>
            
            <label for="profilePic">อัปโหลดรูปโปรไฟล์ (ไฟล์ jpg, png เท่านั้น)</label>
            <input type="file" id="profilePic" name="profilePic" accept=".jpg, .jpeg, .png" required>
            <div id="profilePicError" class="error"></div>
        </fieldset>

        <!-- การยืนยันรหัสผ่าน -->
        <fieldset>
            <legend>การยืนยันรหัสผ่าน</legend>
            
            <label for="password">รหัสผ่าน</label>
            <input type="password" id="password" name="password" required minlength="6">
            <div id="passwordError" class="error"></div>

            <label for="confirmPassword">ยืนยันรหัสผ่าน</label>
            <input type="password" id="confirmPassword" name="confirmPassword" required>
            <div id="confirmPasswordError" class="error"></div>
        </fieldset>

        <!-- ความสนใจในหมวดหมู่สินค้า -->
        <fieldset>
            <legend>ความสนใจในหมวดหมู่สินค้า</legend>
            
            <label for="interests">เลือกหมวดหมู่ที่คุณสนใจ</label>
            <select id="interests" name="interests" required multiple>
                <option value="electronics">อิเล็กทรอนิกส์</option>
                <option value="fashion">แฟชั่น</option>
                <option value="homeGoods">ของใช้ในบ้าน</option>
                <option value="books">หนังสือ</option>
                <option value="game">เล่นเกมส์</option>
            </select>
        </fieldset>

        <!-- การยอมรับเงื่อนไข -->
        <fieldset>
            <label for="terms">
                <input type="checkbox" id="terms" name="terms" required> ยอมรับเงื่อนไขการใช้งาน
            </label>
        </fieldset>

        <!-- ปุ่มสมัครสมาชิก -->
        <button type="submit" class="submit-btn">สมัครสมาชิก</button>
    </form>

    <script>
        // ตรวจสอบฟอร์ม
        document.getElementById("registrationForm").onsubmit = function(event) {
            event.preventDefault();
            
            // ตรวจสอบอีเมล
            const email = document.getElementById("email").value;
            const emailPattern = /^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,4}$/;
            const emailError = document.getElementById("emailError");
            emailError.textContent = emailPattern.test(email) ? "" : "รูปแบบอีเมลไม่ถูกต้อง";

            // ตรวจสอบเบอร์โทร
            const phone = document.getElementById("phone").value;
            const phonePattern = /^[0-9]{10}$/;
            const phoneError = document.getElementById("phoneError");
            phoneError.textContent = phonePattern.test(phone) ? "" : "เบอร์โทรต้องมี 10 หลัก";

            // ตรวจสอบรหัสผ่าน
            const password = document.getElementById("password").value;
            const confirmPassword = document.getElementById("confirmPassword").value;
            const passwordError = document.getElementById("passwordError");
            const confirmPasswordError = document.getElementById("confirmPasswordError");
            passwordError.textContent = password.length >= 6 ? "" : "รหัสผ่านต้องมีอย่างน้อย 6 ตัวอักษร";
            confirmPasswordError.textContent = password === confirmPassword ? "" : "รหัสผ่านและยืนยันรหัสผ่านไม่ตรงกัน";

            // ตรวจสอบขนาดไฟล์รูปภาพ
            const profilePic = document.getElementById("profilePic").files[0];
            const profilePicError = document.getElementById("profilePicError");
            if (profilePic && (profilePic.size > 2 * 1024 * 1024)) {
                profilePicError.textContent = "ขนาดไฟล์รูปภาพไม่เกิน 2MB";
            } else {
                profilePicError.textContent = "";
            }

            // ถ้าทุกอย่างถูกต้อง, ส่งฟอร์ม
            if (!emailError.textContent && !phoneError.textContent && !passwordError.textContent && !confirmPasswordError.textContent && !profilePicError.textContent) {
                alert("สมัครสมาชิกสำเร็จ!");
        
            }
        }
    </script>

</body>
</html>
```html

```
- ภาพผลลัพธ์:
![image](https://github.com/user-attachments/assets/14a9e5bd-4253-4381-b707-703e0a1cdbd2)
![image](https://github.com/user-attachments/assets/482f8ba4-f25a-4f46-82cb-df1edf67244e)




