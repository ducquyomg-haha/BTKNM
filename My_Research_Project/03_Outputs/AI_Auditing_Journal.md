# Nhật ký Kiểm toán AI, Báo cáo Tổng hợp & Đánh giá Đóng góp Nhóm (Tiết 4)

**Đề tài**: *Tác động của Trí tuệ Nhân tạo (AI) đối với Học tập của Sinh viên Đại học*  
**Workspace**: `My_Research_Project/`  
**Tuân thủ quy chuẩn**: `GEMINI.md` (Chuẩn APA 7th Edition, Bảo toàn dữ liệu gốc, Kiểm chứng chéo 100%)

---

## Phần 1. Nhật ký Kiểm toán AI (`AI_Auditing_Journal`)

Trong quá trình thực hiện bài tập thực hành 4 tiết cùng AI Agent trên Antigravity IDE, nhóm nghiên cứu (đặc biệt là **Fact-Checker** và **Data Operator**) đã tiến hành kiểm toán nghiêm ngặt toàn bộ mã nguồn, số liệu thống kê và biểu đồ đầu ra. Dưới đây là **03 lỗi thực tế của AI** đã được nhóm phát hiện và yêu cầu AI khắc phục triệt để:

### Lỗi Thực tế số 01: Xử lý giá trị khuyết (`Missing Values`) và Thứ tự phân loại trên biểu đồ
- **Mô tả lỗi của AI**:
  1. Trong tệp dữ liệu `02_Data/survey_ai_students.csv` ($N = 100$), có **05 bản ghi bị khuyết dữ liệu** (`SV008` và `SV049` khuyết `gpa`; `SV024` và `SV085` khuyết `ai_hours_per_week`; `SV067` khuyết `ai_frequency`). Ở phương án xử lý mặc định ban đầu, việc điền giá trị `0` (`fillna(0)`) vào các ô trống làm kéo tụt điểm GPA trung bình xuống mức sai lệch và vi phạm quy tắc `Data Integrity: Do NOT hallucinate survey metrics` trong `GEMINI.md`.
  2. Khi vẽ biểu đồ cột theo nhóm tần suất (`ai_frequency`), mặc định nhóm phân loại bị sắp xếp theo bảng chữ cái ABC (`Hang ngay` $\rightarrow$ `Hiem khi` $\rightarrow$ `Thinh thoang` $\rightarrow$ `Thuong xuyen`) thay vì trình tự mức độ sử dụng tăng dần.
- **Cách nhóm phát hiện**:
  - **Fact-Checker** kiểm tra đối chiếu số lượng mẫu từng nhóm và phát hiện tổng mẫu hợp lệ phải là $n = 95$ (sau khi loại 5 dòng khuyết), đồng thời nhận thấy thứ tự cột trên trục hoành chưa theo logic tần suất tăng dần.
- **Câu lệnh (Prompt) yêu cầu AI sửa lại**:
  > *"Không được thay thế giá trị khuyết bằng số 0. Hãy lọc bỏ 5 bản ghi khuyết thông tin (Listwise Deletion) và ghi log rõ mã sinh viên bị khuyết vào báo cáo `Data_Analysis.md`. Đồng thời cố định thứ tự trục X trên biểu đồ theo đúng mức độ tăng dần: `['Hiem khi', 'Thinh thoang', 'Thuong xuyen', 'Hang ngay']`."*
- **Kết quả sau khi sửa**:
  - Mẫu phân tích sạch đạt $n = 95$, giữ nguyên vẹn tệp CSV gốc. Thứ tự 4 nhóm trên biểu đồ `gpa_vs_ai.png` hiển thị chuẩn xác từ thấp đến cao.

---

### Lỗi Thực tế số 02: Lỗi Mã hóa Ký tự Tiếng Việt (`UnicodeEncodeError: cp1252`) khi chạy Script qua Windows Terminal
- **Mô tả lỗi của AI**:
  - Khi chạy tự động tệp `analyze_survey.py` trong cửa sổ Terminal của Windows PowerShell, câu lệnh `print("BẮT ĐẦU PHÂN TÍCH DỮ LIỆU...")` gặp ngoại lệ:
    ```text
    UnicodeEncodeError: 'charmap' codec can't encode character '\u1eae' in position 1: character maps to <undefined>
    ```
  - Nguyên nhân do luồng xuất chuẩn (`sys.stdout`) mặc định của Python trên Windows sử dụng bảng mã `cp1252` thay vì `utf-8`.
- **Cách nhóm phát hiện**:
  - **Data Operator** quan sát trực tiếp mã thoát (`Exit Code 1`) và thông báo lỗi trên Terminal ở lần chạy thử nghiệm đầu tiên.
- **Câu lệnh (Prompt) yêu cầu AI sửa lại**:
  > *"Hãy cấu hình lại `sys.stdout.reconfigure(encoding='utf-8')` và `sys.stderr.reconfigure(encoding='utf-8')` ở đầu tệp `analyze_survey.py` để script chạy mượt trên Windows Terminal với tiếng Việt có dấu."*
- **Kết quả sau khi sửa**:
  - Script chạy hoàn toàn tự động qua Terminal với `Exit Code 0`, hiển thị đầy đủ bảng thống kê tiếng Việt có dấu.

---

### Lỗi Thực tế số 03: Xung đột tên biến không phân biệt hoa/thường (`$H` và `$h`) làm hỏng kích thước ảnh `chart_gpa.png`
- **Mô tả lỗi của AI**:
  - Trong mô-đun kết xuất đồ họa độ phân giải cao (`1600x900`), AI đặt biến chiều cao khung vẽ là `$H = 900`. Tuy nhiên, trong vòng lặp duyệt dữ liệu trước đó (`foreach ($r in $rows)`), AI đặt tên biến tạm lưu số giờ dùng AI là `$h = [double]$r.ai_hours_per_week`. Do ngôn ngữ PowerShell không phân biệt chữ hoa và chữ thường (`case-insensitive`), biến `$H` bị ghi đè thành `11` pixel, khiến tệp ảnh `chart_gpa.png` sinh ra lần đầu chỉ nặng `177 bytes` (`1600x11` pixel).
- **Cách nhóm phát hiện**:
  - **Data Operator** kiểm tra dung lượng tệp đầu ra bằng lệnh `Get-Item 03_Outputs/*.png` và **Fact-Checker** mở trực tiếp tệp ảnh để kiểm tra thị giác, phát hiện `chart_gpa.png` bị dẹt bất thường.
- **Câu lệnh (Prompt) yêu cầu AI sửa lại**:
  > *"Đổi tên biến tạm trong vòng lặp từ `$h`, `$g` thành `$hrVal`, `$gpaVal` để không ghi đè lên biến kích thước ảnh `$H = 900`, đồng thời cập nhật ghi chú chân trang của `gpa_vs_ai.png` lấy động giá trị GPA trung bình của nhóm Thường xuyên (3.42/4.0)."*
- **Kết quả sau khi sửa**:
  - Cả hai biểu đồ `03_Outputs/gpa_vs_ai.png` và `03_Outputs/chart_gpa.png` đều đạt độ phân giải `1600x900` sắc nét, đầy đủ trục tọa độ, đường hồi quy, vùng tối ưu và chú giải.

---

## Phần 2. Báo cáo Tổng hợp Dự án Nghiên cứu (Executive Summary)

### 2.1. Đối sánh Kết quả Thực nghiệm Khảo sát ($n = 95$) với Tổng quan Tài liệu (`01_Docs/`)
Kết quả phân tích tập dữ liệu khảo sát sinh viên tại `02_Data/survey_ai_students.csv` ($N = 100$ phản hồi, $n = 95$ bản ghi hợp lệ sau làm sạch) cho thấy sự nhất quán cao với 03 công trình nghiên cứu quốc tế trong `01_Docs/`:

1. **Mối tương quan thuận giữa thời lượng sử dụng AI có định hướng và điểm GPA**:
   - Dữ liệu khảo sát ghi nhận thời lượng sử dụng AI trung bình là **$5.77 \pm 3.65$ giờ/tuần** và điểm GPA trung bình toàn mẫu là **$3.07 \pm 0.32$** (thang 4.0).
   - Hệ số tương quan Pearson đạt **$r = 0.726$ ($p < 0.001$)** với phương trình hồi quy tuyến tính $\text{GPA} = 0.0646 \times \text{Giờ\_AI} + 2.6975$, củng cố phát hiện của Pham et al. (2024) về tương quan thuận giữa sử dụng AI có điều tiết và kết quả học tập ($r = 0.58, p < 0.001$).
2. **Ngưỡng sử dụng tối ưu ("Vùng tối ưu 5.5 – 9.5 giờ/tuần")**:
   - Sinh viên nhóm **Thường xuyên** ($M = 7.18 \pm 1.15$ giờ/tuần, $n = 28$) đạt điểm GPA trung bình cao nhất là **$3.42 \pm 0.09$**, cao hơn **+0.84 điểm** so với nhóm **Hiếm khi** ($M = 2.58 \pm 0.10, n = 20$) và cao hơn **+0.45 điểm** so với nhóm **Thỉnh thoảng** ($M = 2.97 \pm 0.11, n = 29$). Con số này trùng khớp với mức GPA tối ưu **3.42** trong nghiên cứu của Pham et al. (2024) và hiệu suất tra cứu tài liệu tăng **35%** của Nguyen et al. (2024).
3. **Cảnh báo suy giảm hiệu quả khi lạm dụng thụ động**:
   - Ở nhóm sử dụng AI **Hàng ngày** với thời lượng rất cao ($M = 11.71 \pm 1.49$ giờ/tuần, $n = 18$), điểm GPA trung bình giảm nhẹ xuống **$3.23 \pm 0.08$** (thấp hơn 0.19 điểm so với nhóm Thường xuyên). Hiện tượng này minh chứng thực nghiệm cho cảnh báo của Smith và Lee (2023): việc phụ thuộc vào AI quá 10–12 giờ/tuần mà thiếu phản biện làm giảm **22.4%** năng lực lập luận phân tích.

---

## Phần 3. Bảng Đánh giá Đóng góp Nhóm (Team Contribution Rubric)

Bốn thành viên trong nhóm đã phối hợp thực hiện đầy đủ 4 tiết thực hành theo đúng chức trách đã phân công tại Tiết 1 và thống nhất tỷ lệ đóng góp công bằng như sau:

| STT | Vai trò trong Nhóm (Role) | Nhiệm vụ Cụ thể Đã Hoàn thành | Sản phẩm Bàn giao Chính | Tỷ lệ Đóng góp (%) | Đánh giá Hoàn thành |
| :-: | :--- | :--- | :--- | :-: | :-: |
| **1** | **Leader** | Thiết lập cấu trúc thư mục dự án `My_Research_Project/`, điều phối tiến độ 4 tiết, tổng hợp báo cáo cuối kỳ và đóng gói tệp `FINAL_RESEARCH_PACKAGE.zip`. | Cấu trúc Workspace, `Final_Research_Report.md`, `FINAL_RESEARCH_PACKAGE.zip` | **25%** | 100% (Xuất sắc) |
| **2** | **Prompt Architect** | Soạn thảo tệp quy tắc hệ thống `GEMINI.md` (3 quy tắc bắt buộc + quyền truy cập tệp) và thiết kế chuỗi câu lệnh chuẩn **RCTO** (Role - Context - Task - Output) cho Tiết 2, 3, 4. | `GEMINI.md`, Bộ Prompt RCTO chuẩn hóa | **25%** | 100% (Xuất sắc) |
| **3** | **Data Operator** | Quản lý dữ liệu `02_Data/survey_ai_students.csv`, phát triển và chạy script `analyze_survey.py` làm sạch 5 dòng dữ liệu khuyết, xuất 02 biểu đồ PNG và báo cáo thống kê. | `analyze_survey.py`, `03_Outputs/gpa_vs_ai.png`, `03_Outputs/chart_gpa.png`, `03_Outputs/Data_Analysis.md` | **25%** | 100% (Xuất sắc) |
| **4** | **Fact-Checker** | Kiểm chứng chéo toàn bộ trích dẫn APA 7th, mã DOI và số liệu giữa bảng tổng quan với 03 tệp PDF gốc trong `01_Docs/`; phát hiện 03 lỗi thực tế của AI và lập nhật ký kiểm toán. | `03_Outputs/Literature_Review.md`, `03_Outputs/AI_Auditing_Journal.md` | **25%** | 100% (Xuất sắc) |
| **TỔNG** | **4 Thành viên (25% + 25% + 25% + 25%)** | **Hoàn thành toàn bộ yêu cầu 4 Tiết thực hành (Thang điểm 100%)** | **Trọn bộ gói sản phẩm nghiên cứu** | **100%** | **Đạt 100/100** |

---

## Tài liệu Tham khảo (Chuẩn APA 7th Edition)

- Nguyen, T. H., Tran, M. Q., & Le, V. K. (2024). Evaluating the impact of ChatGPT on information retrieval and academic study. *Computers and Education: Artificial Intelligence*, *6*(1), 100215. https://doi.org/10.1016/j.caeai.2024.100215
- Pham, D. A., Hoang, B. N., & Vu, T. L. (2024). AI-assisted personalized learning and student GPA performance in higher education. *Education and Information Technologies*, *29*(4), 4815–4836. https://doi.org/10.1007/s10639-024-12580-3
- Smith, J. R., & Lee, H. J. (2023). Generative AI in undergraduate education: Impacts on critical thinking. *Studies in Higher Education*, *48*(11), 1742–1758. https://doi.org/10.1080/03075079.2023.2189401
