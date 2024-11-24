# 1. Subsystem Context Diagrams

### PrintService

![PrintService Diagram](https://www.planttext.com/api/plantuml/png/b5DBJiCm4Dtd5AFiUm5KLIqKeIugLUG4KtSIJ1Exibr4X7eo5Xo9Ap1sugI1b89tC_EUttl-VBv_pAr3uuvLcQ1msa1wNnrANHEbW1PY4OSRh8qkIrZiAgcaTGQv7P2X4s6tgFQGrTPH5OQ-Rifk8wEVIJXOeyA2Ab8EbkXmYxOHtgnZcII6WQYAaZnDAfUHUP62SMy9y3eRmtGgj79iSJQ3WBrhof9OiyNx5NF1PF8JUDFg0ASLJoJsQSSBAI-H7aWH7mZ18nsqSRQXdP8HbymbawEWw7CL6mERtqKwuHxEkdsHyz4U_5oguXTrUzpQS1iCrgyrUsWSjm6aLXlVlsfbd7Nn9FmQfuHStOtx7HP2aELdq3uJF_fN8Buw_wZ-bcC0Pl6Cr2usOQLotViVG3stVzeTSobDyCnHhJpVu9Im-pb3_7Vx0W00__y30000)

#### Giải thích:

- **PrintController (<<control>>)**: Đây là thành phần điều khiển chính, chịu trách nhiệm xử lý các yêu cầu in từ Employee và Admin (in phiếu lương, tạo báo cáo).
- **PrintInterface (<<interface>>)**: Đây là giao diện cho các thao tác in, mà PrintController sử dụng để thực hiện các chức năng in ấn.
- **ReportGenerationProxy (<<subsystem proxy>>)**: Đây là proxy hệ thống con quản lý việc tạo báo cáo, nó liên hệ với Project Management Database để truy xuất thông tin cần thiết cho báo cáo.
- **PaymentProxy (<<subsystem proxy>>)**: Đây là proxy hệ thống con chịu trách nhiệm gửi thông tin thanh toán (bao gồm thông tin chuyển khoản trực tiếp) tới Bank System.

### ProjectManagementDatabase subsystems

![ProjectManagementDatabase Diagram](https://www.planttext.com/api/plantuml/png/T9DDJiCm48NtESN8-mg99Qgg0kc2HKHfkO3hJ94XjeCzGKI8ax7WI5m1ZvEqeIbPH9xnzrxcH_dv-bu6afuQKsMrL2_o2K6iPUjTLS6s3OH6m4S6yP6Ad0UnCdNbMaG1Ci0GZ851VLqQRNKWBsCwqIcJqFHIpjJEegMZvjPPuWD6mNokkcYnO76F78d_FEuieTzBXMoXX-2FoG6PU1GvhBrxRraRcbr84u2QKxr3aITWelJk6HL1Bad2ofAcv87fr4ixX8aEo3wpqT2xsqBQ69geOsud0mxpB_iOH7vp2ONKTk-bwVOGCsmsh0DciyMaLxW2iMrsHXCyQeDA-l9YVI-oj9L_5LqzXqN7wUwTo2RaI7xS4EjZMmf3W0s-DXWe7BGZB8dxkRBceK7VmdYYKJNSCym3YDm6oMjymnxXxAdLODANFJOvMswqRBmz_VRvYi_D5sqPMmrDnPrconZod_KB003__mC0)

#### Giải thích Chi Tiết:

**Các Thành Phần:**

- **Employee**: Nhân viên nhập thông tin như timecard hoặc đơn hàng (purchase orders) thông qua giao diện Payroll.
- **Payroll Administrator**: Người quản lý hệ thống Payroll thực hiện các tác vụ quản lý thông tin nhân viên.
- **Payroll Controller (<<control>>)**: Thành phần chịu trách nhiệm xử lý logic nghiệp vụ của hệ thống Payroll. Nó kết nối với proxy của hệ thống PMD để truy vấn dữ liệu dự án.
- **Payroll Interface (<<interface>>)**: Giao diện người dùng (UI) nơi nhân viên và Payroll Administrator tương tác với hệ thống.
- **PMD Proxy (<<subsystem proxy>>)**: Là một proxy giúp hệ thống Payroll truy cập dữ liệu từ ProjectManagementDatabase mà không can thiệp trực tiếp vào DB2. Proxy này sẽ đảm bảo các kết nối và xử lý truy vấn một cách phù hợp.
- **Project Data Entity (<<entity>>)**: Đại diện cho dữ liệu dự án được truy vấn từ DB2 Mainframe, như thông tin mã số tính phí và dự án.

**ProjectManagementDatabase:**

- **DB2 Mainframe**: Cơ sở dữ liệu cũ chứa dữ liệu về các dự án và mã số tính phí. Đây là nguồn dữ liệu chính cho các truy vấn liên quan đến thông tin dự án.

**Luồng Dữ Liệu:**

1. Employee/Payroll Administrator nhập yêu cầu thông qua Payroll Interface.
2. Payroll Interface gửi yêu cầu đến Payroll Controller, nơi thực hiện xử lý logic nghiệp vụ.
3. Payroll Controller sử dụng PMD Proxy để kết nối với ProjectManagementDatabase.
4. PMD Proxy gửi truy vấn đến DB2 Mainframe, nhận dữ liệu, và chuyển lại cho Payroll Controller.
5. Payroll Controller gửi kết quả đến Payroll Interface để hiển thị cho người dùng.

---

# 2. Analysis Class to Design Element Map

### PrintService

| Analysis Class               | Design Element            |
|------------------------------|---------------------------|
| PrintInterface               | IPrintService             |
| PrintController              | PrintControllerImpl       |
| Paycheck                     | PaycheckEntity            |
| Report                       | ReportEntity              |
| PaymentProxy                 | PaymentServiceProxy       |
| ReportGenerationProxy        | ReportGenerator           |

### ProjectManagementDatabase subsystems

| Analysis Class                  | Design Element           |
|---------------------------------|--------------------------|
| Payroll Interface               | PayrollInterface         |
| Payroll Controller              | PayrollControllerImpl    |
| PMD Proxy                       | ProjectManagementProxy   |
| Project Data Entity             | ProjectDataEntity        |
| Employee                        | EmployeeInterface        |
| Payroll Administrator           | AdminInterface           |
| DB2 Mainframe                   | DB2MainframeAdapter      |

---

# 3. Design Element to Owning Package Map

### PrintService

| STT  | Design Element         | "Owning Package"        |
|------|------------------------|-------------------------|
| 1    | Print Interface         | User Interface Layer    |
| 2    | Print Controller        | Business Logic Layer    |
| 3    | Print Job Entity        | Data Access Layer       |
| 4    | Printer Proxy           | Data Access Layer       |
| 5    | Printer Adapter         | External Systems        |

### ProjectManagementDatabase subsystems

| STT  | Design Element           | "Owning Package"        |
|------|--------------------------|-------------------------|
| 1    | Payroll Interface         | User Interface Layer    |
| 2    | Employee Interface        | User Interface Layer    |
| 3    | Admin Interface           | User Interface Layer    |
| 4    | Payroll Controller        | Business Logic Layer    |
| 5    | PMD Proxy                | Data Access Layer       |
| 6    | Project Data Entity      | Data Access Layer       |
| 7    | DB2 Mainframe Adapter    | ProjectManagementDatabase|

---

# 4. Architectural Layers and Their Dependencies

![Architectural Layers Diagram](https://www.planttext.com/api/plantuml/png/T98zJiCm68Ptd-9J5gOkZAYA-iU0H8JQY0br-70_KWl7jcod8aBCd8CJS80C39oa9-0As2c2H0aUNp_FAxsMlvgFcVDeVLLAPf0_Oa6Gp8sHWgCNMYKmdKgioQOfF3C8v-xs2fQwD5gHyblsmlwyHUM48kSW9tiGdDo8_SjSwqBmlhz2Zp3dGHmpDsIq4rxRUdiAMZpJEvB3cdjqDDAnMfn3Xa8zM2pff-R6xyd2vPCdgr12NZjFfMihps1TeOBziNc5GXoRTmJ--SQXRNMi_nGmcQI3VN01oHAbJDZWfiKxeoAwhiZMWUt6BTVP6haCJQ2wuOdgpOjW7Zfe3FrdTNGsvAsWGz1cf7RnPtm3003__mC0)

---

