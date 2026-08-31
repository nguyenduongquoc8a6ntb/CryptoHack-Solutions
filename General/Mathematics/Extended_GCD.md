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
  
  - Ta đã biết trong thuật toán Euclid thì ta sẽ thực hiện thao tác chia lấy dư giữa 2 số $a$ và $b$ đến khi số dư bằng 0 ta tìm được $gcd(a,b)$.
    
    > - Bắt đầu bằng thao tác: $(a \bmod b = r_1) \to (b \bmod r_1 = r_2) \to (r_1 \bmod r_2 = r_3) \to ... \to (r_{n-2} mod r_{n-1} = r_n)$ khi đó $r_{n-1}$ chính là $gcd(a,b)$. <br>
    > - Ta có thể viết lại mỗi thao tác chia lấy dư thành: <br>
    >   $a$ <br>
    >   $b$ <br>
    >   $r_1 = a - b.q_1$ <br>
    >   $r_2 = b - r_1.q_2$ <br>
    >   $r_3 = r_1 - r_2.q_3$ <br>
    >   ...... <br>
    >   $r_n = (r_{n-2}) - (r_{n-1}).q_n$ 
  
## 3. Python Implementation & Logic

### **Algorithm Approach:**
> [!CAUTION]
> - Bản chất dùng $b$ hay $b^2$ là như nhau tuỳ theo phương trình $R.b = a^{(Q+1)/2}.b \iff R^2.b^2=a.a^Q.b^2$. Trên phần giải thích tôi dùng $b^2$ để giải thích rõ sự triệt tiêu $t$, còn dưới code tôi dùng $b$ để code không quá phức tạp. <br>
> - Mỗi vòng lặp ta phải tìm lại số $k$ mới để tạo ra $b$ mới vì $t$ không phải lúc nào cũng hạ từng bậc, có lúc hạ nhiều bậc. <br>
> - Trong trường hữu hạn $Z_p$ thì gần một nửa số là **quadratic non-residue** nên cho chạy vòng lặp từ 1 đến p vẫn ổn nhưng vẫn khuyến khích dùng random số hơn. <br>
> - Ở bước tìm $k$ ta cần dùng 1 biến tạm t_temp = $t$ để tránh làm thay đổi giá trị của $t$.

1. Tải file output.txt trong file sẽ chứa số a là **quadratic residue** và p.
2. Tạo hàm tonelli_shanks($a,p$).
3. Tạo mảng rỗng **roots**
4. Tạo nhánh **if** là trường hợp $p \bmod 4 = 3$.
5. Tính $x_1 = a^{(p+1)/4} \pmod p$ và $x_2 = p - x_1$ sau đó thêm 2 nghiệm vào **roots**.
6. Tạo nhánh **else** là trường hợp $p \bmod 4 = 1$.
7. Cho chạy vòng lặp để tìm ra $Q,S$.
8. Chạy vòng lặp tìm ra $z$.
9. Đặt $t = a^Q \bmod p$; $c = z^Q \bmod p$; $R = a^{(Q+1)/2} \bmod p$; $M = S$.
10. Cho chạy vòng lặp **while** với điều kiện $t != 1$.
11. Trong vòng lặp **while** tạo thêm vòng lặp để cập nhật $k$ mới. (Tìm $k$ bằng cách tính số lần thực tế cần để $t^2^k = 1)
12. Tính $b = c^{2^{M-k-1}}$.
13. Cập nhật các giá trị $R = (R.b) \bmod p$; $c = b^2 \bmod p$; $t = (t.c) \pmod p$, $M = k$.
14. Thêm 2 nghiệm $x_1 = R, x_2 = p - R$ vào danh sách **roots**.
15. Flag là nghiệm nhỏ hơn.

### **Python Code:**
```python
