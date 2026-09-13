# Modular Binomials

* **Category:** Mathematics
* **Points:** 80
* **Source:** CryptoHack

---
## 1. Description
<img width="988" height="184" alt="image" src="https://github.com/user-attachments/assets/4f40eff9-7772-45a1-b6da-715b48877df4" />

## 2. Mathematical Background & Solution
- Dựa vào đề bài ta biết được rằng $N \bmod p = 0$ tức là $N \equiv 0 \pmod p$.
> [!CAUTION]
> Công thức tổng quát của Khai triển Nhị thức Newton là: $(a + b)^n = C_n^0 a^n + C_n^1 a^{n-1}b + C_n^2 a^{n-2}b^2 + \dots + C_n^{n-1} a b^{n-1} + C_n^n b^n$. Ta thấy $n$ số hạng đầu đều chia hết cho $a$. Vì thế nếu $a \equiv 0 \pmod p$ thì modulo $p$ của $n$ số hạng đầu đều bằng 0 và chỉ còn đúng số hạng $b^n$.
- Mục tiêu lúc này của ta là biến đổi hệ phương trình đồng dư trên thành $A$ sao cho $A \equiv 0 \pmod p$. Sau đó tính ra $p = gcd(A,N)$.
  
  > - Xét $c_1 = (2p+3q)^{e_1} \bmod N \iff (2p+3q)^{e_1} = k.N + c_1$ <br>
  >
  >   - modulo $p$ hai vế: $(3q)^{e_1} \bmod p = c_1 \bmod p \iff (3q)^{e_1} \equiv c_1 \pmod p$ <br>
  >
  > - Ta làm tương tự với $c_2$ và thu được: $(7q)^{e_2} \equiv c_2 \pmod p$ <br>

- Ta biến đổi hệ phương trình như sau:
  
  > $(3q)^{e_1} \equiv c_1 \pmod p$ <br>
  > $(7q)^{e_2} \equiv c_2 \pmod p$
  
  - Mũ chéo hai phương trình:
    
    > $3^{{e_1}{e_2}} q^{{e_1}{e_2}} \equiv c_1^{e_2} \pmod p$ <br>
    > $7^{{e_1}{e_2}} q^{{e_1}{e_2}}\equiv c_2^{e_1} \pmod p$
  - Nhân $7^{{e_1}{e_2}}$ vào phương trình (1) và $3^{{e_1}{e_2}}$ vào phương trình (2):
    
    > $21^{{e_1}{e_2}} q^{{e_1}{e_2}} \equiv c_1^{e_2} 7^{{e_1}{e_2}} \pmod p$
    > $21^{{e_1}{e_2}} q^{{e_1}{e_2}} \equiv c_2^{e_1} 3^{{e_1}{e_2}} \pmod p$

## 3. Python Implementation & Logic

### **Algorithm Approach:**
1. Tải file **output.txt**.
2. Tạo hàm **decrypt()**.
3. Tạo chuỗi rỗng **binary**.
4. Duyệt mảng **ciphertext**. Nếu là **quadratic residue** thì thêm 1 vào **binary**, ngược lại thì thêm 0 vào **binary**.
5. Từ chuỗi **binary** chuyển thành **int** rồi chuyển thành **plaintext**.
6. Flag chính là **plaintext**.

### **Python Code:**
```python
