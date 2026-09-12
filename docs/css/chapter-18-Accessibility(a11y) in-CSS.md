Chapter 18 — Accessibility (a11y) in CSS 

│   ├── focus-visible & focus management
│   ├── prefers-color-scheme / prefers-contrast
│   ├── forced-colors (Windows High Contrast)
│   ├── prefers-reduced-motion (cross-ref Ch.15)
│   ├── Screen-reader-only patterns (.sr-only)
│   ├── Color contrast & readability
│   ├── Touch target size
│   └── Semantic structure's effect on CSS decisions
السؤال الاول
Accessibility في CSS مش مسؤولية HTML بس
🧠 الفكرة المبسطة

تخيلي مبنى فيه سلالم بس من غير مصعد أو رامب - الباب (HTML) موجود ومفتوح، لكن الطريق (CSS) بيمنع ناس معينة توصل. الـ accessibility الحقيقية محتاجة الاتنين مع بعض.

🔧 الصياغة التقنية

CSS ممكن يخلي الـ UI accessible، أو يصعّبه جدًا - حتى لو الـ HTML underneath سليم 100%.

🎯 الربط

"القاعدة الذهبية للفصل كله: Accessible CSS مش شكل بصري بس - هي إن الطبقة البصرية تفضل شغالة صح مع الـ keyboard navigation، تفضيلات المستخدم، أدوات المساعدة، والـ semantic HTML."

18.2 :focus-visible & Focus Management
🔧 الصياغة التقنية
css
button:focus-visible {
  outline: 2px solid var(--color-primary);
  outline-offset: 3px;
}
⚠️ خطأ شائع جدًا
css
/* ❌ خطر جدًا من غير بديل */
button { outline: none; }
🎯 الربط

":focus-visible بتحل مشكلة قديمة: :focus كانت بتظهر outline حتى مع الضغط بالماوس (مزعج بصريًا)، فكتير كانوا بيشيلوها بالكامل - وده كان بيدمر تجربة مستخدمي الـ keyboard. :focus-visible بتظهر الـ indicator بس وقت الحاجة الفعلية ليه (تنقل بالـ Tab)."

Focus Management مش مسؤولية CSS بس

في Components زي Modal/Dialog/Dropdown، إدارة مكان الـ focus (مش شكله) محتاجة HTML + JavaScript:

User opens modal → Focus moves into modal → User navigates → Modal closes → Focus returns to trigger

"CSS بتحدد شكل الـ focus، لكن منطق انتقاله بين العناصر مسؤولية الـ application logic."

18.3 prefers-color-scheme
🔧 الصياغة التقنية
css
@media (prefers-color-scheme: dark) {
  :root { --color-bg: #111827; --color-text: #ffffff; }
}
🎯 الربط

"مهم متلخبطيش بين System preference (prefers-color-scheme) وApp-level theme choice (data-theme بيختاره المستخدم جوه التطبيق نفسه). الاتنين منفصلين - المستخدم ممكن يختار Dark جوه تطبيقك حتى لو نظام تشغيله على Light."

18.4 prefers-contrast
🔧 الصياغة التقنية
css
@media (prefers-contrast: more) {
  .button { border: 2px solid currentColor; }
}
🎯 الربط

"مهم: prefers-contrast مش بديل عن تصميم أساسي كويس من الأول. القاعدة: Good default contrast + دعم تفضيل المستخدم، مش 'تصميم ضعيف والمستخدم يظبطه بنفسه'."

18.5 🆕 forced-colors — مختلفة تمامًا عن prefers-contrast
🧠 الفكرة المبسطة

تخيلي حد قالك "استخدم بس الألوان دي المحددة، معندكيش حرية اختيار" (forced-colors) - ده مختلف عن حد بيقولك "خلي التباين أعلى بس، اختاري الألوان انتِ" (prefers-contrast).

🔧 الصياغة التقنية
css
@media (forced-colors: active) {
  .card {
    border: 1px solid CanvasText; /* لازم system color keywords */
    forced-color-adjust: none; /* لو محتاجة تمنعي الفرض على عنصر معين */
  }
}
🎯 الربط

"forced-colors: active بتتفعّل لما المستخدم شغّل Windows High Contrast Mode أو مشابه - المتصفح بيفرض palette محدودة من system colors (زي CanvasText, LinkText, ButtonFace) على كل حاجة، بغض النظر عن ألوانك الأصلية. ده مختلف جوهريًا عن prefers-contrast اللي بتسيبلك حرية اختيار الألوان بس بمستوى تباين أعلى. لو design system بتاعك معتمد كتير على ألوان دقيقة (زي gradients أو borders رفيعة)، فيه احتمال إنها تختفي تمامًا جوه forced-colors mode."

18.6 prefers-reduced-motion
🎯 الربط

"اتشرحت بالتفصيل في فصل 15 - هنا بس بنركز على الـ Accessibility impact: القرار مش 'شيلي كل الحركة'، القرار 'قلّلي الحركة اللي مالهاش معنى وظيفي، واحتفظي بالـ feedback الأساسي'."

18.7 Screen Reader Only Patterns (.sr-only)
🔧 الصياغة التقنية
css
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip-path: inset(50%);
  white-space: nowrap;
  border: 0;
}
⚠️ تصحيح تقني مهم

استخدمي clip-path: inset(50%) مش clip: rect(0,0,0,0). خاصية clip بمفردها deprecated في CSS الحديث - لسه شغالة كـ legacy support بس، والمعيار الحالي المعتمد فعليًا في المكتبات الكبيرة هو clip-path.

⚠️ لا تستخدمي display: none
css
/* ❌ ده بيشيل العنصر من accessibility tree كمان */
.sr-only { display: none; }
🎯 الربط

"الهدف من .sr-only: نص موجود فعليًا في الـ DOM ومتاح للـ screen reader، لكن مخفي بصريًا 100%. display: none بتشيله من الاتنين مع بعض، وده بيلغي الغرض كله."

18.8 Color Contrast & Readability
🔧 الصياغة التقنية

معايير WCAG:

المستوى	نص عادي	نص كبير
AA (الحد الأدنى الشائع)	4.5:1	3:1
AAA (أعلى)	7:1	4.5:1
⚠️ متعتمديش على اللون وحده
❌ 🔴 = Error (بس)
✅ 🔴 Error: Invalid email address (لون + نص + أيقونة)
🎯 الربط

"القاعدة: Color + Text/Icon/Shape، مش Color لوحده. مستخدم عنده color blindness مش هيفرّق بين أحمر وأخضر لو ده الاعتماد الوحيد لتوصيل المعنى."

18.9 🆕 Touch Target Size — WCAG 2.5.5
🧠 الفكرة المبسطة

تخيلي بتحاولي تدوسي على زرار صغير جدًا في موبايل بإصبعك - لو الزرار أصغر من حجم إصبعك، هتدوسي جنبه بالغلط. المساحة اللي بتقدري تدوسي عليها بدقة محدودة بحجم فيزيائي معين.

🔧 الصياغة التقنية
css
.icon-button {
  min-width: 44px;
  min-height: 44px; /* الحد الأدنى المقترح في WCAG 2.5.5 */
}
🎯 الربط

"معيار WCAG 2.5.5 بيقترح 44×44px كحد أدنى لأي عنصر تفاعلي على شاشات اللمس. ده مهم جدًا لأي icon-only button (زي X للإغلاق) - حتى لو الأيقونة نفسها بصريًا صغيرة (16px مثلًا)، لازم مساحة اللمس الفعلية حواليها تفضل 44px على الأقل، عادةً بإضافة padding مناسب حوالين الأيقونة."

18.10 Semantic Structure's Effect on CSS
🔧 الصياغة التقنية
html
<!-- ❌ -->
<div class="button">Save</div>

<!-- ✅ -->
<button class="button">Save</button>
🎯 الربط

"<button> بييجي معاه states جاهزة (:hover, :focus-visible, :active, :disabled) وaccessibility behavior مدمج. محاولة تحويل <div> لزرار بصريًا بس بتحرمك من كل ده وبتضطرك تضيفي JavaScript وARIA يدويًا لحاجات كانت هتيجي مجانًا مع العنصر الصح."

18.11 visibility, opacity, display والـ Accessibility
🔧 الصياغة التقنية
	مساحة	Keyboard/Interaction	Screen Reader
display: none	❌	❌	❌
visibility: hidden	✅	❌ (عادة)	❌
opacity: 0	✅	⚠️ ممكن يفضل قابل للتفاعل!	✅
🎯 الربط

"الخطر الحقيقي: opacity: 0 بتخلي العنصر شفاف بصريًا لكنه ممكن يفضل قابل للـ focus بالـ Tab - يعني مستخدم keyboard ممكن "يوصل" لعنصر مش شايفه خالص على الشاشة. متفكريش 'Invisible = Gone' - اسألي: هل هو في layout؟ هل ممكن أوصله بالـ Tab؟ هل الـ screen reader بيشوفه؟"

18.12 Disabled vs Visual Disabled
🔧 الصياغة التقنية
css
/* ❌ يبان معطل، لكنه لسه فعليًا شغال وقابل للضغط */
.button { opacity: 0.5; }
html
<!-- ✅ الحالة الحقيقية semantic + interactive -->
<button disabled>Save</button>
🎯 الربط

"القاعدة: Visual state + Actual state مع بعض، مش بصري بس. زرار يبان باهت لكنه فعليًا قابل للضغط عليه = accessibility bug حقيقي."

🎯 CSS Accessibility Checklist
Keyboard
 كل عنصر تفاعلي وصوله ممكن بالـ keyboard؟
 الـ focus واضح (:focus-visible)؟
Motion & Contrast
 prefers-reduced-motion متطبقة؟
 prefers-contrast وforced-colors مأخوذين في الاعتبار؟
Screen Readers
 icon-only buttons ليها accessible name (.sr-only)؟
 النص المخفي بـ clip-path مش display: none؟
Touch
 العناصر التفاعلية ≥ 44×44px على الموبايل؟
Semantics
 <button> بدل <div>؟
🎤 Senior Interview Questions
1. ليه :focus-visible أفضل من :focus؟

بتظهر الـ indicator بس وقت الحاجة الفعلية (keyboard navigation)، من غير ما تظهر مزعجة عند الضغط بالماوس.

2. الفرق بين prefers-contrast وforced-colors؟

prefers-contrast بتسيبلك حرية اختيار الألوان بمستوى تباين أعلى. forced-colors بتفرض عليكي system color palette محدودة بالكامل.

3. ليه .sr-only بتستخدم clip-path مش display: none؟

عشان النص يفضل موجود في الـ accessibility tree ومتاح للـ screen reader، لكن مخفي بصريًا بس.

4. opacity: 0 زي display: none؟

لأ. العنصر ممكن يفضل قابل للـ focus والتفاعل حتى وهو شفاف تمامًا - ده فرق مهم وخطر محتمل.

5. إيه الحد الأدنى المقترح لمساحة اللمس؟

44×44px حسب WCAG 2.5.5.

📋 Chapter Summary — مراجعة سريعة
المفهوم	القاعدة السريعة
:focus-visible	Focus indicator وقت الـ keyboard بس
prefers-color-scheme	تفضيل نظام التشغيل (مختلف عن app theme)
prefers-contrast	المستخدم طالب تباين أعلى
forced-colors	النظام بيفرض palette محدودة بالكامل
.sr-only	clip-path: inset(50%) مش display: none أو clip: rect()
Color contrast	4.5:1 نص عادي (AA)، مع Color+Text مش لون لوحده
Touch target	44×44px حد أدنى
opacity: 0	ممكن يفضل قابل للتفاعل - احذري
Semantic HTML	<button> بدل <div>
Keywords للحفظ
:focus-visible · Focus Management
prefers-color-scheme · prefers-contrast · forced-colors
prefers-reduced-motion · .sr-only · clip-path: inset(50%)
Contrast Ratio · WCAG AA/AAA · Touch Target Size (44px)
Semantic HTML
🎤 جملتك النموذجية في المقابلة

"I treat accessibility as a CSS responsibility, not just HTML — using :focus-visible for keyboard-only indicators, and being careful that opacity: 0 doesn't silently leave an element focusable and interactive. I distinguish prefers-contrast, which respects user color choices at higher contrast, from forced-colors, which overrides colors entirely with system values. For hidden accessible text, I use clip-path: inset(50%) rather than the deprecated clip property or display: none, which would remove it from the accessibility tree entirely." 
