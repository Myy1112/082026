# KỊCH BẢN QUAY VIDEO DEMO — CareerNova (10 phút)

> Mục tiêu (theo yêu cầu GV phản biện): demo **những chức năng tốt nhất** trong ~10 phút, quay sẵn để tránh sự cố mạng/kỹ thuật.
> Phong cách theo "gu" cô Hằng: mỗi cảnh nói rõ **ĐẦU VÀO (thao tác)** → **ĐẦU RA (kết quả)**.
> Site: `career-nova.online`. Lồng tiếng: **Ý** = phần dữ liệu/thị trường; **Huyền** = phần CV/so khớp/AI (khớp phân vai trình bày).

---

## A. CHUẨN BỊ TRƯỚC KHI QUAY (bắt buộc — quyết định 80% độ mượt)

### A1. Tài khoản & dữ liệu
- [ ] **Tài khoản demo đã kích hoạt** (`is_active=true`). Nếu login yêu cầu xác thực email → bật bằng SQL: `UPDATE users SET is_active=true WHERE email='...';` (xem memory production access).
- [ ] **2 CV mẫu PDF** (1 trang, rõ chữ, ≤ 5 MB):
  - CV-A: **khớp cao** với nhóm nghề mục tiêu (VD Software Engineer / Backend) → cho ra % đẹp + radar cân đối.
  - CV-B: **khớp thấp/lệch ngành** (VD CV thiên data ứng tuyển Security) → cho ra nhiều "kỹ năng còn thiếu" + lộ trình → minh họa giá trị Skill Gap.
- [ ] **1 file sai định dạng** (VD `.docx` hoặc ảnh > 5 MB) để demo cảnh từ chối (tùy chọn, nếu còn giờ).

### A2. ⚠️ Xử lý độ trễ 42 giây của "Đối soát lần đầu" (QUAN TRỌNG NHẤT)
Đối soát CV lần đầu (cache-miss) mất **~42s** (gọi Gemini + tính vector). KHÔNG để 42s im lặng trên video. Chọn **một** cách:
- **Cách 1 (khuyên dùng):** **Đối soát TRƯỚC khi quay** cho cả CV-A và CV-B → khi quay, thao tác lại sẽ là **cache-hit (~0,3s)**, kết quả hiện gần như tức thì, video mượt. *(Không phải "giả": kết quả thật đã tính; nếu hội đồng hỏi tốc độ lần đầu, slide hiệu năng đã công bố 42s trung thực.)*
- **Cách 2:** Quay cảnh bấm "Phân tích" thật → khi hiện màn hình chờ, **tua nhanh 6–8×** hoặc cắt cảnh với chú thích "*Hệ thống đang gọi AI trích xuất & so khớp (~40s, đã đo ở báo cáo)*" rồi cắt sang kết quả.
- Dù cách nào, **nói thật**: "lần đầu mất khoảng 40 giây do gọi AI; các lần sau nhờ cache chỉ dưới 1 giây."

### A3. Công cụ & thiết lập màn hình
- [ ] Phần mềm quay: **QuickTime** (macOS) hoặc **OBS**. Quay **1080p** (1920×1080), 30fps.
- [ ] Trình duyệt **toàn màn hình**, zoom 100–110%, ẩn bookmark bar; dùng **cửa sổ ẩn danh** để không lộ tab/lịch sử cá nhân.
- [ ] Bật **hiện con trỏ + hiệu ứng click** (QuickTime có "Show mouse clicks"; OBS dùng plugin) để hội đồng thấy thao tác.
- [ ] Chuẩn bị sẵn các tab: (1) Landing, (2) Dashboard, (3) trang CV — để chuyển nhanh, tránh gõ URL.
- [ ] Tắt thông báo hệ thống (Do Not Disturb), đóng app khác.

### A4. Cách quay
- Quay **theo từng đoạn** (segment) rồi ghép — an toàn hơn quay một mạch.
- Mỗi đoạn: đọc lời thuyết minh chậm, rõ; dừng 1 nhịp sau mỗi kết quả để người xem kịp nhìn.
- Có thể **thu tiếng riêng** (voice-over) sau khi dựng hình cho sạch tiếng.

---

## B. KỊCH BẢN CHI TIẾT (tổng ~10:00)

### 🎬 Đoạn 0 — Mở đầu (0:00–0:25) · Người: Ý
| Thao tác (input) | Kết quả (output) |
|---|---|
| Mở trang chủ `career-nova.online` | Landing page hiện ra |

**Lời thuyết minh:**
> "Đây là CareerNova — nền tảng đã triển khai thật tại career-nova.online. Sau đây nhóm demo ba nhóm chức năng tốt nhất: phân tích thị trường tuyển dụng, so khớp CV với công việc, và gợi ý lộ trình học tập."

*(Lướt nhanh landing 1 vòng, không dừng lâu.)*

---

### 🎬 Đoạn 1 — Dashboard phân tích thị trường (0:25–3:15 · ~2:50) · Người: Ý
| Thao tác (input) | Kết quả (output) |
|---|---|
| Vào **Dashboard / Thị trường** | Các chỉ số tổng quan (số tin, công ty, kỹ năng) |
| Cuộn tới **Top vị trí tuyển nhiều nhất** | Biểu đồ Top vị trí |
| Xem **Top kỹ năng cầu cao / kỹ năng đang tăng** | Biểu đồ kỹ năng in-demand & rising |
| Xem **xu hướng tuyển dụng / phân bố ngành** | Biểu đồ xu hướng theo thời gian |
| Đổi **bộ lọc** (khu vực / thời gian / loại hình) | Biểu đồ cập nhật theo bộ lọc |

**Lời thuyết minh (nêu input→output):**
> "Đầu vào là bộ lọc khu vực và thời gian; đầu ra là bức tranh thị trường thời gian thực, tổng hợp từ hơn 7.000 tin tuyển dụng thật.
> Ở đây sinh viên thấy ngay: vị trí nào đang được tuyển nhiều nhất, những kỹ năng nào đang được yêu cầu nhiều và kỹ năng nào đang **tăng nhanh** — tức xu hướng nên đầu tư học.
> Khi em đổi bộ lọc sang [khu vực/khoảng thời gian], toàn bộ biểu đồ cập nhật tương ứng. Đây chính là bước 'Dữ liệu → Thông tin' giúp định hướng."

**Tip quay:** dừng ~2s ở mỗi biểu đồ; di chuột lên cột/điểm để hiện tooltip số liệu (chứng minh dữ liệu thật, tương tác được).

---

### 🎬 Đoạn 2 — Upload CV & So khớp năng lực (3:15–7:00 · ~3:45) · Người: Huyền  ⭐ TRỌNG TÂM
| Thao tác (input) | Kết quả (output) |
|---|---|
| Vào **Quản lý CV**, bấm **Tải CV lên** (chọn CV-A) | CV xuất hiện trong danh sách; đặt CV mặc định |
| *(tùy chọn)* Thử tải **file sai định dạng** | Hệ thống **báo lỗi, từ chối** — chứng minh kiểm soát biên (TC-06) |
| Chọn CV-A + **nhóm nghề mục tiêu**, bấm **Phân tích/Đối soát** | *(cache-hit)* Kết quả hiện: **% phù hợp** |
| Xem **biểu đồ radar** CV vs yêu cầu | Radar điểm mạnh/điểm yếu |
| Xem **kỹ năng đã đạt** vs **kỹ năng còn thiếu** | Danh sách phân nhóm rõ ràng |
| Di chuột vào **tooltip "Điểm phù hợp"** | Chú giải cách tính điểm (minh bạch) |

**Lời thuyết minh:**
> "Đầu vào: sinh viên tải CV lên và chọn nhóm nghề muốn hướng tới. *(Nếu demo file sai:)* Hệ thống từ chối file sai định dạng hoặc quá 5MB ngay tại biên.
> Khi bấm phân tích, hệ thống trích xuất kỹ năng từ CV bằng mô hình ngôn ngữ lớn — có cơ chế hậu kiểm bằng chứng nên gần như không nhận nhầm kỹ năng — rồi so khớp ngữ nghĩa với yêu cầu công việc.
> Đầu ra gồm ba phần: **phần trăm phù hợp**; **biểu đồ radar** cho thấy mạnh/yếu ở từng nhóm; và quan trọng nhất là **danh sách kỹ năng còn thiếu** — điều mà công cụ khớp từ khóa không làm được.
> *(Lưu ý tốc độ, nói thật:)* Lần đối soát đầu tiên mất khoảng 40 giây do phải gọi AI; các lần sau nhờ cơ chế cache chỉ còn dưới 1 giây, như quý thầy cô thấy ở đây.
> Con số điểm cũng có chú giải cách tính để người dùng hiểu rõ, không phải một con số 'hộp đen'."

**Tip quay:** đây là phần "đắt" nhất — quay kỹ, phóng to vùng radar & danh sách kỹ năng thiếu.

---

### 🎬 Đoạn 3 — Skill Gap chi tiết → Lộ trình & khóa học (7:00–8:45 · ~1:45) · Người: Huyền
| Thao tác (input) | Kết quả (output) |
|---|---|
| Bấm vào **kỹ năng còn thiếu / Xem chi tiết Skill Gap** | Trang chi tiết khoảng cách kỹ năng |
| Xem **lộ trình học được cá nhân hóa** | Danh sách kỹ năng ưu tiên theo mục tiêu |
| Xem **khóa học/tài liệu gợi ý** | Gợi ý học tập tương ứng từng kỹ năng thiếu |

**Lời thuyết minh:**
> "Từ danh sách kỹ năng còn thiếu, hệ thống gợi ý một **lộ trình học cá nhân hóa** theo mục tiêu nghề nghiệp: nên ưu tiên học kỹ năng nào trước, kèm khóa học/tài liệu tương ứng.
> Đây là bước 'Tri thức → Hành động' — biến kết quả phân tích thành việc sinh viên có thể làm ngay. Trong khảo sát, 100% người dùng đồng ý tính năng này giúp tiết kiệm thời gian tìm định hướng."

*(Tùy chọn nếu còn giờ: đối soát nhanh CV-B lệch ngành để cho thấy nhiều gap hơn → nhấn giá trị của lộ trình.)*

---

### 🎬 Đoạn 4 — Tìm kiếm & lưu việc làm (8:45–9:45 · ~1:00) · Người: Ý
| Thao tác (input) | Kết quả (output) |
|---|---|
| Vào **Tìm việc**, nhập từ khóa + bộ lọc (VD "business analyst") | Danh sách tin đúng tiêu chí |
| Bấm **Lưu** một tin | Tin vào "Cơ hội đã lưu" |
| Mở **danh sách đã lưu**, **hủy lưu** | Danh sách cập nhật đúng |

**Lời thuyết minh:**
> "Ngoài phân tích, sinh viên có thể tìm việc theo từ khóa và bộ lọc, lưu lại các cơ hội quan tâm để theo dõi. Thao tác lưu và hủy lưu gắn với từng tài khoản, làm nền cho các tính năng cá nhân hóa."

---

### 🎬 Đoạn 5 — Kết & nhắc trang Hướng dẫn (9:45–10:00 · ~0:15) · Người: Ý
| Thao tác (input) | Kết quả (output) |
|---|---|
| Mở nhanh trang **Hướng dẫn sử dụng** (4 bước + FAQ) | Trang hướng dẫn |

**Lời thuyết minh:**
> "Cuối cùng, hệ thống có trang hướng dẫn 4 bước và mục hỏi–đáp để người dùng mới bắt đầu dễ dàng. Trên đây là phần demo của nhóm, em xin cảm ơn."

---

## C. HẬU KỲ (dựng video)
- [ ] Ghép các đoạn theo thứ tự 0→5; cắt các khoảng chờ/thao tác thừa.
- [ ] Với cảnh phân tích: nếu dùng Cách 2 → tua nhanh/chú thích đoạn chờ 40s.
- [ ] Thêm **phụ đề** (caption) tiếng Việt cho từng câu thuyết minh (phòng khi loa phòng nhỏ).
- [ ] Thêm **tiêu đề chapter** mỗi đoạn (VD "1 · Dashboard thị trường") để hội đồng dễ theo dõi.
- [ ] Nhạc nền nhẹ, âm lượng thấp (tùy chọn); ưu tiên giọng thuyết minh rõ.
- [ ] Xuất **MP4 H.264, 1080p**; kiểm tra chạy được **offline** (không phụ thuộc mạng khi trình chiếu).
- [ ] Đặt tên: `CareerNova_Demo.mp4`; **copy vào máy trình bày + 1 USB dự phòng**.
- [ ] Xem lại toàn bộ 1 lượt: đủ 3 chức năng chính, mỗi cảnh rõ input→output, không lộ dữ liệu cá nhân thật.

## D. CHECKLIST NHANH TRƯỚC KHI QUAY
- [ ] Tài khoản demo hoạt động · CV-A, CV-B đã **đối soát trước** (để cache-hit)
- [ ] Trình duyệt ẩn danh, toàn màn hình, hiện click chuột, tắt thông báo
- [ ] Mạng ổn định (dù video sẽ chạy offline khi bảo vệ)
- [ ] Đã đọc thử lời thuyết minh 1 lượt, canh đúng ~10 phút
- [ ] Không hiển thị PII thật của người khác trên màn hình
