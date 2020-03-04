---
title: بداية سريعة
---

هذه البداية السريعة موجهة للمطورين الذين لديهم مستوى متوسط و متقدم. للحصول على مقدمة ألطف إلى Gatsby ، [توجه إلى الدليل التطبيقي الخاص بنا](/tutorial/)!

## استخدم Gatsby CLI

<EggheadEmbed
  lessonLink="https://egghead.io/lessons/gatsby-quick-start-with-gatsby-create-develop-and-build-gatsby-sites-from-the-command-line"
  lessonTitle="Quick Start with Gatsby: Create, Develop, and Build Gatsby Sites From the Command Line"
/>

**ملاحظة**: يستخدم هذا الفيديو `npx` ، وهي أداة لتنفيذ حزمة npm دون تثبيتها أولاً على جهازك. إن تشغيل الأمر `npx gatsby new` هو نفسه تشغيل `gatsby new` بعد تثبيت gatsby-cli على جهاز الكمبيوتر الخاص بك.

### تثبيت Gatsby CLI

```shell
npm install -g gatsby-cli
```

> يقوم الأمر أعلاه بتثبيت Gatsby CLI على جهازك.

### انشاء موقع جديد

```shell
gatsby new gatsby-site
```

### تغيير الدلائل إلى مجلد الموقع

```shell
cd gatsby-site
```

### بدء خادم التطوير

```shell
gatsby develop
```

سيبدأ Gatsby في بيئة تطوير سريعة التحميل (hot-reloading) يمكن الوصول إليها افتراضيًا على `http://localhost:8000`.

حاول تحرير صفحات JavaScript في `src / pages`. سيتم حفظ التغييرات بشكل مباشر في المتصفح.

### إنشاء بناء الإنتاج

```shell
gatsby build
```

ستعمل Gatsby على إنشاء إنتاج مُحسّن لموقعك ، من خلال إنشاء حزم HTML ثابتة وحزم شفرة JavaScript.

### خدمة إنتاج البناء محليا

```shell
gatsby serve
```

يبدأ Gatsby خادم HTML محلي لاختبار موقعك المدمج. تذكر أن تقوم بعمل تنفيذ `gatsby build` قبل استخدام هذا الأمر.

### مستندات الوصول لأوامر CLI

للاطلاع على مستندات لأوامر CLI بشكل مفصل ، قم بتشغيل `gatsby --help` في الجهاز.

بالنسبة لبعض الأوامر المحددة ، قم بتشغيل `gatsby COMMAND_NAME --help` على سبيل المثال `gatsby new --help`.

لمزيد من المعلومات حول Gatsby CLI ، تفضل بزيارة قسم [مرجع CLI](/docs/gatsby-cli/) في المستندات.
