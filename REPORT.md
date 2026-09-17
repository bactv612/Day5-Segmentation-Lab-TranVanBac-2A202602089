# Báo cáo Day 5 — điền trực tiếp trong fork của bạn

**Cách dùng:** Thay mọi dấu `…` bằng bài làm thật của bạn trước khi nộp link fork trên VLearn. Giữ nguyên bốn mục và bảng để coach đọc nhanh. Viết ngắn, cụ thể theo ảnh/vùng; không cần thuật ngữ chuyên sâu. Ví dụ trong [hướng dẫn mẫu](reports/REPORT_TEMPLATE.md) chỉ giúp hiểu cách điền, không phải câu trả lời để chép lại.

- Mã học viên theo lớp: 2A202602089
- Ngày / CVAT local: 17/09/2026 / CVAT local
- Công cụ đã dùng: công cụ AI hỗ trợ tạo mask và Polygon để chỉnh biên

Mã học viên là mã lớp cấp; không cần ghi họ tên trong report nếu kênh VLearn đã nhận diện bạn. Chỉ ghi công cụ thật sự đã dùng; không có SAM vẫn làm bài bình thường.

## 1. Bài đã nộp

Ghi tên ZIP đúng như file trong `submissions/` và số ảnh đã vẽ, Save. Chưa làm hoặc export lỗi thì ghi `chưa có`, không tạo ZIP rỗng. Cột điểm là điểm tối đa của task, **không phải điểm tự chấm**.

| Task | File ZIP đúng tên | Hoàn thành mấy ảnh | Điểm tối đa (coach chấm sau) |
| --- | --- | ---: | ---: |
| easy_semantic | `easy_semantic.zip` | 3 / 3 | 20 |
| medium_instance | `medium_instance.zip` | 3 / 3 | 32 |
| hard_panoptic | `hard_panoptic.zip` | 2 / 2 | 30 |
| cp1_holes | `cp1_holes.zip` | 1 / 1 | 3 |
| cp2_slice | `cp2_slice.zip` | 1 / 1 | 3 |
| cp5_occlusion | `cp5_occlusion.zip` | 1 / 1 | 3 |
| cp3_thin | `cp3_thin.zip` | 1 / 1 | 3 |
| cp4_curb | `cp4_curb.zip` | 1 / 1 | 3 |
| cp6_coverage | `cp6_coverage.zip` | 1 / 1 | 3 |
| **Tổng tối đa** | | | **100** |

Nếu export lỗi, ghi task, dữ liệu đã Save đến đâu và lỗi đã báo coach.

## 2. Một quyết định trước khi dùng gợi ý

Chọn object đầu tiên bạn tự vẽ ở `medium_instance`, trước khi xem bất kỳ đề xuất tự động nào cho object đó. Ghi ảnh/vị trí đủ để tìm lại; “quy tắc biên” là lý do bạn chọn hoặc dừng mask ở ranh đó.

- Ảnh, vị trí và object Medium đầu tiên tự vẽ: người ở phía bên phải ảnh `000000181542.jpg`.
- Class và quy tắc tôi dùng để chọn biên: class `person`; tôi bám theo phần cơ thể nhìn thấy và không tự vẽ thêm phần bị che.
- Nếu dùng gợi ý sau đó: tôi dùng công cụ AI hỗ trợ tạo mask. Có chỗ mask ăn vào nền và thiếu một phần cơ thể, nên tôi chỉnh dần các điểm Polygon theo đường viền nhìn thấy.
- Nếu không dùng gợi ý: không áp dụng.

## 3. Một lỗi tôi tìm thấy và sửa

Chọn một lỗi **có thật** trong bài. Nếu công cụ lỗi khiến bạn chưa sửa được, ghi rõ đã thử gì và cần coach hỗ trợ gì; không ghi “đã sửa” khi chưa sửa.

- Task/ảnh/vùng: `medium_instance`, người ở phía bên phải ảnh `000000181542.jpg`.
- Lỗi thuộc loại: biên và phủ vùng.
- Bằng chứng tôi nhìn thấy: mask AI lấy thừa một phần nền nhưng lại bỏ sót một phần cơ thể.
- Quy tắc và hành động sửa: tôi giữ class `person`, chỉ lấy phần cơ thể nhìn thấy và chỉnh Polygon để bỏ nền, đồng thời bổ sung phần cơ thể bị thiếu.
- Sau sửa đã Save và export lại chưa? Có, tôi đã Save và export lại `medium_instance.zip`.

Nếu bạn **đã xem Summary tự đánh giá trên GitHub Actions hoặc tự chạy script**, ghi ngắn một kết quả liên quan lỗi vừa sửa (ví dụ task, metric trước/sau nếu có): notebook báo `medium_instance` OK về cấu trúc với 92 annotation; chưa có điểm. Scorecard ba tier tối đa **82**, không phải điểm cuối trên 100. Không tự ghi PASS/top 3/bonus; người phụ trách xác nhận theo tiêu chí lớp. Không đưa file ground truth vào fork.

## 4. Ba ca chưa chắc hoặc đã cân nhắc

Mỗi ca là một **vùng cụ thể** khiến bạn phải cân nhắc hai cách hiểu. Ghi dấu hiệu nhìn thấy hoặc quy tắc đã dùng, rồi nêu quyết định hoặc câu hỏi cho coach. Không cần ba lỗi; ca đã quyết định được cũng hợp lệ.

| Ảnh/vị trí | Hai cách hiểu có thể | Quy tắc/chứng cứ | Quyết định hoặc câu hỏi cho coach |
| --- | --- | --- | --- |
| 1 | `easy_semantic`, ranh mặt đường ở phía trái ảnh `7ee6d192-89e2408b.jpg` | Có thể chia theo màu bề mặt hoặc theo ranh chức năng của đường và phần sát dải chắn | Ban đầu tôi dựa vào màu mặt đường. Khi xem lại quy tắc, tôi nhận thấy cần ưu tiên ranh chức năng và bó vỉa, nên đây là vùng cần kiểm tra lại trước khi nộp. |
| 2 | `medium_instance`, người ở phía bên phải ảnh `000000181542.jpg` | Có thể chỉ vẽ phần cơ thể nhìn thấy hoặc đoán thêm phần bị xe và người khác che | Tôi chỉ giữ phần nhìn thấy, không tự suy đoán phần bị che. |
| 3 | `hard_panoptic`, các xe nhỏ ở xa giữa ảnh `000000350023.jpg` | Có thể gộp các xe gần nhau thành một vùng `car` hoặc tách từng xe thành một instance | Tôi tách từng xe còn nhìn thấy thành instance riêng vì `car` là thing; notebook ghi nhận 13 mask `car` trong ảnh này. |
