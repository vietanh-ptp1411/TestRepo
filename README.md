# BÀI GIẢNG: TỔNG QUAN & SETUP MÔI TRƯỜNG

**BUỔI 1: GIỚI THIỆU MACHINE VISION & COGNEX VISIONPRO**  
**Khóa học: Lập trình VisionPro từ cơ bản đến nâng cao**

---

## MỤC LỤC

1. [Giới thiệu Machine Vision](#1-giới-thiệu-machine-vision)
2. [Các thành phần hệ thống Vision](#2-các-thành-phần-hệ-thống-vision)
3. [Giới thiệu Cognex VisionPro](#3-giới-thiệu-cognex-visionpro)
4. [Cài đặt & Làm quen giao diện](#4-cài-đặt--làm-quen-giao-diện)
5. [Kết nối Camera & Chụp ảnh](#5-kết-nối-camera--chụp-ảnh)
6. [Bài tập thực hành](#6-bài-tập-thực-hành)

---

## 1. GIỚI THIỆU MACHINE VISION

### 1.1 Machine Vision là gì?

**Machine Vision** = Công nghệ cho phép máy tính "nhìn" và xử lý hình ảnh

**Ứng dụng chính:**
- ✅ Kiểm tra chất lượng (Quality Control)
- ✅ Định vị sản phẩm (Localization)
- ✅ Đo lường kích thước (Measurement)
- ✅ Đọc ký tự/mã vạch (OCR/Barcode)
- ✅ Phát hiện lỗi (Defect Detection)

### 1.2 Quy trình Vision cơ bản

```
TRIGGER → LIGHTING → CAPTURE → PROCESS → DECISION → OUTPUT
(Sensor)   (LED)     (Camera)  (Software)  (OK/NG)    (I/O)
```

### 1.3 Lợi ích

| Lợi ích | So với con người |
|---------|------------------|
| **Tốc độ** | 600 sản phẩm/phút vs 50 sản phẩm/phút |
| **Độ chính xác** | ±0.01mm, không mỏi |
| **Khách quan** | Tiêu chuẩn thống nhất |
| **24/7** | Không nghỉ, không ốm |

---

## 2. CÁC THÀNH PHẦN HỆ THỐNG VISION

### 2.1 Sơ đồ tổng quan

```
┌─────────┐  Trigger   ┌──────────────┐
│   PLC   │ ────────→  │   VISION     │
└─────────┘            │  CONTROLLER  │
                       │  (PC + SW)   │
                       └──┬───────┬───┘
                          │       │
                    Camera│       │Light
                          ↓       ↓
                    ┌─────────┬──────────┐
                    │ CAMERA  │ LIGHTING │
                    │ + LENS  │   (LED)  │
                    └────┬────┴────┬─────┘
                         │         │
                         └────┬────┘
                              ↓
                         [PRODUCT]
```

### 2.2 CAMERA

**Loại Camera phổ biến:**
- **Area Scan:** Chụp toàn bộ (90% ứng dụng)
- **Line Scan:** Tốc độ cao, web inspection

**Thông số quan trọng:**

| Thông số | Ví dụ | Ghi chú |
|----------|-------|---------|
| Resolution | 1280x1024, 2MP, 5MP | Tùy độ chính xác cần |
| Frame Rate | 30-200 fps | Tùy tốc độ sản xuất |
| Interface | GigE, USB3 | GigE phổ biến nhất |
| Sensor | CCD, CMOS | CMOS hiện đại hơn |

### 2.3 LENS

**Thông số chính:**

| Thông số | Ý nghĩa | Ví dụ |
|----------|---------|-------|
| Focal Length | Độ dài tiêu cự | 16mm, 25mm, 35mm |
| Working Distance | Khoảng cách đến sản phẩm | 200-500mm |
| F-number | Khẩu độ (DOF) | F/8, F/11, F/16 |

**Công thức FOV (Field of View):**

```
FOV = (Sensor Size × Working Distance) / Focal Length
```

### 2.4 LIGHTING

**"Lighting is 90% of Vision success"**

**Các loại Lighting:**

| Loại | Ứng dụng |
|------|----------|
| **Back Light** | Đo silhouette, kích thước |
| **Ring Light** | Đa năng, phổ biến |
| **Dome Light** | Bề mặt cong, phản quang |
| **Dark Field** | Phát hiện vết xước |
| **Coaxial** | Bề mặt phẳng, laser marking |

**Màu sắc:**
- **White:** Đa năng
- **Red:** Contrast cao, đọc ký tự
- **Blue:** Chi tiết tốt
- **IR:** Xuyên qua plastic

### 2.5 VISION CONTROLLER

**Yêu cầu PC:**

| Linh kiện | Tối thiểu | Khuyến nghị |
|-----------|-----------|-------------|
| CPU | Intel i5 gen 8 | Intel i7 gen 10+ |
| RAM | 8GB | 16GB+ |
| Storage | 256GB SSD | 512GB SSD |
| Network | GigE | Dual GigE |
| OS | Windows 10 Pro 64-bit | Windows 10/11 Pro |

### 2.6 I/O & COMMUNICATION

**Digital I/O:**
- Input: Nhận trigger từ PLC
- Output: Gửi OK/NG cho PLC

**Ethernet:**
- Ethernet/IP, PROFINET, Modbus TCP
- Truyền data lớn, tốc độ cao

---

## 3. GIỚI THIỆU COGNEX VISIONPRO

### 3.1 Cognex Corporation

- Công ty #1 thế giới về Machine Vision
- Thành lập: 1981 (USA)
- Market share: >50%

### 3.2 VisionPro là gì?

**Phần mềm xử lý ảnh công nghiệp của Cognex**

**Đặc điểm:**
- ✅ 50+ tools (Localization, Measurement, Inspection, OCR)
- ✅ Sub-pixel accuracy
- ✅ QuickBuild GUI (không cần code)
- ✅ Lập trình .NET (C#, VB)
- ✅ Hỗ trợ nhiều loại camera

**Tools chính:**

| Category | Tools | Ứng dụng |
|----------|-------|----------|
| **Localization** | PMAlign, PatMax | Tìm vị trí pattern |
| **Measurement** | Caliper, Blob | Đo kích thước |
| **Inspection** | Flaw Detection | Kiểm tra lỗi |
| **Identification** | OCRMax, ID | Đọc ký tự, barcode |

### 3.3 Cấu trúc Project

```
VisionPro Project (.vpp)
│
├── Job
│   ├── ToolBlock (Main logic)
│   │   ├── Acquisition Tool (Lấy ảnh)
│   │   ├── Vision Tools (PMAlign, Caliper...)
│   │   └── Logic Tools (If, Script, Output)
│   └── HMI (QuickBuild interface)
│
└── Settings (Calibration, Fixtures...)
```

---

## 4. CÀI ĐẶT & LÀM QUEN GIAO DIỆN

### 4.1 Cài đặt VisionPro

**Bước 1: Download**
```
https://support.cognex.com
→ Downloads → VisionPro
→ Download version mới nhất (VD: 10.2)
```

**Bước 2: Setup**
```
1. Run file .exe
2. Accept License
3. Chọn:
   ☑ VisionPro Runtime
   ☑ QuickBuild
   ☑ .NET Framework 4.8
4. Install → Reboot
```

**Bước 3: Activate**
```
Help → License Manager
→ Nhập License Key (hoặc Trial 30 ngày)
```

### 4.2 Giao diện QuickBuild

```
┌──────────────────────────────────────────────┐
│  File  Edit  Tools  Job  Run  Help           │ Menu Bar
├────┬─────────────────────────────────────────┤
│Tool│         WORKSPACE                        │
│Box │      (ToolBlock Editor)                  │
│    │                                          │
│▪Acq│                                          │
│▪PM │                                          │
│▪Cal│                                          │
├────┼──────────────────────────────────────────┤
│Prop│         DISPLAY                          │
│    │      (Image Viewer)                      │
└────┴──────────────────────────────────────────┘
```

**Các vùng chính:**
1. **Tool Box:** Danh sách tools
2. **Workspace:** Kéo thả tools
3. **Properties:** Thiết lập parameters
4. **Display:** Hiển thị ảnh

### 4.3 Tạo Project đầu tiên

**Bước 1: New Job**
```
File → New Job → Empty Job → OK
```

**Bước 2: Save Job**
```
File → Save Job As...
→ Tên: Buoi1_HelloVision.vpp
→ Save
```

**Bước 3: Thêm Tool**
```
Cách 1: Drag & Drop từ Tool Box
Cách 2: Right-click Workspace → Add Tool
```

---

## 5. KẾT NỐI CAMERA & CHỤP ẢNH

### 5.1 Kết nối Camera

**A. Camera thật (GigE/USB)**

```
Bước 1: Cắm camera vào PC
Bước 2: Cài Driver camera
Bước 3: QuickBuild → Add Tool → Acquisition Tool
Bước 4: Properties → Device:
        - Chọn camera từ dropdown
        - Configure (nếu cần)
```

**B. Camera Simulator (không có camera thật)**

```
Option 1: Image File Tool
- Add Tool → Image File
- Properties → Load Image File
- Browse ảnh .bmp/.jpg

Option 2: Webcam
- Add Tool → Acquisition Tool
- Device: DirectShow Camera
- Chọn webcam
```

### 5.2 Thiết lập Camera Parameters

**A. Exposure Time**

```
Properties → Exposure Time

Ý nghĩa: Thời gian cảm biến nhận sáng
- Ngắn (0.1-2ms): Sản phẩm chuyển động nhanh
- Dài (5-20ms): Sản phẩm tĩnh, cần nhiều sáng

Kinh nghiệm:
✓ Object di chuyển 1m/s → Exposure < 1ms
✓ Object tĩnh → 5-10ms
```

**B. Gain**

```
Properties → Gain

Ý nghĩa: Khuếch đại tín hiệu
- Thấp (0-50): Ảnh sáng đủ, ít noise
- Cao (100-200): Ảnh tối, cần tăng gain

⚠️ Gain cao → Nhiễu tăng
💡 Ưu tiên tăng lighting thay vì gain
```

**C. Trigger Mode**

```
Properties → Trigger Mode

ContinuousMode: Chụp liên tục (setup, debug)
ExternalTrigger: Chụp khi có tín hiệu (production)
SoftwareTrigger: Chụp khi code gọi
```

### 5.3 Chụp ảnh đầu tiên

**Bước 1: Setup Acquisition Tool**
```
1. Add Acquisition Tool vào ToolBlock
2. Properties:
   - Device: Chọn camera
   - Exposure: 10ms (thử nghiệm)
   - Gain: 0 (nếu đủ sáng)
   - Trigger: ContinuousMode
```

**Bước 2: Run**
```
1. Click Run button (▶) trên toolbar
2. Ảnh hiển thị trong Display
3. Check chất lượng ảnh:
   ✓ Sáng đủ (không quá tối/sáng)
   ✓ Nét (không mờ)
   ✓ Object trong FOV
```

**Bước 3: Save Image**
```
Right-click Display → Save Image
→ Chọn format: .bmp (không nén)
→ Save vào thư mục project
```

### 5.4 Xác định ROI (Region of Interest)

**ROI là gì?**
- Vùng quan tâm cần xử lý
- Giảm thời gian xử lý
- Loại bỏ vùng không cần thiết

**Cách tạo ROI:**

```
Bước 1: Add CogRectangle Tool
- Tool Box → CogRectangle
- Drag vào Workspace

Bước 2: Setup ROI
- Click Display
- Dùng chuột vẽ rectangle quanh sản phẩm
- Điều chỉnh size, position

Bước 3: Use ROI cho các tools sau
- Các tools khác sẽ chỉ xử lý trong ROI
```

**Ví dụ ROI:**

```
┌────────────────────────┐
│ Background (bỏ qua)    │
│                        │
│    ┌──────────┐        │ ← Toàn bộ ảnh
│    │ PRODUCT  │←ROI    │
│    │   (IC)   │        │
│    └──────────┘        │
│                        │
└────────────────────────┘
```

---

## 6. BÀI TẬP THỰC HÀNH

### BÀI TẬP 1: CHỤP VÀ LƯU ẢNH

**Mục tiêu:** Làm quen với Acquisition Tool

**Các bước:**

```
1. Tạo Job mới: "BT1_CaptureImage"

2. Thêm Acquisition Tool
   - Device: Camera/Webcam/Image File
   - Exposure: 10ms
   - Trigger: ContinuousMode

3. Run và observe ảnh

4. Điều chỉnh:
   - Exposure: Test 5ms, 15ms, 20ms
   - Gain: Test 0, 50, 100 (nếu cần)

5. Chọn ảnh đẹp nhất, Save:
   - Right-click Display → Save Image
   - Tên: sample01.bmp

6. Save Job
```

**Kết quả mong đợi:**
- Có 1 file ảnh .bmp chất lượng tốt
- Hiểu cách điều chỉnh Exposure/Gain

---

### BÀI TẬP 2: TẠO ROI CHO SẢN PHẨM

**Mục tiêu:** Xác định vùng ROI trên ảnh

**Các bước:**

```
1. Mở Job: "BT1_CaptureImage"

2. Thêm Image Display Tool
   - Tool Box → Display → CogDisplay
   - Kéo vào Workspace

3. Tạo ROI Rectangle:
   - Click Display
   - Graphics → Add Rectangle
   - Vẽ rectangle quanh sản phẩm

4. Note tọa độ ROI:
   - CenterX: ___
   - CenterY: ___
   - Width: ___
   - Height: ___

5. Save Job
```

**Kết quả mong đợi:**
- Rectangle bao quanh sản phẩm
- Biết tọa độ và size ROI

---

### BÀI TẬP 3: SETUP NHIỀU CAMERA SETTINGS

**Mục tiêu:** Thử nghiệm với các settings khác nhau

**Test Cases:**

| Test | Exposure | Gain | Mục đích |
|------|----------|------|----------|
| #1 | 1ms | 0 | Sản phẩm nhanh |
| #2 | 5ms | 0 | Cân bằng |
| #3 | 10ms | 0 | Sản phẩm chậm |
| #4 | 5ms | 50 | Lighting yếu |
| #5 | 5ms | 100 | Lighting rất yếu |

**Các bước:**

```
1. Với mỗi test case:
   - Thay đổi Exposure, Gain
   - Run
   - Observe ảnh
   - Save ảnh: testXX.bmp

2. So sánh các ảnh:
   - Ảnh nào sáng nhất?
   - Ảnh nào nét nhất?
   - Ảnh nào có noise nhiều nhất?

3. Chọn setting tốt nhất cho sản phẩm
```

**Kết quả mong đợi:**
- Hiểu ảnh hưởng của Exposure/Gain
- Chọn được setting tối ưu

---

### BÀI TẬP 4: TẠO PROJECT HOÀN CHỈNH

**Mục tiêu:** Tạo project cơ bản với đầy đủ bước

**Yêu cầu:**

```
Project Name: "ProductInspection_Basic"

Structure:
└── ToolBlock: Main
    ├── Acquisition Tool (Lấy ảnh)
    ├── ROI Definition (Xác định vùng)
    └── Display Tool (Hiển thị kết quả)
```

**Các bước:**

```
1. New Job: "ProductInspection_Basic"

2. Add Acquisition Tool
   - Setup camera
   - Test và chọn exposure/gain tối ưu

3. Define ROI
   - Vẽ rectangle quanh sản phẩm
   - Note tọa độ

4. Add Display Tool
   - Hiển thị ảnh + ROI

5. Test:
   - Run nhiều lần
   - Verify ảnh ổn định

6. Save Project + Documentation
   - Save .vpp file
   - Tạo file note.txt ghi:
     * Camera settings
     * ROI coordinates
     * Exposure/Gain values
```

**Kết quả mong đợi:**
- Project chạy ổn định
- Có documentation đầy đủ

---

## TÓM TẮT BUỔI 1

### Key Takeaways

**5 điều quan trọng nhất:**

1. **Machine Vision = Camera + Lighting + Software**
   - Cần đầy đủ 3 yếu tố

2. **Lighting quyết định 90% thành công**
   - Đầu tư thời gian cho lighting

3. **VisionPro = Tools + ToolBlock**
   - Drag & drop tools, không cần code

4. **Exposure & Gain cần cân bằng**
   - Ưu tiên lighting thay vì tăng gain

5. **ROI giúp tăng tốc độ**
   - Chỉ xử lý vùng cần thiết

### Checklist hoàn thành Buổi 1

```
☐ Hiểu nguyên lý Machine Vision
☐ Biết các thành phần hệ thống (Camera, Lens, Lighting, PC)
☐ Cài đặt VisionPro thành công
☐ Tạo được Job mới trong QuickBuild
☐ Kết nối camera và chụp ảnh
☐ Điều chỉnh Exposure/Gain
☐ Xác định ROI cho sản phẩm
☐ Save ảnh và project
```

### Chuẩn bị cho Buổi 2

**Buổi 2 sẽ học:**
- Blob Tool (đếm, đo diện tích)
- Histogram Tool
- Image Processing (Filter, Threshold)

**Chuẩn bị:**
- Chụp sẵn 5-10 ảnh mẫu chất lượng tốt
- Có sản phẩm với edges rõ ràng
- Lighting ổn định

---

**HẾT BÀI GIẢNG BUỔI 1**

© 2024 - Khóa học VisionPro - Buổi 1
