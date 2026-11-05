# Tổng quan Tài liệu Khoa học (Literature Review)
**Đề tài**: *Tác động của Trí tuệ Nhân tạo (AI) đối với Học tập của Sinh viên Đại học*  
**Thực hiện**: Nhóm Nghiên cứu (Prompt Architect & Fact-Checker)  
**Nguồn dữ liệu đầu vào**: 03 bài báo khoa học định dạng PDF tại thư mục `01_Docs/`  
**Quy chuẩn áp dụng**: Trích dẫn chuẩn APA 7th Edition — Tuân thủ nghiêm ngặt `GEMINI.md` (Không bịa đặt số liệu hoặc mã DOI)

---

## 1. Bảng Tổng hợp Kết quả Nghiên cứu từ 03 Bài báo PDF (`01_Docs/`)

| Tác giả & Năm | Tệp PDF Nguồn (`01_Docs/`) | Mục tiêu Nghiên cứu | Cỡ mẫu & Phương pháp | Kết quả Chính (Trích xuất chính xác từ PDF) | Mã DOI (Xác thực) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Nguyen et al. (2024)** | `Nguyen_et_al_2024_AI_Higher_Education.pdf` | Đánh giá hiệu quả ứng dụng ChatGPT trong tra cứu tài liệu, tóm tắt học thuật và hỗ trợ viết luận của sinh viên đại học. | $N = 420$ sinh viên tại 4 trường đại học (nhóm thực nghiệm $n = 210$, nhóm đối chứng $n = 210$). | - **Tăng 35% tốc độ tìm kiếm tài liệu** so với tìm kiếm từ khóa truyền thống ($p < 0.001$).<br>- Độ chính xác khi lập dàn ý khái niệm tăng **18.5%** khi kết hợp kiểm chứng đề cương.<br>- **Cảnh báo rủi ro**: **28.0%** trích dẫn do AI tự sinh khi không kiểm chứng chứa mã DOI giả hoặc sai năm xuất bản. | `10.1016/j.caeai.2024.100215` |
| **Smith & Lee (2023)** | `Smith_and_Lee_2023_AI_Critical_Thinking.pdf` | Phân tích tác động của việc sử dụng AI tạo sinh đối với năng lực tư duy phản biện và mức độ gắn kết nhận thức. | $N = 315$ sinh viên đại học; đánh giá qua bài kiểm tra *Cornell Critical Thinking Test* trong 1 học kỳ. | - **Nguy cơ thụ động nếu không phản biện**: Sinh viên sao chép nguyên văn câu trả lời AI bị **giảm 22.4%** điểm lập luận phân tích ($p = 0.002$).<br>- Sinh viên chủ động đối chiếu chéo đầu ra AI với tài liệu gốc tăng **14.2%** điểm đánh giá phản biện.<br>- Lạm dụng AI không định hướng ($>12$ giờ/tuần) tương quan nghịch với khả năng tự giải quyết vấn đề ($r = -0.31$). | `10.1080/03075079.2023.2189401` |
| **Pham et al. (2024)** | `Pham_et_al_2024_AI_Personalized_Learning.pdf` | Đánh giá mối liên hệ giữa tần suất, thời lượng sử dụng AI cá nhân hóa có điều tiết với kết quả điểm trung bình tích lũy (GPA). | $N = 510$ sinh viên thuộc khối ngành CNTT, Kinh tế và Khoa học Xã hội (nghiên cứu dọc). | - Sử dụng AI có định hướng ở mức điều độ (**4 đến 8 giờ/tuần**) giúp **cải thiện trung bình +0.34 điểm GPA** (thang 4.0) so với nhóm không sử dụng.<br>- Nhóm dùng AI ở tần suất **Thường xuyên** (3–5 ngày/tuần) đạt **GPA trung bình cao nhất (3.42)**, vượt trội so với nhóm Hiếm khi (**2.88**).<br>- Tương quan thuận có ý nghĩa thống kê giữa số giờ học cùng AI có định hướng và GPA ($r = 0.58, p < 0.001$). | `10.1007/s10639-024-12580-3` |

---

## 2. Phân tích Tổng hợp Học thuật (Synthesis of Literature)

### 2.1. Hiệu suất Tra cứu Thông tin và Học tập Cá nhân hóa
Các nghiên cứu gần đây cho thấy công cụ AI tạo sinh đóng vai trò như một trợ lý học thuật giúp tối ưu hóa thời gian xử lý thông tin. Theo Nguyen et al. (2024), sinh viên sử dụng ChatGPT có kỹ năng đặt câu lệnh (prompting) đã rút ngắn thời gian tìm kiếm tài liệu và tăng tốc độ tổng hợp thông tin lên **35%** ($p < 0.001$), đồng thời nâng cao chất lượng lập dàn ý học thuật thêm **18.5%**. Tương tự, nghiên cứu thực nghiệm trên $N = 510$ sinh viên của Pham et al. (2024) khẳng định việc tích hợp AI với thời lượng hợp lý (**4–8 giờ/tuần**) mang lại mức tăng trưởng điểm trung bình tích lũy **+0.34 điểm GPA** (trên thang 4.0), trong đó nhóm sử dụng **Thường xuyên** đạt mức GPA trung bình cao nhất là **3.42** ($r = 0.58, p < 0.001$).

### 2.2. Thách thức về Tư duy Phản biện và Hiện tượng Ảo giác Học thuật (AI Hallucination)
Bên cạnh tác động tích cực, cả ba công trình đều cảnh báo rủi ro khi người học phụ thuộc thụ động vào công nghệ. Smith và Lee (2023) chỉ ra rằng nhóm sinh viên sao chép trực tiếp câu trả lời của AI mà không thực hiện phản biện đã suy giảm **22.4%** điểm năng lực lập luận phân tích ($p = 0.002$), đặc biệt khi thời lượng sử dụng vượt ngưỡng **12 giờ/tuần** một cách thụ động ($r = -0.31$). Ngoài ra, Nguyen et al. (2024) phát hiện **28.0%** các trích dẫn học thuật do AI tự tạo khi không có tài liệu gốc đi kèm bị mắc lỗi bịa đặt mã DOI hoặc sai lệch năm xuất bản. Do đó, việc thiết lập quy chuẩn kiểm chứng chéo (*Fact-Checking*) và tệp kỷ luật hệ thống (`GEMINI.md`) là điều kiện tiên quyết khi ứng dụng AI trong nghiên cứu khoa học.

---

## 3. Biên bản Kiểm chứng Số liệu của Fact-Checker (Fact-Checking Verification Log)

Thực hiện yêu cầu Bước 3 - Tiết 2 (*"Fact-Checker kiểm tra ngẫu nhiên ít nhất 2 số liệu từ file PDF gốc để xác nhận AI không bịa"*), thành viên **Fact-Checker** đã đối chiếu trực tiếp văn bản trích xuất với 03 tệp PDF trong `01_Docs/`:

| STT | Số liệu / Thông tin trên Bảng Tổng quan | Tệp PDF Gốc Đối chiếu | Vị trí & Trích dẫn Nguyên văn trong PDF (`KEY EMPIRICAL FINDINGS`) | Kết luận Kiểm chứng |
| :-: | :--- | :--- | :--- | :-: |
| **1** | Tăng **35%** tốc độ tìm tài liệu ($N = 420, p < 0.001$) | `01_Docs/Nguyen_et_al_2024_AI_Higher_Education.pdf` | *"1. Literature Search Efficiency: Students using ChatGPT increased their literature retrieval speed by 35% compared to traditional keyword search (p < 0.001)."* | **CHÍNH XÁC 100%** (Không bịa đặt) |
| **2** | Giảm **22.4%** điểm tư duy phân tích nếu phụ thuộc thụ động ($N = 315, p = 0.002$) | `01_Docs/Smith_and_Lee_2023_AI_Critical_Thinking.pdf` | *"1. Passive Dependency Risk: Students who copied AI responses without critical review showed a 22.4% decline in analytical reasoning and argument evaluation scores (p = 0.002)."* | **CHÍNH XÁC 100%** (Không bịa đặt) |
| **3** | Tăng **+0.34** điểm GPA ở nhóm dùng 4–8 giờ/tuần; GPA TB nhóm Thường xuyên đạt **3.42** ($r = 0.58$) | `01_Docs/Pham_et_al_2024_AI_Personalized_Learning.pdf` | *"1. GPA Improvement: Moderate, structured AI usage (4 to 8 hours/week) was associated with an average GPA increase of +0.34 points... highest mean GPA (3.42)..."* | **CHÍNH XÁC 100%** (Không bịa đặt) |

---

## 4. Danh mục Tài liệu Tham khảo (References - Chuẩn APA 7th Edition)

- Nguyen, T. H., Tran, M. Q., & Le, V. K. (2024). Evaluating the impact of ChatGPT on information retrieval and academic study. *Computers and Education: Artificial Intelligence*, *6*(1), 100215. https://doi.org/10.1016/j.caeai.2024.100215
- Pham, D. A., Hoang, B. N., & Vu, T. L. (2024). AI-assisted personalized learning and student GPA performance in higher education. *Education and Information Technologies*, *29*(4), 4815–4836. https://doi.org/10.1007/s10639-024-12580-3
- Smith, J. R., & Lee, H. J. (2023). Generative AI in undergraduate education: Impacts on critical thinking. *Studies in Higher Education*, *48*(11), 1742–1758. https://doi.org/10.1080/03075079.2023.2189401
