# EasyDown — Nintendo Switch Standalone Payload (.bin)

**Yazar:** Pasha Bey  
**Tip:** Standalone Payload (`.bin`) — RCM & Hekate Uyumlu  
**Sürüm:** 1.0.0  

---

## 🚀 Nedir ve Ne İşe Yarar?

**EasyDown**, Nintendo Switch için geliştirilmiş tam bağımsız (standalone) bare-metal bir `.bin` payload'dır. 

Hem **Hekate** menüsünden (`Payloads` sekmesi) başlatılabilir hem de **TegraRCMGUI / RCM Dongle / webRCM** ile doğrudan enjekte edilebilir.

Çalıştırıldığında şu işlemleri sırasıyla ve otomatik olarak gerçekleştirir:

1. **SD Kart Mount:** SD kartı bare-metal seviyede bağlar.
2. **Kefir Paketini Köke Çıkarma:** `kefir922.zip` arşivini, üst klasör adını (`kefir922/`) otomatik temizleyerek doğrudan SD kartın kök dizinine (`sdmc:/`) ayıklar (`boot.dat`, `payload.bin`, `atmosphere/`, `hbmenu.nro` vb.).
3. **Fix Archive Bit:** Hekate/Nyx algoritmasıyla tüm SD kart klasörlerinin ve HOS özel dosyalarının arşiv bit özniteliklerini (`AM_ARC`) otomatik düzeltir.
4. **Warmboot Başlatma:** İşlemler tamamlandığında payload içine entegre edilmiş `warmboot.bin` dosyasını hafızadan otomatik chainload ederek başlatır.

---

## 📦 Sürümler

| Dosya | Boyut | Açıklama |
|-------|-------|----------|
| **`EasyDown.bin`** | **~64.3 MB** | **Gömülü Kefir Paket Sürümü.** `kefir922.zip` ve `warmboot.bin` dosyanın içine entegre edilmiştir. SD karta ek zip koymanız gerekmez. |
| **`EasyDown_slim.bin`** | **~140 KB** | **Hafif Sürüm.** `warmboot.bin` içine entegre edilmiştir. SD kartın kökünde `kefir922.zip` veya `kefir.zip` bulunursa onu otomatik algılayıp köke çıkarır. |

*Her iki sürüm de hem RCM (TegraRCMGUI / Dongle) hem de Hekate üzerinden sorunsuz çalışır.*

---

## 📥 Kullanım Talimatları

### 1. Yöntem: Hekate İle Çalıştırma
1. `EasyDown.bin` veya `EasyDown_slim.bin` dosyasını SD karttaki `SD:/bootloader/payloads/` klasörüne atın.
2. Hekate menüsünde **Payloads** bölümüne girip başlatın.

### 2. Yöntem: Doğrudan RCM Enjeksiyonu (TegraRCMGUI / Dongle)
1. Switch'i RCM moduna alın.
2. Bilgisayar veya dongle üzerinden `EasyDown.bin` veya `EasyDown_slim.bin` enjekte edin.

---

## ✍️ Yazar & Teşekkür

- **Yazar:** Pasha Bey
- **Altyapı:** Hekate BDK (Bootloader Development Kit) & Atmosphere-NX
