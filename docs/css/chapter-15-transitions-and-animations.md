Chapter 15 — Transitions & Animations 

│   ├── transition
│   ├── transform
│   ├── @keyframes
│   ├── animation
│   ├── timing functions
│   └── prefers-reduced-motion
السؤال الاول
الفرق الجوهري بين Transition و Animation
🧠 الفكرة المبسطة

Transition زي إنك بتاخدي مصعد من الدور الأول للتالت - انتقال ناعم من نقطة لنقطة، محتاج زرار يتضغط الأول (Hover/Focus). Animation زي فيلم كارتون كامل - له سيناريو بمراحل متعددة، وممكن يشتغل لوحده من غير أي تفاعل.

🔧 الصياغة التقنية
Transition → انتقال ناعم بين حالتين موجودتين
Animation  → حركة بعدة مراحل عبر @keyframes، ممكن تشتغل تلقائيًا
🎯 الربط

"القرار البسيط: لو الحركة رد فعل على تفاعل (hover/focus/state change) → Transition. لو الحركة محتاجة أكتر من نقطتين (بداية ونهاية) أو لازم تشتغل تلقائيًا → Animation."

15.2 transition
🔧 الصياغة التقنية
css
button {
  background: blue;
  transition: background-color 200ms ease;
}
button:hover {
  background: darkblue;
}

الصيغة الكاملة: transition: property duration timing-function delay;

⚠️ تحذير: تجنبي transition: all
css
/* ❌ غير مفضّل في production */
transition: all 200ms ease;

/* ✅ الأفضل - تحديد الخصائص صراحة */
transition: transform 200ms ease, opacity 200ms ease;
🎯 الربط

"transition: all بتخلي أي خاصية بتتغيّر (حتى واحدة ماكنتيش قاصدة تحريكها) تدخل في الانتقال - ده بيخلي الـ behavior أصعب في التوقع والصيانة. القاعدة: Animate only what actually needs to animate."

15.3 transform
🔧 الصياغة التقنية
css
transform: translateX(20px);        /* تحريك أفقي */
transform: translateY(-4px);         /* تحريك رأسي */
transform: scale(1.05);              /* تكبير/تصغير */
transform: rotate(45deg);            /* تدوير */
transform: translateY(-4px) scale(1.02); /* دمج أكتر من تحويل */
🎯 الربط

"transform بيغيّر شكل/مكان العنصر بصريًا من غير ما يأثر على الـ layout بالطريقة التقليدية - العناصر التانية حواليه مش بتحس إنه اتحرك."

⚠️ نقطة دقيقة: هل transform دايمًا GPU؟

لأ. transform وopacity غالبًا بيتعاملوا بكفاءة أعلى لأنهم ممكن يتجنبوا مراحل الـ Layout والـ Paint المكلفة، لكن ده مش مضمون تلقائيًا 100% لكل حالة - المتصفح هو اللي بيقرر يعمل compositing layer منفصل (GPU) بناءً على عوامل تانية كتير. متفتكريش "transform = GPU دايمًا وبأمان مطلق" كقاعدة صلبة.

15.4 🆕 will-change — تلميح للمتصفح
🧠 الفكرة المبسطة

تخيلي بتقوليلها لصاحبك "استعد، أنا هحتاجك تجري بعد شوية" قبل ما تقوليله "اجري دلوقتي" - بتدّيه وقت يستعد فيه بدل ما يتفاجئ.

🔧 الصياغة التقنية
css
.card {
  transition: transform 200ms ease;
}
.card:hover {
  will-change: transform;
  transform: translateY(-4px);
}
⚠️ تحذير مهم

will-change مش سحر تحسّن كل حاجة تلقائي - استخدامها بكثرة أو على عناصر كتير بيستهلك ذاكرة إضافية من المتصفح (بيجهّز compositing layers مسبقًا لكل عنصر). الاستخدام الصح: بس على العناصر اللي فعلًا هتتحرك قريب (زي وقت hover)، مش كـ default عام على كل حاجة.

🎯 الربط

"will-change مفيدة في حالات specific لما بتلاحظي jank فعلي في animation معينة، مش أداة تحطيها على كل عنصر 'احتياطًا'. الاستخدام الزيادة عن اللزوم بيقلب الفايدة لعبء إضافي."

15.5 @keyframes و animation
🔧 الصياغة التقنية
css
@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}
.modal {
  animation: fadeIn 300ms ease;
}
مراحل متعددة
css
@keyframes slideIn {
  0%   { opacity: 0; transform: translateY(20px); }
  50%  { opacity: 0.7; }
  100% { opacity: 1; transform: translateY(0); }
}
الخصائص الفرعية
css
.notification {
  animation-name: slideIn;
  animation-duration: 300ms;
  animation-timing-function: ease-out;
  animation-iteration-count: 1;
  animation-fill-mode: both;
}
🎯 الربط

"@keyframes بتديكي مرونة إن أي حاجة مش متاحة مع transition العادية - نقط توقف متعددة (مش بس بداية ونهاية)، وإمكانية تشتغل تلقائي من غير تفاعل مستخدم."

15.6 animation-iteration-count, direction, fill-mode
🔧 الصياغة التقنية
css
.loader {
  animation: spin 1s linear infinite;  /* تكرار لا نهائي */
}
.element {
  animation: move 1s ease-in-out infinite alternate; /* رايح جاي */
}
.element {
  animation: fadeOut 300ms forwards; /* يحتفظ بحالة النهاية بعد ما يخلص */
}
🎯 الربط

"animation-fill-mode: forwards مهمة جدًا عمليًا - من غيرها، العنصر بيرجع لحالته الأصلية فورًا بعد ما الـ animation يخلص، وده غالبًا مش اللي القارئة قاصداه (زي عنصر بيختفي بـ fadeOut، من غيرها هيظهر تاني فجأة)."

15.7 🆕 مشكلة شائعة: Animation على height: auto
🧠 الفكرة المبسطة

تخيلي عايزة تعملي "سلّم متحرك" بين نقطتين، لكن مش عارفة نقطة النهاية بالظبط (زي "طلعي لحد ما توصلي لأي حاجة"). السلّم مش هيعرف يحسب سرعته لأنه مش عارف طول المشوار.

🔧 الصياغة التقنية
css
/* ❌ مش هيشتغل - مفيش انتقال ناعم، هيقفز فجأة */
.accordion {
  height: 0;
  transition: height 300ms ease;
  overflow: hidden;
}
.accordion.open {
  height: auto; /* المتصفح مش عارف يحسب "auto" كنقطة نهاية رقمية */
}

الحلول الشائعة:

css
/* حل 1: قيمة max-height كبيرة (حل تقريبي، فيه عيوب توقيت) */
.accordion {
  max-height: 0;
  transition: max-height 300ms ease;
  overflow: hidden;
}
.accordion.open {
  max-height: 500px; /* رقم أكبر من أعلى محتوى متوقع */
}

/* حل 2 (حديث): grid-template-rows trick */
.accordion {
  display: grid;
  grid-template-rows: 0fr;
  transition: grid-template-rows 300ms ease;
  overflow: hidden;
}
.accordion.open {
  grid-template-rows: 1fr;
}
🎯 الربط

"ده باج شائع جدًا وحقيقي في أي accordion أو dropdown بيتوسع لمحتوى بحجم متغيّر. الـ transition مبتشتغلش على auto لأن المتصفح محتاج رقم بداية ورقم نهاية واضحين عشان يحسب الخطوات البينية. حل الـ grid-template-rows: 0fr → 1fr أنضف من max-height لأنه مش بيحتاج تخميني رقم تعسفي كبير."

15.8 Timing Functions
🔧 الصياغة التقنية
Function	السلوك	الاستخدام الشائع
linear	سرعة ثابتة	Loading spinner، حركة مستمرة
ease	ناعمة عامة	استخدام عام افتراضي
ease-in	بطيء ثم يتسارع	بعض حركات الخروج
ease-out	سريع ثم يهدأ	Modal, Toast, Dropdown (عناصر داخلة للشاشة)
ease-in-out	بطيء→سريع→بطيء	انتقال ناعم بين حالتين
css
transition: transform 300ms cubic-bezier(0.4, 0, 0.2, 1); /* تحكم دقيق مخصص */
🎯 الربط

"القاعدة العملية الشائعة: عناصر داخلة للشاشة (modal, toast) → ease-out (تبدأ بسرعة وتهدأ، حاسة طبيعية). عناصر مستمرة (loader) → linear."

15.9 prefers-reduced-motion
🔧 الصياغة التقنية
css
@media (prefers-reduced-motion: reduce) {
  .modal { animation: none; }
  .card { transition: none; }
}
⚠️ نقطة Senior مهمة

الحل الشائع (إلغاء كل الحركة بـ 0.01ms) مش دايمًا الأفضل. الأدق: قرري أي حركة ليها معنى وظيفي وأي حركة مجرد زخرفة - Accessibility هدفها تقليل الحركة المزعجة، مش إلغاء الـ functionality.

🎯 الربط

"القاعدة: Normal Motion = تفاعل غني. Reduced Motion = نفس الوظيفة، حركة أقل. مش 'قطع كل حاجة'."

⚠️ أخطاء شائعة
تحريك width/left/margin بدل transform لما ممكن
Animation على كل عنصر (Visual Noise) بدل الـ micro-interactions المهمة بس
transition: all بدل تحديد الخصائص
تجاهل prefers-reduced-motion
🆕 محاولة عمل transition على height: auto مباشرة
🎯 Senior Interview Questions
1. الفرق بين transition وanimation؟

Transition بين حالتين، Animation بمراحل متعددة عبر @keyframes وممكن تشتغل تلقائي.

2. transform دايمًا بيستخدم GPU؟

لأ. غالبًا بيتعامل بكفاءة أعلى، لكن مش مضمون كقاعدة مطلقة - المتصفح هو اللي بيقرر.

3. ليه transition مش بتشتغل على height: auto؟

المتصفح محتاج رقم بداية ونهاية واضحين للحساب. الحل: max-height بقيمة تقريبية أو grid-template-rows: 0fr → 1fr.

4. إيه فايدة will-change؟

بتلمّح للمتصفح يستعد لتحريك خاصية معينة مسبقًا، لكن استخدامها الزايد بيستهلك ذاكرة إضافية.

5. transition: all أفضل ولا لأ؟

لأ، الأفضل تحديد الخصائص صراحة لتوقع أوضح وسهولة صيانة.

🎯 الخلاصة
transition        → State → State (Hover/Focus)
transform          → Move/Scale/Rotate (بدون تأثير layout تقليدي)
will-change        → تلميح مسبق (استخدام موضعي بس)
@keyframes+animation → مراحل متعددة، تلقائي
timing functions    → التحكم في سرعة الحركة عبر الزمن
height: auto محدودية → استخدمي max-height أو grid-template-rows
prefers-reduced-motion → Accessibility (تقليل مش إلغاء وظيفي)
📋 Chapter Summary — مراجعة سريعة
المفهوم	القاعدة السريعة
Transition	حالتين، رد فعل لتفاعل
Animation	مراحل متعددة، ممكن تلقائي
transform/opacity	غالبًا أعلى كفاءة، مش GPU مضمون دايمًا
will-change	تلميح موضعي، مش استخدام عام
height: auto	مش بتتحرك مباشرة - استخدمي max-height أو grid-template-rows
ease-out	مناسبة لعناصر داخلة للشاشة
prefers-reduced-motion	تقليل الحركة، مش إلغاء الوظيفة
Keywords للحفظ
transition · transform · will-change
@keyframes · animation-fill-mode · animation-iteration-count
timing functions · cubic-bezier
height: auto limitation · grid-template-rows trick
prefers-reduced-motion
🎤 جملتك النموذجية في المقابلة

"I animate transform and opacity where possible since browsers can often handle them more efficiently than layout-affecting properties like width or left — though I wouldn't claim that's guaranteed GPU compositing in every case. For accordions or expandable content, I avoid transitioning height: auto directly since the browser can't interpolate to an undefined endpoint — I use grid-template-rows: 0fr to 1fr instead. And I always account for prefers-reduced-motion, reducing motion rather than removing functionality."