# Thiết kế hệ thống con: PrintService

### Phân bổ hành vi subsystem cho các phần tử của subsystem
- Phân tích chức năng `printPaycheck(paycheck: Paycheck)` và phân bổ hành vi cho các phần tử của subsystem như sau:
    * **IPrintService**: interface của subsystem này, xác định hợp đồng chung cho việc in.
    * **PrintServiceImpl**: Cài đặt `IPrintService` và cung cấp chức năng cụ thể để in paychecks.
    * **PrinterManager**: Quản lý kết nối với các máy in và xử lý việc gửi dữ liệu đến máy in.
    * **IPrintFormatter**: interface của subsystem, xác định hợp đồng chung cho việc định dạng đối tượng trước khi in.
    * **PaycheckPrintFormatter**: Cài đặt cụ thể của `IPrintFormatter`, dùng để định dạng paychecks.

### Tài liệu các phần tử trong subsystem
1. **IPrintService**
- Phương thức:
    * `void printPaycheck(Paycheck paycheck);`

2. **PrintServiceImpl**
- Thuộc tính:
    * `PrinterManager printerManager;`
    * `IPrintFormatter printFormatter;`
- Phương thức:
    * `void printPaycheck(Paycheck paycheck);`

3. **PrinterManager**
- Phương thức:
    * `void print(String document);`

4. **IPrintFormatter**
- Phương thức:
    * `String format(Object obj);`

5. **PaycheckPrintFormatter**
- Phương thức:
    * `String format(Object obj);`

##### Class diagram
![Diagram](https://www.planttext.com/api/plantuml/png/d5913e8m4BplAth40xp064uc78malA2K1K5eIIaaHdsP1v_a5mHQ0O4JlRIptPsPtVRpUhkLebBLHGwGSeKofWo9vyiM12YRj4Lt8DrgH1gHihlmwOrTa5sjtu6Kvh239m3BQLMHAOLNbBcXiViuoXFbD46f2GUeKxJyKSY2AlNB6U1sDwFgeYKhKEsMa4Ymka2k-jBvG4P7fjuKnNtSEeSPCaL4c4s5ZPSD1F-li7yupcAei9YoRHzcpQxdp3g2UOTQRjKyW8iywhxC5m00__y30000)
### Subsystem Interaction Diagram
![Diagram](https://www.planttext.com/api/plantuml/png/V9513e9034NtFKN3tWkuCBWnSM5Y91vWCbGam0oMek5iBZoILn04WG7YRlB_V_rjvlry-OKebZ9B0PGMotWkY86Cn5AXT-JOI41yZpNjipprK1Ku5jqayK4P5H4FkLuQaghILzB9rzvPpfJ8Z-YiNWLeri7LnYd5DPxeLb8XA1Rpni6yGy49Dk1qPastxn4poomrIia6Brqa_DFet5sZ0Pbm0UoNh--SCFFwhKwCVQGKHjH2iOa0_7foytSV0000__y30000)
### Mô tả phụ thuộc giữa các phần tử trong subsystem
![Diagram](https://www.planttext.com/api/plantuml/png/T9112i8m44NtESNG0-G0HQGheGj1A1vWZAEM9h5CKg6e9tFXaRo2gGgQjAw6yERFV-HnknVE8_lEQ25QL0tk2RAgsxZUUJ8vhBYslY8-rOeoE0k0y2RUeI8eVs4WIgDpKQ8qhOu1yH9jAE69IuiZ6_J-nJuHxDM1L9FWmADkc5sa71L33iCWGzQx41bnAUU9L8Yi7VrTJZI_sobu-qpAnrPN8Ggos-7xdm000F__0m00)

---

# Subsystem Design: ProjectManagementDatabase

### Phân bổ hành vi subsystem cho các phần tử của subsystem
- **IProjectManagementDatabase**: Interface của subsystem này, nó định nghĩa phương thức `getChargeNumbers`, dùng để lấy charge numbers dựa trên tiêu chí cung cấp.
- **ProjectManagementDatabase**: Cài đặt interface `IProjectManagementDatabase`.
- **DBUtils**: Quản lý kết nối và quản lý cơ sở dữ liệu cũ (legacy database).
- **ChargeNumberDAO**: Chịu trách nhiệm truy vấn charge numbers từ cơ sở dữ liệu cũ.

### Tài liệu các phần tử trong subsystem
1. **IProjectManagementDatabase**:
- Phương thức:
    * `List<String> getChargeNumbers(criteria: String)`

2. **ProjectManagementDatabase**:
- Phương thức:
    * `List<String> getChargeNumbers(criteria: String)`

3. **DBUtils**:
- Thuộc tính:
    * `url: String`
    * `username: String`
    * `password: String`
- Phương thức:
    * `Connection getConnection()`

4. **ChargeNumberDAO**:
- Phương thức:
    * `getChargeNumbers(criteria: String)`

##### Sơ đồ lớp
![Diagram](https://www.planttext.com/api/plantuml/png/f59BJiCm4Dtx5BEZBD83L5LLI3QLIejKSO19CZL6iOrc9aA8SZ8M78aha4zRjKYXI7XZpVZDUs-U_FNnEHT5rjfNvWhI2aMWT6WPFMmZmpt79ohq3WDQyXGqGyKSXK3gN5v5oHlZWX9liI1O3EFV3BHdwKId6sKNx0miQVg8R6bL-vnOHWMxXihX17h8jNatfkXSNM9Eiji7TLLZF-_kVyeTsFRa_JlKN9tNGXpGqrdpkPb_YLps3j8OGkFRnT3f7wlHYTYfg-ncVSZgRtv_oNow6u-7WpF3WqaoEoOmQRUK2-2V6-o7p9n2sVwjRm000F__0m00)

### Sơ đồ tương tác hệ thống
![Diagram](https://www.planttext.com/api/plantuml/png/Z98z4e9038NxFSMMK7W12mULniAVXWE4DOFhG62omSjPU2Il8FwDmZYHDllUbvTah-TB4WHOsgequAHccmLaOvgkvfrlWCIkTbmVqSaQ20gia2G5WHm2zcJZLEaY4r-6Ncrv02vmqrOvSZhV6dFFO2SpfRETsWBbsnWYnrwGFSH6yNLK3UgWB3Mo2dxDzifM4tLANrCKc_VBd-wCqZBPZrNlDzYRlfEXU5mKzt1PUkBqEEgrVlD67PhHeJ_Xq6iIfFtztzu0003__mC0)

### Mô tả phụ thuộc giữa các phần tử trong subsystem
![Diagram](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bT1Od9sOdggWb90KNvMQdA9Rs8Ua9kRcbVYabYIc9HOdAeGN9fKN5bSafghf53DfQ0GxObJQQm2I1wtD4ZMnIcq93Ed6CnspaWiIa_rAyrDIYroSVIFvQhbui9hlAwk7Jxp5QmKF7CBSi22nLpu588DWZa5g2sqE9K83UZkXMdaSaZDIm659W000F__0m00)
