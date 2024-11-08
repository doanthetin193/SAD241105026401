# Quản lý Nhân Viên

Đây là sơ đồ lớp của hệ thống quản lý nhân viên với các lớp cơ bản và các lớp con. Lớp `NhanVien` là lớp cha, và các lớp con bao gồm `NhanVienHanhChinh`, `NhanVienNhanSu`, và `NhanVienKyThuat` kế thừa từ lớp cha này.

## Sơ đồ lớp

![Sơ đồ lớp Quản lý Nhân viên](https://www.planttext.com/api/plantuml/png/d991JiCm44NtESNiW0KNO84g6ebAeH5IhEw7rCgCI2QeiHTHu2IiM7C3ikY2a-G4N047cjOK4KLiRCtN-FlDjp_QxQmok36so8CJY0WPxjvVIiYxzla1Oa9PiPOWpR6gzYKq0G2m65ZYliKfbTcmPB0erNSTej6A2mrnXdN2GbvJo3WdzeIa39sDeX9zzLeR9qccM4xFWgTW17A1GivI2EwxjoqOwjfN1EFMl-Oud6YyA-TaqvNrXDiUu0fb3EktvVdZvI6m2vzfR8X-J-pa2NRjpOyS5N5Ammj5ZYNEY7Kn1N_dzp_sg5PaqKo67_gFmg-rBCkliDSwvG9pkB6ETGh-u3Z6FzEoxd_x9m000F__0m00)

## Sơ đồ ca sử dụng

![Sơ đồ ca sử dụng](https://www.planttext.com/api/plantuml/png/X98_JiCm58Ttd-8fUw-02W5Hn1-9DgswLLRoI28bJkGu88IOcJa2i5Km89WIeGu-YK_05N0RGbix5Oiz-Fj-p-_Pt_MYNmZAHPacXFeYu-1SbgfwOP38Bs2HV6PGgFhT0Lh0O3Wxfuo6o5lsOWLSntBELiHHcYVPBI8X77r1MPWWE0DLFu0NgVgHXV2RVgRJ6tdIo7S4e2pGfuKsl4ZEq-rp7JvsP_j1y5TYWvzYgWl8JvtlnQnBdCHuqvedx2hRj5rLlULQqflu9sQS1rJWhg2f_A1TrY4ckBQs6fMlAPp6gbfqjZj2olseIpoGJncuowNHHkqRQUiO6N9zpI7c6HVadf3rmq6ljsSEqZwrfcKZ7PEm8QDn6p0Qj06Z5zAYEszg0aQ5Fh9W-TT_0000__y30000)

## Sơ đồ gói

![Sơ đồ gói](https://www.planttext.com/api/plantuml/png/X98_JiCm58Ttd-8fUw-02W5Hn1-9DgswLLRoI28bJkGu88IOcJa2i5Km89WIeGu-YK_05N0RGbix5Oiz-Fj-p-_Pt_MYNmZAHPacXFeYu-1SbgfwOP38Bs2HV6PGgFhT0Lh0O3Wxfuo6o5lsOWLSntBELiHHcYVPBI8X77r1MPWWE0DLFu0NgVgHXV2RVgRJ6tdIo7S4e2pGfuKsl4ZEq-rp7JvsP_j1y5TYWvzYgWl8JvtlnQnBdCHuqvedx2hRj5rLlULQqflu9sQS1rJWhg2f_A1TrY4ckBQs6fMlAPp6gbfqjZj2olseIpoGJncuowNHHkqRQUiO6N9zpI7c6HVadf3rmq6ljsSEqZwrfcKZ7PEm8QDn6p0Qj06Z5zAYEszg0aQ5Fh9W-TT_0000__y30000)

## Mô tả các lớp

### Lớp `NhanVien`
- **Thuộc tính**: `MaNhanVien`, `HoTen`, `NgaySinh`, `DiaChi`, `SoDienThoai`
- **Phương thức**: `GetThongTin()`

### Lớp `NhanVienHanhChinh` (Kế thừa từ `NhanVien`)
- **Thuộc tính**: `ChucVu`, `PhongBan`
- **Phương thức**: `GetThongTin()`

### Lớp `NhanVienNhanSu` (Kế thừa từ `NhanVien`)
- **Thuộc tính**: `SoThich`, `KinhNghiem`
- **Phương thức**: `GetThongTin()`

### Lớp `NhanVienKyThuat` (Kế thừa từ `NhanVien`)
- **Thuộc tính**: `ChuyenMon`, `Luong`
- **Phương thức**: `GetThongTin()`
