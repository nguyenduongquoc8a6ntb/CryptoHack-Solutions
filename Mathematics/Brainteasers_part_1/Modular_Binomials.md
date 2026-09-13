# Modular Binomials

* **Category:** Mathematics
* **Points:** 80
* **Source:** CryptoHack

---
## 1. Description
<img width="913" height="176" alt="image" src="https://github.com/user-attachments/assets/31f3fe33-6649-41cd-9e8c-e75b8893ac19" />

## 2. Mathematical Background & Solution
- Mở file **source.py**
  
  > <img width="479" height="453" alt="image" src="https://github.com/user-attachments/assets/8c492077-1955-486a-b7c2-91ec2d97486b" />

- Ta thấy mỗi ký tự trong chuỗi **FLAG** được biến thành 8 ký tự nhị phân. Nếu ký tự là 1 thì mảng **ciphertext** sẽ thêm $n = a^e \bmod p$, ngược lại **ciphertext** sẽ thêm $-n \bmod p$.
- Việc lấy $a^e \pmod p$ với $e$ ngẫu nhiên làm cho ta nghĩ rằng bài toán này là bất khả thi.
- Tuy nhiên khi áp dụng tiêu chuẩn Euler với $a$ ta biết được $a$ là **quadratic residue** vì $a^{(p-1)/2} \equiv 1 \pmod p$.
  >
  > - Lúc này ta lấy mũ $e$ hai vế: <br>
  >
  > $\iff (a^{(p-1)/2})^e \equiv 1^e \pmod p$ <br>
  > - Áp dụng tính chất luỹ thừa của luỹ thừa $(x^m)^n = (x^n)^m$ : <br>
  >
  > $\iff (a^e)^{(p-1)/2} \equiv 1 \pmod p$ <br>
  > - Đẳng thức này chứng minh cho ta thấy rằng $a^e$ chắc chắn là **quadratic residue**.
- Như vậy thao tác $a^e$ thực chất không làm thay đổi tính chất của $a$ là **quadratic residue**, ta chỉ việc khôi phục từ **ciphertext** thành **binary** bằng cách kiểm tra nó có phải **quadratic residue** hay không.
- Từ ciphertext → binary → số nguyên → plaintext (Flag).

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
