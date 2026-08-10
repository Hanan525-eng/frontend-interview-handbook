# Chapter 2 — CSS Selectors


│   ├── Universal
│   ├── Type
│   ├── Class
│   ├── ID
│   ├── Attribute
│   ├── Descendant
│   ├── Child
│   ├── Adjacent Sibling
│   ├── General Sibling
│   ├── Pseudo-classes
│   └── Pseudo-elements

السؤال الاول
What is a CSS Selector?
الإجابة

الـ Selector هو الجزء المسؤول عن تحديد أي عناصر HTML هتتطبق عليها قاعدة الـ CSS.

لو فاكرة من الفصل الأول:
css

button {
  color: red;
}

button هنا هو الـ Selector - هو اللي بيقول للمتصفح "روح دور على كل عناصر الـ button في الـ DOM وطبّق عليهم اللي جاي".
ليه الموضوع ده مهم لمستوى Senior؟

لأن اختيار الـ Selector الغلط بيسبب مشكلتين أساسيتين:

    Specificity wars (هنشرحها بالتفصيل في فصل الـ Cascade القادم)
    Performance issues لو الـ selector معقد جدًا أو بيدور على شجرة الـ DOM كلها

فالموضوع مش مجرد "إزاي أستهدف عنصر" - هو كمان "إزاي أستهدفه بأقل تكلفة وأبسط طريقة".
2.2 Basic Selectors (المحددات الأساسية)
Universal Selector (*)

بيستهدف كل عنصر موجود في الصفحة، من غير استثناء.
css

* {
  margin: 0;
  padding: 0;
}

الاستخدام الشائع

غالبًا بتشوفيه في بداية أي مشروع كـ CSS Reset، عشان تشيلي الـ default margins/paddings اللي المتصفح بيحطها تلقائي.
تحذير Performance

الـ Universal selector بيتطبق على كل node في الـ DOM، فلو استخدمتيه بكثرة أو مع selectors معقدة (* div span) ده بيأثر على سرعة الـ rendering في صفحات كبيرة.
Type Selector (Element)

بيستهدف نوع الوسم نفسه، بغض النظر عن أي class أو id.
css

div {
  color: black;
}

p {
  line-height: 1.6;
}

كل الـ <div> وكل الـ <p> في الصفحة هياخدوا نفس التنسيق.
Class Selector (.)

بيستهدف أي عنصر عنده class معين. وده أكتر نوع بتستخدميه في الشغل اليومي.
css

.card {
  border: 1px solid #ddd;
  border-radius: 8px;
}

html

<div class="card">...</div>
<div class="card">...</div>

ليه Class هو الأكتر استخدامًا؟

    Reusable: نفس الـ class ممكن يتكرر على عناصر كتير
    Specificity متوسطة: مش عالية زي الـ ID (يعني سهل الـ override لو احتجتي)
    بيدعم الـ BEM methodology وكل الـ component-based architectures

ID Selector (#)

بيستهدف عنصر واحد فريد في الصفحة كلها.
css

#header {
  position: sticky;
  top: 0;
}

html

<header id="header">...</header>

نقطة مهمة للمقابلة

من الناحية التقنية، الـ HTML مش بيمنعك تكرري نفس الـ id على أكتر من عنصر - لكن ده invalid HTML وبيكسر أشياء زي:

    الـ document.getElementById() في JavaScript (بيرجع أول عنصر بس)
    الـ accessibility tools

Senior Tip

كتير من الـ Senior developers بيتجنبوا استخدام الـ ID في الـ CSS styling أصلاً (رغم استخدامه في الـ HTML لأغراض تانية زي الـ anchors أو JS hooks)، لأن الـ specificity بتاعته عالية جدًا وبتسبب مشاكل لما تيجي تعملي override بعدين.
2.3 Attribute Selectors (محددات السمات)

بتستهدف العناصر بناءً على وجود أو قيمة خاصية (attribute) معينة.
Existence Selector
css

[disabled] {
  opacity: 0.5;
}

بيستهدف أي عنصر عنده attribute اسمه disabled، بغض النظر عن قيمته.
Exact Value Selector
css

input[type="text"] {
  border: 1px solid blue;
}

[target="_blank"] {
  color: purple;
}

Advanced Attribute Operators (مستوى Senior)

فيه operators تانية مهمة جدًا وبتتسأل كتير في المقابلات:
css

/* يبدأ بـ */
[class^="btn-"] {
  padding: 8px 16px;
}
/* هيستهدف: btn-primary, btn-secondary, btn-large */

/* ينتهي بـ */
[class$="-large"] {
  font-size: 20px;
}
/* هيستهدف: btn-large, card-large */

/* يحتوي على */
[class*="nav"] {
  display: flex;
}
/* هيستهدف: navbar, main-nav, nav-item */

/* يساوي أو يبدأ بـ قيمة متبوعة بشرطة */
[lang|="en"] {
  font-family: 'Inter', sans-serif;
}
/* هيستهدف: lang="en" أو lang="en-US" لكن مش lang="english" */

استخدام عملي حقيقي

لو شغالة على مشروع فيه أيقونات SVG جوه ملفات كتير، ممكن تستخدمي:
css

img[src$=".svg"] {
  filter: grayscale(100%);
}

بدل ما تحطي class منفصل على كل صورة.
2.4 Combinators (محددات العلاقات)

دي بتوصف العلاقة بين عنصرين في شجرة الـ DOM.
Descendant Combinator (مسافة)

بيستهدف أي عنصر جوه العنصر الأب، مهما كان بعيد في التداخل.
css

div p {
  color: gray;
}

html

<div>
  <p>هتتلوّن</p>
  <section>
    <p>هتتلوّن برضه، حتى لو مش ابن مباشر</p>
  </section>
</div>

Child Combinator (>)

بيستهدف الأبناء المباشرين بس.
css

div > p {
  color: blue;
}

html

<div>
  <p>هتتلوّن</p>
  <section>
    <p>مش هتتلوّن - مش ابن مباشر للـ div</p>
  </section>
</div>

Adjacent Sibling Combinator (+)

بيستهدف العنصر الشقيق اللي يجي مباشرة بعده، وشرط يكونوا على نفس المستوى.
css

h1 + p {
  font-weight: bold;
}

html

<h1>العنوان</h1>
<p>دي هتبقى bold - أول فقرة بعد الـ h1 مباشرة</p>
<p>دي مش هتتأثر</p>

General Sibling Combinator (~)

بيستهدف كل الأشقاء اللي بعد العنصر (مش بس أول واحد).
css

h1 ~ p {
  color: green;
}

html

<h1>العنوان</h1>
<p>هتتلوّن</p>
<p>هتتلوّن برضه</p>
<p>وهي كمان</p>

جدول تلخيصي للـ Combinators
Combinator	الرمز	بيستهدف
Descendant	(space)	كل الأحفاد، مهما كان عمق التداخل
Child	>	الأبناء المباشرين بس
Adjacent Sibling	+	أول شقيق مباشر بعد العنصر
General Sibling	~	كل الأشقاء اللي بعد العنصر
2.5 Pseudo-classes & Pseudo-elements
Pseudo-classes (:)

بتستهدف حالة معينة للعنصر - مش جزء تاني منه، لكن حالة بيمر بيها.
css

a:hover {
  color: orange;
}

button:active {
  transform: scale(0.98);
}

input:focus {
  border-color: blue;
}

li:nth-child(2) {
  font-weight: bold;
}

Pseudo-elements (::)

بتستهدف جزء محدد من العنصر، وكأنك بتضيفي عنصر وهمي جواه.
css

p::first-letter {
  font-size: 2em;
  font-weight: bold;
}

p::first-line {
  color: gray;
}

.tooltip::before {
  content: "→ ";
}

🎯 فخ المقابلة الشهير

السؤال: "ما الفرق الجوهري بين الـ Pseudo-classes والـ Pseudo-elements؟ وهل فيه قاعدة تنظم كتابتهم؟"

الإجابة الصحيحة:

    الـ Pseudo-classes (:) بتوصف حالة العنصر - زي :hover, :active, :nth-child
    الـ Pseudo-elements (::) بتستهدف جزء من العنصر - زي ::before, ::after, ::first-line

القاعدة: في CSS3، اتفقوا يكتبوا الـ Pseudo-elements بـ :: (نقطتين) للتفرقة الواضحة بينهم وبين الـ Pseudo-classes، رغم إن المتصفحات لسه بتدعم النسخة القديمة بـ : واحدة (زي :before) للـ backward compatibility.
2.6 Specificity Comparison — مقارنة الوزن (تصحيح مهم)

جدول شائع بيتقال بشكل غلط إن الـ Pseudo-class وزنها "متوسط" مستقل. الحقيقة إن الوزن بيتحسب حسب فئة الـ selector مش نوعه:
فئة الـ Selector	يشمل	Specificity Weight
Inline style	style="..."	(1,0,0,0) — الأعلى
ID	#header	(0,1,0,0)
Class / Attribute / Pseudo-class	.card, [type="text"], :hover	(0,0,1,0) — نفس الوزن بالظبط
Element / Pseudo-element	div, ::before	(0,0,0,1) — نفس الوزن بالظبط
مثال عملي يوضح الفكرة
css

.btn:hover { color: red; }   /* Specificity: 0,0,2,0 */
button::before { content: "★"; } /* Specificity: 0,0,0,2 */

لاحظي إن :hover أضافت نفس وزن الـ .btn بالظبط (كلاهما 0,0,1,0)، و ::before أضافت نفس وزن الـ button بالظبط (كلاهما 0,0,0,1). دي نقطة بيقع فيها ناس كتير في المقابلات لما يفكروا إن الـ pseudo-class/element "درجة مستقلة" بين الـ class والـ element.
🎯 Interview Question
إيه الفرق في الـ Specificity بين #submit و .btn:hover؟

    #submit → ID selector → (0,1,0,0)
    .btn:hover → Class + Pseudo-class → (0,0,2,0) (كل واحدة بتحسب 0,0,1,0 فتتجمع)

النتيجة: #submit هيكسب دايمًا، لأن أي عدد من الـ classes/pseudo-classes مجتمعين برضه أقل من ID واحد بس. الـ ID مبيتقارنش بالعدد، بيتقارن بالـ "خانة" - يعني (0,1,0,0) أكبر من أي قيمة في خانة (0,0,x,x) مهما كبرت.
🎯 Senior Note

الغلطة الشائعة إن المطورين بيفتكروا إن اختيار الـ Selector مجرد "استهداف بصري". لكن على مستوى Senior، اختيارك للـ Selector بيأثر على 3 حاجات مع بعض:

Selector Choice
       ↓
   ┌───┴────┬─────────────┐
   ↓        ↓             ↓
Specificity  Reusability  Performance
   ↓        ↓             ↓
Cascade    Maintainability  Rendering Speed
Conflicts

القاعدة الذهبية اللي معظم الـ style guides الكبيرة (زي BEM) بتتبناها:

    "Prefer classes over IDs and deep nesting" — عشان تحافظي على specificity منخفضة وقابلة للـ override بسهولة.

📋 Chapter Summary — مراجعة سريعة
جدول شامل: كل أنواع الـ Selectors
النوع	الرمز/الصيغة	مثال	Specificity
Universal	*	* { }	(0,0,0,0)
Type	اسم الوسم	div { }	(0,0,0,1)
Class	.	.card { }	(0,0,1,0)
ID	#	#header { }	(0,1,0,0)
Attribute	[attr]	[type="text"]	(0,0,1,0)
Pseudo-class	:	:hover	(0,0,1,0)
Pseudo-element	::	::before	(0,0,0,1)
Descendant	space	div p	مجموع الطرفين
Child	>	div > p	مجموع الطرفين
Adjacent Sibling	+	h1 + p	مجموع الطرفين
General Sibling	~	h1 ~ p	مجموع الطرفين
🪤 فخ المقابلة الشهير

السؤال: "ما الفرق الجوهري بين الـ Pseudo-classes والـ Pseudo-elements؟"

الإجابة: Pseudo-classes بتوصف حالة العنصر (:hover)، وPseudo-elements بتستهدف جزء منه (::before). المعيار الحديث بيفرّق بينهم بعدد النقط (: مقابل ::).
Keywords للحفظ

Selector · Universal · Type/Element · Class · ID
Attribute Selector · Combinator · Descendant · Child
Adjacent Sibling · General Sibling
Pseudo-class · Pseudo-element · Specificity Weight
DOM Tree · State

🎤 جملتك النموذجية في المقابلة

    "I distinguish between pseudo-classes and pseudo-elements based on what they target: pseudo-classes represent a state of an element, like :hover or :nth-child, while pseudo-elements target a specific part of an element, such as ::before or ::after. Both carry the same specificity weight as classes and elements respectively — a common misconception is treating them as a separate specificity tier, which they are not."
