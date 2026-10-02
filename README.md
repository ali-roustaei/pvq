# آزمون ارزش‌های شخصی شوارتز (PVQ)

یک اپلیکیشن تحت وب برای انجام **آزمون ارزش‌های شخصی شوارتز (Schwartz's Personal Values Questionnaire - PVQ)** و مشاهده نتایج بر اساس نظریه ارزش‌های بنیادی شوارتز.

## 🌐 دسترسی به اپلیکیشن

**[مشاهده و انجام آزمون PVQ](https://ali-roustaei.github.io/pvq/)**

> برای استفاده از آزمون نیازی به نصب نرم‌افزار نیست و می‌توانید مستقیماً از طریق مرورگر وارد شوید.

## 📋 درباره آزمون

پرسشنامه ارزش‌های شخصی شوارتز (PVQ) ابزاری برای بررسی ارزش‌هایی است که در تصمیم‌گیری‌ها، انتخاب‌ها و رفتارهای فرد نقش دارند.

این اپلیکیشن با ارائه مجموعه‌ای از پرسش‌ها، پاسخ‌های کاربر را دریافت کرده و در پایان تصویری از ارزش‌های فردی او ارائه می‌دهد.

ارزش‌های مورد بررسی شامل مواردی مانند:

* **خودمختاری (Self-Direction)**
* **تحریک‌پذیری و هیجان‌جویی (Stimulation)**
* **لذت‌گرایی (Hedonism)**
* **موفقیت (Achievement)**
* **قدرت (Power)**
* **امنیت (Security)**
* **همنوایی (Conformity)**
* **سنت (Tradition)**
* **خیرخواهی (Benevolence)**
* **جهان‌گرایی (Universalism)**

## ✨ ویژگی‌ها

* رابط کاربری ساده و واکنش‌گرا
* مناسب برای استفاده در موبایل و دسکتاپ
* نمایش مرحله‌به‌مرحله پرسش‌ها
* محاسبه و نمایش نتایج آزمون
* رابط کاربری فارسی و راست‌به‌چپ (RTL)
* استفاده از فونت **Vazirmatn**
* طراحی شده با کامپوننت‌های **Flowbite Svelte**

## 🛠️ تکنولوژی‌ها

این پروژه با استفاده از تکنولوژی‌های زیر ساخته شده است:

* [Svelte 5](https://svelte.dev/)
* [SvelteKit](https://svelte.dev/docs/kit)
* [TypeScript](https://www.typescriptlang.org/)
* [Tailwind CSS](https://tailwindcss.com/)
* [Flowbite Svelte](https://flowbite-svelte.com/)
* [Vite](https://vite.dev/)

## 🚀 اجرای پروژه در محیط توسعه

ابتدا repository را clone کنید:

```bash
git clone https://github.com/ali-roustaei/pvq.git
cd pvq
```

سپس وابستگی‌ها را نصب کنید:

```bash
npm install
```

برای اجرای پروژه در محیط توسعه:

```bash
npm run dev
```

پس از اجرا، آدرس نمایش‌داده‌شده توسط SvelteKit را در مرورگر باز کنید.

## 📦 ساخت نسخه Production

برای ساخت نسخه production:

```bash
npm run build
```

برای مشاهده نسخه ساخته‌شده به‌صورت محلی:

```bash
npm run preview
```

## 🌍 انتشار روی GitHub Pages

این پروژه برای انتشار به‌صورت یک سایت استاتیک روی **GitHub Pages** تنظیم شده است.

آدرس نهایی پروژه:

**https://ali-roustaei.github.io/pvq/**

مسیر پایه پروژه نیز برای repository با نام `pvq` تنظیم شده است:

```text
/pvq
```

## 📁 ساختار کلی پروژه

```text
pvq/
├── src/
│   ├── lib/
│   └── routes/
├── static/
├── .github/
│   └── workflows/
├── package.json
├── svelte.config.js
├── vite.config.ts
└── README.md
```

## 📄 مجوز

این پروژه یک پروژه شخصی و آموزشی است.

---

**ساخته‌شده توسط [Ali Roustaei](https://github.com/ali-roustaei)**
