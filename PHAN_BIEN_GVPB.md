# NHẬN XÉT PHẢN BIỆN KHÓA LUẬN TỐT NGHIỆP

**Đề tài:** Đề xuất khung phân tích hỗ trợ sinh viên phân tích dữ liệu tuyển dụng (Hệ thống CareerNova)
**Sinh viên:** Thái Thị Kim Huyền – Trần Thị Mỹ Ý
**Vai trò nhận xét:** Giảng viên phản biện (luận án hướng ứng dụng)

---

## A. NHẬN XÉT TỔNG QUAN

Đây là một khóa luận hướng ứng dụng **có khối lượng công việc lớn và mức độ hoàn thiện kỹ thuật cao**: hệ thống được triển khai thật (career-nova.online), có dữ liệu thật (7.245 tin), có đo đạc kèm bằng chứng thô (ảnh psql, terminal), có ma trận truy vết yêu cầu – kiểm thử, và trung thực khai báo phạm vi kiểm thử. Chuỗi kỹ thuật ETL → LLM Structured Outputs + hậu kiểm bằng chứng → SBERT/FAISS + trọng số thị trường → trực quan hóa là một thiết kế hợp lý, được lập luận có căn cứ.

Tuy nhiên, ở tư cách phản biện, khóa luận còn **ba nhóm điểm yếu chính** cần chỉnh sửa trước khi bảo vệ: (1) **mâu thuẫn và thiếu chặt chẽ trong số liệu thực nghiệm** (nhiều chỉ tiêu không đạt ngưỡng nhưng phần lời văn vẫn kết luận "vượt kỳ vọng"); (2) **phương pháp đánh giá thiếu tính khách quan** (nhóm tự gán nhãn, tự chấm, không có baseline so sánh, không có phân tích độ nhạy ngưỡng); (3) **ngôn ngữ quá khẳng định** ("đột phá", "hoàn hảo", "tuyệt đối", "chứng minh") không phù hợp văn phong học thuật và dễ bị hội đồng khai thác.

---

## B. CÁC VẤN ĐỀ TRỌNG YẾU (BẮT BUỘC CHỈNH SỬA)

### B1. Mâu thuẫn giữa số liệu và kết luận trong Chương 5

1. **Recall và F1 KHÔNG đạt ngưỡng nhưng lời văn nói "đạt hiệu năng cao và rất ổn định".** Bảng chỉ số NER đặt mục tiêu Recall ≥ 80,0% và F1 ≥ 82,5%; kết quả thực tế là 77,4% và 82,0% — **hai trong bốn chỉ tiêu không đạt**. Phần Tóm tắt và Chương 6 lại trình bày các con số này như thành tựu thuần túy, không nhắc việc trượt ngưỡng. Phải sửa lời văn thành "2/4 chỉ tiêu đạt, Recall và F1 tiệm cận ngưỡng, nguyên nhân do…" — trung thực trước, biện luận sau.

2. **Mapping Accuracy: tập CV đạt 64,7% < ngưỡng 65,0% nhưng lời văn viết "vượt các ngưỡng kỳ vọng ban đầu".** Chỉ số chung cuộc 67,6% vượt ngưỡng, nhưng tập con CV trượt ngưỡng — cần nêu rõ, không được gộp để che.

3. **Mâu thuẫn quy mô tập đối soát.** Mở đầu Mục 5.4 và Tóm tắt nói tập chuẩn gồm **100 tài liệu (50 CV + 50 JD)**; nhưng đánh giá NER chỉ dùng **40 tài liệu (20 JD + 20 CV)**; đối soát chuẩn hóa dùng 758 mẫu thô "của 20 JD và 20 CV"; đối soát doanh nghiệp lúc là "20 cặp", lúc kết quả tính trên "24 doanh nghiệp". Kịch bản 4 (Pearson) lại quay về "100 bài đăng". Người phản biện không thể xác định tập nào dùng cho phép đo nào. **Cần một bảng tổng hợp duy nhất mô tả các tập dữ liệu đánh giá: kích thước, nguồn gốc, ai gán nhãn, dùng cho thí nghiệm nào.**

4. **Ngưỡng mục tiêu có dấu hiệu "đặt sau khi có kết quả" (post-hoc).** Mapping Accuracy đặt mục tiêu ≥ 65% — một ngưỡng thấp bất thường và vừa khít kết quả. Nếu ngưỡng có căn cứ (từ công trình nào, từ yêu cầu nghiệp vụ nào), phải trích dẫn; nếu không, thừa nhận là ngưỡng nội bộ do nhóm tự đặt.

5. **Kết quả khử trùng lặp 100/100/100% trên 52 cặp, trong đó một phần là dữ liệu "giả lập".** Kết luận "hiệu năng hoàn hảo", "an toàn tuyệt đối cho tính nguyên vẹn dữ liệu" là quá lời với một tập kiểm thử nhỏ, một phần tự sinh, chỉ 3 doanh nghiệp. Cần viết lại thành: kết quả 100% **trên tập đối soát giới hạn này**, chưa đủ để khẳng định tổng quát; nêu rõ tỷ lệ cặp thật/giả lập.

### B2. Tính khách quan của phương pháp đánh giá

6. **Nhãn chuẩn (Ground Truth) do chính nhóm thực hiện đề tài gán, và điểm Y_i trong tương quan Pearson cũng do nhóm chấm.** Mục 5.4 còn viết đo "mức độ tương đồng giữa tư duy đánh giá của thuật toán và **chuyên gia nhân sự**" — trong khi người chấm là sinh viên làm đề tài, không phải chuyên gia nhân sự. Đây là lỗi nghiêm trọng về tính khách quan:
   - Sửa ngay cụm "chuyên gia nhân sự" thành đúng thực tế.
   - Bổ sung quy trình gán nhãn: gán độc lập bởi ≥ 2 người, báo cáo độ đồng thuận (Cohen's kappa hoặc tỷ lệ nhất trí), quy tắc giải quyết bất đồng. Nếu không kịp làm, phải ghi rõ vào "Hạn chế" như một threat to validity, không được im lặng.

7. **Thiếu hoàn toàn baseline so sánh.** Luận văn phê phán exact keyword matching (Chương 1, 2) và đề xuất giải pháp lai, nhưng **không có thí nghiệm nào so sánh** Match Score của CareerNova với: (a) khớp từ khóa chính xác, (b) TF-IDF thuần, (c) SBERT không trọng số/không luật lọc. Không có so sánh này thì không chứng minh được đóng góp của từng thành phần. Tối thiểu cần một ablation nhỏ: Pearson r của hệ thống đầy đủ vs. hệ thống tắt 6 luật lọc vs. keyword matching, trên cùng tập đối soát.

8. **Các chỉ số 88,6% (độ chính xác gợi ý Gap) và 82,4% (gợi ý tài liệu học tập) không có định nghĩa toán học.** Precision/Recall/F1 và Pearson đều có công thức, nhưng hai chỉ số quan trọng nhất với người dùng cuối lại không định nghĩa thế nào là "gợi ý đúng", đếm trên đơn vị nào (kỹ năng? báo cáo? khóa học?). Phải bổ sung định nghĩa và cách đếm.

9. **Nguy cơ vòng lặp luẩn quẩn giữa cơ chế anti-hallucination và cách tính Precision.** TP được định nghĩa là kỹ năng "có bằng chứng xác thực trong văn bản gốc" — trong khi pipeline đã tự động loại mọi kỹ năng không có evidence khớp chuỗi. Như vậy Precision đo sau bộ lọc sẽ tự nhiên cao. Cần nói rõ Precision được đo **trước hay sau** tầng hậu kiểm; lý tưởng là báo cáo cả hai để chứng minh giá trị của tầng hậu kiểm.

### B3. Điểm yếu phương pháp cần biện luận hoặc thí nghiệm bổ sung

10. **"TF-IDF động" thực chất chỉ là trọng số IDF.** Vì TF được định nghĩa nhị phân (kỹ năng có/không trong JD), tích TF×IDF luôn bằng IDF với mọi kỹ năng có mặt. Việc gọi là "TF-IDF" không sai nhưng dễ gây hiểu lầm về đóng góp; nên thừa nhận thẳng: "với TF nhị phân, trọng số quy về IDF" và giải thích vì sao phù hợp với dữ liệu dạng danh sách kỹ năng.

11. **Luật 6 (Soft Skills Direct Match) quá mạnh và thiếu kiểm chứng.** Hai kỹ năng mềm bất kỳ có cosine > 0,35 được nâng lên khớp **hoàn toàn (1,0)** — nghĩa là "Communication" được tính tương đương "Teamwork", "Leadership"… với trọng số đầy đủ. Trong Case Study, chính luật này cộng thêm 10 điểm phần trăm. Câu hỏi hội đồng chắc chắn sẽ hỏi: căn cứ nào cho ngưỡng 0,35 và cho việc làm tròn lên 1,0? Cần: (a) biện luận nghiệp vụ, (b) phân tích độ nhạy (score thay đổi thế nào nếu bỏ luật này), hoặc (c) hạ mức nâng (ví dụ nâng lên 0,8 thay vì 1,0).

12. **Luật 1 (Certification Exclusivity) như đang viết sẽ khiến chứng chỉ KHÔNG BAO GIỜ khớp được, kể cả khi ứng viên có đúng chứng chỉ đó.** "Nếu một trong hai kỹ năng thuộc nhóm Chứng chỉ, ép độ tương đồng về 0.0" — vậy ứng viên ghi "AWS Certified Cloud Practitioner" trong CV vẫn bị chấm 0 với yêu cầu chứng chỉ AWS? Nếu thực tế có nhánh khớp chính xác theo ID/tên trước khi áp luật, phải viết rõ vào mô tả thuật toán; nếu không có, đây là lỗi logic thật.

13. **Các ngưỡng phân loại 0,75/0,45 và hệ số boost ×1,2 không có căn cứ.** Không có thí nghiệm chọn ngưỡng, không phân tích độ nhạy. Ít nhất cần một đoạn giải thích cách chọn (thử nghiệm trên tập dev? tham khảo tài liệu nào?).

14. **Kiểm chứng bằng chứng theo khớp chuỗi con (substring) là giòn.** OCR sai một ký tự, hoặc LLM chuẩn hóa lại dấu câu, là evidence bị loại oan → làm giảm Recall (mà Recall đang trượt ngưỡng). Nên bàn về fuzzy matching cho evidence như hướng cải tiến, và định lượng bao nhiêu % FN do nguyên nhân này.

15. **Đo hiệu năng cache-miss có điểm khả nghi.** Mục 5.3.2 nói đo 20 lượt cache-miss trên "20 bản CV tải lên độc lập" nhưng lại ghi "điểm số ổn định (khoảng 0,57)" cho cả 20 lượt. Nếu 20 CV khác nhau thì điểm khó lòng cùng ≈ 0,57; nếu là cùng một nội dung CV thì cơ chế cache theo nội dung văn bản đã phải kích hoạt (cache-hit). Cần mô tả rõ 20 CV này khác nhau thế nào và vì sao không dính cache.

### B4. Pháp lý, đạo đức dữ liệu — hội đồng sẽ hỏi

16. **Mâu thuẫn giữa "vượt WAF/Cloudflare, Undetected ChromeDriver, xoay vòng proxy" và "tuân thủ điều khoản sử dụng, robots.txt".** Chương 2 mô tả chi tiết kỹ thuật né tránh cơ chế chống bot của chính các nền tảng bị thu thập (LinkedIn cấm scraping trong ToS), rồi cùng đoạn lại nói hệ thống tuân thủ ToS. Hai điều này không thể cùng đúng. Khuyến nghị: (a) chuyển phần bypass thành trình bày kỹ thuật trung tính kèm giới hạn pháp lý rõ ràng; (b) đưa hẳn một mục "Cân nhắc pháp lý và đạo đức thu thập dữ liệu" nêu rate-limit, mục đích học thuật, không tái phân phối dữ liệu thô — hiện chỉ có một gạch đầu dòng trong Hạn chế là chưa đủ.

17. **Dữ liệu cá nhân trong CV được gửi lên Gemini API (bên thứ ba) — chưa có dòng nào bàn về quyền riêng tư.** CV chứa họ tên, email, số điện thoại, quá trình làm việc. Cần bổ sung: có ẩn danh hóa/loại PII trước khi gửi không, người dùng có được thông báo không, đối chiếu Nghị định 13/2023/NĐ-CP về bảo vệ dữ liệu cá nhân. Đây là câu hỏi rất dễ bị hỏi ở buổi bảo vệ với một hệ thống đã chạy công khai.

### B5. Tính nhất quán nội tại của tài liệu

18. **Bảng `users` mâu thuẫn với mô tả.** Lời dẫn ghi bảng lưu "sinh viên và quản trị viên hệ thống" nhưng ràng buộc là `CHECK (role IN ('student'))` — không thể tồn tại quản trị viên. Sửa một trong hai.

19. **Hai định nghĩa trọng số chưa được nối với nhau.** Chương 2 định nghĩa w(s_i, d_j) = TF×IDF tính "thời gian thực" theo từng JD; Chương 3–4 lại dùng bảng `job_group_skill_weights` tính sẵn theo nhóm ngành với ràng buộc Σw=1. Quan hệ giữa hai công thức (chuẩn hóa IDF về tổng 1 theo nhóm? tính lại khi nào?) chưa được trình bày. Cần một đoạn nêu rõ pipeline tính `weight_wi` từ IDF.

20. **Mâu thuẫn mức độ khẳng định về Structured Outputs.** Chương 2 viết thận trọng ("hướng mô hình… giảm lỗi phân tích cú pháp"), Chương 4 viết