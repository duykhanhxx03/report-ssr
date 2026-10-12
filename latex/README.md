# Báo cáo bài tập lớn – LaTeX

- `baocao.tex`: toàn bộ báo cáo (bìa, phân công, mục lục, Mở đầu, 4 chương, Kết luận, Tài liệu tham khảo).
- `baocao.pdf`: bản biên dịch sẵn (29 trang).

## Biên dịch

Dùng **XeLaTeX** (file dùng `fontspec` với font TeX Gyre Termes/Latin Modern Mono, có sẵn trong TeX Live và Overleaf).

- Overleaf: Menu → Compiler → **XeLaTeX**, rồi Recompile (chạy 2 lần để mục lục cập nhật).
- Máy cá nhân có TeX Live/MiKTeX: `xelatex baocao.tex` (2 lần).

## Chỗ cần điền

Ở đầu file, các lệnh `\newcommand`:

- `\TenGV`, `\Lop`, `\SoNhom`
- `\ThanhVienA` … `\ThanhVienD` (họ tên – mã học viên)
- `\RepoNhom` (link GitHub của nhóm; hiện đặt là https://github.com/duykhanhxx03/ssr-repro-and-optimization)

Bảng phân công và bảng tự đánh giá nằm ngay sau trang bìa; sửa trực tiếp trong file.
Muốn chèn logo PTIT: bỏ dấu `%` ở dòng `\includegraphics[height=3.2cm]{logo_ptit.png}` và đặt file ảnh cạnh `baocao.tex`.
