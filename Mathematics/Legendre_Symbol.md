# Legendre Symbol

* **Category:** Mathematics
* **Points:** 35
* **Source:** CryptoHack

---
## 1. Description
<img width="988" height="311" alt="image" src="https://github.com/user-attachments/assets/cef54f4e-c3e8-4b1c-b1d5-94419cef1b6e" />

## 2. Mathematical Background & Solution
> [!CAUTION]
> $(a/p)$ chỉ là ký hiệu không phải phép tính
- Theo Legendre's Symbol ta có: $(a/p)$ $\equiv a^{(p-1)/2} \pmod p$
  * Nếu $(a/p) = 1$ thì $a$ là **quadratic residue**.
  * Nếu $(a/p) = -1$ thì $a$ là **quadratic non-residue**.
  * Nếu $(a/p) = 0$ thì $a \equiv 0 \pmod p$.
- Đề bài còn cho ta biết dữ kiện: $p \equiv 3 \pmod 4 \iff p \bmod 4 = 3$
  * Số nguyên tố $p$ ($p \neq 2$) chỉ có đúng hai dạng: $p \bmod 4 = 3$ và $p \bmod 4 = 1$.
  * Nếu $a$ là **quadratic residue** thì: $a^{(p-1)/2} \equiv 1 \pmod p$.
  * Để giải được bài toán ta cần tìm $k$ sao cho: $(a^k)^2 \equiv x^2 \equiv a \pmod p \iff a^{2k-1} \equiv 1 \pmod p$.
  * Kết hợp các dữ kiện ta tính được: $k = (p+1)/4$ ($k \in N$ do $p \bmod 4 = 3$) $\implies x_1 = a^{(p+1)/4} \b và x_2 = p-x_1$

## 3. Python Implementation & Logic

### **Algorithm Approach:**


### **Python Code:**
```python
p = 29
ints = [14,6,11]
roots = []

for x in range(1,p):
  if x*x % p in ints:
    roots.append(x)
print(roots)
