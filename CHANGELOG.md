# Ghi chú viết lại báo cáo LaTeX (13/10/2026)

File này ghi lại những gì đã làm khi viết lại báo cáo `latex/baocao.tex` theo cấu trúc 5 chương, để các thành viên trong nhóm biết nội dung nào lấy từ đâu và còn chỗ nào cần kiểm tra.

## 1. Kết quả

| File | Trạng thái |
|---|---|
| `latex/baocao.tex` | Viết lại hoàn toàn, một file duy nhất, 2.117 dòng. Bản cũ (4 chương) vẫn còn trong lịch sử git. |
| `latex/baocao.pdf` | Biên dịch lại, 52 trang. |
| `latex/figures/` | Thư mục mới: 2 hình gốc của bài báo (PDF); các hình khác vẽ bằng TikZ/pgfplots (xem mục 5b). |
| `latex/logo_ptit.png` | Logo trên trang bìa, lấy từ file docx. |
| `latex/README.md`, `README.md` | Cập nhật mô tả cấu trúc mới và cách biên dịch. |

Chưa commit vào git. `git status` hiện có: `M README.md`, `M latex/README.md`, `M latex/baocao.pdf`, `M latex/baocao.tex`, `?? latex/figures/`, `?? latex/logo_ptit.png`.

## 2. Nguồn đã dùng

| Nguồn | Lấy gì |
|---|---|
| `Nhom9_NoMoreKMeans.docx` | Khung 5 chương, phần lý thuyết (Chương 1 đến 4), bảng từ viết tắt, tên 5 thành viên, lớp, logo, 6 biểu đồ matplotlib vẽ từ số liệu bài báo. |
| `ban dich/Nhom_9_No_More_Kmeans.zip` (bản dịch bài báo) | Thuật ngữ, công thức (4) đến (12), Phụ lục A (Định lý A, B), các bảng kết quả của bài báo, 4 hình gốc `figure1_vi.pdf`, `figure2_vi.pdf`, `figure3_goc_nguyen_ban.pdf`, `figure4_goc_nguyen_ban.pdf`. |
| `ssr-repro-and-optimization/` (repo thực nghiệm) | Toàn bộ số liệu của nhóm: `README.md`, `opt/results/summary.md`, `opt/results/comparison.md`, `opt/results/bound_tightness.json`, `results/plaid_bench/plaid.json`, `results/plaid_bench/ssr.json`, `logs/quora_summary.txt`, `logs/msmarco_rerank.log`, `logs/A_fixed_nfcorpus.log`, `logs/plaid_bench.log`, `ssr_paper_fixes.patch`. |
| `latex/baocao.tex` cũ (4 chương) | Preamble (font, định dạng PTIT), bảng lỗi, bảng kết quả, hình TikZ/pgfplots (kiểm tra theo split, độ trễ, sơ đồ tối ưu), Phụ lục A chi tiết lỗi. |

## 3. Cấu trúc mới và nguồn từng phần

Tiêu đề 5 chương giữ nguyên tiếng Anh như yêu cầu, kể cả `\protect\newline` ở chương 5.

| Phần | Nội dung | Nguồn chính | Mới viết thêm |
|---|---|---|---|
| Bìa, phân công, tự đánh giá | 5 thành viên, nhóm 9, lớp M25CQHT02-B, ngành Hệ thống thông tin | docx | Bảng phân công 5 người (gán theo chương, cần nhóm sửa lại) |
| Tóm tắt | Ý tưởng SSR, số liệu bài báo, kết quả tái lập và tối ưu của nhóm | docx (khung) + repo (số liệu) | Điền toàn bộ chỗ `[ĐIỀN]` |
| Chương 1. Background & Motivation | Bài toán IR, BM25/SVR/MVR, pipeline PLAID, hạn chế K-means, ý tưởng SSR, nghiên cứu liên quan | docx Ch1 | 1.5.2 Thông tin xuất bản; 1.7 Mục tiêu, phạm vi, phương pháp, cấu trúc báo cáo (từ phần Mở đầu cũ) |
| Chương 2. Sparse Representation & Late Interaction | Dense sang sparse, MaxSim thưa, ví dụ tính tay, SSR-tok/CLS, Định lý A và B | docx Ch2 + bản dịch Phụ lục A | Đoạn "Thứ tự các phép toán" giải thích vì sao mã gốc tính sai; nhận xét về cận trên lỏng (liên hệ 5.4.5) |
| Chương 3. Hybrid Training of Sparse Projectors | SAE TopK, 4 thành phần loss, L_CE, ablation và độ nhạy | docx Ch3 + bản dịch | 3.7 Đối chiếu thiết lập huấn luyện: bài báo, mã nguồn, trả lời của tác giả trong issue, cách nhóm xử lý |
| Chương 4. Indexing & Retrieval: SSR và SSR++ | Inverted index mức neuron, Thuật toán 4.1 và 4.2, độ phức tạp, Bảng 5 của bài | docx Ch4 | 4.7 Những điểm cần chú ý khi cài đặt (4 lỗi mã gốc mắc phải) |
| Chương 5. Experiments, Code Improvement & Conclusion | 5.1 và 5.2 kết quả bài báo; 5.3 tái lập của nhóm; 5.4 tối ưu; 5.5 thảo luận; 5.6 kết luận | docx Ch5 (khung, số liệu bài báo) + baocao.tex cũ Chương 3 và 4 (số liệu nhóm) | 5.2.6 Các phiên bản bài báo và vấn đề độ đo; 5.4.6 Tổng kết phần cải tiến; 5.5.4 Tác động xã hội |
| Tài liệu tham khảo | Gộp danh mục của docx và của bản cũ | cả hai | Thêm COIL, XTR, WARP, LIMIT, sparse coding |
| Phụ lục A | Chi tiết 10 lỗi kèm mã trước và sau | baocao.tex cũ | Thêm mục Lỗi 8 (dựng chỉ mục corpus lớn) |
| Phụ lục B | Hướng dẫn chạy lại thí nghiệm | README của repo | Mới |

Các chỗ trống `[ĐIỀN]` trong docx (môi trường, commit, kết quả tái lập, cải tiến, nhật ký thí nghiệm) đã được thay bằng số liệu thật; các ghi chú mẫu kiểu "Lỗi thường gặp cần tránh", "HÌNH CẦN CHÈN", Phụ lục checklist và script vẽ của docx không đưa vào báo cáo.

## 4. Số liệu của nhóm đã đưa vào

- Môi trường: i5-12400F, 32 GB RAM, RTX 5060 8 GB, Windows 11, Python 3.13, PyTorch 2.11, PyLate 1.6, numba 0.61; commit `c64bc05`; checkpoint SSR-tok tải 11/10/2026.
- Kiểm tra pipeline bằng ColBERTv2 và BM25 (Bảng 5.10).
- 10 lỗi trong mã nguồn (Bảng 5.11) và chi tiết ở Phụ lục A.
- nDCG@10 split test: NFCorpus 43,97; SciFact 87,83; FiQA 41,41; Quora 85,42 (Bảng 5.12).
- Kiểm tra theo split train/dev so với test cho ColBERTv2, backbone dense và SSR-tok (Bảng 5.13, Hình 5.7).
- MS MARCO re-rank BM25 top-100: SSR-tok 23,18 MRR@10 so với ColBERTv2 35,86 (Bảng 5.14).
- So với PLAID trên FiQA: dựng chỉ mục, kích thước, ms/query, nDCG test và dev (Bảng 5.15), đối chiếu từng tuyên bố (Bảng 5.16).
- Tối ưu: kernel `fast_hyb` 1/6/12 luồng, GPU exact, SSR++ tăng tốc (Bảng 5.19, Hình 5.9); LB-rerank và các cấu hình SSR++ trên FiQA dev (Bảng 5.20); độ chặt cận trên (Bảng 5.22).

## 5. Hình ảnh

| Hình trong báo cáo | File | Nguồn |
|---|---|---|
| 1.2 PLAID so với SSR; 1.3 tổng quan SSR | `paper_fig2_paradigms.pdf`, `paper_fig1_overview.pdf` | Hình 1, 2 của bài báo (bản dịch), có ghi "Nguồn" trong chú thích |
| 5.4 hiệu quả pipeline; 5.5 độ nhạy h và K | `paper_fig3_efficiency.pdf`, `paper_fig4_sensitivity.pdf` | Hình 3, 4 của bài báo |
| 3.2 ablation; 3.3 độ nhạy α, β, γ; 5.1 BEIR trung bình; 5.2 LIMIT; 5.3 thời gian lập chỉ mục; 5.6 K theo miền | `ablation_loss.png`, `sensitivity_abg.png`, `beir_avg.png`, `limit_recall5.png`, `index_time_cpu.png`, `k_by_domain.png` | Biểu đồ matplotlib trong docx, vẽ từ số liệu bài báo |
| 1.1 SVR so với MVR; 2.1 luồng biến đổi token; 2.2 phân rã sai số; 3.1 tổng quan huấn luyện; 4.1 cấu trúc inverted index; 4.2 sơ đồ SSR++; 5.8 vị trí tối ưu | TikZ trong `baocao.tex` | Vẽ lại (các sơ đồ trong docx có chữ thô như `x^T y`, `R^768` nên không dùng) |
| 5.7 chất lượng theo split; 5.9 độ trễ FiQA | pgfplots trong `baocao.tex` | baocao.tex cũ, số liệu từ repo |

Hình 3.1 vẽ lại thay vì dùng hình docx vì hình docx ghi "backbone đóng băng", trong khi tác giả xác nhận BERT không đóng băng.

## 5b. Rà soát và vẽ lại hình (lần 3)

Sau khi nhóm góp ý Hình 1.2 chưa ổn, toàn bộ hình được xem lại ở độ phân giải cao. Kết quả:

| Hình | Vấn đề | Cách sửa |
|---|---|---|
| 1.2 PLAID so với SSR | Hình dịch từ bài báo, nhãn lẫn lộn ("Danh sách đảo", "nơ-ron", "SSR của chúng tôi"), chữ nhỏ, rối | Vẽ lại bằng TikZ: hai pipeline đặt song song, tách cột "Lập chỉ mục (offline)" và "Truy hồi (online)", tô đỏ bước K-means, tô xanh các bước của SSR |
| 1.3 tổng quan SSR | Hình dịch từ bài báo, ba panel khó đọc, nhãn "MVR đặc", "vectơ" | Thay bằng biểu đồ pgfplots chất lượng so với độ trễ, vẽ từ Bảng 1 của bài, có tên từng phương pháp |
| 1.1 SVR so với MVR | Nhãn "Ma trận M × chiều" khó hiểu | Viết lại nhãn bốn bước mỗi bên |
| 2.1 luồng biến đổi token | Ghi chú đè lên mũi tên | Bố trí lại thành hai hàng, ghi chú đưa vào ô inverted index |
| 3.1 tổng quan huấn luyện | Mũi tên cong chồng nhau | Xếp ba loss không giám sát thành cột bên trái, nối bằng mũi tên thẳng hoặc gấp khúc |
| 4.1 cấu trúc inverted index | Ví dụ không nhất quán (D1 có neuron 12 nhưng posting list I_12 không chứa D1) | Làm lại ví dụ với 3 tài liệu, 4 posting list, mũi tên nối đủ các cặp tài liệu và neuron, ghi rõ block 2 phần tử chỉ để minh họa |
| 4.2 sơ đồ SSR++ | Hai hàng lệch | Gộp thành một hàng |
| 5.9 độ trễ FiQA | Nhãn trên cột in giá trị log (1,28; 1,73) thay vì ms | Dùng `point meta=rawx`, in "1.635 ms", "54 ms"... |
| 3.2, 3.3, 5.1, 5.2, 5.3, 5.6 | Biểu đồ PNG từ docx: nhãn tiếng Anh thô, trục "Gio" thiếu dấu, font khác báo cáo | Vẽ lại bằng pgfplots (ybar, groupplots, đồ thị đường), dấu phẩy thập phân, tô màu riêng các cột SSR |
| 5.4, 5.5 (Hình 3, 4 của bài) | Hình gốc tiếng Anh, rõ ràng | Giữ nguyên |
| 2.2, 5.7, 5.8 | Ổn | Giữ nguyên |

Các file không còn dùng đã xóa khỏi `latex/figures/`: 6 file PNG và `paper_fig1_overview.pdf`, `paper_fig2_paradigms.pdf`. Thư mục này giờ chỉ còn `paper_fig3_efficiency.pdf` và `paper_fig4_sensitivity.pdf`. Preamble thêm `\usepgfplotslibrary{groupplots}` và đặt dấu phẩy thập phân cho mọi trục pgfplots.

## 6. Thay đổi kỹ thuật trong preamble

- Thêm `amsthm` (Định lý A, B), `float`, `algorithm` + `algpseudocode` (đổi tên "Thuật toán", "Đầu vào", "Đầu ra"), `\graphicspath{{figures/}}`.
- Thêm `\PassOptionsToPackage{hyphens}{url}`, `\Urlmuskip`, `\emergencystretch` để URL và đường dẫn ngắt dòng được.
- Đặt lại `\topfraction`, `\bottomfraction`, `\textfraction`, `\floatpagefraction` để bớt trang trống do hình và bảng.
- `\hypersetup{pageanchor=false}` quanh trang bìa để tránh cảnh báo trùng anchor trang; thêm `pdftitle`, `pdfauthor`.
- Cột tên học viên trong bảng phân công và tự đánh giá dùng `\raggedright` để không bị giãn chữ.
- Các macro mới: `\Rb`, `\bz`, `\bx`, `\by`, `\bq`, `\bd`, `\Wenc`, `\Wdec`, `\bpre`, `\benc`, `\AK`, `\TopK`, `\supp`, `\simscore`.

## 7. Rà soát văn phong và thuật ngữ (lần 2)

Theo yêu cầu: bỏ em dash, văn phong tự nhiên, bỏ dấu hiệu lập luận máy móc, giữ nguyên thuật ngữ.

**Dấu gạch ngang.** Không còn gạch ngang dùng làm dấu câu trong phần chữ. Các chỗ đã đổi: "Tầng I -- Sinh ứng viên" thành "Tầng I: sinh ứng viên"; "Bước 1 -- bất đẳng thức tam giác" thành "Bước 1: ..."; "truy vấn -- tài liệu" thành "truy vấn và tài liệu"; "thô--tinh" thành "từ thô đến tinh"; "cộng--max" thành "cộng rồi max"; "đếm--điền" thành "đếm rồi điền"; "Cauchy--Schwarz" thành "Cauchy-Schwarz"; "Dày -- ColBERT" thành "Dense (ColBERT)"; hai dòng chú thích đầu file dùng "–" đổi thành "-". Gạch nối trong khoảng số (16--19 điểm, 0,22--0,32, pp. 39--48) và trong tham số dòng lệnh (`--split`) giữ nguyên.

**Thuật ngữ giữ tiếng Anh**, thống nhất toàn bài theo bản dịch của nhóm:

| Trước | Sau |
|---|---|
| bộ tự mã hóa thưa | Sparse Autoencoder (SAE) |
| truy hồi đa vector / đơn vector | Multi-Vector Retrieval (MVR) / Single-Vector Retrieval (SVR) |
| truy hồi từ vựng; truy hồi thưa học được | lexical retrieval; learned sparse retrieval |
| tương tác muộn | late interaction |
| chỉ mục ngược; danh sách posting; chỉ mục xuôi | inverted index; posting list; forward index |
| mã thưa; mã hóa thưa; bộ chiếu thưa | sparse code; sparse coding; sparse projector |
| biểu diễn / embedding / điểm "dày" | dense |
| phân cụm; tâm cụm | clustering; centroid |
| cắt tỉa; cắt tỉa an toàn; lọc thô | pruning; safe pruning; chấm điểm thô |
| phần dư; lượng tử hóa; số chiều ẩn; siêu vị trí; token giả | residual; quantization; hidden dimension; superposition; pseudo-token |
| hàm mất mát / tổn thất (tái tạo, tương phản, phụ) | loss (reconstruction, contrastive, auxiliary) |
| khối (posting); bộ đệm; mặt nạ; bộ nạp dữ liệu; bộ chuẩn; độ thưa | block; buffer; mask; data loader; benchmark; sparsity |
| đánh chỉ mục | lập chỉ mục |

Cột "Giải thích" trong bảng từ viết tắt vẫn để tiếng Việt vì đó là phần diễn giải cho người đọc.

**Văn phong.** Đã bỏ hoặc viết lại các cụm: "Thứ nhất / Thứ hai / Thứ ba / Thứ tư", "Điểm mấu chốt là", "Ý then chốt", "Điểm cần ghi nhớ", "Về trực giác", "Cần phân biệt rõ", "Cần lưu ý", "Hai hệ quả quan trọng", "Hệ quả quan trọng", "Quan trọng hơn", "Đáng chú ý là", "Tóm lại", "Nhóm cũng xin nêu ba nhận xét phản biện", "là một luận điểm nối lý thuyết với thực nghiệm", "hệ thống hóa ba trụ cột", "hoàn tất chuỗi lý luận", "Bốn điểm cần rút ra", "biện minh cho việc". Các đoạn mở và kết chương, mục 2.5.5 (nhận xét về định lý), đoạn đọc Bảng 1 của bài báo, mục 5.4.6 (tổng kết tối ưu) đã viết lại thành câu thường. Tiêu đề 2.5.5 đổi thành "Ý nghĩa và nhận xét", 5.2.6 thành "Các phiên bản của bài báo và vấn đề độ đo".

## 8. Kiểm tra biên dịch

- Máy không có XeLaTeX nên dùng Tectonic 0.15 (engine XeTeX) tải vào thư mục tạm; kết quả tương đương Overleaf với compiler XeLaTeX.
- Biên dịch sạch: không có tham chiếu, trích dẫn hay nhãn lỗi; không còn cảnh báo trùng anchor trang.
- Còn một dòng tràn lề 5pt ở Phụ lục A (tên hàm `load_ssr_checkpoint` dài), không ảnh hưởng.
- Cảnh báo font `OT1/texgyretermes` trong log là của gói `newtxmath`, có từ bản cũ, không ảnh hưởng hiển thị.
- Đã xem lại hình ảnh các trang: bìa, phân công, mục lục, mở đầu từng chương, các bảng rộng (Bảng 1 của bài, bảng lỗi, bảng hiệu năng, bảng vị trí tối ưu), thuật toán, phụ lục.

## 9. Nhóm cần kiểm tra lại

- Bảng phân công nhiệm vụ: hiện gán theo chương (Toàn: Chương 1 và tổng hợp; Thọ: Chương 2 và dịch; Nguyên: Chương 3 và dịch; Khánh: cài đặt, sửa lỗi, tối ưu, Chương 4 và mục 5.3 đến 5.4; Khamsing: mục 5.1 đến 5.2, thảo luận, slide). Sửa cho đúng thực tế.
- Bảng tự đánh giá: đang để điểm mặc định.
- Tên giảng viên (`\TenGV`) lấy từ bản cũ, docx không ghi.
- Lỗi số 10 trong Bảng 5.11 (`token_skip_mode`) vẫn ở trạng thái "Chưa sửa", đúng với repo.
- Chưa commit git; nếu đồng ý thì commit cả `latex/figures/` và `latex/logo_ptit.png`.

## 10. Cách biên dịch

- Overleaf: tải lên cả thư mục `latex/` (gồm `figures/` và `logo_ptit.png`), Menu, Compiler, XeLaTeX, Recompile hai lần.
- Máy cá nhân: `xelatex baocao.tex` hai lần, hoặc `tectonic baocao.tex`.

## 11. Cải thiện theo `KE_HOACH_CAI_THIEN_BAO_CAO.md` (lần 4, 13/10/2026)

Làm theo lộ trình 7 đợt ở mục 8 của kế hoạch. Bản trước khi sửa được giữ ở `latex/backup_v3/` (tex và pdf, 52 trang).

**Bố cục mới (phương án mục 2 của kế hoạch, giữ 5 chương).** Tên chương Việt hóa; nội dung chuyển như sau:

| Chương mới | Nguồn từ bản cũ | Trang |
|---|---|---|
| 1. Bài toán, bối cảnh và mục tiêu | Chương 1, rút 1.1.1, 1.1.2, 1.5.2, 1.6; thêm bốn câu hỏi kiểm chứng K1–K4 | 1–5 |
| 2. Biểu diễn sparse và huấn luyện SSR | Chương 2 + Chương 3; gộp hai mục giới thiệu SAE; chứng minh Định lý A/B xuống Phụ lục B; bỏ Hình phân rã sai số và Hình ablation; bảng/hình độ nhạy xuống Phụ lục C | 6–12 |
| 3. Lập chỉ mục và truy hồi | Chương 4; gộp 4.1 vào 4.2; 4.6 (hiệu quả SSR++ theo bài) và bảng chi phí chỉ mục chuyển sang Chương 4 mới | 13–16 |
| 4. Tái lập và kiểm chứng | Mục 5.1–5.3 cũ, chọn lọc; thêm Bảng 4.1 (câu hỏi, phép kiểm tra, kết quả, giới hạn), Bảng 4.2 (trích Bảng 1), Bảng 4.5 (phiên bản và độ đo, dạng bảng), mục giao thức đo; cây repo và log xuống phụ lục; bảng trả lời GitHub gộp vào 2.8 và 4.4 | 17–24 |
| 5. Cải tiến, thảo luận và kết luận | Mục 5.4–5.6 cũ; 5.5.3 rút thành một đoạn "Điều kiện triển khai", 5.5.4 rút thành một câu; kết luận viết lại theo K1–K4; hướng phát triển còn ba ưu tiên | 25–30 |

Phụ lục: A (chi tiết sai lệch, thêm điểm 10 và trích log), B (chứng minh), C (kết quả khác của bài: bộ dữ liệu, Bảng 1 đầy đủ dạng trang ngang, LLM, LoTTE, LIMIT, CPU, hai hình gốc, h/K, K thích ứng, độ nhạy), D (nguồn số liệu hiệu năng), E (hướng dẫn chạy lại kèm cây repo). Nhãn LaTeX cũ giữ nguyên; thêm `ch:intro`, `ch:repro`, `ch:opt`, `sec:protocol`, `sec:prune-bound`, `app:proofs`, `app:paper`, `app:sources`.

**Sửa số liệu và phạm vi kết luận (P0.1–P0.6).**

- P0.1: thống nhất "10 điểm sai lệch, đã xử lý 9 điểm bằng bản sửa hoặc bổ sung cấu hình; `token_skip_mode` chưa triển khai" ở tóm tắt, 4.4, 5.7 và Bảng 4.9 (cột trạng thái: 7 "Đã sửa", "Thêm preset", "Sửa theo issue", "Chưa triển khai"). Kiểm tra lại với patch (16 file) và test (7 trong `SSR/tests`, 9 trong `opt/tests`). Ghi rõ `token_skip_mode` là nguồn sai lệch còn lại có thể ảnh hưởng tái lập.
- P0.2: tỉ số tăng tốc trên FiQA tính trên cùng 100 query đầu (Bảng 5.2, Hình 5.2): repo exact 1.635 ms, base exact 2.332 ms, `fast_hyb` 326 / 84 / 55 ms (1 / 6 / 12 luồng), GPU 56 ms; tức 29,6 lần so với repo exact và 42,2 lần so với base exact ở 12 luồng (bản cũ ghi 30 lần vì ghép 1.635 ms của 100 query với 54,4 ms của 648 query). Phân bố độ trễ trên 648 query để riêng (Bảng 5.3). Phân biệt "repo exact" (chunk 5.000, dựng lại mỗi lần chạy) và "base exact" (một chỉ mục toàn corpus) ở 5.1.
- P0.3: Phụ lục D liệt kê từng số liệu với file, tập query, luồng/thiết bị và phạm vi đo. Mục 4.2.2 ghi giao thức: query mã hóa trước, chỉ đo bước truy hồi top-100, 3 query khởi động, mỗi query đo một lần, trung bình/p50/p95, GPU tính tới khi kết quả về CPU, PLAID đo cùng cách. Làm rõ "≈280 s" của bản cũ là 173,6 s (posting token) + 107 s (posting μ) của base exact; 164 s là đường của repo; 2,6–4,8 s là bản tối ưu. Số "mã hóa SSR ≈420 s" của bản cũ không có trong log nên thay bằng 1.294 s (ngoại suy từ 5.000 tài liệu, `plaid_bench/ssr.json`). 43,97/43,99 trên NFCorpus giải thích bằng thứ tự hòa điểm (top-100 trùng 100%). Đơn vị thống nhất GB thập phân (0,63 / 2,58 / 4,25 GB thay cho 0,59 / 2,41 / 3,96 GiB), nDCG thang 0–100 (1,2 → 44,0; 1,7–2,4 so với 38,8; 10,8).
- P0.4: "split sạch" đổi thành "split đối chứng (train/dev)"; bỏ lập luận zero-shot bắt buộc điểm xấp xỉ; không suy ra checkpoint khác mô hình Bảng 1 chỉ từ điểm số; "không thể quy cho pipeline" đổi thành "làm giảm khả năng sai lệch do các thành phần đã kiểm tra"; mục 4.5.2 đọc kết quả theo ba mức (quan sát, giả thuyết, chưa kết luận) và dùng câu thay thế của kế hoạch.
- P0.5: mục 3.3.1 "Điều kiện bỏ block" nêu cận của tổng điểm gồm điểm đã tích lũy, đóng góp cặp đang duyệt và phần còn lại; thuật toán ghi rõ chỉ minh họa; phân biệt posting mức token và mức tài liệu (3.1, 3.4, với L̄_tok và L̄_doc); mục 2.5.3 bỏ suy luận "ổn định với truy vấn dài", thêm điều kiện bảo toàn thứ tự 2Nη (chứng minh ở Phụ lục B); mục 5.4 ghi cận dưới của LB-rerank không bảo đảm tập ứng viên chứa top-k exact.
- P0.6: Bảng 4.14 đổi "Không đúng trên corpus lớn" thành "Không quan sát được trên FiQA 57.638 tài liệu với checkpoint và cấu hình đã thử", "Phóng đại" thành nhận xét kỹ thuật về triển khai fast-plaid, thêm ghi chú CPU/GPU là so sánh cấu hình thực tế; mục 4.6 giữ kết luận MS MARCO trong giao thức re-ranking.

**Hình và bảng.** Giữ 9 hình cốt lõi (1.1, 1.2, 2.1, 2.2, 3.1, 3.2, 4.1, 4.2, 5.1, 5.2) và hai hình gốc ở Phụ lục C; bỏ Hình phân rã sai số, ablation, độ nhạy, BEIR trung bình, LIMIT, thời gian lập chỉ mục, K theo miền (trùng với bảng). Hình 4.2 (split) vẽ lại hai panel, ba cột mỗi nhóm thay vì sáu. Hình 5.2 (độ trễ) dùng cùng 100 query và ghi số luồng. Caption dài có bản ngắn cho danh mục. Bảng 1 đầy đủ chuyển sang trang ngang (`sidewaystable`) ở Phụ lục C. Các bảng nhiều chữ dùng cột canh trái (`P{}`) để tránh giãn chữ. Không còn `[H]`. Mục lục chỉ tới cấp section (`tocdepth=1`).

**Tóm tắt và kết luận.** Tóm tắt khoảng 360 từ theo bốn ý (vấn đề, cơ chế, phạm vi kiểm chứng, kết quả và giới hạn), chỉ giữ các số đã thống nhất nguồn, ghi speedup kèm số luồng và mốc so sánh, ghi thêm chi phí bộ nhớ chỉ mục. Kết luận trả lời lần lượt K1–K4, nêu giới hạn và ba hướng ưu tiên.

**Tham chiếu.** Mục tài liệu tham khảo ghi URL của issue #1 và #2, ngày truy cập, commit, ngày tải checkpoint. Danh mục từ viết tắt thêm LB.

**Kiểm tra biên dịch.** Tectonic (XeTeX), 53 trang, không tham chiếu hay trích dẫn lỗi, còn một hbox tràn 4,9pt ở Phụ lục A. Đã xem ảnh các trang có bảng và hình mới.

**Nhóm cần kiểm tra lại (bổ sung mục 9).**

- Tên chương tiếng Việt được giữ theo quyết định của nhóm (13/10/2026); bảng phân công ghi đúng năm tên chương này kèm các mục phụ trách. `latex/backup_v3/` chỉ giữ để đối chiếu.
- Bảng phân công đã gán lại theo bố cục mới; nhóm sửa người phụ trách cho đúng thực tế nếu cần.
- Số liệu mã hóa corpus SSR trên FiQA là 1.294 s ngoại suy; nếu nhóm có số đo đầy đủ thì thay vào Bảng 4.13, Bảng 4.14 và Phụ lục D.
- Các việc trong kế hoạch chưa làm vì cần chạy lại thí nghiệm: đo baseline và kernel mới trên toàn bộ cùng tập query FiQA; thống kê độ dài query, nhãn, trùng lặp và khoảng tin cậy để giải thích chênh lệch theo split.

**Thuật ngữ (bổ sung cùng ngày).** Theo quyết định của nhóm giữ thuật ngữ tiếng Anh, các cụm đã dịch được đổi lại: "biểu diễn thưa" thành "biểu diễn sparse" (kể cả tên Chương 2: "Biểu diễn sparse và huấn luyện SSR"), "không gian / vector / điểm / tích vô hướng thưa" thành "... sparse", "MaxSim thưa" thành "sparse MaxSim", "huấn luyện lai" và "hàm mục tiêu lai" thành "hybrid training", "từ thô đến tinh" thành "coarse-to-fine", "mức thưa K" thành "mức sparsity K", "chồng chập" thành "superposition", "sụp đổ biểu diễn" thành "representation collapse", "truy hồi thưa học được" thành "learned sparse retrieval"; "tái tạo" khi là tên khái niệm (sai số reconstruction, thành phần reconstruction, Reconstruction trung thực) đổi sang "reconstruction", khi là động từ ("SAE tái tạo tốt") giữ tiếng Việt. "Bước thô / bước tinh" giữ tiếng Việt vì là từ mô tả, có chú thích "coarse scoring / fine re-scoring" ở lần đầu (mục 3.3). Phần giải thích trong bảng từ viết tắt vẫn tiếng Việt.

**Tài liệu tham khảo và trích dẫn (bổ sung cùng ngày).** Danh mục viết lại theo cách ghi của bài báo gốc (bản dịch trong `ban dich/`): "Họ, Tên viết tắt. Tiêu đề. Nơi công bố, trang, năm", xếp theo bảng chữ cái, nhãn số. Mọi công trình mà bài gốc có dẫn được chép đúng theo bài (ColBERT, ColBERTv2, PLAID, COIL, XTR, WARP, EMVB, SPLADE tách thành ba mục v1/v2/v3, TopK SAE, sparse coding, BEIR, MS MARCO, LIMIT, Okapi BM25). Thêm 27 mục từ bài gốc cho các tên được nhắc mà trước đó không có mục: CITADEL, AligneR, MUVERA, DESSERT, IGP, BERT, FAISS, MTEB, BatchTopK, JumpReLU, Gated SAE, hai công trình về SAE diễn giải, CSR và CSRv2 của nhóm tác giả, Llama-embed-nemotron-8b, Qwen3 embedding, e5-mistral, và 12 bộ dữ liệu BEIR. Giữ các mục ngoài bài theo cùng định dạng: nDCG (Järvelin và Kekäläinen 2002), Anserini, PyLate, mã nguồn và checkpoint SSR, repo nhóm; mục PMLR gộp vào mục bài báo. Thêm trích dẫn còn thiếu trong thân bài: Anserini (Bảng 4.8), PyLate (Bảng 4.6), repo nhóm (mục 1.7), BERT và MTEB (Chương 4), các bộ dữ liệu trong Bảng 4.7 và Bảng C.1, các mô hình trong Bảng C.3, LoTTE dẫn về bài ColBERTv2; mục 1.6 bổ sung một câu về AligneR/CITADEL, MUVERA/DESSERT/IGP và CSR/CSRv2 để các mục mới đều được dẫn tới. Tổng cộng 53 mục, không mục nào không được dẫn. Sửa mục 1.3: số cụm K-means của ColBERTv2 tỉ lệ với căn bậc hai của số vector token (khoảng 16·√n, theo bài và mã nguồn ColBERTv2), thay cho "√(16·số token)" lấy từ docx.

**Bảng C.2 (bổ sung cùng ngày).** Chuyển từ `sidewaystable` (trang dọc, bảng xoay) sang trang ngang thật bằng gói `pdflscape` (`\begin{landscape}` + `table`), để trang hiển thị nằm ngang trong trình xem PDF và in ra khổ ngang; cỡ chữ tăng lên bình thường, `tabcolsep` 7pt. Gói `rotating` không còn dùng.
