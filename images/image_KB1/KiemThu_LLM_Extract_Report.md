# Kịch bản đối soát 1: Trích xuất thực thể và Structured Output từ CV/JD thô

Mục tiêu của kịch bản này là đánh giá chất lượng của mô-đun trích xuất thông tin kỹ năng qua Gemini API với cấu hình nhiệt độ phát sinh \(\text{temperature} = 0.0\) và định dạng JSON Schema cưỡng chế đầu ra, kết hợp với tầng xử lý nhận dạng ký tự quang học (OCR) của Tesseract đối với các tài liệu dạng quét.

Phương pháp kiểm chứng được thực hiện bằng cách đối chiếu trực tiếp dữ liệu trích xuất tự động từ mô hình với nhãn chuẩn (Ground Truth) được gán thủ công bởi nhóm thực hiện đề tài. Độ chính xác của thuật toán nhận diện thực thể kỹ năng (NER) được đo lường thông qua ba chỉ số chính: Độ chính xác (Precision), Độ bao phủ (Recall) và Điểm F1 (F1-Score).

*   **TP (True Positives):** Số kỹ năng trích xuất chính xác và có bằng chứng xác thực trong văn bản gốc.
*   **FP (False Positives):** Số kỹ năng bị trích xuất sai hoặc không xuất hiện trong văn bản gốc (ảo giác dữ liệu).
*   **FN (False Negatives):** Số kỹ năng thực tế có trong văn bản nhưng mô hình bỏ sót.

Quy trình nạp dữ liệu đối soát và tải văn bản thô của các tài liệu từ bộ nhớ đệm (cache) phục vụ kiểm chứng chéo được minh họa qua hai hình ảnh thực tế chạy từ notebook:
*   **[Hình 1]** Ảnh chụp màn hình kết quả thực thi Cell 3: Nạp dữ liệu đối soát NER từ bộ nhớ đệm và tập nhãn chuẩn.
*   **[Hình 2]** Ảnh chụp màn hình kết quả thực thi Cell 5: Nạp văn bản gốc của 20 tin tuyển dụng (JD) và hồ sơ ứng viên (CV) phục vụ đối chứng.

---

## Bảng 5.12: Bảng đối soát thống kê kết quả thực nghiệm trích xuất thực thể kỹ năng (NER) theo tập dữ liệu

| Tập dữ liệu | Số lượng | TP | FP | FN | Precision | Recall | F1-Score |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| Tin tuyển dụng (JD) | 20 | 422 | 5 | 57 | 98.8% | 88.1% | 93.2% |
| Hồ sơ ứng viên (CV) | 20 | 103 | 17 | 34 | 85.8% | 75.2% | 80.2% |
| **Tổng cộng** | **40** | **525** | **22** | **91** | **96.0%** | **85.2%** | **90.3%** |

Bảng Confusion Matrix chi tiết đo lường cho từng tài liệu mẫu trong tập dữ liệu kiểm thử được trích xuất trực tiếp từ Jupyter Notebook được minh họa qua hai hình ảnh kết quả:
*   **[Hình 3]** Ảnh chụp màn hình kết quả đối soát chi tiết của tập tin tuyển dụng (JD) ở chế độ Exact Match trên Jupyter Notebook.
*   **[Hình 4]** Ảnh chụp màn hình kết quả đối soát chi tiết của tập hồ sơ ứng viên (CV) ở chế độ Exact Match trên Jupyter Notebook.

---

## Bảng 5.13: Bảng chỉ số đánh giá độ chính xác định dạng dữ liệu và NER từ mô hình

| Độ đo đánh giá dữ liệu (Metric) | Ngưỡng mục tiêu kỳ vọng | Kết quả thực tế | Trạng thái đánh giá |
| :--- | :---: | :---: | :---: |
| Tỷ lệ hợp lệ cấu trúc JSON đầu ra | 100.0% (sau khi tự động retry) | 100.0% | **ĐẠT** |
| Độ chính xác (Precision) của NER | \(\ge\) 85.0% | 96.0% | **VƯỢT TIÊU CHUẨN** |
| Độ phủ (Recall) của NER | \(\ge\) 80.0% | 85.2% | **VƯỢT TIÊU CHUẨN** |
| Điểm F1 (F1-Score) của NER | \(\ge\) 82.5% | 90.3% | **VƯỢT TIÊU CHUẨN** |

Sự so sánh trực quan các chỉ số thực tế này với các ngưỡng kỳ vọng được mô tả chi tiết bằng ảnh chụp màn hình chạy code trong notebook:
*   **[Hình 5]** Ảnh chụp màn hình Cell 13: So sánh các chỉ số thực tế thu được (Precision, Recall, F1) với ngưỡng kỳ vọng đặt ra cho cả hai tập JD và CV.

---

## Phân tích định tính và đánh giá kết quả thực nghiệm

Kết quả thực nghiệm cho thấy module trích xuất kỹ năng bằng LLM đạt hiệu năng cao và vượt các kỳ vọng ban đầu. Cụ thể, tỷ lệ cấu trúc JSON đầu ra hợp lệ đạt tuyệt đối 100.0%, chứng minh tính đúng đắn khi áp dụng cơ chế cưỡng chế JSON Schema của Gemini API với cấu hình temperature = 0.0.

*   **Về độ chính xác (Precision):** Đạt trung bình chung cuộc **96.0%** (trong đó JD đạt kết quả xuất sắc **98.8%** và CV đạt **85.8%**). Kết quả này phản ánh khả năng nhận dạng thực thể chính xác, hạn chế tối đa việc phát sinh ảo giác (hallucination) kỹ năng không có trong tài liệu. Đối với tin tuyển dụng (JD), việc loại bỏ các từ khóa vĩ mô quá chung chung và đối soát toàn bộ văn bản thô đầy đủ giúp giảm đáng kể lỗi FP oan do AI tự ý trích xuất các công nghệ phụ trợ nằm ở nửa sau văn bản dài.
*   **Về độ phủ (Recall):** Đạt trung bình chung cuộc **85.2%** (trong đó JD đạt **88.1%** và CV đạt **75.2%**). Điểm số này vượt ngưỡng kỳ vọng 80% ban đầu. Lỗi bỏ sót (False Negative) xuất hiện do hai nguyên nhân chính:
    1.  Ứng viên trình bày kỹ năng trong CV bằng các cụm từ hành văn tự do, phi chính quy tiếng Việt (như "*phân tích và viết báo cáo khoa học*") khiến việc so khớp mờ với nhãn chuẩn hóa tiếng Anh bị lệch pha.
    2.  Sự chênh lệch về cấp độ phân loại ngữ nghĩa thô (như Pipeline trích xuất "*restful api*" nhưng Ground Truth gán nhãn "*api design*") do chưa đi qua bước chuẩn hóa ngữ nghĩa (Normalize) của kịch bản tiếp theo. 

Điểm F1-Score toàn phần đạt **90.3%**, khẳng định chất lượng dữ liệu đầu vào ổn định để cung cấp cho các module chuẩn hóa và gợi ý việc làm phía sau.

Danh sách chi tiết các lỗi sai thực tế (FP, FN) của từng tài liệu được Jupyter Notebook phân tích và in ra như minh họa tại hình ảnh:
*   **[Hình 6]** Ảnh chụp màn hình Cell 15 & 16: Thống kê chi tiết các lỗi sai thực tế (chế độ Fuzzy Match) trên tập mẫu kiểm thử kèm ký hiệu phân loại trực quan (🔴 FP - Bịa thật, 🔵 FN - Bỏ sót thật).
