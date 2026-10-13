# Báo cáo bài tập lớn: tái lập và tối ưu SSR (No More K-means, ICML 2026)

Báo cáo môn **Tìm kiếm và truy xuất thông tin** (Nhóm 9, lớp M25CQHT02-B) về bài báo
*No More K-means: Single-Stage Sparse Coding for Efficient Multi-Vector Retrieval*
(Guo và cộng sự, ICML 2026, [arXiv:2605.30120](https://arxiv.org/abs/2605.30120)).

| Đường dẫn | Nội dung |
|---|---|
| `latex/baocao.tex` | Mã LaTeX của báo cáo (một file): bìa, phân công, tóm tắt, mục lục, 5 chương, tài liệu tham khảo, Phụ lục A (chi tiết các lỗi đã sửa trong mã nguồn) và Phụ lục B (hướng dẫn chạy lại). |
| `latex/baocao.pdf` | Bản PDF biên dịch sẵn (52 trang). |
| `latex/figures/` | Hai hình gốc của bài báo (Hình 3 và 4); các hình còn lại vẽ bằng TikZ/pgfplots trong file `.tex`. |
| `latex/README.md` | Hướng dẫn biên dịch và các chỗ cần kiểm tra (tên nhóm, thành viên, link repo). |
| `ssr_audit.html` | Trang tổng hợp kết quả kiểm chứng dạng web (bảng số liệu, biểu đồ, đối chiếu từng tuyên bố của bài báo). |

Cấu trúc báo cáo:

1. **Background & Motivation** – bài toán truy hồi, ba họ phương pháp, pipeline PLAID, hạn chế của K-means, ý tưởng SSR, mục tiêu và phạm vi của báo cáo.
2. **Sparse Representation & Late Interaction** – biểu diễn thưa, MaxSim thưa, SSR-tok/SSR-CLS, Định lý A/B về sai lệch bị chặn.
3. **Hybrid Training of Sparse Projectors** – SAE TopK, các thành phần hàm mất mát, ablation, đối chiếu thiết lập huấn luyện với mã nguồn công bố.
4. **Indexing & Retrieval: SSR và SSR++** – chỉ mục ngược mức neuron, hai thuật toán, độ phức tạp, các điểm cần chú ý khi cài đặt.
5. **Experiments, Code Improvement & Conclusion** – kết quả của bài báo; tái lập, sửa lỗi và kiểm chứng của nhóm; tối ưu kernel truy hồi; thảo luận, kết luận.

Biên dịch bằng **XeLaTeX** (Overleaf: Menu → Compiler → XeLaTeX, chạy hai lần để
cập nhật mục lục) hoặc `tectonic`. Font dùng TeX Gyre Termes và Latin Modern Mono, có
sẵn trong TeX Live và Overleaf.

Mã nguồn thực nghiệm (bản sửa của repo gốc, script đánh giá, kernel tối ưu, kết quả
và log) nằm ở repo riêng: https://github.com/duykhanhxx03/ssr-repro-and-optimization
