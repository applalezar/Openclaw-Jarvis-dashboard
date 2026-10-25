# OpenClaw Dashboard

OpenClaw çoklu ajan gerçek zamanlı izleme paneli (FastAPI + Vue).

## Özellikler
- Sistem durumu: Gateway, CPU, Memory, kanal durumu
- Görevler: yerel yapılacaklar/geçmiş görevler
- Model kullanım paneli: MiniMax + OpenAI(GPT) + Gemini + GLM
- Model yapılandırma sayfası: web içinde API anahtarlarını kaydet ve bağlantıyı doğrula

## Güncelleme Notları (2026-02-17)
- Panel düzeni optimizasyonu: yaygın çözünürlükleri destekler (1K/2K/4K/Notebook), kartlar masaüstü ve mobilde daha kararlıdır.
- Model kullanım paneli yükseltmesi: çoklu model sekme yapısı eklendi (MiniMax / OpenAI / Gemini / GLM), gelecekte genişletmeyi kolaylaştırır.
- Model yapılandırma etkileşimi iyileştirildi: API anahtarları maskeleme dolgu durumu ile gösterilir ve değişiklikten sonra kaydetme etkili hale gelir; yanlış kullanım azalır.
- Görev alanı ve işlem alanı stil birleştirildi: boşluk azaltıldı ve gereksiz kaydırma önlendi; bilgi yoğunluğu ve okunabilirlik arttı.
- Yayın paketi maskeleme: `.env`, günlükler, önbellek, derleme çıktıları kaldırıldı; varsayılan olarak yerel hassas bilgileri içermez.

## 5 Dakikada Başlatma (Yeni başlayanlar)

### macOS (Önerilen)
1. `/Users/macmini/openclaw/openclaw-dashboard/scripts/install-dashboard.command` dosyasını çift tıklayın
2. Kurulum tamamlandıktan sonra terminali açıp şunu çalıştırın:
```bash
cd /Users/macmini/openclaw/openclaw-dashboard
source .venv/bin/activate
./start.sh
```
3. Tarayıcıda `http://localhost:18790` adresini açın
4. Varsayılan hesap: `admin` / `admin123`
5. İlk girişte şifrenizi hemen değiştirmeyi öneririz

### Linux
```bash
cd /Users/macmini/openclaw/openclaw-dashboard
bash scripts/install-dashboard.sh
source .venv/bin/activate
./start.sh
```

### Windows (PowerShell)
```powershell
cd /Users/macmini/openclaw/openclaw-dashboard
powershell -ExecutionPolicy Bypass -File .\scripts\install-dashboard.ps1
.\.venv\Scripts\Activate.ps1
python .\server.py
```

## Model Kullanımı Nasıl Yapılandırılır
1. Giriş yaptıktan sonra ana sayfaya gidin
2. "Model kullanım paneli" kartının sağ üst köşesindeki `Model Ayarları` butonuna tıklayın
3. İstediğiniz şekilde doldurun: MiniMax / OpenAI / Gemini / GLM için API bilgileri
4. `Doğrula`ya tıklayın; başarılı olursa `Yapılandırmayı Kaydet`e basın

### Her Modelin Açıklaması
- MiniMax: Gerçek sayım desteği vardır (kullanılan / kota / kullanım oranı)
- OpenAI(GPT): Usage API istek sayısı istatistiği destekler
- Gemini: şu anda durum özeti gösterilir (sayaç kaynağı henüz entegre edilmedi)
- GLM: şu anda durum özeti gösterilir (sayaç kaynağı henüz entegre edilmedi)

## Yapılandırma Dosyaları
- Ortam değişkeni örneği: `/Users/macmini/openclaw/openclaw-dashboard/.env.example`
- Gerçek ortam değişkenleri: `/Users/macmini/openclaw/openclaw-dashboard/.env`
- Model entegrasyonu ayarları: `~/.openclaw/dashboard_integrations.json`

## Sık Sorulan Sorular
- `Invalid or expired token`: yeniden giriş yapın
- Sayfada veri yok: Gateway işleminin çalıştığını doğrulayın
- MiniMax boş veri: GroupId / Quota URL / API Key değerlerinin doğru olduğundan emin olun
- API Key güvenliği: ön yüzde yalnızca maske gösterilir, anahtar yerel dosyada saklanır

## Geliştirme Komutları
```bash
cd /Users/macmini/openclaw/openclaw-dashboard/frontend
npm run dev
```

```bash
cd /Users/macmini/openclaw/openclaw-dashboard
source .venv/bin/activate
python server.py
```


