Chapter 12 — Typography  

│   ├── font-family
│   ├── font-size
│   ├── font-weight
│   ├── font-style / text-transform
│   ├── line-height
│   ├── letter-spacing
│   ├── text-align
│   ├── text-decoration
│   ├── text-overflow
│   ├── overflow-wrap / word-break
│   ├── text-wrap: balance
│   └── web fonts
السؤال الاول
font-family والـ Fallback Stack
🧠 الفكرة المبسطة

تخيلي بتحجزي طاولة في مطعم، ولو مش لاقية مكان، عندك خطة بديلة، ولو البديلة مش متاحة، عندك خطة ثالثة عامة تضمن إنك مش هتقعدي على الأرض. ده بالظبط الـ font stack.

🔧 الصياغة التقنية
css
body {
  font-family: "Inter", Arial, sans-serif;
}

المتصفح بيجرب Inter الأول، لو مش متاح بيروح لـ Arial، لو مش متاح بيروح لأي خط sans-serif عام متاح على الجهاز.

🎯 الربط

"الـ fallback مش رفاهية - هو ضمان إن النص يفضل قابل للقراءة حتى لو الخط المخصص فشل يتحمّل (مشكلة شبكة، أو الخط مش متاح على الجهاز)."

🎨 في Figma

نفس فكرة الـ font stack موجودة في Figma لو بتستخدمي Text Styles - بتحددي الخط الأساسي، لكن Figma مش بيطبّق fallback تلقائي زي المتصفح (لأنه بيفترض إن الخط متاح على جهازك أثناء التصميم). الـ fallback بتاعتك ده تفكير لازم تضيفيه انتِ وقت كتابة الـ CSS، مش حاجة بتنتقل تلقائيًا من Figma.

12.2 Generic Font Families
🔧 الصياغة التقنية
css
body {
  font-family: system-ui, sans-serif;
}

system-ui بتاخد خط واجهة النظام نفسه (زي San Francisco على macOS، أو Segoe UI على Windows) بدل تحميل خط خارجي.

🎯 الربط

"استخدام system-ui بيوفّر وقت تحميل الخط تمامًا، وبيدّي إحساس 'native' أقرب لنظام تشغيل المستخدم."

12.3 font-size
🔧 الصياغة التقنية
css
h1 { font-size: 2rem; }
h1 { font-size: clamp(2rem, 5vw, 4rem); } /* fluid - من فصل 10 */
🎯 الربط

"هنا بنربط مباشرة بفصل الـ Units - استخدام rem بيضمن التناسق مع الـ root scale، وclamp() بيدّي حجم fluid بحدود آمنة."

🎨 في Figma

خانة الـ Font Size جوه لوحة الـ Text properties - نفس المفهوم، لكن دايمًا بالـ px (زي ما اتفقنا في فصل الـ Units، مفيش وحدات نسبية جوه Figma).

12.4 font-weight
🔧 الصياغة التقنية
css
button { font-weight: 600; } /* Semi Bold */
القيمة	الاسم التقريبي
400	Regular
500	Medium
600	Semi Bold
700	Bold
⚠️ تحذير مهم

مش كل خط بيدعم كل الأوزان. لو الخط معندوش 600 حقيقي، المتصفح بيحاول يقرّب لأقرب وزن متاح.

🎯 الربط

"لو حطيتي font-weight: 600 على خط معندوش نسخة 600 فعلية، النتيجة مش مضمونة - ممكن يستخدم أقرب وزن، أو في حالات نادرة يعمل 'fake bold' بالتمديد البصري، وده بيقلل جودة النص بصريًا."

🎨 في Figma

قائمة الـ Font Weight جوه dropdown الخط - بتعرضلك بس الأوزان المتاحة فعليًا للخط اللي مثبت عندك، فمينفعش تختاري وزن مش موجود أصلًا (عكس CSS اللي ممكن تكتبي أي رقم وتسيبي المتصفح "يحاول").

12.5 🆕 font-style و text-transform
🧠 الفكرة المبسطة

فكري فيهم كـ "تأثيرات بصرية جاهزة" على النص - مش تغيير في الخط نفسه، لكن تحويل شكله أو ميلانه.

🔧 الصياغة التقنية
css
.emphasis {
  font-style: italic;
}

.label {
  text-transform: uppercase;   /* كل الحروف كابيتال */
}
.title {
  text-transform: capitalize;  /* أول حرف كل كلمة كابيتال */
}
🎯 الربط

"text-transform مفيدة جدًا للـ labels والـ buttons (زي 'SUBMIT' بدل 'Submit') من غير ما تحتاجي تكتبي النص في الـ HTML بحروف كابيتال فعليًا - النص الأصلي في الـ DOM بيفضل زي ما هو، والتحويل بصري بس. ده مهم لـ screen readers لأنها بتقرا النص الأصلي مش الشكل البصري المحوّل."

🎨 في Figma

فيه خاصية اسمها "Text case" جوه لوحة الـ Text properties بتدّيكي نفس الخيارات (UPPERCASE, lowercase, Capitalize)، وخاصية Italic ضمن اختيار الخط نفسه.

12.6 line-height
🔧 الصياغة التقنية
css
body {
  line-height: 1.5; /* unitless - موصى بيه */
}
🎯 الربط

"فاكرة الفخ من فصل 10 (الـ Compounding Effect مع em)؟ ده تحديدًا سبب إن الـ unitless line-height هي الممارسة القياسية - القيمة النسبية (1.5) هي اللي بتتوارث، مش رقم px محسوب وثابت."

🎨 في Figma

خانة الـ Line height جوه Text properties - بتقدري تحطيها كـ Percent (نسبة من حجم الخط، أقرب مفهوميًا لـ unitless) أو كـ Fixed (رقم ثابت بالـ px، أقرب لـ line-height بوحدة).

12.7 letter-spacing
🔧 الصياغة التقنية
css
.label {
  letter-spacing: 0.05em; /* توسيع بسيط - شائع في labels كابيتال */
}
.heading {
  letter-spacing: -0.02em; /* تضييق بسيط - شائع في عناوين كبيرة */
}
🎯 الربط

"القاعدة العملية: توسيع خفيف لـ uppercase labels صغيرة (بيحسّن القراءة)، وتضييق خفيف للعناوين الكبيرة (بيدّي إحساس أكتر تماسكًا بصريًا). لكن أي تغيير كبير بيقلل الـ readability."

🎨 في Figma

خانة Letter spacing جوه Text properties - مطابقة تمامًا، بتقدري تحطيها كنسبة مئوية أو رقم ثابت.

12.8 text-align و RTL (start/end)
🔧 الصياغة التقنية
css
.title {
  text-align: start; /* مش left! */
}

في LTR: start = left. في RTL: start = right تلقائيًا.

🎯 الربط

"لو انتِ شغالة على مشروع بيدعم عربي/إنجليزي، استخدام start/end بدل left/right بيوفّرلك overrides كتير وقت الـ RTL، لأن القيمة بتتكيف تلقائيًا مع اتجاه اللغة - هنشوف ده بالتفصيل في فصل RTL القادم."

🎨 في Figma

أزرار الـ Text alignment (يسار/وسط/يمين/justify) موجودة بشكل مباشر - لكن مفيش مفهوم "start/end" منطقي زي CSS، لازم تختاري يمين أو شمال يدويًا حسب اتجاه التصميم بتاعك.

12.9 text-decoration والـ Accessibility Trap
🔧 الصياغة التقنية
css
a { text-decoration: underline; }
a { text-decoration-thickness: 2px; }
⚠️ تحذير Accessibility

لو شلتي الـ underline (text-decoration: none) لازم يبقى فيه تمييز بصري تاني واضح (لون مختلف بوضوح، أو bold) - وإلا الرابط هيبقى صعب اكتشافه لبعض المستخدمين.

🎯 الربط

"القرار الشائع في design systems حديثة إنهم يشيلوا الـ underline من الروابط جوه الفقرات، بس بشرط يعوّضوا بلون واضح جدًا + hover state واضح - مش مجرد تغيير لون خفيف."

🎨 في Figma

خيار Underline موجود جوه dropdown الخط نفسه، لكن مفيش أدوات مدمجة في Figma بتتأكد تلقائيًا من كفاية التمييز البصري - ده قرار تصميمي لازم تاخديه انتِ بوعي.

12.10 text-overflow — نمط الثلاث خصائص
🔧 الصياغة التقنية
css
.title {
  white-space: nowrap;   /* منع النزول لسطر جديد */
  overflow: hidden;        /* إخفاء الزيادة */
  text-overflow: ellipsis; /* استبدالها بـ ... */
}
🎯 الربط

"text-overflow: ellipsis لوحدها مبتعملش حاجة - لازم تجهّزي الظرف الصح الأول: تمنعي النزول لسطر جديد (nowrap)، وتخفي الزيادة (overflow: hidden)، وبعدين ellipsis بس هي اللي بتحدد شكل الإخفاء ده. الثلاثة مع بعض، مش واحدة بديلة عن التانية."

🎨 في Figma

خاصية "Truncate text" (toggle واحد جوه لوحة الـ Text properties) بتعمل نفس التأثير البصري تلقائيًا - سطر واحد + نقاط في الآخر، من غير ما تحتاجي تركّبي 3 خصائص منفصلة زي CSS.

12.11 🆕 overflow-wrap / word-break — باج شائع جدًا في production
🧠 الفكرة المبسطة

تخيلي كلمة طويلة جدًا (زي رابط إنترنت كامل) مكتوبة من غير أي مسافات. المتصفح بيحاول "يحترم" الكلمة كوحدة واحدة ومش بيقصّها - فبتطلع بره حدود الصندوق بالكامل بدل ما تتلف لسطر جديد.

🔧 الصياغة التقنية
css
.comment-text {
  overflow-wrap: break-word; /* اسمح بكسر الكلمة الطويلة لو مفيش مكان تانية */
}

/* أو الأشد صرامة */
.url-display {
  word-break: break-all; /* اكسري في أي مكان، حتى لو نص الكلمة */
}
🎯 الربط

"ده باج شائع جدًا في أي تطبيق فيه محتوى من المستخدم (تعليقات، بايوهات، روابط) - نص عادي شغال تمام، وفجأة لينك طويل أو كلمة غريبة بتكسر الـ layout كله وتطلع بره الـ card. overflow-wrap: break-word هو الحل القياسي، وهو أكثر 'لطفًا' من word-break: break-all لأنه بيكسر الكلمة بس لو فعلاً مفيش مكان تانية، مش بيكسر كل الكلمات بشكل عشوائي."

12.12 Multi-line Text Truncation
🔧 الصياغة التقنية
css
.description {
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
}
⚠️ ملاحظة Browser Support

الصيغة دي (-webkit-) قديمة تاريخيًا لكنها لسه الأشهر عمليًا لدعم المتصفحات الواسع. فيه صيغة حديثة (line-clamp بدون prefix) لكن لازم مراعاة الـ browser support قبل الاعتماد عليها بمفردها في production.

🎯 الربط

"مختلفة عن text-overflow: ellipsis اللي بتشتغل لسطر واحد بس - ده الحل لما محتاجة تقصّي بعد عدد أسطر معين (زي وصف منتج بـ 3 أسطر بالظبط)."

🎨 في Figma

نفس toggle الـ "Truncate text" بيديكي خيار تحددي عدد الأسطر (مش سطر واحد بس)، فبيغطي نفس فكرة الـ multi-line clamp بواجهة مباشرة.

12.13 🆕 text-wrap: balance — خاصية حديثة مهمة للعناوين
🧠 الفكرة المبسطة

تخيلي عنوان اتقسم لسطرين، وسطر طويل قوي وسطر قصير جدًا فيه كلمة واحدة بس معلّقة - شكلها مش مريح بصريًا. text-wrap: balance بتوزّع الكلمات بذكاء عشان الأسطر تبقى متقاربة الطول قد الإمكان.

🔧 الصياغة التقنية
css
h1, h2 {
  text-wrap: balance;
}
🎯 الربط

"خاصية حديثة جدًا ومفيدة تحديدًا للعناوين اللي بتتلف لأكتر من سطر - بتحل مشكلة بصرية كانت قبل كده محتاجة تدخل يدوي (<br> في مكان معين) أو حتى JavaScript. الدعم في المتصفحات بتاعتها لسه نسبيًا حديث، فلازم تتأكدي من browser support المطلوب لمشروعك قبل الاعتماد عليها كحل أساسي."

12.14 Web Fonts & @font-face
🔧 الصياغة التقنية
css
@font-face {
  font-family: "Inter";
  src: url("/fonts/inter-400.woff2") format("woff2");
  font-weight: 400;
  font-style: normal;
  font-display: swap;
}
🎯 الربط

"font-display: swap بتخلي المتصفح يعرض النص فورًا بخط الـ fallback، وبعدين 'يبدّله' لما الخط المخصص يخلص تحميل - ده بيمنع مشكلة الـ FOIT (Flash of Invisible Text) اللي فيها النص بيفضل مختفي تمامًا لحد ما الخط يوصل."

12.15 Variable Fonts
🔧 الصياغة التقنية
css
h1 {
  font-weight: 450; /* قيمة وسطية، مش رقم تقليدي زي 400/500 */
}
🎯 الربط

"بدل ما تحمّلي 4 ملفات خط منفصلة لكل وزن، ملف واحد Variable Font بيدّيكي range كامل من الأوزان - وده بيقلل حجم التحميل الكلي غالبًا."

🎨 في Figma

⚠️ Figma بتدعم الـ Variable Fonts (بتظهر كـ slider بدل قائمة أوزان ثابتة)، لكن التفاصيل الدقيقة لسلوك كل خط بتعتمد على الملف نفسه، فيفضل تتأكدي من التطابق الفعلي وقت التصدير.

12.16 Typography في Design System
🔧 الصياغة التقنية
css
:root {
  --font-size-body: 1rem;
  --font-size-heading: 2rem;
  --font-size-display: 3rem;
}
🎯 الربط

"بدل قيم عشوائية لكل component، بنبني Typography Scale ثابت (Display, H1, H2, Body, Caption...) ونربطها بـ Design Tokens - هنكمل التفاصيل دي في فصل الـ CSS Variables & Theming."

🎨 في Figma

Text Styles هي بالظبط نفس مفهوم الـ Typography Scale ده - بتحفظي مجموعة من الأنماط المسماة (Heading 1, Body, Caption...) وتطبقيها على أي نص، وأي تعديل على الـ style بينعكس على كل الأماكن اللي مستخدماه، بالظبط زي فكرة الـ Design Tokens.

🎯 أشهر أسئلة Senior
1. ليه نستخدم rem للـ typography؟

بتدّي scale متسق مبني على الـ root font size، وبتدعم accessibility واستجابة أفضل.

2. ليه line-height بدون وحدة أفضل؟

بتتحسب ديناميكيًا حسب حجم خط كل عنصر، وبتتجنب مشكلة الـ Compounding اللي بتحصل مع em.

3. إزاي تعملي ellipsis لسطر واحد؟
css
white-space: nowrap; overflow: hidden; text-overflow: ellipsis;
4. إزاي تمنعي كلمة طويلة إنها تكسر الـ layout؟

باستخدام overflow-wrap: break-word عشان تسمحي بكسر الكلمة لما مفيش مكان تانية.

5. ليه منشيلش الـ underline من الروابط من غير بديل؟

عشان التمييز البصري بين الرابط والنص المحيط مهم للـ usability والـ accessibility.

6. إيه الفرق بين text-transform وتغيير النص فعليًا في الـ HTML؟

text-transform تحويل بصري بس - الـ screen reader بيقرا النص الأصلي زي ما هو في الـ DOM، مش الشكل المحوّل.

🧠 Senior Mental Model
                 TYPOGRAPHY
                      │
       ┌──────────────┼──────────────┐
       ↓              ↓              ↓
    Font           Sizing         Spacing
       │              │              │
 font-family      font-size     line-height (unitless!)
 font-weight      clamp()       letter-spacing
 text-transform
       │
       └──────────────┐
                      ↓
              Overflow Handling
                      │
        ┌─────────────┼─────────────┐
        ↓             ↓             ↓
  Single-line     Multi-line    Long words
  (3-property     (line-clamp)  (overflow-wrap)
   ellipsis)
📋 Chapter Summary — مراجعة سريعة
Property	وظيفتها الأساسية
font-family	نوع الخط + fallback stack
font-size	حجم النص
font-weight	سمك الخط
text-transform	تحويل بصري (uppercase/capitalize) بدون تغيير الـ DOM
line-height	مسافة رأسية بين الأسطر (unitless موصى بيه)
letter-spacing	مسافة بين الحروف
text-align: start/end	محاذاة تتكيف مع اتجاه اللغة
text-decoration	زخرفة النص (احذري الـ accessibility)
text-overflow + nowrap + overflow: hidden	ellipsis لسطر واحد
overflow-wrap: break-word	منع الكلمات الطويلة من كسر الـ layout
text-wrap: balance	توزيع متوازن لأسطر العناوين
@font-face + font-display: swap	تحميل خطوط خارجية بدون FOIT
Keywords للحفظ
font-family · fallback stack · system-ui
font-weight · text-transform · line-height (unitless)
letter-spacing · text-align: start/end
text-overflow · white-space: nowrap · overflow: hidden
overflow-wrap · word-break · text-wrap: balance
@font-face · font-display: swap · FOIT · FOUT
Variable Fonts · Typography Scale
🎤 جملتك النموذجية في المقابلة

"I treat typography as a system, not isolated properties — a consistent type scale tied to design tokens, unitless line-height to avoid compounding issues, and text-align: start/end for RTL-ready alignment. For overflow, I distinguish single-line ellipsis (which needs white-space, overflow, and text-overflow together) from long unbroken words breaking layout, which overflow-wrap: break-word handles separately."   
