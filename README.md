# tarnamagard.ir

![Logo](https://via.placeholder.com/150) <!-- لوگوی پروژه را جایگزین کنید -->

ترنم آگرد یک **موتور جستجوی محلی** برای ایرانیان است که به کاربران کمک می‌کند تا اطلاعات مورد نظر خود را به سرعت و به صورت دقیق پیدا کنند. این پروژه از API‌های رایگان، Crawler هوشمند و پردازش طبیعی زبان (NLP) برای بهبود نتایج جستجو استفاده می‌کند.

---

## 🌟 ویژگی‌ها

- **جستجوی هوشمند:**  
  با استفاده از API‌های رایگان مانند DuckDuckGo، NewsAPI و Wikipedia، نتایج جستجو به صورت گسترده و دقیق ارائه می‌شوند.

- **Crawler شخصی‌سازی‌شده:**  
  یک Crawler هوشمند برای جمع‌آوری داده‌ها از وب‌سایت‌های محلی و ذخیره آن‌ها در پایگاه داده.

- **پردازش طبیعی زبان (NLP):**  
  استفاده از الگوریتم‌های NLP برای تحلیل متن و رتبه‌بندی نتایج بر اساس مرتبط‌ترین محتوا.

- **پنل مدیریت:**  
  یک پنل مدیریت کامل برای نظارت بر عملکرد، مدیریت داده‌ها و تنظیمات سیستم.

- **طراحی واکنش‌گرا:**  
  استفاده از Bootstrap برای طراحی زیبا و سازگار با تمام دستگاه‌ها (موبایل، تبلت و دسکتاپ).

---

## 🚀 نصب و راه‌اندازی

### 1. Clone کردن پروژه:
```bash
git clone https://github.com/balvardi/tarnamagard.git
cd tarnamagard
```

### 2. نصب وابستگی‌ها:
ابتدا مطمئن شوید که [Composer](https://getcomposer.org/) روی سیستم شما نصب است. سپس وابستگی‌ها را نصب کنید:
```bash
composer install
```

### 3. تنظیم پایگاه داده:
- یک پایگاه داده MySQL ایجاد کنید.
- فایل `db.php` را ویرایش کنید و اطلاعات پایگاه داده خود را وارد کنید:
```php
$host = 'localhost';
$dbname = 'tarnamagard';
$username = 'YOUR_DB_USERNAME';
$password = 'YOUR_DB_PASSWORD';
```

- جدول‌های پایگاه داده را ایجاد کنید. می‌توانید از فایل SQL زیر استفاده کنید:
```sql
CREATE TABLE pages (
    id INT AUTO_INCREMENT PRIMARY KEY,
    url VARCHAR(255) NOT NULL UNIQUE,
    title VARCHAR(255),
    description TEXT,
    content TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE keywords (
    id INT AUTO_INCREMENT PRIMARY KEY,
    page_id INT,
    keyword VARCHAR(255),
    FOREIGN KEY (page_id) REFERENCES pages(id) ON DELETE CASCADE
);

CREATE TABLE crawl_queue (
    id INT AUTO_INCREMENT PRIMARY KEY,
    url VARCHAR(255) NOT NULL UNIQUE,
    crawled TINYINT(1) DEFAULT 0
);

CREATE TABLE settings (
    key_name VARCHAR(255) PRIMARY KEY,
    value TEXT
);

CREATE TABLE logs (
    id INT AUTO_INCREMENT PRIMARY KEY,
    message TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE admins (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(255) NOT NULL UNIQUE,
    password_hash VARCHAR(255) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### 4. اجرای پروژه:
- سرور محلی خود را راه‌اندازی کنید (مثلاً با استفاده از XAMPP یا PHP Built-in Server):
```bash
php -S localhost:8000
```
- در مرورگر، آدرس زیر را باز کنید:
```
http://localhost:8000/index.php
```

---

## 🛠️ وابستگی‌ها

این پروژه از کتابخانه‌ها و ابزارهای زیر استفاده می‌کند:

- **PHP >= 7.4**
- **MySQL**
- **Bootstrap** ([Link](https://getbootstrap.com/))
- **Chart.js** ([Link](https://www.chartjs.org/))
- **PHP-ML** ([Link](https://php-ml.readthedocs.io/))
- **GuzzleHttp** ([Link](https://docs.guzzlephp.org/))
- **Symfony DomCrawler** ([Link](https://symfony.com/doc/current/components/dom_crawler.html))

---

## 📊 ساختار پروژه

```
tarnamagard/
├── admin/               # پنل مدیریت
├── api.php              # مدیریت API‌ها
├── crawler.php          # Crawler برای جمع‌آوری داده‌ها
├── nlp.php              # پردازش طبیعی زبان (NLP)
├── search.php           # صفحه نتایج جستجو
├── index.php            # صفحه اصلی
├── db.php               # اتصال به پایگاه داده
├── assets/              # فایل‌های CSS و JavaScript
└── README.md            # مستندات پروژه
```

---

## 🛠️ نحوه مشارکت

اگر علاقه‌مند به مشارکت در این پروژه هستید، می‌توانید با انجام مراحل زیر کمک کنید:

1. Fork کردن پروژه.
2. ایجاد یک شاخه جدید (`git checkout -b feature/YourFeatureName`).
3. اعمال تغییرات و Commit کردن (`git commit -m "Add some feature"`).
4. Push کردن تغییرات (`git push origin feature/YourFeatureName`).
5. ارسال Pull Request.

---

## 📜 لایسنس

این پروژه تحت لایسنس [MIT License](https://opensource.org/licenses/MIT) منتشر شده است.  
برای اطلاعات بیشتر، فایل [LICENSE](LICENSE) را مشاهده کنید.

---

## 📧 ارتباط

اگر سوالی دارید یا پیشنهادی برای بهبود پروژه دارید، می‌توانید با من تماس بگیرید:

- **ایمیل:** r.balvardi@gmail.com
- **وب‌سایت:** [tarnamagard.ir](https://tarnamagard.ir)

---

### 🌟 تشکر
از اینکه وقت گذاشتید و این پروژه را بررسی کردید، ممنونم! امیدوارم که از آن لذت ببرید و از آن استفاده کنید. اگر ایده‌ای برای بهبود پروژه دارید، حتماً با من در میان بگذارید. 🚀
