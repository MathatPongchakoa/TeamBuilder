# Pokémon GO Team Builder

แอปพลิเคชันสำหรับสร้างและจัดการทีม Pokémon โดยใช้ Flutter + GetX + GetStorage

## 📋 ข้อกำหนดโปรเจค (Requirements)

### **วัตถุประสงค์**
พัฒนาแอป Pokémon GO Team Builder จากสัปดาห์ที่ 1 ด้วยฟีเจอร์เพิ่มเติมเพื่อให้มีการโต้ตอบและดูเป็นมืออาชีพมากขึ้น

### **การปรับปรุงที่แนะนำ**
- 🖼️ **Display Pokémon images** - แสดงรูปภาพ Pokémon จาก PokeAPI
- ✏️ **Edit team name** - แก้ไขชื่อทีมและบันทึกด้วย GetStorage  
- 🎨 **Visual feedback** - แอนิเมชันเมื่อเลือก/ยกเลิก Pokémon
- 📦 **Persist team data** - เก็บข้อมูลทีมให้โหลดเมื่อเปิดแอปใหม่
- 🔗 **Reset Team button** - ปุ่มรีเซ็ตการเลือก
- 💡 **Search functionality** - ช่องค้นหา Pokémon

## ✅ สถานะการพัฒนา (Development Status)

| ฟีเจอร์ | สถานะ | รายละเอียด |
|---------|--------|------------|
| 🖼️ **Pokémon Images** | ✅ **สำเร็จ** | ใช้ PokeAPI sprites แสดงรูปใน Grid และ Team preview |
| ✏️ **Edit Team Name** | ✅ **สำเร็จ** | Dialog แก้ไขชื่อทีม + บันทึกด้วย GetStorage |
| 🎨 **Visual Feedback** | ✅ **สำเร็จ** | AnimatedContainer พร้อมเปลี่ยนสีเมื่อเลือก |
| 📦 **Data Persistence** | ✅ **สำเร็จ** | GetStorage เก็บทีมทั้งหมด รวมรูปภาพ |
| 🔗 **Reset Team** | ✅ **สำเร็จ** | ปุ่มล้างการเลือกในทั้ง 2 หน้า |
| 💡 **Search Bar** | ✅ **สำเร็จ** | ค้นหาชื่อ Pokémon แบบ Real-time |
| 🎯 **GetX State Management** | ✅ **สำเร็จ** | ใช้ Obx() และ reactive variables |
| 🏗️ **Clean Architecture** | ✅ **สำเร็จ** | แยก Controller แต่ละหน้า แบบ modular |

## 🚀 การติดตั้งและรัน

### **ข้อกำหนดระบบ**
- Flutter SDK >= 3.0.0
- Dart SDK >= 3.0.0

### **Dependencies ที่ใช้**
```yaml
dependencies:
  flutter:
    sdk: flutter
  get: ^4.6.6           # State Management
  get_storage: ^2.1.1   # Local Storage
  http: ^1.1.0          # HTTP Requests
```

### **วิธีการรัน**

1. **Clone โปรเจค**
```bash
git clone https://github.com/MathatPongchakoa/TeamBuilder.git
cd TeamBuilder
```

2. **ติดตั้ง Dependencies**
```bash
flutter pub get
```

3. **รันแอป**
```bash
flutter run -d chrome
```

## 📱 วิธีการใช้งาน

### **1. หน้าแรก - Pokemon List**
- **เรียกดู Pokémon**: แตะที่ Pokémon เพื่อดูรายละเอียด
- **สร้างทีม**: กด "สร้างทีม" เพื่อเข้าสู่โหมดเลือกทีม
- **ค้นหา**: ใช้ช่องค้นหาด้านบนเพื่อหา Pokémon
- **ไปหน้าทีม**: กด "ทีมของฉัน" เพื่อดูทีมที่บันทึกไว้

### **2. โหมดเลือกทีม**
- **เลือก Pokémon**: แตะเพื่อเลือก (สูงสุด 3 ตัว)
- **ดูทีมที่เลือก**: แสดงด้านบนพร้อมรูปภาพ
- **ล้างทีม**: กด "ล้างทั้งหมด" เพื่อรีเซ็ต
- **บันทึกทีม**: กด "บันทึก" เมื่อเลือกครบ 3 ตัว
- **ออกจากโหมด**: กด X เพื่อออกจากโหมดเลือก

### **3. หน้าจัดการทีม**
- **ดูทีมทั้งหมด**: รายการทีมที่บันทึกไว้
- **แก้ไขชื่อทีม**: กดปุ่มแก้ไข (ดินสอ)
- **เปลี่ยน Pokémon**: กดปุ่ม Pets เพื่อแก้ไขสมาชิกทีม
- **ลบทีม**: กดปุ่มถังขยะ

### **4. หน้าแก้ไขทีม**
- **เลือก Pokémon ใหม่**: เหมือนโหมดเลือกทีม
- **ดูการเลือกปัจจุบัน**: แสดงด้านบนพร้อมตัวเลข
- **รีเซ็ต**: กด "ล้างทั้งหมด" เพื่อเริ่มใหม่
- **บันทึก**: กดปุ่ม Save เมื่อเลือกครบ 3 ตัว

## 🏗️ สถาปัตยกรรม (Architecture)

### **โครงสร้างไฟล์**
```
lib/
├── main.dart                    # Entry point
└── page/
    ├── player.dart              # หน้าแรก + โหมดเลือกทีม
    ├── team_manager.dart        # หน้าจัดการทีม
    ├── pokemon_detail.dart      # รายละเอียด Pokémon
    └── EditTeamPage.dart        # หน้าแก้ไขทีม
```

### **Controllers (GetX)**
- `PlayerSelectionController` - จัดการหน้าแรกและโหมดเลือก
- `TeamManagerController` - จัดการทีมที่บันทึก
- `EditTeamController` - จัดการการแก้ไขทีม
- `PokemonDetailController` - จัดการรายละเอียด Pokémon

### **ข้อมูลที่เก็บ (GetStorage)**
```json
{
  "teams": [
    {
      "teamName": "My Awesome Team",
      "pokemons": [
        {
          "id": "1",
          "name": "bulbasaur", 
          "image": "https://raw.githubusercontent.com/.../1.png",
          "url": "https://pokeapi.co/api/v2/pokemon/1/"
        }
      ]
    }
  ]
}
```

## 🔧 เทคโนโลยีที่ใช้

- **Flutter**: UI Framework
- **GetX**: State Management + Navigation + Storage
- **GetStorage**: Local Data Persistence
- **HTTP**: API Calls
- **PokeAPI**: Pokemon Data Source

## 🎯 ฟีเจอร์เด่น

### **1. Reactive UI**
- ใช้ `Obx()` สำหรับ real-time updates
- UI อัพเดททันทีเมื่อ state เปลี่ยน

### **2. Smooth Animations**
- `AnimatedContainer` เมื่อเลือก Pokémon
- เปลี่ยนสีขอบและพื้นหลังแบบ smooth

### **3. Data Persistence**
- ทีมทั้งหมดถูกเก็บใน local storage
- โหลดข้อมูลทันทีเมื่อเปิดแอป

### **4. Search Functionality**
- ค้นหาแบบ real-time
- Filter ตาม name (case-insensitive)



## 📞 ติดต่อ

หากมีปัญหาหรือข้อเสนอแนะ กรุณาติดต่อทาง:
- Email: [mathat.2546@gmail.com]

---
**สร้างด้วย ❤️ โดยใช้ Flutter + GetX**