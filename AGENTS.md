# AGENTS.md — Dịch "Hello Algo" sang tiếng Việt

## Bối cảnh
Đây là kho mã sách "Hello Algo" (hello-algo.com). Nội dung gốc tiếng Trung giản thể
nằm ở docs/ và codes/. Các bản dịch cộng đồng đã có: en/, ja/, ru/, zh-hant/ — mỗi
thư mục lặp lại cấu trúc docs/, codes/, mkdocs.yml, README.md.
Mục tiêu: tạo thư mục vi/ với cấu trúc giống hệt en/, chứa bản dịch tiếng Việt.

## Nguồn để dịch
- Dịch nghĩa từ file tiếng Trung tương ứng trong docs/... (bản gốc, chính xác nhất).
- Có thể đối chiếu file cùng đường dẫn trong en/docs/... (bản tiếng Anh đã được
  người bản ngữ rà soát) để lấy cách diễn đạt/thuật ngữ, nhưng nghĩa cuối cùng phải
  khớp bản tiếng Trung — không dịch lại từ bản dịch.

## Không được thay đổi
- Cú pháp Markdown (heading, danh sách, bảng, thụt lề) giữ nguyên 1:1.
- Công thức toán $...$ và $$...$$: giữ nguyên.
- Code inline `...` và code block ```...```: giữ nguyên y hệt, không dịch tên biến/hàm.
- ![mô tả](đường/dẫn.png): chỉ dịch phần mô tả, giữ nguyên đường dẫn.
- Thẻ HTML và placeholder <id>: giữ nguyên. Không tự đánh số bảng/hình (đã có script
  tự đánh số khi build).
- Dòng !!! tip, !!! note, !!! abstract, !!! question...: giữ nguyên từ khoá sau !!!
  (đây là mã kiểu khung, tiêu đề khung tự hiện tiếng Việt nhờ theme.language: vi).
  Chỉ dịch nội dung thụt lề bên dưới.

## Cần dịch
Toàn bộ văn xuôi, tiêu đề, chú thích ảnh (alt text), comment và chuỗi hiển thị trong
code ví dụ. Giữ giọng văn sư phạm, gần gũi như bản gốc.

## Thuật ngữ — LUÔN nhất quán
Trước khi dịch một khái niệm kỹ thuật, tra bảng tại
vi/docs/chapter_appendix/terminology.md (cấu trúc 2 cột "English | Tiếng Việt",
giống hệt ja/docs hoặc ru/docs cùng tên file). Nếu gặp thuật ngữ chưa có trong bảng,
thêm một dòng mới trước khi dùng, để các file dịch sau tra lại được.

## Ảnh minh hoạ (*.assets/)
Ảnh có chữ nhúng sẵn nên không sửa bằng văn bản được. Khi tạo trang mới trong
vi/docs/..., copy nguyên thư mục *.assets/ tương ứng từ en/docs/... (ảnh tiếng Anh,
dễ đọc hơn ảnh tiếng Trung) sang cùng vị trí trong vi/docs/....

## mkdocs.yml
vi/mkdocs.yml dựa trên en/mkdocs.yml: giữ cấu trúc, đổi site_name/site_description
sang tiếng Việt, docs_dir: ../build/vi/docs, site_dir: ../site/vi,
theme.language: vi, dịch nhãn trong mục nav: sang tiếng Việt (đường dẫn file trong
nav giữ nguyên).