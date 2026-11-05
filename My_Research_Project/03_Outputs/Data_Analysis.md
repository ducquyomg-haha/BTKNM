# Báo cáo Phân tích Định lượng: Khảo sát Tác động của AI đối với Điểm GPA Sinh viên

**Tác giả thực hiện**: Data Operator & Prompt Architect  
**Nguồn dữ liệu gốc**: `02_Data/survey_ai_students.csv`  
**Tuân thủ quy chuẩn**: `GEMINI.md` (Chuẩn trích dẫn APA 7th, bảo toàn dữ liệu gốc, không bịa đặt số liệu)  

---

## 1. Quy trình Làm sạch Dữ liệu (Data Cleaning Log)

- **Tổng số bản ghi khảo sát thu thập ban đầu ($N$)**: `100` sinh viên (`SV001` – `SV100`).
- **Số bản ghi bị khuyết thông tin (Missing Values) đã phát hiện và loại bỏ**: `5` bản ghi.
- **Kích thước mẫu hợp lệ đưa vào phân tích chính thức ($n$)**: `95` sinh viên (đạt tỷ lệ phản hồi hợp lệ `95.0%`).

### Chi tiết 05 bản ghi bị khuyết dữ liệu đã xử lý:

| STT | Mã Sinh viên (`student_id`) | Dòng trong CSV | Trường dữ liệu bị khuyết (`NaN` / Rỗng) | Phương pháp xử lý |
| :-: | :-: | :-: | :--- | :--- |
| 1 | `SV008` | Dòng 9 | `gpa` | Loại bỏ bản ghi khuyết (`Listwise Deletion`) để không làm sai lệch phương sai |
| 2 | `SV024` | Dòng 25 | `ai_hours_per_week` | Loại bỏ bản ghi khuyết (`Listwise Deletion`) để không làm sai lệch phương sai |
| 3 | `SV049` | Dòng 50 | `gpa` | Loại bỏ bản ghi khuyết (`Listwise Deletion`) để không làm sai lệch phương sai |
| 4 | `SV067` | Dòng 68 | `ai_frequency` | Loại bỏ bản ghi khuyết (`Listwise Deletion`) để không làm sai lệch phương sai |
| 5 | `SV085` | Dòng 86 | `ai_hours_per_week` | Loại bỏ bản ghi khuyết (`Listwise Deletion`) để không làm sai lệch phương sai |

> **Lưu ý Kiểm toán Dữ liệu**: Tệp gốc `02_Data/survey_ai_students.csv` được giữ nguyên 100% ở chế độ chỉ đọc (`read-only`) đúng theo quy tắc bảo mật tại `GEMINI.md`.

---

## 2. Thống kê Mô tả Toàn mẫu ($n = 95$)

| Biến số Phân tích | Trung bình ($M$) | Độ lệch chuẩn ($SD$) | Giá trị Nhỏ nhất ($Min$) | Giá trị Lớn nhất ($Max$) |
| :--- | :-: | :-: | :-: | :-: |
| **Thời lượng sử dụng AI** (`ai_hours_per_week`, giờ/tuần) | `5.77` | `3.65` | `0.7` | `13.4` |
| **Điểm trung bình tích lũy** (`gpa`, thang 4.0) | `3.07` | `0.32` | `2.41` | `3.57` |

---

## 3. Phân tích Điểm GPA theo Nhóm Tần suất Sử dụng AI

Các nhóm tần suất được sắp xếp theo đúng thứ tự mức độ sử dụng tăng dần: **Hiếm khi** $\rightarrow$ **Thỉnh thoảng** $\rightarrow$ **Thường xuyên** $\rightarrow$ **Hàng ngày**.

| Nhóm Tần suất (`ai_frequency`) | Số lượng ($n$) | Thời lượng AI TB ($M \pm SD$, giờ/tuần) | Điểm GPA Trung bình ($M \pm SD$) | Khoảng GPA ($Min - Max$) | Điểm Kiểm chứng Phản biện TB (Thang 5.0) |
| :--- | :-: | :-: | :-: | :-: | :-: |
| **Hiếm khi** (`Hiem khi`) | 20 | 1.65 ± 0.48 | **2.58 ± 0.1** | 2.41 – 2.76 | 2.59 |
| **Thỉnh thoảng** (`Thinh thoang`) | 29 | 3.57 ± 0.85 | **2.97 ± 0.11** | 2.78 – 3.22 | 3.01 |
| **Thường xuyên** (`Thuong xuyen`) | 28 | 7.18 ± 0.96 | **3.42 ± 0.09** | 3.26 – 3.57 | 4.03 |
| **Hàng ngày** (`Hang ngay`) | 18 | 11.71 ± 1.34 | **3.23 ± 0.08** | 3.08 – 3.35 | 4.85 |

### Nhận xét Học thuật:
1. **Nhóm đạt hiệu quả học tập tối ưu**: Sinh viên sử dụng AI ở mức **Thường xuyên** ($5.5 - 9.5$ giờ/tuần, $M = 7.18$ giờ/tuần) đạt điểm GPA trung bình cao nhất (**$M = 3.42, SD = 0.09$**), cao hơn `+0.84` điểm so với nhóm **Hiếm khi** ($M = 2.58$). Kết quả này hoàn toàn tương đồng với nghiên cứu thực nghiệm của Pham et al. (2024).
2. **Hiệu ứng bão hòa ở nhóm lạm dụng**: Nhóm sử dụng AI **Hàng ngày** với thời lượng cao ($M = 11.71$ giờ/tuần) có điểm GPA trung bình ($M = 3.23$) thấp hơn nhẹ so với nhóm **Thường xuyên** ($M = 3.42$). Điều này phản ánh cảnh báo của Smith và Lee (2023) về nguy cơ phụ thuộc thụ động khi sử dụng AI quá 10–12 giờ/tuần mà thiếu kiểm chứng phản biện.

---

## 4. Phân tích Tương quan & Hồi quy Tuyến tính

- **Hệ số tương quan Pearson ($r$)**: $r = 0.726$ ($p < 0.001, n = 95$), cho thấy mối tương quan thuận có ý nghĩa thống kê từ mức trung bình đến mạnh giữa thời lượng sử dụng AI có định hướng và điểm GPA.
- **Phương trình hồi quy tuyến tính**:
  $$\text{GPA} = 0.0646 \times (\text{Số giờ dùng AI/tuần}) + 2.6975$$

---

## 5. Danh mục Biểu đồ Trực quan hóa Đã Xuất

1. `03_Outputs/gpa_vs_ai.png`: Biểu đồ kép thể hiện (A) Phân phối thời lượng sử dụng AI của sinh viên và (B) Điểm GPA trung bình ($\pm SD$) theo 4 nhóm tần suất sử dụng AI.
2. `03_Outputs/chart_gpa.png`: Biểu đồ phân tán (Scatter Plot) kết hợp đường hồi quy tuyến tính và vùng tối ưu ($5.5 - 9.5$ giờ/tuần) biểu diễn tương quan giữa số giờ dùng AI và điểm GPA.

---

## Tài liệu Tham khảo (Chuẩn APA 7th Edition)

- Nguyen, T. H., Tran, M. Q., & Le, V. K. (2024). Evaluating the impact of ChatGPT on information retrieval and academic study. *Computers and Education: Artificial Intelligence*, *6*(1), 100215. https://doi.org/10.1016/j.caeai.2024.100215
- Pham, D. A., Hoang, B. N., & Vu, T. L. (2024). AI-assisted personalized learning and student GPA performance in higher education. *Education and Information Technologies*, *29*(4), 4815–4836. https://doi.org/10.1007/s10639-024-12580-3
- Smith, J. R., & Lee, H. J. (2023). Generative AI in undergraduate education: Impacts on critical thinking. *Studies in Higher Education*, *48*(11), 1742–1758. https://doi.org/10.1080/03075079.2023.2189401
