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
* [cite_start]Memahami mekanisme serangan **SYN Flood** (Network Layer) dan **Slowloris** (Application Layer)[cite: 11].
* [cite_start]Menguji efektivitas **Firewall IPTables** dalam memulihkan ketersediaan layanan (*availability*)[cite: 12].

### 2. Lingkungan Pengujian
* **OS Attacker & Defender:** Kali Linux
* [cite_start]**Target:** DVWA (Damn Vulnerable Web Application) pada Apache Web Server[cite: 19].
* **Tools:** Hping3, Nmap, IPTables, `top` (monitoring).

---

## ⚡ Cheatsheet Perintah (Technical Summary)

Berikut adalah rangkuman perintah utama yang digunakan dalam praktikum ini (detail lengkap ada di dalam folder `LAPORAN`).

### A. Persiapan Target (DVWA)
```bash
# Clone DVWA & Atur Izin
cd /var/www/html
sudo git clone [https://github.com/digininja/DVWA.git](https://github.com/digininja/DVWA.git)
sudo chmod -R 777 /var/www/html/DVWA/
