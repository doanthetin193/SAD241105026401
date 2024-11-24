# Phân tích các ca sử dụng còn lại

# 1. Process Payroll (Xử lý lương)

![Process Payroll](https://www.planttext.com/api/plantuml/png/T5FBJiCm4BpdA_O8X_v03gWl97geL54apekpRQFw4UmDKeJuCWvy4h-0dJXEaz8SyjZnx7XsdD_ldxbZj5mhcGc9pi4E6skaN1dDuKaMFZFmrmn8LT8qH6japE4nVaMGIqK2RT61B_4hWXKsuaJYd8VkxLiB00YKefR855NlxdFuC6NHmvOwhEK4SCAlh17adAygqfpONraqqs_ooiEco67FjjJ726XKD2bLNTSjyScCbmCSYVlU6tqmryhz19BooTJMlHfx9j-hr3o8xCYM_may3OpGl-UqsAwd1IGIatO_fAIDojIQSpX8Wpnsv_FoliDz6icY9ON-0oreQxAJKCREbwZF-yOngQJ_vaiB8RfDZ6nE0Xnjr7TU6YC9TMX-VIvdiuSXu1oUwRqcnnUXXsHky58y5xnK2sVu1Y-DDeTLUpY7QMS92milfk0jaoxQXS4ah8cnb2wR-shux_u0003__mC0)

## Giải thích về biểu đồ lớp

Các lớp phân tích trong hệ thống Payroll:

### PayrollController:

- **Thuộc tính:**
  - `employeeData`: Dữ liệu về nhân viên, bao gồm các thông tin cá nhân và phương thức thanh toán.
  - `timecardData`: Dữ liệu về số giờ làm việc của nhân viên trong mỗi kỳ lương.
  - `paycheck`: Đối tượng phiếu lương (Paycheck), sẽ được tạo ra sau khi tính toán lương.

- **Phương thức:**
  - `calculatePayroll()`: Tính toán tổng số tiền lương cho nhân viên dựa trên giờ làm việc, lương cơ bản, và các khoản phụ cấp.
  - `createPaycheck()`: Tạo phiếu lương (Paycheck) cho nhân viên.
  - `processPayment()`: Xử lý thanh toán cho nhân viên qua hệ thống ngân hàng.

### Employee:

- **Thuộc tính:**
  - `employeeId`: ID của nhân viên (dùng để nhận diện nhân viên trong hệ thống).
  - `name`: Tên nhân viên.
  - `paymentMethod`: Phương thức thanh toán của nhân viên (chuyển khoản, tiền mặt, v.v.).

- **Phương thức:**
  - `getEmployeeInfo()`: Trả về các thông tin cơ bản của nhân viên.

### Timecard:

- **Thuộc tính:**
  - `hoursWorked`: Số giờ làm việc của nhân viên trong một kỳ lương.
  - `payPeriod`: Kỳ lương (tuần, tháng, v.v.).

- **Phương thức:**
  - `getHoursWorked()`: Trả về số giờ làm việc của nhân viên trong kỳ lương.
  - `getPayPeriod()`: Trả về kỳ lương của nhân viên (tuần, tháng, v.v.).

### Paycheck:

- **Thuộc tính:**
  - `amount`: Số tiền lương mà nhân viên sẽ nhận.
  - `paymentDate`: Ngày thanh toán.

- **Phương thức:**
  - `calculateAmount()`: Tính toán số tiền lương (bao gồm các khoản phụ cấp, trừ thuế, trừ bảo hiểm, v.v.).
  - `generatePaycheck()`: Tạo ra phiếu lương cho nhân viên.

### BankSystem:

- **Thuộc tính:**
  - `bankAccount`: Số tài khoản ngân hàng của nhân viên.

- **Phương thức:**
  - `processPayment(amount: float)`: Xử lý thanh toán cho nhân viên qua hệ thống ngân hàng.

### 3. Quan hệ giữa các lớp:
- `PayrollController --> Employee`: PayrollController yêu cầu Employee cung cấp thông tin nhân viên (ID, tên và phương thức thanh toán).
- `PayrollController --> Timecard`: PayrollController yêu cầu Timecard cung cấp thông tin về số giờ làm việc và kỳ lương của nhân viên.
- `PayrollController --> Paycheck`: Sau khi tính toán lương, PayrollController tạo ra một đối tượng Paycheck với số tiền đã tính và ngày thanh toán.
- `Paycheck --> BankSystem`: Sau khi tạo phiếu lương, Paycheck gửi thông tin thanh toán (số tiền và thông tin tài khoản ngân hàng) cho BankSystem để xử lý thanh toán.

---

# 2. Generate Reports

![Generate Reports](https://www.planttext.com/api/plantuml/png/Z5DBReCm4Dtd5BCCKha0YofIFsfsKLEfQpSCAQgngJr4GbLFraMFr2iKExOnXgfXWV2RcJTldeUVh--D9gQeQ_Zgm9dMy8YjL7GZ1Id9EIhuMC7mvA1iu9OHAroI-Pu4d_eM2zYJgiNH1W2EA50nmdF5EYlW9ElI1SjQjvprIUnpDP5YkWGHLko036tCsw4eoXb6aXX_a9tIprAzOLb0nIMZEBfZVOmQiJJsN2UzhgPjifaBux3xhccOYkPobeJ9xfgMonunp8KEs9OJ_t8Gh9bRIhv-Aogvn3zCPcxlV_e_VN0CreZCHmE_WL-OnakM0w12EhnwoPxHd-ESfAaxchQphSppwtW_2hWt17YMjfmUJ3SItplK55s4SNAvp7iPLNaeAh8gJ7gm9f4Ky4JAJibJNM8gPP8-IWZP7hBScs4ppH_y2m00__y30000)

## Giải thích về biểu đồ lớp

Các lớp phân tích trong hệ thống Generate Reports:

### ReportController:

- **Thuộc tính:**
  - `reportData`: Dữ liệu báo cáo (ReportData), chứa thông tin cần thiết để tạo báo cáo.
  - `reportType`: Loại báo cáo (ví dụ: báo cáo tổng hợp, báo cáo chi tiết).

- **Phương thức:**
  - `generateReport()`: Tạo báo cáo dựa trên dữ liệu từ các lớp khác (nhân viên, lương, thời gian làm việc).
  - `displayReport()`: Hiển thị báo cáo cho người dùng.

### ReportData:

- **Thuộc tính:**
  - `startDate`: Ngày bắt đầu của phạm vi báo cáo.
  - `endDate`: Ngày kết thúc của phạm vi báo cáo.
  - `totalHoursWorked`: Tổng số giờ làm việc của tất cả nhân viên trong phạm vi thời gian.
  - `totalPay`: Tổng số tiền đã thanh toán cho tất cả nhân viên trong phạm vi thời gian.

- **Phương thức:**
  - `getReportData(startDate: Date, endDate: Date)`: Lấy dữ liệu báo cáo cho một phạm vi thời gian cụ thể.
  - `generateSummaryReport()`: Tạo báo cáo tổng hợp cho phạm vi thời gian đã chỉ định.

### Employee:

- **Thuộc tính:**
  - `employeeId`: ID của nhân viên.
  - `name`: Tên nhân viên.

- **Phương thức:**
  - `getEmployeeInfo()`: Trả về thông tin của nhân viên (như tên, mã số, v.v.).

### Payroll:

- **Thuộc tính:**
  - `employeeId`: ID của nhân viên.
  - `totalPay`: Tổng số tiền đã trả cho nhân viên.

- **Phương thức:**
  - `getPayrollData()`: Lấy dữ liệu về lương của nhân viên trong phạm vi thời gian đã chỉ định.

### Database:

- **Thuộc tính:**
  - `reportData`: Dữ liệu báo cáo được lưu trữ trong hệ thống cơ sở dữ liệu.

- **Phương thức:**
  - `fetchEmployeeData()`: Lấy thông tin nhân viên từ cơ sở dữ liệu.
  - `fetchPayrollData()`: Lấy dữ liệu lương từ cơ sở dữ liệu.

### 3. Quan hệ giữa các lớp:
- `ReportController --> ReportData`: ReportController yêu cầu ReportData lấy dữ liệu báo cáo cho phạm vi thời gian được chỉ định.
- `ReportController --> Employee`: ReportController yêu cầu Employee cung cấp thông tin chi tiết về nhân viên (như tên, ID).
- `ReportController --> Payroll`: ReportController yêu cầu Payroll cung cấp thông tin lương của nhân viên.
- `ReportData --> Database`: ReportData yêu cầu Database lấy dữ liệu từ cơ sở dữ liệu, bao gồm thông tin nhân viên và dữ liệu lương.
- `Database --> Employee`: Database cung cấp thông tin chi tiết về nhân viên.
- `Database --> Payroll`: Database cung cấp dữ liệu lương cho nhân viên.


---

# 3. Payment Processing

![Payment Processing Diagram](https://www.planttext.com/api/plantuml/png/V5J1JeD04Btp5NFK0p_0mJHgOeonCTP-m1IcTUEoYpj33J5-cGS_oL-GBHHsePO3oVBUC6_UFFZz_bcme9Ewr4ckaHcUi2d9o8qrugpMvE0pWVPAeUgGMnJCZZH_YE6LeDISmKgSChi31g2C4eL2VTN5PGPxgueUhPpDYVaqM5V5MDYzV61y9R5ehsQGYwMjZMImrHObrlX8ycgBI6CAuj0mvgAikPzYu-YKWR_tudOanzOagFH1sjGQW3rg5KpX4K_SMAi9pMoCkvRwWSqmoQuxhvsUoC9AFL3p_nodLmN0P8h-wJEzryGIokauZd9IUnfeN5d3v7bzjq7rozXma7pEJ9udP7Iui_6KwDRheDEOX2XeNLe2Nh2NE3BNQDvM3GkLOsBot4TcMPSRSXDzcvQ-n98c_URHZLtChTagLvx0Mo7pJorDhw8iPx1culF4OrhESeDfOzwXZMU4MspjTtQl2c8eFBwrBfbqcvUi3zPpkFf-rKb8dAdf4yX7hz3JaaKRKVzJ-WC00F__0m00)

## Giải thích các lớp và mối quan hệ

### PaymentController
Là lớp chính xử lý yêu cầu thanh toán. Nó sử dụng các lớp khác như `PaymentData`, `PaymentGateway`, và `BankSystem` để thực hiện các thao tác thanh toán.

### PaymentData
Lớp này chứa dữ liệu về thanh toán, như số tiền, phương thức thanh toán, mã giao dịch, và ngày thanh toán. Lớp này cung cấp thông tin thanh toán cho các lớp khác như `PaymentGateway` và `Transaction`.

### PaymentGateway
Lớp này chịu trách nhiệm gửi yêu cầu thanh toán đến cổng thanh toán (ví dụ: PayPal, Stripe) và nhận phản hồi về trạng thái thanh toán.

### Transaction
Lớp này đại diện cho một giao dịch thanh toán. Nó theo dõi trạng thái của giao dịch và lưu trữ thông tin về thanh toán, cũng như yêu cầu xác nhận từ `BankSystem`.

### BankSystem
Hệ thống ngân hàng xử lý thanh toán, xác nhận giao dịch và chuyển tiền vào tài khoản người nhận.

## Các mối quan hệ

- `PaymentController --> PaymentData`: `PaymentController` sử dụng `PaymentData` để lấy thông tin thanh toán.
- `PaymentController --> PaymentGateway`: `PaymentController` sử dụng `PaymentGateway` để gửi yêu cầu thanh toán và nhận phản hồi.
- `PaymentController --> BankSystem`: `PaymentController` sử dụng `BankSystem` để xác nhận thanh toán qua hệ thống ngân hàng.
- `PaymentData --> Transaction`: `PaymentData` cung cấp dữ liệu giao dịch cho `Transaction`.
- `PaymentGateway --> Transaction`: `PaymentGateway` cập nhật trạng thái giao dịch trong `Transaction`.
- `Transaction --> BankSystem`: `Transaction` yêu cầu `BankSystem` xác nhận thanh toán đã hoàn tất.
