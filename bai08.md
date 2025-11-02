```mermaid
stateDiagram-v2

    state "Chờ nhập kho" as ChoNhapKho
    state "Còn hàng" as ConHang
    state "Hết hàng" as HetHang
    state "Ngừng kinh doanh" as NgungKD
    
    [*] --> ChoNhapKho 
    ChoNhapKho --> ConHang: nhập kho
    ConHang --> HetHang: bán
    HetHang --> ChoNhapKho: đặt bổ sung
    ChoNhapKho --> NgungKD: không có hàng
    ConHang --> NgungKD: không bán được
    HetHang --> NgungKD: không bán nữa

```