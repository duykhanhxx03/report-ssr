# Báo cáo bài tập lớn: tái lập và tối ưu SSR (No More K-means, ICML 2026)

Báo cáo môn **Tìm kiếm và truy xuất thông tin** (Nhóm 9, lớp M25CQHT02-B) về bài báo
*No More K-means: Single-Stage Sparse Coding for Efficient Multi-Vector Retrieval*
(Guo và cộng sự, ICML 2026, [arXiv:2605.30120](https://arxiv.org/abs/2605.30120)).

| Đường dẫn | Nội dung |
|---|---|
| `latex/baocao.tex` | Mã LaTeX của báo cáo (một file): bìa, phân công, tóm tắt, mục lục, 5 chương, tài liệu tham khảo và 5 phụ lục (chi tiết sai lệch mã nguồn; chứng minh định lý; kết quả khác của bài báo; nguồn số liệu hiệu năng; hướng dẫn chạy lại). |
| `latex/baocao.pdf` | Bản PDF biên dịch sẵn (53 trang, 30 trang thân bài). |
| `latex/figures/` | Hai hình gốc của bài báo (Hình 3 và 4); các hình còn lại vẽ bằng TikZ/pgfplots trong file `.tex`. |
| `latex/README.md` | Hướng dẫn biên dịch và các chỗ cần kiểm tra (tên nhóm, thành viên, link repo). |
| `latex/backup_v3/` | Bản trước khi chuyển bố cục (tên chương tiếng Anh theo đề cương ban đầu), để đối chiếu. |
| `KE_HOACH_CAI_THIEN_BAO_CAO.md` | Kế hoạch cải thiện báo cáo và nhật ký các đợt sửa. |
| `CHANGELOG.md` | Ghi chú chi tiết từng lần viết lại và sửa. |
| `ssr_audit.html` | Trang tổng hợp kết quả kiểm chứng dạng web (bảng số liệu, biểu đồ, đối chiếu từng tuyên bố của bài báo). |

Cấu trúc báo cáo:

1. **Bài toán, bối cảnh và mục tiêu** – bài toán truy hồi, ba họ phương pháp, pipeline PLAID, hạn chế của K-means, ý tưởng SSR và bài báo, bốn câu hỏi kiểm chứng, phạm vi.
2. **Biểu diễn thưa và huấn luyện SSR** – SAE TopK, MaxSim thưa, SSR-tok/SSR-CLS, Định lý A/B về sai lệch bị chặn, hàm mục tiêu lai, ablation, đối chiếu thiết lập huấn luyện với mã nguồn công bố.
3. **Lập chỉ mục và truy hồi** – inverted index mức neuron, SSR exact, SSR++, độ phức tạp, các điểm cần chú ý khi cài đặt.
4. **Tái lập và kiểm chứng** – kết quả công bố cần kiểm chứng; môi trường và giao thức đo; kiểm tra pipeline bằng baseline; sai lệch mã nguồn; split test và split đối chứng; MS MARCO; so sánh với PLAID và giới hạn.
5. **Cải tiến, thảo luận và kết luận** – kernel `fast_hyb`, GPU, LB-rerank, hướng không hiệu quả, thảo luận, kết luận theo từng câu hỏi kiểm chứng.

Biên dịch bằng **XeLaTeX** (Overleaf: Menu → Compiler → XeLaTeX, chạy hai lần để
cập nhật mục lục) hoặc `tectonic`. Font dùng TeX Gyre Termes và Latin Modern Mono, có
sẵn trong TeX Live và Overleaf.

Mã nguồn thực nghiệm (bản sửa của repo gốc, script đánh giá, kernel tối ưu, kết quả
và log) nằm ở repo riêng: https://github.com/duykhanhxx03/ssr-repro-and-optimization
