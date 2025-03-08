# Avtomatik E-mail Yuborish (SMTP yordamida)

Bu loyiha Gmail yoki boshqa SMTP server orqali avtomatik ravishda e-mail yuborish uchun Python skriptini o'z ichiga oladi.

## 📌 Talablar

Loyihani ishga tushirish uchun quyidagi kutubxonalar talab qilinadi:

```sh
pip install smtplib email
```

## 📜 Foydalanish

1. **SMTP sozlamalarini kiriting**
   - `your_email@gmail.com` ni o'zingizning email manzilingiz bilan almashtiring.
   - `your_password` o'rniga haqiqiy email parolingizni kiriting yoki "App Password" dan foydalaning.
   
2. **Kodni ishga tushiring**
   - Quyidagi Python skriptini ishga tushirish orqali e-mail yuborishingiz mumkin:
   
```python
import smtplib
from email.mime.text import MIMEText

SMTP_SERVER = "smtp.gmail.com"
SMTP_PORT = 587
EMAIL = "your_email@gmail.com"
PASSWORD = "your_password"

def send_email(to_email, subject, message):
    msg = MIMEText(message)
    msg["Subject"] = subject
    msg["From"] = EMAIL
    msg["To"] = to_email

    try:
        server = smtplib.SMTP(SMTP_SERVER, SMTP_PORT)
        server.starttls()
        server.login(EMAIL, PASSWORD)
        server.sendmail(EMAIL, to_email, msg.as_string())
        server.quit()
        print("✅ Email muvaffaqiyatli yuborildi!")
    except Exception as e:
        print(f"❌ Xatolik yuz berdi: {e}")

# Test qilish uchun
send_email("receiver@example.com", "Salom!", "Bu test xabari.")
```

## ⚠️ Muhim!

Agar Gmail-dan foydalansangiz:
- "Less Secure Apps" funksiyasini yoqing **yoki**
- "App Password" yaratib, undan foydalaning.

## 📎 Qo‘shimcha ma’lumotlar

- **SMTP serverlar:**
  - Gmail: `smtp.gmail.com` (port: 587 yoki 465)
  - Outlook: `smtp.office365.com` (port: 587)
  - Yahoo: `smtp.mail.yahoo.com` (port: 465)

## 📬 Muallif

Loyiha muallifi: **Sizning ismingiz**

---

✅ Agar muammo bo'lsa, qo'shimcha yordam so'rashingiz mumkin! 🚀

