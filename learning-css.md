# 🏜️พื้นฐาน css
css = ภาษาที่ใช้ในการตกแต่ง HTML เช่น เปลี่ยนสี ขนาด จัด layout

## ✒️วิธีเขียน css
### 1.Inline CSS
```html
<p style="color:red;">ข้อความนี้สีแดง</p>
```

### 2.Internal CSS
```html
<head>
    <style>
        p {
            color: red;
        }
    </style>
</head>
```

### 3.External CSS
```html
<link rel="stylesheet" href="style.css">
```

ใน style.css ก็เพิ่ม
```css
p {
    color: red;
}
```

## 🖋️Selectors ตัวเลือก
```css
/* เลือก element */
p { color: blue; }

/*เลือก class */
.title { font-size: 24px; }

/* เลือก id */
#main { background: yellow;}

/* เลือกซ้อน */
div p { color: green; }

/* Pseudo-class */
a:hover { color: red; }
```

## Box Model
ทุก element จะมีกรอบแบบนี้
```scss
Margin (รอบนอกสุด)
Border
Padding
Content
```

```css
.box {
    width: 200px;
    padding: 20px;
    border: 5px solid black;
    margin: 10px;
}
```

## Flexbox ตัวอย่าง
```css
.container {
    display: flex;
    justify-content: center; /* จัดแนวนอน */
    align-items: center; /* จัดแนวตั้ง */
    gap: 20px;
}
```

## Responsive (Media Queries)
```css
@media (max-width: 768px) {
    body {
        background: lightblue;
    }
}
```

## Animation
```css
.box {
    width: 100px;
    height: 100px;
    background: red;
    animation: bounce 2s infinite;
}

@keyframes bounce {
    0% { transform: translateY(0); }
    50% { transform: translateY(-50px); }
    100% { transform: translateY(0); }
}
```

## อธิบายเพิ่มที่มีใน miniProject01
- ลองสร้างหน้า Landing page ง่ายๆ ด้วย html + แต่งด้วย css
- จัดกึ่งกลาง ทำข้อความอยู่ในกรอบแบบเหมือนการ์ด ขอบมน
- มีปุ่ม ให้มีเอฟเฟคเวลาเอาเม้าไปวาง แบบเปลี่ยนสีและมีเด้งออกมานิดนึง 
- ปุ่ม เชื่อมไปหน้า To-do List ที่เราจะทำเป็นโปรเจคจริงๆ
- miniProject01 นี้ ฝึกการตกแต่งด้วย css เช่น การกำหนดตำแหน่ง, ใส่สี, ดึงฟอนต์จาก google, จะระขอบ, การทำขอบมน, การใส่เงา, การตกแต่งตัวหนังสือ, การตกแต่งปุ่ม, การใส่เอฟเฟค hover

### flexbox มี 2 แบบ
1. Main axis แกนหลัก → แนวนอน(ซ้าย-ขวา)
2. Cross axis แกนข้าม → แนวตั้ง(บน-ล่าง)
    การปรับด้วย css คือ
    - justify-content = จัดตามแกนหลัก
    - align-items = จัดตามแกนข้าม

ในโปรเจค miniProject01 ใส่ css ตรง body ว่า `display:flex;`
- จัดให้เป็น flex container
- ปกติ body หรือ div ธรรมดา จะวาง element ข้างในหรือเรียกว่าลูก จัดเรียงลงมา (block)
- ถ้าเปลี่ยนเป็น flex ลูกๆ(child elements)ข้างใน body จะถูกเรียงด้วยกฏ flexbox

#### 💡แล้วกฎของ flexbox คืออะไร?
คือสิ่งที่เราสามารถกำหนดต่อได้ว่าอยากให้ลูกๆ ข้างในเรียงยังไง ซึ่งมีชุดคุณสมบัติดังนี้
- flex-direction -> กำหนดทิศทางการเรียง 
    🔹row = เรียงจากซ้ายไปขวา
    🔹column = เรียงจากบนลงล่าง
- justify-content -> จัดตำแหน่งแนวนอน 
    🔹flex-start = ชิดซ้าย
    🔹center = อยู่กลางแนวนอน
    🔹flex-end = ชิดขวา
    🔹space-between = ลูกๆ กระจายเต็มแนวกว้าง (ไม่มีช่องว่างหัวท้าย)
    🔹space-around = กระจายเต็มแนวกว้าง แต่มีช่องว่างรอบๆ ลูก
- align-items -> จัดตำแหน่งแนวตั้ง
    🔹flex-start = ชิดบน
    🔹center = อยู่กลางแนวตั้ง
    🔹flex-end = ชิดล่าง
    🔹stretch = ยืดสูงสุดเต็ม container
    🔹baseline = จัดตามบรรทัดของตัวอักษร
- flex-wrap -> ให้ลูกๆ ขึ้นบรรทัดใหม่ได้ถ้ามีพื้นที่ไม่พอ

เพราะงั้นใน miniProject01 เราใช้เป็น 
    🔹`justify-content: center;` ->กลางแนวนอน
    🔹`align-items: center;` ->กลางแนวตั้ง
    👉ผลลัพธ์การ์ด .card ก็อยู่กลางเว็บ

### height
กำหนด height เพื่อ
1.ควบคุมขนาดของ container -> ถ้าไม่กำหนด height พวกกล่องต่างๆ เช่น div, section, body จะสูงเท่ากับเนื้อหาที่อยู่ คือเราอยากให้ขยายกล่องสูงๆ  ถึงแม้ข้างในมันจะมีเนื้อหาน้อยอะ
2.จัดตำแหน่งง่าย แบบว่าเราใช้ flexbox จัดกลาง ถ้าไม่มี height มันไม่มีพื้นที่พอจะเอาของไปอยู่กลางแนวตั้ง พอเราใส่ `height: 100vh` -> ตอนนี้ container สูงเท่าจอละ พวกลูกๆก็จะจัดกลางพอดี
3.ทำพื้นหลังเต็มจอ background อาจจะเป็นภาพหรือใส่สี ไล่สีก็ได้ ใส่ height เต็มๆ พื้นหลังก็เต็มจอ
4.ออกแบบ layout ที่คุมได้แน่นอน เช่นถ้าเราอยากให้เต็มจอ ก็ใส่100 อยากให้แสดงผลครึ่งจอก็ใส่ 50

#### 100vh
ในโปรเจกต์เราใช้เป็น `height: 100vh;` 
- vh = viewport height ความสูงของหน้าจอแสดงผล/ความสูงของหน้าจอที่มองเห็นตอนนั้น
- 100vh = 100% ของความสูงจอ
- คือถ้าเราอยากให้ background หรือ body เต็มจอ ก็ใช้การกำหนดค่านี้แหล่ะ
👉เช่น ถ้าจอสูง 800px กำหนด 100vh = 800px 
👉หรือ ถ้าจอสูง 1000px กำหนด 100vh = 1000px 
👉หรือ ถ้าจอสูง 800px กำหนด 50vh = 400px  (ลดครึ่งนึง)

❓แล้วเราจะไม่ใส่ height ได้ไหม -> ไม่ใส่ก็ได้ มันก็จะสูงตามเนื้อหา อันนี้แล้วแต่เราอะว่าอยากให้มันเป็นแบบไหน
- แต่ถ้าอยากกำหนดขนาดชัดเจนก็ใส่ height
- อย่างใน miniProject01 ของเราอะ อยากทำเป็นกล่องข้อความอยู่กลางจอ ก็ต้องใส่ height เพื่อจัดกึ่งกลางให้ได้ เพราะถ้าไม่ใส่ มันไม่มีพื้นที่พอจะเอากล่องข้อความเราไปอยู่กลางแนวตั้ง

#### 100dvh
- dvh = dynamic viewport height ความสูง viewport ที่มองเห็นจริงแบบ dynamic
- concept เหมือน 100vh เพียงแต่ว่ามันมีมาเพื่อแก้ปัญหาดูผ่านมือถือ บางทีพวก browser มันมี toolbar ละถ้าใช้ 100vh element อาจเกินจอที่แสดง ก็ต้องเลื่อนจอลงละจะเห็นครบ
- ตัวนี้จะแสดงเฉพาะพื้นที่จริงที่แสดงๆจริงๆเลย -> element พอดีกับจอ

### background
- linear-gradient(...) เป็นฟังก์ชันของ css ไล่สี 
- to right = ไล่จากซ้าย ไป ขวา ซึ่งอันนี้เรากำหนดเองได้มีแบบอื่นๆอีก เช่น to left = ไล่จากขวา ไป ซ้าย
- พื้นหลัง เราใช้การไล่สีใน body พื้นที่กล่อง body ก็จะเป็นสีตามที่เรากำหนด
- ส่วนค่าสีคือจริงๆมันใส่ได้หลายแบบ แต่เราใส่ค่าแบบ Hex ที่มี # ด้านหน้า สำหรับเรามันก็ง่ายดี เราหาในเว็บอื่นๆละก็อปค่าสีมาใส่

