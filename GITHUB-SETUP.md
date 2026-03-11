# 📤 دليل دفع المشروع على GitHub

## خطوة 1: إنشاء مستودع على GitHub

1. اذهب إلى [github.com](https://github.com)
2. سجّل الدخول (أو أنشئ حساب جديد)
3. اضغط على **+** (الزاوية العلوية اليمنى)
4. اختر **New repository**
5. أدخل التفاصيل:
   - **Repository name**: `king-ai`
   - **Description**: `The King AI - Arabic AI Assistant PWA that works offline`
   - **Public** ✅ (لكي يراه الجميع)
   - **Initialize this repository with**:
     - ❌ لا تختر أي خيار (المستودع لديك بالفعل commits)

6. اضغط **Create repository**

---

## خطوة 2: ربط المستودع المحلي مع GitHub

بعد إنشاء المستودع، ستظهر لك التعليمات. اتبع هذا:

### أ. إضافة remote

```bash
# انتقل إلى مجلد المشروع
cd king-ai

# أضف المستودع البعيد (استبدل USERNAME بـ GitHub username)
git remote add origin https://github.com/USERNAME/king-ai.git

# تحقق من الاتصال
git remote -v
```

يجب أن ترى:
```
origin  https://github.com/USERNAME/king-ai.git (fetch)
origin  https://github.com/USERNAME/king-ai.git (push)
```

### ب. إعادة تسمية الفرع (إذا لزم الأمر)

```bash
# GitHub الآن يفضل 'main' بدلاً من 'master'
git branch -M main
```

### ج. دفع الكود

```bash
# ادفع كل الـ commits والفروع
git push -u origin main
```

ستُطلب منك بيانات المصادقة:

**للمصادقة استخدم أحد الطرق:**

#### الطريقة 1: Personal Access Token (موصى به)

1. اذهب إلى [Settings > Developer settings > Personal access tokens](https://github.com/settings/tokens)
2. اضغط **Generate new token**
3. امنح الأذونات:
   - ✅ `repo` (كامل التحكم في المستودعات)
   - ✅ `workflow` (للـ GitHub Actions)
4. انسخ الـ token
5. عند الطلب:
   - **Username**: اسم GitHub
   - **Password**: ألصق الـ token

#### الطريقة 2: SSH Key (متقدمة)

إذا كان لديك SSH key:

```bash
# استخدم SSH بدلاً من HTTPS
git remote set-url origin git@github.com:USERNAME/king-ai.git
git push -u origin main
```

---

## خطوة 3: التحقق من النجاح

1. اذهب إلى `https://github.com/USERNAME/king-ai`
2. يجب أن ترى جميع الملفات والـ commits
3. اضغط على **Commits** لترى سجل التغييرات

---

## خطوة 4: تفعيل GitHub Pages (اختياري - للاستضافة المجانية)

إذا أردت استضافة التطبيق مجاناً على GitHub Pages:

1. اذهب إلى **Settings** > **Pages**
2. تحت **Build and deployment**:
   - **Source**: اختر `GitHub Actions`
3. يجب أن تظهر Action و Deploy workflow
4. بعد دقائق، سترى رابط مثل:
   ```
   Your site is live at https://USERNAME.github.io/king-ai
   ```

---

## خطوة 5: الـ Commits اللاحقة

بعد إجراء تعديلات:

```bash
# 1. اعرض التغييرات
git status

# 2. أضف الملفات المتغيرة
git add .

# 3. اعمل commit
git commit -m "Fix: وصف التعديل هنا"

# 4. ادفع إلى GitHub
git push
```

---

## أوامر مفيدة

```bash
# عرض حالة المستودع
git status

# عرض سجل الـ commits
git log --oneline

# عرض الفروع
git branch -a

# إرجاع آخر تعديلات (خطر!)
git reset --hard origin/main

# حذف ملف من التتبع
git rm --cached filename
```

---

## حل المشاكل الشائعة

### ❌ خطأ "fatal: 'origin' does not appear to be a 'git' repository"

```bash
# تأكد من وجود .git folder
ls -la | grep .git

# إذا لم توجد:
git init
git add .
git commit -m "Initial commit"
git remote add origin https://...
```

---

### ❌ خطأ "Please make sure you have the correct access rights"

**الحل**:
- تحقق من اسم المستودع
- تحقق من الأذونات في GitHub
- جرّب Personal Access Token

---

### ❌ rejected: updates were rejected

```bash
# سحب آخر التغييرات أولاً
git pull origin main --rebase

# ثم ادفع
git push origin main
```

---

## ✅ قائمة التحقق

- [ ] تم إنشاء مستودع على GitHub
- [ ] تم إضافة `origin` remote
- [ ] تم دفع جميع الملفات
- [ ] تم رؤية الملفات على GitHub
- [ ] تم تفعيل GitHub Pages (اختياري)
- [ ] تم فحص Actions و Deploy workflow

---

## 🎉 مبروك!

مشروعك الآن على الإنترنت! يمكنك:

- 📤 **مشاركة الرابط** مع الآخرين
- 🤝 **قبول مساهمات** من الآخرين
- 📊 **تتبع الأخطاء** عبر Issues
- 🚀 **النشر التلقائي** عبر GitHub Actions
- 💬 **فتح Discussion** مع المجتمع

---

## الخطوات التالية

1. **تحديث README.md**:
   - أضف صورة لقطة الشاشة
   - أضف شروط الاستخدام
   - أضف الشكر للمساهمين

2. **إضافة Topics**:
   - اذهب إلى Settings
   - أضف tags مثل: `ai`, `chatbot`, `arabic`, `pwa`

3. **تفعيل الميزات**:
   - Enable Issues
   - Enable Discussions
   - Enable Projects

4. **البدء في التطوير**:
   ```bash
   # إنشاء فرع جديد
   git checkout -b feature/amazing-feature
   
   # تطوير الميزة...
   
   # Push والفتح Pull Request
   git push origin feature/amazing-feature
   ```

---

للمزيد من المعلومات: [GitHub Docs](https://docs.github.com)
