# 🚀 HƯỚNG DẪN HOÀN CHỈNH - BasicTeX + VS Code + Git + AI

## ✅ BƯỚC 1: KIỂM TRA CÀI ĐẶT

```bash
# Kiểm tra BasicTeX đã cài chưa
pdflatex --version

# Kiểm tra Git
git --version

# Kiểm tra VS Code
code --version
```

---

## 📝 BƯỚC 2: KHỞI TẠO GIT REPOSITORY

```bash
cd /Users/ymytr/Downloads/Thesis___HTTT07

# Nếu chưa có .git
git init

# Cấu hình Git (lần đầu)
git config user.name "Tên của bạn"
git config user.email "email@gmail.com"

# Add tất cả file
git add .

# Commit lần đầu
git commit -m "Initial commit: Thesis structure with 6 chapters"

# Xem status
git status
```

---

## 🎨 BƯỚC 3: BIÊN SOẠN VỚI VS CODE + AI

### **Cài AI Assistant (Copilot hoặc tương tự)**

```bash
# Nếu bạn dùng GitHub Copilot
code --install-extension GitHub.copilot

# Hoặc dùng Codeium (free, không cần đăng ký)
code --install-extension Codeium.codeium
```

### **Dùng AI để hỗ trợ viết**

1. Mở file chương bất kỳ (VD: `Chapter1/chapter1.tex`)
2. Nhấn `Ctrl+I` (hoặc `Cmd+I` trên Mac) để gọi AI
3. Yêu cầu AI: "Viết phần 1.2 Phát biểu bài toán chi tiết hơn"
4. AI sẽ suggest code → Bạn accept hoặc modify

---

## 🔄 BƯỚC 4: COMPILE & PREVIEW

### **Compile tự động (mỗi khi lưu)**
- LaTeX Workshop sẽ tự động compile
- Xem kết quả ở tab **PDF**

### **Compile thủ công**
```bash
# Từ terminal
cd /Users/ymytr/Downloads/Thesis___HTTT07

# Compile (sẽ ra main.pdf)
pdflatex -interaction=nonstopmode -file-line-error main.tex

# Nếu có tài liệu tham khảo, compile 4 lần:
pdflatex main.tex
bibtex main.aux
pdflatex main.tex
pdflatex main.tex
```

---

## 💾 BƯỚC 5: QUẢN LÝ VỚI GIT

### **Sau mỗi lần sửa**

```bash
# Xem những file thay đổi
git status

# Add những file cần commit
git add Chapter1/chapter1.tex
git add Chapter2/chapter2.tex

# Hoặc add tất cả
git add .

# Commit với message rõ ràng
git commit -m "Hoàn thành Chapter 1: Giới thiệu - thêm phần ý nghĩa"

# Xem lịch sử commit
git log --oneline
```

### **Backup lên GitHub (tùy chọn)**

```bash
# Tạo repo trên GitHub (web)
# Sau đó push lên

git remote add origin https://github.com/USERNAME/Thesis___HTTT07.git
git branch -M main
git push -u origin main
```

---

## 🔧 CẤU HÌNH BASICTEX VỚI CÁC PACKAGES CẦN THIẾT

```bash
# Update tlmgr (package manager)
tlmgr update --self

# Cài packages cần thiết cho tiếng Việt
tlmgr install babel babel-vietnamese

# Cài packages bổ sung
tlmgr install geometry xcolor hyperref listings algorithm amsmath multirow array
```

---

## ⚡ MẸO DÙNG VS CODE + AI HIỆU QUẢ

### **1. Prompt tốt để AI hỗ trợ:**

```
"Viết phần 2.1 về Quy trình ETL (Extract, Transform, Load) 
với 3 subsections chi tiết, mỗi subsection 3-4 đoạn văn, 
có trích dẫn đến công trình liên quan"
```

### **2. Dùng Comments để hướng dẫn AI:**

```latex
% TODO: Viết phần này chi tiết hơn, thêm ví dụ cụ thể
\section{Mục cần hoàn thành}
% AI sẽ biết bạn muốn gì khi sử dụng Copilot
```

### **3. Refactoring với AI:**

```
Highlight đoạn văn → Ctrl+I → "Make this more concise and academic"
```

---

## 📊 CẤU TRÚC DỰ ÁN CLEAN

```
Thesis___HTTT07/
├── .git/                    ← Git repo (tự quản lý)
├── .gitignore              ← Ignore file tạm (đã tạo)
├── main.tex                ← File chính
├── main.pdf                ← Output (ignore by git)
├── Chapter*.tex            ← Nội dung
├── Appendix/*.tex
├── References/
│   └── references.bib
├── images/                 ← Hình ảnh
└── .vscode/
    └── settings.json       ← VS Code config
```

---

## 🆘 GỢI Ý KHI COMPILE LỖI

| Lỗi | Giải pháp |
|-----|----------|
| `undefined control sequence` | Thiếu package → Thêm `\usepackage{...}` |
| `Encoding error (tiếng Việt)` | Add `\usepackage[utf8]{inputenc}` |
| `bibtex not found` | Cài: `tlmgr install bibtex` |
| `pdflatex: not found` | Re-install BasicTeX |

---

## 🎯 WORKFLOW HÀNG NGÀY

```
1. Mở VS Code → main.tex
2. Sửa/Viết → Nhất Ctrl+S (lưu)
3. LaTeX Workshop tự compile → Xem PDF
4. Lặp lại 2-3
5. Hài lòng? → git add . → git commit -m "..."
6. Lặp lại từ 2
```

---

**Cần giúp gì nữa?** 👇
- ❓ Viết phần nào cụ thể?
- ❓ Có lỗi gì khi compile?
- ❓ Cần ví dụ LaTeX nào?
