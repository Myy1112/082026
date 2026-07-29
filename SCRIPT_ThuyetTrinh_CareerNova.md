# SCRIPT THUYẾT TRÌNH — CareerNova (bản đọc/tập, canh 20 phút)

**Quy ước:** [Ý] = Trần Thị Mỹ Ý · [Huyền] = Thái Thị Kim Huyền · ⏱ = mốc thời gian tích lũy · ➡ = câu chuyển ý/bàn giao.
**Nguyên tắc nói:** chậm, rõ; mỗi phương pháp nói *vì sao chọn*; mỗi số nói *chứng minh điều gì*; KHÔNG dùng "đột phá/hoàn hảo/tuyệt đối"; gọi người gán nhãn là "nhóm thực hiện", không phải "chuyên gia nhân sự".
**Tổng:** ~19–20 phút trình bày + 10 phút demo (video). Nếu cháy giờ, cắt phần in *(có thể lược)*.

---

## MỞ ĐẦU — ⏱0:00

**[Slide 1 · Bìa] — [Ý] (~30s)**
> Kính chào quý thầy cô trong hội đồng. Em là Mỹ Ý, cùng bạn Kim Huyền, thực hiện khóa luận *"Đề xuất khung phân tích hỗ trợ sinh viên phân tích dữ liệu tuyển dụng"*, dưới sự hướng dẫn của cô Vũ Thị Mỹ Hằng. Sản phẩm là hệ thống **CareerNova**, đã được triển khai chạy thật tại career-nova.online. Bài của nhóm gồm 20 phút trình bày và 10 phút demo.

**[Slide 2 · Nội dung] — [Ý] (~30s)**
> Phần trình bày gồm năm mục: giới thiệu và động lực; giải pháp cùng phương pháp; kết quả và đánh giá; demo; và kết luận. Hai chúng em sẽ luân phiên trình bày.

---

## PHẦN I — GIỚI THIỆU & ĐỘNG LỰC — ⏱1:00

**[Slide 3 · Divider 01] + [Slide 4 · Vấn đề] — [Ý] (~1:30)**
> Xuất phát điểm của đề tài là một vấn đề rất thật với chính chúng em. Là sinh viên CNTT năm cuối, chúng em thường xuyên tự hỏi: *"mình còn thiếu kỹ năng gì để đi làm được?"* — và không có công cụ nào trả lời rõ ràng.
> Chúng em nhận thấy ba thách thức. **Thứ nhất**, thị trường IT biến động rất nhanh, sinh viên khó tự lượng hóa năng lực so với yêu cầu thực tế. **Thứ hai**, dữ liệu tuyển dụng trực tuyến tuy nhiều nhưng phân mảnh, viết lệch, chưa chuẩn hóa nên khó phân tích. **Thứ ba**, các công cụ hiện tại chủ yếu khớp từ khóa, nên không chỉ ra được ứng viên đang thiếu chính xác kỹ năng nào.

**[Slide 5 · Khoảng trống → Ý tưởng] — [Ý] (~1:15)**
> Vì sao không dùng khớp từ khóa? Vì keyword bỏ sót các từ đồng nghĩa — ví dụ "React" và "ReactJS" — và không đo được mức độ gần nhau về ngữ nghĩa.
> Từ đó, CareerNova đề xuất một hướng khác: dùng mô hình ngôn ngữ lớn để *hiểu* ngữ nghĩa, kèm cơ chế kiểm chứng bằng chứng để trích xuất kỹ năng đáng tin; sau đó so khớp ngữ nghĩa có gắn trọng số theo thị trường IT Việt Nam; và cuối cùng trực quan hóa khoảng cách kỹ năng cho người dùng.

**[Slide 6 · Mục tiêu · Đóng góp] — [Ý] (~1:15)**
> Đề tài có ba mục tiêu, ánh xạ trực tiếp sang ba đóng góp. Một: thu thập và chuẩn hóa dữ liệu tuyển dụng đa nguồn — tạo ra kho dữ liệu sạch và pipeline ETL. Hai: trích xuất và định lượng khoảng cách kỹ năng giữa CV và tin tuyển dụng — tạo ra công cụ đo Skill Gap. Ba: trực quan hóa xu hướng thị trường — tạo ra web CareerNova và dashboard đã triển khai thật. Phạm vi đề tài là ngành CNTT tại Việt Nam, cho sinh viên năm cuối.
> ➡ *Tiếp theo, bạn Kim Huyền và em sẽ đi vào từng mắt xích kỹ thuật.*

---

## PHẦN II — GIẢI PHÁP & PHƯƠNG PHÁP — ⏱5:00

**[Slide 7 · Divider 02] + [Slide 8 · Kiến trúc] — [Ý] (~1:15)**
> Đây là kiến trúc tổng thể. Dữ liệu tin tuyển dụng được crawler thu thập, đưa qua pipeline ETL và lưu vào PostgreSQL. Core API phục vụ giao diện, còn các tác vụ AI nặng — trích xuất và so khớp — được tách riêng sang dịch vụ *algo-api*.
> Điểm em muốn nhấn mạnh về thiết kế: việc tách algo-api riêng và áp cache giúp giao diện luôn phản hồi nhanh, kể cả khi tác vụ AI tốn thời gian.

**[Slide 9 · Quy trình dữ liệu (ETL)] — [Huyền] (~1:30)**
> Đi vào quy trình dữ liệu. Sau khi crawl từ nhiều nguồn, dữ liệu được làm sạch, rồi **chuẩn hóa thực thể** cho cả kỹ năng lẫn tên công ty, và **khử trùng lặp** trước khi lưu.
> Vì sao chuẩn hóa lại quan trọng? Vì "React.js", "ReactJS", "react" phải được quy về cùng một thực thể thì thống kê thị trường mới chính xác. Khử trùng lặp dùng TF-IDF kết hợp Cosine với ngưỡng 0,8.
> Tại thời điểm đo, cơ sở dữ liệu thật có 7.245 tin tuyển dụng, 3.511 công ty và 6.048 kỹ năng đã chuẩn hóa — tất cả có ảnh chụp truy vấn trực tiếp làm bằng chứng.
> ➡ *Về cơ chế trích xuất kỹ năng, em xin mời Kim Huyền.*

**[Slide 10 · Trích xuất kỹ năng] — [Huyền] (~1:45)**
> Cảm ơn Ý. Đây là mắt xích mà nhóm tâm đắc nhất. Văn bản CV hoặc tin tuyển dụng được đưa vào Gemini, với JSON schema cưỡng chế và nhiệt độ bằng 0, trả về danh sách kỹ năng kèm *bằng chứng* — tức đoạn văn bản chứng minh kỹ năng đó.
> Vấn đề cố hữu của mô hình ngôn ngữ lớn là "ảo giác" — bịa ra kỹ năng không có trong tài liệu. Đóng góp của nhóm là một **tầng hậu kiểm**: đối chiếu từng kỹ năng với bằng chứng trong văn bản gốc và loại bỏ những kỹ năng không có dẫn chứng.
> Nhờ cơ chế này, độ chính xác Precision của bước trích xuất đạt 98,9% — nghĩa là gần như không bịa kỹ năng. *(có thể lược:* nhóm thành thật là hậu kiểm hiện dùng khớp chuỗi con, còn nhạy với lỗi OCR — sẽ nói ở phần hạn chế*).*

**[Slide 11 · Thuật toán so khớp] — [Huyền] (~1:45)**
> Sau khi có kỹ năng đã xác thực, Matching Engine hoạt động qua bốn bước. SBERT chuyển kỹ năng thành vector 384 chiều; Cosine đo độ tương đồng ngữ nghĩa giữa CV và tin tuyển dụng; sau đó nhân **trọng số IDF động** tính từ thị trường IT Việt Nam; và cuối cùng áp **6 luật lọc ngữ nghĩa** theo nhóm kỹ năng.
> Vì sao cần trọng số thị trường? Vì một kỹ năng hiếm và đang được săn đón phải được tính nặng hơn một kỹ năng phổ thông. Đây cùng với bộ 6 luật là hai đóng góp riêng của nhóm.
> Kết quả đầu ra không chỉ là một con số phần trăm phù hợp, mà kèm theo **danh sách kỹ năng còn thiếu** — đúng thứ sinh viên cần. *(Các ngưỡng và luật do nhóm thiết lập dựa trên thử nghiệm; nếu hội đồng quan tâm, nhóm có slide chi tiết.)*
> ➡ *Phần trực quan hóa, em xin mời lại Ý.*

**[Slide 12 · Trực quan hóa] — [Ý] (~1:15)**
> Nhóm xây hai sản phẩm trực quan. Bên trái là Dashboard thị trường: vị trí được tuyển nhiều nhất, kỹ năng cầu cao, xu hướng. Bên phải là Skill Gap: biểu đồ radar so sánh CV với yêu cầu, phân nhóm kỹ năng đã đạt và còn thiếu, kèm gợi ý lộ trình học.
> Tinh thần xuyên suốt là mô hình DIKW: biến dữ liệu thô thành hành động cụ thể — sinh viên biết nên học gì và ứng tuyển vị trí nào.

---

## PHẦN III — KẾT QUẢ & ĐÁNH GIÁ — ⏱12:30

**[Slide 13 · Divider 03] + [Slide 14 · Hệ thống thật] — [Ý] (~1:00)**
> Điều nhóm tâm đắc nhất ở phần kết quả: đây không phải một bản mẫu, mà là **hệ thống chạy thật**, công khai tại career-nova.online, với đầy đủ 5 phân hệ. Toàn bộ 11 ca kiểm thử chức năng đều đạt, và người dùng cho điểm thiện cảm 8,56 trên 10.

**[Slide 15 · Kiểm thử chức năng] — [Ý] (~1:00)**
> Nhóm xây ma trận truy vết, liên kết từng yêu cầu với thành phần thiết kế và ca kiểm thử tương ứng. 11 trên 11 ca đạt trên môi trường thật. Hai ca rủi ro cao nhất đều qua: TC-06 chặn đúng file sai định dạng hoặc quá 5MB ở biên; TC-08 chạy đúng toàn bộ chuỗi AI từ trích xuất đến so khớp.
> ➡ *Về chất lượng thuật toán, em xin mời Kim Huyền.*

**[Slide 16 · Đánh giá thuật toán] — [Huyền] (~1:45)**
> Nhóm trình bày kết quả một cách trung thực — đạt gì và chưa đạt gì.
> Với trích xuất kỹ năng: cấu trúc JSON hợp lệ 100%, Precision 98,9%, F1 84% — đạt; riêng Recall 73%, **chưa đạt ngưỡng 80%**, nguyên nhân là lệch ngôn ngữ Việt–Anh và lệch cấp độ chi tiết giữa nhãn và mô hình.
> Chuẩn hóa kỹ năng đạt cả ba ngưỡng. Khử trùng lặp đạt 100%, nhưng nhóm nói rõ đây là tập nhỏ 52 cặp, có cả cặp giả lập, nên chỉ mang tính kiểm chứng, chưa tổng quát.
> Với phân loại Skill Gap trên 10 CV: độ chính xác chỉ 54,8% — **chưa đạt**. Nhưng nguyên nhân rất rõ ràng và *không phải lỗi thuật toán*: cơ sở dữ liệu hiện chỉ lưu nhị phân "đã có / thiếu", chưa có trạng thái "khớp một phần", nên 117 kỹ năng khớp một phần bị ép về "thiếu". Bằng chứng cho việc thuật toán vẫn đúng: độ lệch điểm số tổng hợp MAE chỉ 0,106 — điểm cuối cùng vẫn rất sát với người chấm.
> ➡ *Về hiệu năng, em xin mời lại Ý.*

**[Slide 17 · Hiệu năng] — [Ý] (~1:15)**
> Nhóm đo 20 lượt cho mỗi thao tác trên môi trường thật. Dashboard và upload CV phản hồi nhanh. Đối soát CV lần đầu — khi phải gọi Gemini và tính vector — trung bình 41,9 giây, lớn nhất 55,1 giây, tức **đạt ngưỡng NFR 60 giây**, không lượt nào vượt. Khi đối soát lặp lại, nhờ bộ nhớ đệm (cache) chỉ còn 0,27 giây, nhanh khoảng 155 lần.
> Nhóm nói rõ: đây là số đo đơn phiên, một người dùng. Máy chủ chỉ 2 vCPU không GPU, nên khi nhiều người truy cập đồng thời có thể vượt ngưỡng; nhóm chưa kiểm thử tải và ghi nhận đây là hạn chế.

**[Slide 18 · Khảo sát người dùng] — [Ý] (~1:15)**
> Cuối cùng là đánh giá chủ quan từ người dùng, khảo sát 9 người đúng chân dung mục tiêu. Trung bình 4,39 trên 5. Tín hiệu mạnh nhất: 100% đồng ý rằng hệ thống *tiết kiệm thời gian tìm định hướng* — đúng giá trị cốt lõi đề tài hướng tới.
> Đáng chú ý, hạng mục điểm thấp nhất là *độ tin cậy của con số phần trăm Matching*, chỉ 3,89 — trùng khớp chính xác với hạn chế Skill Gap vừa nêu. Cảm nhận người dùng và số đo kỹ thuật hội tụ về cùng một điểm. 71,4% muốn được giải thích cách chấm điểm, nên nhóm đã bổ sung tooltip và trang hướng dẫn ngay trên web.

---

## PHẦN IV — DEMO — ⏱18:00

**[Slide 19 · Divider 04] + [Slide 20 · Demo] — [Ý/Huyền] (~30s rồi bật video)**
> Sau đây, nhóm xin trình chiếu video demo ba chức năng tốt nhất, mỗi chức năng theo mạch đầu vào → đầu ra: Dashboard thị trường; upload CV để so khớp ra phần trăm phù hợp cùng danh sách kỹ năng thiếu; và Skill Gap dẫn tới lộ trình học. Video đã quay sẵn để tránh sự cố kỹ thuật.
> *(Bật video ~10 phút. Sau video, chuyển sang kết luận.)*

---

## PHẦN V — KẾT LUẬN — (sau demo)

**[Slide 21 · Divider 05] + [Slide 22 · Điều tâm đắc] — [Ý] (~45s)**
> Nhóm tâm đắc nhất ba điều: một, hệ thống chạy thật và mọi số liệu đều có bằng chứng thô; hai, cơ chế hậu kiểm giúp chống ảo giác của mô hình ngôn ngữ, đạt Precision 98,9%; ba, định lượng được khoảng cách kỹ năng có trọng số thị trường — điều mà khớp từ khóa không làm được.

**[Slide 23 · Hạn chế] — [Huyền] (~1:00)**
> Nhóm cũng nhìn thẳng vào hạn chế. Nhãn chuẩn hiện do nhóm tự gán, chưa có kiểm định liên người gán. Chưa có baseline so sánh định lượng. Recall NER và phân loại Skill Gap chưa đạt ngưỡng. Tập đánh giá còn nhỏ và có phần giả lập. Dữ liệu CV được gửi tới Gemini nhưng chưa xử lý dữ liệu cá nhân. Và mới chỉ đo đơn phiên, chưa kiểm thử tải. Với mỗi hạn chế, nhóm đều đề xuất hướng khắc phục tương ứng ở cột bên phải.

**[Slide 24 · Hướng phát triển] — [Ý] (~45s)**
> Về hướng phát triển: nâng độ vững đánh giá bằng baseline và ablation; cải thiện thuật toán bằng lưu trữ ba trạng thái và fuzzy match; mở rộng dữ liệu đa ngành, bổ sung dữ liệu lương và phỏng vấn — đúng hai thứ người dùng mong muốn nhất; và tăng cường bảo vệ dữ liệu cá nhân cùng khả năng mở rộng quy mô.

**[Slide 25 · Cảm ơn] — [Huyền] (~15s)**
> Trên đây là toàn bộ phần trình bày. Nhóm xin cảm ơn quý thầy cô đã lắng nghe và rất mong nhận được góp ý ạ.

---

## GHI CHÚ TẬP LUYỆN
- Bấm giờ từng phần; nếu quá 20', cắt các câu *(có thể lược)* ở slide 10 và 18.
- Chuẩn bị **giấy bút** ghi lại câu hỏi hội đồng; trả lời **luân phiên**, người kia bổ sung.
- Nếu GVPB hỏi sâu về: baseline, ngưỡng, chứng chỉ, PII, pháp lý crawl, định nghĩa chỉ số, ERD/use case, case study → mở đúng **slide dự phòng D1–D10** (xem file `SLIDE_DuPhong_QA.md`).
- Đọc trước 3 bài báo đã trích (SkillSpan/Bhola/Khaouja) để trả lời nếu bị hỏi.
