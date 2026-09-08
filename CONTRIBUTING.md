# تعليمات التطوير

## البيئة المطلوبة

- Node.js 14+ (اختياري)
- محرر نصوص (VS Code, Sublime, etc.)
- متصفح حديث
- Git

## التثبيت المحلي

```bash
# استنسخ المستودع
git clone https://github.com/Anis-HCH/IPTV-Verifier-iOS.git
cd IPTV-Verifier-iOS

# شغّل خادم محلي
python3 -m http.server 8000

# أو إذا كنت تستخدم Node.js
npx http-server

# افتح في المتصفح
http://localhost:8000
```

## هيكل المشروع

```
IPTV-Verifier-iOS/
├── index.html              # التطبيق الرئيسي (محسّن للـ iOS)
├── manifest.json           # ملف PWA
├── service-worker.js       # Service Worker للـ PWA
├── setup-pwa.js            # سكريبت تثبيت PWA
├── .htaccess               # إعدادات الخادم
├── README.md               # التوثيق الرئيسي
├── GUIDE.html              # دليل الاستخدام
└── CONTRIBUTING.md         # دليل المساهمة
```

## التعديلات والإضافات

### إضافة خادم proxy جديد

في `index.html`، ابحث عن دالة `fetchWithProxy`:

```javascript
if (proxyType === 'your-proxy') {
  finalUrl = `https://your-proxy-url.com/?url=${encodeURIComponent(targetUrl)}`;
}
```

### تعديل الألوان والتصميم

غيّر متغيرات CSS في `:root`:

```css
:root {
  --bg: #090d16;           /* لون الخلفية الرئيسي */
  --accent-blue: #3b82f6;  /* اللون الأساسي */
  /* ... */
}
```

### إضافة لغات جديدة

1. أضف ملف HTML جديد للغة (مثل `guide-en.html`)
2. ترجم النصوص
3. أضف رابط في الصفحة الرئيسية

## اختبار على iOS

### على Safari
1. افتح الرابط: `http://192.168.X.X:8000`
2. استخدم أدوات المطور (Remote Debugging)

### تثبيت PWA
1. اضغط على Share
2. اختر "Add to Home Screen"
3. أكمل العملية

## الأداء والتحسينات

### نصائح للتحسين:
- استخدم compression للملفات
- قلل حجم الصور والرموز
- استخدم caching الفعال
- حسّن JavaScript للأجهزة الضعيفة

## الأمان

- لا تُخزّن كلمات المرور على الخادم
- استخدم HTTPS فقط في الإنتاج
- تحقق من inputs المستخدم
- لا تسجّل البيانات الحساسة

## نشر على الويب

### على GitHub Pages
```bash
git push origin main
# ستكون متاحة على: https://username.github.io/IPTV-Verifier-iOS
```

### على خادم خاص
```bash
# انسخ الملفات إلى الخادم
scp -r * user@server:/var/www/iptv-verifier/
```

### على Vercel أو Netlify
1. ربط الـ GitHub repo
2. اختر الفرع الرئيسي
3. انشر

## الترخيص

هذا المشروع مفتوح المصدر ومتاح للاستخدام الحر.

## الدعم والمساعدة

- افتح Issue للمشاكل
- أرسل PR للإضافات
- تواصل عبر GitHub
