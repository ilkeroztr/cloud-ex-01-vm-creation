# CLOUD-EX-01 ➝ Google Cloud Üzerinde VM Oluşturma ve Ping Testi

Bu repo, Google Cloud üzerinde bir sanal makine (VM) oluşturup, kendi bilgisayarımdan ping testi yaparak bağlantıyı kontrol ettiğim ödevin dosyalarını içeriyor.

---

## 🔧 Yapılanlar
- Google Cloud hesabı açıldı.
- Compute Engine üzerinden VM oluşturuldu.
  - **Makine tipi:** e2-micro
  - **Bölge:** europe-west1-b
  - **İşletim sistemi:** Debian GNU/Linux 12
- Firewall ayarlarında ICMP (ping) trafiğine izin verildi.
- Terminal üzerinden ping testi yapıldı.

---

## 🛰️ Ping Çıktısı
```bash
151 packets transmitted, 151 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 54.465/56.487/62.591/1.350 ms
