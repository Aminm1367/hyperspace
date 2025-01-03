# hyperspace
آموزش ران کردن نود hyperspace


markdown
Copy code
# آموزش راه‌اندازی نود Hyperspace

در این آموزش یاد می‌گیرید چگونه یک نود Hyperspace را روی سرور VPS خود راه‌اندازی کنید.

---

## پیش‌نیازها
1. **یک سرور VPS با سیستم‌عامل Ubuntu 20.04 یا بالاتر.**
2. **اتصال به اینترنت.**
3. **کلید خصوصی (Private Key) از وب‌سایت Hyperspace.**

---

## مراحل نصب و راه‌اندازی

### 1. نصب ابزار AIOS
برای دانلود و نصب ابزار AIOS، دستور زیر را اجرا کنید:

```bash
curl https://download.hyper.space/api/install | bash
source /root/.bashrc
2. ذخیره کلید خصوصی
یک فایل برای ذخیره کلید خصوصی ایجاد کنید و کلید خود را داخل آن ذخیره کنید:

bash
Copy code
nano my.pem
سپس کلید خصوصی خود را درون فایل paste کرده و ذخیره کنید:

Ctrl + X برای خروج
Y برای تأیید ذخیره
Enter برای ذخیره فایل
دستورات زیر را برای اطمینان از تنظیمات اجرا کنید:

bash
Copy code
chmod 600 my.pem
3. شروع نود
یک Screen جدید باز کنید تا نود در پس‌زمینه اجرا شود:

bash
Copy code
screen -S hyperspace_node
داخل Screen، نود را شروع کنید:

bash
Copy code
aios-cli start
برای خروج از Screen بدون متوقف کردن نود، از دستور زیر استفاده کنید:

bash
Copy code
Ctrl + A + D
4. اضافه کردن مدل‌ها
برای مشاهده مدل‌های موجود، دستور زیر را اجرا کنید:

bash
Copy code
aios-cli models available
سپس یک مدل مناسب انتخاب و نصب کنید. به عنوان مثال:

bash
Copy code
aios-cli models add hf:TheBloke/phi-2-GGUF:phi-2.Q4_K_M.gguf
5. اتصال به شبکه Hyperspace
کلید خصوصی خود را وارد کنید و به شبکه متصل شوید:

bash
Copy code
aios-cli hive import-keys ./my.pem
aios-cli hive login
aios-cli hive connect
6. انتخاب Tier
Tier مناسب را بر اساس منابع VPS خود انتخاب کنید. مثلاً برای Tier 3:

bash
Copy code
aios-cli hive select-tier 3
7. بررسی وضعیت نود و دریافت امتیازات
وضعیت نود را بررسی کنید:

bash
Copy code
aios-cli hive points
دستورات عمومی
لیست کردن Screen‌ها:

bash
Copy code
screen -ls
ورود به Screen:

bash
Copy code
screen -r hyperspace_node
بستن Screen:

bash
Copy code
screen -X -S hyperspace_node quit
راه‌اندازی مجدد نود:

bash
Copy code
aios-cli kill
aios-cli start --connect
منابع
برای اطلاعات بیشتر، به گیت‌هاب Hyperspace مراجعه کنید.

yaml
Copy code

---
