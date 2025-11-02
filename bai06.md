```mermaid
stateDiagram-v2

    state "Mới tạo" as MoiTao
    state "Hoạt động" as HoatDong
    state "Bị Khoá" as BiKhoa
    state "Kích hoạt lại" as KichHoatLai

    [*] --> MoiTao : regist
    MoiTao --> HoatDong :  login
    HoatDong --> BiKhoa : locked
    BiKhoa --> KichHoatLai : requestUnlocked
    KichHoatLai --> HoatDong : unlockSucceeded
    HoatDong --> [*]
```