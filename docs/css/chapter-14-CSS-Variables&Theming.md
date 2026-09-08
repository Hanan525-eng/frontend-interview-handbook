├── Chapter 14 — CSS Variables & Theming  

│   ├── Custom Properties
│   ├── var() & fallback values
│   ├── inheritance & scope
│   ├── Theming (Light/Dark mode)
│   └── Design Tokens architecture
السؤال الاول
ليه محتاجين CSS Variables أصلًا؟
🧠 الفكرة المبسطة

تخيلي بدل ما تكتبي رقم تليفون صاحبتك في 10 ورقات مختلفة، تحفظيه مرة واحدة في جهة الاتصال، وأي حد يحتاجه يفتح الجهة دي. لو الرقم اتغيّر، بتغيّريه مرة واحدة بس، مش في كل الورقات.

🔧 الصياغة التقنية
css
:root {
  --primary-color: #2a4b8d;
  --spacing-md: 16px;
}
button {
  background-color: var(--primary-color);
  padding: var(--spacing-md);
}
🎯 الربط

"السؤال اللي بيحدد لو محتاجة Variable: القيمة دي بتتكرر؟ ليها معنى تصميمي؟ ممكن تتغيّر مستقبلًا؟ لو الإجابة أيوه على الثلاثة، دي مرشحة قوية تبقى Variable."

🎨 في Figma

Figma Variables بتعمل نفس الدور بالظبط - قيمة مركزية واحدة (لون، مسافة، رقم) بتتربط بيها عناصر متعددة، وأي تعديل عليها بينعكس على كل حاجة مرتبطة بيها تلقائيًا. المفهوم مطابق تمامًا لـ CSS Custom Properties.

14.2 var() & Fallback Values
🔧 الصياغة التقنية
css
color: var(--text-color, #16213a); /* لو --text-color مش موجودة، استخدمي #16213a */
color: var(--text-color, var(--default-text, black)); /* fallback متعدد المستويات */
⚠️ خطأ شائع في الفهم

الـ fallback مش "قيمة بديلة دايمًا موجودة جنبها" - هي بتتفعّل بس لو المتغير الأساسي مش موجود أو مش صالح في السياق ده تحديدًا.

🎯 الربط

"الـ fallback بتديكي شبكة أمان - مفيدة جدًا لو بتبنيش component قابل لإعادة الاستخدام في مشاريع مختلفة، ومش متأكدة إن الـ variable هتكون معرّفة دايمًا في كل سياق."

🎨 في Figma

⚠️ محتاجة تأكيد: مفيش مفهوم "fallback value" مباشر لو الـ Variable في Figma مش معرّفة - العنصر ببساطة بياخد القيمة اللي محطوطة عليه مباشرة لو مفيش variable مربوطة بيه. الآلية مختلفة تمامًا عن منطق fallback الديناميكي في CSS.

14.3 Inheritance & Scope
🧠 الفكرة المبسطة

فكري في :root كـ "الميزانية العامة للدولة كلها" - متاحة لأي حد. لما تعرّفي variable جوه .card بس، هي بقت "ميزانية القسم" - متاحة بس للقسم ده وفروعه.

🔧 الصياغة التقنية
css
:root {
  --text-color: #16213a; /* Global */
}
.button {
  --button-color: blue; /* Local - خاص بالـ button بس */
  background: var(--button-color);
}
.button-danger {
  --button-color: red; /* Override محلي */
}
🎯 الربط

"الفرق بين :root { --color: red; } و.component { --color: red; } مش مجرد مكان الكتابة - الأول Global، الثاني Local ومربوط بالـ scope بتاع العنصر وأبنائه بس. ده اللي بيخلي نفس الاسم (--button-color) يدّي قيم مختلفة حسب الـ class المستخدمة، وده أساس بناء الـ Component Variants."

14.4 Theming (Light/Dark Mode)
🔧 الصياغة التقنية
css
/* تلقائي حسب إعدادات نظام التشغيل */
@media (prefers-color-scheme: dark) {
  :root {
    --bg-primary: #111827;
    --text-primary: #ffffff;
  }
}

/* يدوي عبر attribute يتحكم فيه المستخدم */
[data-theme="dark"] {
  --bg-primary: #111827;
  --text-primary: #ffffff;
}
🎯 الربط

"أهم جملة في الموضوع كله: Components consume tokens — Theme controls tokens. الـ Component نفسه (background: var(--bg-primary)) مش بيتغيّر خالص بين اللايت والدارك - بس قيمة الـ variable هي اللي بتتغيّر."

🎨 في Figma

Figma Variables بتدعم مفهوم اسمه "Modes" - بتعرّفي أكتر من نسخة (Light/Dark مثلًا) لنفس مجموعة الـ variables، وبتبدّلي بينهم على مستوى الصفحة أو الـ Frame. ده مطابق تمامًا لفكرة الـ theming في CSS بالـ data-theme attribute.

14.5 🆕 محدودية مهمة: var() مش بتشتغل جوه @media
🧠 الفكرة المبسطة

تخيلي عايزة تكتبي "لو عرض الشاشة أكبر من [الرقم المتفق عليه]" لكن الشرط نفسه مقدرش يتقرأ من متغير - لازم تكتبي الرقم الصريح في الشرط.

🔧 الصياغة التقنية
css
:root {
  --breakpoint-tablet: 768px;
}

/* ❌ ده مش هيشتغل خالص */
@media (min-width: var(--breakpoint-tablet)) {
  .card { width: 50%; }
}

/* ✅ لازم تكتبي الرقم صراحة */
@media (min-width: 768px) {
  .card { width: 50%; }
}
🎯 الربط

"ده محدودية معمارية في CSS - الـ Custom Properties بتتقيّم وقت الـ render جوه الـ DOM، لكن شرط الـ media query بيتقيّم في مرحلة مختلفة تمامًا قبل كده. لو محتاجة breakpoints موحّدة عبر المشروع، الحل الشائع هو استخدام SCSS variables (وقت الـ build) أو JavaScript، مش CSS Custom Properties."

14.6 🆕 @property — تسجيل نوع الـ Variable لتفعيل الـ Animation
🧠 الفكرة المبسطة

المتصفح بيتعامل مع أي Custom Property افتراضيًا وكأنها نص عادي غير مفهوم المعنى - يعني لو حاولتي تعملي transition عليها، مش هيعرف "يتدرّج" بينها وبين القيمة الجديدة، هيقفز فجأة. تسجيلها بـ @property بيقول للمتصفح "دي فعليًا رقم/زاوية/لون، اتعاملي معاها بذكاء."

🔧 الصياغة التقنية
css
@property --angle {
  syntax: '<angle>';
  inherits: false;
  initial-value: 0deg;
}

.spinner {
  transition: --angle 1s;
}
🎯 الربط

"دي نقطة متقدمة جدًا (مش أساسية للاستخدام اليومي)، لكنها بتفسّر ليه بعض الـ animations على custom properties مش بتشتغل بسلاسة زي ما متوقعة - المتصفح محتاج يعرف نوع القيمة الأول قبل ما يقدر يعمل تدرّج رياضي بينها."

14.7 Design Tokens Architecture
🔧 الصياغة التقنية
css
:root {
  /* Primitive */
  --blue-700: #2a4b8d;
  /* Semantic */
  --color-primary: var(--blue-700);
  /* Component */
  --button-bg: var(--color-primary);
}
Mental Model
Raw Value (#2A4B8D) → Primitive Token (--blue-700) → Semantic Token (--color-primary) → Component
🎯 الربط

"لماذا Semantic Tokens أفضل من الأسماء الوصفية للون؟ لأن --color-primary بتوصف الوظيفة، مش القيمة الحالية. لو الـ primary اتغيّر من أزرق لأخضر، اسم الـ variable مش هيبقى 'كاذب' زي ما كان هيحصل لو سميتيه --blue-500."

🎨 في Figma

بنية الـ Design Tokens دي (Primitive → Semantic → Component) هي بالظبط نفس الطريقة اللي بيتم بيها تنظيم Figma Variables في الممارسات الحديثة - بتعرّفي مجموعة "Primitives" (ألوان خام)، وبعدين "Semantic" variables بتشاور على الـ primitives دي بالاسم الوظيفي، بنفس التسلسل الهرمي.

14.8 CSS Variables vs SCSS Variables
	CSS Variables	SCSS Variables
وقت المعالجة	Runtime (في المتصفح)	Build time (قبل ما توصل للمتصفح)
تتغير بـ JavaScript	✅	❌
تدعم Inheritance	✅	❌
مناسبة لـ	Theming ديناميكي	Preprocessing وقت البناء
🎯 الربط

"الفرق الجوهري: SCSS variable بتتحول لقيمة ثابتة نهائيًا وقت الـ build - يعني $primary: blue; بتتحول فعليًا لكلمة blue في كل مكان في ملف الـ CSS النهائي. CSS variable بتفضل 'حية' في المتصفح، فتقدري تغيّريها أثناء التشغيل الفعلي (زي theme switcher) من غير ما تحتاجي تعيدي بناء المشروع."

14.9 CSS Variables + JavaScript
🔧 الصياغة التقنية
js
document.documentElement.style.setProperty("--brand-primary", companyColor);
🎯 الربط

"ده أساس أي 'white-label product' - نظام SaaS واحد، لكن كل شركة عميلة بتاخد الـ brand color بتاعها من غير ما تحتاجي تكتبي CSS منفصل لكل عميل. الـ Component بيفضل نفسه، بس الـ variable هي اللي بتتغيّر runtime."

14.10 ⚠️ فخ Senior: ربط رقم مجرد بوحدة قياس
🔧 الصياغة التقنية
css
:root {
  --space: 10; /* رقم من غير وحدة */
}

/* ❌ ده مش هيشتغل - المتصفح بيرفض الدمج النصي المباشر ده */
.box {
  margin-top: var(--space)px;
}

/* ✅ الحل: استخدام calc() للضرب في وحدة */
.box {
  margin-top: calc(var(--space) * 1px);
}
🎯 الربط

"السبب: CSS مش بيعمل 'string concatenation' زي لغات البرمجة العادية - مش ممكن تلصقي px جنب متغير مباشرة. calc() هي الطريقة الرسمية لربط رقم مجرد بوحدة قياس فعلية."

⚠️ أخطاء شائعة
الإفراط في استخدام Variables - مش كل قيمة مستخدمة مرة واحدة تستاهل تبقى variable
أسماء مرتبطة باللون بدل الوظيفة - --blue بدل --color-primary
تجاهل الفرق بين Global و Local scope
🎯 Senior Interview Questions
1. الفرق بين CSS Variable و SCSS Variable؟

CSS تشتغل Runtime وممكن تتغيّر بـ JavaScript، SCSS بتتحول لقيم ثابتة وقت الـ build.

2. ليه Semantic Tokens أفضل من أسماء الألوان الخام؟

بتوصف الوظيفة مش القيمة، فلو اللون اتغيّر الاسم يفضل منطقي.

3. ليه var(--space)px مش بتشتغل؟

CSS مش بيعمل دمج نصي مباشر. الحل: calc(var(--space) * 1px).

4. تقدري تستخدمي var() جوه شرط @media؟

لأ. دي محدودية معمارية - الـ custom properties بتتقيّم في مرحلة مختلفة عن شرط الـ media query.

5. إيه فايدة @property؟

بتسجّل نوع الـ custom property (زاوية، رقم، لون) عشان الـ transitions عليها تشتغل بسلاسة بدل قفزة مفاجئة.

🧠 خلاصة الفصل
CSS Variables
│
├── Custom Properties → --primary
├── var() + fallback   → استخدام آمن
├── Scope & Inheritance → :root (Global) vs .component (Local)
├── Theming             → Light/Dark/Brand (Modes)
├── Design Tokens        → Primitive → Semantic → Component
└── محدوديات مهمة
    ├── مش بتشتغل جوه @media
    └── محتاجة @property عشان تتحرك بسلاسة

أهم جملة في الفصل:

Components consume tokens — Theme controls tokens.

📋 Chapter Summary — مراجعة سريعة
المفهوم	القاعدة السريعة
var(--x, fallback)	fallback بيتفعّل بس لو --x مش موجودة/صالحة
Global vs Local scope	:root = عام، .class = محلي لأبنائه
Theming	الـ Component ثابت، قيمة الـ variable هي اللي بتتغيّر
Semantic Tokens	اسم بيصف الوظيفة مش القيمة الخام
var() جوه @media	❌ مش مدعوم
ربط رقم بوحدة	calc(var(--x) * 1px) مش var(--x)px
@property	يخلي الـ custom property قابلة للـ animation السلس
Keywords للحفظ
Custom Properties · var() · Fallback Value
:root · Scope · Local vs Global
prefers-color-scheme · data-theme
Primitive/Semantic/Component Tokens
@property · calc() * 1px
🎤 جملتك النموذجية في المقابلة

"I architect theming with layered design tokens — primitive values feeding semantic tokens that components actually consume, so switching themes never means touching component code. One limitation worth knowing: custom properties can't be referenced inside a media query condition, since they're resolved at a different stage than the query itself. For animating custom properties smoothly, I register them with @property since the browser otherwise treats them as opaque strings."  

