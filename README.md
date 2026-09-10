
<div align="center">

# ⚡ WIXEROX v7.0

### 💀 Multi-Vector Attack Suite

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)
[![Platform](https://img.shields.io/badge/Platform-Linux%20%7C%20Termux%20%7C%20Windows-red?style=for-the-badge)](https://github.com/)
[![Status](https://img.shields.io/badge/Status-Educational-yellow?style=for-the-badge)]()

**🌐 Website:** [wixerox.ir](https://wixerox.ir)  
**📱 Telegram:** [@wixerox](https://t.me/wixerox)

</div>

---

> ⚠️ **IMPORTANT NOTICE / توجه مهم**
> 
> This project is **completely educational** and is intended to **increase public knowledge** about network security and stress testing.
> 
> The author **takes no responsibility** for any misuse of this tool. **Any responsibility for improper use lies solely with the user.**
> 
> این پروژه **کاملاً آموزشی** بوده و هدف آن **افزایش دانش عمومی** کاربران درباره امنیت شبکه و تست فشار است.
> 
> نویسنده **هیچ‌گونه مسئولیتی** در قبال استفاده نادرست از این ابزار **نمی‌پذیرد**. **تمام مسئولیت استفاده نادرست به عهده فرد استفاده‌کننده است.**

---

## 📖 Table of Contents | فهرست مطالب

- [🇬🇧 English Documentation](#-english-documentation)
- [🇮🇷 مستندات فارسی](#-مستندات-فارسی)

---

# 🇬🇧 English Documentation

## 🔍 Overview

**WIXEROX v7.0** is a high-performance, multi-vector network stress testing tool written in Python. It combines three attack vectors—**HTTP Flood**, **Slowloris**, and **Socket Flood**—into a single, easy-to-use command-line interface.

> 🎓 **This project is provided for educational purposes only** to help users learn about network security concepts and stress testing methodologies. The author takes no responsibility for any misuse. **Users bear full responsibility for their own actions.**

---

## ✨ Features

- 🚀 **Three Attack Vectors Simultaneously**
  - HTTP Flood (GET/POST/HEAD)
  - Slowloris (slow headers)
  - Socket Flood (raw TCP packets)

- 🎭 **Advanced Bypass Mechanisms**
  - Random User-Agent rotation (10+ fallbacks + fake-useragent)
  - Proxy chain support (30+ sources)
  - Cloudflare bypass via cloudscraper
  - TLS fingerprint impersonation via curl_cffi
  - HTTP/2 support via httpx

- 🧠 **Auto-Calibration Engine**
  - 60-second system analysis
  - Automatic worker/connection tuning
  - RAM and CPU-aware optimization

- 🌐 **Smart Proxy Management**
  - Automatic fetch from 30+ sources
  - DNS + HTTP verification
  - Background refresh every 30 seconds
  - Latency-based sorting

- 📊 **Real-Time Monitoring**
  - Live statistics every 5-10 seconds
  - Attack rate (requests/sec)
  - Active connections count
  - Total packets sent

- 🎨 **Beautiful Terminal UI**
  - Color-coded logging
  - Progress bars via tqdm
  - Clean banner and layout

---

## 📋 Requirements

### System
- **OS:** Linux / Termux / Windows / macOS
- **Python:** 3.8 or higher
- **RAM:** 512 MB minimum (2 GB recommended)
- **CPU:** 1 core minimum (multi-core recommended)
- **Network:** Stable internet connection

### Python Libraries
```
aiohttp>=3.8.0
psutil>=5.9.0
fake-useragent>=1.4.0
httpx>=0.25.0
curl_cffi>=0.5.0
cloudscraper>=1.2.71
colorama>=0.4.6
tqdm>=4.65.0
requests>=2.31.0
pysocks>=1.7.1
```

---

## 🔧 Installation

### Step 1: Clone the Repository
```bash
git clone https://github.com/wixerox/wixerox.git
cd wixerox
```

### Step 2: Install Dependencies

**Option A — Using requirements.txt (recommended):**
```bash
pip install -r requirements.txt
```

**Option B — Manual installation:**
```bash
pip install aiohttp psutil fake-useragent httpx curl_cffi cloudscraper colorama tqdm requests pysocks
```

**Option C — On Debian/Ubuntu with PEP 668 restrictions:**
```bash
pip install -r requirements.txt --break-system-packages
```

**Option D — Inside a virtual environment (safest):**
```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

### Step 3: Verify Installation
```bash
python wixerox.py --help
```

---

## 🚀 Usage

### Basic Syntax
```bash
python wixerox.py [TARGET_URL] [OPTIONS]
```

### Interactive Mode
If you don't provide a target URL, the script will ask for one:
```bash
python wixerox.py
# Enter target URL: http://example.com:80
```

---

## 🎛️ Command-Line Options

| Option | Description | Default |
|--------|-------------|---------|
| `target` | Target URL (e.g., `http://example.com:80`) | prompted |
| `--workers N` | Number of HTTP workers | auto |
| `--connections N` | Max Slowloris connections | auto |
| `--rate N` | Packet rate for Socket Flood | auto |
| `--max-workers N` | Maximum workers cap | 2000 |
| `--no-slowloris` | Disable Slowloris attack | off |
| `--no-socket` | Disable Socket Flood attack | off |
| `--no-scan` | Skip port scan (use specified port) | off |
| `--no-proxy` | Disable proxy (exposes your IP) | off |
| `--no-httpx` | Disable HTTP/2 transport | off |
| `--no-cloudscraper` | Disable Cloudflare bypass | off |
| `--no-curl-cffi` | Disable curl_cffi impersonation | off |

---

## 📚 Examples

### Example 1: Full Power Attack (All Vectors)
```bash
python wixerox.py http://target.com:80 --workers 3000 --max-workers 5000
```

### Example 2: HTTP Flood Only (Fastest)
```bash
python wixerox.py http://target.com:80 --workers 3000 --no-proxy --no-scan --no-slowloris --no-socket
```

### Example 3: With Proxy Chain (Stealth Mode)
```bash
python wixerox.py https://target.com:443 --workers 1500
```

### Example 4: Slowloris Focus
```bash
python wixerox.py https://target.com:443 --connections 3000 --no-socket
```

### Example 5: Socket Flood Focus
```bash
python wixerox.py http://target.com:80 --rate 5000 --no-slowloris
```

### Example 6: Custom Port
```bash
python wixerox.py https://target.com:8443 --workers 2000 --no-scan
```

### Example 7: Bypass All Libraries (Direct Mode)
```bash
python wixerox.py http://target.com:80 --no-httpx --no-cloudscraper --no-curl-cffi --no-proxy
```

---

## 🛑 Stopping the Attack

- Press **`Ctrl + C`** to stop gracefully.
- If it doesn't respond, open a new terminal and run:
```bash
pkill -f wixerox.py
```

---

## ⚠️ Disclaimer

**This project is provided for educational purposes only.**

The goal of this project is to increase public awareness and knowledge about network security, stress testing, and how modern web servers handle high-load scenarios.

- The author is **not responsible** for any misuse or damage caused by this software.
- **Any responsibility for improper use lies solely with the user.**
- Do not use it against systems you do not own or have written permission to test.
- Unauthorized use may violate local, national, and international laws.

---

# 🇮🇷 مستندات فارسی

## 🔍 معرفی

**WIXEROX v7.0** یک ابزار تست فشار شبکه‌ی چندبرداری و پرسرعت است که با زبان پایتون نوشته شده. این ابزار سه روش حمله‌ی مختلف را در یک رابط خط فرمان ساده ترکیب می‌کند:

- **HTTP Flood** (سیل درخواست‌های HTTP)
- **Slowloris** (اتصال‌های کند و طولانی)
- **Socket Flood** (سیل بسته‌های TCP خام)

> 🎓 **این پروژه کاملاً آموزشی است** و هدف آن افزایش دانش عمومی کاربران درباره مفاهیم امنیت شبکه و روش‌های تست فشار می‌باشد. نویسنده هیچ‌گونه مسئولیتی در قبال استفاده نادرست **نمی‌پذیرد**. **تمام مسئولیت استفاده نادرست به عهده فرد استفاده‌کننده است.**

---

## ✨ ویژگی‌ها

- 🚀 **سه روش حمله همزمان**
  - HTTP Flood (GET/POST/HEAD)
  - Slowloris (هدرهای کند)
  - Socket Flood (بسته‌های TCP خام)

- 🎭 **مکانیزم‌های دورزدن پیشرفته**
  - چرخش User-Agent تصادفی (بیش از ۱۰ جایگزین + fake-useragent)
  - پشتیبانی از زنجیره پروکسی (بیش از ۳۰ منبع)
  - دورزدن Cloudflare با cloudscraper
  - جعل اثر انگشت TLS با curl_cffi
  - پشتیبانی از HTTP/2 با httpx

- 🧠 **موتور کالیبراسیون خودکار**
  - تحلیل ۶۰ ثانیه‌ای سیستم
  - تنظیم خودکار کارگرها و اتصالات
  - بهینه‌سازی بر اساس RAM و CPU

- 🌐 **مدیریت هوشمند پروکسی**
  - دریافت خودکار از ۳۰+ منبع
  - تأیید با DNS و HTTP
  - تازه‌سازی پس‌زمینه هر ۳۰ ثانیه
  - مرتب‌سازی بر اساس تأخیر

- 📊 **مانیتورینگ لحظه‌ای**
  - آمار زنده هر ۵-۱۰ ثانیه
  - نرخ حمله (درخواست در ثانیه)
  - تعداد اتصالات فعال
  - مجموع بسته‌های ارسالی

- 🎨 **رابط ترمینال زیبا**
  - لاگ‌های رنگی
  - نوار پیشرفت با tqdm
  - بنر و چیدمان تمیز

---

## 📋 پیش‌نیازها

### سیستم
- **سیستم‌عامل:** Linux / Termux / Windows / macOS
- **پایتون:** نسخه ۳.۸ یا بالاتر
- **رم:** حداقل ۵۱۲ مگابایت (۲ گیگابایت توصیه می‌شود)
- **پردازنده:** حداقل ۱ هسته (چند هسته توصیه می‌شود)
- **شبکه:** اتصال اینترنت پایدار

### کتابخانه‌های پایتون
```
aiohttp>=3.8.0
psutil>=5.9.0
fake-useragent>=1.4.0
httpx>=0.25.0
curl_cffi>=0.5.0
cloudscraper>=1.2.71
colorama>=0.4.6
tqdm>=4.65.0
requests>=2.31.0
pysocks>=1.7.1
```

---

## 🔧 نصب

### مرحله ۱: کلون کردن ریپازیتوری
```bash
git clone https://github.com/wixerox/wixerox.git
cd wixerox
```

### مرحله ۲: نصب وابستگی‌ها

**روش الف — استفاده از requirements.txt (توصیه‌شده):**
```bash
pip install -r requirements.txt
```

**روش ب — نصب دستی:**
```bash
pip install aiohttp psutil fake-useragent httpx curl_cffi cloudscraper colorama tqdm requests pysocks
```

**روش ج — روی Debian/Ubuntu با محدودیت PEP 668:**
```bash
pip install -r requirements.txt --break-system-packages
```

**روش د — داخل محیط مجازی (امن‌ترین):**
```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

### مرحله ۳: تأیید نصب
```bash
python wixerox.py --help
```

---

## 🚀 نحوه استفاده

### سینتکس پایه
```bash
python wixerox.py [آدرس هدف] [گزینه‌ها]
```

### حالت تعاملی
اگر آدرس هدف را وارد نکنید، اسکریپت خودش می‌پرسد:
```bash
python wixerox.py
# Enter target URL: http://example.com:80
```

---

## 🎛️ گزینه‌های خط فرمان

| گزینه | توضیح | پیش‌فرض |
|-------|-------|---------|
| `target` | آدرس هدف (مثلاً `http://example.com:80`) | پرسیده می‌شود |
| `--workers N` | تعداد کارگرهای HTTP | خودکار |
| `--connections N` | حداکثر اتصالات Slowloris | خودکار |
| `--rate N` | نرخ بسته برای Socket Flood | خودکار |
| `--max-workers N` | سقف کارگرها | ۲۰۰۰ |
| `--no-slowloris` | غیرفعال کردن Slowloris | خاموش |
| `--no-socket` | غیرفعال کردن Socket Flood | خاموش |
| `--no-scan` | حذف اسکن پورت | خاموش |
| `--no-proxy` | غیرفعال کردن پروکسی (آی‌پی لو می‌رود) | خاموش |
| `--no-httpx` | غیرفعال کردن HTTP/2 | خاموش |
| `--no-cloudscraper` | غیرفعال کردن دورزدن Cloudflare | خاموش |
| `--no-curl-cffi` | غیرفعال کردن curl_cffi | خاموش |

---

## 📚 مثال‌ها

### مثال ۱: حمله کامل (همه روش‌ها)
```bash
python wixerox.py http://target.com:80 --workers 3000 --max-workers 5000
```

### مثال ۲: فقط HTTP Flood (سریع‌ترین)
```bash
python wixerox.py http://target.com:80 --workers 3000 --no-proxy --no-scan --no-slowloris --no-socket
```

### مثال ۳: با زنجیره پروکسی (حالت مخفی)
```bash
python wixerox.py https://target.com:443 --workers 1500
```

### مثال ۴: تمرکز روی Slowloris
```bash
python wixerox.py https://target.com:443 --connections 3000 --no-socket
```

### مثال ۵: تمرکز روی Socket Flood
```bash
python wixerox.py http://target.com:80 --rate 5000 --no-slowloris
```

### مثال ۶: پورت سفارشی
```bash
python wixerox.py https://target.com:8443 --workers 2000 --no-scan
```

### مثال ۷: غیرفعال کردن همه کتابخانه‌ها (حالت مستقیم)
```bash
python wixerox.py http://target.com:80 --no-httpx --no-cloudscraper --no-curl-cffi --no-proxy
```

---

## 🛑 متوقف کردن حمله

- کلید **`Ctrl + C`** را بزنید تا به‌صورت نرم متوقف شود.
- اگر پاسخ نداد، یک ترمینال جدید باز کنید و این دستور را بزنید:
```bash
pkill -f wixerox.py
```

---

## ⚠️ سلب مسئولیت

**این پروژه کاملاً آموزشی است.**

هدف این پروژه افزایش آگاهی و دانش عمومی کاربران درباره امنیت شبکه، تست فشار، و نحوه برخورد سرورهای وب مدرن با بار سنگین است.

- نویسنده **هیچ‌گونه مسئولیتی** در قبال سوءاستفاده یا خسارت ناشی از این نرم‌افزار **نمی‌پذیرد**.
- **تمام مسئولیت استفاده نادرست به عهده فرد استفاده‌کننده است.**
- از آن علیه سیستم‌هایی که مالک آن‌ها نیستید یا مجوز کتبی ندارید، استفاده نکنید.
- استفاده غیرمجاز ممکن است قوانین محلی، ملی و بین‌المللی را نقض کند.

---

<div align="center">

### 🌐 Connect With Us | با ما در ارتباط باشید

[![Website](https://img.shields.io/badge/Website-wixerox.ir-blue?style=for-the-badge&logo=google-chrome)](https://wixerox.ir)
[![Telegram](https://img.shields.io/badge/Telegram-@wixerox-2CA5E0?style=for-the-badge&logo=telegram)](https://t.me/wixerox)

**Made with ❤️ by WIXEROX**

⭐ If you find this project useful, please give it a star! ⭐  
⭐ اگر این پروژه برایتان مفید بود، یک ستاره بدهید! ⭐

</div>
