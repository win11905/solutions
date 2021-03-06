ในข้อนี้เราจะแทนผู้เข้าแข่งขันแต่ละคนด้วยจุดยอดของกราฟ แล้วให้มีเส้นเชื่อมทางเดียวจากจุดยอด $A$ ไปหา $B$ ก็ต่อเมื่อ $A$ สามารถชนะ $B$ ด้วยข้อสอบข้อใดข้อหนึ่ง

สังเกตว่าสำหรับจุดยอด $A$ และ $B$ ใด ๆ หากมี path จาก $A$ ไปหา $B$ จะสามารถสรุปได้ว่าจะสามารถจัดการแข่งขันให้ $A$ เหลือเป็นคนสุดท้ายจากทุก ๆ ผู้เข้าแข่งขันที่อยู่บน path นี้

ดังนั้นถ้ามีจุดยอด $u$ ที่มี path ไปหาทุก ๆ จุดยอดบนกราฟนี้ เราสามารถจัดการแข่งขันให้ $u$ เป็นที่หนึ่งได้ ปัญหาของเราจึงกลายเป็นการหาจุดยอด $u$ เหล่านี้ (สำหรับคนที่สงสัยว่ามันทำได้จริง ๆ หรือเปล่า ให้สร้าง dfs spanning tree โดยมี root เป็น u แล้วจัดการแข่งขันระหว่าง parent-node โดยเริ่มจาก leaf ของ tree นี้)

ในการหาจุดยอด $u$ เหล่านี้ เราจะสร้าง condensation graph บนกราฟนี้ ซึ่งทำได้จากการหา strongly connected components บนกราฟนี้นั่นเอง โดยคำตอบคือจุดยอดที่อยู่ใน strongly connected component ที่แทนโดยจุดยอดใน condensation graph ที่มี in-degree เท่ากับ $0$ นั่นเอง

อุปสรรคในข้อนี้คือ จำนวน edge ที่จะต้องสร้างทั้งหมด ซึ่ง worst case แล้วจะต้องสร้างทั้งหมด $\mathcal{O}(n^2k)$ เส้น ซึ่งเยอะเกินไป

วิธีแก้ปัญหานี้คือ เราจะเปลี่ยนโครงสร้างของกราฟ โดยมีจุดยอดเพิ่ม $k$ จุด เรียก $v_1, v_2, ..., v_k$ แทนข้อสอบ $k$ ข้อ และให้มีเส้นเชื่อมจาก $u$ ไปหา $v_i$ ก็ต่อเมื่อ $u$ สามารถทำข้อสอบข้อที่ $i$ ได้ และมีเส้นเชื่อมจาก $v_i$ ไปหา $u$ ก็ต่อเมื่อ $u$ ไม่สามารถทำข้อสอบข้อที่ $i$

ในโครงสร้างของกราฟแบบใหม่นั้น ข้อสังเกตของเราที่กล่าวไว้ข้างต้นยังคงเป็นจริง จำนวน edge ทั้งหมดที่ต้องสร้างจะเท่ากับ $\mathcal{O}(nk)$

ดังนั้นเราจึงได้อัลกอริธึมในการแก้ปัญหาข้อนี้ในเวลา $\mathcal{O}(nk)$