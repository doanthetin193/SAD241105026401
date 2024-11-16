# Phân Tích Kiến Trúc

## 1. Thành phần kiến trúc được đề xuất

### 1.1. Presentation Layer (Tầng Giao Diện)

#### Mục đích:
- Cung cấp giao diện người dùng cho nhân viên và Quản Lý Lương.
- Hiển thị thông tin và nhận đầu vào từ người dùng (thẻ chấm công, đơn đặt hàng, báo cáo...).

#### Tính năng:
- Giao diện Windows-based, dễ sử dụng và trực quan.
- Đảm bảo khả năng tương tác tốt giữa người dùng và hệ thống.

---

### 1.2. Business Logic Layer (Tầng Xử Lý Nghiệp Vụ)

#### Mục đích:
- Thực hiện các quy trình nghiệp vụ của hệ thống (tính lương, xử lý hoa hồng, báo cáo...).
- Áp dụng các quy tắc nghiệp vụ như tính lương làm thêm giờ, tính hoa hồng theo doanh số, quản lý thời gian làm việc.

#### Tính năng:
- Chứa các quy tắc nghiệp vụ độc lập, dễ bảo trì và mở rộng.
- Xử lý logic thanh toán, đảm bảo tính chính xác và bảo mật.

---

### 1.3. Data Access Layer (Tầng Truy Cập Dữ Liệu)

#### Mục đích:
- Giao tiếp với cơ sở dữ liệu, bao gồm Cơ Sở Dữ Liệu Quản Lý Dự Án (DB2) và các cơ sở dữ liệu khác (nếu cần).
- Thực hiện các thao tác lưu trữ, truy vấn dữ liệu từ Project Management Database và thông tin nhân viên.

#### Tính năng:
- Tách biệt logic nghiệp vụ khỏi truy cập dữ liệu.
- Dễ dàng tích hợp với hệ thống cũ (DB2).

---

### 1.4. Database Layer (Tầng Cơ Sở Dữ Liệu)

#### Mục đích:
- Lưu trữ thông tin nhân viên, thẻ chấm công, đơn đặt hàng, bảng lương...
- Tích hợp với cơ sở dữ liệu cũ DB2 và hỗ trợ giao dịch ngân hàng.

#### Tính năng:
- Quản lý dữ liệu an toàn, hiệu quả.
- Tương thích với các hệ thống ngân hàng qua giao diện giao dịch điện tử.

---

### 1.5. System Integration Layer (Tầng Tích Hợp Hệ Thống)

#### Mục đích:
- Kết nối hệ thống với cơ sở dữ liệu DB2 và hệ thống ngân hàng.
- Tương tác với các API của ngân hàng để thực hiện giao dịch.

#### Tính năng:
- Đóng vai trò như một cầu nối giữa hệ thống Payroll và các hệ thống bên ngoài.
- Đảm bảo tính bảo mật và chuẩn hóa giao tiếp.

---

## 2. Lý do lựa chọn kiến trúc phân lớp

1. **Tính rõ ràng và dễ bảo trì:**
   - Mỗi tầng có trách nhiệm cụ thể, giúp dễ dàng tìm ra lỗi và bảo trì hệ thống.

2. **Khả năng mở rộng:**
   - Khi cần nâng cấp giao diện, thêm chức năng hoặc tích hợp thêm hệ thống mới, chỉ cần thay đổi tầng liên quan.

3. **Tích hợp dễ dàng:**
   - Tầng Data Access và System Integration hỗ trợ tương thích với hệ thống cũ (DB2) và các giao dịch ngân hàng.

4. **Tăng cường bảo mật:**
   - Logic bảo mật được xử lý trong tầng Business Logic và tầng Tích Hợp, ngăn nhân viên truy cập không đúng dữ liệu.

5. **Khả năng tái sử dụng:**
   - Các tầng như Data Access có thể tái sử dụng cho các hệ thống khác trong tương lai.

---

## 3. Ý nghĩa của từng thành phần trong kiến trúc

| **Thành Phần**            | **Ý Nghĩa**                                                                 |
|----------------------------|-----------------------------------------------------------------------------|
| **Presentation Layer**     | Đảm bảo trải nghiệm người dùng tốt nhất và cung cấp giao diện dễ dùng cho cả nhân viên và Quản Lý Lương. |
| **Business Logic Layer**   | Trái tim của hệ thống, xử lý tất cả nghiệp vụ chính và đảm bảo tính chính xác trong quy trình tính toán lương. |
| **Data Access Layer**      | Làm cầu nối giữa nghiệp vụ và cơ sở dữ liệu, giúp truy cập dữ liệu dễ dàng và an toàn. |
| **Database Layer**         | Lưu trữ dữ liệu quan trọng như thông tin nhân viên, lương, giao dịch, và thông tin dự án, đảm bảo hiệu quả và tính bảo mật cao. |
| **System Integration Layer** | Đảm bảo hệ thống hoạt động mượt mà với cơ sở dữ liệu cũ và hệ thống ngân hàng, hỗ trợ tương tác liền mạch và bảo mật với các hệ thống bên ngoài. |

---

## Biểu đồ package mô tả kiến trúc

![Biểu đồ package mô tả kiến trúc](https://www.planttext.com/api/plantuml/png/X9HDJiCm48NtEONL3QjkM5TLqnQXIaL450umEAFMr3_Hs46AK4_6WYDn1Toq9JPnYfHDvhtCV6C_vVlpQsOTaAkLp2hWUzWY6nNGa96IRHhhK8tOHyQOVpgTqA9su8JHR0qDqid369TWBRjJbJGDuiigAEQb4hgj7BAmsRosGgCthCrMy5IxCyu6wLrm38HdeP03bGKPxZiO2hI5KKfOwmaN87ajmKNo4rQ6t3rgfBCIKot10SivRy66DposiS8tQ19OIR6eYU_0uYELI94Z1ZYTFLjfXriQFEdb_3OleN8OxZO7lS-BLIVqLtlr1DVskdWIMoMaQAUKJkODkNi0xG6KJyulmcGYSGkycKulc3V-QcIxhzs9olfAboOs7a_xQJW7Aot6XTQJIat2DX2WXBEVfOGfcPWhTF_vXdFKdnG11FVJdnKX1Cw1QNsIy9i-T1JNxkNKPYWawLP_Gdx8PgZBur_i1m00__y30000)

---

# Đề xuất các cơ chế cần giải quyết trong bài toán và giải thích lý do

## 1. Cơ chế xử lý thời gian làm việc (Timecard Processing)

**Mục tiêu:**  
- Tính toán số giờ làm việc của nhân viên, bao gồm cả giờ làm thêm.

**Lý do:**  
- Đảm bảo xác định chính xác số giờ làm việc thực tế cho nhân viên tính lương theo giờ.  
- Đảm bảo công bằng khi trả thêm tiền cho giờ làm việc ngoài giờ.

**Cách triển khai:**  
- Sử dụng lớp `TimecardProcessor` để xử lý các bản ghi thời gian.  
- Logic bổ sung: Tính giờ làm thêm, chỉ tính 1,5 lần mức lương thông thường cho giờ làm ngoài 8 giờ.

---

## 2. Cơ chế tính toán hoa hồng (Commission Calculation)

**Mục tiêu:**  
- Tính hoa hồng cho nhân viên theo phần trăm doanh thu.

**Lý do:**  
- Đảm bảo tính chính xác lương dựa trên doanh số.  
- Tạo động lực tăng doanh thu.

**Cách triển khai:**  
- Lớp `CommissionCalculator` tính hoa hồng dựa trên các mức: 10%, 15%, 25%, 35%.  
- Sử dụng dữ liệu từ các đơn hàng (`PurchaseOrder`).

---

## 3. Cơ chế tạo báo cáo (Reporting)

**Mục tiêu:**  
- Hỗ trợ nhân viên kiểm tra thông tin về giờ làm, lương, nghỉ phép và các thông tin khác.

**Lý do:**  
- Đảm bảo minh bạch và rõ ràng trong quá trình quản lý.

**Cách triển khai:**  
- Sử dụng `ReportGenerator` để tạo báo cáo như:  
  - Tổng số giờ làm.  
  - Thu nhập từ đầu năm.  
  - Thời gian nghỉ phép còn lại.

---

## 4. Cơ chế bảo mật và quyền truy cập (Security and Access Control)

**Mục tiêu:**  
- Đảm bảo nhân viên chỉ có thể truy cập và thay đổi thông tin cá nhân của mình.

**Lý do:**  
- Ngăn chặn thay đổi trái phép, đặc biệt với bản ghi thời gian và đơn hàng.

**Cách triển khai:**  
- Lớp kiểm soát truy cập xác định quyền hạn:  
  - Chỉ Payroll Administrator được cập nhật thông tin nhân viên.

---

## 5. Cơ chế tích hợp với hệ thống cũ (Legacy System Integration)

**Mục tiêu:**  
- Kết nối hệ thống mới với cơ sở dữ liệu hiện tại (DB2).

**Lý do:**  
- Acme không muốn thay thế hệ thống cũ.  
- Tận dụng dữ liệu sẵn có.

**Cách triển khai:**  
- `DB2Adapter` quản lý dữ liệu từ DB2 mà không thay đổi hệ thống cũ.

---

## 6. Cơ chế chạy tự động cho tính lương định kỳ (Automated Payroll Execution)

**Mục tiêu:**  
- Tự động hóa quy trình tính lương vào các ngày cố định.

**Lý do:**  
- Giảm thiểu can thiệp thủ công.  
- Đảm bảo tính chính xác và đúng hạn.

**Cách triển khai:**  
- Sử dụng `System Clock` và lịch tác vụ tự động vào thứ Sáu và cuối tháng.  
- Hệ thống tổng hợp thông tin từ lần trả lương gần nhất.

---

## 7. Cơ chế lựa chọn phương thức thanh toán (Payment Method Selection)

**Mục tiêu:**  
- Nhân viên có thể lựa chọn cách nhận lương (văn phòng, bưu điện, chuyển khoản).

**Lý do:**  
- Đáp ứng nhu cầu linh hoạt của từng nhân viên.

**Cách triển khai:**  
- Lớp `PaymentMethod` lưu tùy chọn nhận lương.  
- `BankAPIAdapter` hỗ trợ giao dịch qua ngân hàng.

---

## 8. Cơ chế đảm bảo độ tin cậy (Reliability)

**Mục tiêu:**  
- Đảm bảo hệ thống hoạt động ổn định vào thời điểm tính lương.

**Lý do:**  
- Tránh gián đoạn hoạt động của công ty.

**Cách triển khai:**  
- Sử dụng cơ chế dự phòng, giám sát, và quản lý tài nguyên để đảm bảo hệ thống luôn sẵn sàng.

---

# Phân tích ca sử dụng Payment

## Giải thích về các lớp và mối quan hệ

### Employee
**Thuộc tính:**
- `id`: Mã nhân viên.
- `name`: Tên nhân viên.
- `paymentMethod`: Phương thức thanh toán (chuyển khoản, nhận tại văn phòng, gửi qua bưu điện).

**Phương thức:**
- `getTimecards()`: Trả về danh sách các Timecard của nhân viên.
- `getPaycheck()`: Trả về phiếu lương của nhân viên.

**Mối quan hệ:**
- Employee có thể có nhiều Timecard (n-1), vì một nhân viên có thể ghi nhiều giờ làm việc.
- Employee có thể nhận nhiều Paycheck (n-1), vì nhân viên nhận lương theo từng kỳ thanh toán.

---

### Timecard
**Thuộc tính:**
- `date`: Ngày làm việc.
- `hoursWorked`: Số giờ làm việc của nhân viên trong ngày.
- `chargeNumber`: Mã công việc mà nhân viên thực hiện.

**Mối quan hệ:**
- Mỗi Timecard thuộc về một Employee (n-1), vì mỗi nhân viên có thể có nhiều thời gian làm việc (Timecards).
- Mỗi Timecard được sử dụng trong việc tính toán lương của nhân viên.

---

### Paycheck
**Thuộc tính:**
- `amount`: Số tiền nhân viên nhận được sau khi tính toán.
- `paymentDate`: Ngày nhận lương.
- `paymentMethod`: Phương thức thanh toán.

**Phương thức:**
- `generatePaycheck()`: Tạo phiếu lương cho nhân viên sau khi đã tính toán xong số tiền.

**Mối quan hệ:**
- Paycheck được tạo ra từ PaymentProcessor (1-1), vì mỗi lần thanh toán là một Paycheck duy nhất.

---

### PaymentProcessor
**Phương thức:**
- `processPayment(employee: Employee, timecard: Timecard)`: Xử lý thanh toán cho một nhân viên dựa trên Timecard.
- `calculateAmount(employee: Employee, timecard: Timecard)`: Tính toán số tiền mà nhân viên sẽ nhận được dựa trên Timecard và loại nhân viên.

**Mối quan hệ:**
- PaymentProcessor tạo ra một Paycheck (1-1) cho nhân viên.
- PaymentProcessor tương tác với BankSystem để thực hiện giao dịch thanh toán (1-1).

---

### PayrollSystem
**Phương thức:**
- `runPayroll()`: Thực thi quy trình thanh toán, xác định ngày thanh toán.
- `validateChargeNumbers(chargeNumber: string)`: Xác thực mã công việc.
- `generatePayments()`: Tạo các phiếu lương cho nhân viên.

**Mối quan hệ:**
- PayrollSystem quản lý và xử lý thông tin nhân viên (1-n), xác thực các ChargeNumber từ ProjectManagementDatabase (1-n).
- PayrollSystem sử dụng PaymentProcessor để thực hiện thanh toán (1-n).

---

### BankSystem
**Thuộc tính:**
- `accountNumber`: Số tài khoản ngân hàng của nhân viên.
- `transactionID`: Mã giao dịch.

**Phương thức:**
- `processTransaction(amount: float, accountNumber: string)`: Xử lý giao dịch thanh toán cho nhân viên qua ngân hàng.

**Mối quan hệ:**
- BankSystem tương tác với PaymentProcessor để thực hiện giao dịch thanh toán (1-1).

---

### ProjectManagementDatabase
**Thuộc tính:**
- `projectCode`: Mã dự án.
- `chargeNumber`: Mã công việc (charge number).

**Mối quan hệ:**
- ProjectManagementDatabase cung cấp thông tin về các ChargeNumber và được sử dụng bởi PayrollSystem để xác thực mã công việc (1-n).

---

## Các mối quan hệ giữa các lớp
1. Employee có thể có nhiều Timecard và nhận nhiều Paycheck.
2. Timecard là dữ liệu cần thiết cho PaymentProcessor để tính toán và tạo Paycheck.
3. PaymentProcessor xử lý thanh toán cho nhân viên và giao tiếp với BankSystem để thực hiện các giao dịch.
4. PayrollSystem điều phối quy trình thanh toán, xác thực thông tin từ ProjectManagementDatabase về ChargeNumber và thực hiện thanh toán qua PaymentProcessor.

---

### Biểu đồ lớp phân tích
![Biểu đồ lớp](https://www.planttext.com/api/plantuml/png/Z5HDQnin4BtxLmYVN4WEkIx5k8rp22GXK4FFO-tKgrWVHffrCQM_h8V-fFw5IfQqAzcEsykYbMRclNblf3-_VYySWQLUoGcNu1nxK3jf3eZinuGn9jg62KrXgK5XmnnPeJVXVmS7XPgUaJhJbWSRf9LGoC6sRlQXOK_2qSUyCqyHht3W7V9j2CZhoSz98f6Z8uaMo2Cl_JVyTQQtxgknM_IetwI18plUWTtWIw_MQ4_8v8u2L5wFK1ayGe4olQQYRkfoML6uqhf6wuFAxlP6j1LSI7srXgDpnaRONVnDXpDCB4U-DuoI9CqWJgbSK00axwK7_tJiuV-Bn5vBXjP8-UNW25MaPtkTTeU6_EuUf0ZMt1VIkzab8tpIsXY9e4z42jswSv4-WzwM-C1vQEdSNRAW7N0IHZykg-6CWgx6yrbbxStbckTsMVE6d9v1mmRJ8C0Q70w-XUDxqrPNuyemrcBbsn53vW5tk7_JkocxlMLJFHtCyhNwjHBasFnYN1w7XbdaAFOO0ci_Y-Y7OK2IMjV3JoStF0nxiyr9zLJdlBkIL3R-NncZ_SV7n-Tmt_9tGLr8VDUHcklOH3DCgalEC1trz-KMgDlm-Fq5003__mC0)

---

# Phân tích ca sử dụng Maintain Timecard

## Nhiệm vụ của từng lớp phân tích

### Employee

- **Vai trò**: Gửi yêu cầu thêm hoặc cập nhật Timecard qua giao diện người dùng.
- **Phương thức liên quan**: Không có phương thức cụ thể, hoạt động như nguồn yêu cầu.

### Timecard

- **Thuộc tính**:
  - `date`: Ngày làm việc.
  - `hoursWorked`: Số giờ làm việc.
  - `chargeNumber`: Mã công việc liên kết với dự án.

- **Phương thức**:
  - `create(date, hoursWorked, chargeNumber)`: Tạo một Timecard mới.

### TimecardManager

- **Vai trò**: Lớp trung gian xử lý logic ứng dụng liên quan đến quản lý Timecard.
- **Phương thức**:
  - `addTimecard(date, hoursWorked, chargeNumber)`: Xử lý yêu cầu thêm Timecard mới.
  - `updateTimecard(id, date, hoursWorked, chargeNumber)`: Cập nhật Timecard hiện có.

- **Tương tác**:
  - Tương tác với `ProjectManagementDatabase` để xác thực mã công việc.
  - Tạo đối tượng `Timecard` nếu dữ liệu hợp lệ.

### PayrollSystem

- **Vai trò**: Lưu trữ Timecard vào hệ thống cơ sở dữ liệu trung tâm.
- **Phương thức**:
  - `saveTimecard(Timecard)`: Lưu thông tin Timecard.

### ProjectManagementDatabase

- **Vai trò**: Xác thực mã công việc hợp lệ.
- **Phương thức**:
  - `validateChargeNumber(chargeNumber)`: Trả về giá trị hợp lệ hoặc không hợp lệ.

---

## Giải thích các lớp và mối quan hệ

### Employee

- **Đại diện** cho người sử dụng hệ thống. Một nhân viên có thể gửi nhiều Timecard.

### Timecard

- Chứa thông tin chi tiết về ngày làm việc, số giờ và mã công việc. Một Timecard chỉ thuộc về một nhân viên duy nhất.

### TimecardManager

- Điều phối tất cả các hành động liên quan đến Timecard, từ tạo mới, cập nhật đến xóa. Đây là lớp trung gian quan trọng kết nối với các hệ thống khác.

### PayrollSystem

- Hệ thống nhận và lưu trữ Timecard từ TimecardManager vào cơ sở dữ liệu chính. Một Timecard duy nhất được xử lý mỗi lần.

### ProjectManagementDatabase

- Đảm bảo mã công việc trong Timecard hợp lệ. Một Timecard phải được xác thực trước khi được lưu trữ.

---

## Biểu đồ lớp

![Biểu đồ lớp Payment](https://www.planttext.com/api/plantuml/png/h9FDJiCm3CVlVGghfo5r1wuze4d0aGa9f9tTndHX-PYSj58ryMGSU2HUWQHVczW6brwIE8b__jjnlZ-_LiuZ-rghf5Je73pglR8j4HmI090Y1sbyN1hKb8FpB4qLRLSNMlfNgQb45Wk1FXm_X363hQtPRIplABY_AOi-WtABND6wrWNnYBd9eR5I91_947oazS6Fo6YTG-Fk9MotpnJyvbNrX0OhubuS2Z5BxW5LxoDWeWqrps0MyS_OibNgfNMUT2_TONECDYxE7Tc-K-dxf3KP7uHWWMxeZ0QLZ0BlJqGihYWgh5M49hAdzaflKrWk8JNfLDzyw2a7Tydlcb-yhhl3lww7wMeU-PJ3VuJJ4iQtQUokyrcH4V7d_0000F__0m00)

---

# Các lớp phân tích hợp nhất

Từ kết quả phân tích, các lớp phân tích hợp nhất bao gồm:

## Employee

Đại diện nhân viên, người tạo Timecard và nhận Payment.

**Thuộc tính:**

- `id`: Định danh nhân viên.
- `name`: Tên nhân viên.
- `paymentMethod`: Phương thức thanh toán (Direct Deposit, Pickup, Mail).

**Phương thức:**

- `submitTimecard(date, hoursWorked, chargeNumber)`: Gửi yêu cầu tạo hoặc cập nhật Timecard.
- `requestPayment()`: Gửi yêu cầu thanh toán.

## Timecard

Lưu thông tin chi tiết thời gian làm việc.

**Thuộc tính:**

- `date`: Ngày làm việc.
- `hoursWorked`: Số giờ làm việc.
- `chargeNumber`: Mã công việc.

**Phương thức:**

- `create(date, hoursWorked, chargeNumber)`: Tạo Timecard mới.

## TimecardManager

Quản lý logic liên quan đến Timecard.

**Phương thức:**

- `addTimecard(date, hoursWorked, chargeNumber)`: Thêm Timecard mới.
- `validateChargeNumber(chargeNumber)`: Kiểm tra tính hợp lệ của mã công việc.

## PayrollSystem

Xử lý logic thanh toán và lưu trữ thông tin Timecard.

**Phương thức:**

- `processPayment(employeeId)`: Xử lý thanh toán cho nhân viên.
- `saveTimecard(Timecard)`: Lưu thông tin Timecard vào hệ thống.

## Payment

Lưu thông tin thanh toán của nhân viên.

**Thuộc tính:**

- `amount`: Số tiền thanh toán.
- `payPeriod`: Chu kỳ thanh toán.
- `employeeId`: Nhân viên nhận thanh toán.

## ProjectManagementDatabase

Xác thực mã công việc cho Timecard.

**Phương thức:**

- `validateChargeNumber(chargeNumber)`: Kiểm tra tính hợp lệ của mã công việc.

## BankSystem

Hệ thống ngân hàng để xử lý thanh toán.

**Phương thức:**

- `processDirectDeposit(accountDetails, amount)`: Xử lý giao dịch thanh toán qua Direct Deposit.

---

# Mối quan hệ giữa các lớp

## Employee:

- Tương tác với TimecardManager để thêm mới hoặc cập nhật Timecard.
- Nhận Payment từ PayrollSystem.

## TimecardManager:

- Xử lý logic liên quan đến Timecard và xác thực mã công việc với ProjectManagementDatabase.
- Chuyển dữ liệu Timecard hợp lệ đến PayrollSystem.

## PayrollSystem:

- Lưu trữ Timecard từ TimecardManager.
- Tạo và gửi thanh toán qua BankSystem hoặc các phương thức khác.

## BankSystem:

- Xử lý giao dịch thanh toán trực tiếp (Direct Deposit).

---

# Giải thích các mối quan hệ

- **Employee → Timecard**: Một nhân viên có thể tạo nhiều Timecard, mỗi Timecard đại diện cho một ngày làm việc.
- **TimecardManager → ProjectManagementDatabase**: TimecardManager sử dụng ProjectManagementDatabase để xác thực mã công việc, đảm bảo tính hợp lệ.
- **TimecardManager → PayrollSystem**: TimecardManager gửi các Timecard hợp lệ đến PayrollSystem để lưu trữ và xử lý.
- **PayrollSystem → Payment**: PayrollSystem tạo các bản ghi Payment dựa trên Timecard và các thông tin liên quan đến nhân viên.
- **PayrollSystem → BankSystem**: PayrollSystem chuyển tiếp thông tin thanh toán đến BankSystem để xử lý giao dịch Direct Deposit.

![Biểu đồ hợp nhất](https://www.planttext.com/api/plantuml/png/h5GzJyCm4DtpAwnCGIe3QmPKGHWOYYg1n7n9ZjJK7-7iLAeGluo1dyHVm6wSD6bJ6CeIn_RTUtVlNlBz-JKt5iWsKaI506FOdQo5tYAozuWnnikKSMNzgmA9AJEMkAhyleQjH6KNQ5Uw75wO9fVSFd691L2Pb61TNkQUCxRI3PbdJMjq6Iz2WvsnOWLKuKCZSwGEvY9b6yrBZqRurg2novOjwMu-eb1lnzFMkoVpksCwVpf5k3idT7bdrNjKrG8KL4XjSL2M_wNA1WJt4BU3iEH4JgwrG53xufoMf8Lut1gBiYsj9bsWCPtA64nmtuv_G6nWWtqJtSjH-m4dj2rre-nW0CuvIoG-Tiq1vG2Bz2iMjbNIephH80SJ77gM4ZUWrXCoP9mSOuQrDjmcK1I-WGmjS64wkDcuhp5w_n75Lp6xl6InYdjBfC5eXbr7XpQP39Uxoz_2tN9IfRHNw2-4eIjSbwXAdp4sow30CEEKLQYG0lvqj5lsIk_6YrMNCNSy_k_p0m00__y30000)

