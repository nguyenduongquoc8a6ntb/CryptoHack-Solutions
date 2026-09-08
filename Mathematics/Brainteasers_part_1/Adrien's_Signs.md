# Adrien's Signs

* **Category:** Mathematics
* **Points:** 80
* **Source:** CryptoHack

---
## 1. Description
<img width="996" height="135" alt="image" src="https://github.com/user-attachments/assets/c36fc4a9-0faa-4377-b31f-19fc61e62e5e" />

## 2. Mathematical Background & Solution
- Mở file **source.py**
  
  > <img width="479" height="453" alt="image" src="https://github.com/user-attachments/assets/8c492077-1955-486a-b7c2-91ec2d97486b" />

- Ta thấy mỗi ký tự trong chuỗi **FLAG** được biến thành 8 ký tự nhị phân. Mỗi ký tự nhị phân nếu là 1 sẽ thành $n = a^e \pmod p$ , nếu là 0 thì sẽ thành $-n \pmod p$.
- Việc lấy $a^e \pmod p$ với $e$ ngẫu nhiên làm cho ta nghĩ rằng bài toán này là bất khả thi.
- Tuy nhiên khi áp dụng tiêu chuẩn Euler với $a$ ta biết được $a$ là **quadratic residue** vì $a^{(p-1)/2} \equiv 1 \pmod p$.
  >
  > - Lúc này ta lấy mũ $e$ hai vế: <br>
  >
  > $\iff (a^{(p-1)/2)^e \equiv 1^e \pmod p$ <br>
  > - Áp dụng quy tắc giao hoán số mũ $(x^m)^n = (x^n)^m$: <br>
  >
  > $\iff (a^e)^{(p-1)/2} \equiv 1 \pmod p$ <br>
  > - Đẳng thức này chứng minh cho ta thấy rằng $a^e$ chắc chắn là **quadratic residue**.

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
