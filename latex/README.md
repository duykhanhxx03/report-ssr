# Báo cáo bài tập lớn – LaTeX

- `baocao.tex`: toàn bộ báo cáo trong một file (bìa, phân công, tóm tắt, mục lục, danh mục hình/bảng/từ viết tắt, 5 chương, tài liệu tham khảo, 5 phụ lục).
- `baocao.pdf`: bản biên dịch sẵn (53 trang: 30 trang thân bài, còn lại là phần đầu, tài liệu tham khảo và phụ lục).
- `figures/`: hai hình gốc của bài báo (`paper_fig3_efficiency.pdf`, `paper_fig4_sensitivity.pdf`, Hình 3 và 4 của bài, trích từ bản dịch). Mọi sơ đồ và biểu đồ khác vẽ bằng TikZ/pgfplots ngay trong file `.tex`.
- `logo_ptit.png`: logo trên trang bìa.
- `backup_v3/`: bản trước khi chuyển bố cục theo `../KE_HOACH_CAI_THIEN_BAO_CAO.md` (5 chương mang tên tiếng Anh theo đề cương ban đầu, 52 trang). Chỉ giữ để đối chiếu; nhóm đã chọn giữ tên chương tiếng Việt hiện tại.

## Cấu trúc 5 chương

1. Bài toán, bối cảnh và mục tiêu – bài toán truy hồi, BM25/SVR/MVR, pipeline PLAID, hạn chế của K-means, ý tưởng SSR và bài báo, nghiên cứu liên quan, bốn câu hỏi kiểm chứng (K1–K4), phạm vi, phương pháp.
2. Biểu diễn sparse và huấn luyện SSR – biểu diễn sparse, SAE TopK, sparse MaxSim (công thức (4)), SSR-tok/SSR-CLS, Định lý A/B về sai lệch bị chặn (phát biểu, ý nghĩa, điều kiện áp dụng; chứng minh ở Phụ lục B), hàm mục tiêu hybrid training, ablation, đối chiếu thiết lập huấn luyện với mã nguồn.
3. Lập chỉ mục và truy hồi – inverted index mức neuron (posting mức token và mức tài liệu), SSR exact, SSR++ với điều kiện bỏ block, độ phức tạp, các điểm cần chú ý khi cài đặt.
4. Tái lập và kiểm chứng – bảng câu hỏi/phép kiểm tra/kết quả/giới hạn; kết quả công bố cần kiểm chứng; môi trường và giao thức đo; kiểm tra pipeline bằng baseline; 10 điểm sai lệch (9 đã xử lý); split test và split train/dev đối chứng; MS MARCO re-ranking; so sánh với PLAID và giới hạn.
5. Cải tiến, thảo luận và kết luận – nút thắt đã đo; kernel `fast_hyb`; kết quả trên cùng 100 query (29,6 lần so với repo exact, 12 luồng), GPU; LB-rerank; hướng không hiệu quả; thảo luận; kết luận theo K1–K4 và ba hướng phát triển.

Phụ lục: A. chi tiết sai lệch và bản sửa, trích log; B. chứng minh Định lý A/B; C. các kết quả khác của bài báo (Bảng 1 đầy đủ trang ngang, LLM, LoTTE, LIMIT, CPU, h/K, độ nhạy); D. nguồn của từng số liệu hiệu năng (file, tập query, luồng, thiết bị, phạm vi đo); E. hướng dẫn chạy lại.

## Biên dịch

Dùng **XeLaTeX** (file dùng `fontspec` với font TeX Gyre Termes / Latin Modern Mono, có sẵn trong TeX Live và Overleaf).

- Overleaf: tải lên cả thư mục `latex/` (gồm `figures/` và `logo_ptit.png`), Menu → Compiler → **XeLaTeX**, Recompile (chạy 2 lần để mục lục cập nhật).
- Máy cá nhân có TeX Live/MiKTeX: `xelatex baocao.tex` (2 lần), hoặc `tectonic baocao.tex`.

## Chỗ cần kiểm tra lại

Ở đầu file, các lệnh `\newcommand`:

- `\TenGV`, `\Lop`, `\SoNhom`
- `\ThanhVienA` … `\ThanhVienE` (họ tên – mã học viên)
- `\RepoNhom` (link GitHub của nhóm)

Bảng phân công nhiệm vụ và bảng tự đánh giá nằm ngay sau trang bìa (có chú thích trong file); phân công ghi đúng tên năm chương hiện tại kèm các mục phụ trách, nhóm sửa người thực hiện cho đúng thực tế nếu cần. Mục lục chỉ hiện tới cấp section (`\setcounter{tocdepth}{1}`); đổi lại 2 nếu quy định môn học yêu cầu.
