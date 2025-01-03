# آموزش راه‌اندازی نود Hyperspace

در این آموزش یاد می‌گیرید چگونه یک نود Hyperspace را روی سرور VPS خود راه‌اندازی کنید
## پیش‌نیازها
1. **یک سرور VPS با سیستم‌عامل Ubuntu 20.04 یا بالاتر.**
2. **اتصال به اینترنت.**
3. **کلید خصوصی (Private Key) از وب‌سایت Hyperspace.**

   
## مراحل نصب و راه‌اندازی

### 1. نصب ابزار AIOS
برای دانلود و نصب ابزار AIOS، دستور زیر را اجرا کنید:
```bash
   curl https://download.hyper.space/api/install | bash
   ```
تنظیمات Bash را بارگذاری کنید:
 ```bash
   source /root/.bashrc
   ```

### 2. ایجاد فایل برای ذخیره کلید خصوصی:
با استفاده از ویرایشگر nano یک فایل ایجاد کنید:
```bash
  nano my.pem
  ```
کلید خصوصی را در این فایل جای‌گذاری کرده و ذخیره کنید:

برای ذخیره، کلیدهای Ctrl + X، سپس Y و Enter را فشار دهید. دسترسی به فایل را محدود کنید:
 ```bash
  chmod 600 my.pem
  ```

### 3. ایجاد جلسه Screen:
```bash
   screen -S airdropnode_aios
   ```
سپس نود AIOS را راه‌اندازی کنید:
```bash
   aios-cli start
   ```
برای خروج از Screen بدون توقف فرآیند:

کلیدهای Ctrl + A و سپس D را فشار دهید.


### 4. مدیریت مدل‌ها و انتخاب Tier:
لیست مدل‌های موجود را مشاهده کنید:

```bash
   aios-cli models available
   ```
یک مدل را اضافه کنید (مثلاً):
```bash
  aios-cli models add hf:TheBloke/phi-2-GGUF:phi-2.Q4_K_M.gguf
  ```
باید به حجم مدل ها دقت کنید بعضیا خیلی سنگین هستند.



### .5 وارد کردن کلید خصوصی و ورود به شبکه Hive:

کلید خصوصی را وارد کنید:
```bash
  aios-cli hive import-keys ./my.pem
  ```
ورود به شبکه:
```bash
aios-cli hive login
aios-cli hive connect
```


### 6. بررسی امتیازات و وضعیت کلیدها:
مشاهده امتیازات:
```bash
aios-cli hive points
```
بررسی کلید خصوصی و عمومی:
```bash
aios-cli hive whoami
```


### 7. راه‌اندازی مجدد یا ادامه فرآیند:

برای توقف و راه‌اندازی مجدد:
```bash
aios-cli kill
aios-cli start --connect
```
برای بازگشت به Screen:

```bash
screen -r airdropnode_aios
```


## منابع بیشتر:
مستندات رسمی در GitHub: Hyperspace AIOS CLI
