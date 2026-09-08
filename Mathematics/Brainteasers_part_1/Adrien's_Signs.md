# Adrien's Signs

* **Category:** Mathematics
* **Points:** 80
* **Source:** CryptoHack

---
## 1. Description


## 2. Mathematical Background & Solution
- Một số nguyên $a$ được gọi là **Quadratic Residue (Thặng dư bình phương)** mod $p$ nếu tồn tại số $x$ sao cho $x^2 \equiv a \pmod p$
- Ta có: $x^2 \equiv a \pmod p \iff x^2 - a \equiv 0 \pmod p \iff x^2 \pmod p = a$

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
