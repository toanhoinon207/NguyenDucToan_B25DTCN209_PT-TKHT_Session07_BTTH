# Nhiệm vụ 1: Nhận diện Lớp và Khai báo Cấu trúc 3 ngăn

## 1. Xác định 4 Lớp

- Customer – Khách hàng
- Order – Đơn hàng
- MenuItem – Món ăn
- Employee – Nhân viên

## 2. Khai báo cấu trúc 3 ngăn

### Class Customer

| Customer |
|---|
| - customerId: int |
| - name: String |
| - email: String |
| - phone: String |
|---|
| + getName(): String |
| + getEmail(): String |
| + createOrder(): Order |

### Class Order

| Order |
|---|
| - orderId: int |
| - orderDate: Date |
| - status: String |
| - totalAmount: double |
|---|
| + addItem(): void |
| + calculateTotal(): double |
| + applyVoucher(): void |

### Class MenuItem

| MenuItem |
|---|
| - itemId: int |
| - name: String |
| - price: double |
| - stock: int |
|---|
| + updatePrice(): void |
| + updateStock(): void |

### Class Employee

| Employee |
|---|
| - employeeId: int |
| - name: String |
| - email: String |
| - phone: String |
|---|
| + getName(): String |
| + getEmail(): String |

# Nhiệm vụ 2: Thiết lập Bổ từ truy cập và Bảo vệ Dữ liệu

| Ký hiệu | Visibility | Ý nghĩa |
|:---:|---|---|
| + | Public | Có thể truy cập từ bên ngoài |
| - | Private | Chỉ được truy cập bên trong lớp |
| # | Protected | Lớp hiện tại và lớp kế thừa có thể truy cập |
| ~ | Package | Truy cập trong cùng package |

# Nhiệm vụ 3: Phân tích và Lựa chọn Mối quan hệ giữa các Lớp

## 1. Category - MenuItem

**Quan hệ:** Aggregation

**Ý nghĩa:**

- Một Category có thể chứa nhiều MenuItem.
- MenuItem vẫn có thể tồn tại độc lập với Category.
- Xóa Category không đồng nghĩa bắt buộc xóa MenuItem.

## 2. Order - OrderItem

**Quan hệ:** Composition

**Ý nghĩa:**

- OrderItem là thành phần cấu thành của Order.
- Nếu Order bị xóa thì các OrderItem thuộc Order đó cũng không còn ý nghĩa tồn tại độc lập trong mô hình.

## 3. Employee - Shipper

**Quan hệ:** Generalization

**Ý nghĩa:**

- Shipper kế thừa Employee.
- Shipper có thể sử dụng các thuộc tính/phương thức chung của Employee và bổ sung thêm hành vi riêng cho giao hàng.

# Nhiệm vụ 4: Xác định Bội số và Khóa chặt Ràng buộc Số lượng

## 1. Customer - Order

Customer 1 ───────── 0..* Order

## 2. Order - OrderItem

Order 1 ───────── 1..* OrderItem

## 3. Order - Voucher

Order * ───────── 0..1 Voucher

# Nhiệm vụ 5: Chuyển đổi kịch bản đặc tả Use Case sang Class Diagram

## 1. Phân tích Danh từ / Động từ

| Thành phần | Từ khóa | Phân tích |
|---|---|---|
| Danh từ | Đơn hàng | Order |
| Danh từ | Món hàng | OrderItem |
| Danh từ | Thanh toán | Payment |
| Danh từ | Hóa đơn | Receipt |
| Động từ | Kiểm tra đơn hàng | checkOrder() |
| Động từ | Tính tổng tiền | calculateTotal() |
| Động từ | Thanh toán | pay() |
| Động từ | Xác nhận thanh toán | confirmPayment() |
| Động từ | Xuất hóa đơn | generateReceipt() |

## 2. Các Lớp được trích xuất

### Order

| **Order** |
|---|
| - orderId: int |
| - totalAmount: double |
| - status: String |
|---------------------------|
| + checkOrder(): boolean |
| + calculateTotal(): double |
| + checkout(): Payment |

### OrderItem

| **OrderItem** |
|---|
| - quantity: int |
| - price: double |
|-------------------------------|
| + calculateSubtotal(): double |

### Payment

| **Payment** |
|---|
| - paymentId: int |
| - amount: double |
| - status: String |
|--------------------------------|
| + pay(): boolean |
| + confirmPayment(): boolean |

### Receipt

| **Receipt** |
|---|
| - receiptId: int |
| - issueDate: Date |
| - amount: double |
|---------------------------|
| + generateReceipt(): void |

# Nhiệm vụ 6: Dựng Sơ đồ Class Diagram Tổng thể theo Quy trình 5 bước
