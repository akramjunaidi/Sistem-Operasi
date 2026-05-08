### 1. Navigasi & Operasi File (Dasar)
| Perintah | Penjelasan Singkat |
| :--- | :--- |
| `cd` | Berpindah ke folder home atau direktori tertentu. |
| `mkdir [nama]` | Membuat folder atau direktori baru dengan nama tertentu. |
| `ls` | Menampilkan daftar file dan folder di direktori saat ini. |
| `ls -la` | Menampilkan seluruh isi direktori termasuk file tersembunyi. |

### 2. Monitoring Sistem & Hardware
| Perintah | Penjelasan Singkat |
| :--- | :--- |
| `free -h` | Menampilkan penggunaan memori RAM dalam format yang mudah dibaca (GB/MB). |
| `htop` | Menampilkan proses sistem dan penggunaan sumber daya secara interaktif. |
| `sudo snap install htop` | Menginstal aplikasi monitoring htop melalui Snap Store. |
| `cat /proc/meminfo` | Menampilkan detail teknis mengenai penggunaan memori sistem. |
| `lscpu` | Menampilkan informasi arsitektur dan spesifikasi prosesor (CPU). |
| `swapon --summary` | Menampilkan status dan penggunaan area Swap pada disk. |
| `vmstat -s` | Menampilkan statistik akumulatif mengenai aktivitas memori dan sistem. |
| `ps aux --sort=%mem \| head` | Menampilkan 10 proses teratas yang mengonsumsi RAM paling besar. |

### 3. Pemrograman & Scripting
| Perintah | Penjelasan Singkat |
| :--- | :--- |
| `nano tes.py` | Membuat atau mengedit file Python menggunakan editor teks Nano. |
| `python3 tes.py` | Menjalankan file skrip Python 3. |
| `nano nuri.sh` | Membuat atau mengedit file skrip Shell (Bash). |
| `chmod +x nuri.sh` | Memberikan izin eksekusi agar file skrip bisa dijalankan. |
| `./nuri.sh` | Menjalankan skrip shell yang berada di direktori saat ini. |

### 4. Kontrol Daya & Sistem
| Perintah | Penjelasan Singkat |
| :--- | :--- |
| `sudo reboot` | Melakukan restart pada sistem secara paksa/langsung. |
| `sudo shutdown now` | Mematikan sistem (power off) saat ini juga. |
| `sudo shutdown -r 07:00` | Menjadwalkan sistem untuk restart otomatis pada jam 07:00 pagi. |
| `sudo shutdown -h 08:00` | Menjadwalkan sistem untuk mati otomatis pada jam 08:00 pagi. |
