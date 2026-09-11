# 💵 قیمت لحظه‌ای دلار — Live USD Price

قیمت لحظه‌ای دلار آمریکا (بازار آزاد تهران) از [tgju.org](https://www.tgju.org/profile/price_dollar_rl)، ارائه‌شده روی GitHub Pages.

## 🔗 لینک صفحه

**https://mohammad123-98.github.io/dollar-price/**

## ⚙️ معماری

```
tgju.org ──(GitHub Actions هر ۳۰ دقیقه)──► Gist (dollar_price.json)
                                                │
                                                ▼
                                    index.html روی GitHub Pages
                                    (fetch مستقیم از Gist)
```

1. **ورک‌فلو** [`.github/workflows/update-price.yml`](.github/workflows/update-price.yml) هر ۳۰ دقیقه اجرا می‌شود.
2. قیمت دلار (`price_dollar_rl`) از API سایت tgju.org خوانده می‌شود.
3. داده در فایل JSON داخل [گیست](https://gist.github.com/mohammad123-98/004dbecb707498c78bfa86a7d03203c9) ذخیره می‌شود (Gist ها هدر CORS باز دارند).
4. صفحه `index.html` با `fetch` داده را از Gist می‌خواند و نمایش می‌دهد.
5. صفحه هر ۶۰ ثانیه خودش را رفرش می‌کند.

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
