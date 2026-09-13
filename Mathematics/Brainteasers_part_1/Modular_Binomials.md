# Modular Binomials

* **Category:** Mathematics
* **Points:** 80
* **Source:** CryptoHack

---
## 1. Description
<img width="913" height="176" alt="image" src="https://github.com/user-attachments/assets/31f3fe33-6649-41cd-9e8c-e75b8893ac19" />

## 2. Mathematical Background & Solution
- Dựa vào đề bài ta biết được rằng $N \bmod q = 0$ tức là $N \equiv 0 \pmod q$.
- Mục tiêu lúc này của ta là biến đổi hệ phương trình đồng dư trên thành $A$ và sao cho $A \equiv 0 \pmod q$.

## 3. Python Implementation & Logic

### **Algorithm Approach:**
1. Tải file **output.txt**.
2. Tạo hàm **decrypt()**.
3. Tạo chuỗi rỗng **binary**.
4. Duyệt mảng **ciphertext**. Nếu là **quadratic residue** thì thêm 1 vào **binary**, ngược lại thì thêm 0 vào **binary**.
5. Từ chuỗi **binary** chuyển thành **int** rồi chuyển thành **plaintext**.
6. Flag chính là **plaintext**.

### **Python Code:**
```python
