نمونه قالب‌بندی:

Copy code
# آموزش اجرای نود Hyperspace

در این آموزش مراحل نصب و اجرای نود Hyperspace توضیح داده شده است.

---

## ۱. نصب AIOS

برای نصب و راه‌اندازی AIOS، دستور زیر را وارد کنید:

```bash
curl https://download.hyper.space/api/install | bash
بعد از اتمام نصب، برای اعمال تغییرات، دستور زیر را اجرا کنید:

bash
Copy code
source /root/.bashrc
۲. ذخیره کلید خصوصی
ابتدا یک فایل جدید به نام my.pem ایجاد کنید:

bash
Copy code
nano my.pem
کلید خصوصی خود را داخل این فایل قرار دهید و آن را ذخیره کنید (Ctrl + X و سپس Enter را بزنید). بعد از آن سطح دسترسی فایل را تغییر دهید:

bash
Copy code
chmod 600 my.pem
۳. اجرای نود
برای اجرای نود، ابتدا یک اسکرین جدید باز کنید:

bash
Copy code
screen -S airdropnode_aios
سپس دستور زیر را برای شروع نود وارد کنید:

bash
Copy code
aios-cli start
برای خروج از اسکرین بدون بستن آن، از ترکیب کلید‌های زیر استفاده کنید:

text
Copy code
CTRL + A + D
۴. انتخاب مدل و Tier
ابتدا لیست مدل‌های موجود را مشاهده کنید:

bash
Copy code
aios-cli models available
سپس Tier مناسب را انتخاب کنید (به عنوان مثال Tier 3):

bash
Copy code
aios-cli hive select-tier 3
مدل مناسب را اضافه کنید (مثال):

bash
Copy code
aios-cli models add hf:TheBloke/phi-2-GGUF:phi-2.Q4_K_M.gguf
۵. بررسی وضعیت
برای مشاهده وضعیت کلید عمومی و خصوصی، دستور زیر را اجرا کنید:

bash
Copy code
aios-cli hive whoami
برای مشاهده امتیازات:

bash
Copy code
aios-cli hive points
نکات پایانی
در صورت نیاز به توقف یا راه‌اندازی مجدد نود، از دستورات زیر استفاده کنید:

توقف نود:

bash
Copy code
aios-cli kill
راه‌اندازی مجدد:

bash
Copy code
aios-cli start --connect
yaml
Copy code
