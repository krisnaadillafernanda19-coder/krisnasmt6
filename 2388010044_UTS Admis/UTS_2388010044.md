# A. DESKRIPSI TUGAS (THE MISSION)
Anda sedang melamar posisi Cloud Engineer di sebuah perusahaan teknologi multinasional. Sebagai ujian teknis sekaligus pembuktian skill Anda, Tim HRD dan Tim Infrastruktur memberikan tantangan:

"Deploy Curriculum Vitae (CV) atau Portofolio Pribadi Anda dalam bentuk Website Statis ke server AWS dari nol, dalam waktu kurang dari 1,5 jam."

Anda diwajibkan membangun infrastruktur servernya, mengamankannya sesuai standar industri, dan memastikan Web CV Anda dapat diakses secara global oleh tim penilai.

# B. SPESIFIKASI INFRASTRUKTUR YANG DIMINTA
1. Region: Wajib menggunakan region Singapore (ap-southeast-1).
2. Compute: * Amazon EC2 Instance dengan OS Ubuntu 22.04 LTS atau 24.04 LTS.
Tipe Instance wajib t2.micro atau t3.micro (Free Tier Eligible).
3. Storage: 8 GB General Purpose SSD (gp2/gp3).
4. Security & Access:
- Wajib menggunakan Key Pair (Tidak boleh menggunakan password/EIC).
- Security Group: Hanya buka Port 80 (HTTP) dari Anywhere (0.0.0.0/0) dan Port 22 (SSH) hanya dari IP Publik Anda sendiri (My IP).
5. Web Server: Menggunakan Nginx (Bukan Apache).
6. Monitoring: Wajib mengaktifkan Detailed CloudWatch Monitoring dan membuat 1 buah Alarm jika penggunaan CPU menyentuh >80%.

# C. INSTRUKSI PENGERJAAN (STEP-BY-STEP)
# Tahap 1: Provisioning & Security
- Buat instance EC2 sesuai spesifikasi di atas.
![alt text](image.png)
- Buat Elastic IP (EIP) dan Attach (hubungkan) EIP tersebut ke instance EC2 Anda secara permanen.
![alt text](image-3.png)
- Konfigurasi Security Group dengan ketat sesuai aturan di atas.
![alt text](image-1.png)

# Tahap 2: Konfigurasi Web Server
- Lakukan remote login (SSH) ke dalam server Anda menggunakan PuTTY atau Terminal.
![alt text](image-2.png)
- Lakukan instalasi web server Nginx.
![alt text](image-4.png)
- Pastikan service Nginx berstatus running dan enabled.
![alt text](image-6.png)
![alt text](image-5.png)

# Tahap 3: Deployment Aplikasi Web CV
- Siapkan source code Web CV / Portofolio Pribadi Anda (berbasis HTML/CSS/JS). Anda diizinkan menggunakan template gratis dari internet, namun wajib dimodifikasi dengan Data Diri Asli Anda (Foto, Riwayat Pendidikan, Skill, dll).
- Gunakan aplikasi SFTP (seperti FileZilla atau WinSCP) untuk memindahkan source code Web CV tersebut dari laptop Anda ke dalam server.
![alt text](image-8.png)
![alt text](image-7.png)
- Pindahkan source code tersebut ke Document Root Nginx/Apache (biasanya di /var/www/html).
- PENTING: Atur Ownership dan Permissions (chown & chmod) pada folder website tersebut secara benar agar Nginx (www-data) bisa membacanya tanpa terkena Error 403 Forbidden.
- Validasi Ujian: Pastikan di bagian paling bawah website CV Anda (footer) terdapat tulisan tebal: "Dideploy oleh: [Nama Lengkap Anda] - [NIM Anda]".
![alt text](image-9.png)
![alt text](image.png)