1. อัปเดตระบบ
ก่อนอื่นให้รันคำสั่งต่อไปนี้เพื่ออัปเดต package index ของระบบ:

sudo apt update
sudo apt upgrade -y

2. ติดตั้งแพ็กเกจที่จำเป็น
Docker ต้องใช้บางแพ็กเกจเพิ่มเติมก่อนติดตั้ง:

sudo apt install -y ca-certificates curl gnupg


3. เพิ่ม GPG Key และ Repository ของ Docker
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo tee /etc/apt/keyrings/docker.asc > /dev/null
sudo chmod a+r /etc/apt/keyrings/docker.asc
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update


4. ติดตั้ง Docker Engine
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

5. ตรวจสอบการติดตั้ง
ตรวจสอบว่า Docker ทำงานได้ถูกต้องโดยรัน:

sudo systemctl status docker

7. อนุญาตให้ใช้งาน Docker โดยไม่ต้องใช้ sudo (ตัวเลือกเสริม)
ค่าเริ่มต้นต้องใช้ sudo ทุกครั้งในการรัน Docker ถ้าต้องการใช้งานโดยไม่ต้องใช้ sudo ให้เพิ่ม user ของคุณเข้าไปในกลุ่ม docker:

sudo usermod -aG docker $USER


เสร็จเรียบร้อย!
คุณสามารถเริ่มต้นใช้งาน Docker บน Ubuntu ได้แล้ว 🎉
หากต้องการติดตั้ง Docker Compose เพิ่มเติม ให้รัน:

sudo apt install docker-compose-plugin




