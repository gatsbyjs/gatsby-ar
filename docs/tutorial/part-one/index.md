---
title: تعرف على لبنات Gatsby
typora-copy-images-to: ./
disableTableOfContents: true
---

في [**القسم السابق**](/tutorial/part-zero/)، قد قمت بتجهيز بيئية التطوير المحلية الخاصة بك عن طريق تثبت البرامج الضرورية وإنشاء أول موقع Gatsby خاص بك بإستخدام [**عدة البدء “hello world”**](https://github.com/gatsbyjs/gatsby-starter-hello-world). الآن غص عميقً في الشيفرة التي تم إنشاؤها بواسطة هذا العدة.

## إستخدم عدة البدء في Gatsby

في [**الدليل التطبيقي السابق**](/tutorial/part-zero/)، أنشأت موقعًا جديدًا استنادًا إلى عدة البدء “Hello World” باستخدام الأمر التالي:

```shell
gatsby new hello-world https://github.com/gatsbyjs/gatsby-starter-hello-world
```

عند إنشاء موقع Gatsby جديد، يمكنك استخدام بنية الأوامر التالية لإنشاء موقع جديد يستند إلى أي عدة بدء Gatsby موجودة:

```shell
gatsby new [SITE_DIRECTORY_NAME] [URL_OF_STARTER_GITHUB_REPO]
```

إذا حذفت عنوان URL من النهاية، سيتم تلقائيا إنشاء موقع Gatsby لك بإستخدام [**عدة البدء الإفتراضية**](https://github.com/gatsbyjs/gatsby-starter-default). بالنسبة إلى هذا القسم من الدليل التطبيقي، سنستمر بموقع “Hello World” الذي قمت بإنشائه بالفعل في الدليل التطبيقي السابق. من هنا يمكنك التعلم أكثر عن [تعديل عدة البدء الإفتراضية](/docs/modifying-a-starter)

### ✋ افتح الشيفرة

في محرر الشيفرة الخاص بك، إفتح الشيفرات المولدة لموقعك “Hello World” والقي نظرة على مختلف المجلدات والملفات الموجودة في المجلد ‘hello-world’. يجب أن يبدو مثل هذا:

![مشروع Hello World على محرر VS Code](01-hello-world-vscode.png)

_ملاحظة: مرة أخرى، المحرر الموضح هنا هو Visual Studio Code. إذا كنت تستخدم محررًا مختلفًا، فسيبدو مختلفًا بعض الشيء._

دعونا نلقي نظرة على الشيفرة الذي يشغل الصفحة الرئيسية.

> 💡 إذا أوقفت خادم التطوير بعد تشغيل `gatsby develop` في القسم السابق، إبدء تشغيله مرة أخرى الآن - حان الوقت لإجراء بعض التغييرات على موقع hello-world!

## التعرف على صفحات Gatsby

افتح المجلد `/src` في محرر الشيفرات خاصتك. في الداخل مجلد وحيد: `/pages`.

قم بفتح الملف `src/pages/index.js`. الشيفرة في هذا الملف تنشئ مكونًا يحتوي على div وحيدة ونص — مناسب “Hello world!”

### ✋ قم بإجراء تغييرات على صفحة “Hello World” الرئيسية

1. قم بتغيير النص “Hello World!” إلى “Hello Gatsby!” وأحفظ الملف. إذا كانت النوافذ الخاصة بك جنبًا إلى جنب، يمكنك أن ترى أن تغييرات الشيفرة والمحتوى تنعكس على الفور تقريبًا في المتصفح بعد حفظ الملف.

<video controls="controls" autoplay="true" loop="true">
  <source type="video/mp4" src="./02-demo-hot-reloading.mp4"></source>
  <p>المعذرة! متصفحك لا يدعم هذا الفيديو.</p>
</video>

> 💡 Gatsby تستخدم **إعادة التحميل الساخن** لتسريع عملية التطوير الخاصة بك. بشكل أساسي، عندما تقوم بتشغيل خادم تطوير Gatsby، ملفات موقع Gatsby تكون “متابعة” في الخلفية — في أي وقت تقوم فيه بحفظ ملف، سوف تحدث التغييرات الخاصة بك على الفور في المتصفح. لا تحتاج إلى تحديث الصفحة أو إعادة تشغيل خادم التطوير - ستظهر تغييراتك فقط.

2. يمكنك الآن جعل التغييرات أكثر وضوحًا. حاول إستبدال الشيفرة في الملف `src/pages/index.js` بالشيفرة المكتوبة في الاسفل وأحفظ مرة أخرى. سترى تغييرات على النص - سيكون لون النص أرجوانيًا وسيكون حجم الخط أكبر.

```jsx:title=src/pages/index.js
import React from "react"

export default () => (
  <div style={{ color: `purple`, fontSize: `72px` }}>مرحباً Gatsby!</div>
)
```

> 💡 سنغطي المزيد حول التنسيقات في Gatsby في [**الجزء الثاني**](/tutorial/part-two/) من الدليل التطبيقي.

3. إزالة حجم الخط من التنسيقات، تغيير نص “مرحباً Gatsby!” إالى رأس من المستوى الاول(h1)، وإضافة فقرة نصية أسفل الرأس.

```jsx:title=src/pages/index.js
import React from "react"

export default () => (
  {/* highlight-start */}
  <div style={{ color: `purple` }}>
    <h1>مرحباً Gatsby!</h1>
    <p>يا له من عالم.</p>
  {/* highlight-end */}
  </div>
)
```

![المزيد من التغييرات مع إعادة التحميل الساخنة](03-more-hot-reloading.png)

4.إضافة صورة. (في هذه الحالة، صورة عشوائية من Unsplash).

```jsx:title=src/pages/index.js
import React from "react"

export default () => (
  <div style={{ color: `purple` }}>
    <h1>مرحباً Gatsby!</h1>
    <p>يا له من عالم.</p>
    {/* highlight-next-line */}
    <img src="https://source.unsplash.com/random/400x200" alt="" />
  </div>
)
```

![إضافة صورة](04-add-image.png)

### انتظر… HTML في JavaScript؟

_إذا كنت معتادًا على React و JSX، فلا تتردد في تخطي هذا القسم._ إذا لم تكن ذو خبرة ولو بسيطة بإطار React، قد تتساءل عما يفعله HTML في دالة JavaScript. أو لماذا نستورد `react` في السطر الأول ولكن يبدو أنه لا يستخدمه في أي مكان. هذا الهجين من  “HTML-in-JS” هي عبارة عن صياغة ممتدة إلى JavaScript، مع React، تسمى JSX.يمكنك متابعة جنبا إلى جنب مع هذا الدليل التطبيقي دون خبرة سابقة مع React، ولكن إذا كنت مهتمًا، فإليك شرحاً موجزًا…

تامل المحتويات الأصلية لملف `src/pages/index.js`:

```jsx:title=src/pages/index.js
import React from "react"

export default () => <div>مرحباً بالعالم!</div>
```

في JavaScript الإعتيادية، ستبدوا أكثر مثل هذا:

```javascript:title=src/pages/index.js
import React from "react"

export default () => React.createElement("div", null, "مرحباً بالعالم!")
```

الآن يمكنك اكتشاف استخدام `'react'` import! لكن انتظر. أنت تكتب JSX، وليست شيفرة HTML و JavaScript اعتيادية.كيف يقرأ المتصفح ذلك؟ الإجابة الأقصر: لا يفعل ذالك. مواقع Gatsby يأتي مع الأدوات التي تم إعدادها بالفعل لتحويل شيفرة المصدر الخاصة بك إلى شيء يمكن المتصفحات تفسيره.

## بناء مع المكونات

تم إنشاء الصفحة الرئيسية التي كنت تجريها للتو من خلال تعريف مكون الصفحة. ما هو بالضبط “المكون”؟

بشكل عام، المكون هو لبنة بناء لموقعك؛ إنه جزء من الشيفرة قائمة بذاتها يصف قسمًا من واجهة المستخدم (user interface).

Gatsby بنيت إعتماداً على React. عندما نتحدث عن استخدام وتعريف **مكونات**، نحن نتحدث حقا عن **مكونات React** — أجزاء من الشيفرة (مكتوبة عادةً مع JSX) يمكنها قبول حقول الإدخال وإرجاع عناصر React التي تصف قسمًا من واجهة المستخدم.

أحد التحولات الذهنية الكبيرة التي تقوم بها عند البدء في البناء باستخدام المكونات (إذا كنت بالفعل مطورًا) هو أن CSS و HTML و JavaScript لديك الآن مرتبطون بإحكام ويعيشون غالبًا داخل نفس الملف.

في حين أن التغيير بسيط على ما يبدو، فإن هذا له آثار عميقة على طريقة تفكيرك في إنشاء مواقع الويب.

خذ مثال على إنشاء زر مخصص. في الماضي، قمت بإنشاء صنف CSS (ربما `.primary-button`) باستخدام التنسيقات المخصصة الخاصة بك، ثم استخدمها متى أردت تطبيق تلك التنسيقات. فمثلا:

```html
<button class="primary-button">انقر هنا</button>
```

في عالم المكونات، يمكنك إنشاء مكون `PrimaryButton` مع تنسيقات الزر الخاص بك واستخدامها في جميع أنحاء موقعك مثل:

<!-- prettier-ignore -->
```jsx
 <PrimaryButton>انقر هنا</PrimaryButton>
```

ستصبح المكونات اللبنات الأساسية لموقعك. بدلاً من أن يقتصر المتصفح على العناصر الأساسية التي يوفرها المتصفح، على سبيل المثال `<button />، يمكنك بسهولة إنشاء لبنات بناء جديدة تلبي احتياجات مشاريعك بأناقة.

### ✋ إستخدام مكونات الصفحة

أي مكون React معرف في `src/pages/*.js` سوف تصبح تلقائيا صفحة. دعونا نرى هذا بشكل عملي.

لديك بالفعل ملف `src/pages/index.js` الذي جاء مع قالب البدء “Hello World”. لنقم بإنشاء صفحة about.

1. إنشاء ملف جديد بالمسار `src/pages/about.js`، انسخ الشيفرة التالية في الملف الجديد واحفظه.

```jsx:title=src/pages/about.js
import React from "react"

export default () => (
  <div style={{ color: `teal` }}>
    <h1>عن Gatsby</h1>
    <p>هذا نجاح باهر. للغاية React.</p>
  </div>
)
```

2. انتقل إلى `http://localhost:8000/about/`

![صفحة عن الجديدة](05-about-page.png)

فقط عن طريق وضع مكون React في الملف `src/pages/about.js`، لديك الآن صفحة يمكن الوصول إليها في `/about`.

### ✋ إستخدام المكونات الفرعية

دعنا نقول ان الصفحة الرئيسية وصفحة عن كلاهما كبير للغاية وانت تعيد كتابة الكثير من الاشياء. يمكنك استخدام المكونات الفرعية لتقسيم واجهة المستخدم إلى قطع قابلة لإعادة الاستخدام. تحتوي كل من صفحتك على `<h1>` رؤوس - قم بإنشاء مكون سيصف `رأس`.

1. إنشاء مجلد جديد في `src/components` وملف داخله هذا المجلد يسمى `header.js`.
2. أضف الشيفرة التالية إلى الملف الجديد `src/components/header.js`.

```jsx:title=src/components/header.js
import React from "react"

export default () => <h1>هذا هو الرأس.</h1>
```

3. عدّل الملف `about.js` لاستيراد المكون `Header`. استبدال تمثيل `h1` بالمكون `<Header />`:

```jsx:title=src/pages/about.js
import React from "react"
import Header from "../components/header" // highlight-line

export default () => (
  <div style={{ color: `teal` }}>
    <Header /> {/* highlight-line */}
    <p>هذا نجاح باهر. للغاية React.</p>
  </div>
)
```

![إضافة مكون الرأس](06-header-component.png)

في المتصفح، نص الرأس “عن Gatsby” يجب ان يستبدل الان بالنص “هذا هو الرأس.” لكنك لا تريد صفحة “عن” لتقول “هذا هو الرأس.” بل تريدها ان تقول، “عن Gatsby”.

4. العودة الى `src/components/header.js` وإجراء التغيير التالي:

```jsx:title=src/components/header.js
import React from "react"

export default props => <h1>{props.headerText}</h1> {/* highlight-line */}
```

5. العودة الى `src/pages/about.js` وإجراء التغيير التالي:

```jsx:title=src/pages/about.js
import React from "react"
import Header from "../components/header"

export default () => (
  <div style={{ color: `teal` }}>
    <Header headerText="عن Gatsby" /> {/* highlight-line */}
    <p>هذا نجاح باهر. للغاية React.</p>
  </div>
)
```

![تمرير البيانات إلى الرأس](07-pass-data-header.png)

يجب أن تشاهد الآن نص رأس “عن Gatsby” مرة أخرى!

### ماذا تكون الخصائص “props”?

لقد قمت في وقت سابق بتعريف مكونات React على أنها أجزاء قابلة لإعادة الاستخدام من الشيفرة تصف واجهة المستخدم. لجعل هذه القطع القابلة لإعادة الاستخدام ديناميكية، يجب أن تكون قادرًا على تزويدها ببيانات مختلفة. يمكنك القيام بذلك مع إدخال يسمى الخصائص “props". الخصائص (appropriately enough) المقدمة لمكونات React.

في ملف `about.js` لقد مررت الخاصية `headerText` prop مع قيمة `"عن Gatsby"` إلى المكون الفرعي المستوردة `Header`:

```jsx:title=src/pages/about.js
<Header headerText="عن Gatsby" />
```

من خلال `header.js`، المكون رأس تتوقع الحصول على الخاصية `headerText` prop (لانك كتبتها للتوقع ذلك). حتى تتمكن من الوصول إليها مثل ذلك:

```jsx:title=src/components/header.js
<h1>{props.headerText}</h1>
```

> 💡 في JSX، يمكنك تضمين أي تعبير JavaScript عن طريق لفه بـواسطة `{}`. هذه هي الطريقة التي يمكنك الوصول إلى الخاصية `headerText` (أو “prop!”) من الكائن “props”.

إذا مررت خاصية أخرى prop للمكون `<Header />`، مثل...

```jsx:title=src/pages/about.js
<Header headerText="عن Gatsby" arbitraryPhrase="تعسفي" />
```

...ستكون قادرً على الوصول للخاصية `arbitraryPhrase` prop: `{props.arbitraryPhrase}`.

6. للتأكيد على كيفية جعل مكوناتك قابلة لإعادة الاستخدام، إضافة عنصر إضافي `<Header />` للصفحة عن، أضف الشيفرة التالية إلى ملف `src/pages/about.js` واحفظه.

```jsx:title=src/pages/about.js
import React from "react"
import Header from "../components/header"

export default () => (
  <div style={{ color: `teal` }}>
    <Header headerText="عن Gatsby" />
    <Header headerText="انه رائع جدا" /> {/* highlight-line */}
    <p>Such wow. Very React.</p>
  </div>
)
```

![رأس مكرر لإظهار قابلية إعادة الاستخدام](08-duplicate-header.png)

وهناك لديك؛ رأس ثانٍ - دون إعادة كتابة أي رمز - عن طريق تمرير بيانات مختلفة باستخدام الخصائص props.

### باستخدام مكونات النسق

مكونات النسق مخصصة لأقسام الموقع التي ترغب في مشاركتها عبر عدة صفحات. على سبيل المثال، سيكون لمواقع Gatsby عادةً مكون تخطيط مع رأس (header) وتذييل (footer) مشترك. تتضمن الأشياء الشائعة الأخرى المراد إضافتها إلى التخطيطات شريطًا جانبيًا و / أو قائمة التنقل.

ستكتشف مكونات التخطيط في [**الجزء الثالث**](/tutorial/part-three/).

## الربط بين الصفحات

ستحتاج غالبًا إلى الارتباط بين الصفحات - دعنا ننظر إلى التوجيه في موقع Gatsby.

### ✋ إستخدام المكون `<Link />`

1. افتح مكون صفحة الرئيسية (`src/pages/index.js`)، استورد المكون `<Link />` من Gatsby، أضف المكون `<Link />` فوق الرأس، وأعطة الخاصية `to` prop بالقيمة `"/contact/"` للمسار:

```jsx:title=src/pages/index.js
import React from "react"
import { Link } from "gatsby" // highlight-line
import Header from "../components/header"

export default () => (
  <div style={{ color: `purple` }}>
    <Link to="/contact/">التواصل</Link> {/* highlight-line */}
    <Header headerText="مرحباً Gatsby!" />
    <p>يا له من عالم.</p>
    <img src="https://source.unsplash.com/random/400x200" alt="" />
  </div>
)
```

عند النقر على رابط "التواصل" الجديد في الصفحة الرئيسية، يجب أن تشاهد ...

![صفحة Gatsby dev 404](09-dev-404.png)

...صفحة Gatsby development 404. لماذا? لأنك تحاول الارتباط بصفحة غير موجودة بعد.

2. الآن سيتعين عليك إنشاء مكون صفحة لصفحة "التواصل" على `src/pages/contact.js` وتربطها ايضاً بصفحة الرئيسية:

```jsx:title=src/pages/contact.js
import React from "react"
import { Link } from "gatsby"
import Header from "../components/header"

export default () => (
  <div style={{ color: `teal` }}>
    <Link to="/">الرئيسية</Link>
    <Header headerText="التواصل" />
    <p>أرسل لنا رسالة!</p>
  </div>
)
```

بعد أن تقوم بحفظ الملف، يجب أن ترى صفحة الاتصال وتكون قادرًا على الارتباط بينها وبين الصفحة الرئيسية.

<video controls="controls" loop="true">
  <source type="video/mp4" src="./10-linking-between-pages.mp4"></source>
  <p>المعذرة! متصفحك لا يدعم هذا الفيديو.</p>
</video>

المكون `<Link />` في Gatsby يقوم بعملية الربط بين الصفحات في موقعك. لربط صفحات خارجية لربط الصفحات الخارجية الغير مبنية في موقع Gatsby خاصتك. إستخدم وسم HTML الإعتيادي `<a>`.

## نشر موقع Gatsby

يعتبر Gatsby.js _مولد مواقع ساكنة_، بمعنى أنه لا توجد خوادم لإعدادها او قواعد بيانات معقده لنشرها. بدلاً عن ذلك، فالامر `build` في Gatsby ينتج مجلد يحتوي على ملفات HTML و JavaScript ساكنة والتي يمكن نشرها في خدمات إستضافة المواقع الساكنة.

جرب إستخدام [Surge](http://surge.sh/) لنشر موقعك الاول بإستخدام Gatsby. Surge يُعتبر واحد من العديد من "إستضافات المواقع الساكنة (static) " التي جعلت نشر مواقع Gatsby ممكنة.

إذا لم تكن قد قمت بتثبيت &amp; إعداد Surge، افتح نافذة طرفية جديدة وقم بتثبيت أداة سطر الأوامر الخاصة به:

```shell
npm install --global surge

# ثم قم بإنشاء حساب (مجاني) معهم
surge login
```

التالي، قم ببناء موقعك عن طريق تشغيل الأمر التالي في "الطرفية Terminal" من المجلد الرئيسي لموقعك (نصيحة: تأكد من تشغيل هذا الأمر في المجلد الرئيسي لموقعك، في هذه الحالة في مجلد hello-world، والذي يمكنك القيام به من خلال فتح علامة تبويب جديدة في نفس النافذة التي استخدمتها لتشغيل `gatsby develop`):

```shell
gatsby build
```

عملبة الإنشاء تستغرق 15-30 ثانية. بمجرد الانتهاء من الإنشاء، من المثير للاهتمام القيام بالقاء نظرة على الملفات التي اعدّها الامر `gatsby build` للنشر.

الق نظرة على قائمة الملفات التي تم إنشاؤها عن طرقة كتابة الامر في "الطرفية Terminal" في المجلد الرئيسي لموقعك، والذي سيسمح لك بمشاهدة ماهو بداخل المجلد `public`:

```shell
ls public
```

ثم أخيرًا نشر موقعك من خلال نشر الملفات التي تم إنشاؤها إلى surge.sh.

```shell
surge public/
```

بمجرد الانتهاء من تشغيل هذا، يجب أن تشاهد في جهاز الكمبيوتر الخاص بك شيء مثل:

> Note that you will have to press the `enter` key after you see the `domain: some-name.surge.sh` information on your command-line interface.

![لقطة شاشة لنشر موقع Gatsby مع Surge](surge-deployment.png)

قم بفتح رابط عنوان الويب في السطر السفلي (في هذه الحاله `lowly-pain.surge.sh`) وسترى موقعك المنشور حديثًا! عمل عظيم!

## ➡️ ماذا بعد؟

في هذا القسم أنت قد:

- تعلمت عُدَد البدء في Gatsby، و كيفية استخدامهم لإنشاء مشروع جديد
- تعلمت صيغة JSX
- تعلمت المكونات
- تعلمت مكونات صفحة Gatsby والمكونات الفرعية
- تعلمت “خصائص” React وإعادة إستخدام المكونات

والان، إنتقل الى [**إضافة التنسيقات لموقعك**](/tutorial/part-two/)!
