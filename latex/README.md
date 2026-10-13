# Báo cáo bài tập lớn – LaTeX

- `baocao.tex`: toàn bộ báo cáo trong một file (bìa, phân công, tóm tắt, mục lục, danh mục hình/bảng/từ viết tắt, 5 chương, tài liệu tham khảo, 2 phụ lục).
- `baocao.pdf`: bản biên dịch sẵn (52 trang).
- `figures/`: hai hình gốc của bài báo (`paper_fig3_efficiency.pdf`, `paper_fig4_sensitivity.pdf`, Hình 3 và 4 của bài, trích từ bản dịch). Mọi sơ đồ và biểu đồ khác vẽ bằng TikZ/pgfplots ngay trong file `.tex`.
- `logo_ptit.png`: logo trên trang bìa.

## Cấu trúc 5 chương

1. Background & Motivation – bài toán truy hồi, BM25/SVR/MVR, pipeline PLAID, hạn chế của K-means, ý tưởng SSR, nghiên cứu liên quan, mục tiêu/phạm vi của báo cáo.
2. Sparse Representation & Late Interaction – biểu diễn thưa, MaxSim thưa (công thức (4)), hai biến thể SSR-tok/SSR-CLS, Định lý A/B về sai lệch bị chặn.
3. Hybrid Training of Sparse Projectors – SAE TopK, các thành phần hàm mất mát, ablation của bài báo, đối chiếu thiết lập huấn luyện với mã nguồn và issue trên GitHub.
4. Indexing & Retrieval: SSR và SSR++ – chỉ mục ngược mức neuron, hai thuật toán, độ phức tạp, các điểm cần chú ý khi cài đặt.
5. Experiments, Code Improvement & Conclusion – kết quả của bài báo; cài đặt, kiểm chứng và tái lập của nhóm (10 lỗi đã sửa, kết quả theo split, MS MARCO, so với PLAID); tối ưu kernel truy hồi (`fast_hyb`, GPU, LB-rerank); thảo luận; kết luận và hướng phát triển.

## Biên dịch

Dùng **XeLaTeX** (file dùng `fontspec` với font TeX Gyre Termes / Latin Modern Mono, có sẵn trong TeX Live và Overleaf).

- Overleaf: tải lên cả thư mục `latex/` (gồm `figures/` và `logo_ptit.png`), Menu → Compiler → **XeLaTeX**, Recompile (chạy 2 lần để mục lục cập nhật).
- Máy cá nhân có TeX Live/MiKTeX: `xelatex baocao.tex` (2 lần), hoặc `tectonic baocao.tex`.

## Chỗ cần kiểm tra lại

Ở đầu file, các lệnh `\newcommand`:

- `\TenGV`, `\Lop`, `\SoNhom`
- `\ThanhVienA` … `\ThanhVienE` (họ tên – mã học viên)
- `\RepoNhom` (link GitHub của nhóm)

Bảng phân công nhiệm vụ và bảng tự đánh giá nằm ngay sau trang bìa (có chú thích trong file); nhóm sửa trực tiếp cho đúng thực tế.
