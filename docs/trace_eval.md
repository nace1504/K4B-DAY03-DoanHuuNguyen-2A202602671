# 📊 BÁO CÁO THU HOẠCH NGHIỆM THU BÀI LAB 3 (BƯỚC 3 — SUBMISSION ARTIFACT)

> **Họ và Tên Học viên:** Doãn Hữu Nguyên  
> **Mã Sinh Viên / Mã Học viên:** 2A202602671  
> **Chủ đề Lựa chọn:** Trợ lý Học vụ & Tra cứu Lịch thi VinUni (Gợi ý 1.1)

---

## 1. BẢNG CHẤM ĐIỂM AGENTIC FIT SCORING MATRIX (ĐÁNH GIÁ CHỦ ĐỀ)

| Tiêu chí Đánh giá | Mức độ (1 - 5) | Giải trình chi tiết lý do chọn điểm |
| :--- | :---: | :--- |
| **1. Multi-step Reasoning** | 4 / 5 | Bài toán yêu cầu chia nhỏ các bước: tra cứu thông tin học vụ trước để lấy thông tin, sau đó quyết định và thực hiện thao tác đặt lịch hẹn. |
| **2. Tool Interaction** | 5 / 5 | Hệ thống bắt buộc phải tương tác với MCP Server để truy xuất database sinh viên giả lập và ghi nhận lịch hẹn qua các Native Tools. |
| **3. Dynamic Decision** | 4 / 5 | Agent phải linh hoạt tự chọn gọi tool `academic_query` hay `schedule_appointment` tùy thuộc vào ý định và câu hỏi thực tế của sinh viên. |
| **4. Long Horizon Goal** | 3 / 5 | Agent duy trì ngữ cảnh xuyên suốt các bước ReAct (Thought -> Action -> Observation) để đạt được mục tiêu trả lời trọn vẹn cho sinh viên. |
| **TỔNG ĐIỂM AGENTIC FIT** | **16 / 20** | *Nếu tổng điểm > 12/20: Bài toán rất phù hợp triển khai Agentic System.* |

---

## 2. TRÍCH XUẤT KẾT QUẢ WATERFALL TRACE LOG (SAU KHI CHẠY TEST SUITE TRÊN API THẬT)

> ⚠️ **YÊU CẦU NGHIỆM THU:** Mở tệp `.env` điền `GEMINI_API_KEY` (hoặc `OPENAI_API_KEY`) để kết nối LLM thật trước khi thực thi `python src/app.py --all`. Bài nộp chỉ dùng Mock Offline Provider sẽ không đạt điểm nghiệm thực tế.

Dán 1 đoạn trích xuất log tiêu biểu từ file `docs/trace_waterfall.json` sinh ra từ phản hồi LLM API thật:

```json
[
  {
    "step": 1,
    "query": "Đặt lịch hẹn tư vấn cho SV2026001 vào 14:00 ngày 15/23/2009",
    "action_type": "TOOL_EXECUTION",
    "tool_name": "schedule_appointment",
    "arguments": {
      "student_id": "SV2026001",
      "datetime_str": "14:00 15/23/2009"
    },
    "observation": {
      "status": "SUCCESS",
      "booking_id": "BK-SV2026001-99",
      "student_id": "SV2026001",
      "datetime": "14:00 15/23/2009",
      "advisor": "PGS.TS Nguyễn Văn A",
      "message": "Đặt lịch thành công cho sinh viên SV2026001 với PGS.TS Nguyễn Văn A vào lúc 14:00 15/23/2009."
    },
    "latency_ms": 4038.33
  },
  {
    "step": 2,
    "query": "Đặt lịch hẹn tư vấn cho SV2026001 vào 14:00 ngày 15/23/2009",
    "action_type": "FINAL_ANSWER",
    "thought": "Tổng hợp kết quả từ MCP Server thành công.",
    "output": "Đặt lịch thành công cho sinh viên SV2026001 với PGS.TS Nguyễn Văn A vào lúc 14:00 15/23/2009.",
    "latency_ms": 10.0
  }
]