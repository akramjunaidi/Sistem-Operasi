### 1. Instalasi & Konfigurasi WSL
| Perintah | Penjelasan Singkat |
| :--- | :--- |
| `wsl --install` | Menginstal Windows Subsystem for Linux (WSL) beserta distro Linux default (Ubuntu). |
| `wsl --update` | Memperbarui kernel atau komponen WSL ke versi terbaru. |

### 2. Perintah Dasar Docker
| Perintah | Penjelasan Singkat |
| :--- | :--- |
| `docker run hello-world` | Menjalankan container uji coba dasar untuk memastikan Docker terinstal dengan benar. |
| `docker pull nginx:latest` | Mengunduh (pull) *image* Nginx versi terbaru dari Docker Hub tanpa menjalankannya. |
| `docker ps` | Menampilkan daftar container yang *sedang berjalan* (aktif) saat ini. |
| `docker ps -a` | Menampilkan daftar *seluruh* container, baik yang sedang berjalan maupun yang sudah berhenti. |
| `docker images` | Menampilkan daftar *image* Docker yang sudah tersimpan di sistem lokal. |

### 3. Manajemen Docker Volume
| Perintah | Penjelasan Singkat |
| :--- | :--- |
| `docker volume create` | Membuat volume Docker baru (tempat penyimpanan data persisten). |
| `docker volume inspect` | Menampilkan detail informasi dan konfigurasi dari suatu volume. |
| `docker volume ls` | Menampilkan daftar semua volume Docker yang ada di sistem. |
| `docker volume prune` | Menghapus *seluruh* volume yang tidak terpakai oleh container apa pun. |
| `docker volume rm` | Menghapus volume Docker tertentu secara spesifik. |
| `docker volume create tka` | Membuat volume Docker spesifik dengan nama "tka". |

### 4. Praktikum 1 — Web Server PHP Apache (PowerShell & Docker)
| Perintah | Penjelasan Singkat |
| :--- | :--- |
| `New-Item -ItemType Directory...` | (PowerShell) Membuat folder baru bernama `akramjunaidi`. Sama seperti `mkdir`. |
| `Set-Content -Path "..." -Value "..."` | (PowerShell) Membuat file `index.php` dan langsung mengisinya dengan skrip kode `<?php phpinfo(); ?>`. |
| `docker build -t ubuntu-tka-image ./` | Membangun Docker *image* dengan tag (nama) `ubuntu-tka-image` berdasarkan `Dockerfile` di folder saat ini (`./`). |
| `docker run --name ubuntu-tka-container ...` | Membuat dan menjalankan container dari image tadi, berjalan di *background* (`-d`), dan memetakan port host 9001 ke port 80 container. |
| `Start-Process "http://localhost:9001"` | (PowerShell) Membuka web browser secara otomatis ke alamat lokal di port 9001. |

### 5. Praktikum 2 — Flask + Redis Docker Compose
| Perintah | Penjelasan Singkat |
| :--- | :--- |
| `code .` | Membuka folder saat ini menggunakan aplikasi Visual Studio Code. |
| `pip install flask redis` | Menginstal *library* Python bernama Flask (untuk web) dan Redis (untuk database caching) secara lokal. |
| `docker compose up` | Membangun dan menjalankan seluruh aplikasi multi-container sesuai dengan konfigurasi yang ada di file `compose.yaml`. |

### 6. Catatan Konfigurasi: Dockerfile & Compose
| Baris Konfigurasi | Penjelasan Singkat |
| :--- | :--- |
| **(Dockerfile - Apache/PHP)** | |
| `FROM ubuntu:16.04` | Menggunakan *base image* sistem operasi Ubuntu versi 16.04. |
| `RUN apt-get update && ...` | Mengeksekusi perintah instalasi Apache dan PHP di dalam image saat di-build. |
| `COPY ... /var/www/html/...` | Menyalin file `index.php` dari komputer lokal ke folder *web root* di dalam container. |
| `WORKDIR /var/www/html` | Menetapkan `/var/www/html` sebagai folder kerja utama (*working directory*). |
| `CMD ["apachectl", "-D", ...]` | Perintah utama untuk menyalakan web server Apache secara *foreground* agar container tidak mati. |
| `EXPOSE 80` | Menginformasikan bahwa container ini mendengarkan koneksi lalu lintas pada port 80. |
| **(Dockerfile - Python/Flask)** | |
| `FROM python:3.11-alpine` | Menggunakan *base image* Python versi 3.11 dengan OS Alpine (sangat ringan). |
| `ENV FLASK_APP=app.py` | Menetapkan variabel lingkungan (Environment Variable) untuk aplikasi Flask. |
| `RUN apk add ...` | Menginstal dependensi *compiler* OS bawaan Alpine agar library Python bisa di-compile. |
| `COPY requirements.txt ...` | Menyalin file konfigurasi daftar paket library Python. |
| `RUN pip install -r ...` | Menginstal semua *library* Python yang terdaftar di dalam file `requirements.txt`. |
| **(compose.yaml)** | |
| `build: .` | Menginstruksikan Docker Compose untuk mem-build image dari Dockerfile di folder ini. |
| `ports: - "8000:5000"` | Memetakan port 8000 (diakses host/komputer) ke port 5000 (port internal Flask). |
| `depends_on: - redis` | Memastikan service *web* baru akan dijalankan *setelah* service *redis* berhasil berjalan. |
| `restart: on-failure / always` | Kebijakan *restart* otomatis jika container mengalami *crash* atau server *reboot*. |
