Chapter 7 — Flexbox  

│   ├── Flex Container
│   ├── Flex Items
│   ├── Main Axis
│   ├── Cross Axis
│   ├── justify-content
│   ├── align-items
│   ├── align-content
│   ├── align-self
│   ├── gap
│   ├── flex-direction
│   ├── flex-wrap
│   ├── flex-grow
│   ├── flex-shrink
│   ├── flex-basis
│   └── order
السؤال الاول
What is a Flex Container?
🧠 الفكرة المبسطة

تخيلي علبة مطاطية (Flex = مرن). لما تحطي أي حاجة جواها، العلبة والحاجات اللي جواها بيتصرفوا بمرونة حسب المساحة المتاحة - مش زي الصندوق الجامد العادي.

🔧 الصياغة التقنية
css
.container {
  display: flex;
}

أي عنصر عليه display: flex بيبقى Flex Container، والـ direct children بتاعته بس (مش الأحفاد) بيبقوا Flex Items.

html
<div class="container">
  <div>Item 1</div>
  <div>Item 2</div>
  <div>Item 3</div>
</div>
┌────────┐ ┌────────┐ ┌────────┐
│ Item 1 │ │ Item 2 │ │ Item 3 │
└────────┘ └────────┘ └────────┘
🎯 الربط

"Flexbox بيأثر أساسًا على الأبناء المباشرين بس - لو عندك div جوه div جوه الـ container، الـ Flexbox مبيوصلش للحفيد إلا لو هو نفسه بقى flex container منفصل."

7.2 Main Axis & Cross Axis — أهم مفهوم في الفصل كله
🧠 الفكرة المبسطة

تخيلي طريق فيه اتجاهين: الطريق الرئيسي اللي العربيات ماشية عليه، والطريق العرضي اللي عمودي عليه. الـ Main Axis هو "اتجاه الحركة الأساسي"، والـ Cross Axis هو "العمودي عليه".

🔧 الصياغة التقنية
css
.container {
  flex-direction: row; /* Default */
}

مع row:

Main Axis  →
Cross Axis ↓
🎯 الربط

"القاعدة الذهبية اللي لازم تتحفظي عليها: flex-direction هو اللي بيحدد اتجاه الـ Main Axis - مش دايمًا أفقي. النقطة دي أساس كل حاجة جاية بعد كده في الفصل."

7.3 flex-direction
🔧 الصياغة التقنية
css
flex-direction: row;            /* → 1 2 3 */
flex-direction: row-reverse;    /* ← 3 2 1 */
flex-direction: column;         /* ↓ 1,2,3 */
flex-direction: column-reverse; /* ↑ 3,2,1 */
🎯 الربط

"مهم: flex-direction مش بس بيقلب اتجاه العرض - هو بيقلب تعريف الـ Main Axis والـ Cross Axis نفسهم. ده اللي بيخلي justify-content تتصرف 'رأسي' جوه column بدل أفقي."

7.4 justify-content (Main Axis) vs align-items (Cross Axis)
🧠 الفكرة المبسطة

فكري في justify-content كـ "توزيع الناس على طول الطابور"، وalign-items كـ "محاذاة ارتفاعهم عرضيًا جوه نفس الطابور".

🔧 الصياغة التقنية
css
.container {
  display: flex;
  justify-content: center; /* على الـ Main Axis */
  align-items: center;     /* على الـ Cross Axis */
}

قيم justify-content: flex-start, flex-end, center, space-between, space-around, space-evenly

قيم align-items: stretch (Default), flex-start, flex-end, center, baseline

🎯 الربط

"القاعدة الخاطئة الشائعة: justify = horizontal وalign = vertical. دي بتتكسر فورًا لو غيّرتي الاتجاه:"

css
.container {
  display: flex;
  flex-direction: column;
  justify-content: center; /* دلوقتي رأسي! لأنه بيتبع Main Axis */
  align-items: center;      /* دلوقتي أفقي! لأنه بيتبع Cross Axis */
}

"لو فهمتي إن الاتنين بيتبعوا الـ axes مش الاتجاهات الثابتة، Flexbox بيبقى أسهل بكتير."

7.5 align-self — 🆕 خاصية مفقودة ومهمة
🧠 الفكرة المبسطة

تخيلي كل الطابور واقف بمحاذاة معينة، لكن شخص واحد قرر "أنا عايز أقف مختلف عن الباقي". align-self هي بالظبط الاستثناء ده - بتاخد حق الفيتو على align-items بتاع الأب، لكن لعنصر واحد بس.

🔧 الصياغة التقنية
css
.container {
  display: flex;
  align-items: center; /* كل العناصر في النص */
}

.item-special {
  align-self: flex-end; /* العنصر ده بس يتحاذى في الآخر */
}

قيمها زي align-items بالظبط: stretch, flex-start, flex-end, center, baseline, بالإضافة لـ auto (بترث من الأب).

🎯 الربط

"من غير align-self، الطريقة الوحيدة تحطي محاذاة مختلفة لعنصر واحد كانت هتبقى wrapper إضافي أو margin يدوي - وده مش ضروري. align-self بتحل المشكلة دي مباشرة على مستوى الـ item نفسه."

7.6 align-content (توزيع الـ Lines مش الـ Items)
🧠 الفكرة المبسطة

فكري في قاعة سينما فيها صفوف كراسي متعددة. align-items بتحاذي الكراسي جوه الصف الواحد، لكن align-content بتحاذي الصفوف نفسها ككتلة واحدة داخل القاعة.

🔧 الصياغة التقنية
css
.container {
  display: flex;
  flex-wrap: wrap;
  align-content: space-between;
}
⚠️ شرط أساسي

لو عندك سطر Flex واحد بس، مش هتشوفي أي تأثير لـ align-content - هي أصلاً محتاجة أكتر من line عشان تشتغل (يعني محتاجة flex-wrap: wrap غالبًا).

	align-items	align-content
بيتحكم في	Items جوه سطر واحد	الـ Lines نفسها
محتاج wrap؟	❌	✅ غالبًا
🎯 الربط

"لو حد سألك 'ليه align-content مش شغالة؟'، أول حاجة تتأكدي منها: هل فيه فعلاً أكتر من flex line أصلاً؟"

7.7 gap
🔧 الصياغة التقنية
css
.container {
  display: flex;
  gap: 20px;        /* row-gap و column-gap */
  gap: 10px 20px;   /* row-gap: 10px, column-gap: 20px */
}
🎯 الربط

"gap بقت الطريقة الأنضف لعمل مسافات بين الـ items، بدل ما تحطي margin يدوي على كل عنصر وتضطري تشيلها من آخر عنصر يدويًا."

7.8 flex-wrap
🔧 الصياغة التقنية
css
flex-wrap: nowrap; /* Default - كله في سطر واحد */
flex-wrap: wrap;   /* يسمح بالنزول لسطر جديد */
🎯 الربط

"flex-wrap هو اللي بيحدد أصلًا هل align-content هيبقى ليها معنى أو لأ."

7.9 flex-grow, flex-shrink, flex-basis
🧠 الفكرة المبسطة

فكري في 3 أسئلة عن أي flex item:

flex-basis → حجمه الأساسي الأول (قبل أي حسبة)
flex-grow  → هل بياخد نصيب من المساحة الفاضية؟
flex-shrink → هل بيصغر لو المساحة مش كفاية؟
🔧 الصياغة التقنية
css
.item1 { flex-grow: 1; }
.item2 { flex-grow: 2; } /* هياخد ضعف نصيب item1 من المساحة الإضافية */

.item {
  flex-shrink: 0; /* امنعي العنصر من الانكماش خالص */
}

.item {
  flex-basis: 200px; /* الحجم الأساسي قبل توزيع المساحة */
}
🆕 مشكلة الـ Overflow الشهيرة (min-width: auto)

حتى لو حطيتي flex-shrink: 1 (الافتراضي)، فيه حالة شائعة جدًا العنصر بيرفض ينكمش ويطلع بره الـ container:

css
.item {
  flex-shrink: 1; /* موجودة، لكن العنصر لسه بيعمل overflow! */
}

السبب: القيمة الافتراضية لـ min-width هي auto، وجوه سياق الـ Flexbox، دي بتتحول ضمنيًا لـ min-content size - يعني العنصر مش هينكمش أقل من حجم المحتوى بتاعه (زي كلمة طويلة من غير مسافات، أو صورة بحجم ثابت).

css
.item {
  min-width: 0; /* الحل: بيسمح للعنصر ينكمش فعليًا تحت حجم محتواه */
}
🎯 الربط

"ده من أشهر الـ bugs العملية في production - مطور بيحط flex-shrink: 1 ومتأكد إنها المفروض تشتغل، لكن العنصر (خصوصًا لو فيه نص طويل أو صورة) بيرفض ينكمش. الحل السريع اللي بينساه ناس كتير: min-width: 0 (أو min-height: 0 لو flex-direction: column)."

7.10 flex Shorthand
🔧 الصياغة التقنية
css
.item {
  flex: 1;          /* = flex-grow:1, flex-shrink:1, flex-basis:0% */
  flex: 1 1 200px;   /* grow:1, shrink:1, basis:200px */
}
القيم الجاهزة المهمة (سؤال شائع في المقابلات)
Shorthand	يعادل	ملاحظة
flex: initial (Default)	0 1 auto	مبيكبرش، بينكمش، حجمه من المحتوى
flex: auto	1 1 auto	بيكبر وينكمش، حجمه الأساسي من المحتوى
flex: none	0 0 auto	ثابت تمامًا - مبيكبرش ولا بينكمش
flex: 1	1 1 0%	بيكبر وينكمش، بيتجاهل حجم المحتوى كنقطة بداية
🎯 الربط

"الفرق العملي بين flex: 1 وflex: auto: flex: 1 بتبدأ من الصفر وتوزع المساحة بالتساوي بغض النظر عن حجم المحتوى، أما flex: auto بتاخد حجم المحتوى في الاعتبار الأول كنقطة بداية قبل التوزيع."

7.11 order
🔧 الصياغة التقنية
css
.item:nth-child(1) { order: 3; }
.item:nth-child(2) { order: 1; }
.item:nth-child(3) { order: 2; }
/* العرض البصري: B C A - لكن ترتيب الـ DOM ما اتغيرش */
⚠️ تحذير Accessibility

order بتغيّر الترتيب البصري بس، مش ترتيب الـ DOM. ده بيسبب مشاكل في:

Keyboard navigation (الـ Tab بيتنقل حسب ترتيب DOM مش الترتيب البصري)
Screen readers (بتقرا حسب DOM)
Logical reading order
🎯 الربط

"القاعدة السليمة: خليكي الـ HTML مرتب منطقيًا من الأساس، واستخدمي order لأغراض layout محدودة بس - مش كأداة لإعادة ترتيب المحتوى بالكامل."

🎯 أشهر Interview Questions
1. الفرق بين Main Axis و Cross Axis؟

Main Axis بيحدده flex-direction، والـ Cross Axis عمودي عليه.

2. الفرق بين align-items وalign-content؟

align-items بتحاذي العناصر جوه سطر واحد، align-content بتوزع أسطر متعددة داخل الـ container.

3. ليه align-content مش شغالة؟

غالبًا لأن فيه سطر flex واحد بس، أو flex-wrap: wrap مش مفعّلة.

4. الفرق بين flex-grow وflex-shrink؟

grow بتستخدم المساحة الإضافية، shrink بتتعامل مع نقص المساحة.

5. ليه العنصر مش بينكمش رغم flex-shrink: 1؟

غالبًا بسبب min-width: auto الافتراضية اللي بتتحول لـ min-content size. الحل: min-width: 0.

🪤 فخ المقابلة الشهير: ليه align-items: center مش شغالة؟

السؤال: "استخدمت align-items: center عشان أسنتر الأبناء رأسيًا، لكن مفيش أي تغيير حصل! ليه؟"

الفخ: الظن إن Flexbox بيحدد ارتفاع الأب تلقائيًا من الفراغ المتاح.

الإجابة الصحيحة: الـ Flex Container عنده ارتفاع محدد من الـ content بس (height: auto) - يعني مفيش مساحة رأسية زايدة أصلًا عشان الأبناء يتسنتروا فيها. لازم الأب يكون عنده ارتفاع صريح (زي height: 100vh أو height: 400px) عشان المحاذاة الرأسية تبان.

6. order بتغيّر ترتيب الـ DOM؟

لأ. بتغيّر الـ visual order بس، ومحتاجة حذر مع الـ accessibility.

🧠 Senior Mental Model
                 FLEX CONTAINER
                       │
                 flex-direction
                       │
             ┌─────────┴─────────┐
             ↓                   →
        Main Axis           Cross Axis
             │                   │
      justify-content       align-items
      flex-grow             align-content
      flex-shrink           align-self (فردي)
      flex-basis

ثم:

flex-wrap → هل يوجد أكثر من line؟
gap       → المسافات بين الـ items
order     → visual ordering (احذري الـ accessibility)
min-width: 0 → لو العنصر رافض ينكمش رغم flex-shrink
أهم قاعدة في الفصل كله

justify-content وalign-items مبيعنوش horizontal وvertical؛ هما بيتبعوا Main Axis وCross Axis - واللي بيحددهم هو flex-direction.

📋 Chapter Summary — مراجعة سريعة
الخاصية	بتشتغل على	ملاحظة
justify-content	Main Axis	توزيع العناصر
align-items	Cross Axis	محاذاة كل العناصر جوه سطر
align-self	Cross Axis	محاذاة عنصر واحد بس (استثناء)
align-content	Cross Axis	توزيع الأسطر (محتاج wrap)
flex-grow	Main Axis	النمو
flex-shrink	Main Axis	الانكماش (احذري min-width: auto)
flex-basis	Main Axis	الحجم الأساسي
order	-	ترتيب بصري بس (احذري accessibility)
Keywords للحفظ
Flex Container · Flex Item · Main Axis · Cross Axis
flex-direction · justify-content · align-items
align-content · align-self · gap · flex-wrap
flex-grow · flex-shrink · flex-basis · order
min-width: auto (min-content size)
🎤 جملتك النموذجية في المقابلة

"Flexbox is a one-dimensional layout system built around two axes defined by flex-direction. justify-content distributes items along the main axis, align-items aligns them along the cross axis, and align-self overrides that for a single item. A common real-world bug is a flex item refusing to shrink below its content size — that's because min-width defaults to auto, which resolves to the content's min-content size in a flex context; setting min-width: 0 fixes it."