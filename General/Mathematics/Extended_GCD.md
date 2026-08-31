# Modular Square Root

* **Category:** General
* **Points:** 20
* **Source:** CryptoHack

---
## 1. Description
<img width="983" height="178" alt="image" src="https://github.com/user-attachments/assets/b2230c5a-9bfc-482b-b408-fc6ac657f427" />

## 2. Mathematical Background & Solution

> Chú thích: <br>
> - $a$, $b$ là hai số cần tìm $gcd(a,b)$. <br>
> - $r_n$ là số dư. <br>
> - $q_n$ là thương số.

- Thuật toán Euclid mở rộng là thuật toán giúp ta tìm ra $x$, $y$ và $gcd(a,b)$ biết **$a.x+b.y = gcd(a,b)$**. Cụ thể:
  
  - Chúng ta đã biết trong thuật toán Euclid ta sẽ thực hiện thao tác chia lấy dư giữa 2 số $a$ và $b$ (a,b được cập nhật liên tục) đến khi số dư bằng 0 ta tìm được $gcd(a,b)$.
    
    > - Bắt đầu bằng thao tác: $(a \bmod b = r_1) \to (b \bmod r_1 = r_2) \to (r_1 \bmod r_2 = r_3) \to ... \to (r_{n-2} mod r_{n-1} = r_n)$ khi đó $r_{n-1}$ chính là $gcd(a,b)$. <br>
    > - Ta có thể viết lại mỗi thao tác chia lấy dư thành: <br>
    >   $r_1 = a - b.q_1$ <br>
    >   $r_2 = b - r_1.q_2$ <br>
    >   $r_3 = r_1 - r_2.q_3$ <br>
    >   ...... <br>
    >   $r_n = (r_{n-2}) - (r_{n-1}).q_n$

  - Thuật toán Euclid cho chúng ta biết hai dữ kiện quan trọng: $r_n = a.x_n + b.y_n$ và $r_n = (r_{n-2}) - (r_{n-1}).q_n$
  - Kết hợp hai dữ kiện trên ta thu được:
    
    >  $r_n = (a.x_{n-2} + b.y_{n-2}) - (a.x_{n-1} + b.y_{n-1}).q_n$ <br>
    >
    > $\iff r_n = a.x_{n-2} + b.y_{n-2} - a.x_{n-1}.q_n - b.y_{n-1}.q_n$ <br>
    >
    > $\iff r_n = a.[(x_{n-2}) - (x_{n-1}).q_n] + b.[(y_{n-2}) - (y_{n-1}).q_n]$

  - Như vậy cứ mỗi vòng lặp ta cập nhật biến $x_n$, $y_n$ tương ứng. Thì ở vòng lặp cuối ta sẽ thu được $a.x + b.y = gcd(a,b)$ với $x = x_n$, $y = y_n$ và $gcd(a,b) = r_{n-1}$.
    
## 3. Python Implementation & Logic

### **Algorithm Approach:**
> [!CAUTION]
> Để tạo ra $r_1$ ta cần đặt $a = a.1 + b.0$ và $b = a.0 + b.1$ khi này $r_1 = a.(1-0.q_1) + b.(0-1.q_1)$

1. Tạo hàm **extended_gcd**(a,b).
2. Đặt $x_0 = 1$; $x_1 = 0$; $y_0 = 0$ và $y_1 = 1$.
3. Cho chạy vòng lặp **while** với điều kiện $b \neq 0$.
4. Mỗi vòng lặp tính $q_n$ và cập nhật $a = b & b = a \bmod b$. Tiếp đó cập nhật $x_n = x_{n-2}-x_{n-1}.q_n$ và $y_n = y_{n-2}-y_{n-1}.q_n$.
5. Khi vòng lặp kết thúc thì $a = gcd(a,b)$, $b=0$ và tìm được x,y.
6. Flag là **min**(x,y).

### **Python Code:**
```python
