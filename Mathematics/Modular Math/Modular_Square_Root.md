# Modular Square Root

* **Category:** Mathematics
* **Points:** 35
* **Source:** CryptoHack

---
## 1. Description
<img width="997" height="108" alt="image" src="https://github.com/user-attachments/assets/a6c4469b-3c0b-4ea1-a0c7-ec1bd5b0a45c" />

## 2. Mathematical Background & Solution
- Giải thích thuật toán Tonelli-Shanks:
  * Muốn tìm $x$ sao cho $x^2 \equiv a \pmod p$ ta cần tìm $k$ để $x^2 \equiv (a^k)^2 \equiv a \pmod p$.
  * Ta đã biết $p$ ($p \neq 2$) là số nguyên tố và chỉ có 2 dạng $p \bmod 4 = 3$ và $p \bmod 4 = 1$.
 
## 3. Python Implementation & Logic

### **Algorithm Approach:**
1. Tạo danh sách **roots** rỗng.
2. Chạy vòng lặp với biến $x$ từ 1 đến $p-1$.
3. Nếu $x^2 \bmod p = a$ với a là 1 số trong danh sách `[14,6,11]` thì thêm $x$ vào **roots**.
4. In ra **roots** sẽ có 2 nghiệm $x$ và $p-x$.
5. Flag là nghiệm nhỏ hơn.

### **Python Code:**
```python
p = 29
ints = [14,6,11]
roots = []

for x in range(1,p):
    if x*x % p in ints:
        roots.append(x)
print(roots)
