# Kế hoạch cải thiện báo cáo SSR

Tài liệu làm việc để sửa dần báo cáo `latex/baocao.tex`, dựa trên mã LaTeX, bản PDF 52 trang và một số kết quả thực nghiệm trong repository bên cạnh. Ngày rà soát: 13/10/2026.

Phạm vi góp ý là **bản báo cáo của nhóm**. Các phần “không cần thiết” dưới đây là nội dung có thể rút khỏi thân báo cáo, không phải đánh giá rằng chúng không cần thiết trong bài báo nghiên cứu gốc. Chưa kiểm chứng lại các nguồn trực tuyến và chưa chạy lại thực nghiệm.

## 1. Định hướng biên tập

Báo cáo nên đi theo một mạch: **SSR giải quyết bài toán gì → hoạt động như thế nào → nhóm kiểm chứng ra sao → sửa và tối ưu được gì → kết luận trong phạm vi nào**.

Hiện tại phần phương pháp khá đầy đủ, nhưng Chương 5 chứa cả kết quả công bố, tái lập, kiểm toán mã nguồn, tối ưu và kết luận. Điều này làm phần đóng góp của nhóm xuất hiện muộn và khiến người đọc phải đi qua nhiều kết quả nhóm chưa trực tiếp kiểm chứng.

- [x] Ưu tiên độ chặt của bằng chứng và sự nhất quán của số liệu.
- [x] Rút các đoạn lặp, bảng phụ và kết quả ngoài phạm vi thực nghiệm.
- [x] Giữ các ví dụ, sơ đồ và kết quả giúp giải thích hoặc bảo vệ đóng góp của nhóm.
- [x] Không đặt mục tiêu giảm trang bằng cách thu nhỏ font hoặc ép giãn dòng.
- [x] Giữ thuật ngữ tiếng Anh đã được nhóm thống nhất; có thể Việt hóa tiêu đề chương để phù hợp phần diễn giải tiếng Việt.

## 2. Bố cục đề xuất: giữ 5 chương

Đây là phương án ưu tiên vì giữ khung 5 chương đang có, nhưng phân lại nội dung để tách phương pháp khỏi thực nghiệm. Nếu đề bài bắt buộc tên hoặc nội dung từng chương, dùng phương án ít thay đổi ở mục 3.

| Chương | Nội dung chính | Nguồn trong báo cáo hiện tại | Dung lượng tham khảo |
|---|---|---|---|
| 1. Bài toán, bối cảnh và mục tiêu | Bài toán truy hồi; BM25/SVR/MVR; hạn chế pipeline hiện có; ý tưởng SSR; câu hỏi kiểm chứng và phạm vi | Chương 1 | 4–5 trang |
| 2. Biểu diễn sparse và huấn luyện SSR | MaxSim thưa; SSR-tok/CLS; SAE TopK; các nhóm loss; cận sai lệch và điều kiện áp dụng | Chương 2 + 3 | 7–9 trang |
| 3. Lập chỉ mục và truy hồi | Inverted index mức neuron; exact SSR; SSR++; pruning; độ phức tạp; các sai lệch cài đặt liên quan | Chương 4 | 5–6 trang |
| 4. Tái lập và kiểm chứng | Kết quả công bố liên quan; môi trường/giao thức; baseline; lỗi; kết quả test và train/dev; MS MARCO; so sánh PLAID; giới hạn | Mục 5.1–5.3, chọn lọc | 8–10 trang |
| 5. Cải tiến, thảo luận và kết luận | fast_hyb; GPU; LB-rerank; đánh đổi tốc độ/bộ nhớ/chất lượng; các hướng thất bại tiêu biểu; trả lời câu hỏi kiểm chứng | Mục 5.4–5.6 | 5–7 trang |

Các khoảng trang là mục tiêu biên tập, không phải yêu cầu đã xác nhận. Chưa tính bìa, mục lục, tài liệu tham khảo và phụ lục.

### Khung mục cho Chương 4

1. Những kết quả công bố cần kiểm chứng: chọn chất lượng BEIR, hiệu quả chỉ mục và SSR++.
2. Môi trường, checkpoint, dữ liệu và giao thức đo.
3. Kiểm tra pipeline bằng baseline và các phép tính độc lập.
4. Sai lệch mã nguồn và trạng thái xử lý.
5. Kết quả trên test và đối chứng train/dev.
6. MS MARCO với giao thức re-ranking BM25 top-100.
7. So sánh thực tế với ColBERTv2/PLAID và giới hạn của phép so sánh.

### Khung mục cho Chương 5

1. Nút thắt đã đo được và mục tiêu tối ưu.
2. Kernel exact fast_hyb và các thay đổi cấu trúc dữ liệu.
3. Kết quả cùng tập query: một luồng, nhiều luồng, GPU.
4. LB-rerank: cách chọn ứng viên và đánh đổi chất lượng/độ trễ.
5. Những hướng không hiệu quả và nguyên nhân có bằng chứng.
6. Kết luận theo từng câu hỏi kiểm chứng và hướng phát triển ưu tiên.

### Checklist chuyển bố cục

- [x] Lưu một bản trước khi chuyển mục để đối chiếu.
- [x] Gộp giới thiệu SAE TopK và trình bày huấn luyện, tránh định nghĩa lại.
- [x] Tách tái lập và tối ưu thành hai chương như bảng trên.
- [x] Chuyển nội dung bằng cách giữ nguyên `\label` trước; đổi nhãn sau nếu cần.
- [x] Thay các số mục viết tay bằng `\ref` phù hợp.
- [x] Cập nhật phần “Cấu trúc báo cáo”, bảng phân công, README và mô tả đầu file.
- [x] Biên dịch và kiểm tra mục lục, số hình/bảng, tham chiếu sau khi chuyển.

## 3. Phương án ít thay đổi nếu cần giữ nguyên khung hiện tại

*Không áp dụng: ngày 13/10/2026 đã chuyển bố cục theo mục 2. Riêng bảng "Câu hỏi – Phép kiểm tra – Kết quả chính – Giới hạn" đã đưa vào đầu Chương 4 (Bảng 4.1). Nhóm đã quyết định giữ tên chương tiếng Việt hiện tại; bản cũ ở `latex/backup_v3/` chỉ để đối chiếu.*

- [ ] Giữ Chương 1–4, nhưng rút phần nền tảng lặp và chuyển chứng minh dài xuống phụ lục.
- [ ] Chia Chương 5 thành bốn phần rõ: kết quả công bố chọn lọc; tái lập; tối ưu; thảo luận/kết luận.
- [x] Thêm đầu Chương 5 một bảng “Câu hỏi – Phép kiểm tra – Kết quả chính – Giới hạn”. *(đặt ở đầu Chương 4 mới)*
- [ ] Chuyển kết quả LLM, LoTTE, LIMIT và độ nhạy chi tiết sang phụ lục tổng hợp kết quả bài báo.
- [ ] Dùng tiêu đề chương ngắn hơn, chẳng hạn “Thực nghiệm, cải tiến và kết luận”; bỏ ngắt dòng cưỡng bức trong tên chương.

## 4. Nội dung nên rút, chuyển phụ lục hoặc bỏ

“Chuyển phụ lục” nghĩa là giữ bằng chứng và dẫn chiếu từ thân bài. Không xóa số liệu chỉ vì chúng bất lợi cho phương pháp hoặc cho kết luận của nhóm.

| Vị trí hiện tại | Đề xuất | Phần nên giữ ở thân bài | Lý do |
|---|---|---|---|
| 1.1.1 Định nghĩa bài toán | Rút | Top-k, hàm chấm điểm và ký hiệu cần dùng | Không cần giải thích dài bài toán học xếp hạng nếu không dùng tiếp |
| 1.1.2 Độ đo | Gộp với mục độ đo thực nghiệm | Một câu phân biệt MRR và nDCG, dẫn chiếu định nghĩa | Định nghĩa đang xuất hiện ở hai nơi |
| 1.2 BM25/SVR/MVR | Giữ, rút phần kể tên mô hình | Một bảng so sánh và công thức MaxSim | Là nền tảng cần thiết cho SSR |
| 1.5.2 Thông tin xuất bản | Rút mạnh | Tên bài, tác giả, nơi công bố, phiên bản sử dụng | Danh sách đầy đủ cơ quan tác giả và lĩnh vực không hỗ trợ lập luận |
| 1.6 Nghiên cứu liên quan | Chọn lọc | ColBERT/PLAID, SPLADE/COIL, TopK SAE và khác biệt với SSR | Tránh liệt kê nhiều tên không được phân tích hoặc đo lại |
| Hình chất lượng/độ trễ ở Chương 1 | Cân nhắc chuyển | Sơ đồ pipeline PLAID/SSR | Kết quả thực nghiệm nên tập trung tại chương thực nghiệm; giữ hình này nếu nó thực sự làm rõ động lực |
| 2.2 và 3.2 SAE TopK | Gộp | Một định nghĩa, một công thức, một sơ đồ | Tránh giới thiệu cùng cơ chế hai lần |
| 2.5 Chứng minh Định lý A/B | Chuyển chứng minh chi tiết | Giả thiết, phát biểu cận, ý nghĩa và giới hạn | Người đọc cần hiểu điều kiện áp dụng; toàn bộ khai triển có thể tra phụ lục |
| Hình phân rã sai số | Cân nhắc bỏ | Công thức cận và giải thích hai thành phần | Nếu chỉ lặp lại ngay công thức mà không thêm trực giác |
| 3.3–3.5 Các thành phần loss | Giữ, gộp các mục rất ngắn | Công thức tổng, bảng vai trò và các thành phần quan trọng | Tránh mỗi thành phần vài dòng thành một mục riêng |
| 3.6 Ablation loss | Giữ một cách trình bày | Bảng ablation hoặc biểu đồ, kèm nhận xét | Không cần cả bảng và biểu đồ nếu cùng truyền đạt một kết luận |
| Độ nhạy alpha/beta/gamma | Chuyển chi tiết | Một đoạn về cấu hình lựa chọn, nếu liên quan tái lập | Nhóm chưa khảo sát lại nên không cần diễn giải dài |
| 4.1 Nhắc lại inverted index | Gộp với 4.2 | Nhắc lại ngắn rồi giải thích posting mức neuron | Khái niệm đã được giới thiệu ở Chương 1 |
| 4.6 Hiệu quả SSR++ theo bài báo | Chuyển về thực nghiệm | Dẫn chiếu từ phần thuật toán | Tách mô tả cơ chế khỏi kết quả đo |
| 5.2.1 Bảng BEIR đầy đủ | Chuyển bảng rộng nếu quá nhỏ | Bảng tổng hợp + các tập nhóm thực sự đo | Bảng nhiều cột buộc giảm font, khó đọc và khó đối chiếu |
| 5.2.2 Backbone LLM | Chuyển phụ lục | 2–3 câu về khả năng mở rộng theo công bố | Nhóm chưa kiểm chứng biến thể này |
| 5.2.3 LoTTE và văn bản dài | Chuyển phụ lục | Một câu phạm vi đánh giá bổ sung | Không trực tiếp phục vụ thực nghiệm nhóm |
| 5.2.3 LIMIT | Rút hoặc chuyển | Một minh họa ngắn về động lực MVR, nếu cần | Không cần lặp cả bảng, biểu đồ và giải thích tại nhiều chương |
| 5.2.4 CPU và tài nguyên | Giữ có chọn lọc | Chất lượng, thời gian, bộ nhớ, thiết bị và phạm vi | Liên quan trực tiếp các tuyên bố nhóm kiểm chứng |
| 5.2.5 Độ nhạy h/K và K theo miền | Chuyển chi tiết | Cấu hình h/K dùng trong thực nghiệm và lý do chọn | Các bảng theo miền, K thích ứng nằm ngoài phạm vi nhóm chạy lại |
| 5.2.6 Phiên bản và độ đo | Giữ, viết lại dạng bảng | Phiên bản – nhãn độ đo – số liệu – hệ quả so sánh | Đây là điểm quan trọng nhưng đoạn hiện tại nhiều con số khó theo dõi |
| 5.3.2 Cây repository và CLI | Chuyển Phụ lục hướng dẫn chạy | 3–5 thành phần chính liên quan phương pháp | Cấu trúc file và lệnh chạy là tài liệu tái lập |
| Log NFCorpus và PLAID trong thân bài | Chuyển phụ lục | Kết quả và đường dẫn log | Log chứng minh nguồn số liệu nhưng làm ngắt mạch đọc |
| 5.3.4 Bảng 10 sai lệch | Giữ bảng tóm tắt | Lỗi, ảnh hưởng, trạng thái, bằng chứng | Chi tiết trước/sau đã có Phụ lục A |
| 5.3.9 Trả lời GitHub | Gộp vào mục liên quan | Thông tin tác động đến thiết lập và cách nhóm xử lý | Tránh lặp bảng đối chiếu huấn luyện ở Chương 3 |
| 5.4.5 Các hướng thất bại | Giữ ngắn | 1–2 kết quả cho thấy vì sao cận/pruning chưa hiệu quả | Đây là đóng góp thực nghiệm; chuyển bảng phụ nếu quá dài |
| 5.5.3 Ứng dụng thực tiễn | Rút | Một đoạn về điều kiện triển khai | Các kịch bản chung không thay thế được kết quả thực nghiệm |
| 5.5.4 Tác động xã hội | Rút nếu đề bài không yêu cầu riêng | Một đoạn ngắn có liên hệ với truy hồi | Nội dung chung hiện không phải trọng tâm báo cáo |
| 5.6 Hướng phát triển | Chọn 3 ưu tiên | Huấn luyện minh bạch; đánh giá chuẩn; giảm bộ nhớ | Danh sách quá nhiều hướng làm loãng bước tiếp theo |

### Nội dung nên bảo vệ khi cắt bài

- [x] Ví dụ tính tay MaxSim thưa và khác biệt với chấm điểm theo neuron.
- [x] Sơ đồ biểu diễn token, huấn luyện SAE và inverted index.
- [x] Baseline đối chứng và kiểm tra điểm bằng các phép tính độc lập.
- [x] Trạng thái lỗi chưa sửa và giới hạn chưa huấn luyện lại đầy đủ.
- [x] Kết quả train/dev và test, kèm cách diễn giải thận trọng.
- [x] Giao thức MS MARCO re-ranking và giới hạn recall ứng viên.
- [x] Kết quả cùng tập query, mức luồng và thiết bị của từng kernel.
- [x] Chi phí bộ nhớ tăng thêm khi tối ưu tốc độ.
- [x] Chất lượng và độ trễ LB-rerank so với exact và SSR++.

## 5. Các sửa chữa cần làm trước khi rút gọn

### P0.1. Thống nhất số lỗi đã xử lý

**Vị trí:** Tóm tắt; mục 5.3.4; 5.4.6; kết luận; Bảng `tab:bugs`.

Bảng ghi lỗi 10 `token_skip_mode` chưa sửa, trong khi nhiều đoạn ghi đã sửa mười lỗi. Một số hàng là thêm preset hoặc xử lý sai lệch thiết lập, nên “điểm sai lệch” chính xác hơn “lỗi đã sửa” khi tổng kết.

- [x] Dùng câu: “Nhóm phát hiện 10 điểm sai lệch, đã xử lý 9 điểm bằng bản sửa hoặc bổ sung cấu hình; cơ chế token_skip_mode chưa được triển khai.”
- [x] Kiểm tra trạng thái thực tế từng hàng trước khi chốt con số.
- [x] Nêu phần còn thiếu có thể ảnh hưởng đến khả năng tái lập.

### P0.2. Chuẩn hóa mẫu query khi tính speedup

**Vị trí:** `tab:opt`, `fig:latency`, tóm tắt và kết luận.

Trong `../ssr-repro-and-optimization/opt/results/summary.md`, mốc repo 1.634,69 ms đo trên 100 query FiQA test; fast_hyb 54,40 ms đo trên 648 query. Tỷ số trong báo cáo hiện ghép hai phạm vi này.

- [x] Dùng kết quả cùng 100 query để tính speedup: repo 1.634,69 ms và fast_hyb 12 luồng khoảng 55,2 ms, tức khoảng 29,6 lần theo bảng cùng mẫu.
- [x] Dùng 648 query để báo cáo chất lượng và phân bố độ trễ của kernel tối ưu.
- [ ] Nếu đo lại được, chạy baseline và kernel mới trên toàn bộ cùng tập query. *(chưa chạy lại; hiện dùng 100 query đầu cho tỉ số và 648 query cho phân bố)*
- [x] Tách cải tiến một luồng với cải tiến tổng khi dùng nhiều luồng.
- [x] Phân biệt mức tăng tốc so với `repo_exact` và so với `base_exact`; không gọi cả hai là “bản gốc”.

### P0.3. Thống nhất các lần đo và phạm vi đo

**Vị trí:** `tab:perf`, `tab:opt`, đoạn mô tả fast_hyb, log PLAID.

Các số 54/59 ms, 2,9/4,8 s và 164/~280 s có thể đến từ những lần đo hoặc thành phần khác nhau. Không tự chọn một số thay thế trước khi truy lại nguồn.

- [x] Tạo bảng nguồn: số liệu – file kết quả – tập query – luồng – thiết bị – phạm vi thời gian.
- [x] Làm rõ thời gian dựng cấu trúc chỉ mục, lưu/nạp file và mã hóa corpus.
- [x] Làm rõ độ trễ có bao gồm mã hóa query hay chỉ retrieval trên query đã mã hóa.
- [x] Ghi mean/p50/p95, số query, warmup, số lần lặp và đồng bộ GPU nếu có.
- [x] Kiểm tra 43,97/43,99 trên NFCorpus và giải thích quy tắc hòa điểm hoặc khác biệt cấu hình nếu đó là nguyên nhân.
- [x] Thống nhất đơn vị GB/GiB, thang nDCG 0–1/0–100 và cách viết số thập phân.

### P0.4. Viết lại kết luận về checkpoint

**Vị trí:** mục 5.3.3, 5.3.5–5.3.7, thảo luận và kết luận.

Các phép kiểm tra hiện có củng cố độ tin cậy của kết quả, nhưng không xác định chắc chắn lịch sử huấn luyện checkpoint hoặc nguyên nhân chênh lệch theo split.

- [x] Đổi “split sạch” thành “split train/dev đối chứng” khi chưa có bằng chứng về dữ liệu checkpoint từng tiếp xúc.
- [x] Bỏ lập luận zero-shot bắt buộc có điểm xấp xỉ giữa các split.
- [x] Không suy ra checkpoint chắc chắn khác mô hình Bảng 1 chỉ từ điểm số khác nhau.
- [x] Đổi “không thể quy cho pipeline” thành “kiểm tra baseline làm giảm khả năng sai lệch do các thành phần pipeline đã kiểm tra”.
- [x] Phân biệt ba mức: quan sát đo được; giả thuyết giải thích; kết luận chưa thể đưa ra.
- [ ] Nếu bổ sung thực nghiệm, ưu tiên thống kê độ dài query, nhãn liên quan, số tài liệu liên quan, trùng lặp và khoảng tin cậy của chênh lệch. *(chưa làm; đã ghi vào hướng phát triển)*

**Câu thay thế tham khảo:**

> Checkpoint công bố có mức cải thiện khác biệt rõ giữa split test và các split train/dev đối chứng trên ba tập dữ liệu đã đo. Kiểm tra backbone và baseline chưa giải thích được hiện tượng này. Các kết quả hiện tại chưa xác định được nguyên nhân hoặc lịch sử tiếp xúc dữ liệu của checkpoint.

### P0.5. Hoàn thiện lập luận thuật toán

**Vị trí:** Thuật toán `alg:ssrpp`; mục độ phức tạp; nhận xét sau Định lý B; LB-rerank.

- [x] Trong pruning, chỉ rõ cận của tổng điểm gồm điểm đã tích lũy và các đóng góp còn lại; riêng `z_q × U_B` chỉ chặn một phần đóng góp.
- [x] Nếu giả mã chỉ minh họa pipeline, nói rõ nó chưa mô tả đầy đủ thủ tục pruning an toàn.
- [x] Phân biệt posting mức tài liệu và mức token khi phân tích thời gian/bộ nhớ; định nghĩa rõ độ dài posting trung bình.
- [x] Không suy ra “ổn định với truy vấn dài” chỉ từ cận sai số tăng tuyến tính theo N.
- [x] Có thể thêm điều kiện bảo toàn thứ tự: nếu mỗi điểm tài liệu sai lệch tối đa Nη, khoảng cách hai điểm dense lớn hơn 2Nη là điều kiện đủ để giữ thứ tự.
- [x] Nêu rõ cận dưới của LB-rerank không bảo đảm tập ứng viên chứa mọi tài liệu top-k exact; chất lượng chọn ứng viên được kiểm chứng thực nghiệm.

### P0.6. Thu hẹp phạm vi phản biện hiệu năng

**Vị trí:** `tab:claims`, đoạn sau bảng, tóm tắt và kết luận.

- [x] Đổi “không đúng trên corpus lớn” thành “không quan sát được trên FiQA 57.638 tài liệu với checkpoint và cấu hình đã thử”.
- [x] Ghi rõ so sánh CPU/GPU là so sánh cấu hình thực tế trên máy nhóm, chưa tách riêng tác động thuật toán và phần cứng.
- [x] Phân biệt PLAID trong bài báo với triển khai fast-plaid của nhóm; chức năng cập nhật của một triển khai không tự chứng minh mọi pipeline đều hỗ trợ giống nhau.
- [x] Đổi nhãn “Phóng đại” thành nhận xét kỹ thuật cụ thể, chẳng hạn “triển khai nhóm dùng hỗ trợ cập nhật tài liệu”.
- [x] Với MS MARCO, giữ kết luận trong giao thức BM25 top-100; không đối chiếu trực tiếp điểm re-ranking với full retrieval như cùng điều kiện.

## 6. Hình, bảng và trình bày LaTeX

### Danh sách hình cốt lõi

- [x] SVR và MVR: giữ nếu cần cho người đọc mới.
- [x] Pipeline PLAID và SSR: giữ.
- [x] Dense token → SAE → sparse code → posting: giữ.
- [x] Tổng quan huấn luyện: giữ.
- [x] Inverted index và luồng SSR++: giữ, đảm bảo nhãn đọc được.
- [x] Kết quả theo split: giữ; cân nhắc hai panel hoặc thể hiện chênh lệch để giảm sáu cột mỗi nhóm.
- [x] Vị trí tối ưu: giữ nếu bổ sung thông tin cho mô tả kernel.
- [x] Độ trễ kernel: giữ, ghi cùng mẫu đo và số luồng.
- [x] LB-rerank: cân nhắc đồ thị chất lượng–độ trễ khi có đủ điểm cấu hình; nếu ít điểm, bảng là đủ.

Không cần thêm tất cả các hình trên nếu chúng lặp nhau. Mỗi hình nên giúp người đọc hiểu một cơ chế hoặc đánh đổi riêng.

### Checklist trình bày

- [x] Mỗi hình/bảng được nhắc đến trong văn bản, có 1–3 câu giải thích kết quả chính.
- [x] Caption phân biệt “theo bài báo”, “nhóm đo” và “vẽ lại từ số liệu công bố”.
- [x] Bảng quan trọng có font đủ đọc; ưu tiên chia bảng hoặc chuyển bảng đầy đủ xuống phụ lục thay vì dùng `\scriptsize` liên tục.
- [x] Với bảng rộng, cân nhắc `tabularx` hoặc trang ngang nếu cần giữ toàn bộ cột.
- [x] Không ép toàn bộ hình/bảng bằng `[H]`; kiểm tra bố trí sau biên dịch.
- [x] Rút caption quá dài trong danh mục bằng `\caption[Tên ngắn]{Mô tả đầy đủ}`.
- [x] Nếu được phép, giảm `tocdepth` từ 2 xuống 1 để mục lục chỉ hiện chương và section; vẫn giữ subsection trong nội dung. *(đã đặt 1; đổi lại 2 nếu môn học yêu cầu)*
- [x] Rút đoạn mở/kết chương chỉ kể lại danh sách mục; giữ đoạn nối khi nó giải thích mạch lập luận.
- [x] Gộp các mục chỉ có 1–2 câu, tránh phân cấp quá sâu.
- [x] Kiểm tra phần đầu tài liệu theo mẫu môn học: phân công, tự đánh giá, danh mục hình/bảng và từ viết tắt.
- [x] Các tham chiếu GitHub cần URL issue cụ thể, ngày truy cập và commit/checkpoint revision khi có.
- [x] Giữ bìa, lề, cỡ chữ và giãn dòng theo quy định môn học nếu có.

## 7. Tóm tắt và kết luận nên viết lại thế nào

### Tóm tắt

- [x] Nhắm khoảng 250–350 từ nếu quy định môn học cho phép. *(bản mới khoảng 360 từ)*
- [x] Viết theo bốn ý: vấn đề; cơ chế SSR; phạm vi nhóm kiểm chứng; kết quả và giới hạn chính.
- [x] Chỉ giữ 2–3 số tiêu biểu đã thống nhất nguồn và giao thức.
- [x] Không đưa chi tiết cây mã nguồn, cấu hình bộ nhớ hoặc toàn bộ phiên bản bài báo vào tóm tắt.
- [x] Ghi rõ speedup gồm cấu hình luồng và mốc so sánh.
- [x] Tránh các câu “chỉ vượt trên test”, “tốt hơn trên corpus lớn” khi phạm vi đo hẹp hơn câu chữ.

### Kết luận

- [x] Trả lời lần lượt: đã hiểu cơ chế gì; tái lập được/không được gì; sửa được gì; tối ưu có đánh đổi gì.
- [x] Không kể lại toàn bộ bối cảnh và số liệu của bài báo.
- [x] Nêu giới hạn còn ảnh hưởng kết luận: token_skip_mode, chưa huấn luyện lại đầy đủ, MS MARCO chỉ re-ranking, chưa kiểm SSR-CLS/LLM.
- [x] Chốt 3 hướng tiếp theo có thứ tự: checkpoint minh bạch; đánh giá cùng giao thức ở quy mô lớn hơn; giảm bộ nhớ chỉ mục.

## 8. Lộ trình sửa dần

| Đợt | Công việc | Tiêu chí hoàn tất |
|---|---|---|
| 1 | Sửa số lỗi, phạm vi kết luận và tên các split | Tóm tắt, bảng lỗi, thảo luận, kết luận không mâu thuẫn |
| 2 | Truy nguồn và thống nhất benchmark | Mỗi số có nguồn; speedup tính trên cùng tập query |
| 3 | Chọn bố cục và chuyển mục | Phương pháp, tái lập, tối ưu có mạch riêng; tham chiếu hoạt động |
| 4 | Chuyển nội dung phụ, bỏ lặp | Đóng góp nhóm dễ tìm; bằng chứng vẫn có ở phụ lục |
| 5 | Rà thuật toán, cận sai số và độ phức tạp | Điều kiện bảo đảm và phần xấp xỉ được phân biệt rõ |
| 6 | Chỉnh hình/bảng, tóm tắt và kết luận | PDF đọc được, caption gọn, kết luận trả lời mục tiêu |
| 7 | Kiểm tra cuối | Không tham chiếu lỗi, không tràn bảng, README và phân công khớp bố cục |

### Nhật ký sửa

| Ngày | Mục đã sửa | Điều chỉnh chính | Đã kiểm tra PDF |
|---|---|---|---|
| 13/10/2026 | Đợt 1: Tóm tắt, 4.4, 4.5, 5.6, 5.7, Bảng 4.9 | Thống nhất "10 điểm sai lệch, 9 đã xử lý, `token_skip_mode` chưa triển khai"; "split sạch" đổi thành "split đối chứng (train/dev)"; kết luận về checkpoint viết lại theo ba mức quan sát / giả thuyết / chưa kết luận | Có |
| 13/10/2026 | Đợt 2: 4.2.2, 4.7, 5.1, 5.3, Phụ lục D | Speedup tính trên cùng 100 query (29,6 lần so với repo exact, 42,2 lần so với base exact, 12 luồng); phân bố 648 query để riêng; bảng nguồn số liệu; giao thức đo; GB thập phân; nDCG thang 0–100; giải thích 43,97/43,99; thay 420 s không có nguồn bằng 1.294 s ngoại suy | Có |
| 13/10/2026 | Đợt 3: toàn bộ | Chuyển sang bố cục 5 chương của mục 2; giữ nhãn cũ, thêm `ch:intro`, `ch:repro`, `ch:opt`; bản cũ lưu ở `latex/backup_v3/` | Có |
| 13/10/2026 | Đợt 4: Ch1, Ch2, Ch4, Phụ lục C, E | Rút 1.1, 1.5.2, 1.6; gộp SAE; chứng minh xuống Phụ lục B; LLM/LoTTE/LIMIT/CPU/h-K/độ nhạy xuống Phụ lục C; cây repo và log xuống phụ lục; bảng trả lời GitHub gộp; 5.5.3 còn một đoạn, 5.5.4 còn một câu | Có |
| 13/10/2026 | Đợt 5: 2.5.3, 3.1, 3.3.1, 3.4, 5.4, Phụ lục B | Điều kiện bỏ block; posting mức token và mức tài liệu; bỏ suy luận "ổn định với truy vấn dài"; điều kiện bảo toàn thứ tự 2Nη; cận dưới LB-rerank không bảo đảm ứng viên | Có |
| 13/10/2026 | Đợt 6: hình, bảng, tóm tắt, kết luận | Hình split hai panel; hình độ trễ cùng 100 query ghi số luồng; bỏ 7 hình trùng bảng; caption ngắn; Bảng 1 trang ngang; `tocdepth` 1; tóm tắt khoảng 360 từ; kết luận theo K1–K4, ba hướng ưu tiên | Có |
| 13/10/2026 | Đợt 7: kiểm tra cuối | Biên dịch 53 trang (30 trang thân bài), không tham chiếu lỗi, một hbox tràn 4,9pt; README, CHANGELOG, bảng phân công cập nhật | Có |

### Cách tìm nhanh vị trí sửa

Tìm bằng tiêu đề hoặc nhãn LaTeX để tránh phụ thuộc số dòng sau khi chuyển bố cục:

```bash
rg -n 'tab:questions|tab:bugs|tab:perf|tab:opt-same100|tab:opt-dist|tab:claims|tab:sources|alg:ssrpp|sec:prune-bound|sec:split|sec:versions|sec:protocol|sec:conclusion' latex/baocao.tex
```

Chạy từ thư mục `report-ssr`. Sau mỗi đợt chuyển bố cục, biên dịch bằng XeLaTeX hai lần hoặc Tectonic theo `latex/README.md`, rồi kiểm tra PDF và cảnh báo tham chiếu/tràn lề.
