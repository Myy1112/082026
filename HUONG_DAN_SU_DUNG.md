# 📖 HƯỚNG DẪN BIÊN SOẠN LUẬN VĂN VỚI LATEX WORKSHOP TRÊN VS CODE

## 🎯 CÁCH SỬ DỤNG CƠ BẢN

### **1️⃣ MỞ PROJECT**
- Mở folder `/Thesis___HTTT07` trong VS Code
- Mở file `main.tex` (đây là file chính)

### **2️⃣ COMPILE & PREVIEW PDF**

#### **Cách A: Tự động (Recommended)**
- **Mỗi khi bạn lưu file (.tex), hệ thống tự động compile**
- Xem kết quả ở tab **PDF** bên phải

#### **Cách B: Compile thủ công**
1. Nhấn `Ctrl+Shift+P` (Mac: `Cmd+Shift+P`)
2. Gõ: `LaTeX: Build with recipe`
3. Chọn: **`pdfLatex ➔ BibTeX ➔ pdfLatex × 2`** (nếu có trích dẫn)
   - Hoặc chọn **`latexmk 🔃`** (để compile nhanh)

### **3️⃣ XEM PDF RESULT**
- **Tab PDF** sẽ hiển thị bên phải cửa sổ
- **Scroll** trực tiếp trong tab PDF
- **Tìm kiếm** trong PDF: `Ctrl+F` trong tab PDF

---

## 🔄 QUY TRÌNH COMPILE (BẮT BUỘC)

⚠️ **Lưu ý**: Khi bạn thêm tài liệu tham khảo hoặc trích dẫn mới, phải compile theo thứ tự:

```
1️⃣ pdfLatex (compile LaTeX code)
2️⃣ BibTeX (compile tài liệu tham khảo)
3️⃣ pdfLatex × 2 (compile lại 2 lần để update số hiệu tham khảo)
```

**Trong VS Code:**
- Chỉ cần chọn recipe `pdfLatex ➔ BibTeX ➔ pdfLatex × 2` → Tự động làm hết!

---

## 🎨 CÁC SHORTCUT TIỆN LỢI

| Tác vụ | Shortcut |
|--------|----------|
| **Build (Compile)** | `Ctrl+Alt+B` (Mac: `Cmd+Opt+B`) |
| **View PDF** | `Ctrl+Alt+V` (Mac: `Cmd+Opt+V`) |
| **Clean** (xóa file tạm) | `Ctrl+Shift+P` → `LaTeX: Clean up auxiliary files` |
| **Count words** | `Ctrl+Shift+P` → `LaTeX: Word count` |

---

## 📝 CẤU TRÚC DỰ ÁN CỦA BẠN

```
Thesis___HTTT07/
├── main.tex                 ← 📌 FILE CHÍNH (mở cái này!)
├── Chapter1/
│   └── chapter1.tex        ← Chương 1: Giới Thiệu
├── Chapter2/
│   └── chapter2.tex        ← Chương 2: Cơ Sở Lý Thuyết
├── Chapter3/
│   └── chapter3.tex        ← Chương 3: Thiết Kế Khung Thu Thập
├── Chapter4/
│   └── chapter4.tex        ← Chương 4: Thiết Kế Ứng Dụng
├── Chapter5/
│   └── chapter5.tex        ← Chương 5: Hiện Thực Hóa & Đánh Giá
├── Chapter6/
│   └── chapter6.tex        ← Chương 6: Kết Luận
├── Appendix/
│   ├── abstract.tex        ← Tóm tắt + Abstract
│   ├── abbreviations.tex   ← Danh mục chữ viết tắt
│   └── ... (các file khác)
├── References/
│   └── references.bib      ← 📌 TÀI LIỆU THAM KHẢO (chỉnh sửa file này!)
├── images/
│   └── (hình ảnh của bạn)
└── .vscode/
    └── settings.json       ← Cấu hình (đã tạo)
```

---

## ✏️ CÁC THAO TÁC THƯỜNG GẶP

### **A. Thêm một chương mới**

1. Tạo folder `Chapter7` mới
2. Tạo file `chapter7.tex`:
```latex
\chapter{Tên chương của bạn}
\label{Chapter7}

\section{Mục 1}
Nội dung ở đây...

\section{Mục 2}
Nội dung ở đây...
```

3. Thêm vào `main.tex`:
```latex
\include{Chapter7/chapter7}
```

### **B. Thêm hình ảnh**

1. Đặt hình vào folder `images/`
2. Trong file `.tex`, viết:
```latex
\begin{figure}[ht]
\centering
\includegraphics[width=10cm]{images/tenhinh.png}
\caption{Mô tả hình}
\label{fig:label_name}
\end{figure}
```

3. Tham chiếu: `Xem Hình \ref{fig:label_name}`

### **C. Thêm tài liệu tham khảo**

1. Mở `References/references.bib`
2. Thêm tài liệu (ví dụ):
```bibtex
@article{Smith2020,
  title={Machine Learning Basics},
  author={Smith, John},
  year={2020},
  journal={AI Journal}
}
```

3. Trong file `.tex`, trích dẫn:
```latex
Nghiên cứu của Smith~\cite{Smith2020} chỉ ra rằng...
```

4. **Compile lại** bằng recipe: `pdfLatex ➔ BibTeX ➔ pdfLatex × 2`

### **D. Thêm bảng biểu**

```latex
\begin{table}[ht]
\caption{Bảng ví dụ}
\label{tab:example}
\begin{center}
\begin{tabular}{|c|c|c|}
\hline
\textbf{Cột 1} & \textbf{Cột 2} & \textbf{Cột 3} \\
\hline
Dữ liệu 1 & Dữ liệu 2 & Dữ liệu 3 \\
\hline
\end{tabular}
\end{center}
\end{table}
```

---

## 🔍 GIẢI QUYẾT LỖI THƯỜNG GẶP

| Lỗi | Giải pháp |
|-----|----------|
| **PDF không cập nhật** | Nhấn `Ctrl+Shift+P` → `LaTeX: Clean` → Build lại |
| **Bibtex không hoạt động** | Chắc chắn compile với recipe `pdfLatex ➔ BibTeX ➔ pdfLatex × 2` |
| **Ký tự tiếng Việt bị lỗi** | Kiểm tra `\usepackage[utf8]{inputenc}` trong main.tex |
| **Compile bị treo** | Ctrl+C để dừng, sau đó Clean và Build lại |

---

## 🚀 TIPS & TRICKS

✅ **Lưu thường xuyên** - Cách 2-3 phút lưu một lần  
✅ **Dùng Comments** - `% Cái này là comment` để ghi chú  
✅ **Tìm kiếm nhanh** - `Ctrl+F` tìm trong file hiện tại  
✅ **Multiple monitors** - Để main.tex bên trái, PDF bên phải để so sánh  
✅ **Sử dụng Outline** - `Ctrl+Shift+O` để xem cấu trúc file  

---

## 📞 CẦN GIÚP GÌ TIẾP?

- ❓ Không biết cách viết phương trình toán? → Hỏi tôi!
- ❓ Cần thêm cấu trúc nào? → Hỏi tôi!
- ❓ Muốn chỉnh định dạng? → Hỏi tôi!

**Chúc bạn biên soạn luận văn tốt! 🎓**
