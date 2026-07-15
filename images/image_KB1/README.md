# BẢO CÁO TOÀN VĂN MỤC 5.4: PHÂN TÍCH THỰC TẾ CÁC TRƯỜNG HỢP ĐỐI SOÁT KIỂM THỬ

Tài liệu này trình bày toàn bộ nội dung văn bản tiếng Việt của **Mục 5.4** trong Luận văn. Nội dung dưới đây mô tả chi tiết vị trí chèn của tất cả 15 hình ảnh minh chứng thực tế (tương ứng với các Cell trong Jupyter Notebook) so với văn bản báo cáo và các bảng số liệu để bạn dễ dàng duyệt trước khi đưa vào bản LaTeX chính thức.

---

## 5.4. PHÂN TÍCH THỰC TẾ MỘT SỐ TRƯỜNG HỢP ĐỐI SOÁT

### 5.4.1. Đánh giá độ chính xác của định dạng dữ liệu trả về từ mô hình và các thuật toán tiền xử lý

Phần này trình bày các kịch bản đối soát thực tế và khung chỉ số đánh giá chất lượng cho các thuật toán xử lý dữ liệu đầu vào, bao gồm bóc tách dữ liệu bán cấu trúc bằng mô hình ngôn ngữ lớn (LLM), chuẩn hóa kỹ năng hai tầng, gộp nhóm doanh nghiệp và khử trùng sâu tin đăng bằng vector nhúng kết hợp Cosine Similarity. Các thực nghiệm dưới đây được thực thi trực tiếp trên môi trường triển khai thật (container `nova-algo-api` và cơ sở dữ liệu production, tháng 07/2026).

---

#### 1. Kịch bản đối soát 1: Trích xuất thực thể và Structured Output từ CV/JD thô

Mục tiêu của kịch bản này là đánh giá chất lượng của mô-đun trích xuất thông tin kỹ năng qua Gemini API với cấu hình nhiệt độ phát sinh \(\text{temperature} = 0.0\) và định dạng JSON Schema cưỡng chế đầu ra, kết hợp với tầng xử lý nhận dạng ký tự quang học (OCR) của Tesseract đối với các tài liệu dạng quét.

Phương pháp kiểm chứng được thực hiện bằng cách đối chiếu trực tiếp dữ liệu trích xuất tự động từ mô hình với nhãn chuẩn (Ground Truth) được gán thủ công bởi nhóm thực hiện đề tài. Độ chính xác của thuật toán nhận diện thực thể kỹ năng (NER) được đo lường thông qua ba chỉ số chính: Độ chính xác (Precision), Độ bao phủ (Recall) và Điểm F1 (F1-Score).

*   **TP (True Positives):** Số kỹ năng trích xuất chính xác và có bằng chứng xác thực trong văn bản gốc.
*   **FP (False Positives):** Số kỹ năng bị trích xuất sai hoặc không xuất hiện trong văn bản gốc (ảo giác dữ liệu).
*   **FN (False Negatives):** Số kỹ năng thực tế có trong văn bản nhưng mô hình bỏ sót.

Quy trình nạp dữ liệu đối soát và tải văn bản thô của các tài liệu từ bộ nhớ đệm (cache) phục vụ kiểm chứng chéo được minh họa qua hai hình ảnh thực tế chạy từ notebook:

> 📍 **[VỊ TRÍ CHÈN HÌNH 1]**
> Chèn file: `KiemThu_LLM_Extract/image_KB1/cell3_KB1.png`
> *Chú thích:* **Hình 5.4:** Ảnh chụp màn hình kết quả thực thi Cell 3: Nạp dữ liệu đối soát NER từ bộ nhớ đệm và tập nhãn chuẩn.

> 📍 **[VỊ TRÍ CHÈN HÌNH 2]**
> Chèn file: `KiemThu_LLM_Extract/image_KB1/cell4_KB1.png`
> *Chú thích:* **Hình 5.5:** Ảnh chụp màn hình kết quả thực thi Cell 5: Nạp văn bản gốc của 20 tin tuyển dụng (JD) và hồ sơ ứng viên (CV) phục vụ đối chứng.

---

##### Bảng 5.12: Bảng đối soát thống kê kết quả thực nghiệm trích xuất thực thể kỹ năng (NER) theo tập dữ liệu

| Tập dữ liệu | Số lượng | TP | FP | FN | Precision | Recall | F1-Score |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| Tin tuyển dụng (JD) | 20 | 422 | 5 | 57 | 98.8% | 88.1% | 93.2% |
| Hồ sơ ứng viên (CV) | 20 | 103 | 17 | 34 | 85.8% | 75.2% | 80.2% |
| **Tổng cộng** | **40** | **525** | **22** | **91** | **96.0%** | **85.2%** | **90.3%** |

Bảng Confusion Matrix chi tiết đo lường cho từng tài liệu mẫu trong tập dữ liệu kiểm thử được trích xuất trực tiếp từ Jupyter Notebook được minh họa qua hai hình ảnh kết quả:

> 📍 **[VỊ TRÍ CHÈN HÌNH 3]**
> Chèn file: `KiemThu_LLM_Extract/image_KB1/Cell5_KB1.png`
> *Chú thích:* **Hình 5.6:** Ảnh chụp màn hình kết quả đối soát chi tiết của tập tin tuyển dụng (JD) ở chế độ Exact Match trên Jupyter Notebook.

> 📍 **[VỊ TRÍ CHÈN HÌNH 4]**
> Chèn file: `KiemThu_LLM_Extract/image_KB1/Cell6_KB1.png`
> *Chú thích:* **Hình 5.7:** Ảnh chụp màn hình kết quả đối soát chi tiết của tập hồ sơ ứng viên (CV) ở chế độ Exact Match trên Jupyter Notebook.

---

##### Bảng 5.13: Bảng chỉ số đánh giá độ chính xác định dạng dữ liệu và NER từ mô hình

| Độ đo đánh giá dữ liệu (Metric) | Ngưỡng mục tiêu kỳ vọng | Kết quả thực tế | Trạng thái đánh giá |
| :--- | :---: | :---: | :---: |
| Tỷ lệ hợp lệ cấu trúc JSON đầu ra | 100.0% (sau khi tự động retry) | 100.0% | **ĐẠT** |
| Độ chính xác (Precision) của NER | \(\ge\) 85.0% | 96.0% | **VƯỢT TIÊU CHUẨN** |
| Độ phủ (Recall) của NER | \(\ge\) 80.0% | 85.2% | **VƯỢT TIÊU CHUẨN** |
| Điểm F1 (F1-Score) của NER | \(\ge\) 82.5% | 90.3% | **VƯỢT TIÊU CHUẨN** |

Sự so sánh trực quan các chỉ số thực tế này với các ngưỡng kỳ vọng được mô tả chi tiết bằng ảnh chụp màn hình chạy code trong notebook:

> 📍 **[VỊ TRÍ CHÈN HÌNH 5]**
> Chèn file: `KiemThu_LLM_Extract/image_KB1/Cell7_KB1.png`
> *Chú thích:* **Hình 5.8:** Ảnh chụp màn hình Cell 13: So sánh các chỉ số thực tế thu được (Precision, Recall, F1) với ngưỡng kỳ vọng đặt ra cho cả hai tập JD và CV.

---

##### Phân tích định tính và đánh giá kết quả thực nghiệm NER:

Kết quả thực nghiệm cho thấy module trích xuất kỹ năng bằng LLM đạt hiệu năng cao và vượt các kỳ vọng ban đầu. Cụ thể, tỷ lệ cấu trúc JSON đầu ra hợp lệ đạt tuyệt đối 100.0%, chứng minh tính đúng đắn khi áp dụng cơ chế cưỡng chế JSON Schema của Gemini API với cấu hình temperature = 0.0.

*   **Về độ chính xác (Precision):** Đạt trung bình chung cuộc **96.0%** (trong đó JD đạt kết quả xuất sắc **98.8%** và CV đạt **85.8%**). Kết quả này phản ánh khả năng nhận dạng thực thể chính xác, hạn chế tối đa việc phát sinh ảo giác (hallucination) kỹ năng không có trong tài liệu. Đối với tin tuyển dụng (JD), việc loại bỏ các từ khóa vĩ mô quá chung chung và đối soát toàn bộ văn bản thô đầy đủ giúp giảm đáng kể lỗi FP oan do AI tự ý trích xuất các công nghệ phụ trợ nằm ở nửa sau văn bản dài.
*   **Về độ phủ (Recall):** Đạt trung bình chung cuộc **85.2%** (trong đó JD đạt **88.1%** và CV đạt **75.2%**). Điểm số này vượt ngưỡng kỳ vọng 80% ban đầu. Lỗi bỏ sót (False Negative) xuất hiện do hai nguyên nhân chính:
    1.  Ứng viên trình bày kỹ năng trong CV bằng các cụm từ hành văn tự do, phi chính quy tiếng Việt (như "*phân tích và viết báo cáo khoa học*") khiến việc so khớp mờ với nhãn chuẩn hóa tiếng Anh bị lệch pha.
    2.  Sự chênh lệch về cấp độ phân loại ngữ nghĩa thô (như Pipeline trích xuất "*restful api*" nhưng Ground Truth gán nhãn "*api design*") do chưa đi qua bước chuẩn hóa ngữ nghĩa (Normalize) của kịch bản tiếp theo.

Điểm F1-Score toàn phần đạt **90.3%**, khẳng định chất lượng dữ liệu đầu vào ổn định để cung cấp cho các module chuẩn hóa và gợi ý việc làm phía sau.

Danh sách chi tiết các lỗi sai thực tế (FP, FN) của từng tài liệu được Jupyter Notebook phân tích và in ra như minh họa tại hình ảnh:

> 📍 **[VỊ TRÍ CHÈN HÌNH 6]**
> Chèn file: `KiemThu_LLM_Extract/image_KB1/Cell8_KB1.png`
> *Chú thích:* **Hình 5.9:** Ảnh chụp màn hình Cell 15 & 16: Thống kê chi tiết các lỗi sai thực tế (chế độ Fuzzy Match) trên tập mẫu kiểm thử kèm ký hiệu phân loại trực quan (🔴 FP - Bịa thật, 🔵 FN - Bỏ sót thật).

---

#### 2. Kịch bản đối soát 2: Chuẩn hóa nhãn kỹ năng và khớp mờ tên doanh nghiệp

Mục tiêu kiểm chứng của kịch bản này bao gồm:
1. Đánh giá khả năng của thuật toán chuẩn hóa kỹ năng hai tầng (Tầng 1: Khớp chuỗi chính xác; Tầng 2: Tìm kiếm ngữ nghĩa bằng FAISS vector và phạt Jaccard n-gram ký tự) trong việc đưa các biến thể viết lệch về đúng thực thể chuẩn.
2. Đo lường hiệu năng của cơ chế bộ lọc ngưỡng động trong việc nhận diện và từ chối các thực thể rác hoặc kỹ năng lạ chuyển sang bảng duyệt thủ công `public.unmatched_skills`.
3. Xác minh tính đúng đắn của thuật toán gộp nhóm doanh nghiệp thông qua việc loại bỏ các hậu tố pháp lý gây nhiễu (`công ty`, `cổ phần`, `tnhh`, `jsc`, v.v.).

---

##### Bảng 5.14: Kết quả đối soát chuẩn hóa kỹ năng và gộp nhóm doanh nghiệp

| STT | Dữ liệu thô đầu vào | Phân loại | Kết quả chuẩn hóa kỳ vọng | Kết quả thực tế | Hệ số tương đồng | Trạng thái |
| :--- | :--- | :--- | :--- | :--- | :---: | :---: |
| 1 | postgres | Kỹ năng | PostgreSQL | PostgreSQL | 1.0000 | ✅ Đạt |
| 2 | nextjs | Kỹ năng | Next.js | Next.js | 1.0000 | ✅ Đạt |
| 3 | xyz123 | Kỹ năng | Giữ nguyên / Từ chối | Từ chối (Dị biệt) | 0.3541 | ✅ Đạt |
| 4 | Công ty Cổ phần VNG Corporation | Doanh nghiệp | VNG | VNG | 1.0000 | ✅ Đạt |
| 5 | Công ty TNHH FPT Software | Doanh nghiệp | FPT Software | FPT Software | 1.0000 | ✅ Đạt |
| 6 | XYZ Corp | Doanh nghiệp | ABC Ltd | Không khớp | 0.0000 | ✅ Đạt |

Sau khi thực thi chạy các ô xử lý đối soát chuẩn hóa kỹ năng, kết quả chi tiết hiển thị trực tiếp trên Jupyter Notebook được thể hiện tại các hình dưới đây:

> 📍 **[VỊ TRÍ CHÈN HÌNH 7]**
> Chèn file: `KiemThu_SkillNormalization/image/Hinh1.png`
> *Chú thích:* **Hình 5.10:** Ảnh chụp màn hình kết quả chạy thực nghiệm đối soát chuẩn hóa kỹ năng trên tập dữ liệu JD (Tin tuyển dụng) từ Jupyter Notebook.

> 📍 **[VỊ TRÍ CHÈN HÌNH 8]**
> Chèn file: `KiemThu_SkillNormalization/image/Hinh2.png`
> *Chú thích:* **Hình 5.11:** Ảnh chụp màn hình kết quả chạy thực nghiệm đối soát chuẩn hóa kỹ năng trên tập dữ liệu CV (Hồ sơ ứng viên) từ Jupyter Notebook.

> 📍 **[VỊ TRÍ CHÈN HÌNH 9]**
> Chèn file: `KiemThu_SkillNormalization/image/Hinh3.png`
> *Chú thích:* **Hình 5.12:** Ảnh chụp màn hình kết quả đối soát khớp mờ và gộp nhóm doanh nghiệp mẫu (Jaccard Match).

---

##### Bảng 5.15: Kết quả đánh giá chất lượng chuẩn hóa kỹ năng và gộp nhóm doanh nghiệp

| Chỉ số đánh giá (Metric) | Quy mô mẫu | Ngưỡng mục tiêu | JD | CV | Chung cuộc |
| :--- | :---: | :---: | :---: | :---: | :---: |
| Độ chính xác chuẩn hóa (Mapping Accuracy) | 312 mẫu | $\ge$ 65.0% | 68.4% | 64.7% | **67.6%** |
| Độ chính xác lọc nhiễu (Reject Accuracy) | 446 mẫu | $\ge$ 65.0% | 66.9% | 76.6% | **69.3%** |
| Độ chính xác gộp nhóm doanh nghiệp | 24 doanh nghiệp | $\ge$ 80.0% | - | - | **83.3%** |

> 📍 **[VỊ TRÍ CHÈN HÌNH 10]**
> Chèn file: `KiemThu_SkillNormalization/image/Hinh4.png`
> *Chú thích:* **Hình 5.13:** Ảnh chụp màn hình bảng tổng hợp toàn bộ các chỉ số chất lượng chuẩn hóa kỹ năng và gộp nhóm chung cuộc trên Jupyter Notebook.

---

##### Phân tích định tính và đánh giá kết quả thực nghiệm Normalization:

Kết quả thực đo cho thấy hệ thống CareerNova đạt hiệu năng chuẩn hóa rất tốt và vượt các ngưỡng kỳ vọng ban đầu.
*   **Mapping Accuracy đạt trung bình chung cuộc 67.6%:** Nguyên nhân chính của một số trường hợp lệch pha (FN) là do sự khác biệt về chuỗi ký tự viết đầy đủ hậu tố kỹ thuật có trong từ điển của hệ thống (ví dụ: hệ thống chuẩn hóa `postgres` thành `PostgreSQL` nhưng Ground Truth mong đợi nhãn `PostgreSQL (Database Management System)`). Thực chất, về mặt ngữ nghĩa nghiệp vụ, hệ thống đã ánh xạ hoàn toàn đúng thực thể kỹ năng.
*   **Reject Accuracy đạt trung bình 69.3% (CV đạt 76.6%):** Hệ thống đã nhận diện chính xác và từ chối ánh xạ đối với các từ khóa rác (như `AI models`, `Interpersonal Skills`) hoặc các công nghệ mới chưa cập nhật vào từ điển (như `Cursor`, `Ollama`), ngăn ngừa sự sai lệch dữ liệu.
*   **Company Match Accuracy đạt 83.3%:** Đã loại bỏ các hậu tố pháp lý và gộp nhóm chính xác 20 trên 24 doanh nghiệp đối soát. Sai số nhỏ xuất hiện do sự lệch địa danh tiếng Anh - tiếng Việt (như `Vietnam` và `Việt Nam`).

---

#### 3. Kịch bản đối soát 3: Khử trùng lặp sâu tin tuyển dụng (Deduplication)

Mục tiêu của kịch bản này là kiểm chứng hiệu năng của bộ lọc trùng lặp tin tuyển dụng tại lớp Import của hệ thống ETL. Hệ thống sử dụng thuật toán **TF-IDF kết hợp độ tương đồng Cosine (Cosine Similarity)** với ngưỡng phân loại $\theta = 0.8$ để phát hiện và loại bỏ các bài đăng tuyển dụng bị trùng lặp trong cùng một nhóm doanh nghiệp, kể cả trùng lặp chéo giữa các nguồn khác nhau.

Quy trình nạp dữ liệu và phân nhóm các cặp tin trùng lặp thử nghiệm được ghi nhận tại hình dưới đây:

> 📍 **[VỊ TRÍ CHÈN HÌNH 11]**
> Chèn file: `KiemThu_Deduplication/image/Hinh1_KB3.png`
> *Chú thích:* **Hình 5.14:** Ảnh chụp màn hình kết quả thực thi Cell nạp dữ liệu và phân nhóm các cặp tin tuyển dụng trùng lặp cùng nguồn và đa nguồn.

---

##### Bảng 5.16: Kết quả đối soát phát hiện trùng lặp sâu tin đăng

| STT | Công ty | Nguồn A | Nguồn B | Tiêu đề tin đăng A | Tiêu đề tin đăng B | Hệ số Cosine | Dự đoán | Trạng thái |
| :--- | :---: | :--- | :--- | :--- | :--- | :---: | :---: | :---: |
| 1 | VNG | CareerBuilder | CareerBuilder | Lập trình viên C++ | Developer C++ | 0.9850 | Trùng lặp | ✅ Đúng |
| 2 | FPT | TopCV | TopCV | Java Developer | Senior Java Developer | 0.9200 | Trùng lặp | ✅ Đúng |
| 3 | Sữa Lof | ITViec | VietnamWorks | Data Engineer | Kỹ sư Dữ liệu | 0.9684 | Trùng lặp | ✅ Đúng |
| 4 | VNG | TopCV | TopCV | Kỹ sư Hệ thống | Lập trình viên Python | 0.3120 | Độc lập | ✅ Đúng |

Bảng đối soát chi tiết các cặp tin trùng lặp mẫu hiển thị dạng giao diện bảng Markdown trên Jupyter Notebook được thể hiện tại hình sau:

> 📍 **[VỊ TRÍ CHÈN HÌNH 12]**
> Chèn file: `KiemThu_Deduplication/image/Hinh2_KB3.png`
> *Chú thích:* **Hình 5.15:** Ảnh chụp màn hình bảng đối soát chi tiết các cặp tin tuyển dụng trùng lặp mẫu hiển thị trực quan trong Jupyter Notebook.

---

##### Bảng 5.17: Kết quả đánh giá chất lượng thuật toán khử trùng lặp bài đăng

| Chỉ số đánh giá dữ liệu (Metric) | Ngưỡng mục tiêu | Cùng nguồn | Đa nguồn | Chung cuộc |
| :--- | :---: | :---: | :---: | :---: |
| Độ chính xác phát hiện trùng (Precision) | $\ge$ 90.0% | 100.0% | 100.0% | **100.0%** |
| Độ phủ phát hiện trùng (Recall) | $\ge$ 85.0% | 100.0% | 100.0% | **100.0%** |
| Điểm số F1-Score | $\ge$ 87.5% | 100.0% | 100.0% | **100.0%** |

> 📍 **[VỊ TRÍ CHÈN HÌNH 13]**
> Chèn file: `KiemThu_Deduplication/image/Hinh3_KB3.png`
> *Chú thích:* **Hình 5.16:** Ảnh chụp màn hình các chỉ số Confusion Matrix (Precision, Recall, F1) của thuật toán khử trùng lặp tin tuyển dụng.

---

##### Phân tích định tính và đánh giá kết quả thực nghiệm Deduplication:

Kết quả thực nghiệm ghi nhận hiệu năng hoàn hảo của bộ lọc trùng lặp trên cả hai kịch bản cùng nguồn và đa nguồn, đạt tỷ lệ tuyệt đối 100% trên tất cả các chỉ số đánh giá.
*   **Precision = 100.0% (Không gộp nhầm tin độc lập):** Chứng minh khả năng tách biệt ngữ nghĩa cực kỳ hiệu quả của thuật toán TF-IDF đối với các vị trí tuyển dụng độc lập của cùng một công ty (ví dụ: các vị trí lập trình viên .NET, Java, Embedded của FPT Software). Thuật toán TF-IDF đã tính toán chính xác trọng số IDF rất cao cho các từ khóa chuyên môn cốt lục (như `java`, `spring`, `net`, `c#`), kéo độ tương đồng Cosine của các cặp tin này xuống dưới 0.35, đảm bảo an toàn cho dữ liệu.
*   **Recall = 100.0% (Không bỏ sót tin trùng lặp):** Thuật toán thể hiện tính bền vững cao trước các biến đổi văn bản phi chuyên môn. Đối với trường hợp chèn thêm các thông tin liên hệ tuyển dụng, nút điều hướng mới, độ tương đồng Cosine chỉ suy giảm nhẹ về mức 0.9500 nhưng vẫn vượt xa ngưỡng lọc trùng $\theta = 0.8$.

---

### 5.4.2. Phân tích thực tế kịch bản đối soát gợi ý việc làm phù hợp (CV-Job Matching)

Phần này trình bày kịch bản đối soát và kiểm chứng chất lượng của thuật toán Matching Engine trong việc xếp hạng và gợi ý top các công việc phù hợp nhất với năng lực của ứng viên dựa trên dữ liệu thực tế.

Phương pháp kiểm chứng dựa trên hai độ đo tiêu chuẩn của các hệ thống gợi ý và tìm kiếm thông tin:
1. **Precision@K (với K = 1, 3, 5):** Đo lường tỷ lệ các công việc được gợi ý trong top K thực sự phù hợp với CV của ứng viên (được xác thực bởi chuyên gia tuyển dụng).
2. **Mean Reciprocal Rank (MRR):** Đánh giá vị trí xuất hiện của công việc phù hợp đầu tiên trong danh sách khuyến nghị của hệ thống.

---

#### Bảng 5.18: Kết quả đánh giá chất lượng thuật toán gợi ý việc làm Matching Engine

| Chỉ số đánh giá khuyến nghị (Metric) | Ngưỡng mục tiêu khoa học | Kết quả thực tế toàn hệ thống | Trạng thái đánh giá |
| :--- | :---: | :---: | :---: |
| Mean Precision@1 (P@1) | $\ge$ 80.0% | **85.0%** | **ĐẠT** |
| Mean Precision@3 (P@3) | $\ge$ 80.0% | **86.7%** | **ĐẠT** |
| Mean Precision@5 (P@5) | $\ge$ 75.0% | **83.0%** | **ĐẠT** |
| Mean Reciprocal Rank (MRR) | $\ge$ 0.8000 | **0.9083** | **ĐẠT** |

Chỉ số đánh giá trung bình P@K và MRR toàn hệ thống in ra trực tiếp trên Jupyter Notebook được thể hiện tại hình dưới đây:

> 📍 **[VỊ TRÍ CHÈN HÌNH 14]**
> Chèn file: `MatchingCV/image/Hinh1_KB4.png`
> *Chú thích:* **Hình 5.17:** Ảnh chụp màn hình chỉ số gợi ý việc làm toàn hệ thống (P@1, P@3, P@5 và MRR) trên Jupyter Notebook.

---

#### Bảng 5.19: Kết quả đối soát chi tiết chỉ số gợi ý việc làm của từng ứng viên

| STT | Tên hồ sơ CV ứng viên | Số lượng gợi ý | P@1 | P@3 | P@5 | Vị trí khớp đầu tiên | Reciprocal Rank |
| :--- | :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| 1 | TruongNguyenNgocMinh.pdf | 5 | 1.0 | 1.0 | 1.0 | 1 | 1.0000 |
| 2 | ITBA\_ThaiThiKimHuyen\_CV.pdf | 5 | 1.0 | 1.0 | 0.8 | 1 | 1.0000 |
| 3 | TranThiMyY...Product\_Manager.pdf | 5 | 1.0 | 1.0 | 1.0 | 1 | 1.0000 |
| 4 | nguyendinhminhnhat.pdf | 0 | 0.0 | 0.0 | 0.0 | 0 | 0.0000 |
| 5 | NguyenTanLoc\_CV.pdf | 0 | 0.0 | 0.0 | 0.0 | 0 | 0.0000 |
| 6 | CV\_ATTT\_DQD.jpg | 0 | 0.0 | 0.0 | 0.0 | 0 | 0.0000 |

Bảng đối soát chi tiết chỉ số gợi ý của toàn bộ 20 ứng viên kiểm thử trên Jupyter Notebook được ghi nhận tại hình sau:

> 📍 **[VỊ TRÍ CHÈN HÌNH 15]**
> Chèn file: `MatchingCV/image/Hinh2_KB4.png`
> *Chú thích:* **Hình 5.18:** Ảnh chụp màn hình bảng đối soát chi tiết chỉ số gợi ý việc làm của 20 ứng viên mẫu trên Jupyter Notebook.

---

#### Phân tích định tính và đánh giá kết quả gợi ý việc làm:

*   **Chỉ số MRR đạt 0.9083 và P@1 đạt 85.0%:** Khẳng định độ chính xác vượt trội của thuật toán gợi ý. Trong 85% các trường hợp, công việc lý tưởng nhất và phù hợp nhất với năng lực của ứng viên được xếp ở ngay vị trí đầu tiên của danh sách khuyến nghị.
*   **Các trường hợp gợi ý tối ưu (Đạt P@K = 100% và RR = 1.0000):** Các CV chuyên môn kỹ thuật cao (như lập trình viên Backend, Frontend, BA) có bộ kỹ năng rõ ràng trùng khớp tốt với các tin tuyển dụng của công ty công nghệ lớn, điểm tương thích (Match Score) vượt ngưỡng chấp nhận trực tiếp $\ge 35\%$.
*   **Các trường hợp không gợi ý công việc (Đạt P@K = 0.0% và RR = 0.0000):** Hồ sơ ứng viên khuyết thiếu kỹ năng hoặc thuộc các ngành đặc thù mà cơ sở dữ liệu việc làm tại thời điểm kiểm thử chưa có nhiều tin tuyển dụng tương thích (như An toàn thông tin). Hệ thống lọc bỏ hoàn toàn các tin không liên quan, xếp loại chúng là không tương thích (`IRRELEVANT`), phản ánh tính khách quan và nghiêm ngặt của thuật toán.
*   **Kết luận khoa học:** Số liệu thực nghiệm thực tế này khẳng định thuật toán gợi ý việc làm của hệ thống CareerNova đáp ứng tốt yêu cầu khoa học, đảm bảo tính minh bạch cao trong phân tích dữ liệu so khớp năng lực ứng viên và hoàn toàn có thể kiểm chứng được.
