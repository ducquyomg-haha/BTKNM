# Quy chuẩn Hệ thống & Kỷ luật Nghiên cứu Khoa học (GEMINI.md)

Dự án: **Tác động của AI đối với Học tập của Sinh viên**
Workspace: `My_Research_Project/`

---

## 1. System Constraints (Ràng buộc Hệ thống)
- **Language**: Academic Vietnamese (Tiếng Việt học thuật, rõ ràng, khách quan, chuẩn mực).
- **Citation Style**: APA 7th Edition (Định dạng trích dẫn và danh mục tài liệu tham khảo bắt buộc tuân thủ chuẩn APA phiên bản thứ 7).
- **Data Integrity**: Do NOT hallucinate survey metrics, authors, publication years, statistical p-values, or DOI codes (Tuyệt đối KHÔNG tự bịa đặt tác giả, số liệu thống kê, kết quả khảo sát hoặc mã DOI).

---

## 2. Mandatory Rules (3 Quy tắc Bắt buộc)
1. **Định dạng trích dẫn theo chuẩn APA 7th**: Mọi trích dẫn trong bài (`in-text citation`) và danh mục tham khảo (`reference list`) phải tuân thủ nghiêm ngặt quy chuẩn APA 7th Edition (ví dụ: *Nguyen et al., 2024*; *Smith & Lee, 2023*).
2. **Cấm tự bịa tác giả, số liệu hoặc mã DOI**: Chỉ sử dụng dữ liệu có thật từ các bài báo gốc trong thư mục `01_Docs/` và tập dữ liệu khảo sát thực tế tại `02_Data/survey_ai_students.csv`. Mọi con số đưa vào báo cáo phải truy xuất được nguồn gốc.
3. **Phải xin xác nhận trước khi xóa hoặc ghi đè file gốc**: AI Agent tuyệt đối không tự ý xóa bất kỳ tệp tin nào hoặc sửa đổi trực tiếp tệp dữ liệu thô (`02_Data/survey_ai_students.csv`) khi chưa có sự xác nhận rõ ràng của người dùng.

---

## 3. File Permissions & Directory Structure (Quyền Truy cập & Cấu trúc Thư mục)
- **Ask for confirmation** before modifying raw CSV data in `02_Data/survey_ai_students.csv`.
- **Ask for confirmation** before deleting any file in the workspace.
- **Read-only Sources**: Treat all PDF articles in `01_Docs/` and raw datasets in `02_Data/` as immutable source files.
- **Output Destination**: Save all output markdown files (`Literature_Review.md`, `Data_Analysis.md`, `AI_Auditing_Journal.md`, `Final_Research_Report.md`) and visualization charts (`.png`) to `03_Outputs/`.

```text
My_Research_Project/
├── GEMINI.md
├── analyze_survey.py
├── 01_Docs/
│   ├── Nguyen_et_al_2024_AI_Higher_Education.pdf
│   ├── Smith_and_Lee_2023_AI_Critical_Thinking.pdf
│   └── Pham_et_al_2024_AI_Personalized_Learning.pdf
├── 02_Data/
│   └── survey_ai_students.csv
└── 03_Outputs/
    ├── Literature_Review.md
    ├── Data_Analysis.md
    ├── gpa_vs_ai.png
    ├── chart_gpa.png
    ├── AI_Auditing_Journal.md
    └── Final_Research_Report.md
```

---

## 4. Phân công Vai trò Nhóm Nghiên cứu (Team Roles - 4 Thành viên)
| Vai trò (Role) | Trách nhiệm Chính | Tỷ lệ Đóng góp |
| :--- | :--- | :---: |
| **1. Leader** | Điều phối tiến độ 4 tiết, thiết lập cấu trúc Workspace, kiểm duyệt báo cáo tổng hợp và đóng gói `FINAL_RESEARCH_PACKAGE.zip`. | 25% |
| **2. Prompt Architect** | Soạn thảo tệp quy tắc `GEMINI.md`, thiết kế câu lệnh theo mô hình **RCTO** (Role - Context - Task - Output) cho từng tiết học. | 25% |
| **3. Data Operator** | Quản lý dữ liệu `02_Data/survey_ai_students.csv`, vận hành script Python làm sạch dữ liệu khuyết và xuất biểu đồ trực quan hóa. | 25% |
| **4. Fact-Checker** | Kiểm chứng chéo số liệu giữa văn bản AI sinh ra với 3 bài báo PDF gốc và dữ liệu CSV; lập nhật ký kiểm toán `AI_Auditing_Journal.md`. | 25% |
