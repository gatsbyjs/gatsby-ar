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

<<<<<<< HEAD
### تثبيت Gatsby CLI.
=======
### Install the Gatsby CLI
>>>>>>> 90932a06db2e297cf416552b84e48b4b82e56fbc

```shell
npm install -g gatsby-cli
```

<<<<<<< HEAD
### انشاء موقع جديد.
=======
> The above command installs Gatsby CLI globally on your machine.

### Create a new site
>>>>>>> 90932a06db2e297cf416552b84e48b4b82e56fbc

```shell
gatsby new gatsby-site
```

<<<<<<< HEAD
### تغيير الدلائل إلى مجلد الموقع.
=======
### Change directories into site folder
>>>>>>> 90932a06db2e297cf416552b84e48b4b82e56fbc

```shell
cd gatsby-site
```

<<<<<<< HEAD
### بدء خادم التطوير.
=======
### Start development server
>>>>>>> 90932a06db2e297cf416552b84e48b4b82e56fbc

```shell
gatsby develop
```

<<<<<<< HEAD
سيبدأ Gatsby في بيئة تطوير سريعة التحميل (hot-reloading) يمكن الوصول إليها افتراضيًا على `localhost:8000`.
=======
Gatsby will start a hot-reloading development environment accessible by default at `http://localhost:8000`.
>>>>>>> 90932a06db2e297cf416552b84e48b4b82e56fbc

حاول تحرير صفحات JavaScript في `src / pages`. سيتم حفظ التغييرات بشكل مباشر في المتصفح.

<<<<<<< HEAD
### إنشاء بناء الإنتاج.
=======
### Create a production build
>>>>>>> 90932a06db2e297cf416552b84e48b4b82e56fbc

```shell
gatsby build
```

ستعمل Gatsby على إنشاء إنتاج مُحسّن لموقعك ، من خلال إنشاء حزم HTML ثابتة وحزم شفرة JavaScript.

<<<<<<< HEAD
### خدمة إنتاج البناء محليا.
=======
### Serve the production build locally
>>>>>>> 90932a06db2e297cf416552b84e48b4b82e56fbc

```shell
gatsby serve
```

يبدأ Gatsby خادم HTML محلي لاختبار موقعك المدمج. تذكر أن تقوم بعمل تنفيذ `gatsby build` قبل استخدام هذا الأمر.

### مستندات الوصول لأوامر CLI

للاطلاع على مستندات لأوامر CLI بشكل مفصل ، قم بتشغيل `gatsby --help` في الجهاز.

بالنسبة لبعض الأوامر المحددة ، قم بتشغيل `gatsby COMMAND_NAME --help` على سبيل المثال `gatsby new --help`.

لمزيد من المعلومات حول Gatsby CLI ، تفضل بزيارة قسم [مرجع CLI](/docs/gatsby-cli/) في المستندات.
