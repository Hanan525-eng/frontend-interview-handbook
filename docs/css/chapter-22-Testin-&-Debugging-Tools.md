Chapter 22 — Testing & Debugging Tools 

│   ├── DevTools: Grid Inspector
│   ├── DevTools: Flexbox Inspector
│   ├── Computed Styles & Specificity debugging
│   ├── Forcing pseudo-class states
│   ├── Quick outline debugging trick
│   ├── Visual Regression Testing (Percy, Chromatic)
│   └── Linting (Stylelint)
السؤال الاول
الفرق بين "تخمين" و"تشخيص" في CSS Debugging
🧠 الفكرة المبسطة

تخيلي دكتور بيشخّص مريض - مش بيقول "يمكن معدتك" وبيدّيلك دوا عشوائي. بيفحص، بياخد تحاليل، بيتأكد من السبب، وبعدين يعالج. الـ CSS Debugging نفس المنطق بالظبط.

🔧 الصياغة التقنية
UI Problem → Inspect → Identify source → Test hypothesis → Fix → Verify
🎯 الربط

"القاعدة الذهبية للفصل كله: متعدّليش properties عشوائي لحد ما الشكل يظبط - استخدمي DevTools عشان تفهمي ليه المتصفح طلّع النتيجة دي، وبعدين صلّحي السبب الحقيقي."

22.2 Grid Inspector
🔧 الصياغة التقنية
css
.dashboard {
  display: grid;
  grid-template-columns: 240px 1fr 320px;
  gap: 24px;
}

Grid overlay بيوريكي: Grid lines، Tracks، Areas، Gaps، Item placement.

🎯 الربط

"بدل ما تبدئي تعدّلي margin/padding/width عشوائي لما الـ Grid مش متصرف زي المتوقع، افتحي Grid Inspector الأول واسألي: عدد الأعمدة صح؟ الـ gap صح؟ العنصر في الـ track المتوقع؟ فيه implicit tracks مش متوقعة؟"

22.3 Flexbox Inspector
🔧 الصياغة التقنية
css
.sidebar {
  display: flex;
  flex-direction: column;
  height: 100vh;
}
.footer { margin-top: auto; }
🎯 الربط

"مثال كلاسيكي: 'ليه الـ footer نزل لتحت؟' - Flexbox Inspector بتوريكي بصريًا إن المساحة الرأسية الفاضية اتاخدت بواسطة margin-top: auto، بدل ما تحفظي الـ behavior نظريًا بس."

22.4 Styles vs Computed
🔧 الصياغة التقنية
css
.title { color: red; }         /* ممكن تبقى crossed-out */
.card .title { color: blue; }   /* دي اللي كسبت - أعلى specificity */
Panel	بيجاوب على
Styles	إيه القواعد المتنافسة، ومين اتلغى
Computed	إيه القيمة النهائية اللي المتصفح فعليًا مستخدمها
🎯 الربط

"استخدمي الاتنين مع بعض: Styles بتوريكي ليه فيه تنافس، Computed بتوريكي مين كسب فعليًا."

22.5 🆕 إجبار حالات الـ Pseudo-class في DevTools
🧠 الفكرة المبسطة

تخيلي عايزة تفحصي CSS خاصة بلحظة مؤقتة (زي لما حد بيبص عليكي في الكاميرا لثانية بس) - مستحيل تمسكي اللحظة دي وتفتحي أدوات الفحص في نفس الوقت من غير ما "تجمّدي" اللحظة الأول.

🔧 الصياغة التقنية

في Chrome DevTools: افتحي الـ Elements panel → حددي العنصر → دوسي على ":hov" (أو من الـ Styles pane) → اختاري :hover, :focus, :active, أو :visited.

🎯 الربط

"من غير الأداة دي، فحص CSS خاص بـ :hover أو :focus صعب جدًا - إما تفضلي ماسكة الماوس فوق العنصر (وده بيمنعك تفتحي DevTools تتفاعلي معاه في نفس الوقت)، أو تعدّلي الكود مؤقتًا بس تنسي ترجعيه. 'إجبار' الحالة بيخليها تفضل ثابتة في الـ Styles panel، فتقدري تفحصي وتعدّلي عليها بارتياح - مفيدة جدًا لما تصمّمي أو تصلّحي hover states، focus indicators (فصل 18)، أو link states."

22.6 🆕 Quick Outline Debugging Trick
🧠 الفكرة المبسطة

تخيلي عايزة تفهمي حدود كل غرفة في شقة من غير ما تحتاجي تقيسي كل حيطة بالمسطرة - أسرع حل تحطي خط واضح حوالين كل غرفة وتبصي بعينك.

🔧 الصياغة التقنية
css
* {
  outline: 1px solid red;
}

أو أكتر تنظيمًا (ألوان مختلفة لمستويات مختلفة):

css
* { outline: 1px solid hsl(calc(var(--depth, 0) * 40) 80% 50%); }
⚠️ ليه outline مش border؟

outline مبيأثرش على الـ layout أو الـ box model (مش بياخد مساحة زي الـ border)، فبتقدري تحطيه مؤقتًا على كل عنصر بالصفحة من غير ما تكسري أي حاجة أو تغيّري مقاسات حقيقية.

🎯 الربط

"دي أسرع أداة تشخيص بصري قبل ما تفتحي أي Inspector متخصص - في ثانية واحدة بتشوفي أي عنصر واخد مساحة غريبة، أي padding زيادة عن المتوقع، أو أي عنصر خارج حدود أبوه. كتير من الـ Seniors بيبدأوا بيها قبل حتى ما يفكروا في Grid/Flex Inspector، خصوصًا لو المشكلة مش واضح أصلًا هل هي Grid ولا Flex ولا حاجة تانية تمامًا زي overflow أو margin collapsing."

22.7 Specificity Debugging
🔧 الصياغة التقنية
css
button { background: gray; }      /* (0,0,0,1) */
.button { background: blue; }      /* (0,0,1,0) */
#submit { background: red; }        /* (0,1,0,0) - كسبت */
⚠️ متصلحيش بـ !important فورًا

اسألي بالترتيب: Specificity؟ Cascade layer؟ Source order؟ Selector أدق؟ Inline style؟ - وبعدين صلّحي السبب الحقيقي.

22.8 Debugging Custom Properties
🔧 الصياغة التقنية
css
:root { --primary: #2a4b8d; }
.button { background: var(--primary); }

اللون غلط؟ افحصي جوه Computed إن فيه [data-theme="dark"] { --primary: ... } غيّرت الـ token جوه سياق مختلف.

🎯 الربط

"ده مباشرة مرتبط بفصل 14 - قيمة الـ variable ممكن تتغيّر في أماكن كتير (media query، data-theme، scope مختلف)، والـ Computed tab هي أسرع طريقة تعرفي مين فعليًا اللي بيحدد القيمة النهائية دلوقتي."

22.9 Visual Regression Testing
🔧 الصياغة التقنية
Baseline screenshot → New commit → Render → Compare → Fail/Review
🎯 الربط

"الفرق الجوهري عن Unit Testing: Unit Test بيسأل 'الـ logic شغالة؟'، Visual Regression بيسأل 'الشكل اتغيّر من غير قصد؟'. مهم جدًا في design systems لأن تعديل بسيط في component مشترك (زي .button) ممكن يأثر على شاشات كتير من غير ما الـ developer يعرف."

Percy vs Chromatic
	Percy	Chromatic
الطبيعة	منصة Visual Testing عامة	مرتبطة بقوة بـ Storybook
الأنسب لـ	مشاريع عامة	مشاريع بتستخدم Storybook للـ component stories أصلًا
22.10 Stylelint
🔧 الصياغة التقنية
json
{
  "extends": "stylelint-config-standard",
  "rules": {
    "max-nesting-depth": 3
  }
}
🎯 الربط

"زي ESLint للـ JavaScript، بس للـ CSS. بيكتشف syntax errors، duplicate declarations، naming problems، وممكن يفرض قواعد الـ architecture اللي اخترتيها (فصل 19) - لو BEM، ممكن قواعد naming convention؛ لو Tailwind، قواعد مختلفة تمامًا مناسبة للـ utility classes."

22.11 CSS Debugging Checklist
□ العنصر متحدد صح؟
□ ملف الـ CSS متحمّل؟
□ الـ selector matching؟
□ فيه rule متلغية (crossed out)؟
□ المشكلة specificity؟
□ فيه inheritance متداخلة؟
□ Source order له دور؟
□ فيه @layer؟
□ الأب Flexbox/Grid؟
□ فيه width/height constraints؟
□ overflow بيخفي العنصر؟
□ z-index/stacking context له دور؟
□ الـ computed value زي المتوقع؟
🧠 Senior Mental Model
CSS Bug
   ↓
متتخمنيش
   ↓
افحصي (Grid/Flex Inspector, outline trick, forced states)
   ↓
افهمي النتيجة المحسوبة (Styles + Computed)
   ↓
حددي السبب (Specificity/Cascade/Layout)
   ↓
اختبري الفرضية في DevTools مباشرة
   ↓
صلّحي
   ↓
تأكدي بصريًا + Visual Regression لو متاح
🎯 Senior Interview Questions
1. إزاي تشخّصي مشكلة layout في CSS؟

أفحص العنصر، أحدد هل الأب Flexbox أو Grid، أستخدم الـ Inspector المناسب، أفحص computed styles والـ rules المتلغية، وبعدين أختبر الفرضية قبل ما أطبّق الحل.

2. الفرق بين Styles و Computed؟

Styles بتوري القواعد المتنافسة (بما فيها المتلغية). Computed بتوري القيمة النهائية اللي المتصفح فعليًا مستخدمها.

3. إزاي تفحصي CSS خاص بـ :hover من غير ما تفضلي ماسكة الماوس؟

من خلال "Force state" جوه Elements panel في DevTools - بتخلي الحالة تفضل ثابتة للفحص.

4. إيه أسرع تقنية تشخيص بصري لمشكلة layout؟

* { outline: 1px solid red; } - بتوريكي حدود كل عنصر فورًا من غير ما تأثري على الـ box model، لأن outline مبياخدش مساحة زي border.

5. Visual Regression Testing بتختبر إيه بالظبط؟

مقارنة الشكل البصري الحالي بـ baseline معتمد عشان تكتشفي تغييرات غير مقصودة، مش الـ logic.

6. إيه Stylelint؟

Linter للـ CSS بيفرض معايير الكود ويكتشف patterns مشكوك فيها أو invalid.

📋 Chapter Summary — مراجعة سريعة
الأداة	الاستخدام
Grid Inspector	فحص tracks/gaps/placement بصريًا
Flexbox Inspector	فهم توزيع المساحة على المحاور
Styles panel	القواعد المتنافسة
Computed panel	القيمة النهائية الفعلية
Force pseudo-class state	فحص :hover/:focus/:active بثبات
outline trick	تشخيص بصري سريع من غير تأثير على layout
Visual Regression (Percy/Chromatic)	كشف تغييرات بصرية غير مقصودة
Stylelint	جودة واتساق الكود
Keywords للحفظ
Grid Inspector · Flexbox Inspector
Styles vs Computed · Specificity Debugging
Force pseudo-class state · outline debugging trick
Visual Regression Testing · Percy · Chromatic
Stylelint · Hypothesis Testing
🎤 جملتك النموذجية في المقابلة

"My CSS debugging process starts with inspection, not guessing — the Grid or Flexbox inspector for layout issues, Computed styles to see what actually won the cascade, and forcing pseudo-class states when debugging hover or focus styles. For a fast first pass, I still reach for the classic outline: 1px solid red trick since it reveals box boundaries instantly without affecting layout. For catching unintended visual changes at scale, I rely on visual regression tools like Percy or Chromatic rather than manual review."   
