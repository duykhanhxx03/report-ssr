# Báo cáo bài tập lớn: tái lập và tối ưu SSR (No More K-means, ICML 2026)

Báo cáo môn **Tìm kiếm và truy xuất thông tin** về bài báo *No More K-means:
Single-Stage Sparse Coding for Efficient Multi-Vector Retrieval* (Guo và cộng sự,
ICML 2026, [arXiv:2605.30120](https://arxiv.org/abs/2605.30120)).

| Đường dẫn | Nội dung |
|---|---|
| `latex/baocao.tex` | Mã LaTeX của báo cáo (bìa, phân công, mục lục, Mở đầu, 4 chương, Kết luận, Tài liệu tham khảo, Phụ lục A về các lỗi đã sửa trong mã nguồn). |
| `latex/baocao.pdf` | Bản PDF biên dịch sẵn (29 trang). |
| `latex/README.md` | Hướng dẫn biên dịch và các chỗ cần điền (tên nhóm, thành viên, link repo). |
| `ssr_audit.html` | Trang tổng hợp kết quả kiểm chứng dạng web (bảng số liệu, biểu đồ, đối chiếu từng tuyên bố của bài báo). |

Biên dịch bằng **XeLaTeX** (Overleaf: Menu → Compiler → XeLaTeX, chạy hai lần để
cập nhật mục lục). Font dùng TeX Gyre Termes và Latin Modern Mono, có sẵn trong TeX
Live và Overleaf.

Mã nguồn thực nghiệm (bản sửa của repo gốc, script đánh giá, kernel tối ưu, kết quả
và log) nằm ở repo riêng: https://github.com/duykhanhxx03/ssr-repro-and-optimization
