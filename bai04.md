```mermaid
sequenceDiagram
    actor User
    participant UI as Website UI
    participant Cart as Cart Service

    User ->> UI: Chọn sản phẩm và nhấn "Add to Cart"
    
    loop Thêm từng sản phẩm vào giỏ (n lần)
        UI ->> Cart: sendAddToCartRequest(productId, quantity)
        
        Cart -->> UI: return success (product added)
        UI -->> User: Hiển thị thông báo "Đã thêm vào giỏ"
    end
    
    User ->> UI: Xem giỏ hàng
    UI ->> Cart: getCartItems(userId)
    Cart -->> UI: return cart data
    UI -->> User: Hiển thị danh sách sản phẩm trong giỏ
```