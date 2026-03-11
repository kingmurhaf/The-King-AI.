# 🚀 دليل الإعداد المحلي الشامل

## المتطلبات الأساسية

قبل البدء، تأكد من وجود:

- **Node.js** (الإصدار 16 أو أعلى)
- **npm** أو **yarn** أو **pnpm**
- **متصفح حديث** (Chrome 90+, Firefox 88+, Safari 14+, Edge 90+)

### التحقق من الإصدارات

```bash
node --version  # يجب أن يكون >= v16.0.0
npm --version   # يجب أن يكون >= 7.0.0
```

### تثبيت Node.js

اذهب إلى [nodejs.org](https://nodejs.org) واختر الإصدار LTS (Long Term Support)

---

## خطوات الإعداد

### 1️⃣ استنساخ المستودع

```bash
# استخدم HTTPS
git clone https://github.com/yourusername/king-ai.git

# أو استخدم SSH (إذا كنت قد أعددت مفاتيح SSH)
git clone git@github.com:yourusername/king-ai.git

# انتقل إلى المجلد
cd king-ai
```

### 2️⃣ تثبيت المتطلبات

```bash
npm install
```

أو إذا كنت تستخدم yarn:

```bash
yarn install
```

أو مع pnpm:

```bash
pnpm install
```

**وقت التثبيت**: حوالي 2-5 دقائق (يعتمد على سرعة الإنترنت)

### 3️⃣ بدء خادم التطوير

```bash
npm run dev
```

ستشاهد شيء مثل هذا:

```
  VITE v6.0.5  ready in 245 ms

  ➜  Local:   http://localhost:5173/
  ➜  press h to show help
```

### 4️⃣ فتح التطبيق

افتح متصفحك واذهب إلى: **http://localhost:5173**

---

## الاستخدام في بيئة التطوير

### أوامر مفيدة

```bash
# بدء خادم التطوير
npm run dev

# بناء للإنتاج
npm run build

# معاينة الإصدار الإنتاجي محلياً
npm run preview

# إيقاف الخادم
# اضغط Ctrl+C في Terminal
```

### Hot Module Replacement (HMR)

التطبيق يدعم HMR، مما يعني أن التغييرات ستظهر فوراً دون إعادة تحميل المتصفح!

---

## إضافة مفاتيح API (اختياري)

### 1. إنشاء ملف `.env.local`

```bash
cp .env.example .env.local
```

### 2. ملء المفاتيح

**لـ Claude (Anthropic)**:
1. اذهب إلى [console.anthropic.com](https://console.anthropic.com)
2. أنشئ حساب أو سجّل الدخول
3. انقر على "API Keys" أو "Keys"
4. انسخ المفتاح
5. ألصقه في `.env.local`:

```env
VITE_CLAUDE_KEY=sk-ant-xxxxxxxxxxxxx
```

**لـ Gemini (Google)**:
1. اذهب إلى [ai.google.dev](https://ai.google.dev)
2. اضغط على "Get API Key"
3. أنشئ مشروع جديد
4. انسخ المفتاح
5. ألصقه في `.env.local`:

```env
VITE_GEMINI_KEY=AIzaxxxxxxxxxxxxx
```

### 3. إعادة تشغيل الخادم

```bash
# إيقاف الخادم (Ctrl+C)
# ثم أعد تشغيله
npm run dev
```

---

## استكشاف الأخطاء

### ✅ المشاكل الشائعة والحلول

#### المشكلة: "command not found: npm"

**الحل**: تأكد من تثبيت Node.js بشكل صحيح

```bash
# تحقق من المسار
which node
which npm

# أو أعد تثبيت Node.js
```

---

#### المشكلة: "port 5173 is already in use"

**الحل**: غيّر المنفذ

```bash
npm run dev -- --port 3000
```

---

#### المشكلة: الملفات لا تُحدّث تلقائياً

**الحل**: تأكد من أن `watch` مُفعّل (يجب أن يكون افتراضياً)

```bash
# أو جرّب:
npm run dev -- --force
```

---

#### المشكلة: خطأ "node_modules is corrupted"

**الحل**: حذف واعادة تثبيت

```bash
rm -rf node_modules package-lock.json
npm install
```

---

## البناء للإنتاج

عندما تكون جاهزاً لنشر التطبيق:

### 1. بناء التطبيق

```bash
npm run build
```

سيتم إنشاء مجلد `dist/` يحتوي على ملفات الإنتاج المُحسّنة

### 2. اختبار الإصدار المبني

```bash
npm run preview
```

افتح `http://localhost:4173` للمعاينة

### 3. النشر على GitHub Pages (اختياري)

إذا كنت تريد استضافة مجاني:

```bash
# تأكد من أن مستودعك عام (public)
# تفعّل GitHub Pages من الإعدادات
# اختر `gh-pages` أو `main` كمصدر
# ستجد التطبيق على: https://yourusername.github.io/king-ai
```

---

## هيكل ملفات التطوير

```
king-ai/
├── src/
│   ├── App.jsx               ← المكون الرئيسي
│   ├── main.jsx              ← نقطة الدخول
│   ├── components/           ← مكونات React
│   ├── engine/               ← منطق البرنامج
│   ├── context/              ← إدارة الحالة
│   ├── hooks/                ← React Hooks
│   └── styles/               ← التنسيقات
├── public/                   ← الملفات الثابتة
├── dist/                     ← الإخراج المبني (بعد npm run build)
├── node_modules/             ← الحزم (لا تلمسها يدوياً)
├── .env.local                ← متغيرات البيئة (انشئها أنت)
├── .env.example              ← مثال من متغيرات البيئة
├── vite.config.js            ← إعدادات Vite
├── package.json              ← الحزم والمعلومات
└── README.md                 ← التوثيق
```

---

## نصائح إضافية

### 📱 اختبار على الهاتف

1. اعرف IP عنوان جهازك:

```bash
# على Mac/Linux
ifconfig | grep "inet "

# على Windows
ipconfig
```

2. افتح على جهازك الآخر:
```
http://YOUR_IP:5173
```

### 🎨 أدوات المطور

- اضغط `F12` لفتح أدوات المتصفح
- استخدم React DevTools (إضافة متصفح)
- استخدم Vue DevTools (إذا لزم الأمر)

### 📚 مراجع مفيدة

- [Vite Docs](https://vitejs.dev/guide/)
- [React Docs](https://react.dev)
- [MDN Web Docs](https://developer.mozilla.org)
- [ES6+ Cheatsheet](https://cheatsheetbase.com/cheatsheet/es6)

---

## الحصول على المساعدة

إذا واجهت مشكلة:

1. **تحقق من الـ Terminal** - ابحث عن رسائل الخطأ
2. **انظر إلى [Issues](https://github.com/yourusername/king-ai/issues)** - ربما حل شخص آخر المشكلة
3. **أنشئ Issue جديد** - قدّم:
   - وصف المشكلة
   - الخطوات لإعادة الحدوث
   - نسخة Node.js والمتصفح
   - رسالة الخطأ كاملة

4. **انضم إلى Discussion** - [GitHub Discussions](https://github.com/yourusername/king-ai/discussions)

---

## 🎉 مبروك!

أنت الآن جاهز لتطوير The King AI محلياً!

**خطواتك التالية**:
- ✅ استكشف الكود
- ✅ اقرأ التعليقات
- ✅ جرّب التعديلات الصغيرة
- ✅ شارك ملاحظاتك

Happy Coding! 🚀
