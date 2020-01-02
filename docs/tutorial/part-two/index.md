---
title: مقدمة في التصميم في Gatsby
typora-copy-images-to: ./
disableTableOfContents: true
---

<!-- Idea: Create a glossary to refer to. A lot of these terms get jumbled -->

<!--
  - Global styles
  - Component css
  - CSS-in-JS
  - CSS Modules

-->

مرحبًا بك في الجزء الثاني من برنامج Gatsby التعليمي!

## ماذا يوجد في هذا البرنامج التعليمي؟

في هذا الجزء ، ستستكشف خيارات تصميم مواقع الويب Gatsby وتعمق في استخدام مكونات React لبناء المواقع.

## باستخدام التصميم الشاملة

كل موقع لديه نوع من النمط شامل . يتضمن ذلك أشياء مثل الطباعة وألوان الخلفية الخاصة بالموقع. تضفي هذه الأنماط طابعًا عامًا على الموقع - تمامًا مثل لون وملمس الحائط الذي يحدد المظهر العام للغرفة.

### إنشاء أنماط شاملة مع ملفات CSS القياسية

إحدى أكثر الطرق المباشرة لإضافة أنماط شاملة إلى موقع ما هي استخدام ورقة أنماط `.css` عالمية.

#### ✋ إنشاء موقع غاتسبي الجديد

ابدأ بإنشاء موقع Gatsby جديد. قد يكون من الأفضل (خصوصًا إذا كنت جديدًا في سطر الأوامر) إغلاق النوافذ الطرفية التي استخدمتها لـ [الجزء الأول](/tutorial/part-one/) وبدء جلسة طرفية جديدة للجزء الثاني.

افتح نافذة طرفية جديدة ، وقم بإنشاء موقع Gatsby جديد "hello world" ، وابدأ خادم التطوير:

```shell
gatsby new tutorial-part-two https://github.com/gatsbyjs/gatsby-starter-hello-world
cd tutorial-part-two
```

لديك الآن موقع Gatsby جديد (استنادًا إلى "hello world" في Gatsby) بهيكله التالي:

```text
├── package.json
├── src
│   └── pages
│       └── index.js
```

#### ✋ إضافة أنماط إلى ملف css

1. قم بإنشاء ملف `.css` في مشروعك الجديد:

```shell
cd src
mkdir styles
cd styles
touch global.css
```

> ملاحظة: لا تتردد في إنشاء هذه الدلائل والملفات باستخدام محرر الشفرة ، إذا كنت تفضل ذلك.

يجب أن يكون لديك الآن هيكل مثل هذا:

```text
├── package.json
├── src
│   └── pages
│       └── index.js
│   └── styles
│       └── global.css
```

2. حدد بعض الأنماط في ملف `global.css`:

```css:title=src/styles/global.css
html {
  background-color: lavenderblush;
}
```

> ملاحظة: يعد وضع ملف css example في مجلد `/src/styles/` عشوائيًا.

#### ✋ تضمين ورقة الأنماط في `gatsby-browser.js`

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

> 💡 ما هو 'gatsby-browser.js`؟ لا تقلق بشأن هذا كثيرًا ، والآن ، تعرف فقط أن "gatsby-browser.js" هو واحد من مجموعة من الملفات الخاصة التي يبحث عنها Gatsby ويستخدمها (إذا كانت موجودة). هنا ، تسمية الملف ** مهمة **. إذا كنت تريد استكشاف المزيد الآن ، فتحقق من [المرجع ](/docs/browser-apis/).

2. استيراد ورقة أنماط تم إنشاؤها مؤخرًا في ملف `gatsby-browser.js`:

```javascript:title=gatsby-browser.js
import "./src/styles/global.css";

// or:
// require('./src/styles/global.css')
```

> ملاحظة: يعمل بناء جملة CommonJS (`requ`) و ES Module (`import`) هنا. إذا لم تكن متأكدًا من الخيار ، فسنستخدم "استيراد" معظم الوقت.

3. ابدأ خادم التطوير:

```shell
gatsby develop
```

إذا ألقيت نظرة على مشروعك في المتصفح ، فسترى خلفية الخزامي مطبقة على إصدار "hello world":

![خزامي Hello World!](global-css.png)

> نصيحة: ركز هذا الجزء من البرنامج التعليمي على الطريقة الأسرع والأكثر مباشرة للبدء في تصميم موقع Gatsby - استيراد ملفات CSS القياسية مباشرةً ، باستخدام `gatsby-browser.js`. في معظم الحالات ، تتمثل أفضل طريقة لإضافة أنماط عمومية في مكون تخطيط مشترك. [راجع المستندات](/docs/global-css/) لمعرفة المزيد حول هذا النهج.

## باستخدام مكون المغلق النطاق

لقد تحدثنا حتى الآن عن الطريقة التقليدية لاستخدام أوراق أنماط CSS القياسية. الآن ، سوف نتحدث عن طرق مختلفة لنظم CSS لمعالجة التصميم بطريقة موجهة للمكون.

### CSS Modules

دعنا نستكشف ** وحدات CSS **. نقلا عن
[الصفحة الرئيسية لوحدة CSS](https://github.com/css-modules/css-modules):

> ** CSS Module ** هو ملف CSS فيه جميع أسماء الفئات وأسماء الرسوم المتحركة
> يتم تحديد النطاق محليًا بشكل افتراضي.

وحدات CSS شائعة جدًا لأنها تتيح لك كتابة CSS بشكل طبيعي ولكن مع قدر أكبر من الأمان. تقوم الأداة تلقائيًا بإنشاء أسماء فصول ورسوم متحركة فريدة ، لذا لا داعي للقلق بشأن تضارب أسماء المحدد.

Gatsby يعمل خارج المألوف مع CSS Modules. ينصح بشدة هذا النهج لأولئك جديدة لبناء مع Gatsby (React و بشكل عام).

#### ✋ بناء صفحة جديدة باستخدام وحدات CSS

في هذا القسم ، ستقوم بإنشاء مكون صفحة جديد ونمط مكون الصفحة باستخدام وحدات CSS.

أولاً ، قم بإنشاء مكون "Container" جديد.

1. قم بإنشاء دليل جديد على `src/components` ثم ، في هذا الدليل الجديد ، قم بإنشاء ملف باسم`container.js` ولصق ما يلي:

```javascript:title=src/components/container.js
import React from "react";
import containerStyles from "./container.module.css";

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

ستلاحظ أن اسم الملف ينتهي بـ ".module.css" بدلاً من `.css` المعتاد. هذه هي الطريقة التي تخبر بها Gatsby أنه يجب معالجة ملف CSS كوحدة نمطية CSS بدلاً من CSS عادي.

3. قم بإنشاء مكون صفحة جديد عن طريق إنشاء ملف في `src/pages/about-css-module.js`:

```javascript:title=src/pages/about-css-modules.js
import React from "react";

import Container from "../components/container";

export default () => (
  <Container>
    <h1>About CSS Modules</h1>
    <p>CSS Modules are cool</p>
  </Container>
);
```

الآن ، إذا قمت بزيارة `http://localhost:8000/about-css-modules/` ، فيجب أن تبدو صفحتك على النحو التالي:

![صفحات مع أنماط وحدات CSS](css-modules-basic.png)

#### ✋ Style a component using CSS Modules

In this section, you'll create a list of people with names, avatars, and short Latin biographies. You'll create a `<User />` component and style that component using a CSS module.

1. Create the file for the CSS at `src/pages/about-css-modules.module.css`.

2. Paste the following into the new file:

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

3. Import the new `src/pages/about-css-modules.module.css` file into the `about-css-modules.js` page you created earlier by editing the first few lines of the file like so:

```javascript:title=src/pages/about-css-modules.js
import React from "react"
// highlight-next-line
import styles from "./about-css-modules.module.css"
import Container from "../components/container"

// highlight-next-line
console.log(styles)
```

The `console.log(styles)` code will log the resulting import so you can see the result of your processed `./about-css-modules.module.css` file. If you open the developer console (using e.g. Firefox or Chrome's developer tools) in your browser, you'll see:

![Import result of CSS module in console](css-modules-console.png)

If you compare that to your CSS file, you'll see that each class is now a key in the imported object pointing to a long string e.g. `avatar` points to `src-pages----about-css-modules-module---avatar---2lRF7`. These are the class names CSS Modules generates. They're guaranteed to be unique across your site. And because you have to import them to use the classes, there's never any question about where some CSS is being used.

4. Create a `User` component.

Create a new `<User />` component inline in the `about-css-modules.js` page
component. Modify `about-css-modules.js` so it looks like the following:

```jsx:title=src/pages/about-css-modules.js
import React from "react"
import styles from "./about-css-modules.module.css"
import Container from "../components/container"

console.log(styles)

// highlight-start
const User = props => (
  <div className={styles.user}>
    <img src={props.avatar} className={styles.avatar} alt="" />
    <div className={styles.description}>
      <h2 className={styles.username}>{props.username}</h2>
      <p className={styles.excerpt}>{props.excerpt}</p>
    </div>
  </div>
)
// highlight-end

export default () => (
  <Container>
    <h1>About CSS Modules</h1>
    <p>CSS Modules are cool</p>
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
)
```

> Tip: Generally, if you use a component in multiple places on a site, it should be in its own module file in the `components` directory. But, if it's used only in one file, create it inline.

The finished page should now look like:

![User list page with CSS modules](css-modules-userlist.png)

### CSS-in-JS

CSS-in-JS is a component-oriented styling approach. Most generally, it is a pattern where [CSS is composed inline using JavaScript](https://reactjs.org/docs/faq-styling.html#what-is-css-in-js).

#### Using CSS-in-JS with Gatsby

There are many different CSS-in-JS libraries and many of them have Gatsby plugins already. We won't cover an example of CSS-in-JS in this initial tutorial, but we encourage you to [explore](/docs/styling/) what the ecosystem has to offer. There are mini-tutorials for two libraries, in particular, [Emotion](/docs/emotion/) and [Styled Components](/docs/styled-components/).

#### Suggested reading on CSS-in-JS

If you're interested in further reading, check out [Christopher "vjeux" Chedeau's 2014 presentation that sparked this movement](https://speakerdeck.com/vjeux/react-css-in-js) as well as [Mark Dalgleish's more recent post "A Unified Styling Language"](https://medium.com/seek-blog/a-unified-styling-language-d0c208de2660).

### Other CSS options

Gatsby supports almost every possible styling option (if there isn't a plugin yet for your favorite CSS option, [please contribute one!](/contributing/how-to-contribute/))

- [Typography.js](/packages/gatsby-plugin-typography/)
- [Sass](/packages/gatsby-plugin-sass/)
- [JSS](/packages/gatsby-plugin-jss/)
- [Stylus](/packages/gatsby-plugin-stylus/)
- [PostCSS](/packages/gatsby-plugin-postcss/)

and more!

## What's coming next?

Now continue on to [part three of the tutorial](/tutorial/part-three/), where you'll learn about Gatsby plugins and layout components.
