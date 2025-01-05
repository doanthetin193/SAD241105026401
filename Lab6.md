# **Create Initial Design Classes**

## **Mục tiêu**
Xác định danh sách các lớp cần thiết từ **Use Case** và mô tả trách nhiệm chính của chúng. Đây là bước khởi đầu quan trọng để định nghĩa cấu trúc cơ bản của hệ thống, đảm bảo các lớp được tạo ra đúng với yêu cầu của **Use Case**.

---

## **Các lớp cần thiết**

### **1. Timecard**
- **Trách nhiệm**: Quản lý thông tin về thẻ chấm công của nhân viên.
- **Vai trò**: Lưu trữ thông tin chi tiết và thực hiện các thao tác cơ bản liên quan đến timecard.

### **2. Employee**
- **Trách nhiệm**: Đại diện cho nhân viên trong hệ thống.
- **Vai trò**: Quản lý thông tin cá nhân của nhân viên và liên kết với các thẻ chấm công.

### **3. TimecardController**
- **Trách nhiệm**: Điều phối logic nghiệp vụ liên quan đến việc xử lý thẻ chấm công.
- **Vai trò**: Xử lý các yêu cầu từ giao diện người dùng hoặc các hệ thống khác và tương tác với lớp `Timecard` để thực hiện các hành động như lưu, cập nhật, hoặc truy vấn.

### **4. TimecardForm**
- **Trách nhiệm**: Giao diện giữa người dùng và hệ thống để quản lý thẻ chấm công.
- **Vai trò**: Cung cấp chức năng nhập thông tin thẻ chấm công từ người dùng.

### **5. ProjectManagementDatabase**
- **Trách nhiệm**: Tương tác với cơ sở dữ liệu quản lý dự án để lấy hoặc lưu thông tin liên quan đến mã charge (charge codes).
- **Vai trò**: Kết nối với cơ sở dữ liệu và cung cấp dữ liệu cần thiết cho các lớp khác như `TimecardController`.

---

## **Sơ đồ lớp (Class Diagram)**
https://www.planttext.com/plantuml/png/Z5FRIWD137tVhyXZ2_OFf1Is2WMLWeBFwKxOZivboMGBHVmo7_maVq5cTdPsKIg-9Jd9EISPvklZize4GPRUcagq68AQ2OLWvxHeDB2be5i7jS4GA5HL4mDuqfOQP0Ll5G20TW97ttDuzlnAAjM2i7OjT7ZU4si_5BSe56UXIIegvWauUQqWu8aMoodlEvNxezRYXyhLBubbzJuQlB6TyMUYR31tEhGqpobtxGPtTph8zIYt1ibHc6X7iFPEs1j3d0Nsx5-eaNjqs98b9riKF60WK3b8RULkBKdTCvEJijvoyl2OxArJrn6vfTeh2lFJn5ELoS8wEfuTOiHkFTliDH5er_L5EvgTioiTEeFdVmdiBsu-gDNUEMf4UvVMATcV-pxqza0S5WC03MiXrfXaYvdLQbtUkLHdBnFniNm9l-Y-3AJ3pQacXcf3JiMVymq00F__0m00
