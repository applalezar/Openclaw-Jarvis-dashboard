# OpenClaw Dashboard

OpenClaw çok ajanlı gerçek zamanlı izleme paneli (FastAPI + Vue).

## Özellikler
- Sistem durumu: Gateway, CPU, Memory, kanal durumu
- Görevler: yerel yapılacaklar / geçmiş görevler
- Model kullanım panosu: MiniMax + OpenAI(GPT) + Gemini + GLM
- Model yapılandırma sayfası: API anahtarlarını web içinde kaydetme ve bağlantıyı doğrulama

## Güncelleme Notları (2026-02-17)
- Panonun düzeni iyileştirildi: yaygın çözünürlüklere uyum (1K/2K/4K/Notebook), kartlar masaüstü ve mobil cihazlarda daha kararlı hale geldi.
- Model kullanım panosu yükseltildi: çoklu model sekme yapısı eklendi (MiniMax / OpenAI / Gemini / GLM), ileride genişletme kolaylaştırıldı.
- Model yapılandırma deneyimi iyileştirildi: API anahtarları maskeli giriş ve düzenlenip kaydedildikten sonra etkinleştirildi; yanlış işlemler azaltıldı.
- Görev alanı ve işlem alanı stilleri birleştirildi: boş alan azaltıldı ve gereksiz kaydırma engellendi; bilgi yoğunluğu ve okunabilirlik yükseltildi.
- Yayın paketi sansürlendi: `.env`, loglar, önbellekler ve derleme çıktıları kaldırıldı; varsayılan olarak yerel hassas bilgiler dahil edilmez.

## 5 Dakikada Başlatma (Yeni Başlayanlar)

### macOS (Önerilen)
1. `/Users/macmini/openclaw/openclaw-dashboard/scripts/install-dashboard.command` dosyasına çift tıklayın.
2. Kurulum tamamlandıktan sonra terminali açıp şunu çalıştırın:
```bash
cd /Users/macmini/openclaw/openclaw-dashboard
source .venv/bin/activate
./start.sh
```
3. Tarayıcıda `http://localhost:18790` adresini açın.
4. Varsayılan hesap: `admin` / `admin123`
5. İlk girişten sonra parolanızı hemen değiştirmeyi öneririz.

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

## Model Kullanım Nasıl Yapılandırılır
1. Giriş yaptıktan sonra ana sayfaya gidin.
2. Sağ üst köşedeki `模型设置` (Model Ayarları) düğmesine tıklayın.
3. Gerekli alanları doldurun: MiniMax / OpenAI / Gemini / GLM için API bilgileri.
4. `验证` (Doğrula) düğmesine basın; başarılı olursa `保存配置` (Ayarları Kaydet) ile kaydedin.

### Her Model için Açıklama
- MiniMax: gerçek sayım desteği vardır (kullanılan / kota / oran).
- OpenAI(GPT): Usage API istek sayısı istatistiklerini destekler.
- Gemini: mevcut olarak durum özeti gösterilir (sayım kaynağı eklenmesi bekleniyor).
- GLM: mevcut olarak durum özeti gösterilir (sayım kaynağı eklenmesi bekleniyor).

## Yapılandırma Dosyaları
- Ortam değişkeni örneği: `/Users/macmini/openclaw/openclaw-dashboard/.env.example`
- Gerçek ortam değişkenleri: `/Users/macmini/openclaw/openclaw-dashboard/.env`
- Model entegrasyon yapılandırması: `~/.openclaw/dashboard_integrations.json`

## Sık Sorulan Sorular
- `Invalid or expired token`: yeniden giriş yapın.
- Sayfada veri yok: Gateway işleminin çalıştığını doğrulayın.
- MiniMax boş veri: GroupId / Quota URL / API Key değerlerinin doğru olduğundan emin olun.
- API Key güvenliği: ön yüz yalnızca maskelenmiş değeri gösterir; anahtar yerel dosyada saklanır.

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

## Projeyi Destekleyin

Bu proje size yardımcı olduysa, bana bir kahve ısmarlamanızı memnuniyetle kabul ederim.

![微信赞赏码](assets/social/wechat-donate.png)
