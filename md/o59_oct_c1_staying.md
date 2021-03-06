เราจะแก้โจทย์ข้อนี้ด้วย dynamic programming

ให้ $dp[n][city][a][b][c]$ แทนจำนวนวิธีในการเดินทางถ้าเซลส์แมนของเราอยู่ที่เมือง $city$ มีเวลาเหลือ $n$ วัน และเคยไปเมือง a b และ c ก็ต่อเมื่อ $a = 1$, $b = 1$, $c = 1$ ตามลำดับ มิเช่นนั้นจะเท่ากับ $0$ 

จะได้ว่า

$$
dp[n][city][a][b][c] = \sum_{d = a, b, c}\sum_{i = 1}^{k_{city}}dp[n-i][d][a'][b'][c']
$$

โดยที่ $a', b', c'$ คือค่า $a, b, c$ ที่เปลี่ยนไปจากการไป visit เมือง $d$

นั่นคือ เราจะลองทุก ๆ ทางที่เป็นไปได้ในการเดินออกจากเมือง $city$ และลองทุก ๆ วันในการอยู่ที่เมืองนั้นที่เป็นไปได้

ขนาดของ state-space ของ dp นี้จะเท่ากับ $\mathcal{O}(3 \cdot 2^3 \cdot n)$ และ transition จะใช้เวลา $\mathcal{O}(k_a)$ ทำให้เราได้อัลกอริธึมที่จะแก้ปัญหานี้ได้ใน $\mathcal{O}(nk_a)$