Chapter 17 — RTL & Internationalization  

│   ├── dir attribute & its effect on Cascade
│   ├── Logical Properties as the RTL foundation (cross-ref Ch.16)
│   ├── writing-mode
│   ├── Icon & Image Mirroring
│   ├── Bidi-aware layouts (Flex/Grid in RTL)
│   ├── :dir() pseudo-class
│   ├── Scrollbar direction
│   └── Bilingual typography considerations
السؤال الاول
dir مش مجرد CSS
🧠 الفكرة المبسطة

تخيلي بتقولي لكتاب "انت مكتوب من الشمال لليمين" - ده مش مجرد "شكل الصفحة"، ده بيأثر على إزاي القارئ نفسه بيفهم ترتيب الكلام. dir="rtl" بنفس الفكرة - مش تنسيق بصري، هو تعريف لغوي أساسي.

🔧 الصياغة التقنية
html
<html lang="ar" dir="rtl">
<html lang="en" dir="ltr">

ممكن كمان على مستوى عنصر واحد:

html
<div dir="rtl">...</div>
🎯 الربط

"الترتيب الصح للبناء: HTML (dir) → CSS (Logical Properties) → Components - مش العكس (تبدئي بـ CSS وتحاولي 'تقلبي' كل حاجة). لو بدأتي بـ dir الصح، Flexbox والـ Logical Properties بيتصرفوا صح تلقائيًا من غير أي override يدوي."

🎨 في Figma

⚠️ محتاجة تأكيد: الإصدارات الحديثة من Figma بتدعم "Right to left" كخيار على مستوى الـ Frame/Auto Layout، بيقلب اتجاه ترتيب العناصر تلقائيًا بشكل مشابه لمفهوم dir - لكن يفضل تتأكدي من دقة السلوك الحالي في حسابك لأن الميزة دي حديثة نسبيًا وممكن تختلف تفاصيلها.

17.2 Logical Properties كأساس الـ RTL
🔧 الصياغة التقنية
css
.card {
  margin-inline-start: 24px;
  padding-inline-end: 16px;
}

في LTR: start = left, end = right. في RTL: العكس تلقائيًا.

🎯 الربط

"فاكرة فصل 16؟ ده تطبيقها العملي المباشر - القاعدة الذهبية: متفكريش في Left/Right، فكري في Start/End."

17.3 writing-mode
🔧 الصياغة التقنية
css
writing-mode: horizontal-tb; /* الافتراضي - معظم استخداماتك */
writing-mode: vertical-rl;
🎯 الربط

"مش هتستخدميها كتير في SaaS/ERP عادي، لكن فهمها مهم لأن الـ Logical Properties (inline/block) أساسًا مبنية على مفهوم الـ writing mode - مش دايمًا inline = أفقي بشكل مطلق."

17.4 Icon & Image Mirroring
🧠 الفكرة المبسطة

تخيلي سهم بيقول "التالي" - المعنى بتاعه مرتبط باتجاه القراءة، فلازم ينقلب مع اللغة. لكن لوجو شركة أو أيقونة كاميرا معندهاش "اتجاه" أصلًا - قلبهم هيبقى غلط بصريًا مش تصحيح.

🔧 الصياغة التقنية
css
[dir="rtl"] .icon-directional {
  transform: scaleX(-1);
}
قاعدة الحسم
بتتقلب	مبتتقلبش
أسهم تنقل (Next/Back)	Logo وBrand marks
Undo/Redo	Camera, Microphone, Play/Pause
مؤشرات تقدم (Progress)	Search, Lock, Heart
🎯 الربط

"السؤال اللي بيحدد: هل الأيقونة دي بتعبّر عن اتجاه (زمني أو مكاني)، ولا هي رمز عالمي معناه ثابت؟ لو اتجاه → اقلبيها. لو رمز عالمي → سيبيها زي ما هي."

17.5 Bidi-aware Layouts (Flex/Grid)
🔧 الصياغة التقنية
css
.actions {
  display: flex;
  gap: 8px;
  /* ❌ متحطيش flex-direction: row-reverse هنا */
}
⚠️ فخ مهم: row-reverse مش "خاصية RTL"

row-reverse بتعكس ترتيب الـ main axis بغض النظر عن اللغة. dir="rtl" بيحدد اتجاه الكتابة نفسه. الاتنين مختلفين تمامًا - لو استخدمتي row-reverse مع dir="rtl" سوا من غير فهم، ممكن تلاقي ترتيب مقلوب مرتين (يرجع لوضعه الطبيعي بالغلط أو يتعقد أكتر).

🎯 الربط

"غالبًا dir="rtl" + display: flex عادي بيكفي - الـ main direction بيتصرف صح تلقائيًا من غير ما تحتاجي row-reverse خالص."

17.6 🆕 :dir() Pseudo-class مقابل [dir] Attribute Selector
🧠 الفكرة المبسطة

تخيلي عايزة تعرفي "هل الشخص ده بيتكلم عربي؟" - ممكن تسأليه هو نفسه (attribute صريح عليه)، أو ممكن تلاحظي إنه جاي من عيلة بتتكلم عربي حتى لو هو نفسه مقالش كده صراحة (وراثة). دي بالظبط الفرق بين الاتنين.

🔧 الصياغة التقنية
css
/* ❌ بيشتغل بس لو العنصر ده نفسه عليه attribute [dir="rtl"] مكتوب صراحة */
[dir="rtl"] .icon { transform: scaleX(-1); }

/* ✅ بيشتغل حتى لو الاتجاه موروث من أب بعيد (زي <html dir="rtl">) */
:dir(rtl) .icon { transform: scaleX(-1); }
🎯 الربط

"في الحالة الشائعة إن الـ dir متحطوطة على <html> بس، [dir="rtl"] هتشتغل برضه لأنها CSS attribute selector بيدور في الشجرة كلها. لكن الفرق بيبان لو عندك component معزول (زي third-party widget) الـ dir بتاعه متوارثة مش مكتوبة عليه صراحة - هنا :dir() هي اللي هتلتقط الحالة الفعلية للاتجاه، بينما [dir="rtl"] ممكن تفشل. :dir() بتتبع الاتجاه الفعلي المحسوب (computed)، مش بس القيمة المكتوبة صراحة."

17.7 🆕 مشكلة الـ Scrollbar في RTL
🧠 الفكرة المبسطة

تخيلي مصعد في مبنى - في مبنى عادي هو على الشمال، لكن في مبنى "مقلوب" المصعد بيبقى على اليمين. لو انتِ افترضتي "المصعد دايمًا شمال" وحطيتي لافتة بناءً على الافتراض ده، هتلاقيها في المكان الغلط في المبنى التاني.

🔧 الصياغة التقنية
css
/* ❌ افتراض خطير */
.sidebar {
  position: fixed;
  right: 0; /* في RTL، الـ native scrollbar بيظهر على الشمال، فده ممكن يعمل تصادم بصري */
}

/* ✅ استخدام Logical Properties بدل الافتراض الفيزيائي */
.sidebar {
  position: fixed;
  inset-inline-end: 0;
}
🎯 الربط

"في أغلب المتصفحات، الـ scrollbar الأصلي للصفحة بيتقلب مكانه في RTL (بيبان على الشمال بدل اليمين). أي عنصر position: fixed/absolute بيفترض 'اليمين دايمًا فاضي عشان المحتوى' هيتصادم مع المكان الجديد للـ scrollbar. الحل: استخدام inset-inline-start/inset-inline-end بدل left/right حتى في الـ positioning، مش بس في الـ margin/padding."

17.8 Bidi Text & unicode-bidi
🔧 الصياغة التقنية
css
.order-id {
  direction: ltr; /* لجزء محدد زي كود الطلب أو الإيميل */
  unicode-bidi: isolate; /* يمنع الجزء ده يأثر على اتجاه النص المحيط */
}
🎯 الربط

"الترتيب الصح للحلول: HTML dir صح الأول → Logical CSS → استخدام unicode-bidi/direction بس لجزئيات محددة زي أرقام الطلبات أو الإيميلات، مش كحل عام أول ما تواجهي مشكلة."

17.9 Bilingual Typography
🔧 الصياغة التقنية
css
:lang(ar) {
  font-family: "IBM Plex Sans Arabic", sans-serif;
  line-height: 1.7; /* مساحة أكبر للتشكيل */
}
:lang(en) {
  font-family: "Inter", sans-serif;
  line-height: 1.5;
}
🎯 الربط

"العربية والإنجليزية مختلفين في font metrics، كثافة الحروف، والـ line-height المناسب - :lang() بتخليكي تطبّقي قيم مختلفة حسب اللغة الفعلية للنص، بدل افتراض إن نفس الـ line-height هيشتغل كويس للغتين."

⚠️ Common RTL Mistakes
استخدام left/right في كل مكان بدل Logical Properties
قلب الصفحة كلها بـ transform: scaleX(-1) - بيكسر النص والصور والتفاعل
row-reverse كـ "حل RTL" في كل مكان
عكس كل الأيقونات تلقائيًا (حتى غير الاتجاهية)
🆕 افتراض إن اليمين "فاضي دايمًا" للـ scrollbar
🎯 Senior Mental Model
1. HTML         → dir="rtl"
2. Layout        → Logical Properties
3. Flex/Grid      → Direction-aware (بدون row-reverse تلقائي)
4. Typography      → Arabic + English real testing
5. Icons             → Mirror directional بس
6. Mixed content      → direction:ltr لجزئيات محددة
7. Selectors           → :dir() للاتجاه المحسوب، مش بس [dir] الصريح
8. Positioning           → inset-inline بدل left/right (احذري scrollbar!)
🎤 Senior Interview Questions
1. ليه نستخدم dir="rtl" بدل عكس CSS بس؟

لأن RTL مش تغيير بصري بس - dir بيحدد اتجاه الكتابة نفسه وبيأثر على تفسير النص، بينما CSS بيتعامل مع الـ presentation بس.

2. row-reverse بتعني RTL؟

لأ. بتعكس ترتيب الـ main axis، مختلفة تمامًا عن dir="rtl" اللي بيحدد اتجاه الكتابة.

3. الفرق بين :dir(rtl) و[dir="rtl"]؟

[dir="rtl"] بتشتغل بس لو العنصر أو أحد أجداده عليه الـ attribute مكتوب صراحة، بينما :dir(rtl) بتتبع الاتجاه المحسوب فعليًا للعنصر.

4. ليه right: 0 خطر في RTL؟

الـ scrollbar الأصلي بيتقلب مكانه في RTL (بيبان شمال)، فأي عنصر بيفترض "اليمين فاضي دايمًا" ممكن يتصادم بصريًا معاه. الحل: inset-inline-end بدل right.

5. لازم نعكس كل الأيقونات في RTL؟

لأ. بس الأيقونات الاتجاهية (أسهم، undo/redo). اللوجوهات والرموز العالمية (كاميرا، play، search) بتفضل زي ما هي.

📋 Chapter Summary — مراجعة سريعة
المفهوم	القاعدة السريعة
dir attribute	أساس اتجاه الكتابة، مش مجرد بصري
Logical Properties	start/end بدل left/right
row-reverse	مش "حل RTL" - مفهوم مختلف تمامًا
Icon mirroring	اتجاهية بس، مش رموز عالمية
:dir() vs [dir]	:dir() بتتبع الاتجاه المحسوب، [dir] بس الصريح
Scrollbar RTL	بيتقلب مكانه - استخدمي inset-inline مش right
unicode-bidi/direction	لجزئيات محددة بس (order ID, email)
:lang()	typography مختلفة لكل لغة
Keywords للحفظ
dir attribute · Logical Properties · start/end
writing-mode · Icon Mirroring · row-reverse (ليست RTL)
:dir() pseudo-class · Scrollbar flip · inset-inline
unicode-bidi · direction · :lang()
Bidi (Bidirectional text)
🎤 جملتك النموذجية في المقابلة

"I build direction-aware UI from the start rather than flipping an LTR design — using logical properties and letting dir="rtl" on the HTML drive the rest. A subtle distinction worth knowing: :dir(rtl) matches the computed direction even when inherited, while [dir="rtl"] only matches an explicit attribute. I also watch for the native scrollbar flipping sides in RTL, which can collide with elements positioned using physical right instead of inset-inline-end."   
