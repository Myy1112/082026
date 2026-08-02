# SCRIPT THUYẾT TRÌNH CHI TIẾT — CareerNova (khớp deck Canva 35 slide)

**Quy ước:** [Ý] = Trần Thị Mỹ Ý · [Huyền] = Thái Thị Kim Huyền · ⏱ = mốc tích lũy · ➡ = câu bàn giao. Lời trong `> …` là phần **đọc gần như nguyên văn**; *(in nghiêng)* là ghi chú diễn.
**Nguyên tắc:** nói chậm–rõ; mỗi phương pháp nêu *vì sao chọn*; mỗi con số nói *chứng minh điều gì*; KHÔNG dùng "đột phá/hoàn hảo/tuyệt đối"; gọi người gán nhãn là **"nhóm thực hiện"**.
**Tổng:** ~19 phút slide (S1–S25) + 10 phút demo (video). Cắt phần *(có thể lược)* nếu cháy giờ.

> ⚠️ **Trước khi in/xuất:** thống nhất chức danh GVHD — slide 1 ghi **ThS.**, slide 25 ghi **TS.** (chọn 1). Gộp các slide trùng: 2 slide "So khớp ngữ nghĩa", 2 slide Dashboard/KQ3, 2 slide KQ1.

---

## MỞ ĐẦU — ⏱ 0:00

### Slide 1 · Bìa — [Ý] (~30s)
> Kính chào quý thầy cô trong hội đồng. Em là Trần Thị Mỹ Ý, cùng bạn Thái Thị Kim Huyền, thực hiện khóa luận **"Đề xuất khung phân tích hỗ trợ sinh viên phân tích dữ liệu tuyển dụng"**, dưới sự hướng dẫn của cô Vũ Thị Mỹ Hằng. Sản phẩm của đề tài là hệ thống **CareerNova**, hiện đã được triển khai chạy thật tại địa chỉ career-nova.online. Bài báo cáo của nhóm gồm khoảng 20 phút trình bày và 10 phút demo ạ.

### Slide 2 · Nội dung trình bày — [Ý] (~20s)
> Bài trình bày gồm năm phần: **một** — giới thiệu; **hai** — giải pháp và phương pháp; **ba** — kết quả và đánh giá; **bốn** — demo; và **năm** — kết luận. Hai chúng em sẽ luân phiên trình bày. Em xin bắt đầu với phần giới thiệu.

---

## PHẦN I — GIỚI THIỆU — ⏱ 0:50

### Slide 3 (Divider 01) + Slide 4 · Ngữ cảnh — [Ý] (~1:15)
> Đề tài đặt trong bối cảnh các **nền tảng tuyển dụng trực tuyến** hiện nay: dữ liệu việc làm rất phong phú, nhưng **rời rạc và phi cấu trúc**. Các nền tảng chủ yếu tập trung vào việc đăng tin và tìm ứng viên; còn khả năng hỗ trợ người học **đối chiếu năng lực cá nhân với yêu cầu thị trường** thì vẫn còn hạn chế.
> Từ đó, nhóm hướng tới một **hệ thống phân tích mô tả có ứng dụng mô hình ngôn ngữ lớn (LLM)**: mục tiêu là **chuẩn hóa và khai thác hiệu quả** nguồn dữ liệu tuyển dụng đó, hỗ trợ sinh viên **ra quyết định dựa trên dữ liệu** thay vì cảm tính.

### Slide 5 · Động lực — [Ý] (~1:00)
> Có ba động lực chính. **Thứ nhất**, hệ thống giúp sinh viên **nhận diện xu hướng nghề nghiệp và khoảng trống kỹ năng** cần bổ sung. **Thứ hai**, hỗ trợ các em **xây dựng lộ trình phát triển năng lực** phù hợp với nhu cầu thị trường. **Thứ ba**, nguồn dữ liệu tuyển dụng trực tuyến ngày càng phong phú, **mang lại nhiều cơ hội phân tích** mà trước đây chưa được khai thác đúng mức.

### Slide 6 · Khó khăn — [Ý] (~1:00)
> Tuy nhiên, có ba khó khăn. **Một**, dữ liệu tuyển dụng thu từ nhiều nguồn còn **rời rạc và không nhất quán**. **Hai**, việc so sánh năng lực hiện nay chủ yếu dựa trên **so khớp từ khóa**, chưa xét đến **mức độ liên quan và ý nghĩa** của từng kỹ năng — nên bỏ sót các trường hợp đồng nghĩa. **Ba**, những điều này khiến sinh viên **khó theo dõi và phân tích** thực trạng thị trường lao động. Đây chính là ba bài toán mà CareerNova giải quyết.

### Slide 7 · Mục tiêu luận văn — [Ý] (~1:15)
> Mục tiêu tổng quát của luận văn là **hỗ trợ sinh viên phân tích dữ liệu tuyển dụng và phát hiện khoảng trống kỹ năng so với vị trí công việc mong muốn**. Mục tiêu này được cụ thể hóa thành ba mục tiêu con, ánh xạ trực tiếp sang ba kết quả:
> — **Mục tiêu 1**: thu thập và chuẩn hóa dữ liệu tuyển dụng đa nguồn → cho ra **Kết quả 1: kho dữ liệu sạch và pipeline ETL**.
> — **Mục tiêu 2**: trích xuất và định lượng khoảng cách kỹ năng giữa CV và tin tuyển dụng bằng NLP/AI → **Kết quả 2: pipeline trích xuất và công cụ đo Skill Gap**.
> — **Mục tiêu 3**: trực quan hóa xu hướng thị trường hỗ trợ ra quyết định → **Kết quả 3: web CareerNova và Dashboard đã triển khai thật**.
> Phạm vi đề tài là ngành CNTT tại thị trường Việt Nam, đối tượng là sinh viên năm cuối và mới ra trường.

### Slide 8 · Phương pháp và kết quả — [Ý] (~1:00)
> Về phương pháp, nhóm thực hiện theo bốn bước. **Bước một** — khảo sát và phân tích yêu cầu: khảo sát công nghệ ETL, thuật toán Skill Gap và các cách trực quan hóa để áp dụng. **Bước hai** — thu thập và tiền xử lý dữ liệu, tạo ra Kết quả 1. **Bước ba** — thiết kế và phát triển hệ thống, tạo ra Kết quả 2 và Kết quả 3. **Bước bốn** — kiểm thử và đánh giá ứng dụng, triển khai thật tại career-nova.online.
> ➡ *Tiếp theo em xin đi vào phần Giải pháp và Phương pháp.*

---

## PHẦN II — GIẢI PHÁP & PHƯƠNG PHÁP — ⏱ 5:20

### Slide 9 (Divider 02) + Slide 10 · Khảo sát các nền tảng tuyển dụng — [Ý] (~1:00)
> Trước khi thiết kế, nhóm khảo sát các nền tảng hiện có: LinkedIn, TopCV, ITviec và Glints. Bảng đối chiếu cho thấy: việc **tự động thu thập dữ liệu đa nguồn**, **trích xuất kỹ năng ẩn bằng LLM**, **chấm điểm tương đồng ngữ nghĩa**, **biểu đồ xu hướng kỹ năng** và **báo cáo khoảng trống kỹ năng** — hầu hết các nền tảng đều **không hỗ trợ** hoặc chỉ hỗ trợ một phần.
> Kết luận rút ra: **chưa có nền tảng nào kết hợp được cả ba khâu — thu thập tự động, đối soát ngữ nghĩa và trực quan hóa**. Đây chính là khoảng trống mà CareerNova lấp vào.

### Slide 11 · Khảo sát công nghệ & lựa chọn — ETL — [Ý] (~1:00)
> Với từng nhiệm vụ trong pipeline dữ liệu, nhóm khảo sát nhiều phương án rồi chọn theo tiêu chí đáp ứng:
> — **Làm sạch HTML**: chọn **BeautifulSoup4 + Regex** vì linh hoạt với HTML rác nhiều lớp lồng nhau.
> — **Khử trùng lặp**: chọn **khóa URL/ID + đối soát tương đồng** — nhanh ở tầng cào, chính xác ở tầng nạp.
> — **Trích xuất thực thể**: chọn **Gemini 2.5 Flash + Structured Output** vì chi phí thấp, tốc độ nhanh, hỗ trợ JSON Schema gốc.
> — **Chuẩn hóa kỹ năng**: chọn **Vector Embedding (SBERT) + ngưỡng phù hợp** — không tốn phí API lặp lại, xử lý cục bộ tức thời.
> — **Lưu trữ**: chọn **PostgreSQL + JSONB** — vừa quan hệ chặt chẽ, vừa lưu JSON linh hoạt.
> *(Điểm mấu chốt: mỗi lựa chọn đều có lý do, đúng tinh thần "vì sao chọn".)*
> ➡ *Phần thuật toán so khớp, em xin mời Kim Huyền.*

### Slide 12 · Khảo sát công nghệ & lựa chọn — Thuật toán matching — [Huyền] (~1:00)
> Cảm ơn Ý. Với thuật toán so khớp, nhóm cân nhắc ba bước:
> — **Phương thức so khớp**: thay vì khớp từ khóa hay Jaccard, nhóm chọn **Vector Embedding SBERT** vì nó **hiểu ngữ nghĩa đồng nghĩa** — ví dụ "JS" và "JavaScript" — và hỗ trợ so khớp thời gian thực.
> — **Xác định trọng số kỹ năng**: thay vì đánh giá chuyên gia (AHP) hay nhờ LLM chấm, nhóm chọn **TF-IDF tính động từ thị trường** — tự động hoàn toàn, phản ánh đúng cung–cầu, chi phí API bằng 0 và minh bạch công thức.
> — **Lọc nhiễu kỹ năng**: áp **ngưỡng Coverage ≥ 10%** để loại kỹ năng hiếm/rác.
> *(Đây là nền tảng cho ba slide kỹ thuật tiếp theo.)*

### Slide 13 · Kiến trúc tổng thể của CareerNova — [Ý] (~1:15)
> Đây là kiến trúc tổng thể, gồm bốn tầng. **Tầng trình bày** là Frontend Next.js 15 với các Dashboard thị trường, phân tích Skill Gap và lộ trình học. **Tầng nghiệp vụ** gồm Backend API viết bằng NestJS, và một **ETL Pipeline riêng bằng Python/FastAPI** đảm nhận crawl, làm sạch, chuẩn hóa và nạp dữ liệu. **Tầng dữ liệu** là PostgreSQL lưu jobs, skills, CV và kết quả so khớp. **Dịch vụ ngoài** gồm Google Gemini API cho trích xuất, mô hình all-MiniLM-L6-v2 với FAISS cho tìm kiếm ngữ nghĩa, và các nguồn tin tuyển dụng như ITViec, VietnamWorks, CareerViet.
> Điểm em muốn nhấn mạnh: nhóm **tách riêng phần xử lý AI nặng** khỏi Backend chính và áp cache, nhờ đó giao diện luôn phản hồi nhanh kể cả khi tác vụ AI tốn thời gian.

### Slide 14 · KQ1 — Kho dữ liệu + pipeline ETL — [Ý] (~1:15)
> Đi vào Kết quả 1. Dữ liệu được thu thập từ bốn nguồn — ITViec, VietnamWorks, CareerViet, LinkedIn — rồi chạy qua quy trình ETL: **Extract** thu thập → lưu tạm ở **Staging** → **Transform** đưa qua LLM để biến đổi và chuẩn hóa → **Load** nạp vào cơ sở dữ liệu → **cập nhật trọng số** IDF theo thị trường → sẵn sàng cho Web và Matching Engine.
> Vì sao khâu chuẩn hóa quan trọng? Vì "React.js", "ReactJS", "react" phải được quy về **cùng một thực thể** thì thống kê thị trường mới chính xác.
> Tại thời điểm đo ngày 14/07, cơ sở dữ liệu thật có **7.245 tin tuyển dụng, 3.511 công ty đã gộp nhóm và 6.048 kỹ năng đã chuẩn hóa** — tất cả đều có ảnh chụp truy vấn trực tiếp làm bằng chứng.
> ➡ *Về cơ chế trích xuất và so khớp kỹ năng, em xin mời Kim Huyền.*

### Slide 15 · Kết hợp LLM và hậu kiểm bằng chứng — [Huyền] (~1:30)
> Đây là mắt xích nhóm tâm đắc nhất và cũng là **đóng góp thứ nhất**. Quy trình có bốn bước: văn bản CV hoặc tin tuyển dụng, nếu là ảnh thì qua OCR, được đưa vào **Gemini với JSON Schema cưỡng chế**, trả về danh sách kỹ năng **kèm bằng chứng** — tức đoạn văn bản chứng minh cho kỹ năng đó. Sau đó là **tầng hậu kiểm bằng chứng**: đối chiếu từng kỹ năng với bằng chứng trong văn bản gốc và **loại bỏ mọi kỹ năng không có dẫn chứng**. Cuối cùng ra danh sách kỹ năng đã xác thực.
> Vì sao cần bước này? Vì mô hình ngôn ngữ lớn có thể **"ảo giác" — bịa ra kỹ năng không có trong tài liệu**. Cơ chế hậu kiểm evidence-based của nhóm loại bỏ đúng những kỹ năng bịa đó. Nhờ vậy, **độ chính xác Precision của bước trích xuất đạt 98,9%** — nghĩa là gần như không nhận nhầm.

### Slide 16 · So khớp ngữ nghĩa có trọng số thị trường lao động — [Huyền] (~1:30)
> Sau khi có kỹ năng đã xác thực, Matching Engine hoạt động qua bốn bước. **SBERT** chuyển kỹ năng thành vector nhúng 384 chiều bằng mô hình all-MiniLM-L6-v2. **Cosine** đo độ tương đồng ngữ nghĩa giữa CV và tin tuyển dụng. Sau đó nhân **trọng số IDF tính động từ thị trường IT Việt Nam**. Và cuối cùng áp **6 luật lọc ngữ nghĩa** theo nhóm kỹ năng.
> Đầu ra là **Match Score = phần trăm phù hợp, kèm danh sách kỹ năng còn thiếu** — đúng thứ sinh viên cần.
> Đây là **đóng góp thứ hai và thứ ba** của nhóm. Vì sao cần trọng số thị trường? Vì một kỹ năng **hiếm và đang được săn đón** phải được tính nặng hơn một kỹ năng phổ thông — như vậy điểm số mới phản ánh đúng giá trị thị trường.
> *(Các ngưỡng và bộ luật do nhóm thiết lập dựa trên thử nghiệm; nếu hội đồng quan tâm, nhóm có slide chi tiết ở phần dự phòng.)*
> ➡ *Phần trực quan hóa, em xin mời lại Ý.*

### Slide 17 · Dashboard thị trường & phân tích khoảng cách kỹ năng (KQ3) — [Ý] (~1:00)
> Kết quả 3 là hai sản phẩm trực quan. Bên trái là **Dashboard thị trường**: vị trí được tuyển nhiều nhất, kỹ năng cầu cao, kỹ năng đang tăng nhanh và xu hướng theo thời gian. Bên phải là **phân tích Skill Gap**: biểu đồ radar so sánh CV với yêu cầu, phân nhóm kỹ năng đã đạt và còn thiếu, kèm gợi ý lộ trình học.
> Tinh thần xuyên suốt là mô hình **DIKW**: biến **Dữ liệu thô → Thông tin → Tri thức → hành động cụ thể** cho sinh viên, tức là biết nên học gì và ứng tuyển vị trí nào.
> ➡ *Sau đây là phần Kết quả và Đánh giá.*

---

## PHẦN III — KẾT QUẢ & ĐÁNH GIÁ — ⏱ 12:20

### Slide 18 (Divider 03) + Slide 19 · Triển khai công khai, dữ liệu thật — [Ý] (~0:50)
> Điều nhóm tâm đắc nhất ở phần kết quả: đây **không phải một bản mẫu (prototype)**, mà là **hệ thống chạy thật**, triển khai công khai tại career-nova.online trên Microsoft Azure, với đầy đủ **5 phân hệ** — Auth, Dashboard, Job, CV và So khớp. Toàn bộ **11 trên 11 ca kiểm thử chức năng đều đạt**, và người dùng cho điểm thiện cảm **8,56 trên 10**.

### Slide 20 · Trình bày trung thực: đạt gì, chưa đạt gì — [Huyền] (~1:30)
> Nhóm xin trình bày kết quả đánh giá thuật toán một cách **trung thực** — đạt gì và chưa đạt gì:
> — **Trích xuất kỹ năng (NER)** trên 40 tài liệu, chứng minh *tính tin cậy của trích xuất*: JSON hợp lệ 100%, Precision 98,9%, F1 84% — đạt; riêng **Recall 73%, chưa đạt ngưỡng 80%**, nguyên nhân là lệch ngôn ngữ Việt–Anh và lệch cấp độ chi tiết giữa nhãn và mô hình.
> — **Chuẩn hóa kỹ năng** trên 758 mẫu, chứng minh *tính nhất quán của dữ liệu*: Mapping 67,6%, Reject 69,3%, gộp công ty 83,3% — **đạt cả ba ngưỡng**.
> — **Khử trùng lặp** trên 52 cặp, chứng minh *tính toàn vẹn dữ liệu*: Precision/Recall/F1 đều 100% — nhưng nhóm nói rõ đây là **tập nhỏ, có cả cặp giả lập**, nên chỉ mang tính kiểm chứng, chưa tổng quát.
> — **Phân loại Skill Gap** trên 10 CV, chứng minh *tính hợp lý của điểm số*: Accuracy chỉ 54,8% và Macro-F1 50,1% — **chưa đạt**. Nhưng nguyên nhân rất rõ ràng và *không phải lỗi thuật toán*: cơ sở dữ liệu hiện chỉ lưu nhị phân "đã có / thiếu", chưa có trạng thái "khớp một phần", nên **117 kỹ năng khớp một phần bị ép về thiếu**. Bằng chứng thuật toán vẫn đúng: **độ lệch điểm tổng hợp MAE chỉ 0,106** — điểm cuối cùng vẫn rất sát người chấm.
> ➡ *Về hiệu năng, em xin mời lại Ý.*

### Slide 21 · Kiểm thử chức năng: 11/11 ca ĐẠT — [Ý] (~0:45)
> Nhóm xây **ma trận truy vết**, liên kết từng yêu cầu với thành phần thiết kế và ca kiểm thử tương ứng. Toàn bộ 11 trên 11 ca đạt trên môi trường thật. Hai ca rủi ro cao nhất đều qua: **TC-06** chặn đúng file sai định dạng hoặc quá 5MB ở biên; **TC-08** chạy đúng toàn bộ chuỗi AI từ trích xuất đến so khớp.

### Slide 22 · Thời gian phản hồi thực đo — đạt NFR — [Ý] (~1:00)
> Nhóm đo 20 lượt cho mỗi thao tác trên môi trường thật. Dashboard và upload CV phản hồi nhanh, dưới 2 giây. Đối soát CV lần đầu — khi phải gọi Gemini và tính vector — trung bình **41,9 giây, lớn nhất 55,1 giây**, tức **đạt ngưỡng NFR-02 là 60 giây**, không lượt nào vượt. Khi đối soát lặp lại, nhờ **bộ nhớ đệm (cache)** chỉ còn **0,27 giây, nhanh khoảng 155 lần**.
> Nhóm nói rõ: đây là số đo **đơn phiên, một người dùng**. Máy chủ chỉ 2 vCPU không GPU, nên khi nhiều người truy cập đồng thời, cache-miss có nguy cơ vượt 60 giây; nhóm **chưa kiểm thử tải** và ghi nhận đây là một hạn chế.

### Slide 23 · Khảo sát trải nghiệm người dùng (n=9) — [Ý] (~1:00)
> *(Lưu ý sửa lỗi chính tả tiêu đề slide: "chỉ đúng điểm yếu".)*
> Cuối cùng là đánh giá chủ quan từ người dùng, khảo sát 9 người đúng chân dung mục tiêu. Điểm thiện cảm tổng thể **8,56 trên 10**, và **100% cho từ 7 điểm trở lên**. Tín hiệu mạnh nhất: **100% đồng ý rằng hệ thống tiết kiệm thời gian tìm định hướng** — đúng giá trị cốt lõi của đề tài.
> Đáng chú ý, hạng mục điểm thấp nhất là **độ tin cậy của con số phần trăm Matching, chỉ 3,89** — trùng khớp chính xác với hạn chế Skill Gap vừa nêu; cảm nhận chủ quan và số đo khách quan hội tụ về cùng một điểm. Có **71,4% muốn hệ thống giải thích cách chấm điểm**, nên nhóm đã bổ sung tooltip và trang hướng dẫn ngay trên web.

---

## PHẦN IV — DEMO — ⏱ 18:10

### Slide 24 (Divider 04) + Ba chức năng chính — [Ý mở, Huyền tiếp] (~0:30 rồi bật video)
> Sau đây, nhóm xin trình chiếu video demo ba chức năng tốt nhất, mỗi chức năng theo mạch **Đầu vào → Đầu ra**:
> **Một** — Dashboard thị trường: *đầu vào* chọn bộ lọc ngành/khu vực → *đầu ra* việc làm hot, kỹ năng cầu cao, xu hướng.
> **Hai** — Upload CV và So khớp: *đầu vào* tải CV và chọn nhóm nghề → *đầu ra* phần trăm phù hợp, radar và danh sách kỹ năng còn thiếu.
> **Ba** — Skill Gap và Lộ trình: *đầu vào* xem chi tiết khoảng cách → *đầu ra* kỹ năng ưu tiên và gợi ý học tập.
> Video đã quay sẵn để tránh sự cố kỹ thuật. *(Bật video ~10 phút. Sau video chuyển sang kết luận.)*

---

## PHẦN V — KẾT LUẬN — (sau demo)

### Slide 25 (Divider 05) + Điều tâm đắc nhất — [Ý] (~0:45)
> Nhóm tâm đắc nhất ba điều. **Một — chạy thật, đo thật**: hệ thống triển khai công khai, dữ liệu thật hơn 7.000 tin, mọi số liệu đều có bằng chứng thô từ psql và terminal. **Hai — chống ảo giác LLM**: cơ chế hậu kiểm bằng chứng giúp Precision trích xuất đạt 98,9%, gần như không bịa. **Ba — định lượng khoảng cách**: so khớp ngữ nghĩa có trọng số thị trường, chỉ ra được "thiếu gì" — điều mà khớp từ khóa không làm được.

### Slide 26 · Hạn chế & tự đánh giá — [Huyền] (~1:00)
> Nhóm cũng nhìn thẳng vào hạn chế, mỗi hạn chế kèm hướng khắc phục. **Một**, nhãn chuẩn do nhóm tự gán → sẽ bổ sung gán độc lập từ hai người trở lên và đo Cohen's kappa. **Hai**, chưa có baseline so sánh → sẽ chạy ablation tách vai trò từng thành phần. **Ba**, Recall NER 73% và Skill Gap 54,8% → fuzzy match bằng chứng và lưu trữ ba trạng thái, thêm Partial. **Bốn**, tập đánh giá nhỏ và có phần giả lập → mở rộng tập thật, thêm cặp khó. **Năm**, CV gửi Gemini nhưng chưa xử lý dữ liệu cá nhân → sẽ ẩn danh hóa PII, đối chiếu Nghị định 13/2023. **Sáu**, mới đo đơn phiên → sẽ xử lý bất đồng bộ và kiểm thử tải.

### Slide 27 · Hướng phát triển — [Ý] (~0:45)
> Hướng phát triển theo bốn trục. **Nâng độ vững đánh giá**: baseline và ablation, phân tích độ nhạy ngưỡng, kiểm định liên người gán. **Cải thiện thuật toán**: lưu trữ ba trạng thái, fuzzy match bằng chứng, xử lý bất đồng bộ. **Mở rộng và làm giàu dữ liệu**: đa ngành, tự cập nhật từ điển kỹ năng, thêm dữ liệu lương và phỏng vấn. **Riêng tư và mở rộng quy mô**: ẩn danh hóa PII, load test, mở rộng theo chiều ngang. Bám sát phản hồi người dùng, hai thứ họ mong muốn nhất là **so sánh lương (77,8%)** và **chuẩn bị phỏng vấn kỹ thuật (55,6%)**.

### Slide 28 · Cảm ơn — [Huyền] (~0:15)
> Trên đây là toàn bộ phần trình bày của nhóm. Chúng em xin cảm ơn quý thầy cô đã lắng nghe và rất mong nhận được góp ý của hội đồng ạ.

---

## SLIDE DỰ PHÒNG (D1–D10) — chỉ mở khi bị hỏi

| Khi hội đồng/GVPB hỏi về… | Mở slide | Câu chốt để nói |
|---|---|---|
| **Baseline / so sánh phương pháp** | D1 | "Nhóm chưa chạy đối chứng đầy đủ — đã ghi nhận là hạn chế; đề xuất ablation trên cùng tập 20 JD + 20 CV: (1) chỉ khớp từ khóa, (2) SBERT thuần, (3) đầy đủ; kỳ vọng (3) > (2) > (1)." |
| **Vì sao ngưỡng 0,75/0,55/×1,2…** | D2 | "Đây là tham số vận hành thật trong mã nguồn, chọn theo trực giác thang Cosine + thử nghiệm trên tập dev; chưa grid-search toàn diện. Luật soft-skill nâng lên 1,0 dễ thổi phồng → đề xuất hạ trần 0,85." |
| **Luật chứng chỉ ép về 0 → chứng chỉ không bao giờ khớp?** | D3 | "Có nhánh khớp chính xác theo tên/ID chứng chỉ TRƯỚC khi áp luật ép-0; luật ép-0 chỉ chi phối khi hai kỹ năng khác nhóm phân loại." |
| **CV gửi Gemini — quyền riêng tư?** | D4 | "CV chứa PII và hiện chưa ẩn danh hóa trước khi gửi — nhóm nhận là hạn chế; chỉ dùng học thuật, không tái phân phối; hướng khắc phục: ẩn danh PII, đối chiếu Nghị định 13/2023." |
| **Pháp lý crawl / ToS** | D5 | "Kỹ thuật trình bày trung tính, mục đích học thuật, áp rate-limit, không tái phân phối dữ liệu thô; thừa nhận một số nền tảng hạn chế scraping trong ToS." |
| **Cỡ mẫu đánh giá đá nhau (40/758/52/10)** | D6 | "Mỗi thí nghiệm dùng tập nhãn riêng — bảng tổng hợp: NER 20 JD+20 CV; chuẩn hóa 758 (312+446)+24 công ty; dedup 17 tin→52 cặp; Skill Gap 10 CV (290 cặp)." |
| **Định nghĩa chỉ số / "TF-IDF động"** | D7 | "TP/FP/FN theo công thức chuẩn; TF nhị phân ⇒ trọng số quy về IDF, phù hợp dữ liệu dạng danh sách kỹ năng." |
| **Thiết kế CSDL** | D8 (ERD) | Chỉ vào các bảng: users, jobs, skills, job_skills, user_cvs, cv_job_matches, job_group_skill_weights. |
| **Phạm vi chức năng** | D9 (Use Case) | 4 nhóm: quản lý tài khoản; quản lý CV & so khớp; khám phá việc làm; trực quan hóa. |
| **Điểm số có đáng tin?** | D10 (Case Study) | "Ứng viên tốt nhất: hệ thống 34% vs người chấm 25%, MAE 0,09; 7 ca sai đều là Partial bị ép về Missing; không ca nào Missing→Matched → sàn cosine ≥ 0,55 an toàn." |

---

## GHI CHÚ TẬP LUYỆN
- Bấm giờ từng phần; nếu quá 20', cắt các câu *(có thể lược)* và rút gọn slide khảo sát công nghệ (11, 12).
- Chuẩn bị **giấy bút** ghi câu hỏi hội đồng; trả lời **luân phiên**, người kia bổ sung.
- Mở sẵn thư mục `KiemThu/` để tái lập số tại chỗ nếu được yêu cầu; đọc trước 3 bài báo đã trích (SkillSpan, Bhola COLING 2020, Khaouja IEEE Access 2021).
- **Việc cần sửa trên deck trước khi bảo vệ:** (1) thống nhất ThS./TS. cô Hằng; (2) sửa lỗi chính tả tiêu đề slide khảo sát người dùng ("chỉ đúng điểm yếu"); (3) gộp các slide trùng (So khớp × 2, Dashboard/KQ3 × 2, KQ1 × 2) để deck gọn còn ~28–30 slide.
