 Chapter 21 — CSS Performance 

 │   ├── Reflow
│   ├── Repaint
│   ├── Compositing & GPU layers
│   ├── Expensive Properties
│   ├── CSS Containment
│   │   ├── contain
│   │   └── content-visibility
│   ├── Critical CSS & unused CSS
│   ├── Layout Thrashing
│   └── Performance best practices
السؤال الاول
إزاي المتصفح بيحوّل تغيير CSS لـ Rendering Work؟
🧠 الفكرة المبسطة

تخيلي مصنع فيه خط إنتاج بمراحل متتالية: تصميم → تجميع → طلاء → تغليف. مش كل تعديل بيحتاج يمر بكل المراحل - لو غيّرتي لون التغليف بس، مش لازم ترجعي لمرحلة التصميم من الأول.

🔧 الصياغة التقنية
CSS/DOM Change → Style Calculation → Layout → Paint → Compositing

مش كل تغيير بيوصل لكل المراحل - وده أساس فهم الـ performance كله.

🎯 الربط

"السؤال الأهم مش 'إيه الـ properties السيئة' - السؤال 'التغيير ده بيوصل لأنهي مرحلة، وهل ممكن يقف عند مرحلة أبكر وأرخص؟'"

21.2 Reflow / Layout
🔧 الصياغة التقنية
css
.box { width: 500px; } /* ممكن يسبب إعادة حساب layout */

Properties ممكن تسبب Layout: width, height, margin, padding, top, left, font-size.

🎯 الربط

"Layout مكلفة لأن تغيير عنصر ممكن يأثر على عناصر تانية - الأب، الإخوة، وأي حاجة مرتبطة بمكانه. المصطلح الحديث في documentation المتصفحات بقى غالبًا 'Layout' بدل 'Reflow'، لكن نفس المفهوم."

21.3 Repaint
🔧 الصياغة التقنية
css
.box { background: blue; } /* Layout زي ما هو، بس محتاج يترسم تاني */
🎯 الربط

"تغيير اللون مش دايمًا محتاج إعادة حساب المكان والمقاس - بس محتاج 'يترسم' تاني بلون مختلف. أرخص من Layout، لكنه لسه شغل حقيقي على المتصفح."

21.4 Compositing & GPU Layers
🔧 الصياغة التقنية
css
.card { transform: translateX(100px); }
.card { opacity: 0.5; }
⚠️ نقطة دقيقة

متقوليش إن transform دايمًا "بيستخدم GPU" أو دايمًا أسرع. المتصفح هو اللي بيقرر استراتيجية الـ compositing، وإنشاء layers ليه تكلفة (ذاكرة) هو كمان.

🎯 الربط

"لو قدرنا ننفذ animation في مرحلة الـ Compositing بس (من غير المرور بـ Layout/Paint)، بنتجنب شغل كتير. transform وopacity غالبًا بيدوا أقرب طريق للمسار ده، لكن مش مضمون 100% في كل حالة."

21.5 مثال عملي: Modal Animation
🔧 الصياغة التقنية
css
/* ❌ محتمل يسبب Layout في السياق ده */
.modal { top: 0; }
.modal.open { top: 100px; }

/* ✅ أقرب لـ Composite بس */
.modal { transform: translateY(-20px); opacity: 0; }
.modal.open { transform: translateY(0); opacity: 1; }
🎯 الربط

"نفس الحركة البصرية، لكن الطريق المتصفحي مختلف تمامًا خلف الكواليس."

21.6 Expensive Properties
🔧 الصياغة التقنية

مفيش قائمة ثابتة "سيئة دايمًا" - السؤال الصح:

هل التغيير ده بيسبب Layout؟
هل بيسبب Paint؟
ولا ممكن يفضل جوه Compositing بس؟
النوع	أمثلة
Layout-triggering	width, height, margin, top, left
Paint-heavy	box-shadow, background, border, color
Composite-friendly	transform, opacity
🎯 الربط

"القاعدة العملية: transition: all من غيرها تحديد، بتخليكي عرضة لتحريك خصائص Layout-triggering بدون قصد."

21.7 CSS Containment — contain
🧠 الفكرة المبسطة

تخيلي عندك شقق منفصلة في عمارة - لو عملتي تجديد جوه شقة واحدة، مش لازم تفحصي كل شقة تانية في العمارة عشان تتأكدي إن التجديد ده معملش تأثير عليهم. contain بتقول للمتصفح "الجزء ده مستقل، متفترضيش إنه هيأثر على باقي الصفحة."

🔧 الصياغة التقنية
css
.widget { contain: layout; }  /* يحد تأثيرات layout للعنصر ده */
.widget { contain: paint; }   /* يحد تأثير الرسم خارج حدود العنصر */
.widget { contain: layout paint; } /* الاتنين مع بعض */
⚠️ تحذير

contain: strict (الجمع الأقوى) بيغيّر behavior مهم (sizing, layout, painting) - متستخدميهاش عشوائيًا.

🎯 الربط

"مفيدة جدًا في dashboards كبيرة فيها widgets مستقلة عن بعض بحدود واضحة - مش أداة تحطيها على كل عنصر 'احتياطًا'."

21.8 content-visibility — أهم أداة Performance حديثة
🔧 الصياغة التقنية
css
.section {
  content-visibility: auto;
}

المتصفح بيقدر يأجّل rendering work للمحتوى برة الـ viewport لحد ما يقرب يكون محتاج فعليًا.

⚠️ الفرق الجوهري عن display: none

display: none = العنصر مش موجود في الـ rendering/layout خالص. content-visibility: auto = العنصر لسه جزء من الصفحة، بس شغل الـ rendering بتاعه بيتأجل لما يكون خارج الشاشة.

🎯 الربط

"الفايدة الحقيقية بتظهر في صفحات طويلة جدًا (زي جداول بيانات أو قوائم كبيرة) - بدل ما المتصفح يعمل layout/paint لآلاف العناصر البعيدة عن الشاشة، بيأجل الشغل ده لحد ما يبقى قريب فعليًا من الحاجة."

ملاحظة مهمة عن الأرقام: التحسن الفعلي بيعتمد كليًا على حجم وتعقيد صفحتك - محتاجة تقيسي بنفسك (DevTools Performance) مش تفترضي نسبة ثابتة من مصدر خارجي.

21.9 contain-intrinsic-size
🔧 الصياغة التقنية
css
.section {
  content-visibility: auto;
  contain-intrinsic-size: 500px; /* تقدير حجم المحتوى قبل الـ render */
}
🆕 الصيغة الأحدث: auto <size>
css
.section {
  content-visibility: auto;
  contain-intrinsic-size: auto 500px;
}
🎯 الربط

"من غير تقدير الحجم، المتصفح ممكن يفترض العنصر ارتفاعه صفر لحد ما يترسم فعليًا، وده بيسبب 'قفزة' في الـ scrollbar وموضع المحتوى. الصيغة auto <size> بتقول للمتصفح 'استخدمي الحجم التقديري ده في البداية، لكن لو العنصر اترسم فعليًا قبل كده (زي لما المستخدم يرجع يعلى بعد ما نزل تحت)، افتكري آخر حجم حقيقي بدل ما ترجعي للتقدير من الأول' - وده بيقلل مشاكل الـ layout shift أكتر من الصيغة القديمة."

21.10 متى أستخدم Containment؟
🎯 الربط

"مش 'حطي contain على كل عنصر' - لكن لما يكون عندك clear performance boundary: صفحات طويلة، dashboards كبيرة، مكونات متكررة ومستقلة عن بعض."

21.11 Critical CSS & Unused CSS
🔧 الصياغة التقنية

Critical CSS = الـ CSS الضروري لعرض الجزء الأول من الصفحة (above-the-fold) بسرعة.

🎯 الربط

"في frameworks حديثة زي Next.js، كتير من الـ optimization ده بيتعمل تلقائي عن طريق الـ framework/build tooling. متبدأيش تعملي Critical CSS يدوي إلا لو فيه مشكلة أداء فعلية اتقاست ومؤكدة."

Unused CSS: classes معرّفة بس مش مستخدمة فعليًا (زي component اتشال بس الـ CSS بتاعه فضل). بتزوّد حجم الملف من غير أي فايدة. أدوات زي DevTools Coverage أو build analysis بتساعد تكتشفيها.

21.12 Layout Thrashing
🧠 الفكرة المبسطة

تخيلي بتسألي "كام كرسي فاضي؟" وبعدين "حطي كرسي جديد" وبعدين "كام كرسي فاضي دلوقتي؟" وبعدين "حطي كرسي تاني" - كل مرة بتسألي، لازم حد يعدّ الكراسي كلها من الأول تاني بدل ما يحسب مرة واحدة في الآخر.

🔧 الصياغة التقنية
js
// ❌ Layout Thrashing - تناوب Write/Read بيجبر إعادة حساب متكررة
element.style.width = "500px";
const height = element.offsetHeight; // Read بيجبر المتصفح يحسب layout فورًا
element.style.width = "600px";
const width = element.offsetWidth; // نفس المشكلة تاني
🎯 الربط

"مش خاصية CSS بحد ذاتها، لكنها نقطة مهمة جدًا في التفاعل بين CSS وJavaScript. الحل: جمّعي كل الـ writes مع بعض، وكل الـ reads مع بعض، بدل التناوب بينهم."

21.13 Performance Best Practices
transform/opacity للـ animations بدل left/top/width/height
تجنبي transition: all
مش كل حاجة محتاجة animation (1000 صف جدول مش محتاجين animate عند الـ render)
will-change مش "خليها أسرع" - هي hint ليها تكلفة ذاكرة، استخدميها بحذر ولسبب مقاس
21.14 DevTools Performance — القياس قبل التخمين
🎯 الربط

"متقوليش 'أعتقد إن box-shadow هي المشكلة' - قيسي فعليًا. استخدمي DevTools Performance وراقبي Frames/Rendering/Layout/Paint/Composite. العقلية الصح: Measure → Identify bottleneck → Optimize → Measure again، مش افتراض رقم جاهز من مقال قرأتيه."

🎯 Senior Interview Questions
1. الفرق بين Reflow وRepaint؟

Layout بيحسب الأبعاد والمواقع، Repaint بترسم البكسلات بصريًا. تغيير Layout ممكن يستدعي Repaint بعده.

2. transform دايمًا بتستخدم GPU؟

لأ. المتصفح هو اللي بيقرر، وإنشاء compositor layers ليه تكلفة كمان.

3. إيه الفرق بين display: none وcontent-visibility: auto؟

display: none بيشيل العنصر من الـ rendering تمامًا. content-visibility: auto بيأجل شغل الـ rendering بس، والعنصر لسه جزء من الصفحة.

4. content-visibility: auto بتحسّن الأداء بنسبة كام؟

مفيش رقم ثابت عام - بيعتمد كليًا على حجم وتعقيد الصفحة. لازم تتقاس فعليًا بـ DevTools مش تُفترض من رقم جاهز.

5. إيه الـ Layout Thrashing؟

تناوب متكرر بين DOM writes وreads بيجبر المتصفح على إعادة حساب layout بشكل متكرر ومكلف.

6. will-change أداة تحسين أداء مضمونة؟

لأ. هي hint للمتصفح، مش "زرار أسرع" - استخدامها الزايد بيزود استهلاك الذاكرة.

📋 Chapter Summary — مراجعة سريعة
المفهوم	القاعدة السريعة
Layout/Reflow	إعادة حساب أبعاد ومواقع
Repaint	إعادة رسم بصري بدون تغيير الأبعاد
Compositing	دمج الطبقات - transform/opacity غالبًا هنا
contain	حدود صريحة تمنع افتراض تأثير على باقي الصفحة
content-visibility: auto	تأجيل rendering للمحتوى البعيد عن الشاشة
contain-intrinsic-size: auto <size>	حجم تقديري + تذكر آخر حجم حقيقي
Critical CSS	الأساسي لعرض أول شاشة بسرعة
Unused CSS	classes مش مستخدمة، بتزود الحجم من غير فايدة
Layout Thrashing	تناوب Write/Read بيجبر layout متكرر
will-change	Hint له تكلفة، مش تحسين مضمون
Keywords للحفظ
Layout (Reflow) · Repaint · Compositing
GPU / Compositor Layers · transform · opacity
contain · content-visibility · contain-intrinsic-size
Critical CSS · Unused CSS · Layout Thrashing
will-change · DevTools Performance
🎤 جملتك النموذجية في المقابلة

"I think about CSS performance through the rendering pipeline — Style, Layout, Paint, Composite — and prefer animating transform/opacity since they can often stay within compositing. For long pages, content-visibility: auto defers rendering work for off-screen content, paired with contain-intrinsic-size: auto <size> to avoid layout shift. But I never assume a fixed performance percentage from an article — I measure with DevTools first, identify the actual bottleneck, then optimize."   


---

🔙 **[رجوع للمرجع الشامل (كل الفصول)](CSS-Reference-Handbook.md)**
