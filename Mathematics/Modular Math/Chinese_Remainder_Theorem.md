# Chinese Remainder Theorem

* **Category:** Mathematics
* **Points:** 40
* **Source:** CryptoHack

---
## 1. Description
<img width="958" height="222" alt="image" src="https://github.com/user-attachments/assets/64cbab42-07e5-4013-ab2d-4a006be9705d" />

## 2. Mathematical Background & Solution
Giải thích thuật toán **Chinese Remainder Theorem.**
- Cho:
  > $x \equiv a_1 \pmod {n_1}$ <br>
  > $x \equiv a_2 \pmod {n_2}$ <br>
  > $x \equiv a_3 \pmod {n_3}$ <br>
  > ...... <br>
  > $x \equiv a_n \pmod {n_n}$ <br>
- Biết ước chung lớn nhất của 2 số $n_i, n_j$ bất kì đôi một bằng 1 tức là gcd($n_i,n_j$) = 1 và $n_i,n_j \in$ {n_1,n_2,n_3,...,n_n$}.
- Mục tiêu chúng ta là tìm ra $x$ sao cho $x \equiv a \pmod N$ với $N = n_1.n_2.n_3...n_n$
- Ta biết $x \equiv a_i \pmod {n_i} \iff (x-a_i) \bmod n_i = 0 \iff x-a_i=k.n_i \iff x=k.n_i + a_i \iff x \bmod n_i = a_i$.
  - Lúc này bài toán trở thành tìm $x$ sao cho:
    > $x \bmod n_1 = a_1$ <br>
    > $x \bmod n_2 = a_2$ <br>
    > $x \bmod n_3 = a_3$ <br>
    > ...... <br>
    > $x \bmod n_n = a_n$
  - Muốn chia $x$ cho bất kỳ số $n_i$ để dư $a_i$ ta cần phải tách $x = x_1 + x_2 + x_3 + ... + x_n$ với $x_i$ chia $n_i$ dư $a_i$ và $x_i$ chia hết cho $n_j (n_j \neq n_i)$.
  - 
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

