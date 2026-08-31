Chapter 11 — Colors & Backgrounds 

│   ├── color
│   ├── background
│   ├── gradients
│   ├── opacity
│   └── background positioning/sizing
السؤال الاول
الفرق بين color وbackground
🧠 الفكرة المبسطة

فكري في أي عنصر كـ "ورقة مكتوب عليها كلام" - لون الورقة نفسها حاجة (background)، ولون الحبر اللي بتكتبي بيه حاجة تانية (color).

🔧 الصياغة التقنية
css
p {
  color: blue;              /* لون النص */
  background-color: #fff;    /* لون الخلفية */
}
🎯 الربط

"color بيتحكم في الـ foreground (النص والمحتوى الأمامي)، background بيتحكم في الخلفية. بسيطة، لكن أساس كل حاجة جاية بعد كده."

🎨 في Figma

مفهوم مطابق تمامًا: أي عنصر نص في Figma ليه Fill خاص بيه (بيتحكم في لون الحروف)، والـ Frame/Shape اللي وراه ليه Fill منفصل خاص بيه (بيتحكم في الخلفية) - بالظبط نفس الفصل المنطقي بين color وbackground-color.

11.2 طرق كتابة الألوان
🔧 الصياغة التقنية
css
color: red;                              /* Named */
color: #2A4B8D;                          /* HEX */
color: rgb(42, 75, 141);                 /* RGB */
color: rgb(42 75 141 / 0.5);             /* RGB + Alpha */
color: hsl(220 54% 36%);                 /* HSL */
color: hsl(220 54% 36% / 0.5);           /* HSL + Alpha */
🎯 الربط

"في Design Systems الحقيقية، الأسماء (red) نادرًا ما بتُستخدم - الأشهر HEX أو RGB/HSL عشان دقة أعلى وقابلية دمج مع design tokens."

🎨 في Figma

نفس الصيغ دي (HEX وRGB وHSL) موجودة كخيارات مباشرة جوه أي Fill picker في Figma - تقدري تبدّلي بينهم من نفس القائمة المنسدلة وهما بيمثلوا نفس اللون بس بصيغ مختلفة، بالظبط زي CSS.

11.3 background vs background-color
🔧 الصياغة التقنية
css
.card {
  background-color: #fff; /* بس اللون */
}

.hero {
  background: url("hero.jpg") center/cover no-repeat; /* shorthand شامل */
}
🎯 الربط

"background هي shorthand بتقدر تجمع كذا خاصية (image, position, size, repeat) في سطر واحد. background-color بتتحكم في اللون بس."

11.4 Background Images: Position, Size, Repeat
🔧 الصياغة التقنية
css
.hero {
  background-image: url("hero.jpg");
  background-position: center;
  background-size: cover;      /* يملأ المساحة، ممكن يقص جزء */
  background-size: contain;    /* الصورة كاملة، ممكن مساحة فاضية */
  background-repeat: no-repeat;
}
	cover	contain
السلوك	يملأ الـ container بالكامل	الصورة كلها ظاهرة
العيب المحتمل	ممكن يقص جزء من الصورة	ممكن مساحة فاضية حوالين الصورة
الاستخدام الشائع	Hero sections, banners	لوجوهات، أيقونات محتاجة تبان كاملة
🎯 الربط

"القرار بين الاتنين بيعتمد على سؤال واحد: مهم أشوف الصورة كاملة، ولا مهم أملي المساحة حتى لو اتقصت شوية؟"

🎨 في Figma

نفس المنطق موجود بالظبط لما بتحطي صورة كـ Image Fill: خيارات "Fill" (بتملأ الفريم بالكامل، ممكن تقص جزء من الصورة - مطابقة لـ cover)، و**"Fit"** (الصورة كاملة تبان جوه الفريم، ممكن مساحة فاضية - مطابقة لـ contain)، بالإضافة لـ "Crop" و**"Tile"** (اللي بتكرر الصورة، مطابقة لـ background-repeat: repeat).

11.5 🆕 object-fit / object-position — المكافئ لـ <img> الحقيقية
🧠 الفكرة المبسطة

كل اللي اتعلمناه فوق (cover/contain) كان عن صور خلفية (background-image). لكن الفصل نفسه قال "استخدمي <img> للمحتوى المهم" - يبقى محتاجة نفس المنطق ده لما الصورة تكون عنصر HTML حقيقي مش خلفية.

🔧 الصياغة التقنية
html
<img src="product.jpg" class="product-image" alt="...">
css
.product-image {
  width: 300px;
  height: 200px;
  object-fit: cover;      /* نفس منطق background-size: cover */
  object-position: center; /* نفس منطق background-position */
}
🎯 الربط

"من غير object-fit، أي <img> بتحطيلها width/height مختلفين عن أبعادها الأصلية هتتمطط أو تتشوّه. object-fit: cover بيخليها تتصرف زي صورة خلفية cover - تملأ المساحة وتقص الزيادة بدل ما تتشوّه. ده أساسي جدًا لأي Product card أو User avatar فيها صور بمقاسات مختلفة."

🎨 في Figma

نفس خيارات الـ "Fill"/"Fit"/"Crop" اللي اتكلمنا عنها فوق بتتطبق سواء الصورة دي "خلفية" لفريم أو صورة أساسية - Figma مش بيفرّق بين الحالتين زي ما CSS بيفرّق بين background-image و<img> + object-fit.

11.6 Gradients: Linear, Radial, و🆕 Conic
🔧 الصياغة التقنية
css
/* Linear - خط مستقيم */
background: linear-gradient(90deg, #2A4B8D, #6C8CD5);

/* Radial - من المركز للخارج */
background: radial-gradient(circle, white, blue);

/* 🆕 Conic - دوراني حوالين نقطة مركزية، زي عقارب الساعة */
background: conic-gradient(from 0deg, red, yellow, green, blue, red);
🎯 الربط

"الـ conic-gradient أقل شيوعًا من الاتنين التانيين، لكنها الأداة الطبيعية لعمل حاجات زي color wheels، pie charts بسيطة بـ CSS بس، أو مؤشرات progress دائرية (زي loading spinner)."

🎨 في Figma

الـ Fill panel في Figma بيدعم أنواع gradient متعددة تحت قائمة الاختيار: Linear، Radial، Angular (وده هو نفسه الـ conic-gradient في CSS - بس باسم مختلف)، وكمان Diamond (مش ليها مكافئ مباشر في CSS العادي).

11.7 Multiple Backgrounds & Overlay Pattern
🔧 الصياغة التقنية
css
.hero {
  background:
    linear-gradient(rgba(0,0,0,0.5), rgba(0,0,0,0.5)),
    url("hero.jpg") center/cover no-repeat;
}
🎯 الربط

"الترتيب مهم - أول layer مكتوبة بتبقى فوق. ده بيغنيكي عن عمل <div> overlay منفصل في الـ HTML بس عشان تحطي طبقة غامقة فوق صورة."

🎨 في Figma

الفريمات في Figma بتقبل أكتر من Fill في نفس الوقت (تقدري تضيفي أكتر من طبقة fill من زرار "+" جوه لوحة الـ Fill)، وترتيبهم في القائمة بيحدد أيهم فوق الآخر - نفس فكرة الـ layering بالظبط.

11.8 opacity vs Alpha Color — أهم فرق في الفصل
🧠 الفكرة المبسطة

تخيلي بتحطي نظارة شمس على وشك كله (نص وخلفية وكل حاجة) - ده opacity. أما لو حطيتي ورق زجاج شفاف بس على خلفية اللوحة وسبتي الرسمة اللي فوقها واضحة - ده alpha color.

🔧 الصياغة التقنية
css
/* ❌ opacity بتأثر على كل حاجة جوه العنصر */
.card {
  opacity: 0.5; /* النص والأيقونة والخلفية كلهم بيبقوا شفافين */
}

/* ✅ alpha بتأثر على اللون نفسه بس */
.card {
  background: rgb(0 0 0 / 0.5); /* النص فضل واضح 100% */
}
🎯 الربط

"دي من أهم النقاط في UI حقيقي: لو عايزة overlay غامق نص واضح فوقه، opacity غلط لأنها هتوضّح النص كمان. الحل الصح: alpha channel على الخلفية بس."

🎨 في Figma

الفرق ده موجود بنفس الدقة: Opacity الطبقة نفسها (في أعلى لوحة الخصائص، بتأثر على العنصر وكل اللي جواه) منفصلة تمامًا عن Opacity الخاص بالـ Fill نفسه (جوه لوحة الـ Fill، بيأثر على اللون بس). لو حطيتي Fill opacity منخفضة على خلفية Frame فيه نص، النص بيفضل واضح 100% - بالظبط نفس سلوك alpha color في CSS.

11.9 🆕 currentColor — قيمة عملية مفقودة
🧠 الفكرة المبسطة

تخيلي عندك متغيّر اسمه "لون الكلام الحالي"، وتقدري تستخدميه في أي حتة تانية عشان "خدي نفس اللون اللي النص شغال بيه دلوقتي" - من غير ما تكرري كتابة نفس الكود لوني مرتين.

🔧 الصياغة التقنية
css
.icon-button {
  color: #2A4B8D;        /* لون النص/الأيقونة */
  border: 2px solid currentColor;  /* الحدود بتاخد نفس لون النص تلقائيًا */
}

/* لو غيّرتي color على hover، الـ border هيتغيّر معاه أوتوماتيك */
.icon-button:hover {
  color: #6C8CD5;
}
🎯 الربط

"currentColor بتوفّر عليكي تكرار نفس قيمة اللون في أكتر من property، وبتضمن إن أي تغيير في color (زي hover state) بينعكس تلقائيًا على أي حاجة تانية مستخدمة currentColor - شائعة جدًا مع الـ SVG icons (fill: currentColor) عشان الأيقونة تاخد لون النص المحيط بيها تلقائيًا."

11.10 🆕 Color Contrast (WCAG) — معيار Accessibility مفقود
🧠 الفكرة المبسطة

تخيلي بتكتبي على سبورة - لو الطباشير رمادي فاتح والسبورة رمادي غامق قريب منه، محدش هيقدر يقرا. لازم فرق واضح بين اللون والخلفية عشان أي حد (بما فيهم ضعاف البصر) يقدر يقرا.

🔧 الصياغة التقنية

مفيش property واحدة لده - هو معيار بتتأكدي منه بأدوات:

css
/* نسبة تباين ضعيفة - صعبة القراءة */
.bad-example {
  color: #999999;
  background: #cccccc;
}

/* نسبة تباين قوية - سهلة القراءة */
.good-example {
  color: #1a1a1a;
  background: #ffffff;
}
القاعدة (WCAG)
نوع المحتوى	الحد الأدنى المطلوب (AA)
نص عادي	نسبة تباين 4.5:1
نص كبير (18pt+)	نسبة تباين 3:1
🎯 الربط

"اختيار الألوان مش قرار جمالي بس - فيه معيار رسمي (WCAG) بيحدد أقل نسبة تباين مقبولة بين النص والخلفية. أدوات زي Chrome DevTools بتحسب النسبة دي تلقائي وبتقولك لو مطابقة للمعيار ولا لأ."

🎨 في Figma

فيه plugins مخصصة (زي Stark أو Contrast) بتحسب نسبة WCAG مباشرة جوه Figma وانتِ بتصممي، من غير ما تحتاجي تنقلي لـ DevTools - مفيدة جدًا تتأكدي من التباين من مرحلة التصميم نفسها قبل ما توصلي لمرحلة الكود.

🎯 أشهر أسئلة Senior
1. الفرق بين opacity وalpha color؟

opacity بتأثر على العنصر وكل محتوياته، alpha بتأثر على اللون نفسه بس.

2. cover vs contain؟

cover بتملأ المساحة وممكن تقص، contain بتحافظ على الصورة كاملة وممكن تسيب مساحة فاضية.

3. background-image أو <img>؟

<img> للمحتوى المهم دلاليًا (مع alt مناسب)، background-image للـ decorative/presentational.

4. إيه الفرق بين object-fit: cover وbackground-size: cover؟

نفس المنطق بالظبط، لكن object-fit بتتطبق على عنصر <img> حقيقي في الـ HTML، بينما background-size بتتطبق على صورة مستخدمة كـ CSS background.

5. إيه معيار WCAG لنسبة التباين؟

4.5:1 للنص العادي، 3:1 للنص الكبير (18pt+) كحد أدنى (مستوى AA).

6. إيه فايدة currentColor؟

بتخلي property زي border أو fill (في SVG) تاخد نفس قيمة color تلقائيًا، فأي تغيير على color (زي hover) بينعكس تلقائيًا من غير تكرار الكود.

🧠 Senior Mental Model
                Colors & Backgrounds
                        │
        ┌───────────────┼───────────────┐
        ↓               ↓               ↓
     color          background      Accessibility
   (foreground)          │                │
        │          ┌─────┴─────┐    Contrast Ratio
  currentColor      ↓           ↓    (WCAG 4.5:1)
                  Color        Image
                              │
                  ┌───────────┼───────────┐
                  ↓           ↓           ↓
              Position      Size        Repeat
                          (cover/contain)

opacity → العنصر كله      |    alpha → اللون بس
⭐ أهم نقاط الفصل
color للـ foreground، background للخلفية
cover/contain لصور الخلفية، object-fit لنفس الفكرة مع <img> حقيقية
opacity بتأثر على كل حاجة، alpha بتأثر على اللون بس
الألوان مش قرار جمالي بس - فيه معيار WCAG رسمي للتباين
<img> للمحتوى، background-image للـ decoration
📋 Chapter Summary — مراجعة سريعة
المفهوم	القاعدة السريعة
color	لون النص/foreground
background/background-color	لون أو صورة الخلفية
cover	يملأ، ممكن يقص
contain	كامل، ممكن فراغ
object-fit	نفس منطق background-size بس لـ <img>
opacity	شفافية العنصر كله
Alpha color	شفافية اللون بس
currentColor	ورّث لون النص الحالي لـ property تانية
WCAG Contrast	4.5:1 نص عادي، 3:1 نص كبير
linear/radial/conic gradient	3 أنواع تدرج مختلفة
Keywords للحفظ
color · background · background-color · cover · contain
object-fit · object-position · opacity · alpha channel
currentColor · linear-gradient · radial-gradient · conic-gradient
WCAG · Contrast Ratio · Multiple Backgrounds
🎤 جملتك النموذجية في المقابلة

"I distinguish opacity from alpha transparency carefully — opacity fades the entire element tree including text, while an alpha channel on the background color keeps text fully legible. For images, object-fit gives <img> elements the same cover/contain behavior as CSS backgrounds. I also treat color choices as an accessibility concern, not just aesthetics — checking contrast ratios against WCAG's 4.5:1 minimum for normal text." 
