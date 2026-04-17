# GitHub Pages-ready clean URLs package

هذا المجلد جاهز للرفع مباشرةً إلى GitHub Pages بدل النسخة الحالية.

## ما الذي تم تغييره

- تم تحويل الصفحات الداخلية من ملفات root مثل `about.html` إلى صفحات نظيفة داخل مجلدات مثل `about/index.html`.
- تم تحديث الروابط الداخلية داخل الصفحات إلى النسخة النظيفة:
  - `/about/`
  - `/contact/`
  - `/eye-photos/`
  - `/packages/`
  - `/pigeon-photos/`
  - `/video/`
- تم تحويل مراجع الصور والفيديو والملفات إلى مسارات تبدأ من الجذر مثل `/assets/...` حتى تعمل من داخل المجلدات.
- تم الإبقاء على الصفحات القديمة `*.html` كصفحات تحويل فورية إلى الروابط النظيفة.
- تمت إضافة `.nojekyll` حتى يتعامل GitHub Pages مع الملفات كـ static files مباشرة.

## مهم جدًا

هذه النسخة مناسبة للرفع على **GitHub Pages فقط**.

لكن لأن GitHub Pages استضافة static من الريبو، فالتحويلات من `*.html` هنا هي **تحويلات داخل المتصفح** وليست **HTTP 301 server-side**.

إذا كنت تريد 301 حقيقي من `about.html` إلى `/about/` فالحل الصحيح يظل Cloudflare أو أي edge/CDN redirects.

## خطوات الرفع

1. فك الضغط عن الملف.
2. افتح المستودع الذي ينشر GitHub Pages.
3. احذف الملفات القديمة من جذر الموقع أو استبدلها بهذه النسخة.
4. ارفع **كل محتويات هذا المجلد** إلى جذر الريبو.
5. تأكد أن ملف `CNAME` موجود إذا كنت تستخدم دومين مخصص.
6. في GitHub:
   - **Settings**
   - **Pages**
   - اختر الفرع الصحيح (عادة `main`) والمجلد الصحيح (`/root` أو `/docs` حسب إعدادك)
7. انتظر حتى يعيد GitHub Pages النشر.

## المسارات الجديدة

- `/` ← الصفحة الرئيسية
- `/about/`
- `/contact/`
- `/eye-photos/`
- `/packages/`
- `/pigeon-photos/`
- `/video/`

## سلوك الروابط القديمة

- `/about.html` → تحويل فوري إلى `/about/`
- `/contact.html` → تحويل فوري إلى `/contact/`
- `/eye-photos.html` → تحويل فوري إلى `/eye-photos/`
- `/packages.html` → تحويل فوري إلى `/packages/`
- `/pigeon-photos.html` → تحويل فوري إلى `/pigeon-photos/`
- `/video.html` → تحويل فوري إلى `/video/`
- `/index.html` → تحويل فوري إلى `/`

## ملاحظات فنية

- في المتصفحات العادية سيتم الحفاظ على `?query=` و `#fragment` أثناء التحويل لأن التحويل يتم عبر JavaScript.
- fallback الخاص بـ `meta refresh` لا يضمن الحفاظ على query/hash إذا كانت JavaScript معطلة.
- الأصول مثل الصور والفيديو و `site.webmanifest` و `favicon` لم يتم نقلها من أماكنها، فقط تم تعديل المسارات المرجعية داخل الصفحات.

## اختبار سريع بعد النشر

افتح هذه المسارات وتأكد:

- `/` يعمل
- `/about/` يعمل
- `/contact/` يعمل
- `/eye-photos/` يعمل
- `/packages/` يعمل
- `/pigeon-photos/` يعمل
- `/video/` يعمل
- `/about.html` يحول إلى `/about/`
- `/video.html?x=1#t` يحول إلى `/video/?x=1#t`
- `/assets/logo_legacy.webp` يعمل بدون تحويل
- `/assets/video.mp4` يعمل بدون تحويل
- `/site.webmanifest` يعمل بدون تحويل
- `/favicon.ico` يعمل بدون تحويل

## الملفات المضافة/المهمة

- `.nojekyll`
- `README.md`
- مجلدات الصفحات النظيفة (`about/`, `contact/`, ...)
- صفحات التحويل القديمة (`about.html`, `contact.html`, ...)
