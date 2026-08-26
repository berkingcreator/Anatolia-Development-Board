# Anatolia Geliştirme Kart Serisi

**Anatolia Geliştirme Kart Serisi**, açık kaynaklı mikrodenetleyici mimarilerini ve minimal AVR (ATtiny) çekirdeklerini temel alan, yerli ve modüler bir geliştirme donanımı ailesidir. Düşük güç tüketimi gerektiren gömülü sistemlerden lojik devre simülasyonlarına, giyilebilir teknolojilerden hafif otonom modüllere kadar geniş bir yelpazede esnek çözümler sunar.

---

## 🚀 Öne Çıkan Özellikler

* **Açık Kaynak Donanım & Mimari:** Tamamen açık kaynaklı şematik ve donanım tasarımı ile özelleştirilebilir yapı.
* **ATtiny Çekirdek Desteği:** ATtiny85 / ATtiny84 tabanlı yüksek verimli, düşük güç tüketimli mikrodenetleyici entegrasyonu.
* **Kompakt Form Faktörü:** Minimal alan kaplayan, breadboard ve özel PCB uygulamalarına kolayca entegre edilebilir yapı.
* **Dahili Bootloader Desteği:** Micronucleus / V-USB bootloader sayesinde harici programlayıcıya ihtiyaç duymadan USB üzerinden doğrudan kod yükleme.
* **Esnek G/Ç (GPIO) ve PWM:** Küçük boyutuna rağmen dahili ADC okuma, SPI/I2C haberleşme ve PWM çıkış yeteneği.

---

## 🛠 Donanım Mimarisi

| Parametre | Özellik / Değer |
| :--- | :--- |
| **Mikrodenetleyici** | Microchip / Atmel ATtiny Serisi (ATtiny85 / ATtiny84) |
| **Çekirdek Mimarisi** | 8-bit AVR (Açık Ekosistem Uyumlu) |
| **Çalışma Frekansı** | 8 MHz / 16 MHz / 20 MHz (Dahili/Harici osilatör) |
| **Çalışma Gerilimi** | 3.3V - 5V DC |
| **Flash Bellek** | 8 KB (Yaklaşık 6 KB kullanılabilir bootloader alanı) |
| **EEPROM / SRAM** | 512 Bytes EEPROM / 512 Bytes SRAM |
| **Haberleşme** | Software UART, USI (Universal Serial Interface - I2C / SPI) |
| **Programlama Arayüzü** | USB (V-USB) / ISP (In-System Programming) |

---

## 💻 Kurulum ve Başlangıç

### 1. Arduino IDE Yapılandırması
1. Arduino IDE içerisinde `Dosya > Tercihler` sekmesini açın.
2. **Ek Kart Yöneticisi URL'leri** kısmına aşağıdaki kart paket linkini ekleyin:
   `https://raw.githubusercontent.com/damellis/attiny/ide-1.6.x-boards-index/package_damellis_attiny_index.json` (veya *ATTinyCore* paketi)
3. `Araçlar > Kart > Kart Yöneticisi` yolunu izleyip **attiny** paketini aratın ve yükleyin.
4. `Araçlar > Kart` altından kullanmak istediğiniz **ATtiny85** veya ilgili Anatolia varyantını seçin.
5. İşlemci saat frekansını (örneğin `Internal 8 MHz` veya `Internal 16 MHz`) donanımınıza göre ayarlayın.

### 2. Sürücü Kurulumu (USB / Micronucleus)
Kart üzerinde dahili USB bootloader kullanılıyorsa, bilgisayarınıza **Digispark / Micronucleus** USB sürücülerini yüklemeniz gerekmektedir.

---

## ⚡ Hızlı Başlangıç Kodu (Blink Örneği)

```cpp
// Anatolia ATtiny Serisi - Dahili/Harici LED Test Kodu

#define LED_PIN PB1 // ATtiny85 üzerindeki varsayılan PWM/LED pini

void setup() {
  pinMode(LED_PIN, OUTPUT);
}

void loop() {
  digitalWrite(LED_PIN, HIGH);
  delay(500);
  digitalWrite(LED_PIN, LOW);
  delay(500);
}
