# DevOps Hackathon - Đề 006: Quản lý sinh viên (Student)

## 1. Thông tin sinh viên
- Họ và tên: Đỗ Hồng Ký
- Mã sinh viên: K24CNTT3
- Lớp: CNTT5
- Tài khoản Linux: dohongky-k24cntt3
- GitHub: dohongky
- Repository: devops-hackathon-de006-dohongky-k24cntt3

## 2. Cấu trúc repository
```text
devops-hackathon-de006-dohongky-k24cntt3/
├── src/
│   └── index.html
├── nginx/
│   └── dohongky-k24cntt3.conf
├── screenshots/
│   ├── 01-user.png
│   ├── 02-nginx.png
│   ├── 03-ufw.png
│   ├── 04-website.png
│   ├── 05-git-log.png
│   └── 06-update.png
├── .gitignore
├── README.md
└── .git
```

## 3. Mục tiêu đề bài
- Tạo tài khoản Linux, cài đặt Nginx, Git, UFW.
- Triển khai website tĩnh bằng HTML và cấu hình Nginx.
- Đẩy lên GitHub public, cập nhật nội dung website.
- Chụp ảnh minh chứng và ghi trong README.

## 4. Quá trình thực hiện

### 4.1 Tạo user Linux
```bash
sudo adduser dohongky-k24cntt3
sudo usermod -aG sudo dohongky-k24cntt3
```

### 4.2 Cài đặt Nginx, Git, UFW
```bash
sudo apt update
sudo apt install -y nginx git ufw
```

### 4.3 Cấu hình Nginx
```bash
sudo mkdir -p /var/www/devops-hackathon-de006-dohongky-k24cntt3/src
sudo cp nginx/dohongky-k24cntt3.conf /etc/nginx/sites-available/
sudo ln -s /etc/nginx/sites-available/dohongky-k24cntt3.conf /etc/nginx/sites-enabled/
sudo nginx -t
sudo systemctl reload nginx
```

### 4.4 Bật UFW
```bash
sudo ufw allow 22/tcp
sudo ufw allow 80/tcp
sudo ufw enable
sudo ufw status verbose
```

### 4.5 Kiểm tra website
```bash
curl -I http://localhost/
```

### 4.6 Quản lý mã nguồn bằng Git
```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/dohongky/devops-hackathon-de006-dohongky-k24cntt3.git
git push -u origin main
```

## 5. Ảnh minh chứng
Các file ảnh minh chứng được lưu trong `screenshots/`:
- `01-user.png`
- `02-nginx.png`
- `03-ufw.png`
- `04-website.png`
- `05-git-log.png`
- `06-update.png`

## 6. Hướng dẫn chạy local
```bash
cd /var/www/devops-hackathon-de006-dohongky-k24cntt3/src
python3 -m http.server 8000
```
Sau đó mở:
```text
http://localhost:8000/
```

## 7. Ghi chú
- Port 80 phải mở trên firewall.
- Nginx phục vụ website tĩnh từ `src/index.html`.
- Repository cần đặt ở chế độ public trên GitHub để chấm điểm.
