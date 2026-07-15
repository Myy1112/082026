# Hướng dẫn xử lý nhận xét phản biện — Luận văn CareerNova

---
## 🔴 CẬP NHẬT (phiên làm việc 16/07/2026) — ĐÃ ĐỐI CHIẾU VỚI CODE KIỂM THỬ THẬT

Sau khi pull code kiểm thử mới (`JobVisualization_BE/KiemThu/`), tôi đã đối chiếu **từng con số Chương 5 với artifact tái lập được** và sửa trực tiếp. Tóm tắt:

**Phát hiện lớn nhất:** 3 số ở Mục 5.4.2 + Tóm tắt (**Pearson r=0,842 / Gap 88,6% / khóa học 82,4%**) **KHÔNG có nguồn** ở bất kỳ đâu trong repo. Đánh giá matching thật (`KiemThu/MatchingCV`) là bài toán **gợi ý việc làm**: P@1=60%, P@3=P@5=55%, MRR=0,60 trên 10 CV.

**Đã sửa (dùng số thật):**
- ✅ Mục 5.4.2: bỏ Pearson/Gap/khóa học → thay bằng P@1=60%, P@3=P@5=55%, MRR=0,60 (gợi ý việc làm, 10 CV).
- ✅ NER (Nhóm 2): JD cũ 277/39/77 (87,7/78,3/82,7) → **thật 421/5/58 (98,8/87,9/93,0)**; tổng **96,0/85,1/90,2** — đạt cả 3 chỉ tiêu. Thêm cảnh báo **15/20 CV là ảnh cho 0/0/0**.
- ✅ A2 cỡ mẫu: khớp hết — NER 20+20; chuẩn hóa **758 (312+446) + 24 DN**; dedup 17 tin/52 cặp; matching 10 CV. Bỏ "100 (50+50)" ở mở đầu 5.4, Mục 5.4.2 và Chương 1.
- ✅ Tóm tắt (VN+EN), bảng khung đánh giá, câu mô tả chuẩn hóa: đồng bộ số thật.
- ✅ B5 (Pearson thiếu n/p-value): **không còn là vấn đề** vì Pearson đã bị gỡ.
- ✅ PDF build sạch, không lỗi.

**Nguồn artifact** (để trưng cho hội đồng): `KiemThu/KiemThu_LLM_Extract/` (NER), `KiemThu/KiemThu_SkillNormalization/` (chuẩn hóa), `KiemThu/KiemThu_Deduplication/` (dedup), `KiemThu/MatchingCV/` (gợi ý việc làm).

**Còn tồn (chỉ còn 1 việc cần chạy code):** A4 (ablation). Tất cả mục còn lại coi như đã xử lý.

**A6 phần 2 (thêm nguồn học thuật):** ✅ Đã xác minh bibtex THẬT trên ACL Anthology / IEEE Access và thêm 3 nguồn vào Mục 2.1.2 để định vị khoảng trống theo *nghiên cứu*: Bhola et al. COLING 2020 (`bhola2020retrieving`), Zhang et al. "SkillSpan" NAACL 2022 (`zhang2022skillspan`), Khaouja et al. IEEE Access 2021 survey (`khaouja2021survey`). Build + bibtex sạch, 3 citation resolve đúng. ⚠️ **NHÓM PHẢI ĐỌC 3 bài này trước khi bảo vệ** — hội đồng có thể hỏi nội dung.

**B6 (hình trùng):** ✅ Đã bỏ hình `fig:cv_flow` (dùng lại ảnh của Mục 3.2.3) ở Mục 3.5.1, thay bằng tham chiếu về Hình `fig:cv_upload_sequence`. Không còn hình trùng.

**B1/B2/B3 (biện minh ngưỡng & 6 luật):** ✅ Đã **xác minh tất cả ngưỡng khớp code thật**: 0,75/0,45/0,85 (`match_cv_with_url.py`), 0,85+0,15 hybrid & 0,80/0,70/0,62/0,60 dynamic (`normalize_*.py`), ×1,2 boost & soft-skill >0,35→1,0 & 6 luật (`match_cv.py`). Đã thêm: (B1) đoạn "Cơ sở lựa chọn các ngưỡng" cuối Chương 3 — nêu rõ đây là tham số vận hành thật, trực giác Cosine, và thừa nhận chưa grid-search; (B2) biện minh luật soft-skill + đề xuất hạ trần; (B3) đoạn "Thứ tự áp dụng" nêu đúng thứ tự tuần tự trong code và giải thích vì sao luật ép-0 chi phối.

**A6 phần 1 (gỡ trích dẫn sai):** ✅ Đã gỡ `li2020competence` khỏi các chỗ nó KHÔNG chứng minh: taxonomy "4 thế hệ ATS" (nêu rõ là tổng hợp của nhóm), GPT-4/Gemini/LLaMA, quy tắc Gen I, lập luận chi phí/độ trễ LLM, bước Gemini offline, định dạng CV/OCR đa cột. Sửa 1 lỗi nữa: Bag-of-Words/TF-IDF/Word2Vec trích nhầm `cloudflarebots` → đổi thành `manning2008`. Bước JSON có cấu trúc → gắn `geministructured`. Giữ `li2020competence` ở 5 chỗ đúng bản chất (so khớp hồ sơ, NER lĩnh vực nhân sự). Build sạch, không citation lỗi.

**A6 phần 2 (cần bạn — THÊM nguồn học thuật):** Tôi KHÔNG tự chèn citation vì (a) luận văn chỉ được trích cái nhóm đã đọc, (b) tránh bịa. Gợi ý một số bài THẬT, tiêu biểu về *skill extraction / labor-market NLP* để bạn **tự tìm, đọc, kiểm chứng bibliographic rồi mới cite** ở Mục 2.1.2 (định vị khoảng trống theo nghiên cứu, không chỉ theo sản phẩm thương mại):
- Zhang et al., "SkillSpan: Hard and Soft Skill Extraction from English Job Postings", NAACL 2022.
- Bhola et al., "Retrieving Skills from Job Descriptions: A Language Model Based Extreme Multi-label Classification Framework", COLING 2020.
- Khaouja et al., "A Survey on Skill Identification From Online Job Ads", IEEE Access 2021 (bài survey, rất hợp để định vị khoảng trống).
- Decorte et al., "JobBERT: Understanding Job Titles through Skills", 2021.
- Sayfullina et al., "Learning Representations for Soft Skill Matching", 2018.
⚠️ Phải tự xác minh tác giả/năm/venue và ĐỌC trước khi trích. Sau khi bạn chọn được vài bài, mình có thể giúp thêm vào `references.bib` và chèn `\cite` đúng chỗ.

**A7 (đóng góp):** ✅ Mục 1.6 đã viết lại, tách bạch rõ *tích hợp kỹ thuật* (Gemini/SBERT/FAISS/TF-IDF) vs *3 đóng góp riêng* của nhóm (hậu kiểm evidence-based, IDF động từ thị trường VN, 6 luật lọc ngữ nghĩa). Đã cắm ghi chú nối sang A4 (nên chứng minh 3 đóng góp bằng ablation).

**B7 (perf đơn phiên):** ✅ Đã thêm ở Mục 5.3.2 và 6.2: nói rõ số liệu đo *đơn phiên*, chưa load/stress test, nguy cơ vượt 60s khi tải đồng thời trên 2 vCPU.

⚠️ **Việc quan trọng nhất còn lại:** hãy đảm bảo notebook `KiemThu/` **chạy lại ra đúng** các số này và chuẩn bị mở cho hội đồng xem. Số đã khớp code, nhưng phải *tái lập được tại chỗ*.

---


> Mục tiêu: đưa luận văn từ "hệ thống chạy tốt" lên "đánh giá khoa học vững chắc, đủ sức bảo vệ trước hội đồng".
> Các mục **A** = bắt buộc xử lý trước bảo vệ; **B** = nên xử lý để tăng độ vững; **C** = lỗi biên tập, sửa nhanh.
> Ký hiệu ✅ = đã sửa sẵn trong mã nguồn; ⚠️ = cần bạn tự bổ sung dữ liệu/quyết định (đã cắm ghi chú `% GHI CHÚ PHẢN BIỆN` tại đúng vị trí trong file `.tex`).

---

## NGUYÊN TẮC VÀNG khi sửa
1. **Không nâng khống số liệu.** Nếu chạy lại thí nghiệm mà số tốt hơn thì cập nhật; nếu không, giữ số thật và **thừa nhận hạn chế**. Hội đồng đánh giá cao sự trung thực hơn là số đẹp.
2. **Mỗi con số phải truy vết được** về một log/script/ảnh chụp. Trước bảo vệ, hãy chuẩn bị sẵn file nguồn cho mọi bảng ở Chương 5.
3. **Mỗi khẳng định gắn đúng một nguồn.** Không dùng một trích dẫn cho nhiều nội dung không liên quan.

---

## A. NHÓM BẮT BUỘC (xử lý trước bảo vệ)

### A1 — Ground Truth do nhóm tự gán → thiên lệch ✅ (đã sửa wording) + ⚠️ (nên bổ sung)
- **Đã sửa:** bỏ cụm "chuyên gia nhân sự"; thêm câu thừa nhận nhãn do nhóm gán là hạn chế hợp lệ (Mục 5.4.2 + trỏ về 6.2).
- **Bạn cần làm thêm (mạnh nhất):** mời **1–2 người độc lập** (bạn cùng lớp, TA…) gán nhãn lại **một phần** tập mẫu (ví dụ 20 tài liệu), rồi tính **độ đồng thuận Cohen's κ**. Chỉ cần κ ≥ 0.6 là đã tăng đáng kể độ tin cậy. Nếu không kịp → giữ nguyên phần thừa nhận hạn chế đã thêm.
- **Câu trả lời cho hội đồng nếu bị hỏi:** "Nhãn do nhóm gán nên đây là mức nhất quán nội bộ; chúng em đã nêu rõ là hạn chế và đề xuất kiểm định liên người gán ở hướng phát triển."

### A2 — Cỡ mẫu mâu thuẫn trong Chương 5 ⚠️ (BẮT BUỘC KHỚP LẠI)
Các con số đang đá nhau:
| Nơi xuất hiện | Con số |
|---|---|
| Mở đầu 5.4 & Mục 5.4.2 | 100 tài liệu (50 CV + 50 JD) |
| Bảng NER `tab:match_extraction_details` | 40 tài liệu (20 JD + 20 CV) |
| Phương pháp chuẩn hóa (câu văn) | 300 kỹ năng thô + 100 từ khóa rác + 20 cặp DN |
| Bảng `tab:eval_norm_matching` | 312 / 446 / 758 mẫu; 24 doanh nghiệp |

- **Hành động:** thêm **một bảng "Tổng quan bộ dữ liệu đánh giá"** ngay đầu Mục 5.4, cột: *Thí nghiệm | Tập dữ liệu | Cỡ mẫu | Nguồn/log*. Giải thích rõ quan hệ (ví dụ: "40 tài liệu NER là tập con được gán nhãn chi tiết cấp thực thể; 312 mẫu kỹ năng là số cụm kỹ năng thô *có nghĩa* lọc từ 758 cụm của 40 tài liệu").
- **Tuyệt đối không tự chọn bừa một số** — phải mở log thí nghiệm thật và điền số đúng. Nếu "100" là mục tiêu ban đầu nhưng thực đo chỉ 40 → sửa "100" thành "40" ở các câu mô tả cho khớp.

### A3 — Khử trùng lặp 100% trên tập nhỏ/giả lập ✅ (đã hạ giọng) + ⚠️
- **Đã sửa:** đổi câu "hiệu năng hoàn hảo" thành "phân loại đúng toàn bộ 52 cặp trong tập nhỏ… mang tính kiểm chứng tính đúng đắn hơn là ước lượng tổng quát".
- **Bạn cần:** ghi rõ trong đoạn **số cặp thực vs giả lập** (VD: 17 cặp thực, 35 cặp có bổ sung nhiễu nhân tạo). Nếu có thời gian, thêm vài cặp **thực tế khó** (cùng công ty, khác vị trí, mô tả 70–80% giống) để chứng minh không chỉ ăn may.

### A4 — Thiếu baseline / ablation ⚠️ (đây là mục nâng hạng luận văn)
- **Vấn đề:** cả luận văn lập luận "lai LLM+SBERT+TF-IDF tốt hơn ATS từ khóa / LLM thuần" nhưng **không đo đối chứng**.
- **Hành động tối thiểu:** trên cùng tập 100 tài liệu, chạy 3 cấu hình và lập 1 bảng:
  1. Chỉ khớp từ khóa (regex) — baseline thấp.
  2. SBERT thuần (không TF-IDF, không 6 luật lọc).
  3. Hệ thống đầy đủ (SBERT + TF-IDF động + 6 luật lọc).
  So cùng chỉ số (Pearson r với nhãn, hoặc độ chính xác Gap). Chỉ cần số của (3) > (2) > (1) là **đã chứng minh được giá trị của từng thành phần** — đúng thứ hội đồng muốn thấy.
- Nếu không kịp chạy đủ 3: tối thiểu bật/tắt **trọng số TF-IDF** để cho thấy nó có tác dụng.

### A5 — Recall & F1 chưa đạt ngưỡng nhưng diễn giải như đã thành công ✅ (đã sửa)
- **Đã sửa:** Mục 5.4.1 giờ nói thẳng Recall 77.4% **chưa đạt** 80%, F1 82.0% **thấp hơn** 82.5%, và tổng kết "đạt 2/4, chưa đạt 2/4 với mức chênh nhỏ", kèm trỏ tác động sang 6.2.
- **Bạn nên:** thêm 1 câu ở **Tóm tắt** cho cân đối (hiện Tóm tắt chỉ khoe số). Ví dụ: *"…đạt Precision 87,2%, Recall 77,4% (xấp xỉ ngưỡng kỳ vọng 80%)…"* — trung thực mà vẫn gọn.

### A6 — Lạm dụng một trích dẫn `li2020competence` ⚠️ (dễ bị bắt lỗi học thuật)
- **Vấn đề:** một bài EMNLP đang được gắn cho crawling, OCR, "4 thế hệ ATS", chi phí LLM… (rải khắp Chương 2).
- **Hành động:**
  - Crawling/Scraping → đã có `olston2010web`, `webdriver`, `cloudscraper` rồi; **bỏ** `li2020competence` khỏi các câu này.
  - "4 thế hệ ATS" và bảng so sánh chi phí/độ trễ → nếu là tổng hợp của nhóm thì viết *"Dựa trên khảo sát của nhóm…"* và **bỏ** trích dẫn giả; hoặc tìm 1–2 survey thật về ATS/resume-matching.
  - OCR/định dạng CV đa cột → tìm 1 nguồn về document layout/OCR.
- **Bổ sung 3–5 công trình học thuật** về *skill gap analysis / labor market NLP / job recommendation* để phần "khoảng trống nghiên cứu" (Mục 2.1.2) đứng vững — hiện đang định vị chủ yếu so với **sản phẩm thương mại**, chưa so với **nghiên cứu**.

### A7 — Định vị đóng góp khoa học so với nhan đề "khung phân tích" ⚠️
- **Vấn đề:** nhan đề nói "đề xuất khung phân tích" (framework) nhưng nội dung nghiêng về **tích hợp kỹ thuật** công cụ có sẵn.
- **Hành động:** viết lại đoạn "Đóng góp" (Mục 1.6) tách bạch:
  - *Phần tích hợp kỹ thuật* (dùng lại: Gemini, SBERT, FAISS, TF-IDF) — nói thẳng là kỹ thuật.
  - *Phần thực sự mới của nhóm*, ví dụ: (i) cơ chế hậu kiểm evidence-based chống ảo giác; (ii) **trọng số theo độ hiếm tính động từ thị trường IT Việt Nam**; (iii) **bộ 6 luật lọc ngữ nghĩa theo metadata phân loại kỹ năng**. Nhấn mạnh đây là đóng góp, và **đo giá trị của nó qua ablation A4**.
- Nếu phần "mới" còn mỏng, có thể đề xuất chỉnh nhan đề cho khớp deliverable (VD thêm "và xây dựng hệ thống…") — bàn với GVHD.

---

## B. NHÓM NÊN XỬ LÝ (tăng độ vững chắc)

### B1 — Ngưỡng/hệ số kinh nghiệm, không hiệu chỉnh ⚠️
Các hằng số quyết định kết quả mà chưa nêu cơ sở: **0.75 / 0.45** (phân loại), **0.85/0.15** (hybrid), **0.35** (soft skill), **0.80/0.70** (ngưỡng động), **×1.2** (boost), **θ=0.8** (dedup).
- **Hành động:** thêm 1–2 câu nêu cơ sở chọn (thử nghiệm sơ bộ / tham khảo / heuristic). Lý tưởng: một bảng **phân tích độ nhạy** cho 1–2 ngưỡng quan trọng nhất (ví dụ quét ngưỡng phân loại 0.70/0.75/0.80 và xem độ chính xác Gap đổi thế nào).

### B2 — Luật "Soft Skills Direct Match" nâng thẳng 1.0 ⚠️
- Bất kỳ cặp kỹ năng mềm nào cosine > 0.35 đều thành 1.0 → thổi phồng điểm (Communication↔Teamwork 0.45→1.0 trong Case Study).
- **Hành động:** hoặc **biện minh** (vì sao kỹ năng mềm coi là thay thế được nhau), hoặc **hạ trần** (giữ nguyên cosine, hoặc nâng lên tối đa 0.85 thay vì 1.0). Nếu giữ nguyên, phải sẵn sàng trả lời chất vấn.

### B3 — 6 luật lọc "cứng" ép cosine→0 có thể phạt oan + thứ tự chưa rõ ⚠️
- **Hành động:** thêm **pseudocode/sơ đồ** nêu rõ **thứ tự ưu tiên** áp dụng 6 luật (luật nào chạy trước, có short-circuit không). Thảo luận rủi ro phạt oan kỹ năng liên quan chéo phân nhóm → có thể tạo "missing" giả.

### B5 — Pearson r thiếu thông tin thống kê ✅ (đã cắm ghi chú) + ⚠️
- **Bạn cần bổ sung:** **cỡ mẫu n** dùng để tính r (50 cặp? 100?), **p-value**, và nếu được **biểu đồ phân tán**. Một hệ số tương quan không có n và p rất dễ bị bắt lỗi.

### B7 — Hiệu năng lần đầu sát trần, chưa test tải ⚠️
- 41.9s TB / 55.1s max trên 2 vCPU, đo **tuần tự có giãn cách** → chỉ là độ trễ đơn phiên (single-session).
- **Hành động:** ở Mục 5.3.2 và 6.2 ghi rõ đây là độ trễ **một người dùng**; nêu rủi ro khi nhiều người đồng thời và CV dài hơn → có thể vượt 60s (NFR-02). Có thể đề xuất hàng đợi/xử lý bất đồng bộ như hướng khắc phục (bạn đã có ý này ở cuối 5.3.2, chỉ cần nối vào phần hạn chế).

---

## C. LỖI BIÊN TẬP (sửa nhanh)

| Mã | Nội dung | Trạng thái |
|---|---|---|
| C1 | Câu lặp 2 lần "Bảng `tab:eval_norm_matching` thiết lập khung tiêu chí…" (Ch.5) | ✅ đã xóa 1 dòng |
| C2 | `Appendix/edit.tex` còn câu hướng dẫn template | ✅ đã thay bằng ghi chú trung tính |
| C3 | "20 cặp doanh nghiệp" vs "24 doanh nghiệp" (Ch.5) | ⚠️ đã cắm ghi chú, cần khớp 1 số |
| C4 | Tóm tắt: 88.6% là "độ chính xác gợi ý Gap", tránh hiểu là accuracy toàn cục | ⚠️ hiện wording tạm ổn; rà lại 1 lần |
| C5 | `Appendix/summary.tex` còn là text mẫu — kiểm tra file này KHÔNG được `\include` trong main.tex | ⚠️ đã xác nhận main.tex dùng `abstract.tex`, không dùng `summary.tex` → an toàn, không lên bản in |
| B6 | Hình `cv_upload_sequence` bị dùng lại cho 2 figure khác caption (Ch.3) | ⚠️ đã cắm ghi chú; cần vẽ 1 sơ đồ riêng hoặc bỏ 1 hình |

---

## D. GỢI Ý TĂNG ĐIỂM (không bắt buộc)
1. **Bảng ablation (A4)** là thứ đáng đầu tư nhất — biến luận văn từ "mô tả hệ thống" thành "có đánh giá phương pháp".
2. **Tác động của Recall 77.4%** tới người dùng: ~22% kỹ năng bị bỏ sót → có thể tạo "khoảng trống giả" khiến sinh viên học nhầm. Đã trỏ ở 5.4.1, nên viết 1 đoạn ở 6.2.
3. Case Study 5.4.2 là **n=1** — giữ vai trò *minh họa cơ chế*, đừng để đóng vai *bằng chứng định lượng*. Kết luận định lượng dựa trên tập 100 tài liệu (qua A4).

---

## THỨ TỰ ƯU TIÊN GỢI Ý (nếu ít thời gian)
1. **A2** (khớp cỡ mẫu) — nếu số đá nhau, mất uy tín tức thì. Làm trước.
2. **A5, A1, A3** — đã sửa wording; bạn chỉ cần đọc lại và bổ sung nếu có dữ liệu.
3. **A6** (trích dẫn) — dọn 1 buổi là xong, tránh mất điểm học thuật.
4. **A4** (ablation) — nếu còn thời gian chạy được, đây là điểm cộng lớn nhất.
5. **A7** (đóng góp) — viết lại 1 đoạn, làm cuối cùng sau khi A4 có số.
6. **B/C** còn lại — rà trong lần đọc soát cuối.

> Sau khi bạn khớp xong các số ở A2/C3 và quyết định về A4/A6, gọi mình để mình sửa tiếp trực tiếp vào `.tex` (viết đoạn đóng góp A7, dựng khung bảng ablation, dọn trích dẫn A6…).
