# Chinese Remainder Theorem

* **Category:** Mathematics
* **Points:** 40
* **Source:** CryptoHack

---
## 1. Description
<img width="958" height="222" alt="image" src="https://github.com/user-attachments/assets/64cbab42-07e5-4013-ab2d-4a006be9705d" />

## 2. Mathematical Background & Solution
- Thuật toán Chinese Remainder Theorem như sau:
  > $x \equiv a_1 \pmod {n_1}$ <br>
  > $x \equiv a_2 \pmod n_2$ <br>
  > $x \equiv a_3 \pmod n_3$ <br>
  > ...... <br>
  > $x \equiv a_n \pmod n_n$ <br>

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

