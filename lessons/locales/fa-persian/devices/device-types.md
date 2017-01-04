# نوع دستگاه‌ها

## محتوای درس

قبل از صبحت در مورد این که دستگاه‌ها چطور مدیریت می‌شوند‌، بیایید نگاهی به تعدادی از آن‌ها بیاندازیم:


```
$ ls -l /dev
brw-rw----   1 root disk      8,   0 Dec 20 20:13 sda
crw-rw-rw-   1 root root      1,   3 Dec 20 20:13 null
srw-rw-rw-   1 root root           0 Dec 20 20:13 log
prw-r--r--   1 root root           0 Dec 20 20:13 fdata
```

هر ستون از چپ به راست به نشانگر مقادیر زیر است:

- اجازه‌های دسترسی
- مالک
- گروه
- شماره دستگاه اصلی
- شماره دستگاه فرعی
- زمان
- نام دستگاه

به خاطر دارید که می‌توانستیم با استفاده از بیت اول هر خط از خروجی دستور ls، به نوع آن فایل پی ببریم؟ device file‌ها به صورت زیر نشانه‌گذاری می‌شوند:

- ‏c - کاراکتر
- b - بلاک
- p - پایپ
- s - سوکت

### دستگاه کاراکتر

این نوع دستگاه‌ها قابلیت انتقال داده به صورت یک کاراکتر در لحظه را دارند. تعداد
زیادی از شبه دستگاه‌ها (از جمله ‎/dev/null) از نوع دستگاه کاراکتر‌اند. این دستگاه‌ها
به صورت فیزیکی به سیستم متصل نشده‌اند، ولی به سیستم عامل قدرت عمل بیشتری می‌دهند.

### دستگاه بلاک

این نوع دستگاه‌ها نیز قابلیت انتقال داده دارند‌، ولی این کار را به صورت یک بلاک
بزرگ از داده به اندازهٔ ثابت انجام می‌دهند. عموما دستگاه‌هایی که از داده‌ها استفاده
می‌کنند‌، به صورت دستگاه بلاک نشانه گذاری می‌شوند. دستگاه‌هایی چون دیسک‌های سخت و
سیستم فایل‌ها از این دست‌اند.

### دستگاه پایپ

دستگاه‌های پایپ (لوله) امکان ارتباط بین چند پروسه با یکدیگر را فراهم می‌کنند. این
نوع دستگاه‌ها از بسیاری جهات شبیه به دستگاه‌های کاراکتر عمل می‌کنند، اما به جای
ارسال خروجی به یک دستگاه‌، آن را به پروسه‌ای دیگر هدایت می‌کنند.

### دستگاه سوکت

دستگاه‌های سوکت‌، همچون دستگاه‌های پایپ ارتباط بین پروسه‌ها را تسهیل می‌کنند‌. ولی
امکان ارتباط همزمان با تعداد زیادی از پروسه‌های مختلف را دارند.

### شناسایی دستگاه‌هایی

دستگاه‌ها با استفاده از دو عدد شناسایی می‌شوند. **شماره دستگاه اصلی** و **شماره
دستگاه فرعی**. در نمونه خروجی دستور ls بالا‌،‌می‌توانید این اعداد را مشاهده کنید که
با یک کاما از هم جدا شده‌اند. برای نمونه بیایید فرض کنیم یک دستگاه با شماره‌های
**8, 0** نشانه گذاری شده است:

شماره دستگاه اصلی‌، نشان‌گر راه‌انداز دستگاهی است که استفاده شده است. مثلا در این‌جا
8، که عموما به عنوان شماره دستگاه اصلی دستگاه‌های بلاک sd استفاده می‌شود. شماره
دستگاه فرعی‌، به کرنل نشان می‌دهد که دستگاه حاضر در کجای کلاس راه‌انداز حاضر قرار
دارد. در نمونهٔ فعلی‌، عدد 0 نشان می‌دهد که دستگاه حاضر‌، اولین دستگاه این کلاس راه‌انداز است.

## تمرینات

به دایرکتوری ‎/dev سیستم خود نگاهی بیاندازید و ببینید چه نوع دستگاه‌هایی در آن خواهید یافت.

## سوال آزمون

علامت اختصاصی دستگاه‌های کاراکتر در خروجی دستور `ls -l` چیست؟

## پاسخ آزمون

c