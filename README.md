# PROJECT 1: FINE-TUNING VÀ TỐI ƯU MÔ HÌNH TÓM TẮT VĂN BẢN TIẾNG VIỆT BẰNG SFT VÀ DPO

Dự án này nhằm mục đích tinh chỉnh (fine-tune) và tối ưu hóa một mô hình ngôn ngữ lớn cho nhiệm vụ Tóm tắt Văn bản Tiếng Việt.

## 🔑 CÁC PHƯƠNG PHÁP VÀ MÔ HÌNH CHÍNH

1.  **Mô hình cơ sở**: Sử dụng **VietAI/vit5-base** (kiến trúc T5) đã được huấn luyện trước trên dữ liệu Tiếng Việt.
2.  **Giai đoạn 1 (Supervised Fine-Tuning - SFT)**:
    * Sử dụng bộ dữ liệu **nam194/vietnews** (20.000 mẫu).
    * Áp dụng kỹ thuật **LoRA (Low-Rank Adaptation)** để tối ưu tài nguyên.
    * Kết quả: SFT là bước cải thiện quan trọng nhất, nâng điểm **ROUGE-L** từ 12.62 (Base) lên **37.61**.
3.  **Giai đoạn 2 (Reinforcement Learning - RL)**:
    * Thực nghiệm các phương pháp học tăng cường: **DPO (Direct Preference Optimization)**, **PPO (Proximal Policy Optimization)** và **GRPO**.
    * **DPO** (35.50) chứng minh tính ổn định và duy trì chất lượng tốt nhất so với các thử nghiệm PPO và GRPO (tối đa 29.19), vốn gặp vấn đề về sụp đổ chế độ (mode collapse) và "lách luật" hàm thưởng (reward hacking).

<img width="780" height="508" alt="image" src="https://github.com/user-attachments/assets/43ff735c-ddb6-4a2a-9d45-603d6f8610b5" />

## 🚀 KẾT LUẬN

SFT là nền tảng cốt lõi để mô hình học cách thực hiện tác vụ tóm tắt. DPO là phương pháp RLHF hiệu quả nhất trong các thí nghiệm được thực hiện, giúp tinh chỉnh thêm chất lượng đầu ra mà không cần Mô hình Thưởng (Reward Model) phức tạp.


# 🤖 Project 2 (file endterm_p2): Medical Visual Question Answering (VQA-Med) - ImageCLEF 2019

## 📝 Tóm Tắt Dự Án

Dự án nhằm giải quyết bài toán Hỏi đáp trên Hình ảnh Y tế (VQA-Med) trong cuộc thi ImageCLEF 2019. Mục tiêu là xây dựng một hệ thống có khả năng đưa ra câu trả lời chính xác dựa trên hình ảnh lâm sàng và câu hỏi liên quan.

## 🧠 Giải Pháp Kỹ Thuật

| Thành phần | Chi tiết |
| :--- | :--- |
| **Mô hình Chính** | **ViLT-B/32 (Vision-and-Language Transformer)**. |
| **Ưu điểm** | Kiến trúc Transformer đơn giản (end-to-end) và nhẹ, hiệu quả cho học tương tác đa phương thức. |
| **Xử lý Ảnh Y tế** | Áp dụng **CLAHE** (tăng tương phản cục bộ) và **Smart Resize** (Letterbox Padding) để bảo toàn chi tiết giải phẫu. |
| **Loss Function** | **Softened Weighted Cross-Entropy Loss** để đối phó với vấn đề mất cân bằng dữ liệu (Class Imbalance). |

## 📊 Kết Quả Đạt Được

Mô hình được huấn luyện và đánh giá trên tập dữ liệu ImageCLEF 2019 VQA-Med.

| Độ đo (Metric) | Kết quả (Mô hình Cải tiến) | So sánh |
| :--- | :--- | :--- |
| **Accuracy (Độ chính xác)** | **$55.8\%$** | Tương đương với **Hạng 7** của cuộc thi ImageCLEF 2019. |
| **BLEU Score** | **$47.7\%$** | Cần cải thiện khả năng sinh văn bản cho câu hỏi Bệnh lý (Abnormality). |
| **Số lượng lớp** | $2183$ | Bài toán phân loại phức tạp. |

## 🚀 Hướng Phát Triển

Để đạt mức SOTA, cần tập trung vào **Medical Domain Pre-training** (Tiền huấn luyện trên miền y tế), áp dụng kỹ thuật **Ensemble** (Học kết hợp) và chuyển sang hướng **Generative** cho các câu hỏi mở (Abnormality).

---

### 🎓 Nhóm thực hiện

* **Trường:** Đại học Tôn Đức Thắng, Khoa Công nghệ Thông tin
* **Giảng viên Hướng dẫn:** PGS.TS Lê Anh Cường
* **Thành viên:** Phạm Văn Minh Khang, Dương Gia Huy, Lâm Vĩ Khang
