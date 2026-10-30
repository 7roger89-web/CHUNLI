# LUẬT XNK VÀ LOGISTICS — KHO TRA CỨU

Repo phục vụ công việc vận chuyển hàng Trung Quốc – Việt Nam và xuất khẩu hàng Việt đi nước thứ ba.

## Hai tầng, hai câu hỏi khác nhau
- `core/` `domains/` `registry/` — **luật bắt gì**: phân loại, giấy phép, thủ tục, thuế, chế tài.
- `osint/` — **đối tác này là ai**: thẩm định, điều tra sự cố, dựng dòng tiền.

Không trộn hai tầng khi hỏi.

## Cách dùng
Với model đọc được web, dán một dòng:
`Đọc <raw AS-OF> <raw .ai/READ-FIRST> <raw core/system.md> <raw domains/[đúng thẻ]>. Trả lời theo core/output.md. In URL đã đọc.`

Với model không đọc web: dán `core/system.md` và thẻ tương ứng vào chat, tự dán văn bản luật lấy từ vbpl.vn.

Sau mỗi câu trả lời, chạy câu chốt:
`Liệt kê mọi văn bản đã viện dẫn kèm trạng thái hiệu lực và URL. Đánh dấu cái chưa xác minh.`

## Cổng người — tự làm, không giao AI
Trước khi nộp hồ sơ, tự mở vbpl.vn kiểm ba thứ: dòng trạng thái văn bản, mục văn bản sửa đổi, thông tư mới nhất của bộ quản lý ngành.

## Bảo trì
Mỗi thứ Sáu rà `registry/pending-law.md`. Mỗi lần luật đổi: cập nhật `AS-OF.md`, `CHANGELOG.md`, đúng thẻ. Mỗi tháng kiểm lại ba thẻ bất kỳ.

## Giới hạn
Công cụ hỗ trợ, không phải tư vấn pháp lý. Mốc pháp lý ghi ở `AS-OF.md`.
