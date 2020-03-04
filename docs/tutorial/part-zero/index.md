---
title: Set Up Your Development Environment
typora-copy-images-to: ./
disableTableOfContents: true
---

قبل البدء في إنشاء موقعك الأول بـ Gatsby ، ستحتاج إلى التعرف على بعض تقنيات الويب الأساسية والتأكد من أنك قمت بتثبيت جميع أدوات البرمجيات المطلوبة.

## عود نفسك على سطر الأوامر

سطر الأوامر هو واجهة قائمة على النصوص تُستخدم لتشغيل الأوامر على جهاز الحاسب الخاص بك. سترى أيضًا في كثير من الأحيان أنه يشار إليه باسم "الطرفية Terminal". في هذا الدليل التطبيقي ، سنستخدم كلاهما بالتبادل. انه يشبه كثيراً استخدام Finder على جهاز Mac أو Explorer على نظام التشغيل Windows. Finder و Explorer أمثلة من واجهات المستخدم الرسومية (GUI). يعد سطر الأوامر طريقة فعالة تعتمد على النص للتفاعل مع جهاز الحاسب الخاص بك.

نتوقف لحظة لتحديد مكان وفتح واجهة سطر الأوامر (CLI) في جهاز الحاسب الخاص بك. اعتمادًا على نظام التشغيل الذي تستخدمه ، راجع [**إرشادات لنظام التشغيل Mac**](http://www.macworld.co.uk/feature/mac-software/how-use-terminal-on-mac-3608274/) أو [**تعليمات لنظام التشغيل Windows**](https://www.quora.com/How-do-I-open-terminal-in-windows) أو [**تعليمات لنظام التشغيل Linux**](https://www.howtogeek.com/140679/beginner-geek-how-to-start-using-the-linux-terminal/).

_Note: If you’re new to the command line, "running" a command, means "writing a given set of instructions in your command prompt, and hitting the Enter key". Commands will be shown in a highlighted box, something like `node --version`, but not every highlighted box is a command! If something is a command it will be mentioned as something you have to run/execute._

## Install Node.js for your appropriate operating system

Node.js is an environment that can run JavaScript code outside of a web browser. Gatsby is built with Node.js. To get up and running with Gatsby, you’ll need to have a recent version installed on your computer. npm comes bundled with Node.js so if you don't have npm, chances are that you don't have Node.js either.

### تعليمات مستخدمو Mac

لتثبيت Gatsby و Node.js ، يوصى باستخدام [Homebrew](https://brew.sh/). مجموعة تنصيبات صغيرة في البداية يمكن أن تجنبك بعض الصداع في وقت لاحق!

#### كيفية تثبت أو تتحقق من Homebrew على جهازك:

1. قم بفتح "الطرفية Terminal".
2. تاكد ما إذا تم تثبيت Homebrew عن طريق تنفيذ `brew -v`. يجب أن تشاهد "Homebrew" ورقم الإصدار.
3. اذا لم يظهر لك، حمل ونصب [Homebrew باتباع التعليمات](https://docs.brew.sh/Installation).
4. بمجرد تثبيت Homebrew ، كرر الخطوة رقم 2 للتحقق.

#### قم بتثبيت أدوات سطر أوامر Xcode:

1. قم بفتح "الطرفية Terminal".
2. قم بتثبيت أدوات سطر أوامر Xcode عن طريق تشغيل `xcode-select --install`.
   - إذا فشل ذلك، قم بتنزيله [مباشرةً من موقع Apple](https://developer.apple.com/download/more/) بعد تسجيل الدخول باستخدام حساب مطور Apple
3. بعد مطالبتك ببدء التثبيت ، ستتم مطالبتك مرة أخرى بقبول ترخيص برنامج للأدوات المراد تنزيلها.

#### Install Node

1. Open your Terminal
2. Run `brew install node`
   - If you don't want to install it through Homebrew, download the latest Node.js version from [the official Node.js website](https://nodejs.org/en/), double click on the downloaded file and go through the installation process.

### Windows Instructions

- Download and install the latest Node.js version from [the official Node.js website](https://nodejs.org/en/)

### Linux Instructions

Install nvm (Node Version Manager) and needed dependencies. nvm is used to manage Node.js and all its associated versions.

_💡 If when installing a package, it asks for confirmation, type `y` and press enter._

#### Ubuntu, Debian, and other `apt` based distros:

1. Run `sudo apt update` and then `sudo apt -y upgrade` to make sure your Linux distribution is ready to go.
2. Run `sudo apt-get install curl` to install curl which allows you to transfer data and download additional dependencies.
3. After it finishes installing, run `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.1/install.sh | bash` to download the latest nvm version.
4. To confirm this has worked, use the following command. `nvm --version`. The output should be a version number.
5. [Set default Node.js version](#set-default-nodejs-version)

#### Arch, Manjaro and other `pacman` based distros:

1. Run `sudo pacman -Sy` to make sure your distribution is ready to go.
2. These distros come installed with curl, so you can use that to download nvm.
   `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.1/install.sh | bash`
3. Before using nvm, you need to install additional dependencies by running `sudo pacman -S grep awk tar`.
4. To confirm this has worked, use the following command. `nvm --version`. The output should be a version number.
5. [Set default Node.js version](#set-default-nodejs-version)

#### Fedora, RedHat, and other `dnf` based distros:

1. These distros come installed with curl, so you can use that to download nvm.
   `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.1/install.sh | bash`
2. To confirm this has worked, use the following command. `nvm --version`. The output should be a version number.
3. [Set default Node.js version](#set-default-nodejs-version)

If the Linux distribution you are using is not listed here, please find instructions on the web.

#### Set default Node.js version

When nvm is installed, it does not default to a particular node version. You’ll need to install the version you want and give nvm instructions to use it. This example uses the latest release of version 10, but more recent version numbers can be used instead.

```shell
nvm install 10
nvm use 10
```

To confirm that this worked, you can run `npm --version` and `node --version`. The output should look similar to the screenshot below, showing version numbers in response to the commands.

Once you have followed the installation steps and you have checked everything is installed properly, you can continue to the next step.

## تثبيت Git

Git هو نظام للتحكم في الإصدار الموزع مجانًا ومفتوح المصدر مصمم للتعامل مع كل شيء بدءًا من المشاريع الصغيرة إلى المشاريع الكبيرة جدًا بسرعة وكفاءة. عندما تقوم بتثبيت موقع "عدة البدء" Gatsby ، يستخدم Gatsby نظام Git وراء الكواليس لتنزيل وتثبيت الملفات المطلوبة لعدة البدء. ستحتاج إلى تثبيت Git لإعداد أول موقع Gatsby خاصتك.

تعتمد خطوات تنزيل Git وتثبيته على نظام التشغيل لديك. اتبع دليل نظامك:

- [تثبيت Git على macOS](https://www.atlassian.com/git/tutorials/install-git#mac-os-x)
- [تثبيت Git على Windows](https://www.atlassian.com/git/tutorials/install-git#windows)
- [تثبيت Git على Linux](https://www.atlassian.com/git/tutorials/install-git#linux)

## إستخدام واجهة سطر الأوامر Gatsby CLI

تتيح لك أداة Gatsby CLI إنشاء مواقع جديدة مدعومة من Gatsby وتشغيل أوامر لتطوير مواقع Gatsby. إنها حزمة npm منشورة.

يتوفر Gatsby CLI عبر npm ويجب تثبيته بشكلٍ عام عن طريق تنفيذ `npm install -g gatsby-cli`.

_**ملاحظة**: عند تثبيت Gatsby وتشغيله لأول مرة ، سترى رسالة قصيرة لإعلامك ببيانات الاستخدام مجهولة المصدر التي يتم جمعها لأوامر Gatsby ، يمكنك قراءة المزيد حول كيفية سحب تلك البيانات واستخدامها في [وثيقة القياس عن بعد](/docs/telemetry)._

لمعرفة الأوامر المتاحة، نفذ `gatsby --help`.

![تحقق من اوامر gatsby في "الطرفية Terminal"](05-gatsby-help.png)

> 💡 إذا لم تتمكن من تشغيل Gatsby CLI بنجاح بسبب مشكلة في الأذونات، فقد ترغب في التحقق من [مستندات npm على إصلاح الأذونات](https://docs.npmjs.com/getting-started/fixing-npm-permissions), او [هذا الدليل](https://github.com/sindresorhus/guides/blob/master/npm-global-without-sudo.md).

## إنشاء موقع Gatsby

أنت الآن جاهز لاستخدام أداة Gatsby CLI لإنشاء أول موقع لك Gatsby. باستخدام الأداة, يمكنك تحميل “عدة البدء” (مواقع بنيت جزئيا مع بعض المكونات الافتراضية) لمساعدتك في التحرك بشكل أسرع عند إنشاء نوع معين من الموقع. عدة البدء “Hello World” ستستخدم هنا هي عدة بدء مع عدد ضائل من المكونات اللازمة لموقع Gatsby.

1. قم بفتح "الطرفية Terminal".
2. نفذ `gatsby new hello-world https://github.com/gatsbyjs/gatsby-starter-hello-world`. (_ملاحظة: بناءً على سرعة التنزيل لديك ، سوف يختلف مقدار الوقت المستغرق. من أجل الإيجاز ، تم إيقاف gif أدناه أثناء جزء من التثبيت_).
3. نفذ `cd hello-world`.
4. نفذ `gatsby develop`.

<video controls="controls" autoplay="true" loop="true">
  <source type="video/mp4" src="./03-create-site.mp4" />
  <p>المعذرة! متصفحك لا يدعم هذا الفيديو.</p>
</video>

ماذا حدث للتو؟

```shell
gatsby new hello-world https://github.com/gatsbyjs/gatsby-starter-hello-world
```

- `new` هو أمر gatsby لإنشاء مشروع Gatsby جديد.
- هنا, `hello-world` هو عنوان تعسفي - يمكنك اختيار أي شيء. ستضع أداة CLI الشيفرة البرمجية لموقعك الجديد في مجلد جديد يسمى “hello-world”.
- أخيرًا ، يشير عنوان URL الخاص بـ GitHub إلى مستودع الشبفرة الذي يحتفظ بشيفرة عدة البدء الذي تريد استخدامه.

```shell
cd hello-world
```

- هذا يقول "أريد تغيير مسار المجلّد (`cd`) إلى المجلد الفرعي" hello-world ". كلما أردت تشغيل أي أوامر لموقعك ، يجب أن تكون في سياق هذا المسار (ويعرف أيضًا باسم المحطة الطرفية أن يتم توجيهك إلى الدليل حيث يعيش رمز موقعك).

```shell
gatsby develop
```

- يبدأ هذا الأمر في تشغيل خادم التطوير. ستتمكن من رؤية موقعك الجديد والتفاعل معه في بيئة تطوير - محلية (على جهاز الحاسب الخاص بك ، وليس منشوراً على الإنترنت).

### عرض موقعك محليا

افتح علامة تبويب جديدة في متصفحك وانتقل إلى الرابط `http://localhost:8000/`

![تحقق من الصفحة الرئيسية](04-home-page.png)

مبروك! هذه هي بداية موقعك Gatsby الأول! 🎉

ستتمكن من زيارة الموقع محليًا على `http://localhost:8000/` طالما أن خادم التطوير الخاص بك يعمل. هذه هي العملية التي بدأت بتنفيذ الامر `gatsby develop`. لوقف تشغيل هذه العملية (أو “للتوقف عن تشغيل خادم التطوير”), العودة إلى النافذة الطرفية الخاصة بك ، اضغط باستمرار على مفتاح “التحكم”, ثم إضغط على “c” (ctrl-c). لبدء ذلك مرة أخرى, نفذ `gatsby develop` مرة أخرى!

**ملاحظة:** إذا كنت تستخدم إعداد VM مثل `vagrant` و / أو ترغب في الاستماع على عنوان IP المحلي الخاص بك, نفذ `gatsby develop -- --host=0.0.0.0`. الآن، يستمع خادم التطوير على كل من `http://localhost` و IP المحلي الخاص بك.

## إعداد محرر الشيفرة البرمجية

محرر الشيفرة البرمجية هو عبارة عن برنامج صمم خصيصاً لتحرير شيفرة الحاسب. هنالك العديد من .المحررات المشهورة

### تنزيل VS Code

تتضمن وثائق Gatsby أحيانًا لقطات شاشة تم التقاطها في VS Code ،لذلك إذا لم يكن لديك محرر للشيفرة البرمجية مستحسن حتى الآن, فإن استخدام VS Code سوف يجعلك تتاكد من أن شاشتك تبدو تمامًا مثل لقطات الشاشة في الدليل التطبيقي والمستندات. إذا اخترت استخدام VS Code ،فانتقل إلى [موقع VS Code](https://code.visualstudio.com/#alt-downloads) وقم بتنزيل الإصدار المناسب للنظام الأساسي الخاص بك.

### تثبيت الاضافة Prettier

نوصي أيضا باستخدام [Prettier](https://github.com/prettier/prettier), كونها أداة تساعد في تنسيق التعليمات البرمجية لتجنب الأخطاء.

يمكنك استخدام Prettier مباشرة في محررك باستخدام [إضافة Prettier VS Code](https://github.com/prettier/prettier-vscode):

1. افتح عرض الامتدادات على VS Code (View => Extensions).
2. أبحث عن "Prettier - Code formatter".
3. اضغط "Install". (بعد التثبيت ، سيُطلب منك إعادة تشغيل VS Code لتمكين الاضافة. الإصدارات الأحدث من VS Code ستمكّن الاضافة تلقائيًا بعد التنزيل.)

> 💡 إذا كنت لا تستخدم VS Code, تحقق من مستندات Prettier لمعرفة [تعليمات التثبيت](https://prettier.io/docs/en/install.html) أو [تكامل مع محررات أخرى](https://prettier.io/docs/en/editors.html).

## ➡️ ماذا بعد؟

للتلخيص, في هذا القسم أنت قد:

- تعلمت عن سطر الأوامر وكيفية استخدامها
- تثبيت ومعرفة Node.js وأداة npm CLI ونظام التحكم في الإصدار Git وأداة Gatsby CLI
- إنشاء موقع Gatsby جديد باستخدام أداة Gatsby CLI
- تشغيل خادوم تطوير Gatsby ومشاهدة موقع محلياً
- تنزيل محرر الشيفرة البرمجية
- تثبيت منسق الشيفرة البرمجية المسمى Prettier

الان, إنتقل الى [**التعرف على لبنات Gatsby**](/tutorial/part-one/).

## المراجع

### نظرة عامة على التقنيات الأساسية

ليس من الضروري أن تكون خبيرًا بالفعل مع هؤلاء - إذا لم تكن كذلك ، فلا تقلق! ستحصل على الكثير من خلال هذه السلسلة التعليمية. هذه بعض تقنيات الويب الرئيسية التي ستستخدمها عند إنشاء موقع Gatsby:

- **HTML**: لغة ترميز يستطيع كل متصفح ويب فهمها. وهي إختصار لـ "HyperText Markup Language". توفر HTML لمحتوى الويب الخاص بك بنية إعلامية شاملة، تحدد أشياء مثل العناوين والفقرات والمزيد.
- **CSS**: لغة عرض تُستخدم في تصميم مظهر محتوى الويب الخاص بك (الخطوط والألوان والتخطيط وما إلى ذلك). وهي إختصار لـ "Cascading Style Sheets".
- **JavaScript**: لغة برمجة تساعدنا على جعل الويب ديناميكيًا وتفاعليًا.
- **React**: مكتبة برمجية (بنيت مع JavaScript) لبناء واجهات المستخدم. إنه إطار العمل الذي يستخدمه Gatsby لإنشاء صفحات وبنية المحتوى.
- **GraphQL**: لغة استعلام تتيح لك سحب البيانات إلى موقع الويب الخاص بك. إنها الواجهة التي يستخدمها Gatsby لإدارة بيانات الموقع.

### ما هو موقع الويب؟

للحصول على مقدمة شاملة حول ماهية موقع الويب - بما في ذلك مقدمة إلى HTML و CSS - راجع “[**بناء أول صفحة الويب الخاصة بك**](https://learn.shayhowe.com/html-css/building-your-first-web-page/)”. إنه مكان رائع لبدء التعلم عن الويب. لمزيد من الدليل التطبيقي على مقدمة [**HTML**](https://www.codecademy.com/learn/learn-html), و[**CSS**](https://www.codecademy.com/learn/learn-css), و[**JavaScript**](https://www.codecademy.com/learn/introduction-to-javascript), تحقق من الدروس في Codecademy. [**React**](https://reactjs.org/tutorial/tutorial.html) و [**GraphQL**](http://graphql.org/graphql-js/) لديها أيضا دروس تمهيدية خاصة بهم.

### تعرف على المزيد حول سطر الأوامر

للحصول على مقدمة رائعة لاستخدام سطر الأوامر ، راجع [**دليل سطر الاوامر من Codecademy**](https://www.codecademy.com/courses/learn-the-command-line/lessons/navigation/exercises/your-first-command) لمستخدمي Mac و Linux, و [**هذا الدليل التطبيقي**](https://www.computerhope.com/issues/chusedos.htm) لمستخدمي ويندوز. حتى لو كنت أحد مستخدمي Windows ، فإن الصفحة الأولى من الدليل التطبيقي لـ Codecademy هي قراءة قيمة. يشرح ما هو سطر الأوامر ، وليس فقط كيفية التعامل معه.

### تعلم المزيد عن npm

npm هو مدير حزمة JavaScript. الحزمة عبارة عن وحدة نمطية من التعليمات البرمجية التي يمكنك اختيار تضمينها في مشاريعك. إذا قمت بتنزيل وتثبيت Node.js ، تم تثبيت npm به!

يحتوي npm على ثلاثة مكونات متميزة: موقع npm ، وسجل npm ، وواجهة سطر أوامر npm (CLI).

- على موقع npm على الويب ، يمكنك استعراض حزم JavaScript المتاحة في سجل npm.
- سجل npm عبارة عن قاعدة بيانات كبيرة تحتوي على معلومات حول حزم JavaScript المتاحة على npm.
- بمجرد تحديد الحزمة التي تريدها ، يمكنك استخدام npm CLI لتثبيته في مشروعك أو بشكلٍ عام (مثل أدوات CLI الأخرى). npm CLI هو ما يتحدث إلى السجل - أنت تتفاعل بشكل عام فقط مع موقع npm أو npm CLI.

> 💡 تحقق من مقدمة npm ، "[**ما هو npm؟**](https://docs.npmjs.com/getting-started/what-is-npm)”.

### معرفة المزيد عن Git

لن تحتاج إلى معرفة Git لإكمال هذا الدليل التطبيقي ، لكنه أداة مفيدة للغاية. إذا كنت مهتمًا بمعرفة المزيد حول التحكم في الإصدار ، Git و GitHub ، تحقق من دليل GitHub [Git Handbook](https://guides.github.com/introduction/git-handbook/).
