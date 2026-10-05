# EasyDown — Nintendo Switch Standalone Payload (.bin)

**Yazar:** Pasha Bey  
**Tip:** TegraRCM / Hekate Standalone Payload (`.bin`)  
**Sürüm:** 1.0.0  

---

## 🚀 Nedir ve Ne İşe Yarar?

**EasyDown**, Nintendo Switch için geliştirilmiş, tam bağımsız (standalone) bare-metal bir `.bin` payload'dır. 

Tek tıkla şu işlemleri sırasıyla ve otomatik olarak gerçekleştirir:

1. **SD Kart Mount:** SD kartı bare-metal seviyede bağlar.
2. **Kefir Paketini Köke Çıkarma:** Payload içine entegre edilmiş `kefir922.zip` arşivini, üst klasör önekini (`kefir922/`) otomatik temizleyerek doğrudan SD kartın kök dizinine (`sdmc:/`) ayıklar (`boot.dat`, `payload.bin`, `atmosphere/`, `hbmenu.nro` vb.).
3. **Fix Archive Bit:** Hekate/Nyx algoritmasıyla tüm SD kart klasörlerinin ve HOS özel dosyalarının arşiv bit özniteliklerini (`AM_ARC`) otomatik düzeltir.
4. **Warmboot Başlatma:** İşlemler tamamlandığında payload içine entegre edilmiş `warmboot.bin` dosyasını hafızadan doğrudan chainload ederek başlatır.

---

## 📦 Paket İçeriği ve Dosyalar

| Dosya | Boyut | Açıklama / Kullanım Amacı |
|-------|-------|---------------------------|
| **`EasyDown.bin`** | **~64.3 MB** | **Tam Paket (Önerilen).** İçinde `kefir922.zip` ve `warmboot.bin` gömülüdür. Hekate menüsünden (`sdmc:/bootloader/payloads/EasyDown.bin`) başlatılması önerilir. |
| **`EasyDown_slim.bin`** | **~140 KB** | **Hafif Sürüm.** TegraRCMGUI / RCM Dongle ile enjeksiyon için uygundur. İçinde `warmboot.bin` gömülüdür; SD kartta `kefir922.zip` varsa onu ayıklar ve Fix Archive Bit yapar. |

---

## 📥 Kullanım Talimatları

### Yöntem 1: Hekate Üzerinden Çalıştırma (Önerilen - `EasyDown.bin`)

1. SD kartınızı bilgisayara takın.
2. `EasyDown.bin` dosyasını SD kartınızdaki şu klasöre kopyalayın:
   ```
   SD:/bootloader/payloads/EasyDown.bin
   ```
3. SD kartı Switch'e takıp Hekate'ye girin.
4. **Payloads** sekmesine tıklayıp **EasyDown.bin**'i seçin.

---

### Yöntem 2: RCM Enjeksiyonu (TegraRCMGUI / Dongle - `EasyDown_slim.bin`)

1. Switch'i RCM moduna alın.
2. Bilgisayarınızda **TegraRCMGUI** veya RCM enjektörünüzde **`EasyDown_slim.bin`** dosyasını seçip enjekte edin.
3. *(İsteğe bağlı)* SD kartınızın kökünde `kefir922.zip` varsa otomatik ayıklanacaktır.

---

## ⚙️ Derleme Talimatı (Geliştiriciler İçin)

Gerekli Araçlar:
- [devkitPro](https://devkitpro.org) `devkitARM`

```bash
export DEVKITPRO=/opt/devkitpro
export DEVKITARM=$DEVKITPRO/devkitARM
export PATH=$DEVKITARM/bin:$PATH

cd /home/pizza/.gemini/antigravity/scratch/EasyDown_Payload
make
```

Çıktılar `output/` dizininde oluşturulur.

---

## ✍️ Yazar & Teşekkür

- **Yazar:** Pasha Bey
- **Altyapı:** Hekate BDK (Bootloader Development Kit) & Atmosphere-NX
