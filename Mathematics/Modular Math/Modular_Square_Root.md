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
    - *Trường hợp 1*: $p \bmod 4 = 3$
      
      > 📌 **Lưu ý quan trọng:**
      > Ở TH1 thì $k$ chắc chắn là số nguyên nên ta dễ dàng tìm được $k$. Với TH2, $k$ là số mũ không nguyên nên bắt buộc phải dùng thuật toán Tonelli-Shanks.
      
      * Ta biết khi $a$ là **quadratic residue** thì $a^{(p-1)/2} \equiv 1 \pmod p$.
      * Biến đổi $(a^k)^2 \equiv a \pmod p$ thành $a^{2k-1} \equiv 1 \pmod p$.
      * Kết hợp ta thu được: $k = (p+1)/4 \iff x_1 = a^{(p-1)/4} \bmod p$ và $x_2 = p - x_1$.
    - *Trường hợp 2*: $p \bmod 4 = 1$
      * Mục tiêu lúc này cũng là tìm $k$ sao cho $a^{2k-1} \equiv 1 \pmod p$.
      * Ta liên hệ định lý Fermat nhỏ và thấy $a^{p-1} \equiv a^{2k-1} \equiv 1 \pmod p$.
      * Nhưng nếu gán $2k-1=p-1$ thì $k = p/2$ là một số không nguyên, ta quyết định tách $p-1$ thành $Q.2^S$
        
        - Để tách $p-1$ thành $Q.2^S$ ta sẽ lấy $p-1$ chia 2 và sau S lần kết quả sẽ là một số lẻ Q.
          
      * Do không thể dùng $p-1$ ta quyết định tách phần lẻ $Q$ của $p-1$ gán nó bằng $2k-1$ tức $2k-1 = Q$ để làm nghiệm tạm.
      * Khi đó nghiệm tạm $R \equiv a^{(Q+1)/2} \pmod p$ hay $R^2 \equiv a^{Q+1} = a.a^Q \pmod p$.

      > 📌 **Lưu ý quan trọng:**
      > Ta chọn $2k-1=Q$ vì Q là một số lẻ (nó sẽ làm k nguyên) và khi $(a^Q)^{2^{S-1}}$ chắc chắn ra 1.
      > Nghiệm tạm thường sẽ chưa phải là nghiệm đúng.

      * Ta dễ dàng nhận thấy để biến $x^2 \equiv R^2 \equiv a \pmod p \iff x^2 \equiv a.a^Q \equiv a \pmod p$ **thì** $a^Q$ phải bằng 1.
      * Mục tiêu bài toán lúc này trở thành làm thế nào để biến $a^Q = 1$ trong $R^2 \equiv a.a^Q \pmod p$.
        
        - Ta không thể trực tiếp bình phương 2 vế để làm mất $a^Q$ được vì nó sẽ làm thay đổi biến $a$.
        - Lúc này thuật toán Tonelli-Shanks sẽ phát huy tác dụng:
          * Ta cần tìm một số $b^2$ sao cho khi nhân $b^2$ cho cả 2 vế của phương trình $R^2 \equiv a.a^Q \pmod p$ ta sẽ làm cho $a^Q$ nhỏ dần và phải tiến tới 1.
          * Để tạo ra được $b$ ta cần tìm một số z là **quadratic non-residue**. Ta chọn $z$ vì nó có tính chất $(z^Q)^{2^{M-1}}$ sẽ ra -1.
          
     
          > 📌 **Lưu ý quan trọng:**
          > Số bình phương ra số 1 chỉ có -1 và 1.
          > Đối với $a^Q$ thì thường bình phương $2^k$ ($2^k < 2^{S-1}$) là nó đã ra 1 rồi, tức là thực tế chỉ cần $(a^Q)^{2^{k-1}}$ là ra -1.

          * Muốn cho $a^Q$ và $b^2$ triệt tiêu nhau thì $(a^Q)^{2^{k-1}} = (b^2)^{2^{k-1}} = -1$ khi này $(a^Q)^{2^{k-1}}.(b^2)^{2^{k-1}} = 1$.
            
            - Mà ta phải biến đổi $(z^Q)^{2^{M-1}}$ sao cho nó bằng $(b^2)^{2^{k-1}}$, để làm được điều đó ta cần biến đổi phương trình $(z^Q)^{2^{M-1}} = (b^2)^{2^{k-1}}$ thành $b^2 = (z^Q)^{2^{M-k}}$ bằng cách đặt $b^2 = (z^Q)^x$ và tìm $x$.
           
            - Lúc này ta cho chạy vòng lặp cứ mỗi vòng lặp tìm $k$ mới từ đó suy ra $b^2$ mới sau đó đem nhân với $R^2$ đến khi $a^Q$ và $b^2$ triệt tiêu nhau thì $R^2 \equiv x^2 \equiv a \pmod p \iff x_1 = R \bmod p$ và $x_2 = p - x_1$

            
    
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
