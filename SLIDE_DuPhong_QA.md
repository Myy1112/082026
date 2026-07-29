# SLIDE DỰ PHÒNG & KỊCH BẢN TRẢ LỜI PHẢN BIỆN — CareerNova

> Dùng khi hội đồng/GVPB hỏi sâu. Mỗi mục = 1 slide dự phòng (D1–D10, đã có trong file .pptx) + **câu trả lời mẫu** để nói.
> Nguyên tắc: **trung thực trước, biện luận sau**; nếu chưa làm kịp → thừa nhận là hạn chế + nêu ngay phương án. Không dùng "hoàn hảo/tuyệt đối/vượt kỳ vọng".

---

## D1 — Baseline & Ablation (câu hỏi gần như CHẮC CHẮN bị hỏi)

**Hội đồng sẽ hỏi:** "Các em nói giải pháp lai tốt hơn khớp từ khóa / SBERT thuần — có đo đối chứng không?"

**Trả lời mẫu:**
> Dạ, hiện nhóm chưa chạy đầy đủ thí nghiệm đối chứng, và nhóm ghi nhận đây là một hạn chế. Phương án nhóm đề xuất là chạy ablation trên cùng tập nhãn 20 JD + 20 CV với ba cấu hình: (1) chỉ khớp từ khóa; (2) SBERT thuần không trọng số, không luật; (3) hệ thống đầy đủ. Kỳ vọng thứ tự (3) > (2) > (1) sẽ tách bạch được đóng góp của trọng số IDF và bộ 6 luật. Tối thiểu, chỉ cần bật/tắt trọng số IDF cũng cho thấy tác dụng của nó.

**Nếu bị hỏi "vì sao chưa làm":** thời gian có hạn, nhóm ưu tiên hoàn thiện và triển khai hệ thống thật cùng bộ kiểm thử tái lập được; ablation là bước đánh giá tiếp theo.

---

## D2 — Căn cứ chọn ngưỡng & hệ số

**Hỏi:** "Các ngưỡng 0,75 / 0,45 / 0,55, boost ×1,2, soft-skill 0,35 lấy ở đâu ra?"

**Trả lời mẫu:**
> Đây là các tham số vận hành thật trong mã nguồn: phân loại 0,75/0,45, sàn cosine 0,55, hybrid 0,85+0,15, ngưỡng động 0,80/0,70, boost ×1,2, khử trùng lặp θ=0,8. Cơ sở lựa chọn là trực giác về thang Cosine của SBERT kết hợp thử nghiệm sơ bộ trên tập dev. Nhóm thành thật là **chưa grid-search toàn diện**, và xem phân tích độ nhạy ngưỡng là hướng cải tiến — ví dụ quét 0,70/0,75/0,80 để xem độ chính xác thay đổi ra sao.

**Về luật soft-skill (>0,35 → 1,0):** nhóm thừa nhận nâng thẳng lên 1,0 có thể thổi phồng điểm; phương án là **hạ trần xuống tối đa 0,85** hoặc giữ nguyên giá trị cosine.

---

## D3 — Luật chứng chỉ & thứ tự 6 luật

**Hỏi:** "Luật ép chứng chỉ về 0 nghĩa là ứng viên có đúng chứng chỉ vẫn bị chấm 0?"

**Trả lời mẫu:**
> Dạ không. Trước khi áp luật ép-0, hệ thống có nhánh **khớp chính xác theo tên/ID chứng chỉ**; nếu ứng viên có đúng chứng chỉ thì vẫn được tính khớp. Luật ép-0 chỉ chi phối khi *hai kỹ năng thuộc hai nhóm phân loại khác nhau* (ví dụ một bên là chứng chỉ, một bên là kỹ năng thường) để tránh khớp nhầm chéo nhóm. 6 luật áp dụng tuần tự, có short-circuit. Nhóm cũng ghi nhận rủi ro phạt oan kỹ năng liên quan chéo và cân nhắc nới luật.

---

## D4 — Quyền riêng tư dữ liệu CV (PII) — câu dễ bị hỏi với hệ thống chạy công khai

**Hỏi:** "CV chứa thông tin cá nhân, các em gửi lên Gemini — có vi phạm quyền riêng tư không?"

**Trả lời mẫu:**
> Nhóm ý thức CV chứa PII (họ tên, email, SĐT, quá trình làm việc) và hiện được gửi tới Gemini API. Ở phiên bản này nhóm **chưa ẩn danh hóa PII trước khi gửi**, và nhóm nhìn nhận đây là một hạn chế. Về mặt sử dụng: dữ liệu chỉ phục vụ mục đích học thuật, không tái phân phối, và người dùng chủ động tải CV lên. Hướng khắc phục là loại/ẩn danh PII trước khi gửi, thông báo và xin đồng ý minh bạch, đối chiếu **Nghị định 13/2023/NĐ-CP** về bảo vệ dữ liệu cá nhân.

---

## D5 — Pháp lý & đạo đức thu thập dữ liệu

**Hỏi:** "Các em mô tả kỹ thuật vượt anti-bot, vậy có tuân thủ điều khoản của các trang không?"

**Trả lời mẫu:**
> Nhóm trình bày kỹ thuật thu thập ở góc độ trung tính, mục đích học thuật và phi thương mại. Nhóm áp rate-limit hợp lý, **không tái phân phối dữ liệu thô**, chỉ lưu dữ liệu tổng hợp phục vụ phân tích. Nhóm thừa nhận một số nền tảng hạn chế scraping trong điều khoản sử dụng; hướng đi bền vững là ưu tiên các nguồn có API hoặc cho phép, hoặc thỏa thuận sử dụng dữ liệu.

---

## D6 — Tổng quan bộ dữ liệu đánh giá (giải quyết "cỡ mẫu đá nhau")

**Hỏi:** "Rốt cuộc các em đánh giá trên bao nhiêu mẫu? Chỗ nói 100, chỗ nói 40..."

**Trả lời mẫu (chỉ vào bảng D6):**
> Mỗi thí nghiệm dùng một tập nhãn riêng phù hợp với thuật toán:
> - Trích xuất NER: **20 JD + 20 CV** (40 tài liệu, gán nhãn cấp thực thể).
> - Chuẩn hóa kỹ năng: **758 mẫu** (312 mẫu có nghĩa để đo mapping + 446 mẫu nhiễu để đo reject) + **24 công ty**.
> - Khử trùng lặp: **17 tin → 52 cặp** (17 cùng nguồn + 35 đa nguồn, có cặp giả lập).
> - Phân loại Skill Gap: **10 CV** (290 cặp kỹ năng).
> Con số "100" ở bản nháp trước là mục tiêu ban đầu; nhóm đã khớp lại toàn bộ theo dữ liệu thật tái lập được trong thư mục KiemThu/.

---

## D7 — Định nghĩa chỉ số & "TF-IDF động"

**Hỏi 1:** "88,6% và 82,4% định nghĩa thế nào?" → **Lưu ý:** hai số này đã bị GỠ khỏi luận (không có nguồn). Nếu bị hỏi, trả lời:
> Nhóm đã rà soát và gỡ hai chỉ số đó vì không truy vết được nguồn. Thay vào đó, chất lượng gợi ý được đánh giá qua các chỉ số có định nghĩa toán học rõ ràng: Precision/Recall/F1 (NER), Mapping/Reject Accuracy (chuẩn hóa), và Classification Accuracy + Macro-F1 + Match Score MAE (Skill Gap).

**Hỏi 2:** "Gọi TF-IDF nhưng TF nhị phân thì có phải TF-IDF không?"
> Đúng là với TF nhị phân (kỹ năng có/không trong JD), tích TF×IDF quy về IDF. Nhóm dùng cách này vì dữ liệu là *danh sách kỹ năng* — mỗi kỹ năng xuất hiện một lần, không có tần suất lặp — nên trọng số theo độ hiếm (IDF) là phù hợp. Nhóm sẵn sàng gọi chính xác là "trọng số IDF theo thị trường".

---

## D8 — Thiết kế CSDL (ERD)
**Dùng khi hỏi về mô hình dữ liệu.** Chỉ vào ERD; nhấn: bảng `jobs`, `companies`, `skills`, `job_skills`, `user_cvs`, `user_cv_skills`, `cv_job_matches`, `job_group_skill_weights`.
**Lưu ý sửa mâu thuẫn:** bảng `users` — nếu bị hỏi vai trò, nói rõ hiện chỉ có role `student` (ràng buộc CHECK), không có admin ở tầng dữ liệu.

## D9 — Use Case tổng quát
**Dùng khi hỏi phạm vi chức năng.** Nhấn 4 nhóm: xác thực; quản lý CV; đối soát năng lực; khai thác dữ liệu thị trường.

---

## D10 — Case Study (chứng minh Match Score hợp lý)

**Dùng khi hỏi "điểm số có đáng tin không".**
> Ví dụ ứng viên tốt nhất trong tập, ứng tuyển nhóm Information Security Consultant (28 kỹ năng yêu cầu): hệ thống phân loại đúng 75%, Match Score hệ thống 34% so với người chấm 25%, độ lệch MAE 0,09 — đạt ngưỡng. Toàn bộ 7 ca sai đều là "khớp một phần" bị trả về "thiếu" — đúng nguyên nhân CSDL nhị phân đã nêu. Quan trọng: không có ca nào sai theo chiều ngược lại (thiếu → đã có), chứng tỏ sàn lọc cosine ≥ 0,55 hoạt động an toàn, không tạo khớp giả.

---

## CÂU HỎI KHÁC CÓ THỂ GẶP (không có slide riêng)

| Câu hỏi | Ý trả lời cốt lõi |
|---|---|
| **"Recall 73% nghĩa là bỏ sót 27% kỹ năng, ảnh hưởng gì?"** | Có thể tạo "khoảng trống giả" khiến SV học nhầm; nhóm ghi ở 6.2. Bước chuẩn hóa phía sau quy các biến thể về cùng thực thể nên Recall thực tế của toàn hệ cao hơn bước NER thô. Hướng khắc phục: fuzzy match cho bằng chứng. |
| **"Vì sao đóng góp mới, không phải chỉ ghép công cụ có sẵn?"** | Tách bạch: *tích hợp kỹ thuật* (Gemini/SBERT/FAISS) vs *3 đóng góp riêng*: (i) hậu kiểm evidence-based, (ii) trọng số IDF động từ thị trường VN, (iii) 6 luật lọc ngữ nghĩa. |
| **"Khảo sát n=9 có ý nghĩa thống kê không?"** | Không — nhóm nêu rõ là khảo sát *định hình* (formative), cỡ mẫu nhỏ, chỉ định hướng cải tiến, không suy rộng. |
| **"Cache-miss 20 CV mà điểm đều ~0,57?"** | 20 CV khác nhau nhưng cùng nhóm nghề mục tiêu (software engineer) nên điểm gần nhau là hợp lý; cache theo nội dung nên 20 CV độc lập đều là cache-miss thật. |
| **"Số jobs 7.245 nhưng Dashboard hiển thị ít hơn?"** | Backend giữ toàn bộ tin (kể cả hết hạn) để phân tích xu hướng/tính IDF; Dashboard chỉ hiển thị tin còn hiệu lực + lọc mặc định 30 ngày. |
| **"Vì sao dedup 100% mà vẫn coi là hạn chế?"** | Tập nhỏ 52 cặp, có cặp giả lập, chỉ 3 doanh nghiệp → là kiểm chứng tính đúng đắn, chưa phải ước lượng tổng quát. |

---

## CHECKLIST TRƯỚC BUỔI BẢO VỆ (phản biện)
- [ ] Mở sẵn thư mục `KiemThu/` để **tái lập số tại chỗ** nếu hội đồng yêu cầu.
- [ ] Đọc kỹ 3 bài báo đã trích (SkillSpan, Bhola COLING 2020, Khaouja IEEE Access 2021).
- [ ] Thuộc 3 đóng góp riêng của nhóm (hậu kiểm / IDF động / 6 luật).
- [ ] Nhớ: nhãn do **nhóm** gán (không nói "chuyên gia nhân sự").
- [ ] Thuộc nguyên nhân Skill Gap 54,8% (CSDL nhị phân, thiếu Partial) — đây là câu hay bị hỏi nhất.
