### 1. Variabel & Echo (Bash Dasar)
| Perintah / Skrip | Penjelasan Singkat |
| :--- | :--- |
| `#!/bin/bash` | Deklarasi wajib (Shebang) agar file dieksekusi sebagai skrip Bash. |
| `nama="Afdhal"` | Membuat variabel `nama` yang berisi teks. |
| `umur=19` | Membuat variabel `umur` yang berisi angka. |
| `echo "... $nama ..."` | Mencetak teks ke layar dan memanggil nilai variabel menggunakan `$`. |

### 2. Operasi Aritmatika
| Perintah / Skrip | Penjelasan Singkat |
| :--- | :--- |
| `hasil=$((x + y))` | Menjumlahkan variabel `x` dan `y`, lalu menyimpannya ke variabel `hasil`. |
| `echo "... $hasil"` | Menampilkan hasil penjumlahan ke layar. |

### 3. Kondisi If-Else
| Perintah / Skrip | Penjelasan Singkat |
| :--- | :--- |
| `if [ $angka -gt 5 ]; then` | Mengecek apakah nilai variabel lebih besar dari (greater than / `-gt`) 5. |
| `else` | Perintah yang akan dieksekusi jika kondisi `if` tidak terpenuhi (salah). |
| `fi` | Penanda berakhirnya blok kondisi logika `if`. |

### 4. Kondisi If-Elif-Else
| Perintah / Skrip | Penjelasan Singkat |
| :--- | :--- |
| `if [ $nilai -ge 90 ]; then` | Mengecek apakah nilai lebih besar atau sama dengan (greater or equal / `-ge`) 90. |
| `elif [ $nilai -ge 75 ]; then`| Kondisi alternatif (Else-If) jika kondisi pertama bernilai salah. |
| `else` | Dieksekusi jika semua kondisi `if` dan `elif` di atasnya bernilai salah. |

### 5. Loop For
| Perintah / Skrip | Penjelasan Singkat |
| :--- | :--- |
| `for angka in {1..5}` | Memulai perulangan yang menghitung angka berurutan dari 1 sampai 5. |
| `do ... done` | Penanda batas awal (`do`) dan batas akhir (`done`) perintah yang akan diulang. |

### 6. Loop While
| Perintah / Skrip | Penjelasan Singkat |
| :--- | :--- |
| `while [ $angka -le 5 ]` | Terus melakukan perulangan selama nilai kurang dari atau sama dengan (less or equal / `-le`) 5. |
| `angka=$((angka + 1))` | Menambah nilai variabel sebesar 1 agar perulangan pada akhirnya bisa berhenti. |

### 7. Membuat Script Log Waktu
| Perintah / Skrip | Penjelasan Singkat |
| :--- | :--- |
| `echo "... $(date)" >> file.txt` | Menulis teks dan waktu saat ini (dari perintah `date`) ke baris terbawah file (`>>`). |
| `chmod +x ~/log_time.sh` | Memberikan izin agar file skrip tersebut dapat dijalankan sebagai program. |

### 8. Penjadwalan dengan Crontab
| Perintah / Skrip | Penjelasan Singkat |
| :--- | :--- |
| `crontab -e` | Membuka editor untuk menambah, mengubah, atau menghapus jadwal tugas otomatis (cron). |
| `* * * * * ~/log_time.sh` | Format jadwal cron yang menginstruksikan sistem untuk menjalankan skrip **setiap menit**. |
| `crontab -l` | Menampilkan daftar seluruh jadwal cron yang saat ini aktif untuk user tersebut. |

### 9. Cek Status Cron
| Perintah / Skrip | Penjelasan Singkat |
| :--- | :--- |
| `sudo systemctl status cron` | Mengecek apakah layanan penjadwalan (cron daemon) berjalan normal di latar belakang sistem. |

### 10. Systemd Service & Timer (Penjadwalan Lanjutan)
| Perintah / Skrip | Penjelasan Singkat |
| :--- | :--- |
| `Type=oneshot` | Konfigurasi service yang hanya berjalan sekali, menyelesaikan tugas, lalu berhenti. |
| `ExecStart=/path/ke/skrip` | Menentukan lokasi file skrip atau perintah yang akan dijalankan oleh service. |
| `OnUnitActiveSec=5min` | Konfigurasi timer untuk menjalankan service setiap 5 menit. |
| `sudo systemctl enable --now ...` | Mengaktifkan timer agar berjalan otomatis saat booting, dan langsung menjalankannya saat ini juga. |
| `systemctl list-timers --all` | Menampilkan seluruh timer systemd yang ada beserta jadwal eksekusi berikutnya. |

### 11. Monitoring Log dengan Journalctl
| Perintah / Skrip | Penjelasan Singkat |
| :--- | :--- |
| `journalctl --no-pager` | Menampilkan seluruh log sistem secara langsung tanpa jeda halaman (tanpa perlu tekan spasi/enter). |
| `journalctl --since "30 ..."` | Memfilter dan menampilkan log sistem yang terjadi hanya dalam 30 menit terakhir. |
| `journalctl -b -1` | Menampilkan log sistem dari proses booting (menyala) terakhir sebelum restart. |
| `journalctl -f` | Menampilkan log sistem terbaru secara *real-time* (mirip `tail -f`). |
| `dmesg \| tail -10` | Menampilkan 10 baris paling bawah (terbaru) dari log pesan kernel (hardware/driver). |
| `sudo journalctl -k` | Membaca log kernel (sama seperti `dmesg`) tapi dengan hak akses administrator. |
