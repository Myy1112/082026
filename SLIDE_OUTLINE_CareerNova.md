# BỐ CỤC SLIDE BÁO CÁO KHÓA LUẬN — CareerNova

**Đề tài:** Đề xuất khung phân tích hỗ trợ sinh viên phân tích dữ liệu tuyển dụng (Hệ thống CareerNova)
**SV:** Thái Thị Kim Huyền (22127169) – Trần Thị Mỹ Ý (22127468) · **GVHD:** TS. Vũ Thị Mỹ Hằng
**Định dạng mục tiêu:** ~20 slide nội dung (trong quy định 15–20) · 20 phút trình bày + 10 phút demo (video quay sẵn)

---

## PHẦN 0 — NGUYÊN TẮC THIẾT KẾ (đọc trước khi làm slide)

### 0.1. Yêu cầu bắt buộc từ Quy định + GV phản biện
| Nguồn | Yêu cầu | Cách áp dụng trong bộ slide này |
|---|---|---|
| Quy định slide | 15–20 slide, 15–20 phút, còn lại hỏi đáp | Bộ này ~20 slide chính + slide dự phòng (không tính giờ) |
| Quy định slide | Cô đọng, **ưu tiên hình ảnh & sơ đồ**, tối đa 2 dòng/gạch đầu dòng | Mỗi slide 1 hình/sơ đồ chủ đạo, chữ tối thiểu |
| Quy định slide | Cấu trúc giống cuốn: giới thiệu → động lực → nội dung từng phần → kết luận | Đúng thứ tự 5 phần bên dưới |
| Quy định slide | "Kể lại câu chuyện làm luận văn", trình bày **điều quan trọng nhất VỚI NGƯỜI NGHE** | Mở đầu bằng thách thức của SV CNTT, xuyên suốt bám "giúp người dùng điều gì" |
| Quy định slide | Ghi nguồn tham khảo, độ tương phản cao, **không lạm dụng animation** | Footer ghi nguồn ở slide khảo sát; theme tương phản cao |
| GV phản biện TTDATN | Trình bày **điều tâm đắc nhất** + **tự đánh giá hạn chế** (20') rồi demo chức năng tốt nhất (10') | Phần IV (Kết quả) + Phần V (slide "Điều tâm đắc" & "Hạn chế") + kịch bản demo |
| Quy định | **Tất cả thành viên phải trình bày** · **Quay video demo trước** | Đã chia người trình bày theo từng slide; demo là clip |

### 0.2. "Gu" của cô Hằng — rút từ feedback bộ slide năm ngoái (cùng GVHD)
> Đây là lợi thế lớn: bám đúng các điểm này gần như chắc chắn được cô đánh giá cao.

1. **Luôn giải thích TẠI SAO chọn** (vì sao dùng LLM + hậu kiểm? vì sao SBERT chứ không keyword? vì sao ngưỡng này?). *Năm ngoái cô hỏi liên tục "vì sao galaxy schema", "vì sao lọc từ 2009".*
2. **Liên kết kết quả/kết luận với mục tiêu phía sau** — mỗi con số phải nói rõ "chứng minh được điều gì cho đề tài".
3. **Bảng test case: Input → Kết quả kỳ vọng (tính thủ công) → Kết quả thực tế** để chứng minh tính chính xác (cô yêu cầu 3 lần trong comment).
4. **Slide demo/kết quả: nêu rõ Đầu vào (thao tác) → Đầu ra (biểu đồ)**; nên demo trực tiếp hoặc quay video.
5. **Bỏ slide có kết quả không tốt**, đẩy chi tiết dài (bảng, use case) **vào phụ lục**.
6. **Thêm mô tả "đóng góp lớn nhất" cho mỗi bước** của phương pháp.

### 0.3. Điểm phản biện đã biết trước → xử lý trong slide (KHÔNG né tránh)
GV phản biện đã liệt kê các lỗi. Chiến thuật: **chủ động thừa nhận ở slide "Hạn chế"** và **thủ slide dự phòng**. Điều này biến điểm yếu thành điểm cộng về sự trung thực học thuật (đúng tinh thần cô muốn).

- Recall 77,4% / F1 82,0% **chưa đạt ngưỡng** → nói thẳng "2/4 chỉ tiêu tiệm cận ngưỡng", không tô hồng.
- Mapping Accuracy tập CV 64,7% < 65% → nêu rõ, không gộp che.
- Nhãn chuẩn do **nhóm tự gán** (không phải "chuyên gia nhân sự") → sửa cách gọi, ghi vào hạn chế (threat to validity).
- **Thiếu baseline** (keyword / TF-IDF / SBERT thuần) → thừa nhận + để slide dự phòng có ablation nếu kịp làm.
- **Dữ liệu CV gửi Gemini (bên thứ 3)** → chuẩn bị slide dự phòng về quyền riêng tư (Nghị định 13/2023).
- **Pháp lý crawl** (bypass anti-bot vs. tuân thủ ToS) → slide dự phòng "cân nhắc pháp lý & đạo đức".
- Luật 6 (soft skill nâng lên 1,0) & Luật 1 (chứng chỉ) → slide dự phòng giải thích logic + độ nhạy.
- Bỏ mọi từ "đột phá / hoàn hảo / tuyệt đối / chứng minh" khỏi slide.

### 0.4. Phân vai trình bày (ĐÃ CHỐT — nguyên tắc "ai làm phần nào nói phần đó")
Chia theo trục kỹ thuật: **Mỹ Ý = dữ liệu & sản phẩm**, **Kim Huyền = AI & thuật toán**. Mỗi người ~10 phút, cân bằng.

| Slide | Nội dung | Người trình bày |
|---|---|---|
| 1–2 | Bìa + chào hội đồng + Agenda | **Ý** |
| 3–6 | Giới thiệu: vấn đề · khoảng trống · mục tiêu-đóng góp | **Ý** |
| 7–9 | Divider II + Kiến trúc tổng thể + Quy trình dữ liệu (ETL, chuẩn hóa) | **Ý** (bàn giao ở cuối slide 9) |
| 10–11 | Trích xuất kỹ năng (LLM + hậu kiểm) + Thuật toán so khớp | **Huyền** |
| 12 | Trực quan hóa (Dashboard + Skill Gap) | **Ý** |
| 13–15 | Divider III + Hệ thống thật + Kiểm thử chức năng | **Ý** |
| 16 | Đánh giá thuật toán (NER, chuẩn hóa, dedup, Skill Gap) | **Huyền** |
| 17–18 | Hiệu năng + Khảo sát người dùng | **Ý** |
| 19–20 | Divider IV + Demo (dẫn vào video) | **cả hai** (Ý mở, Huyền tiếp) |
| 21–22 | Divider V + Điều tâm đắc | **Ý** |
| 23 | Hạn chế & tự đánh giá | **Huyền** |
| 24 | Hướng phát triển | **Ý** |
| 25 | Cảm ơn | **Huyền** |
| D1–D10 | Slide dự phòng khi hỏi đáp | người phụ trách mảng đó (AI→Huyền, dữ liệu/hệ thống→Ý) |

**Cân đối thời lượng:** Ý ≈ 10' (giới thiệu, dữ liệu, hệ thống, hiệu năng, khảo sát, hạn chế) · Huyền ≈ 8' (thuật toán, trích xuất, đánh giá thuật toán, tâm đắc, hướng phát triển) + phần AI trong demo. Q&A: trả lời **luân phiên**, người kia bổ sung.

---

## PHẦN 1 — BỐ CỤC TỔNG QUAN (5 phần lớn)

| # | Phần lớn | Ý chính cần truyền đạt | Slide | ~Phút |
|---|---|---|---|---|
| I | **Giới thiệu & Động lực** | SV CNTT không tự lượng hóa được năng lực so với thị trường; dữ liệu tuyển dụng phân mảnh; keyword matching không chỉ ra "thiếu gì". → CareerNova ra đời để giải quyết. | 3–5 | 3–4' |
| II | **Giải pháp & Phương pháp** | Chuỗi kỹ thuật: Thu thập đa nguồn → ETL/chuẩn hóa → Trích xuất kỹ năng (LLM + hậu kiểm bằng chứng) → So khớp ngữ nghĩa (SBERT + trọng số thị trường) → Trực quan hóa. Mỗi bước **giải thích vì sao**. | 6–10 | 7–8' |
| III | **Kết quả & Đánh giá** | Hệ thống chạy thật (career-nova.online, ~7.245 tin thật); kiểm thử chức năng + truy vết; đánh giá thuật toán **trung thực**; hiệu năng đạt NFR; khảo sát người dùng tích cực. | 11–15 | 5–6' |
| IV | **Demo** | Trỏ tới video 10': các chức năng tốt nhất (dashboard, upload CV → skill gap → lộ trình). | 16 | (10' riêng) |
| V | **Kết luận** | Điều tâm đắc nhất → Hạn chế (tự đánh giá trung thực) → Hướng phát triển. | 17–20 | 3' |

---

## PHẦN 2 — CHI TIẾT TỪNG SLIDE

> Ký hiệu: **[H]** = hình/sơ đồ chủ đạo · **[Nói]** = ý người trình bày nói (speaker note, KHÔNG in lên slide) · **Người:** ai trình bày.
> Ảnh gợi ý lấy từ `082026/images/`.

---

### PHẦN MỞ ĐẦU

**Slide 1 — Bìa (Title)**
- Tên đề tài (đầy đủ), logo Trường + Khoa, tên 2 SV + MSSV, GVHD: TS. Vũ Thị Mỹ Hằng, Bộ môn HTTT, TP.HCM 08/2026.
- **[H]** `logo-khtn.png` + `logo.png` (logo CareerNova). Nền sạch, tương phản cao.
- **Người:** Ý mở đầu chào hội đồng.

**Slide 2 — Nội dung trình bày (Agenda)**
- 5 mục: 01 Giới thiệu · 02 Giải pháp & Phương pháp · 03 Kết quả & Đánh giá · 04 Demo · 05 Kết luận.
- **[H]** đánh số lớn kiểu năm ngoái (01–05), làm slide chuyển mục dùng lại layout này (highlight mục đang tới).

---

### I. GIỚI THIỆU & ĐỘNG LỰC

**Slide 3 — Bối cảnh & Vấn đề (đặt "thách thức")**
- 3 ý ngắn (mỗi ý 1 dòng):
  - Thị trường IT biến động nhanh → SV năm cuối **khó tự lượng hóa** năng lực vs. yêu cầu thật.
  - Dữ liệu tuyển dụng online **phong phú nhưng phân mảnh, chưa chuẩn hóa**.
  - Công cụ lọc CV truyền thống chỉ **khớp từ khóa** → không nói ứng viên **thiếu kỹ năng gì**.
- **[H]** sơ đồ 3 icon (SV bối rối · dữ liệu rời rạc nhiều nguồn · CV↔JD khớp từ khóa gạch chéo). Có thể dùng `image2_1.png`/`image2_2.png` nếu phù hợp, hoặc vẽ mới.
- **[Nói]** Đây là câu chuyện xuất phát: "chính chúng em từng loay hoay không biết mình thiếu gì" → dẫn động lực. *(bám yêu cầu "quan trọng với người nghe")*
- **Người:** Ý.

**Slide 4 — Giải pháp hiện có & Khoảng trống → Ý tưởng CareerNova**
- Cột trái: hạn chế giải pháp hiện tại (LinkedIn/TopCV/ATS: khớp từ khóa, không định lượng khoảng cách kỹ năng, dữ liệu đóng).
- Cột phải: **ý tưởng CareerNova** = kết hợp **LLM (hiểu ngữ nghĩa) + kiểm chứng bằng chứng** + **so khớp ngữ nghĩa có trọng số thị trường** + **trực quan hóa khoảng cách kỹ năng**.
- **[H]** bảng so sánh 2 cột (hiện có ✗ vs. CareerNova ✓) — nguồn Chương 2, mục "Khoảng trống nghiên cứu".
- **[Nói]** *Giải thích VÌ SAO không dùng keyword thuần* (gu cô Hằng): keyword bỏ sót đồng nghĩa ("ReactJS" vs "React"), không đo được mức độ gần.
- **Người:** Ý.

**Slide 5 — Mục tiêu · Phạm vi · Đóng góp**
- **Mục tiêu (3):** (1) thu thập & chuẩn hóa dữ liệu tuyển dụng đa nguồn; (2) trích xuất kỹ năng & định lượng khoảng cách CV↔JD bằng NLP/AI; (3) dashboard trực quan xu hướng thị trường.
- **Phạm vi:** ngành CNTT, thị trường VN; đối tượng: SV năm cuối.
- **Đóng góp:** kho dữ liệu sạch + pipeline trích xuất kỹ năng + công cụ đánh giá khoảng cách + web CareerNova đã triển khai thật.
- **[H]** 3 khối mục tiêu → mũi tên → 3 đóng góp, gắn nhãn **"Kết quả 1/2/3"** (mượn cách đóng khung sản phẩm của anh chị: Mục tiêu N → Kết quả N — Kết quả 1: Kho dữ liệu sạch + pipeline ETL · Kết quả 2: Pipeline trích xuất + công cụ Skill Gap · Kết quả 3: Web CareerNova + Dashboard).
- **Người:** Ý.

---

### II. GIẢI PHÁP & PHƯƠNG PHÁP

**Slide 6 — Kiến trúc tổng thể hệ thống**
- Bức tranh lớn: Nguồn tin tuyển dụng → Crawler → ETL/PostgreSQL → API Backend → (Algo-API: trích xuất + so khớp) → Frontend (Dashboard + Skill Gap).
- **[H]** `system_architecture.png` (kiến trúc tổng thể). Có `sequence_system_overview.png` để backup.
- **[Nói]** Nêu 1 câu "đóng góp lớn nhất" của kiến trúc: tách **algo-api** riêng để xử lý AI nặng, có cache.
- **Người:** Ý giới thiệu tổng thể rồi bàn giao Huyền ở slide 8.

**Slide 7 — Quy trình dữ liệu (ETL): Thu thập → ETL → Chuẩn hóa & Khử trùng lặp**
- Luồng: crawl đa nguồn → làm sạch → **chuẩn hóa thực thể** (công ty, kỹ năng) → **khử trùng lặp** → PostgreSQL.
- Con số thật: ~7.245 tin / 3.511 công ty / 6.048 kỹ năng (snapshot 14/07).
- **[H]** `sequence_etl_process.png` hoặc `system_architecture.png` (phần ETL) + `db_snapshot_psql.png` (bằng chứng dữ liệu thật).
- **[Nói]** *Vì sao cần chuẩn hóa*: dữ liệu thô "React.js/ReactJS/React" phải gộp về 1 để thống kê đúng. **Không dùng từ "hoàn hảo/tuyệt đối"** khi nói khử trùng lặp (phản biện đã nhắc).
- **Người:** Ý.

**Slide 8 — Trích xuất kỹ năng: LLM Structured Output + Hậu kiểm bằng chứng (chống ảo giác)**
- Ý cốt lõi (điểm tâm đắc kỹ thuật #1): LLM trả về **JSON có cấu trúc** → **tầng hậu kiểm** đối chiếu từng kỹ năng với **bằng chứng trong văn bản gốc**, loại kỹ năng "bịa".
- **[H]** sơ đồ: Văn bản CV/JD → LLM (Structured Output) → danh sách kỹ năng + evidence → Bộ lọc bằng chứng → kỹ năng đã xác thực. (dùng `system_architecture_algorithm.png` hoặc vẽ mới).
- **[Nói]** *Vì sao*: LLM có thể "ảo giác" kỹ năng không có thật → hậu kiểm để đảm bảo tin cậy. Thành thật: đây là khớp chuỗi con, còn giòn với OCR (để dành cho slide hạn chế).
- **Người:** Huyền.

**Slide 9 — Thuật toán so khớp năng lực (Matching Engine)**
- Công thức trực quan: **SBERT embedding → Cosine similarity → nhân trọng số thị trường (IDF theo nhóm ngành) → 6 luật nghiệp vụ → Match Score**.
- Đầu ra người dùng: % phù hợp + **danh sách kỹ năng còn thiếu** + gợi ý.
- **[H]** `sequence_matching_cv.png` hoặc `system_architecture_algorithm.png`; kèm 1 ví dụ nhỏ (CV kỹ sư phần mềm ~0,57).
- **[Nói]** *Vì sao có trọng số thị trường*: kỹ năng hiếm/cầu cao được tính nặng hơn. Thừa nhận sớm: ngưỡng & luật do nhóm đặt (chi tiết ở slide dự phòng). **Tránh gọi "chuyên gia nhân sự"** — người chấm là nhóm.
- **Người:** Huyền.

**Slide 10 — Trực quan hóa hỗ trợ ra quyết định (Dashboard + Skill Gap)**
- 2 sản phẩm trực quan: (1) **Dashboard thị trường** (job hot, kỹ năng cầu cao, xu hướng lương); (2) **Skill Gap** (radar CV vs JD + lộ trình).
- **[H]** ghép `ui_market_dashboard.png` + `ui_skill_gap.png` (hoặc `ui_cv_matching_radar.png`).
- **[Nói]** Nguyên lý DIKW: từ Dữ liệu → Thông tin → Tri thức → hành động cho SV. (`dikw_visualization_model.png` để backup).
- **Người:** Ý.

---

### III. KẾT QUẢ & ĐÁNH GIÁ

**Slide 11 — Hệ thống đã xây dựng & Dữ liệu thật (điều tâm đắc: chạy được thật)**
- Đã triển khai công khai **career-nova.online**, dữ liệu thật ~7.245 tin, cập nhật liên tục.
- Liệt kê phân hệ: Auth · Dashboard · Tìm/lưu job · Quản lý CV · So khớp năng lực.
- **[H]** ảnh ghép giao diện thật: `ui_landing.png` + `ui_market_dashboard.png` + `ui_cv_matching.png`.
- **[Nói]** Nhấn mạnh: khác luận prototype năm ngoái, đây là hệ thống **deploy thật, đo được thật**.
- **Người:** Ý.

**Slide 12 — Kiểm thử chức năng & Ma trận truy vết**
- Ma trận truy vết yêu cầu → kiểm thử (mỗi yêu cầu chức năng ánh xạ test case).
- **1 bảng test case mẫu** kiểu cô yêu cầu: **Test case | Đầu vào | Kết quả kỳ vọng | Kết quả thực tế | Đạt/Không**.
- **[H]** `test_cv_upload_rejected.png` / `test_job_search.png` / `test_saved_job.png` (bằng chứng test thật) + trích ma trận truy vết.
- **[Nói]** Trung thực khai báo phạm vi kiểm thử (đúng điều phản biện khen).
- **Người:** Ý.

**Slide 13 — Đánh giá thuật toán (TRÌNH BÀY TRUNG THỰC)**
- Bảng gọn 4 khối thuật toán, ghi rõ ĐẠT/CHƯA ĐẠT so ngưỡng (SỐ THẬT đã tái lập):
  - **NER (40 tài liệu):** JSON hợp lệ 100% ✓ · Precision 98,9% ✓ · **Recall 73,0% (chưa đạt 80%)** · F1 84,0% ✓.
  - **Chuẩn hóa kỹ năng:** Mapping 67,6% ✓ · Reject 69,3% ✓ · Gộp công ty 83,3% ✓.
  - **Khử trùng lặp:** P/R/F1 = 100% — nêu rõ **tập nhỏ 52 cặp (có cặp giả lập), mang tính kiểm chứng, không tổng quát**.
  - **Skill Gap (10 CV):** Accuracy 54,8% & Macro-F1 50,1% **(chưa đạt)** — nguyên nhân: **CSDL chỉ lưu nhị phân Matched/Missing, chưa có Partial** → 117 kỹ năng Partial bị ép về Missing; **MAE điểm số vẫn 0,106** (điểm tổng hợp vẫn sát người chấm).
- **[H]** bảng số (4 khối), mỗi khối kèm dòng **"→ Chứng minh: tính…"** (mượn cách đặt tên theo tiêu chí của anh chị): NER → *tính tin cậy của trích xuất* · Chuẩn hóa → *tính nhất quán của dữ liệu* · Khử trùng lặp → *tính toàn vẹn dữ liệu* · Skill Gap → *tính hợp lý của điểm số*. Kèm Case Study ứng viên tốt nhất (Match Score hệ thống 34% vs người chấm 25%, MAE 0,09).
- **[Nói]** *Chứng minh gì cho mục tiêu* (gu cô): NER Precision gần tuyệt đối → gần như không "bịa" kỹ năng; điểm số tổng hợp tin cậy (MAE≈0,1). Recall & Skill-Gap chưa đạt **có nguyên nhân rõ ràng, không phải lỗi thuật toán** → chuyển thẳng sang slide Hạn chế. **Tuyệt đối không nói "vượt kỳ vọng/hoàn hảo".**
- **Người:** Huyền.

**Slide 14 — Đánh giá hiệu năng (Response Time / NFR-02)**
- Kết quả đo 20 lượt: Dashboard 0,2–1,3s; Upload CV TB 1,31s; **Analyze cache-miss TB 41,9s, max 55,1s → 0/20 vượt 60s (ĐẠT NFR-02)**; cache-hit ~0,27s (~155× nhanh hơn).
- **[H]** `perf_measurement_terminal.png` (bằng chứng thô) + biểu đồ cột thời gian phản hồi.
- **[Nói]** *Vì sao có cache*: analyze nặng (gọi AI) → cache theo nội dung để lần sau tức thì. Nêu giới hạn: algo-api 2 vCPU dễ quá tải nếu gọi dồn (để dành slide hạn chế/dự phòng).
- **Người:** Ý.

**Slide 15 — Đánh giá với người dùng cuối**
- Khảo sát trải nghiệm người dùng: điểm giao diện / tốc độ / tính hữu ích của skill gap; trích 1–2 phản hồi tiêu biểu.
- **[H]** biểu đồ kết quả khảo sát (từ "Khảo sát trải nghiệm người dùng — CareerNova"); nếu chưa có ảnh trong `images/`, xuất biểu đồ mới.
- **[Nói]** Nêu cả điểm người dùng muốn cải thiện → dẫn sang phần hạn chế.
- **Người:** Ý.

---

### IV. DEMO

**Slide 16 — Demo (trỏ tới video 10 phút)**
- Liệt kê 3–4 chức năng **tốt nhất** sẽ demo, khung **Đầu vào → Đầu ra** (gu cô Hằng):
  1. Dashboard thị trường — *Đầu vào:* chọn bộ lọc ngành → *Đầu ra:* job hot, kỹ năng cầu cao, xu hướng lương.
  2. Upload CV → So khớp — *Đầu vào:* tải CV + chọn nhóm ngành → *Đầu ra:* % phù hợp + radar + **kỹ năng còn thiếu**.
  3. Skill Gap → Lộ trình — *Đầu vào:* xem chi tiết gap → *Đầu ra:* gợi ý kỹ năng & tài liệu học.
- **[H]** ảnh tĩnh 3 chức năng làm "mục lục demo"; nhắc "video đã quay sẵn tránh sự cố mạng" (đúng quy định).
- **Người:** cả 2 (mỗi người dẫn phần mình đã làm).

---

### V. KẾT LUẬN

**Slide 17 — Điều chúng em tâm đắc nhất** *(đáp trực tiếp yêu cầu GV phản biện)*
- 3 điểm: (1) **hệ thống chạy thật, dữ liệu thật, đo đạc có bằng chứng thô**; (2) **pipeline LLM + hậu kiểm bằng chứng** giảm ảo giác; (3) **định lượng khoảng cách kỹ năng có trọng số thị trường** — thứ keyword matching không làm được.
- **[H]** 3 icon + 1 ảnh sản phẩm.
- **Người:** chia đôi.

**Slide 18 — Hạn chế & Tự đánh giá (TRUNG THỰC)** *(đáp yêu cầu GV phản biện)*
- Nêu thẳng (mỗi ý 1 dòng):
  - Nhãn chuẩn do **nhóm tự gán**, chưa có gán độc lập ≥2 người / Cohen's kappa → threat to validity.
  - **Chưa có baseline** so sánh (keyword / TF-IDF / SBERT thuần) → chưa tách bạch đóng góp từng thành phần.
  - Recall/F1 **tiệm cận** ngưỡng; kiểm chứng bằng chứng khớp chuỗi con còn **giòn với OCR**.
  - Tập đánh giá nhỏ; một phần dữ liệu khử trùng lặp là giả lập → **chưa tổng quát**.
  - Dữ liệu CV gửi API bên thứ ba (Gemini) → **cần hoàn thiện xử lý PII/quyền riêng tư**.
- **[H]** bảng 2 cột "Hạn chế → Hướng khắc phục" (như layout năm ngoái, slide 47).
- **[Nói]** Đây là phần cô & hội đồng đánh giá cao sự trung thực. Với mỗi hạn chế, có **1 câu đề xuất cách giải quyết** (đúng lời khuyên "trình bày ngay giải pháp em đề xuất").
- **Người:** chia đôi.

**Slide 19 — Hướng phát triển tương lai**
- Mở rộng đa ngành; tự động cập nhật từ điển kỹ năng; **thêm baseline & phân tích độ nhạy ngưỡng**; ẩn danh hóa PII; nâng cấp gợi ý lộ trình; fuzzy matching cho bằng chứng.
- **[H]** timeline/roadmap ngắn.
- **Người:** chia đôi.

**Slide 20 — Cảm ơn & Hỏi đáp**
- "Cảm ơn quý thầy cô đã lắng nghe" + tên nhóm + link career-nova.online (QR nếu muốn).
- **[H]** `logo.png`. Giữ mở để hội đồng đặt câu hỏi.

---

## PHẦN 3 — SLIDE DỰ PHÒNG (Backup — để sau slide 20, KHÔNG trình bày trừ khi bị hỏi)

> Thủ sẵn cho các câu phản biện đã dự đoán. Khi bị hỏi, mở đúng slide → trả lời có bằng chứng.

- **D1 — So sánh baseline / Ablation:** Pearson r của hệ thống đầy đủ vs. tắt 6 luật vs. keyword matching (làm nếu kịp; nếu chưa, trình bày như đề xuất phương án).
- **D2 — Căn cứ chọn ngưỡng:** giải thích ngưỡng 0,75/0,45, boost ×1,2, soft-skill 0,35→ (hạ xuống 0,8 thay vì 1,0), thừa nhận là ngưỡng nội bộ + cách chọn trên tập dev.
- **D3 — Luật 1 (Chứng chỉ):** làm rõ có nhánh khớp chính xác theo tên/ID chứng chỉ trước khi ép về 0 (nếu không có → thừa nhận là lỗi logic cần sửa).
- **D4 — Quyền riêng tư PII:** CV gửi Gemini → có/không ẩn danh, đối chiếu **Nghị định 13/2023/NĐ-CP**, hướng loại PII trước khi gửi.
- **D5 — Pháp lý crawl:** trình bày trung tính về kỹ thuật + rate-limit, mục đích học thuật, không tái phân phối dữ liệu thô; nêu giới hạn ToS.
- **D6 — Định nghĩa 88,6% & 82,4%:** định nghĩa toán học "gợi ý đúng" là gì, đếm trên đơn vị nào.
- **D7 — "TF-IDF động":** thừa nhận TF nhị phân ⇒ trọng số quy về IDF; giải thích vì sao phù hợp dữ liệu dạng danh sách kỹ năng.
- **D8 — Bảng tổng hợp các tập đánh giá:** 1 bảng thống nhất (tập nào, kích thước, ai gán nhãn, dùng cho thí nghiệm nào) — giải quyết mâu thuẫn 40/100/758/52 mẫu.
- **D9 — ERD / lược đồ CSDL:** `erd_diagram.png`, `class_diagram.png` (nếu hỏi thiết kế dữ liệu).
- **D10 — Use case tổng quát:** `usecase_diagram.png` / `overall_usecase.png`.

---

## PHẦN 4 — KỊCH BẢN VIDEO DEMO (10 phút, quay sẵn)

| Phút | Chức năng | Đầu vào (thao tác) | Đầu ra (kết quả) |
|---|---|---|---|
| 0–3 | Dashboard thị trường | Mở trang, chọn lọc ngành/nhóm | Job hot, kỹ năng cầu cao, xu hướng lương |
| 3–7 | Upload CV → So khớp | Tải CV, chọn nhóm ngành, bấm phân tích | % phù hợp, radar CV vs JD, **danh sách kỹ năng còn thiếu** |
| 7–9 | Skill Gap → Lộ trình | Xem chi tiết gap | Gợi ý kỹ năng ưu tiên + tài liệu học |
| 9–10 | Lưu job / quản lý CV | Lưu job, xem lại lịch sử | Danh sách đã lưu |

**Lưu ý quay:** giọng thuyết minh nêu rõ *đầu vào → đầu ra* từng bước; quay lúc mạng ổn; có phụ đề; chuẩn bị sẵn tài khoản test đã kích hoạt (`is_active=true`) và CV mẫu.

---

## PHẦN 5 — CHECKLIST TRƯỚC KHI BẢO VỆ
- [ ] ≤ 20 slide chính; mỗi slide ≤ 2 dòng/bullet; ưu tiên hình.
- [ ] Đã bỏ mọi từ "đột phá/hoàn hảo/tuyệt đối/chứng minh"; sửa "chuyên gia nhân sự" → "nhóm thực hiện".
- [ ] Slide kết quả thuật toán trình bày **trung thực** (nêu chỉ tiêu chưa đạt).
- [ ] Có ≥1 bảng test case (Input → kỳ vọng → thực tế).
- [ ] Mỗi slide phương pháp có 1 câu "vì sao chọn" + "đóng góp lớn nhất".
- [ ] 10 slide dự phòng đã sẵn sàng cho câu hỏi phản biện.
- [ ] Video demo quay sẵn, tài khoản test hoạt động, CV mẫu chuẩn bị.
- [ ] Cả 2 thành viên đều có phần trình bày; tập luân phiên trả lời.
- [ ] Ghi nguồn tham khảo ở slide khảo sát; theme tương phản cao; không lạm dụng animation.
