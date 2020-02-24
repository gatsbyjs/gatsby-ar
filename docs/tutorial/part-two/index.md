---
title: مقدمة في التنسيق في Gatsby
typora-copy-images-to: ./
disableTableOfContents: true
---


مرحبًا بك في الجزء الثاني من الدليل Gatsby التطبيقي!

## ماذا يوجد في هذا دليل التطبيقي؟

في هذا الجزء ، ستستكشف خيارات تنسيق مواقع الويب Gatsby وتعمق في استخدام مكونات React لبناء المواقع.

## باستخدام التنسيق الشامل

كل موقع لديه نوع من التنسيق الشامل . يتضمن ذلك أشياء مثل الطباعة وألوان الخلفية الخاصة بالموقع. تضفي هذه التناسيق طابعًا عامًا على الموقع - تمامًا مثل لون وملمس الحائط الذي يحدد المظهر العام للغرفة.

### إنشاء تناسيق شاملة مع ملفات CSS القياسية

إحدى أكثر الطرق المباشرة لإضافة تناسيق شاملة إلى موقع ما هي استخدام ورقة تناسيق `.css` شاملة .

#### ✋ إنشاء موقع Gatsby جديد

ابدأ بإنشاء موقع Gatsby جديد. قد يكون من الأفضل (خصوصًا إذا كنت جديدًا في سطر الأوامر) إغلاق النوافذ الطرفية التي استخدمتها لـ [الجزء الأول](/tutorial/part-one/) وبدء جلسة طرفية جديدة للجزء الثاني.

افتح نافذة طرفية جديدة ، وقم بإنشاء موقع Gatsby جديد "hello world" ، وابدأ خادوم التطوير:

```shell
gatsby new tutorial-part-two https://github.com/gatsbyjs/gatsby-starter-hello-world
cd tutorial-part-two
```

لديك الآن موقع Gatsby جديد (مستند على حزمة البدء "hello world" في Gatsby) بالهيكل التالي:

```text
├── package.json
├── src
│   └── pages
│       └── index.js
```

#### ✋ إضافة تناسيق إلى ملف css

1. قم بإنشاء ملف `.css` في مشروعك الجديد:

```shell
cd src
mkdir styles
cd styles
touch global.css
```

> ملاحظة: لا تتردد في إنشاء هذه المجلدات والملفات باستخدام محرر الشفرة ، إذا كنت تفضل ذلك.

يجب أن يكون لديك الآن هيكل مثل هذا:

```text
├── package.json
├── src
│   └── pages
│       └── index.js
│   └── styles
│       └── global.css
```

2. تحديد بعض التناسيق في ملف `global.css`:

```css:title=src/styles/global.css
html {
  background-color: lavenderblush;
}
```

> ملاحظة: يعد وضع ملف css example في مجلد `/src/styles/` عشوائيًا.

#### ✋ تضمين ورقة التناسيق في `gatsby-browser.js`

1.  إنشاء `gatsby-browser.js`

```shell
cd ../..
touch gatsby-browser.js
```

يجب أن تبدو بنية ملف المشروع الآن كما يلي:

```text
├── package.json
├── src
│   └── pages
│       └── index.js
│   └── styles
│       └── global.css
├── gatsby-browser.js
```

> 💡 ما هو 'gatsby-browser.js`؟ لا تقلق بشأن هذا كثيرًا ، والآن ، تعرف فقط أن "gatsby-browser.js" هو واحد من مجموعة من الملفات الخاصة التي يبحث عنها Gatsby ويستخدمها (إذا كانت موجودة). هنا ، تسمية الملف **مهمة**. إذا كنت تريد استكشاف المزيد الآن ، فتحقق من [المرجع](/docs/browser-apis/).

2. استيراد ورقة تناسيق تم إنشاؤها مؤخرًا في ملف `gatsby-browser.js`:

```javascript:title=gatsby-browser.js
import "./src/styles/global.css";

// or:
// require('./src/styles/global.css')
```

> ملاحظة: يعمل بناء جملة CommonJS (`require`) و ES Module (`import`) هنا. إذا لم تكن متأكدًا من الخيار ، فسنستخدم `import` معظم الوقت. يتوجب عليك استخدام `require` عند العمل على ملفات تعمل فقط على بيئة عمل `Node.js` (مثل `gatsby-node.js`)

3. ابدأ خادوم التطوير:

```shell
gatsby develop
```

إذا ألقيت نظرة على مشروعك في المتصفح ، فسترى خلفية الزهري مطبقة على إصدار "hello world":

![زهري Hello World!](global-css.png)

> نصيحة: ركز هذا الجزء من الدليل التطبيقي على الطريقة الأسرع والأكثر مباشرة للبدء في تصميم موقع Gatsby - استيراد ملفات CSS القياسية مباشرةً ، باستخدام `gatsby-browser.js`. في معظم الحالات ، تتمثل أفضل طريقة لإضافة تناسيق عمومية في مكون تخطيط مشترك. [راجع المستندات](/docs/global-css/) لمعرفة المزيد حول هذا النهج.

## باستخدام مكون المغلق النطاق

لقد تحدثنا حتى الآن عن الطريقة التقليدية لاستخدام أوراق تناسيق CSS القياسية. الآن ، سوف نتحدث عن طرق مختلفة لنظم CSS لمعالجة التنسيق بطريقة موجهة للمكون.

### وحدات CSS

دعنا نستكشف **وحدات CSS**. نقلا عن
[الصفحة الرئيسية لوحدة CSS](https://github.com/css-modules/css-modules):

> **CSS Module** هو ملف CSS فيه جميع أسماء الفئات وأسماء الرسوم المتحركة
> يتم تحديد النطاق محليًا بشكل افتراضي.

وحدات CSS شائعة جدًا لأنها تتيح لك كتابة CSS بشكل طبيعي ولكن مع قدر أكبر من الأمان. تقوم الأداة تلقائيًا بإنشاء أسماء فصول ورسوم متحركة فريدة ، لذا لا داعي للقلق بشأن تضارب أسماء المحدد.

Gatsby يعمل خارج المألوف مع CSS Modules. ينصح بشدة هذا النهج لأولئك جديدة لبناء مع Gatsby (React و بشكل عام).

#### ✋ بناء صفحة جديدة باستخدام وحدات CSS

في هذا القسم ، ستقوم بإنشاء مكون صفحة جديد ونسق مكون الصفحة باستخدام وحدات CSS.

أولاً ، قم بإنشاء مكون "Container" جديد.

1. قم بإنشاء دليل جديد على `src/components` ثم ، في هذا الدليل الجديد ، قم بإنشاء ملف باسم`container.js` ولصق ما يلي:

```jsx:title=src/components/container.js
import React from "react"
import containerStyles from "./container.module.css"

export default ({ children }) => (
  <div className={containerStyles.container}>{children}</div>
);
```

ستلاحظ أنك قمت باستيراد ملف وحدات CSS باسم `container.module.css`. لنقم بإنشاء هذا الملف الآن.

2. في نفس الدليل (`src/components`) ، قم بإنشاء ملف`container.module.css` وانسخ / الصق ما يلي:

```css:title=src/components/container.module.css
.container {
  margin: 3rem auto;
  max-width: 600px;
}
```

ستلاحظ أن اسم الملف ينتهي بـ ".module.css" بدلاً من `.css` المعتاد. هذه هي الطريقة التي تخبر بها Gatsby أنه يجب معالجة ملف CSS كوحدة تنسيقية CSS بدلاً من CSS عادي.

3. قم بإنشاء مكون صفحة جديد عن طريق إنشاء ملف في `src/pages/about-css-module.js`:

```jsx:title=src/pages/about-css-modules.js
import React from "react"

import Container from "../components/container";

export default () => (
  <Container>
    <h1>حول وحدات CSS</h1>
    <p>وحدات CSS هي رائعة</p>
  </Container>
);
```

الآن ، إذا قمت بزيارة `http://localhost:8000/about-css-modules/` ، فيجب أن تبدو صفحتك على النحو التالي:

![صفحات مع تناسيق وحدات CSS](css-modules-basic.png)

#### ✋ نسق مكّون باستخدام وحدات CSS

في هذا القسم ، ستنشئ قائمة بالأشخاص الذين لديهم أسماء ، وأفاتار ، وسير ذاتية لاتينية قصيرة. ستقوم بإنشاء مكون `<User />` ونسق ذلك المكون باستخدام وحدة CSS.

1. قم بإنشاء ملف CSS في `src/pages/about-css-modules.module.css`.

2. الصق ما يلي في الملف الجديد:

```css:title=src/pages/about-css-modules.module.css
.user {
  display: flex;
  align-items: center;
  margin: 0 auto 12px auto;
}

.user:last-child {
  margin-bottom: 0;
}

.avatar {
  flex: 0 0 96px;
  width: 96px;
  height: 96px;
  margin: 0;
}

.description {
  flex: 1;
  margin-left: 18px;
  padding: 12px;
}

.username {
  margin: 0 0 12px 0;
  padding: 0;
}

.excerpt {
  margin: 0;
}
```

3. استيراد الجديد `src/pages/about-css-modules.module.css` ملف في صفحة `about-css-modules.js` التي قمت بإنشائها سابقًا من خلال تحرير الأسطر القليلة الأولى من الملف مثل:

```javascript:title=src/pages/about-css-modules.js
import React from "react";
// highlight-next-line
import styles from "./about-css-modules.module.css";
import Container from "../components/container";

// highlight-next-line
console.log(styles);
```

ستقوم شفرة `console.log(styles)` بتسجيل الاستيراد الناتج حتى تتمكن من رؤية نتيجة ملفك المعالج`./about-css-modules.module.css` إذا قمت بفتح وحدة تحكم مطوّر البرامج (باستخدام أدوات مطوري Firefox أو Chrome) في متصفحك ، فسترى:

![استيراد نتيجة وحدة CSS في وحدة التحكم](css-modules-console.png)

إذا قارنت ذلك بملف CSS الخاص بك ، فسترى أن كل فصل دراسي أصبح الآن مفتاحًا في الكائن المستورد يشير إلى سلسلة طويلة على سبيل المثال `avatar` تشير إلى صفحات src---- about-css-modules-module---avatar---2lRF7`. هذه هي أسماء الفئات التي تنشئها وحدات CSS. أنها مضمونة لتكون فريدة من نوعها عبر موقعك. ولأنه يتعين عليك استيرادها لاستخدام الفصول الدراسية ، فلا يوجد أي سؤال حول مكان استخدام بعض CSS.

4. قم بإنشاء مكون جديد `<User />` مضمن في صفحة`about-css-modules.js`
مكون. تعديل `about-css-modules.js` بحيث يبدو كما يلي:

```jsx:title=src/pages/about-css-modules.js
import React from "react";
import styles from "./about-css-modules.module.css";
import Container from "../components/container";

console.log(styles);

// highlight-start
const User = props => (
  <div className={styles.user}>
    <img src={props.avatar} className={styles.avatar} alt="" />
    <div className={styles.description}>
      <h2 className={styles.username}>{props.username}</h2>
      <p className={styles.excerpt}>{props.excerpt}</p>
    </div>
  </div>
);
// highlight-end

export default () => (
  <Container>
    <h1>حول وحدات CSS</h1>
    <p>وحدات CSS هي رائعة</p>
    {/* highlight-start */}
    <User
      username="Jane Doe"
      avatar="https://s3.amazonaws.com/uifaces/faces/twitter/adellecharles/128.jpg"
      excerpt="I'm Jane Doe. Lorem ipsum dolor sit amet, consectetur adipisicing elit."
    />
    <User
      username="Bob Smith"
      avatar="https://s3.amazonaws.com/uifaces/faces/twitter/vladarbatov/128.jpg"
      excerpt="I'm Bob Smith, a vertically aligned type of guy. Lorem ipsum dolor sit amet, consectetur adipisicing elit."
    />
    {/* highlight-end */}
  </Container>
);
```

> نصيحة: بشكل عام ، إذا كنت تستخدم مكونًا في أماكن متعددة على أحد المواقع ، فيجب أن يكون في ملف الوحدة التنسيقية الخاص به في دليل `modules`. ولكن ، إذا تم استخدامه في ملف واحد فقط ، فقم بإنشائه عبر الإنترنت.

يجب أن تبدو الصفحة النهائية الآن كما يلي:

![صفحة قائمة المستخدمين مع وحدات CSS](css-modules-userlist.png)

### CSS-in-JS

CSS-in-JS هو أسلوب تصميم موجه للمكونات. بشكل عام ، هو نسق حيث [يتكون CSS بشكل مضمن باستخدام JavaScript](https://reactjs.org/docs/faq-styling.html#what-is-css-in-js).

#### باستخدام CSS-in-JS مع Gatsby

هناك العديد من مكتبات CSS-in-JS المختلفة والعديد منها يحتوي على ملحقات Gatsby بالفعل. لن نغطي مثالًا على CSS-in-JS في هذا الدليل التطبيقي الأولي ، لكننا نشجعك على [استكشاف](/docs/styling/) ما يمكن أن يقدمه النظام البيئي. هناك دروس تعليمية مصغرة لمكتبتين ، على وجه الخصوص ، [العاطفة](/docs/emotion/) و [نصب مكونات](/docs/styled-components/).

#### اقترح القراءة على CSS-in-JS

إذا كنت مهتمًا بمزيد من القراءة ، تحقق من [Christopher "vjeux" عرض Chedeau 2014 الذي أثار هذه الحركة](https://speakerdeck.com/vjeux/react-css-in-js) وكذلك [Mark Dalgleish's more آخر منشور "لغة تصميم موحدة"](https://medium.com/seek-blog/a-unified-styling-language-d0c208de2660).

### خيارات CSS الأخرى

يدعم Gatsby جميع خيارات التنسيق الممكنة تقريبًا (إذا لم يكن هناك مكون إضافي حتى الآن لخيار CSS المفضل لديك ، [الرجاء المساهمة في احد!](/contributing/how-to-contribute/))

- [Typography.js](/packages/gatsby-plugin-typography/)
- [Sass](/packages/gatsby-plugin-sass/)
- [JSS](/packages/gatsby-plugin-jss/)
- [Stylus](/packages/gatsby-plugin-stylus/)
- [PostCSS](/packages/gatsby-plugin-postcss/)

و اكثر!

## ما الذي سيأتي بعد ذلك؟

انتقل الآن إلى [الجزء الثالث من الدليل التطبيقي](/tutorial/part-three/) ، حيث ستتعرف على مكونات Gatsby الإضافية ومكونات التخطيط.
