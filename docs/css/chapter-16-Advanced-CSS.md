Chapter 16 — Advanced CSS 

│   ├── Logical Properties
│   ├── CSS Nesting
│   ├── Container Queries
│   ├── Cascade Layers
│   ├── :is()
│   ├── :where()
│   ├── :has()
│   └── Modern CSS
السؤال الاول
Logical Properties
🧠 الفكرة المبسطة

تخيلي بتوصفي مكان حاجة بكلمة "شمال" - ده وصف ثابت مش بيتغيّر. لكن لو وصفتيها بـ "بداية الصف"، الوصف ده بيتغيّر معنى حسب اتجاه القراءة (من الشمال في الإنجليزي، من اليمين في العربي).

🔧 الصياغة التقنية
css
.card {
  padding-inline: 24px;  /* بدل padding-left + padding-right */
  margin-inline-start: 16px; /* بدل margin-left */
}
Physical	Logical
margin-left	margin-inline-start
top/bottom	inset-block-start/inset-block-end
width/height	inline-size/block-size
🎯 الربط

"margin-inline-start: 16px بتتكيف تلقائيًا مع اتجاه الكتابة - في LTR تبقى شمال، في RTL تبقى يمين، من غير ما تكتبي أي override يدوي. التفصيل الكامل هنشوفه في فصل RTL القادم."

🎨 في Figma

⚠️ محتاجة تأكيد: Figma بتدعم "Auto layout" مع خاصية اتجاه (LTR/RTL) في بعض الإصدارات الحديثة، لكن آلية الـ "logical spacing" بدقة CSS مش نفس المفهوم بالظبط - يفضل تتأكدي من أحدث سلوك للأداة لو ده مهم لشغلك.

16.2 CSS Nesting
🔧 الصياغة التقنية
css
.card {
  padding: 24px;

  .title {
    font-size: 20px;
  }

  &:hover {
    transform: translateY(-2px);
  }
}
⚠️ فخ خطير: & مش اختيارية زي ما بتبدو
css
.button {
  &:hover { color: red; }   /* ✅ يعادل: .button:hover */
}

.button {
  :hover { color: red; }     /* ❌ يعادل: .button :hover (descendant!) */
}
🎯 الربط

"الفرق ده مش تفصيلة شكلية - .button:hover بتستهدف الزرار نفسه وقت الـ hover، بينما .button :hover (بمسافة) بتستهدف أي عنصر تاني جوه الزرار وقت ما هو نفسه في حالة hover - سلوك مختلف تمامًا. القاعدة الآمنة: أي وقت بتكتبي pseudo-class أو pseudo-element جوه nesting، حطي & قبلها على طول، متعتمديش على الـ browser يفهم قصدك."

⚠️ تحذير Senior آخر: عمق الـ Nesting
css
/* ❌ صعب القراءة، مرتبط جدًا بهيكل الـ DOM */
.page .section .card .content .title span { }

القاعدة: استخدمي الـ Nesting عشان تحسّني الـ readability، مش عشان تعيدي بناء شجرة selectors عميقة الارتباط بالـ DOM.

16.3 Container Queries
🔧 الصياغة التقنية
css
.card-wrapper {
  container-type: inline-size;
}
@container (min-width: 500px) {
  .card { display: grid; grid-template-columns: 120px 1fr; }
}
🎯 الربط

"الفرق الجوهري: Media Query = responsive للصفحة كلها. Container Query = responsive للمكوّن نفسه، بغض النظر عن حجم الشاشة. نفس الـ Card ممكن تتصرف مختلف تمامًا لو حطيتيها جوه sidebar ضيقة أو main content واسعة."

	Media Query	Container Query
المرجع	الـ viewport	الـ container
مناسب لـ	تخطيط الصفحة العام	Reusable components
16.4 Cascade Layers — @layer
🔧 الصياغة التقنية
css
@layer reset, base, components, utilities;

@layer reset { * { box-sizing: border-box; } }
@layer components { .button { padding: 8px 16px; } }
🎯 الربط

"@layer بتديكي تحكم صريح في ترتيب أولوية مجموعات الـ CSS، بدل ما تعتمدي بس على الـ Specificity العادية. الترتيب اللي بتكتبيه في @layer reset, base, components, utilities; هو نفسه ترتيب الأولوية - آخر layer مكتوبة بتكسب لو فيه تعارض، بغض النظر عن specificity القاعدة نفسها جوه كل layer."

🆕 نقطة Senior حرجة: الـ CSS "من غير layer" بتكسب دايمًا
css
@layer reset, base, components;

@layer components {
  .button { color: blue; } /* جوه layer عالي الأولوية */
}

/* CSS عادي من غير @layer خالص */
.button { color: red; } /* 🏆 ده اللي هيكسب! */

السبب: أي قاعدة CSS مش مكتوبة جوه أي @layer بتتحط تلقائيًا في طبقة أعلى من كل الـ layers المسمّاة، بغض النظر عن ترتيبهم. ده منطقي لو فكرتي فيه كـ "الكود اللي انتِ كتبتيه يدويًا آخر حاجة بيغلب أي نظام طبقات منظم قبله" - لكنه بيفاجئ ناس كتير أول مرة يستخدموا @layer.

🎯 الربط

"لو مشروعك بيستخدم @layer وفجأة قاعدة عادية 'من برة النظام' كسبت رغم إنها منطقيًا المفروض تكون أضعف، السبب غالبًا إنها مش متحطوطة جوه أي layer - والـ CSS الـ unlayered دايمًا فوق أي layer معرّف."

16.5 :is() و :where()
🔧 الصياغة التقنية
css
/* :is() - بتاخد أعلى specificity من جوّاها */
.card :is(h1, h2, h3) { margin-block-end: 16px; }
:is(.card, #dashboard) { color: red; } /* specificity = زي #dashboard (الأعلى) */

/* :where() - specificity = صفر دايمًا */
:where(.card h2) { font-size: 20px; }
	:is()	:where()
Specificity	أعلى selector جواها	صفر دايمًا
الاستخدام المناسب	selectors ليها وزن مقصود	Base/default styles سهلة الـ override
🎯 الربط

"استخدمي :where() لما بتكتبي base styles لـ design system وعايزة أي component تاني بعدين يقدر يعمل override من غير ما يحتاج يرفع specificity بتاعه أصلًا."

16.6 :has()
🔧 الصياغة التقنية
css
.card:has(.badge) { border-color: blue; }
.field:has(.error) { border-color: red; }
.form-group:has(input:invalid) { color: red; }
🎯 الربط

":has() بتخليكي تستهدفي الأب بناءً على وجود ابن معين - حاجة كانت مستحيلة في CSS من غير JavaScript أو class إضافية زي has-error."

⚠️ تحذير أداء

استخدام :has() بشكل عام جدًا (زي body:has(*)) أو على عناصر بتتغيّر كتير أثناء الـ scroll بيجبر المتصفح يعمل فحص عكسي لشجرة الـ DOM بشكل متكرر، وده ممكن يسبب تقطيع بصري. القاعدة الآمنة: حدّدي النطاق قد الإمكان (.card:has(.card-media) بدل selectors واسعة جدًا).

16.7 @property
🔧 الصياغة التقنية
css
@property --angle {
  syntax: "<angle>";
  inherits: false;
  initial-value: 0deg;
}
🎯 الربط

"فاكرة فصل الـ Variables؟ ده بالظبط اللي بيحل مشكلة إن الـ custom properties العادية بيتعامل معاها المتصفح كـ نص عادي - @property بتديها نوع حقيقي، وده بيخلي الـ animation عليها سلس."

16.8 @scope
🔧 الصياغة التقنية
css
@scope (.card) {
  h2 { font-size: 20px; }
  p { color: gray; }
}
🎯 الربط

"بدل ما تكتبي .card h2 صريح، @scope بتخلي القواعد دي مربوطة بـ 'داخل نطاق .card' كمفهوم، وده بيقلل التداخل غير المقصود بين أجزاء مختلفة من الـ UI. لكنها أداة إضافية للتنظيم، مش بديل كامل عن CSS Modules أو BEM."

🎯 Senior Decision Map
المشكلة	الأداة
RTL/LTR-friendly CSS	Logical Properties
Component يتغير حسب مساحته	Container Queries
تنظيم الـ Cascade	@layer (احذري: unlayered CSS بيكسب دايمًا)
تجميع selectors مع الحفاظ على وزنهم	:is()
تجميع selectors بدون أي وزن	:where()
اختيار أب بناءً على ابن	:has() (باحتراس من الأداء)
Custom Property قابلة للـ animation	@property
تحديد نطاق CSS	@scope
🎤 Senior Interview Questions
1. الفرق بين :is() و:where()؟

:is() بتاخد أعلى specificity من جوّاها، :where() دايمًا صفر.

2. .button { :hover {} } بتعمل إيه بالظبط؟

دي مش .button:hover - دي .button :hover (descendant combinator) وبتستهدف أي عنصر جوه الزرار في حالة hover، مش الزرار نفسه. لازم &:hover عشان تستهدفي الزرار.

3. لو عندك @layer معرّفة، وقاعدة CSS عادية من برة أي layer - مين بيكسب؟

القاعدة اللي من برة أي @layer بتكسب دايمًا، بغض النظر عن ترتيب الـ layers - الـ unlayered CSS أعلى أولوية من أي layer معرّف.

4. إيه خطورة :has() لو استخدمناها بشكل عام جدًا؟

بتجبر المتصفح على فحص عكسي متكرر لشجرة الـ DOM، وده ممكن يسبب مشاكل أداء لو استخدمت على نطاق واسع جدًا أو على عناصر بتتغيّر كتير.

5. الفرق بين Media Query وContainer Query؟

Media بتعتمد على الـ viewport، Container بتعتمد على حجم الـ container نفسه.

🧠 الخلاصة النهائية
Advanced CSS
│
├── Logical Properties  → Direction-aware
├── CSS Nesting          → احذري & قبل pseudo-classes!
├── Container Queries     → Component-level responsiveness
├── @layer                → احذري: unlayered = أعلى أولوية دايمًا
├── :is() / :where()      → Grouping مع/من غير specificity
├── :has()                 → Parent selector (احذري الأداء)
├── @property               → Typed custom properties
└── @scope                   → CSS boundaries
📋 Chapter Summary — مراجعة سريعة
الأداة	القاعدة السريعة
Logical Properties	inline/block بدل left/right
CSS Nesting	لازم & قبل pseudo-class، وإلا descendant غلط
Container Queries	container-type: inline-size + @container
@layer	ترتيب الكتابة = أولوية، لكن unlayered CSS يكسب الكل
:is()	specificity = أعلى واحد جواها
:where()	specificity = صفر
:has()	اختيار أب بناءً على ابن (احذري الأداء)
@property	typed custom property، قابلة للـ animation
@scope	حدود لتطبيق CSS
Keywords للحفظ
Logical Properties · inline-start/end · block-start/end
CSS Nesting · & (ampersand) · descendant combinator trap
Container Queries · container-type
@layer · unlayered CSS priority
:is() · :where() · :has()
@property · @scope
🎤 جملتك النموذجية في المقابلة

"Modern CSS gives us native tools that used to require JavaScript or preprocessors — Logical Properties for direction-aware layouts, :has() as a real parent selector, and @layer for explicit cascade control. One nesting gotcha worth knowing: omitting & before a pseudo-class inside nesting creates an unintended descendant selector instead of a compound one. And with @layer, unlayered CSS always wins over any layered rule, regardless of layer order — a counterintuitive but important detail." 
