# 💵 قیمت لحظه‌ای دلار — Live USD Price

قیمت لحظه‌ای دلار آمریکا (بازار آزاد تهران) از [tgju.org](https://www.tgju.org/profile/price_dollar_rl)، ارائه‌شده روی GitHub Pages.

## 🔗 لینک صفحه

**https://mohammad123-98.github.io/dollar-price/**

## ⚙️ معماری

```
                ┌── (مستقیم از مرورگر، هر ۳۰ ثانیه — زنده) ──┐
index.html ──► │            api.tgju.org (CORS باز)             │
                └── (فال‌بک: هر ۵ دقیقه) ──────────────────┐   │
                                                            ▼   ▼
tgju.org ──(GitHub Actions هر ۵ دقیقه)──► Gist (dollar_price.json)
```

1. صفحه `index.html` اول تلاش می‌کند قیمت را **مستقیم از API سایت tgju.org** بخواند (به‌روزرسانی زنده هر ۳۰ ثانیه).
2. اگر API مستقیم در دسترس نبود، از **گیست** به عنوان پشتیبان استفاده می‌کند.
3. **ورک‌فلو** [`.github/workflows/update-price.yml`](.github/workflows/update-price.yml) هر **۵ دقیقه** (حداقل مجاز در GitHub Actions) اجرا می‌شود و گیست را به‌روز نگه می‌دارد.

## 📄 ساختار فایل داده

```json
{
  "price_rial": 2359750,
  "price_toman": 235975,
  "high_rial": 2360200,
  "low_rial": 2338600,
  "change_rial": 0,
  "change_percent": 0,
  "direction": "stable",
  "last_updated_tehran": "2026-09-11 23:49"
}
```

## 🔐 نیازمندی‌ها

- یک توکن GitHub با دسترسی `gist` به عنوان Secret با نام `GIST_TOKEN` در تنظیمات ریپو (Settings → Secrets and variables → Actions).

## 🧰 اجرای دستی

از تب Actions ریپو، روی ورک‌فلو **Update Dollar Price** و بعد **Run workflow** بزنید.
