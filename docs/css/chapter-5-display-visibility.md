Chapter 5 — Display & Visibility 

:

│   ├── block
│   ├── inline
│   ├── inline-block
│   ├── none
│   ├── visibility
│   └── overflow
السؤال الاول
What does display really control?
🧠 الفكرة المبسطة

تخيلي صالة سينما، والعناصر هي الناس اللي بتحاول تقعد فيها. خاصية display مش بس بتحدد "الشخص ظاهر ولا لأ" - هي بتحدد طريقة قعدته وتعامله مع اللي حواليه.

🔧 الصياغة التقنية

display بيحدد إزاي العنصر بيشارك في الـ layout flow - مش مجرد ظاهر أو مخفي.

display
│
├── block         → new line / يحجز السطر كله
├── inline        → يشارك في نفس السطر
├── inline-block  → في السطر، لكن بحجم متحكم فيه
└── none          → مالوش layout box خالص
🎯 الربط

"الغلطة الشائعة إن المطور يفتكر display بس بيتحكم في الشكل البصري. في الحقيقة هو بيحدد مشاركة العنصر في التدفق الطبيعي للصفحة (Normal Flow) بالكامل - وده أساس فهم باقي الفصل."

5.2 display: block
🧠 الفكرة المبسطة

تخيلي واحد دخل السينما وحجز الصف كله لحسابه، حتى لو هو رفيع وممكن يقعد جنبه خمسة. رافض تمامًا إن حد يشاركه نفس السطر.

🔧 الصياغة التقنية
css
.card {
  display: block;
  width: 300px;
}

خصائصه:

يبدأ في سطر جديد
ياخد عرض المساحة المتاحة (100%) افتراضيًا
بيقبل width, height, margin, padding بشكل كامل

أمثلة افتراضية: <div>, <p>, <h1>, <section>

┌──────────────────────────────┐
│ Element                      │
└──────────────────────────────┘
┌──────────────────────────────┐
│ Next Element                 │
└──────────────────────────────┘
🎯 الربط

"أي عنصر block بيتصرف زي شخص أناني في الصف - بياخد السطر كله لوحده حتى لو مش محتاجه فعليًا."

5.3 display: inline
🧠 الفكرة المبسطة

تخيلي كلمة مكتوبة جوه سطر في كتاب. الكلمة بتاخد مساحة على قد حروفها بالظبط، والكلمة اللي بعدها بتيجي جنبها عادي في نفس السطر.

🔧 الصياغة التقنية
css
span {
  display: inline;
}
html
<p>Hello <span>world</span>!</p>

الـ span مش بيبدأ سطر جديد.

⚠️ نقطة مهمة جدًا
css
span {
  width: 300px;   /* المتصفح هيتجاهلها تمامًا */
  height: 100px;  /* هيتجاهلها كمان */
}

عناصر الـ inline مش بتستجيب للـ width/height بنفس طريقة الـ block. وكمان الـ margin/padding الرأسي (فوق وتحت) مش بيزق العناصر اللي فوق وتحت.

🎯 الربط

"الكلمة في السطر مش بتاخد 'حيز إضافي' حواليها لتزق باقي الكلام - هي بتاخد مساحتها بالظبط بس. ده أساس ليه الـ inline elements بترفض الـ width/height."

5.4 display: inline-block
🧠 الفكرة المبسطة

تخيلي علبة عصير صغيرة على صينية - تقدر تحط علبة تانية جنبها (زي الـ inline)، لكن في نفس الوقت العلبة ليها حجم ثابت ومحدد (زي الـ block).

🔧 الصياغة التقنية
css
.button {
  display: inline-block;
  width: 150px;
  padding: 10px;
}
html
<a class="button">Login</a><a class="button">Register</a>
┌───────────┐  ┌───────────┐
│   Login   │  │ Register  │
└───────────┘  └───────────┘
🎯 الربط

"inline-block هو الهجين - بياخد أحسن ما في العالمين: يقعد جنب زمايله زي inline، لكن بيقبل width/height/margin/padding زي block."

🪤 فخ المقابلة الشهير (الأخطر في الفصل)

السؤال: "لو عندك زرارين display: inline-block كل واحد width: 50%، ليه بيكسروا وينزلوا سطر جديد رغم إن 50% + 50% = 100%؟"

الفخ: الظن إن السبب padding أو border، والدخول في تجربة box-sizing من غير فايدة.

الإجابة الصحيحة: السبب هو الـ White Space بين الوسمين في كود الـ HTML نفسه (المسافة أو الـ Enter بين </button> و<button>). الـ inline-block بيعامل المسافة دي كأنها حرف مسافة حقيقي (بوزن ~4px تقريبًا)، فيبقى المجموع الفعلي 50% + 50% + 4px وده بيتجاوز 100%.

الحلول:

html
<!-- 1. إلزاق الوسوم في بعض في الكود -->
<button>A</button><button>B</button>

<!-- 2. أو صفر الـ font-size على الأب -->
css
.container { font-size: 0; }
<!-- 3. الأفضل حديثًا: استخدام Flexbox بدل inline-block للـ layout -->
css
.container { display: flex; }
5.5 Block vs Inline vs Inline-block
الخاصية	Block	Inline	Inline-block
يبدأ سطرًا جديدًا	✅	❌	❌
بجانب عناصر أخرى	❌	✅	✅
width/height	✅	❌	✅
Padding	✅	✅ (أفقي بس بيزق)	✅
5.6 display: none
🧠 الفكرة المبسطة

تخيلي واحد قام من الكرسي ومشى بحاجته كلها. الكرسي بقى فاضي تمامًا، والشخص اللي وراه اتقدم وأخد مكانه. مفيش أي أثر إنه كان موجود أصلاً.

🔧 الصياغة التقنية
css
.modal {
  display: none;
}

العنصر بيتشال بالكامل من الـ layout tree - مش مجرد "مخفي بصريًا".

قبل:              بعد (B لها display:none):
Element A         Element A
Element B         Element C
Element C
🎯 الربط

"display: none مش 'اخفاء بصري' - هو 'إزالة كاملة من شجرة الـ layout'. الفرق ده جوهري وأساس السؤال الجاي."

5.7 visibility: hidden
🧠 الفكرة المبسطة

تخيلي واحد لابس طاقية إخفاء وهو قاعد على كرسيه. مش شايفاه، لكنه لسه قاعد فعليًا ومحدش تاني يقدر ياخد مكانه.

🔧 الصياغة التقنية
css
.element {
  visibility: hidden;
}
قبل:              بعد (B لها visibility:hidden):
┌───┐              ┌───┐
│ A │              │ A │
└───┘              └───┘
┌───┐              
│ B │                (مساحة فاضية محجوزة)
└───┘              
┌───┐              ┌───┐
│ C │              │ C │
└───┘              └───┘

المساحة بتفضل محجوزة، بس المحتوى مش ظاهر.

🎯 الربط

"العنصر لسه 'موجود فعليًا' في الصفحة وشاغل مكانه - بس عين المستخدم مش بتشوفه. ده الفرق الجوهري عن display:none."

5.8 display: none vs visibility: hidden vs opacity: 0
🧠 الفكرة المبسطة
display: none = الشخص مشى وسايب المكان خالص
visibility: hidden = لابس طاقية إخفاء وقاعد
opacity: 0 = بقى شفاف جدًا، لكن لسه ممكن تلمسيه فعليًا
🔧 الصياغة التقنية
	display: none	visibility: hidden	opacity: 0
المساحة في الصفحة	تختفي (0×0)	محجوزة	محجوزة
قابل للضغط/التفاعل (Events)	❌	❌	✅ لسه قابل للضغط!
مناسب للـ Animation	❌	صعب	✅ مثالي
نوع التحديث	Reflow	Repaint	Repaint (composite)
🎯 الربط

"النقطة الأهم عمليًا: opacity: 0 بيخلي العنصر شفاف بصريًا بس بيسيبه قابل للضغط عليه (clickable) - ده سبب شائع لباجات UX (زرار 'مختفي' بس المستخدم بيقدر يدوسه بالغلط). لو محتاجة إخفاء بصري + منع التفاعل مع animation سلس، الحل الاحترافي هو الجمع بين الاتنين:"

css
.hidden-animated {
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.3s;
}
طريقة سهلة للحفظ
display: none      → No box / no layout space / no interaction
visibility: hidden  → Box exists / space remains / no interaction
opacity: 0           → Box exists / space remains / interaction STILL works
5.9 overflow
🧠 الفكرة المبسطة

معاكي شنطة سفر بمقاس ثابت، وحاولتي تحشري فيها هدوم أكتر من مساحتها. الهدوم هتبدأ "تدلق" برة الشنطة. خاصية overflow هي طريقتك تتعاملي مع الهدوم المدلوقة دي.

🔧 الصياغة التقنية
css
.card {
  width: 200px;
  height: 100px;
  overflow: hidden;
}
القيم الأربعة
القيمة	🧠 التشبيه	🔧 السلوك
visible (Default)	الهدوم بتدلق وتغطي العفش اللي حواليها	المحتوى بيظهر برة حدود العنصر عادي
hidden	تقصي الهدوم الزايدة وترميها	أي محتوى زايد بيتقص ويختفي
scroll	تركّبي سوستة للشنطة على طول	Scrollbar موجود دايمًا، حتى لو مش محتاجاه
auto	سوستة تظهر بس لو محتاجاها	Scrollbar بيظهر بس لو المحتوى فعلاً أكبر من المساحة
🎯 الربط

"auto هي الأكتر استخدامًا عمليًا لأنها 'ذكية' - بتقرر هي نفسها لو محتاجة تضيف scroll ولا لأ، عكس scroll اللي بتفرض الشريط دايمًا حتى لو مش لازم."

5.10 overflow-x و overflow-y
🔧 الصياغة التقنية
css
.container {
  overflow-x: auto;
  overflow-y: hidden;
}
🎯 الربط

"الاستخدام العملي الأشهر: جدول كبير على شاشة موبايل - تسمحي بالـ scroll الأفقي بس وتمنعي أي تمدد رأسي غريب."

css
.table-container {
  overflow-x: auto;
}
استخدامات حقيقية شائعة
css
/* Tabs بتتمرر أفقيًا */
.tabs { overflow-x: auto; }

/* قص الصور جوه container بحواف مدورة */
.image-wrapper { overflow: hidden; }

/* Modal body قابل للتمرير رأسيًا */
.modal-body { overflow-y: auto; }
🎯 Interview Questions
1. الفرق بين display: none و visibility: hidden؟

display: none بيشيل العنصر من الـ layout بالكامل ويعمل reflow. visibility: hidden بيخفيه بصريًا بس بيسيب مساحته ويعمل repaint بس.

2. الفرق بين block، inline، وinline-block؟

Block بيبدأ سطر جديد ويقبل width/height. Inline بيشارك في نفس السطر ومبيستجيبش لـ width/height. Inline-block بيفضل في السطر لكن بيقبل تحكم كامل في الأبعاد.

3. overflow: hidden بتعمل إيه بالظبط؟

بتقص أي محتوى بيتجاوز حدود الـ overflow area بتاعت العنصر.

4. امتى تستخدمي opacity: 0 بدل visibility: hidden؟

لما محتاجة animation سلس (transition)، لأن opacity قابلة للـ transition بسهولة عكس visibility. لازم تضيفي pointer-events: none معاها عشان تمنعي التفاعل.

🧠 Senior Mental Model

متفتكريش display كـ "ظاهر / مش ظاهر" بس. فكري فيه كـ مشاركة العنصر في الـ layout:

display
│
├── block          → new line / block-level layout
├── inline          → participates in inline formatting
├── inline-block     → inline-level + controllable dimensions
└── none              → no layout box at all

وافصليه عن:

visibility  → hidden but space remains
opacity     → hidden but space AND interaction remain
overflow    → controls content outside the box

السؤال اللي المفروض تعرفي تجاوبيه من غير حفظ:

"لو أخفيت العنصر، عايزة مساحته تختفي؟ عايزة يفضل قابل للتفاعل؟"

عايزة المساحة تختفي؟	عايزة يفضل قابل للتفاعل؟	الحل
نعم	-	display: none
لأ	لأ	visibility: hidden
لأ	نعم (نادر)	opacity: 0 + احترسي من pointer-events
📋 Chapter Summary — مراجعة سريعة
المفهوم	القاعدة السريعة
block	سطر جديد، يقبل كل الأبعاد
inline	نفس السطر، مايقبلش width/height
inline-block	نفس السطر + يقبل الأبعاد
display: none	إزالة كاملة (مساحة + تفاعل)
visibility: hidden	مخفي بصريًا، المساحة محجوزة
opacity: 0	شفاف، المساحة والتفاعل لسه موجودين
overflow: hidden	قص المحتوى الزايد
overflow: auto	scroll بس لو محتاج
فخ inline-block	مسافات الـ HTML بتتحسب كـ ~4px
Keywords للحفظ
block · inline · inline-block · display: none
visibility · opacity · pointer-events
overflow · overflow-x · overflow-y
Reflow · Repaint · Normal Flow
🎤 جملتك النموذجية في المقابلة

"The key difference between display: none and visibility: hidden is their impact on document flow: display: none completely removes the element and triggers a reflow, while visibility: hidden preserves its space and only triggers a repaint. For smooth visual transitions where I still want to control interactivity, I combine opacity: 0 with pointer-events: none rather than relying on visibility alone."