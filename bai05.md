```mermaid
sequenceDiagram
    actor User
    participant UI as Website UI
    participant Order as Order Service
    participant VNPay as VNPay

    User ->> UI: Nhấn nút "Thanh toán"
    UI ->> Order: tạo yêu cầu thanh toán

    alt Chọn phương thức thanh toán = VNPay
        Order ->> VNPay: Tạo link thanh toán với VNPay
        VNPay -->> Order: trả về URL thanh toán
        Order -->> UI: redirectTo(vnpayURL)
        UI -->> User: Redirect đến trang VNPay
    else Chọn phương thức thanh toán = COD
        Order ->> Order: Lưu đơn hàng với phương thức COD
        Order -->> Order: Xác nhận lưu thành công
        Order -->> UI: Trả kết quả xác nhận đơn hàng
        UI -->> User: Hiển thị thông báo "Đặt hàng thành công"
    end
```