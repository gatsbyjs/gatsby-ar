---
title: إنشاء مكونات تخطيط متداخل
typora-copy-images-to: ./
disableTableOfContents: true
---

مرحبا بكم في الجزء الثالث!!

## ماذا يوجد في هذا الدليل التطبيقي؟?

في هذا الجزء ، ستتعرف على المكونات الإضافية لـ Gatsby وإنشاء مكونات "layout".

ملحقات Gatsby هي حزم JavaScript تساعد على إضافة وظائف إلى موقع Gatsby. تم تصميم Gatsby ليكون قابلاً للتوسعة ، مما يعني أن الإضافات قادرة على تمديد وتعديل كل ما يفعله Gatsby.


مكونات النسق مخصصة لأقسام موقعك التي ترغب في مشاركتها عبر عدة صفحات. على سبيل المثال ، سيكون للمواقع عادةً مكون تخطيط برأس وتذييل مشترك. الأشياء الشائعة الأخرى المراد إضافتها إلى التخطيطات هي شريط جانبي و / أو قائمة تنقل. في هذه الصفحة على سبيل المثال ، يمثل الرأس في الجزء العلوي جزءًا من مكون تخطيط gatsbyjs.org.

دعونا الغوص في الجزء الثالث.

## باستخدام الإضافات

ربما تكون على دراية بفكرة المكونات الإضافية. تدعم العديد من أنظمة البرامج إضافة مكونات إضافية مخصصة لإضافة وظائف جديدة أو حتى تعديل الأعمال الأساسية للبرنامج. الإضافات Gatsby تعمل بنفس الطريقة.

يمكن لأعضاء المجتمع (مثلك!) المساهمة في المكونات الإضافية (كميات صغيرة من شفرة JavaScript) التي يمكن للآخرين استخدامها عند إنشاء مواقع Gatsby.

> هناك بالفعل المئات من الإضافات! استكشف Gatsby [Plugin Library](/plugins/).

هدفنا مع المكونات الإضافية هو جعلها سهلة التركيب والاستخدام. من المحتمل أنك تستخدم المكونات الإضافية في كل موقع Gatsby تقريبًا تقوم بإنشائه. أثناء العمل خلال بقية الدليل التطبيقي، ستتاح لك العديد من الفرص للتدرب على تثبيت المكونات الإضافية واستخدامها.

للحصول على مقدمة أولية لاستخدام المكونات الإضافية ، سنقوم بتثبيت وتطبيق Gatsby plugin لـ Typography.js.

[Typography.js] (https://kyleamathews.github.io/typography.js/) هي مكتبة JavaScript تنشئ تناسيق أساسية عالمية لطباعة موقعك. تحتوي المكتبة على [ملحق Gatsby المقابل] (/package/gatsby-plugin-typography/) لتبسيط استخدامه في موقع Gatsby.
### ✋ إنشاء موقع Gatsby جديد

As we mentioned in [part two](/tutorial/part-two/), at this point it's probably a good idea to close the terminal window(s) and project files from previous parts of the tutorial, to keep things clean on your desktop. Then open a new terminal window and run the following commands to create a new Gatsby site in a directory called `tutorial-part-three` and then move to this new directory:

```shell
gatsby new tutorial-part-three https://github.com/gatsbyjs/gatsby-starter-hello-world
مؤتمر نزع السلاح تعليمي الجزء الثالث
```

### ✋ تثبيت وتكوين `gatsby-plugin-typography`

هناك خطوتان أساسيتان لاستخدام مكون إضافي: التثبيت والتكوين.

1. تحميل هذا `gatsby-plugin-typography` NPM package.

```shell
npm install --save gatsby-plugin-typography react-typography typography typography-theme-fairy-gates
```

> ملاحظة: يتطلب Typography.js بعض الحزم الإضافية ، بحيث يتم تضمينها في الإرشادات. سيتم إدراج متطلبات إضافية مثل هذا في تعليمات "التثبيت" لكل مكون إضافي.

2. قم بتحرير الملف `gatsby-config.js` في جذر مشروعك إلى ما يلي:

```javascript:title=gatsby-config.js
module.exports = {
  plugins: [
    {
      resolve: `gatsby-plugin-typography`,
      options: {
        pathToConfigModule: `src/utils/typography`,
      },
    },
  ],
}
```

يعد "gatsby-config.js" ملفًا خاصًا آخر يتعرف عليه Gatsby تلقائيًا. هذا هو المكان الذي تضيف فيه المكونات الإضافية وتهيئة الموقع الأخرى.

> تحقق من [doc on gatsby-config.js] (/docs/gatsby-config/) لقراءة المزيد ، إذا كنت ترغب في ذلك.

3. Typography.js يحتاج إلى ملف التكوين. قم بإنشاء دليل جديد يسمى `utils` في دليل` src`. ثم قم بإضافة ملف جديد يسمى `typography.js` إلى` utils` وانسخ ما يلي إلى الملف:

```javascript:title=src/utils/typography.js
import Typography from "typography"
import fairyGateTheme from "typography-theme-fairy-gates"

const typography = new Typography(fairyGateTheme)

export const { scale, rhythm, options } = typography
export default typography
```

4. تشغيل خادم التطوير .

```shell
gatsby develop
```

Once you load the site, if you inspect the generated HTML using the Chrome developer tools, you’ll see that the typography plugin added a `<style>` element to the `<head>` element with its generated CSS:

![typography-styles](typography-styles.png)

### ✋ قم بإجراء بعض التغييرات في المحتوى والأسلوب

انسخ ما يلي إلى `src/pages/index.js` حتى تتمكن من رؤية
تأثير CSS التي تم إنشاؤها بواسطة Typography.js أفضل.

```jsx:title=src/pages/index.js
import React from "react"

export default () => (
  <div>
    <h1>Hi! I'm building a fake Gatsby site as part of a tutorial!</h1>
    <p>
      What do I like to do? Lots of course but definitely enjoy building
      websites.
    </p>
  </div>
)
```

يجب أن يبدو موقعك الآن هكذا:

![no-layout](no-layout.png)

دعونا نجعل تحسنا سريعا. تحتوي العديد من المواقع على عمود واحد من النص يتمركز في منتصف الصفحة. لإنشاء هذا ، أضف الأنماط التالية إلى

`<div>` in `src/pages/index.js`.

```jsx:title=src/pages/index.js
import React from "react"

export default () => (
  // highlight-next-line
  <div style={{ margin: `3rem auto`, maxWidth: 600 }}>
    <h1>Hi! I'm building a fake Gatsby site as part of a tutorial!</h1>
    <p>
      What do I like to do? Lots of course but definitely enjoy building
      websites.
    </p>
  </div>
)
```

![with-layout2](with-layout2.png)

حلو. لقد قمت بتثبيت وتهيئة أول مكون إضافي لبرنامج Gatsby!

## إنشاء مكونات التخطيط

الآن دعنا ننتقل إلى التعرف على مكونات التخطيط. للاستعداد لهذا الجزء ، أضف صفحتين جديدتين إلى مشروعك: صفحة حول وصفحة اتصال.

```jsx:title=src/pages/about.js
import React from "react"

export default () => (
  <div>
    <h1>About me</h1>
    <p>I’m good enough, I’m smart enough, and gosh darn it, people like me!</p>
  </div>
)
```

```jsx:title=src/pages/contact.js
import React from "react"

export default () => (
  <div>
    <h1>I'd love to talk! Email me at the address below</h1>
    <p>
      <a href="mailto:me@example.com">me@example.com</a>
    </p>
  </div>
)
```

لنرى كيف تبدو الصفحة الجديدة:

![about-uncentered](about-uncentered.png)

سيكون من الرائع أن يتم توسيط محتوى الصفحتين الجديدتين مثل صفحة الفهرس. وسيكون من الجيد أن يكون لديك نوع من التنقل الشامل ، لذلك يسهل على الزائرين العثور على كل صفحة من الصفحات الفرعية وزيارتها.

ستتعامل مع هذه التغييرات عن طريق إنشاء مكون التخطيط الأول.

### ✋ قم بإنشاء مكون التصميم الأول الخاص بك

1. إنشاء دليل جديد في `src/components`.

2. قم بإنشاء مكون تخطيط أساسي جدًا على `src/components/layout.js`:

```jsx:title=src/components/layout.js
import React from "react"

export default ({ children }) => (
  <div style={{ margin: `3rem auto`, maxWidth: 650, padding: `0 1rem` }}>
    {children}
  </div>
)
```

3. قم باستيراد مكون التصميم الجديد هذا إلى مكون الصفحة src/pages/index.js`:

```jsx:title=src/pages/index.js
import React from "react"
import Layout from "../components/layout" // highlight-line

export default () => (
  <Layout> {/* highlight-line */}
    <h1>Hi! I'm building a fake Gatsby site as part of a tutorial!</h1>
    <p>
      What do I like to do? Lots of course but definitely enjoy building
      websites.
    </p>
  </Layout> {/* highlight-line */}
)
```

![with-layout2](with-layout2.png)

الحلو ، والتخطيط يعمل! لا يزال محتوى صفحة الفهرس مركَّزًا.

ولكن حاول الانتقال إلى `/about/`, أو `/contact/`. لا يزال المحتوى على تلك الصفحات غير مركز.

4. قم باستيراد مكون التخطيط في `about.js` و` contact.js` (كما فعلت بالنسبة لـ index.js` في الخطوة السابقة).

تتمحور محتويات الصفحات الثلاث جميعها بفضل مكون التخطيط المشترك هذا!

### ✋ إضافة عنوان الموقع

1. أضف السطر التالي إلى مكون التخطيط الجديد الخاص بك:

```jsx:title=src/components/layout.js
import React from "react"

export default ({ children }) => (
  <div style={{ margin: `3rem auto`, maxWidth: 650, padding: `0 1rem` }}>
    <h3>MySweetSite</h3> {/* highlight-line */}
    {children}
  </div>
)
```

إذا ذهبت إلى أي من صفحاتك الثلاث ، فستظهر العنوان نفسه مضافًا ، على سبيل المثال صفحة `/about/`:

![with-title](with-title.png)

### ✋ إضافة روابط التنقل بين الصفحات

1. انسخ ما يلي إلى ملف مكون التخطيط الخاص بك:

```jsx:title=src/components/layout.js
import React from "react"
// highlight-start
import { Link } from "gatsby"

const ListLink = props => (
  <li style={{ display: `inline-block`, marginRight: `1rem` }}>
    <Link to={props.to}>{props.children}</Link>
  </li>
)
// highlight-end

export default ({ children }) => (
  <div style={{ margin: `3rem auto`, maxWidth: 650, padding: `0 1rem` }}>
    {/* highlight-start */}
    <header style={{ marginBottom: `1.5rem` }}>
      <Link to="/" style={{ textShadow: `none`, backgroundImage: `none` }}>
        <h3 style={{ display: `inline` }}>MySweetSite</h3>
      </Link>
      <ul style={{ listStyle: `none`, float: `right` }}>
        <ListLink to="/">Home</ListLink>
        <ListLink to="/about/">About</ListLink>
        <ListLink to="/contact/">Contact</ListLink>
      </ul>
    </header>
    {/* highlight-end */}
    {children}
  </div>
)
```

![with-navigation2](with-navigation2.png)

وهناك لديك! موقع من ثلاث صفحات مع الملاحة العالمية الأساسية.

__تحدي: _بفضل قوى "مكون التخطيط" الجديدة ، حاول إضافة الرؤوس والتذييلات والتنقل الشامل والأشرطة الجانبية وما إلى ذلك إلى مواقع Gatsby الخاصة بك!

## ما الذي سيأتي بعد ذلك؟
متابعة إلى [الجزء الرابع من الدليل التطبيقي](/tutorial/part-four/) حيث ستبدأ في التعرف على طبقة بيانات Gatsby وإنشاء صفحات برمجياً!
