# Hava Durumu Uyarı Sistemi

Bu Python betiği, OpenWeatherMap API'sini kullanarak Gaziantep'teki hava durumu verilerini alır ve belirli hava koşullarına göre e-posta uyarıları gönderir. Sistemde düşük sıcaklık ve şiddetli rüzgar gibi hava durumu olaylarına karşı uyarılar verilir.

## Özellikler

- **Hava Durumu Verisi Alımı**: Gaziantep için OpenWeatherMap API'sinden anlık hava durumu verileri alınır.
- **E-posta Uyarıları**: Hava durumu koşullarına göre (örneğin sıcaklık 0°C'nin altına düşerse veya rüzgar hızı 10 m/s'nin üzerine çıkarsa) belirlenen alıcıya e-posta gönderilir.
- **Otomatik Kontrol**: Betik, belirli aralıklarla (örneğin her saat başı) hava durumu verilerini kontrol eder.

## Gereksinimler

- Python 3.x
- `requests` ve `smtplib` kütüphaneleri
- OpenWeatherMap API anahtarı
- E-posta gönderimi için bir Gmail hesabı

## Kurulum

1. **Bağımlılıkların Yüklenmesi**:
   Projenin çalışabilmesi için gerekli Python kütüphanelerini yükleyin:
   ```bash
   pip install requests
   ```

2. **Çevresel Değişkenlerin Tanımlanması**:
   API anahtarınız, gönderici e-posta adresi, şifre ve alıcı e-posta adresi gibi bilgileri çevresel değişkenler olarak tanımlamanız gerekmektedir.

   ```bash
   export OPENWEATHER_API_KEY='your_openweather_api_key'
   export SENDER_EMAIL='your_email@gmail.com'
   export SENDER_PASSWORD='your_email_password'
   export RECEIVER_EMAIL='receiver_email@gmail.com'
   ```

3. **SMTP Hesap Ayarları**:
   Bu sistem Gmail SMTP sunucusunu kullanarak e-posta gönderir. Gmail hesabınızı kullanarak giriş yapabilmeniz için 2 adımlı doğrulama ve "Daha az güvenli uygulama erişimi" ayarlarını açmanız gerekebilir.

## Kullanım

1. **Ana Betik Çalıştırma**:
   Betiği çalıştırarak hava durumu uyarılarını otomatik olarak alabilirsiniz. Betik sürekli olarak belirli bir zaman aralığı (varsayılan olarak 1 saat) ile hava durumu kontrolü yapacak ve gerekli uyarıları gönderecektir.

   ```bash
   python weather_alert_system.py
   ```

2. **Çalışma Süresi**:
   Betik her 3600 saniyede (1 saatte bir) hava durumu verilerini kontrol eder ve belirlenen koşullara göre e-posta gönderir.

## Hava Durumu Koşulları

- **Düşük Sıcaklık Uyarısı**: Sıcaklık 0°C'nin altına düşerse bir e-posta uyarısı gönderilir.
- **Şiddetli Rüzgar Uyarısı**: Rüzgar hızı 10 m/s'nin üzerine çıkarsa bir e-posta uyarısı gönderilir.

## Özelleştirme

- **Sıcaklık ve Rüzgar Hızı Sınırları**: Eğer başka hava durumu koşullarına göre uyarı göndermek isterseniz, `check_weather_conditions` fonksiyonunda koşulları değiştirebilirsiniz.
- **E-posta İçeriği ve Başlıkları**: E-posta başlıklarını ve içeriğini `send_warning_email` fonksiyonunda özelleştirebilirsiniz.

## Sorun Giderme

- **API Anahtarı Hatası**: API anahtarınızın geçerli olup olmadığını kontrol edin.
- **SMTP Bağlantı Hatası**: Gmail hesabınızın doğru ayarlarla yapılandırıldığından emin olun.
