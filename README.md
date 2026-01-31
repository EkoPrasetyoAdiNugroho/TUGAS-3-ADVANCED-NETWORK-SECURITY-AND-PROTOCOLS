# TUGAS-3-ADVANCED-NETWORK-SECURITY-AND-PROTOCOLS

**Simulasi Serangan DoS (Hping3 & Slowloris) & Mitigasi Firewall**

Repositori ini berisi dokumentasi dan laporan praktikum mengenai analisis dampak serangan *Denial of Service* (DoS) terhadap layanan web dan penerapan mitigasi menggunakan IPTables.

---

## 👤 Identitas Mahasiswa
* **Nama:** Eko Prasetyo Adi Nugroho
* **NIM:** 105841114223
* **Kelas:** 5 JK-A

---

## 📂 Struktur Repositori

| Folder/File | Deskripsi |
| :--- | :--- |
| **`Dokumentasi/`** | Berisi bukti tangkapan layar (screenshot) proses instalasi, monitoring CPU, serangan, dan log firewall. |
| **`LAPORAN/`** | Berisi laporan praktikum lengkap (PDF) yang mencakup pendahuluan, landasan teori, dan analisis hasil. |
| **`README.md`** | Ringkasan teknis dan panduan singkat proyek ini. |

---

## 📝 Ringkasan Praktikum

### 1. Tujuan
* Memahami mekanisme serangan **SYN Flood** (Network Layer) dan **Slowloris** (Application Layer).
* Menguji efektivitas **Firewall IPTables** dalam memulihkan ketersediaan layanan (*availability*).

### 2. Lingkungan Pengujian
* **OS Attacker & Defender:** Kali Linux
* **Target:** DVWA (Damn Vulnerable Web Application) pada Apache Web Server.
* **Tools:** Hping3, Nmap, IPTables, `top` (monitoring).

---

## ⚡ Cheatsheet Perintah (Technical Summary)

Berikut adalah rangkuman perintah utama yang digunakan dalam praktikum ini.

### A. Persiapan Target (DVWA)
Masuk ke direktori web server, unduh source code DVWA, dan berikan izin akses penuh agar aplikasi dapat berjalan dengan baik.

```bash
# Masuk ke direktori web server
cd /var/www/html

# Clone repositori DVWA
sudo git clone https://github.com/digininja/DVWA.git

# Ubah izin akses folder (R/W/X)
sudo chmod -R 777 /var/www/html/DVWA/
```

### B. Simulasi Serangan (Hping3)
Perintah ini digunakan untuk melakukan serangan SYN Flood ke target. Serangan ini membanjiri server dengan permintaan koneksi palsu.

```bash
# Syntax: hping3 -S (Syn) -p (Port) -i (Interval) IP_Target
sudo hping3 -S -p 80 -i u10 127.0.0.1
```
**Dampak:** Penggunaan CPU akan melonjak drastis (idle time mendekati 0%), menyebabkan layanan menjadi lambat atau tidak bisa diakses.

### C. Mitigasi (IPTables)
Untuk menanggulangi serangan, kita menerapkan aturan firewall untuk membatasi jumlah koneksi yang masuk (Rate Limiting).

```bash
# Batasi paket masuk maksimal 25 per menit dengan burst 100
sudo iptables -A INPUT -p tcp --dport 80 -m limit --limit 25/minute --limit-burst 100 -j ACCEPT
```
**Hasil:** Paket yang melebihi batas akan dibuang (drop), sehingga beban server kembali normal dan layanan dapat diakses kembali.

---

> [!WARNING]
> **Disclaimer**
> Project ini dibuat semata-mata untuk tujuan pendidikan di mata kuliah Keamanan Jaringan Lanjut. Penulis tidak bertanggung jawab atas penyalahgunaan informasi ini.
