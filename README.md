# AVAXUSDT EMA13 Telegram Alert Bot

Bu bot Binance Spot'taki AVAXUSDT paritesinin 1 saatlik kapanmış mumlarını kontrol eder.

Sinyal şartı:

- Önceki kapanış <= önceki EMA13
- Son kapanış > son EMA13

Şart gerçekleşirse Telegram'a mesaj gönderir.

## Dosyalar

- `main.py` - bot kodu
- `requirements.txt` - Python bağımlılığı
- `render.yaml` - Render Cron Job ayarı

## Telegram

1. Telegram'da `@BotFather` üzerinden bir bot oluştur.
2. Bot token'ını al.
3. Kendi botuna `/start` gönder.
4. Telegram API'nin `getUpdates` çıktısından kendi `chat.id` değerini öğren.
5. Token ve chat ID'yi Render Environment Variables kısmına ekle.

Environment variables:

- `TELEGRAM_BOT_TOKEN`
- `TELEGRAM_CHAT_ID`

Bot token'ını GitHub'a veya koda yazma.

## Render

Bu proje `render.yaml` ile Cron Job olarak tasarlanmıştır.

Cron:
`1 * * * *`

Yani her saat UTC'nin 1. dakikasında çalışır. Binance'ten son kapanmış 1H mum alınır ve EMA13 yukarı kırılımı kontrol edilir.

Not: Render cron job'ları UTC zamanlaması kullanır. Cron servislerinin ücretlendirmesi Render'ın güncel planına göre yapılır.

Bu bot işlem açmaz veya kapatmaz; yalnızca Telegram uyarısı gönderir.
