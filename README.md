# Email Microservice - Python FastAPI

Mağaza Projesi için ayrı Email Mikroservis uygulaması.

## 🏗️ Mimari

```
Spring Boot (13.60.76.224:8080)
         │
         ├─ REST API (HTTP POST)
         ↓
Python FastAPI (16.16.197.152:8000)
         │
         ├─ Gmail SMTP
         ↓
User Email Inbox
```

## 🚀 Endpoints

| Method | Endpoint | Açıklama |
|--------|----------|----------|
| GET | `/` | Health check |
| GET | `/health` | Servis durumu |
| POST | `/api/email/welcome` | Hoşgeldin maili |
| POST | `/api/email/order` | Sipariş özeti maili |
| POST | `/api/email/send` | Genel mail gönderimi |

## ⚙️ Kurulum

### Yerel Geliştirme

```bash
pip install -r requirements.txt
python main.py
```

### AWS EC2

```bash
# SSH ile bağlan
ssh -i magaza-key.pem ubuntu@16.16.197.152

# Projeyi klonla
git clone https://github.com/omerdikmen13/email-microservice.git
cd email-microservice

# Bağımlılıkları kur
pip3 install -r requirements.txt

# Servisi başlat
nohup python3 -m uvicorn main:app --host 0.0.0.0 --port 8000 > email.log 2>&1 &
```

## 📧 Environment Variables

`.env` dosyası oluştur:

```
MAIL_HOST=smtp.gmail.com
MAIL_PORT=587
MAIL_USER=your-email@gmail.com
MAIL_PASS=your-app-password
```

## 🔗 Spring Boot Entegrasyonu

Spring Boot `application.properties`:

```properties
email.microservice.url=http://16.16.197.152:8000
```

## 📄 Lisans

MIT
