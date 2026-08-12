Chapter 6 — Positioning 

│   ├── static
│   ├── relative
│   ├── absolute
│   ├── fixed
│   ├── sticky
│   ├── containing block
│   └── z-index
السؤال الاول
What does position actually control?
🧠 الفكرة المبسطة

position هو "GPS العنصر" - بيحدد هل العنصر ماشي في الطابور الطبيعي للصفحة، ولا خارج منه وبيتحدد مكانه بمرجع تاني تمامًا.

🔧 الصياغة التقنية

القيم الأساسية:

static · relative · absolute · fixed · sticky

خصائص top/right/bottom/left والـ z-index بتشتغل بس لو الـ position مش static.

🎯 الربط

"عشان تفهمي absolute وfixed بمستوى Senior، لازم تفهمي الأول مفهوم أساسي: Containing Block - مين المرجع اللي بيتحسب عليه مكان العنصر."

6.2 position: static
🧠 الفكرة المبسطة

شخص واقف في طابور بالترتيب بالظبط. مكان ما الطابور يوديه هيقف، ومش بيستجيب لأي أمر حركة جانبي.

🔧 الصياغة التقنية
css
.box {
  position: static;  /* Default */
  top: 20px;  /* هتتجاهل تمامًا */
}

العنصر بيفضل في Normal Flow، ومينفعش تحركيه بـ top/right/bottom/left.

🎯 الربط

"القيمة الافتراضية لكل عنصر. من غيرها، مفيش أي خاصية تحريك هتشتغل خالص."

6.3 position: relative
🧠 الفكرة المبسطة

شخص واقف في الطابور، مدّ إيده أو مال خطوتين لليمين. هو اتحرك فعليًا بصريًا، لكن مكانه في الطابور لسه محجوز - محدش تاني يقدر ياخده.

🔧 الصياغة التقنية
css
.box {
  position: relative;
  top: 20px;
  left: 10px;
}

العنصر بيفضل في Normal Flow حتى لو اتحرك بصريًا - العناصر التانية بتتعامل معاه وكأنه لسه في مكانه الأصلي.

أهم استخدام لـ relative (مش بس التحريك)
css
.card {
  position: relative;  /* بيبقى Containing Block */
}
.badge {
  position: absolute;
  top: 10px;
  right: 10px;
}
🎯 الربط

"الاستخدام الحقيقي الأشهر لـ relative مش تحريك العنصر - هو خلقه لـ Containing Block لأي عنصر absolute جواه. ده Pattern موجود فعليًا في مشاريعك زي الـ .wf-node والـ .perm-disabled-btn اللي بتستخدمي فيهم relative كحاوية لعناصر absolute بداخلها."

6.4 position: absolute
🧠 الفكرة المبسطة

طائرة درون خرجت من المبنى بالكامل وطايرة في الجو - مش ملتزمة بطابور الأرض، وبتتحرك بالنسبة لأقرب سور مبنى محيط بيها.

🔧 الصياغة التقنية
css
.element {
  position: absolute;
  top: 10px;
  right: 10px;
}

العنصر بيخرج تمامًا من Normal Flow - العناصر التانية معاملوش ليه أي مساحة.

🎯 الربط

"السؤال الأهم مش 'العنصر فين' - السؤال هو: Absolute relative to what؟ الإجابة: أقرب ancestor بينشئ Containing Block مناسب - مش بالضرورة الأب المباشر."

6.5 Containing Block — أهم مفهوم في الفصل
🧠 الفكرة المبسطة

فكريها كـ "نقطة الصفر" اللي المتصفح بيحسب منها إحداثيات top/right/bottom/left. مش بالضرورة أقرب أب - هي أقرب أب مؤهل يبقى نقطة صفر.

🔧 الصياغة التقنية
css
.parent {
  position: relative;
}
.child {
  position: absolute;
  top: 0;
  right: 0;
}

هنا top: 0; right: 0; = أعلى يمين .parent بالظبط.

ماذا لو مفيش أب مؤهل؟
html
<div class="parent">
  <div class="child"></div>
</div>
css
.child { position: absolute; top: 0; right: 0; }
/* .parent مالهاش position خالص */

المتصفح هيكمل يدور لفوق في شجرة الـ DOM لحد ما يلاقي أب مؤهل، ولو مفيش، هيوصل لـ <html> نفسها.

🎯 الربط

"القاعدة الشائعة 'absolute بتاخد مكانها من الأب المباشر' غلط تمامًا. الصح: 'absolute بتاخد مكانها من أقرب أب مؤهل يبقى Containing Block'."

🆕 نقطة Senior ناقصة غالبًا: transform بتعمل Containing Block كمان!

مش بس position هو اللي بيأهّل الأب يبقى Containing Block. أي أب عليه واحدة من الخصائص دي بيبقى مؤهل تلقائيًا حتى لو مالوش position خالص:

css
.parent {
  transform: translateZ(0);   /* أو أي transform تاني */
  /* أو: filter: blur(0);     */
  /* أو: will-change: transform; */
  /* أو: perspective: 1000px; */
}

ده باج شائع جدًا وواقعي: بتحطي position: fixed على مودال متوقّعة إنها تتثبت بالنسبة للـ viewport، لكن لو أي أب فوقها عليه transform (حتى المستخدمة للـ performance زي translateZ(0))، الـ fixed هتتصرف زي absolute وهتتموضع بالنسبة للأب ده مش الشاشة كلها.

6.6 position: fixed
🧠 الفكرة المبسطة

استيكر ملصوق على شاشة نظارتك - مهما مشيتي أو طلعتي سلم (Scroll)، الاستيكر ثابت قدام عينك في نفس النقطة بالظبط.

🔧 الصياغة التقنية
css
.help-button {
  position: fixed;
  right: 20px;
  bottom: 20px;
}

بيتموضع بالنسبة للـ viewport (في الحالة العادية، من غير الاستثناء اللي فوق)، وبيفضل ثابت أثناء الـ scroll.

استخدامات حقيقية: Floating action button, Chat button, Cookie banner, Fixed nav, Back-to-top button

🎯 الربط

"لاحظي 'في الحالة المعتادة' - فاكرة الاستثناء اللي فات (transform على أب)؟ ده بالظبط اللي بيكسر السلوك المتوقع لـ fixed."

6.7 absolute vs fixed
	Absolute	Fixed
Normal Flow	❌	❌
المرجع المعتاد	Containing Block	Viewport
يتحرك مع الـ scroll	✅ (مع الـ containing context)	❌ (ثابت)
6.8 position: sticky
🧠 الفكرة المبسطة

شخص ماشي معاكي في الشارع عادي (زي relative)، لكن بمجرد ما توصلوا نقطة معينة، بيمسك في السور ويفضل ثابت طول ما انتِ مكملة تمشي جوه الشارع ده، وبمجرد ما الشارع يخلص بيمشي معاكي تاني.

🔧 الصياغة التقنية
css
.header {
  position: sticky;
  top: 0;
}

بيبدأ في Normal Flow، وعند الوصول لـ threshold محدد (top: 0)، بيبقى sticky أثناء الـ scroll جوه حدود الـ scrolling container بتاعه.

⚠️ ليه لازم top أو threshold؟
css
.header {
  position: sticky;  /* من غير top، مش هيشتغل زي المتوقع! */
}

لازم دايمًا تحددي top (أو bottom/left/right) عشان تقولي للمتصفح "التصقي عند النقطة دي بالظبط".

🎯 الربط

"الـ sticky هجين - بيبدأ relative وبيتحول fixed مؤقتًا، لكنه محبوس جوه حدود أبوه. لو الأب طلع من الشاشة، الـ sticky بيطلع معاه."

6.9 sticky vs fixed
	Sticky	Fixed
يبدأ في Normal Flow	✅	❌
مرتبط بـ scrolling context	✅	عادةً الـ viewport
بيحتفظ بمكانه الأصلي	✅	❌

استخدامات شائعة: Sidebar جوه Dashboard، Header جوه Table

6.10 z-index
🧠 الفكرة المبسطة

طبقات ورق كوتشينة فوق بعض - اللي رقمه أعلى بيغطي اللي رقمه أقل.

🔧 الصياغة التقنية
css
.modal { position: fixed; z-index: 1000; }
.dropdown { position: absolute; z-index: 100; }

المودال (1000) هيظهر فوق الـ dropdown (100) لو اتداخلوا.

⚠️ z-index مش شغالة على أي عنصر
z-index بتشتغل على:
- positioned elements (position غير static)
- flex items
- grid items
🎯 الربط

"لا تحفظي 'z-index بتشتغل بس مع position' - ده تبسيط قديم. هي كمان بتشتغل على flex/grid items حتى من غير position صريح."

6.11 Stacking Context — الجزء الحقيقي لمستوى Senior
🧠 الفكرة المبسطة

تخيلي كل شركة عندها ميزانية منفصلة تمامًا عن الشركة التانية. موظف عنده راتب مليون في شركة صغيرة، برضه مش هيقدر "يشتري" شركة تانية أكبر منها - لأن الميزانيتين في عالمين منفصلين. الـ Stacking Context بالظبط كده: z-index: 9999 جوه context معين، برضه مش هيقدر "يخرج" ويغلب context تاني أعلى منه.

🔧 الصياغة التقنية

وجود z-index: 9999 مش ضمانة إن العنصر هيفوز دايمًا. لو الأب بتاعه جوه Stacking Context منخفض، والعنصر التاني جوه Stacking Context أعلى، الـ 9999 مش هيعدّي.

🆕 إيه بالظبط اللي بيعمل Stacking Context جديد؟

دي القائمة اللي غالبًا مش موجودة كاملة في أي مرجع - وهي أساس تشخيص "ليه z-index بتاعي مش شغال":

css
/* أي واحدة من الخصائص دي على الأب = Stacking Context جديد */
position: relative/absolute/fixed/sticky  + z-index (مش auto)
opacity: 0.99;          /* أي قيمة أقل من 1 */
transform: scale(1);     /* أي قيمة غير none */
filter: blur(0);         /* أي قيمة غير none */
will-change: opacity, transform;
isolation: isolate;      /* مخصصة لعمل stacking context بشكل صريح */
🎯 الربط

"لما تلاقي z-index: 9999 مش شغالة، أول حاجة تفكري فيها مش زيادة الرقم لـ 999999. السؤال الصح: 'العنصر ده جوه أنهي Stacking Context، وهل فيه أب بينه وبين اللي عايزة تغلبيه عنده واحدة من الخصائص اللي فوق؟'"

🎯 أشهر Interview Questions
1. القيمة الافتراضية لـ position؟
static
2. هل relative بتشيل العنصر من Normal Flow؟

لأ. العنصر بيحتفظ بمكانه في الـ layout.

3. هل absolute دايمًا بالنسبة للأب المباشر؟

لأ. بالنسبة لأقرب Containing Block مؤهل - ومش بس position، كمان transform/filter/will-change بتأهّل الأب.

4. الفرق بين absolute وfixed؟

absolute → Containing Block. fixed → Viewport (إلا لو فيه أب بـ transform).

5. الفرق بين sticky وfixed؟

sticky بتبدأ في Normal Flow وبتلتصق عند threshold، fixed بتتشال من الـ flow من الأول.

6. ليه z-index: 9999 مش شغالة؟

غالبًا بسبب Stacking Context - العنصر محبوس جوه context أبوه، والرقم الكبير مش بيكسر الحدود دي.

🧠 Senior Mental Model
                 POSITION
                     │
       ┌─────────────┼─────────────┐
       │             │             │
    Normal Flow   Positioned    Scrolling
       │             │             │
     static       relative       sticky
                     │
              ┌──────┴──────┐
              │             │
          absolute        fixed
       (Containing Block) (Viewport*)

* إلا لو فيه أب بـ transform/filter/will-change

السؤال اللي لازم تسأليه بالترتيب لما تشوفي أي position:

1. "Positioned relative to what?"       → مين الـ Containing Block
2. "Does it remain in normal flow?"      → static/relative/sticky = أيوه، absolute/fixed = لأ
3. "Which stacking context is it in?"    → لو فيه overlap مشكلة
📋 Chapter Summary — مراجعة سريعة
القيمة	Normal Flow	المرجع	ملاحظة
static	✅	-	Default
relative	✅	مكانه الأصلي	بيبقى Containing Block لأبنائه
absolute	❌	أقرب Containing Block مؤهل	مش بس position، كمان transform
fixed	❌	Viewport	إلا لو أب بيه transform
sticky	✅ (لحد الالتصاق)	Scrolling container	محتاج top/bottom محدد
Keywords للحفظ
Normal Flow · position · Containing Block
static · relative · absolute · fixed · sticky
z-index · Stacking Context · isolation
transform (كـ containing block trigger)
🎤 جملتك النموذجية في المقابلة

"An element with position: absolute is removed from normal flow and positioned relative to its nearest positioned ancestor — but 'positioned' isn't limited to position; a transform, filter, or will-change on an ancestor also creates a containing block, which is a common source of unexpected fixed behavior. Similarly, a high z-index doesn't guarantee an element renders on top — stacking contexts, created by properties like opacity, transform, or isolation: isolate, can trap it below elements with much lower z-index values."