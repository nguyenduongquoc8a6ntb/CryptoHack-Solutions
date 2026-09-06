# Successive Powers

* **Category:** Mathematics
* **Points:** 60
* **Source:** CryptoHack

---
## 1. Description
<img width="996" height="115" alt="image" src="https://github.com/user-attachments/assets/1dc5148c-e68b-4f47-b1aa-a506f6075bdb" />

## 2. Mathematical Background & Solution
- Theo đề bài ta có:
  
  > $x^k \bmod p = 588$ <br>
  > $x^{k+1} \bmod p = 665$ <br>
  > $x^{k+2} \bmod p = 216$ <br>
  > $x^{k+3} \bmod p = 113$ <br>
  > $x^{k+4} \bmod p = 642$ <br>
  > ......

- Chúng ta có thể biến đổi thành:

  > $x^k \equiv 588 \pmod p (1)$ <br>
  > $x^{k+1} \equiv 665 \pmod p (2)$ <br>
  > $x^{k+2} \equiv 216 \pmod p (3)$ <br>
  > $x^{k+3} \equiv 113 \pmod p (4)$ <br>
  > $x^{k+4} \equiv 642 \pmod p (5)$ <br>
  > ......

- Kết hợp ba phương trình $(1),(2) và (3)$ ta thu được:

  > $x^k \equiv 588 \pmod p (1)$ <br>
  > $x^k.x \equiv 665 \pmod p (2)$ <br>
  > $x^k.x^26 \equiv 216 \pmod p (3)$ <br>
  > - Thay (1) vào (2) và (3): <br>
  >   $\iff 588.x \equiv 665 \pmod p$ <br>
  >   $     588.x^2 \equiv 216 \pmod p$ <br>
  > - Nhân 588 vào hai vế phương trình $588.x^2 \equiv 216 \pmod p:$ <br>
  >   $(588.x)^2 \equiv 216.588 \pmod p$ <br>
  >   $\iff 665^2 \equiv 127008 \pmod p$ <br>
  >   $\iff 665^2 - 127008 \equiv 0 \pmod p$ <br>
  >   $\iff 315217 \equiv 0 \pmod p$

- Ta làm tương tự với phương trình (2),(3),(4) và (3),(4),(5)


## 3. Python Implementation & Logic

### **Algorithm Approach:**


### **Python Code:**
```python


