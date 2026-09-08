Chapter 13 — CSS Functions (Math & Color)

│   ├── calc()
│   ├── min()
│   ├── max()
│   ├── clamp()
│   ├── rgb()
│   ├── hsl()
│   └── color functions (color-mix, oklch, etc.)
السؤال الاول
ليه محتاجين CSS Functions أصلًا؟
🧠 الفكرة المبسطة

فكري في الفرق بين "اكتبي 350" و"احسبي 300 زائد 50". القيمة الثابتة جامدة، لكن الدالة بتدّيكي منطق حسابي حي بيتفاعل مع باقي القيم.

🔧 الصياغة التقنية

CSS Functions بتحوّل القيم من ثابتة لـ dynamic - بتحسبي، بتحطي حدود، وبتتعاملي مع الألوان بمرونة أكتر.

🎯 الربط

"الفرق الجوهري بين مطور بيكتب width: 960px ومطور بيكتب width: min(90%, 1200px) - التاني بيفكر في العلاقة بين القيمة والسياق، مش رقم منفصل عن أي حاجة."

13.2 calc()
🔧 الصياغة التقنية
css
.container {
  width: calc(100% - 40px);
}
main {
  width: calc(100% - 240px); /* Sidebar 240px + Main = الباقي */
}
.content {
  min-height: calc(100vh - 80px); /* Navbar 80px + Content = الباقي */
}
⚠️ تحذير Syntax حرج

لازم مسافة قبل وبعد + و- جوه calc()، وإلا الـ declaration بتتجاهل بالكامل:

css
/* غلط - بيتجاهل تمامًا */
width: calc(100%-40px);

/* صح */
width: calc(100% - 40px);

* و/ مش شرط مسافة حواليهم.

🎯 الربط

"الفايدة الحقيقية لـ calc() مش الحسبة نفسها - هي إمكانية جمع وحدات مختلفة مع بعض (percentage + px، أو vh + px) في تعبير واحد، وده مستحيل تعمليه بأي وحدة لوحدها."

🎨 في Figma

⚠️ محتاجة تأكيد: حقول الأرقام في Figma (زي Width/Height) بتقبل تعبيرات حسابية بسيطة (تقدري تكتبي 300-20 في خانة الرقم وهي بتحسبها تلقائي)، لكن ده مش دالة calc() حقيقية بتتقيّم وقت الـ render زي CSS - هي مجرد حاسبة بتحول الناتج لرقم ثابت لحظة الكتابة. يفضل تتأكدي من التفاصيل لو محتاجة دقة أكبر.

13.3 min()
🔧 الصياغة التقنية
css
.container {
  width: min(90%, 1200px); /* الأصغر من الاتنين */
}
🆕 مش بس قيمتين
css
width: min(90%, 1200px, 50vw); /* بتقبل أي عدد من القيم */
🎯 الربط

"بدل كتابة width: 90%; max-width: 1200px; كسطرين منفصلين، min() بتديكي نفس النتيجة في سطر واحد - وده pattern شائع جدًا لتحديد سقف أقصى بشكل مختصر."

13.4 max()
🔧 الصياغة التقنية
css
.container {
  padding-inline: max(20px, 5vw); /* الأكبر من الاتنين */
}
🎯 الربط

"عكس min() تمامًا - بتضمنلك حد أدنى بدل حد أقصى. مثال شائع: padding مايقلش عن 20px حتى على شاشة صغيرة جدًا، لكن يكبر مع الشاشة الكبيرة."

13.5 min() vs max() vs clamp()
Function	الفكرة
min()	اختاري الأصغر (سقف أقصى)
max()	اختاري الأكبر (حد أدنى)
clamp()	minimum + preferred + maximum مع بعض
🎯 الربط

"clamp() عمليًا هي min() وmax() مدموجين في دالة واحدة - بتديكي قيمة fluid لكن بحدود آمنة من الطرفين."

13.6 clamp()
🔧 الصياغة التقنية
css
h1 {
  font-size: clamp(2rem, 5vw, 4rem);
  /*              min   preferred max */
}

بدل ما تكتبي 3 media queries منفصلة للـ mobile/tablet/desktop، القيمة بتتغير تلقائيًا وناعمة بين الحدين.

🎯 الربط

"أهم فايدة عملية: تقليل عدد الـ breakpoints اللي محتاجاها بشكل كبير - القيمة بتتكيف بذاتها بدل ما تحتاجي تكتبي حالة لكل حجم شاشة."

13.7 rgb() و hsl()
🔧 الصياغة التقنية
css
/* RGB */
color: rgb(42, 75, 141);
color: rgb(42 75 141 / 0.5); /* الصيغة الحديثة بدون فواصل + alpha */

/* HSL */
color: hsl(220 54% 36%);
color: hsl(220 54% 36% / 0.5);

HSL بتتكون من: Hue (نوع اللون على العجلة 0-360°)، Saturation (تشبع 0%=رمادي، 100%=مشبع بالكامل)، Lightness (إضاءة 0%=أسود، 100%=أبيض).

🎯 الربط

"الفايدة العملية لـ HSL: سهل تعملي variations من نفس اللون - غيّري رقم الـ Lightness بس (تصغير/تكبير الرقم) عشان تجيبي نسخة أغمق أو أفتح من نفس اللون، بدل ما تحسبي أرقام RGB جديدة من الصفر."

🎨 في Figma

نفس الصيغ (RGB وHSL) متاحة كتبويبات مباشرة جوه أي Fill picker، وتقدري تبدّلي بينهم لنفس اللون.

13.8 color-mix()
🧠 الفكرة المبسطة

تخيلي بتخلطي دهان أبيض مع دهان أزرق بنسب معينة عشان تطلعي بلون أزرق فاتح - بدل ما تشتري علبة دهان لون جاهز جديدة.

🔧 الصياغة التقنية
css
.button:hover {
  background: color-mix(in srgb, var(--primary) 90%, black);
}

الفكرة: خدي var(--primary) بنسبة 90%، واخلطيها مع black بنسبة 10% (الباقي تلقائي).

🎯 الربط

"بدل ما تعرّفي 3-4 ألوان يدوي لكل حالة (hover/active/disabled)، color-mix() بتشتق اللون تلقائي من اللون الأساسي. لكن ده مش بديل دايمًا عن الـ explicit design tokens - في أنظمة كبيرة، أحيانًا التحكم اليدوي في كل لون بيبقى أضمن للـ consistency والـ accessibility."

13.9 oklch()
🔧 الصياغة التقنية
css
color: oklch(60% 0.15 250);
/* L (Lightness) → C (Chroma) → H (Hue) */
🎯 الربط

"الميزة الحقيقية: oklch() مصممة عشان تكون متسقة بصريًا - يعني لو ثبّتي الـ Lightness عند 60% وغيّرتي بس الـ Hue، كل الألوان الناتجة هتبان بنفس درجة السطوع للعين البشرية فعليًا. مع HSL أو RGB، نفس النسبة ممكن تدّي إحساس بسطوع مختلف تمامًا حسب اللون (الأصفر بيبان أسطع من الأزرق حتى بنفس رقم الإضاءة)."

🆕 تحذير عملي: Browser Support
css
.button {
  background: #2A4B8D;                    /* Fallback أولًا */
  background: oklch(55% 0.15 250);         /* المتصفحات الحديثة بتاخد ده */
}

السبب: oklch() وcolor-mix() من الإضافات الحديثة نسبيًا لـ CSS (الدعم الواسع بدأ فعليًا حوالي 2023). المتصفح بيتجاهل أي قيمة مش فاهمها ويستخدم آخر قيمة صالحة قبلها - فكتابة اللون العادي الأول ثم القيمة الحديثة بعده بتضمن fallback تلقائي من غير أي كود إضافي. تقدري كمان تستخدمي @supports لو محتاجة تحكم أدق.

13.10 دمج color-mix() + oklch() + var()
🔧 الصياغة التقنية
css
.button:hover {
  background: color-mix(in oklch, var(--primary), black 10%);
}
🎯 الربط

"لاحظي إن var() هنا مجرد مدخل للدالة، مش موضوع الفصل - التفاصيل الكاملة عن الـ Custom Properties وSpecial theming هنشوفها في الفصل الجاي (14) عشان نتجنب التكرار بين الفصلين."

🧠 أهم Pattern في الفصل
محتاجة calculation؟              → calc() (لا تنسي المسافات!)
محتاجة سقف أقصى؟                 → min()
محتاجة حد أدنى؟                   → max()
محتاجة fluid value بحدود؟         → clamp()
محتاجة تمثيل لون تقليدي؟          → rgb() / hsl()
محتاجة خلط ألوان ديناميكي؟         → color-mix()
محتاجة color space حديث متسق بصريًا؟ → oklch() (مع fallback!)
🎯 أسئلة Senior مهمة
1. الفرق بين min()، max()، clamp()؟

min() بتختار الأصغر، max() بتختار الأكبر، clamp() بتحدد minimum وpreferred وmaximum مع بعض.

2. ليه clamp() مهمة للـ responsive design؟

بتدّي قيم fluid بحدود محددة، وبتقلل الحاجة لعدد كبير من الـ breakpoints.

3. إيه color-mix()؟

بتخلط لونين بنسب محددة داخل color space معين.

4. إيه oklch()؟

Color function حديثة مبنية على OKLCH color space، مفيدة لبناء ألوان متسقة بصريًا (perceptual uniformity).

5. لو استخدمتي oklch() في مشروع، إزاي تضمني fallback للمتصفحات القديمة؟

بكتابة قيمة لون تقليدية (hex/rgb) الأول، وبعدها قيمة oklch() - المتصفح القديم هيتجاهل السطر التاني ويفضل على الأول.

6. min() بتقبل قيمتين بس؟

لأ. بتقبل أي عدد من القيم مفصولة بفاصلة، مش بس اتنين.

📋 Chapter Summary — مراجعة سريعة
Function	الاستخدام
calc()	حسابات تجمع وحدات مختلفة (لا تنسي المسافات!)
min()	أصغر قيمة (سقف أقصى) - تقبل أكتر من قيمتين
max()	أكبر قيمة (حد أدنى)
clamp()	fluid بحدود min/max
rgb()/hsl()	تمثيل ألوان تقليدي
color-mix()	خلط لونين ديناميكيًا
oklch()	color space حديث متسق بصريًا (يحتاج fallback)
Keywords للحفظ
calc() · min() · max() · clamp()
rgb() · hsl() · Hue · Saturation · Lightness
color-mix() · oklch() · Perceptual Uniformity
Browser Support Fallback
🎤 جملتك النموذجية في المقابلة

"CSS math functions like clamp(), min(), and max() let me build fluid, responsive values without stacking media queries. For color, I use color-mix() to derive hover and active states from a base token instead of hardcoding every variant, and I'm moving toward oklch() for perceptual consistency across a palette — always with a traditional color fallback declared first, since these are newer additions with less universal support." 
