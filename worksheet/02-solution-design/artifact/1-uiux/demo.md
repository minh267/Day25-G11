---
artifact: 1 — Demo giao diện
format: ASCII UI sketch
---

# demo.md — Demo giao diện

Demo minh họa cách giao diện giảm rủi ro T-01: AI không được tự lưu số tiền OCR từ hóa đơn như dữ liệu chắc chắn khi ảnh mờ hoặc số tiền bất thường.

---

## 1. Màn hình chính

```text
┌──────────────────────────────────────────────┐
│ Trợ lý chi tiêu                              │
├──────────────────────────────────────────────┤
│ User                                         │
│ Chụp hóa đơn ăn tối cùng bạn bè              │
│ Ảnh hóa đơn: tổng tiền 188.000đ              │
│ AI đang đọc được: 1.888.000đ                 │
├──────────────────────────────────────────────┤
│ ⚠ Cần xác nhận số tiền                       │
│ Ảnh hóa đơn hơi mờ và số tiền 1.888.000đ     │
│ cao bất thường so với các bữa ăn gần đây.    │
│                                              │
│ AI đề xuất:                                  │
│ - Danh mục: Ăn uống                          │
│ - Số tiền đọc được: 1.888.000đ               │
│ - Độ tin cậy: thấp                           │
│                                              │
│ Vui lòng xác nhận trước khi lưu vào báo cáo. │
│                                              │
<<<<<<< HEAD
│ [Lưu 188.000đ] [Sửa số tiền] [Xem ảnh gốc]   │
=======
│ [Xem checklist an toàn] [Nói chuyện vởi      |
|                              tổng đài]       |
>>>>>>> 50f471e7e1cf1d8754e25c8c5f90a2cd328f0eae
└──────────────────────────────────────────────┘
```

---

## 2. Luồng màn hình

```text
User chụp hóa đơn giấy
  -> OCR đọc số tiền, ngày, cửa hàng, danh mục
  -> Hệ thống kiểm tra confidence và số tiền bất thường
  -> Nếu không chắc, hiện banner "Cần xác nhận số tiền"
  -> Giao dịch ở trạng thái chờ xác nhận, chưa cộng vào tổng chắc chắn
  -> User chọn:
      -> Lưu số tiền đúng
      -> Sửa số tiền
      -> Xem ảnh gốc
```

---

## 3. Trạng thái cần minh họa

| Trạng thái | Người dùng thấy gì? | Người dùng làm gì tiếp? |
|---|---|---|
| Hóa đơn đọc rõ | AI hiển thị số tiền, danh mục, độ tin cậy cao | Lưu nhanh hoặc sửa nếu cần |
| Hóa đơn mờ / số tiền bất thường | Banner "Cần xác nhận số tiền", ảnh gốc, số tiền AI đọc được | Xác nhận 188.000đ, sửa số tiền hoặc chụp lại |
| Báo cáo có giao dịch chờ xác nhận | Nhãn "Chưa tính vào tổng chắc chắn", liệt kê hóa đơn cần xác nhận | Mở từng hóa đơn để xác nhận |
| OCR sai đã được user sửa | App lưu lịch sử chỉnh sửa và cập nhật tổng tháng | Xem tổng đã cập nhật |

---

## 4. Ghi chú cho từng thành phần

- **Banner cần xác nhận**: nằm trên form lưu khoản chi, dùng khi OCR confidence thấp, ảnh mờ, hoặc số tiền bất thường.
- **Khung ảnh gốc**: cho phép user phóng to vùng tổng tiền để đối chiếu.
- **Nút sửa nhanh**: giúp đổi 1.888.000đ hoặc 138.000đ về 188.000đ mà không phải nhập lại toàn bộ giao dịch.
- **Nhãn dữ liệu báo cáo**: phân biệt "đã xác minh" và "chờ xác nhận" khi user hỏi tổng chi cuối tháng.

---

## 5. Kiểm tra nhanh

- [x] Nhìn vào demo là hiểu rủi ro đang được chặn ở đâu.
- [x] Có trạng thái khi AI không có đủ thông tin.
- [x] Có cách sửa/xác nhận số tiền trước khi lưu.
- [x] Câu chữ đủ ngắn để đặt trên màn hình thật.
