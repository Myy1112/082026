# SCRIPT TỰ ĐỌC — CareerNova (mạch kể liền lạc · nối chuyển mượt · canh giây · ~19 phút)

**[Ý]** = Trần Thị Mỹ Ý · **[Huyền]** = Thái Thị Kim Huyền
*Mẹo: câu ngắn, ngắt nghỉ rõ, nhấn chỗ in đậm. **Câu cuối mỗi slide là câu "nối" — đọc nối liền sang slide sau, đừng dừng hẳn.** Số slide khớp file CareerNova_Slide_BaoVe.pptx.*

---

**⏱ 0:00 · Slide 1 — Bìa · [Ý]**
Em kính chào quý thầy cô ạ. Em là Mỹ Ý, cùng với bạn Kim Huyền. Hôm nay nhóm em xin báo cáo khóa luận **"Đề xuất khung phân tích hỗ trợ sinh viên phân tích dữ liệu tuyển dụng"**, do cô Vũ Thị Mỹ Hằng hướng dẫn. Sản phẩm là hệ thống **CareerNova**, tụi em đã đưa lên chạy thật tại career-nova.online. Nhóm em xin trình bày khoảng 20 phút, rồi demo thêm 10 phút. *Trước tiên, em xin điểm qua nội dung bài.*

**⏱ 0:30 · Slide 2 — Nội dung · [Ý]**
Bài gồm năm phần: giới thiệu và động lực; giải pháp và phương pháp; kết quả và đánh giá; demo; và cuối cùng là kết luận. Hai đứa em sẽ thay phiên nhau nói. *Và để quý thầy cô hiểu vì sao tụi em làm đề tài này, em xin bắt đầu từ chính câu chuyện của tụi em.*

**⏱ 0:50 · Slide 3–4 — Ba thách thức · [Ý]**
Là sinh viên năm cuối, tụi em gặp ba cái khó. **Thứ nhất**, thị trường IT đổi rất nhanh, nên khó biết mình còn thiếu kỹ năng gì so với chỗ làm. **Thứ hai**, tin tuyển dụng thì nhiều nhưng nằm rải rác, mỗi nơi viết một kiểu, rất khó phân tích. **Thứ ba**, các công cụ hiện tại chủ yếu khớp từ khóa, nên không nói được mình thiếu gì, lại hay bỏ sót từ đồng nghĩa. Chính tụi em từng loay hoay với câu hỏi: "mình còn thiếu gì để đi làm được?". *Vậy các công cụ đang có đã giải quyết được ba cái khó này chưa? Em mời qua slide tiếp theo.*

**⏱ 2:20 · Slide 5 — Khoảng trống & Ý tưởng · [Ý]**
Câu trả lời là chưa. Các giải pháp hiện có khớp từ khóa nên bỏ sót từ đồng nghĩa, không đo được khoảng cách kỹ năng, dữ liệu thì đóng, và cũng không nói bạn cần học thêm gì. **Chính khoảng trống đó là lý do CareerNova ra đời.** Ý tưởng của tụi em là: dùng AI để hiểu ngữ nghĩa, có kiểm chứng bằng chứng để tránh sai; so khớp có trọng số theo thị trường IT Việt Nam; đo được khoảng cách và liệt kê kỹ năng còn thiếu; và cuối cùng là dashboard trực quan. *Từ ý tưởng đó, tụi em đặt ra mục tiêu cụ thể như sau.*

**⏱ 3:30 · Slide 6 — Mục tiêu & Kết quả · [Ý]**
Mục tiêu chia làm ba, và mỗi mục tiêu cho ra một kết quả cụ thể. Một là thu thập và chuẩn hóa dữ liệu, ra **Kết quả 1: kho dữ liệu sạch cùng quy trình ETL**. Hai là đo khoảng cách kỹ năng giữa CV và tin tuyển dụng, ra **Kết quả 2: công cụ đo Skill Gap**. Ba là trực quan hóa, ra **Kết quả 3: web CareerNova và Dashboard đã chạy thật**. Đề tài tập trung ngành CNTT ở Việt Nam, cho sinh viên năm cuối và mới ra trường. *Ba mục tiêu đó được hiện thực hóa thế nào? Em xin qua phần giải pháp — bắt đầu từ bức tranh tổng thể.*

**⏱ 4:40 · Slide 7–8 — Kiến trúc tổng thể · [Ý]**
Toàn hệ thống gồm bốn tầng. Tầng giao diện là web Next.js, có Dashboard, phân tích kỹ năng và lộ trình học. Tầng xử lý gồm Backend và một khối ETL riêng bằng Python lo việc thu thập, làm sạch. Tầng dữ liệu là PostgreSQL. Ngoài ra có Gemini để trích xuất, và mô hình SBERT với FAISS để tìm kiếm theo ngữ nghĩa. Điểm hay ở thiết kế là tụi em tách riêng phần AI nặng ra một dịch vụ riêng và có cache, nhờ vậy web luôn chạy mượt. *Bây giờ em đi vào từng mắt xích — và mắt xích đầu tiên chính là dữ liệu.*

**⏱ 5:50 · Slide 9 — Quy trình dữ liệu (ETL) · [Ý]**
Đây là Kết quả 1. Dữ liệu lấy từ bốn nguồn, rồi chạy lần lượt: thu thập, lưu tạm, biến đổi và chuẩn hóa qua AI, cuối cùng nạp vào cơ sở dữ liệu. Tại sao phải chuẩn hóa? Vì "React.js", "ReactJS" hay "react" thực ra là một, phải gom về một mối thì thống kê mới đúng. Tính tới ngày đo, cơ sở dữ liệu thật có **hơn 7.200 tin, khoảng 3.500 công ty và hơn 6.000 kỹ năng** đã chuẩn hóa, tất cả đều có ảnh chụp để chứng minh. *Có dữ liệu sạch rồi, câu hỏi tiếp theo là: làm sao lấy được kỹ năng từ một tờ CV? Phần này em xin nhường lại cho Kim Huyền.*

**⏱ 7:10 · Slide 10 — Trích xuất kỹ năng · [Huyền]**
Dạ em cảm ơn Ý. Đây cũng là phần nhóm em tâm đắc nhất, là **đóng góp thứ nhất**. Cách làm là đưa CV hoặc tin tuyển dụng vào Gemini, nó trả về danh sách kỹ năng kèm luôn câu văn chứng minh cho từng kỹ năng. Sau đó tụi em có bước **hậu kiểm**: đối chiếu lại với văn bản gốc, kỹ năng nào không có dẫn chứng thì bỏ. Tại sao cần bước này? Vì AI đôi khi **"bịa" ra kỹ năng không có thật**. Nhờ vậy độ chính xác trích xuất đạt tới **98,9%**, gần như không nhận nhầm. *Trích được kỹ năng chuẩn rồi, giờ làm sao so nó với yêu cầu công việc? Đó là nhiệm vụ của thuật toán so khớp.*

**⏱ 8:40 · Slide 11 — So khớp năng lực · [Huyền]**
Hệ thống so khớp qua bốn bước. SBERT biến kỹ năng thành vector, Cosine đo độ giống nhau giữa CV và tin tuyển dụng, rồi nhân thêm **trọng số theo thị trường**, cuối cùng áp sáu luật lọc. Kết quả không chỉ là con số phần trăm, mà **kèm danh sách kỹ năng bạn còn thiếu** — đúng cái sinh viên cần. Đây là **đóng góp thứ hai và thứ ba**. Tại sao cần trọng số? Vì một kỹ năng hiếm mà đang được săn thì phải tính nặng hơn kỹ năng phổ thông, như vậy điểm mới sát thực tế. *Những kết quả so khớp này sẽ được đưa lên giao diện cho người dùng thấy — phần trực quan hóa, em xin mời lại Ý.*

**⏱ 10:10 · Slide 12 — Trực quan hóa · [Ý]**
Dạ. Kết quả 3 là hai màn hình trực quan. Bên trái là Dashboard thị trường: vị trí nào tuyển nhiều, kỹ năng nào đang hot, và xu hướng ra sao. Bên phải là phân tích Skill Gap: một biểu đồ radar so CV của bạn với yêu cầu, chỉ rõ kỹ năng nào đã có, kỹ năng nào còn thiếu, kèm gợi ý học. Nói gọn, hệ thống biến dữ liệu thô thành việc làm được: bạn biết nên học gì và ứng tuyển vị trí nào. *Vừa rồi là toàn bộ giải pháp. Nhưng nói hay thì phải có bằng chứng — nên tiếp theo tụi em xin chứng minh hệ thống chạy thật và tốt tới đâu.*

**⏱ 11:10 · Slide 13–14 — Hệ thống chạy thật · [Ý]**
Điều tụi em vui nhất: đây **không phải bản demo cho có**, mà là hệ thống **chạy thật**, ai cũng vào được tại career-nova.online, với đủ năm phân hệ. Cả **11 trên 11 ca kiểm thử đều đạt**, và người dùng chấm điểm thiện cảm **8,56 trên 10**. *Chạy được là một chuyện, nhưng có chạy đúng không lại là chuyện khác — nên tụi em kiểm thử kỹ từng chức năng.*

**⏱ 12:00 · Slide 15 — Kiểm thử chức năng · [Ý]**
Tụi em làm một ma trận truy vết, nối từng yêu cầu với từng ca kiểm thử. Cả 11 ca đều đạt trên hệ thống thật. Hai ca khó nhất cũng qua: một ca chặn đúng file sai định dạng hoặc quá dung lượng, một ca chạy trọn cả chuỗi AI từ trích xuất tới so khớp. *Kiểm thử mới chỉ trả lời "chạy đúng không"; còn chất lượng thuật toán chính xác tới đâu, em xin mời Kim Huyền.*

**⏱ 12:45 · Slide 16 — Đánh giá thuật toán · [Huyền]**
Dạ, phần này tụi em xin trình bày **thẳng thắn**, đạt gì và chưa đạt gì. Về trích xuất: định dạng đúng 100%, độ chính xác 98,9%, F1 là 84% — đều đạt; riêng độ phủ 73% thì **chưa đạt mức 80%**, do lệch giữa tiếng Việt và tiếng Anh. Chuẩn hóa kỹ năng đạt cả ba ngưỡng. Khử trùng lặp đạt 100%, nhưng đây là tập nhỏ và có dữ liệu giả lập nên chỉ để kiểm chứng. Còn phân loại Skill Gap chỉ đạt 54,8%, **chưa đạt**; nhưng lý do rất rõ và **không phải do thuật toán sai**: cơ sở dữ liệu hiện chỉ lưu hai trạng thái "có" và "thiếu", chưa có "khớp một phần", nên 117 kỹ năng khớp một phần bị dồn vào "thiếu". Bằng chứng là điểm tổng hợp vẫn lệch rất ít so với người chấm. *Đó là về độ chính xác; còn về tốc độ thì sao, em xin mời lại Ý.*

**⏱ 14:15 · Slide 17 — Hiệu năng · [Ý]**
Dạ. Tụi em đo mỗi thao tác 20 lần. Dashboard và tải CV phản hồi dưới 2 giây. Riêng lần so khớp CV đầu tiên mất khoảng **42 giây**, nhiều nhất 55 giây, nhưng vẫn **trong mức cho phép là 60 giây**, không lần nào vượt. Từ lần thứ hai trở đi, nhờ cache nên chỉ còn **chưa tới 1 giây**. Tụi em nói thật là mới đo với một người dùng; máy chủ chỉ 2 CPU nên đông người cùng lúc có thể chậm hơn — cái này tụi em ghi nhận là hạn chế. *Số đo kỹ thuật là vậy, nhưng quan trọng là người dùng thật cảm nhận thế nào.*

**⏱ 15:15 · Slide 18 — Khảo sát người dùng · [Ý]**
Tụi em khảo sát 9 bạn đúng đối tượng mục tiêu. Điểm thiện cảm là **8,56 trên 10**, và **100% chấm từ 7 trở lên**. Vui nhất là **100% đồng ý hệ thống giúp tiết kiệm thời gian tìm định hướng** — đúng điều tụi em mong muốn. Điểm thấp nhất là độ tin cậy con số phần trăm phù hợp, và điều này **khớp đúng với hạn chế Skill Gap** vừa nói. 71% bạn muốn được giải thích cách chấm điểm, nên tụi em đã bổ sung chú thích và trang hướng dẫn ngay trên web. *Nói thì cũng đã nhiều rồi — giờ xin mời quý thầy cô xem hệ thống chạy thực tế qua video.*

**⏱ 16:15 · Slide 19–20 — Demo · [Ý → Huyền]**
Tụi em xin chiếu video demo ba chức năng hay nhất, mỗi cái theo kiểu "làm gì thì ra gì". Một là Dashboard thị trường: chọn bộ lọc là ra ngay việc làm hot và kỹ năng đang cần. Hai là tải CV lên và so khớp: ra phần trăm phù hợp, radar và danh sách kỹ năng còn thiếu. Ba là Skill Gap dẫn tới lộ trình học. Tụi em đã quay sẵn để tránh trục trặc mạng ạ.

*(→ Bật video demo ~10 phút. Xong video, đọc nối tiếp: "Vừa rồi là ba chức năng chính; sau đây em xin đi vào phần kết luận.")*

**Slide 21–22 — Điều tâm đắc · [Ý]**
Nhóm em tâm đắc nhất ba điều. Một là hệ thống **chạy thật, đo thật**, mọi con số đều có bằng chứng. Hai là cơ chế **chống việc AI bịa kỹ năng**, giúp độ chính xác đạt gần 99%. Ba là tụi em **đo được khoảng cách kỹ năng**, chỉ ra bạn còn thiếu gì — điều mà cách khớp từ khóa cũ không làm được. *Bên cạnh những điều tự hào đó, tụi em cũng thẳng thắn nhìn nhận còn nhiều hạn chế.*

**Slide 23 — Hạn chế · [Huyền]**
Dạ, và với mỗi hạn chế tụi em đều có hướng khắc phục. Nhãn dữ liệu hiện do nhóm tự gán, tới đây sẽ mời thêm người gán độc lập. Chưa có so sánh với phương pháp cũ, sẽ bổ sung thí nghiệm đối chứng. Độ phủ và Skill Gap chưa đạt, sẽ thêm trạng thái "khớp một phần". Tập đánh giá còn nhỏ, sẽ mở rộng. CV gửi qua Gemini nhưng chưa che thông tin cá nhân, sẽ ẩn danh trước khi gửi. Và mới đo một người dùng, sẽ kiểm thử với nhiều người cùng lúc. *Chính từ những hạn chế này, tụi em vạch ra hướng phát triển sắp tới.*

**Slide 24 — Hướng phát triển · [Ý]**
Dạ. Sắp tới tụi em muốn làm bốn việc: đánh giá chắc hơn bằng các thí nghiệm đối chứng; cải thiện thuật toán với trạng thái "khớp một phần"; mở rộng dữ liệu sang nhiều ngành, thêm thông tin lương và phỏng vấn; và tăng cường bảo mật cùng khả năng phục vụ đông người. Đây cũng là hai thứ người dùng mong nhất: so sánh lương và chuẩn bị phỏng vấn. *Trên đây là những gì nhóm em muốn phát triển tiếp — và cũng là phần cuối của bài.*

**Slide 25 — Cảm ơn · [Huyền]**
Trên đây là toàn bộ phần trình bày của nhóm em. Tụi em xin chân thành cảm ơn quý thầy cô đã lắng nghe, và rất mong nhận được góp ý của hội đồng ạ.

---

### Bản đồ "mạch kể" (một câu cho dễ nhớ)
Câu chuyện của em → công cụ cũ chưa giải quyết được → nên đặt mục tiêu → xây hệ thống (dữ liệu → trích xuất → so khớp → hiển thị) → chứng minh chạy thật & tốt (kiểm thử → thuật toán → tốc độ → người dùng) → xem tận mắt (demo) → tự hào gì, còn thiếu gì, đi tiếp ra sao → cảm ơn.
