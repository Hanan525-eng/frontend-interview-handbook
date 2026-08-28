Chapter 8 — CSS Grid  

│   ├── Grid Container
│   ├── Columns & Rows
│   ├── fr
│   ├── gap
│   ├── grid-template
│   ├── grid-column / grid-row / span
│   ├── grid-area
│   ├── Alignment (justify/align - items/self/content)
│   ├── auto-fit
│   ├── auto-fill
│   ├── minmax()
│   └── implicit vs explicit grid
السؤال الاول
What is a Grid Container?
🧠 الفكرة المبسطة

فكري في طاولة شطرنج - فيها صفوف وأعمدة في نفس الوقت، مش اتجاه واحد بس زي Flexbox. كل قطعة (Grid Item) ليها مكان محدد بالصف والعمود مع بعض.

🔧 الصياغة التقنية
css
.container {
  display: grid;
}

العنصر بيبقى Grid Container، والـ direct children بتاعته بيبقوا Grid Items. بس لسه محدّدناش عدد الأعمدة أو الصفوف.

🎯 الربط

"الفرق الجوهري عن Flexbox: Grid من الأول مصمم يفكر في بُعدين مع بعض (صفوف + أعمدة)، مش بُعد واحد بيتلف."

8.2 Columns & Rows
🔧 الصياغة التقنية
css
.container {
  display: grid;
  grid-template-columns: 200px 200px 200px;
  grid-template-rows: 100px 200px;
}
┌────────┐ ┌────────┐ ┌────────┐
│ Item 1 │ │ Item 2 │ │ Item 3 │
└────────┘ └────────┘ └────────┘
┌────────┐
│ Item 4 │
└────────┘
🎯 الربط

"عدد القيم اللي بتكتبيها في grid-template-columns هو نفسه عدد الأعمدة - 3 قيم = 3 أعمدة، بغض النظر عن عدد العناصر الفعلي."

8.3 fr — Fraction Unit
🧠 الفكرة المبسطة

تخيلي بيتزا مقسومة على أشخاص حسب "نصيب" كل واحد - مش مقاس ثابت بالسم، لكن نسبة من الكل المتاح.

🔧 الصياغة التقنية
css
grid-template-columns: 1fr 1fr;      /* تقسيم متساوي 50/50 */
grid-template-columns: 1fr 2fr;      /* تقسيم بنسبة 1:2 */
🎯 الربط

"fr بتاخد نصيبها من المساحة المتبقية بعد أي أعمدة بمقاس ثابت. يعني grid-template-columns: 200px 1fr 1fr بتدي أول عمود 200px ثابتة، والـ 1fr التانيين بيتقاسموا الباقي بالتساوي."

8.4 gap
🔧 الصياغة التقنية
css
.grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 24px;          /* row-gap و column-gap */
  gap: 20px 30px;      /* row-gap: 20px, column-gap: 30px */
}
🎯 الربط

"نفس مفهوم gap بالظبط اللي اتعلمناه في Flexbox، بس هنا بتفصل بين الصفوف والأعمدة."

8.5 repeat()
🔧 الصياغة التقنية
css
grid-template-columns: repeat(3, 1fr);
/* = grid-template-columns: 1fr 1fr 1fr; */
🎯 الربط

"مجرد اختصار كتابي - نفس النتيجة، لكن أنضف لما يكون عدد الأعمدة كبير."

8.6 محاذاة المحتوى جوه الـ Grid — 🆕 قسم مفقود بالكامل ومهم جدًا
🧠 الفكرة المبسطة

تخيلي كل خلية في طاولة الشطرنج فيها قطعة أصغر من حجم الخلية. سؤالين هيتطرحوا: "القطعة تقف فين جوه خليتها؟" و**"لو الطاولة كلها أصغر من المساحة المتاحة، تقف فين وسط المساحة الفاضية؟"**

🔧 الصياغة التقنية

فيه 3 مستويات من التحكم، وكل واحد بيجاوب سؤال مختلف:

المستوى 1: محاذاة المحتوى جوه كل خلية (على مستوى الـ Container - بيأثر على كل العناصر)
css
.container {
  display: grid;
  justify-items: center;  /* أفقيًا جوه كل خلية */
  align-items: center;     /* رأسيًا جوه كل خلية */
}
المستوى 2: استثناء لعنصر واحد بس (على مستوى الـ Item)
css
.item-special {
  justify-self: end;   /* العنصر ده بس، أفقيًا */
  align-self: end;      /* العنصر ده بس، رأسيًا */
}
المستوى 3: محاذاة الـ Grid كله جوه الـ Container (لو الـ Grid أصغر من المساحة المتاحة)
css
.container {
  display: grid;
  justify-content: center;  /* الأعمدة كلها كـ كتلة، أفقيًا */
  align-content: center;     /* الصفوف كلها كـ كتلة، رأسيًا */
}
🎯 الربط

"القاعدة اللي بتفرّق: items/self بيتحكموا في مكان المحتوى جوه خليته، بينما content بيتحكم في مكان الـ tracks (الصفوف/الأعمدة) نفسها كـ كتلة واحدة جوه الـ container - وده بس بيبان لو فيه مساحة فاضية زيادة عن حجم الـ Grid الكلي. لاحظي إن الأسماء دي هي نفسها بالظبط اللي اتعلمناها في Flexbox (الفصل السابع)، بس هنا شغالة على بُعدين مش واحد."

8.7 grid-template
🔧 الصياغة التقنية
css
.container {
  display: grid;
  grid-template: 100px 1fr 100px / 200px 1fr;
  /* rows / columns */
}
🎯 الربط

"موجودة، لكن في الاستخدام اليومي grid-template-columns وgrid-template-rows منفصلين أوضح للقراءة وأشهر استخدامًا."

8.8 grid-column / grid-row + span — 🆕 قسم مفقود ومهم عمليًا
🧠 الفكرة المبسطة

تخيلي عايزة قطعة شطرنج تاخد مكان خانتين مجاورين مع بعض بدل خانة واحدة بس. span هي كلمة السحر اللي بتقولها للمتصفح "امدّي العنصر ده على قد كذا خانة".

🔧 الصياغة التقنية
css
.item {
  grid-column: 1 / 3;       /* من خط 1 لخط 3 (يعني عمودين) */
  grid-row: 2 / 4;           /* من خط 2 لخط 4 */
}

/* أو بطريقة أسهل بكتير - الأشهر عمليًا */
.item {
  grid-column: span 2;      /* امتدي عمودين، أيًا كان مكانك */
  grid-row: span 3;          /* امتدي 3 صفوف */
}
🎯 الربط

"دي أشهر طريقة عمليًا تخلي عنصر واحد ياخد مساحة أكبر من خلية واحدة - أشهر وأسهل من كتابة grid-area بالأرقام الأربعة كاملة (1/1/3/3) اللي شرحناها زمان."

8.9 grid-area (بالأرقام)
🔧 الصياغة التقنية
css
.item {
  grid-area: 1 / 1 / 3 / 3;
  /* row-start / column-start / row-end / column-end */
}
🎯 الربط

"دي صيغة grid-area القديمة بالأرقام - بتعمل نفس حاجة grid-column + grid-row مجمّعين في خاصية واحدة. عمليًا الصيغة بالـ named areas (الفقرة الجاية) أشهر وأوضح بكتير."

8.10 Grid Areas — Named Areas
🧠 الفكرة المبسطة

تخيلي بترسمي خريطة الصفحة بالكلام بدل الأرقام - زي ما ترسمي على ورقة "هنا الهيدر، هنا السايدبار، هنا المحتوى".

🔧 الصياغة التقنية
css
.layout {
  display: grid;
  grid-template-areas:
    "header header"
    "sidebar main"
    "footer footer";
}

.header  { grid-area: header; }
.sidebar { grid-area: sidebar; }
.main    { grid-area: main; }
.footer  { grid-area: footer; }
┌─────────────────────────┐
│         Header          │
├──────────┬──────────────┤
│ Sidebar  │     Main     │
├──────────┴──────────────┤
│         Footer          │
└─────────────────────────┘
🎯 الربط

"دي من أقوى استخدامات Grid - بتخليكي ترسمي شكل الصفحة بالكلمات بدل الأرقام، وده بيخلي الكود سهل القراءة جدًا حتى لحد جديد على المشروع. مفيدة جدًا للـ dashboards والـ layouts المعقدة."

8.11 auto-fit + minmax() — Responsive Grid
🧠 الفكرة المبسطة

تخيلي رف فيه صناديق بحجم أدنى معين، والرف بيحاول يحط أكبر عدد ممكن منهم، وبعدين يمدّهم يملوا أي فراغ زيادة.

🔧 الصياغة التقنية
css
.cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 24px;
}

minmax(250px, 1fr) معناها: العمود ميقلش عن 250px، ويقدر يتمدد لحد 1fr لو فيه مساحة.

🎯 الربط

"ده الـ pattern الأشهر في أي مشروع حديث - بتاخدي responsive grid كامل من غير ما تكتبي ولا media query واحدة."

8.12 auto-fit vs auto-fill
🧠 الفكرة المبسطة

تخيلي رف فاضي وعندك 3 صناديق بس، لكن الرف يتسع لـ 6:

auto-fill: بيحجز أماكن لـ 6 صناديق (حتى لو 3 منهم فاضيين)، فالـ 3 صناديق الموجودين بيفضلوا بحجمهم الأصلي
auto-fit: بيشيل الأماكن الفاضية، فالـ 3 صناديق الموجودين بيتمددوا يملوا الرف كله
🔧 الصياغة التقنية
css
repeat(auto-fit, minmax(200px, 1fr));   /* الفراغات تتطوي، العناصر تتمدد */
repeat(auto-fill, minmax(200px, 1fr));  /* الفراغات تفضل موجودة كـ tracks فاضية */
🎯 الربط

"الفرق بس بيبان لما عدد العناصر أقل من المساحة المتاحة. لمعظم استخدامات الـ cards المتجاوبة، auto-fit هو المطلوب فعليًا."

8.13 Explicit vs Implicit Grid
🧠 الفكرة المبسطة

الـ Explicit هو اللي انتِ رسمتيه بنفسك بالمسطرة. الـ Implicit هو اللي المتصفح بيضيفه تلقائي لما العناصر تزيد عن اللي رسمتيه.

🔧 الصياغة التقنية
css
.container {
  display: grid;
  grid-template-columns: 1fr 1fr; /* Explicit: عمودين بس */
}
/* لو عندك 6 items، المتصفح هيضيف rows تلقائي = Implicit Grid */
التحكم في الـ Implicit tracks
css
.container {
  grid-auto-rows: 150px;    /* أي row تتضاف تلقائي هتبقى 150px */
  grid-auto-columns: 200px;
}
🎯 الربط

"لو مش حددتي rows كفاية للعناصر اللي عندك، متتفاجئيش - المتصفح مش بيرفض يعرض العنصر، هو بيضيف صف جديد تلقائي (implicit) بحجم افتراضي، واللي تقدري تتحكمي فيه بـ grid-auto-rows."

8.14 grid-auto-flow
🔧 الصياغة التقنية
css
grid-auto-flow: row;    /* Default - يملأ صف صف */
grid-auto-flow: column;  /* يملأ عمود عمود */
grid-auto-flow: dense;   /* يحاول يملأ الفراغات بعناصر تناسبها */
⚠️ تحذير Accessibility

زي order بالظبط في Flexbox - dense ممكن يخلي الترتيب البصري مختلف عن ترتيب الـ DOM، وده بيأثر على screen readers والـ keyboard navigation.

🎯 الربط

"متستخدميش dense عشوائيًا - هي مفيدة لملء الفراغات البصرية، لكنها بتفصل الترتيب البصري عن ترتيب المصدر، بالظبط زي مشكلة order في Flexbox."

8.15 Grid vs Flexbox
	Flexbox	Grid
البعد	1D (اتجاه واحد)	2D (صفوف وأعمدة مع بعض)
مناسب لـ	Navbar, مجموعة عناصر صغيرة	Layout كامل للصفحة
المنطق	Content-first (بيتبع حجم المحتوى)	Layout-first (بترسمي الهيكل الأول)
🎯 الربط

"القاعدة العملية: لو بتفكري 'عايزة أرتب عناصر في اتجاه واحد' → Flexbox. لو بتفكري 'عايزة أتحكم في صفوف وأعمدة مع بعض' → Grid. مش أحدهم بديل عن التاني - بيكملوا بعض، وغالبًا هتلاقي Grid للـ layout العام وFlexbox جوه المكونات الفردية."

🎯 أهم Interview Questions
1. الفرق بين Grid و Flexbox؟

Flexbox أحادي البعد، Grid ثنائي الأبعاد بيتحكم في صفوف وأعمدة مع بعض.

2. fr بتعني إيه؟

نصيب (fraction) من المساحة المتبقية جوه الـ container.

3. الفرق بين auto-fit وauto-fill؟

auto-fit بتطوي الـ tracks الفاضية والعناصر بتتمدد. auto-fill بتحافظ على الـ tracks الفاضية كمساحات محجوزة.

4. إيه الفرق بين justify-content وjustify-items في Grid؟

justify-items بتحاذي المحتوى جوه كل خلية على حدة. justify-content بتحاذي الـ Grid كله كـ كتلة واحدة جوه الـ container، وبس بتبان لو فيه مساحة فاضية زيادة عن حجم الـ Grid.

5. إيه الـ Implicit Grid؟

الـ tracks اللي المتصفح بيضيفها تلقائي لما عدد العناصر يزيد عن الـ Grid المحدد صراحة.

🧠 Senior Mental Model
                  CSS GRID
                     │
              display: grid
                     │
          ┌──────────┴──────────┐
          ↓                     ↓
      Columns                  Rows
          │                     │
 grid-template-columns   grid-template-rows
          │                     │
          └──────────┬──────────┘
                     ↓
                  Tracks
                     │
              ┌──────┴──────┐
              ↓             ↓
          Explicit       Implicit
             Grid           Grid
                              │
                       grid-auto-rows/columns

وبعدين طبقة تانية للمحاذاة:

justify-items / align-items  → محاذاة داخل كل خلية (كل العناصر)
justify-self / align-self     → محاذاة داخل خلية واحدة (استثناء)
justify-content / align-content → محاذاة الـ Grid كله جوه الـ container
أهم Pattern عملي في الفصل
css
.cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 24px;
}
📋 Chapter Summary — مراجعة سريعة
المفهوم	القاعدة السريعة
fr	نصيب من المساحة المتبقية
repeat(auto-fit, minmax())	Responsive grid من غير media queries
auto-fit vs auto-fill	fit بتطوي الفراغات، fill بتحافظ عليها
grid-column: span 2	امتداد عنصر لعدد خلايا
justify-items/align-items	محاذاة المحتوى جوه كل خلية
justify-self/align-self	استثناء لعنصر واحد
justify-content/align-content	محاذاة الـ Grid كله جوه الـ container
Explicit vs Implicit	معرّف يدويًا vs مُضاف تلقائي من المتصفح
Keywords للحفظ
Grid Container · Grid Item · fr · gap
grid-template-columns/rows · repeat() · minmax()
auto-fit · auto-fill · grid-area · grid-column · grid-row · span
justify-items · align-items · justify-self · align-self
justify-content · align-content
Explicit Grid · Implicit Grid · grid-auto-rows/columns · grid-auto-flow
🎤 جملتك النموذجية في المقابلة

"CSS Grid is a two-dimensional layout system that handles rows and columns simultaneously, unlike Flexbox's one-dimensional model. Beyond track sizing with fr and minmax(), Grid has its own alignment layer: justify-items/align-items position content within each cell, justify-self/align-self override that for a single item, and justify-content/align-content position the entire track grid within the container when there's leftover space. For responsive layouts, repeat(auto-fit, minmax(250px, 1fr)) eliminates the need for explicit breakpoints entirely."