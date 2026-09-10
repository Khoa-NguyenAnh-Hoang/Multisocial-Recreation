# MultiSocial — Springer LNCS Paper

## Cấu trúc thư mục

```
paper/
├── main.tex                  % Entry point — compile file này
├── llncs.cls                 % Springer LNCS class (cần tải từ Overleaf/Springer)
├── README.md                 % File này
│
├── sections/
│   ├── 00_abstract.tex       % Abstract (~150 từ)
│   ├── 01_introduction.tex   % 1. Giới thiệu
│   ├── 02_related_work.tex   % 2. Công trình liên quan
│   ├── 03_dataset.tex        % 3. Xây dựng Dataset
│   ├── 04_methodology.tex    % 4. Phương pháp
│   ├── 05_results.tex        % 5. Kết quả & Thảo luận
│   ├── 06_conclusion.tex     % 6. Kết luận & Hướng phát triển
│   └── references.bib        % Danh sách tài liệu tham khảo (BibTeX)
│
├── figures/
│   ├── cm_baseline_en.png    % Confusion matrix: Baseline — EN
│   ├── cm_baseline_vi.png    % Confusion matrix: Baseline — VI
│   ├── cm_baseline_zh.png    % Confusion matrix: Baseline — ZH
│   ├── cm_baseline_ar.png    % Confusion matrix: Baseline — AR
│   ├── cm_finetuned_en.png   % Confusion matrix: XLM-R fine-tuned — EN
│   ├── cm_finetuned_vi.png   % Confusion matrix: XLM-R fine-tuned — VI
│   ├── cm_finetuned_zh.png   % Confusion matrix: XLM-R fine-tuned — ZH
│   ├── cm_finetuned_ar.png   % Confusion matrix: XLM-R fine-tuned — AR
│   └── roc_combined.png      % ROC curves — Qwen2.5-1.5B PPL (4 ngôn ngữ)
│
└── tables/                   % (Bảng phức tạp có thể tách ra đây)
```

## Hướng dẫn biên dịch

1. Tải `llncs.cls` từ Overleaf: https://www.overleaf.com/latex/templates/springer-lecture-notes-in-computer-science/kzwwpvhwnvfj
   hoặc từ Springer: https://resource-cms.springernature.com/springer-cms/rest/v1/content/19238648/data/v8
   Đặt file `llncs.cls` vào thư mục `paper/`.

2. Biên dịch bằng pdflatex + biber:
   ```
   pdflatex main.tex
   biber main
   pdflatex main.tex
   pdflatex main.tex
   ```
   Hoặc dùng Overleaf (upload toàn bộ thư mục).

## Thông tin bài báo

- **Tiêu đề:** Phát hiện Văn bản do Máy Tạo Ra trên Mạng Xã Hội Đa Ngôn Ngữ
- **Chuẩn:** Springer LNCS (Lecture Notes in Computer Science)
- **Giới hạn:** 6 trang (~3,500–4,500 từ + hình/bảng)
- **Tác giả:** Hoàng Nguyễn Anh Khoa (23520736@gm.uit.edu.vn), UIT
- **GVHD:** Lưu Thanh Sơn
