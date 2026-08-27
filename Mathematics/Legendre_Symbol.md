# Legendre Symbol

* **Category:** Mathematics
* **Points:** 35
* **Source:** CryptoHack

---
## 1. Description
<img width="988" height="311" alt="image" src="https://github.com/user-attachments/assets/cef54f4e-c3e8-4b1c-b1d5-94419cef1b6e" />

## 2. Mathematical Background & Solution
> [CAUTION!]
> (a/p) chỉ là ký hiệu không phải phép tính
- Theo Legendre's Symbol ta có: (a/p) $\equiv a^{(p-1)/2} \pmod p$

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
