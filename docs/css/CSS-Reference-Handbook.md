# 📘 CSS Reference Handbook
### مرجعك الشامل: مراجعة سريعة + دليل مشروع + تحضير مقابلات

> **كيفية الاستخدام:**
> - 🔍 **نسيت نقطة؟** استخدمي الفهرس واقفزي للقسم المطلوب مباشرة.
> - 💻 **بتبدئي مشروع جديد؟** كل فصل فيه "Quick Pattern" جاهز للنسخ.
> - 🎤 **قبل مقابلة؟** روحي مباشرة لفصل 23 في الآخر، وكل فصل فيه قسم 🎤 إجابة جاهزة.
> - الكود دايمًا بالإنجليزي (اتجاه LTR طبيعي)، والشرح بالعربي (اتجاه RTL) — من غير خلط بين الاتنين في نفس السطر.

---

## 📑 الفهرس السريع

| # | الفصل | أهم ما فيه |
|---|---|---|
| 1 | [CSS Fundamentals](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-1-css-fundamentals.md) | Syntax, Rules, طرق التطبيق |
| 2 | [Selectors](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-2-css-selectors.md) | أنواع الـ Selectors + Specificity |
| 3 | [Cascade & Specificity](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-3-cascade-specificity.md) | Origin, Specificity, !important |
| 4 | [Box Model](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-4-box-model.md) | Content/Padding/Border/Margin, box-sizing |
| 5 | [Display & Visibility](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-5-display-visibility.md) | block/inline/none, opacity vs visibility |
| 6 | [Positioning](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-6-positioning.md) | relative/absolute/fixed/sticky, Containing Block |
| 7 | [Flexbox](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-7-flexbox.md) | Main/Cross Axis, align-self, min-width bug |
| 8 | [CSS Grid](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-8-css-grid.md) | fr, auto-fit/auto-fill, محاذاة Grid |
| 9 | [Responsive Design](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-9-responsive-design.md) | Viewport meta, Mobile First, Container Queries |
| 10 | [Units & Values](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-10-css-units-values.md) | px/%/em/rem/vw/ch, calc/min/max/clamp |
| 11 | [Colors & Backgrounds](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-11-colors-backgrounds.md) | opacity vs alpha, WCAG contrast |
| 12 | [Typography](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-12-typography.md) | line-height, ellipsis, overflow-wrap |
| 13 | [CSS Functions](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-13-css-functions-math-and-color.md) | calc/min/max/clamp, color-mix/oklch |
| 14 | [Variables & Theming](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-14-css-variables-and-theming.md) | Custom Properties, Design Tokens |
| 15 | [Transitions & Animations](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-15-transitions-and-animations.md) | transform/opacity, height:auto bug |
| 16 | [Advanced CSS](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-16-advanced-css.md) | Nesting, Container Queries, :has(), @layer |
| 17 | [RTL & i18n](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-17-rtl-and-internationalization.md) | Logical Properties, dir, Icon Mirroring |
| 18 | [Accessibility](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-18-accessibility-a11y-in-css.md) | focus-visible, sr-only, forced-colors |
| 19 | [CSS Architecture](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-19-css-architecture.md) | BEM, CSS Modules, Tailwind, CSS-in-JS |
| 20 | [Browser Compatibility](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-20-browser-compatibility-and-progressive-enhancement.md) | @supports, Progressive Enhancement |
| 21 | [Performance](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-21-css-performance.md) | Layout/Paint/Composite, content-visibility |
| 22 | [Testing & Debugging](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-22-testing-and-debugging-tools.md) | DevTools, Visual Regression, Stylelint |
| 23 | [Senior Interview Map](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-23-senior-css-interview-questions.md) | خريطة قرار شاملة + أهم 15 سؤال |

---
---

## 1️⃣ CSS Fundamentals
📎 **الفصل الكامل على GitHub:** [chapter-1-css-fundamentals.md](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-1-css-fundamentals.md)

**الفكرة الأساسية:** CSS لغة declarative بتوصف الـ presentation والـ layout، مش مجرد ألوان.

```css
selector {
  property: value;   /* Declaration */
}
```

| المكوّن | المثال |
|---|---|
| Selector | `button` |
| Property | `color` |
| Value | `red` |
| Declaration | `color: red;` |
| Declaration Block | `{ ... }` |
| CSS Rule | Selector + Declaration Block |

**طرق التطبيق:**

| الطريقة | مثال | الاستخدام |
|---|---|---|
| Inline | `<p style="color:red">` | تجنبيها |
| Internal | `<style>` في `<head>` | صفحة واحدة استثنائية |
| External | `<link rel="stylesheet">` | **Best Practice** |

**⚠️ فخ شائع:** لو استخدمتِ الطرق التلاتة مع بعض على نفس العنصر → Inline بتكسب دايمًا لأنها عندها **أعلى Specificity** `(1,0,0,0)`، **مش** لأنها "الأحدث". لو Internal وExternal بس، الأخير في الكود بيكسب (Source Order).

**🎤 مقابلة:** *"CSS is a declarative language that describes presentation, layout, and visual behavior. An External Stylesheet via `<link>` is the industry standard for reusability, caching, and separation of concerns."*

---

## 2️⃣ Selectors
📎 **الفصل الكامل على GitHub:** [chapter-2-css-selectors.md](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-2-css-selectors.md)

```css
*                    /* Universal — (0,0,0,0) */
div                  /* Type — (0,0,0,1) */
.card                /* Class — (0,0,1,0) */
#header              /* ID — (0,1,0,0) */
[type="text"]        /* Attribute — (0,0,1,0) */
[class^="btn-"]      /* يبدأ بـ */
[class$="-lg"]       /* ينتهي بـ */
[class*="nav"]       /* يحتوي على */

div p                /* Descendant — كل الأحفاد */
div > p              /* Child — أبناء مباشرين بس */
h1 + p               /* Adjacent Sibling — أول شقيق مباشر */
h1 ~ p               /* General Sibling — كل الأشقاء التاليين */

a:hover              /* Pseudo-class — (0,0,1,0) نفس وزن Class */
p::first-letter      /* Pseudo-element — (0,0,0,1) نفس وزن Element */
```

**⚠️ فخ شائع جدًا:** Pseudo-class مالهاش وزن "متوسط" مستقل — وزنها **زي الـ Class بالظبط**. Pseudo-element وزنها **زي الـ Element بالظبط**.

```css
.btn:hover { }        /* Specificity: 0,0,2,0 (كلاس + pseudo-class) */
button::before { }    /* Specificity: 0,0,0,2 (element + pseudo-element) */
```

**🎤 مقابلة:** *"Pseudo-classes describe state (`:hover`) and carry class-level specificity; pseudo-elements target a sub-part (`::before`) and carry element-level specificity — they're not a separate specificity tier."*

---

## 3️⃣ Cascade & Specificity
📎 **الفصل الكامل على GitHub:** [chapter-3-cascade-specificity.md](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-3-cascade-specificity.md)

**الترتيب الهرمي (كل مرحلة بتتفعّل بس لو اللي قبلها متعادلة):**

```
1. Origin & Importance   →  User Agent < User < Author < Author!important < User!important
2. Specificity           →  Inline > ID > Class/Attr/Pseudo-class > Element/Pseudo-element
3. Source Order          →  الأخير في الكود بيكسب
```

**⚠️ فخ !important:** مش بس "بتتخطى" الترتيب — بتعكسه. لو Author وUser الاتنين حطوا `!important`، **User !important بتغلب Author !important**.

```css
p { color: black; }              /* (0,0,0,1) */
p.description { color: blue; }    /* (0,0,1,1) */
#main-text { color: green; }      /* (0,1,0,0) — الفائز دايمًا */
```

**Inheritance:**
```css
inherit   /* تجبر الوراثة حتى لو الخاصية مش بتورث أصلًا */
initial   /* القيمة الافتراضية في CSS spec */
unset     /* inherit لو بتورث طبيعي، initial لو لأ */
revert    /* ترجع لستايل المتصفح الافتراضي (User Agent) */
```

**🪤 فخ المقابلة الكلاسيكي:** 100 كلاس `.c1.c2...c100` ضد `#myId` واحد → **الـ ID بيفوز دايمًا**. الخانات مستقلة، والعدد مش بيفيض بين الخانات.

**🎤 مقابلة:** *"The Cascade resolves conflicts through three sequential layers — origin/importance, specificity, then source order — each activating only if the previous one ties."*

---

## 4️⃣ Box Model
📎 **الفصل الكامل على GitHub:** [chapter-4-box-model.md](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-4-box-model.md)

```
Content → Padding → Border → Margin (من جوه لبره)
```

```css
.box {
  box-sizing: content-box;  /* Default: width = content فقط */
  box-sizing: border-box;   /* width = content+padding+border (المعيار الصناعي) */
}

/* Reset شائع */
*, *::before, *::after { box-sizing: border-box; }
```

**حساب العرض:**
```
content-box: Total Width = width + padding + border
border-box:  Total Width = width (بيقلل الـ content تلقائي)
```

**Margin Collapsing (عمودي بس، مش أفقي أبدًا):**
```css
h2 { margin-bottom: 30px; }
p  { margin-top: 20px; }
/* المسافة الفعلية = 30px (الأكبر) مش 50px */
```

**⚠️ الحالة الأخطر:** Parent & First Child — لو مفيش padding/border فاصل، الـ margin-top بتاع الابن **بتنط برة الأب**.

**الحلول لمنع Collapsing:**
```css
.parent { display: flex; }        /* أو grid */
.parent { display: flow-root; }   /* الأنضف - BFC جديد */
.parent { overflow: hidden; }     /* أقدم */
```

**🎤 مقابلة:** *"Vertical margins between adjacent block elements collapse to the largest value — prevented via Flexbox, Grid, or `flow-root`."*

---

## 5️⃣ Display & Visibility
📎 **الفصل الكامل على GitHub:** [chapter-5-display-visibility.md](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-5-display-visibility.md)

| Display | سطر جديد | width/height | بجانب عناصر |
|---|---|---|---|
| `block` | ✅ | ✅ | ❌ |
| `inline` | ❌ | ❌ (بيتجاهلها) | ✅ |
| `inline-block` | ❌ | ✅ | ✅ |

**🪤 فخ inline-block الشهير:** زرارين `inline-block` بـ `width: 50%` كل واحد بيكسروا لسطر جديد رغم إن 50%+50%=100%. **السبب:** المسافة/الـ Enter بين الوسوم في الـ HTML بتتحسب كـ ~4px (white space character). **الحل:** الصقي الوسوم في بعض، أو `font-size:0` على الأب، أو الأفضل: استخدمي Flexbox بدل inline-block خالص.

```css
display: none        /* No box / no space / no interaction */
visibility: hidden    /* Box exists / space remains / no interaction */
opacity: 0             /* Box exists / space remains / ⚠️ interaction لسه شغالة! */
```

**⚠️ خطر `opacity: 0`:** العنصر بيفضل قابل للضغط/التركيز رغم إنه شفاف تمامًا — لازم `pointer-events: none` معاها لو محتاجة تعطيل حقيقي.

```css
overflow: visible   /* Default — المحتوى يظهر برة */
overflow: hidden     /* يقص أي زيادة */
overflow: scroll      /* Scrollbar دايمًا ظاهر */
overflow: auto         /* Scrollbar بس لو محتاج */
```

**🎤 مقابلة:** *"`display: none` removes the element from flow and triggers reflow; `visibility: hidden` preserves space and triggers repaint; I combine `opacity: 0` with `pointer-events: none` for smooth transitions without leaving the element interactive."*

---

## 6️⃣ Positioning
📎 **الفصل الكامل على GitHub:** [chapter-6-positioning.md](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-6-positioning.md)

```css
position: static     /* Default — Normal Flow، متجاوبش مع top/left */
position: relative     /* في Normal Flow، وبتبقى Containing Block لأبنائها الـ absolute */
position: absolute       /* برة Normal Flow، بالنسبة لأقرب Containing Block مؤهل */
position: fixed            /* برة Normal Flow، بالنسبة للـ Viewport (عادةً) */
position: sticky             /* Normal Flow لحد threshold، وبعدين تلتصق */
```

**⚠️ القاعدة الغلط الشائعة:** "absolute بتاخد مكانها من الأب المباشر دايمًا" — **غلط**. الصح: أقرب **أب مؤهل** (عنده `position` غير static).

**🆕 نقطة Senior:** `transform` / `filter` / `will-change: transform` على أي أب بتخليه **Containing Block** حتى لو مالوش `position` خالص — وده بيكسر سلوك `fixed` المتوقع (بيتصرف زي `absolute`).

**Stacking Context — إيه اللي بيعملها:**
```css
position: relative/absolute/fixed/sticky + z-index ≠ auto
opacity < 1
transform ≠ none
filter ≠ none
will-change: opacity/transform
isolation: isolate
```

**🪤 فخ:** `z-index: 9999` مش دايمًا بتكسب — لو العنصر محبوس جوه Stacking Context أقل من واحد تاني، الرقم مش بيعدّي. **الحل: افحصي الـ stacking contexts، متزوديش الرقم عشوائي.**

**🎤 مقابلة:** *"A high z-index doesn't guarantee top rendering — stacking contexts created by opacity, transform, or isolation can trap it below elements with lower z-index."*

---

## 7️⃣ Flexbox
📎 **الفصل الكامل على GitHub:** [chapter-7-flexbox.md](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-7-flexbox.md)

```css
.container {
  display: flex;
  flex-direction: row;          /* يحدد الـ Main Axis */
  justify-content: center;       /* توزيع على الـ Main Axis */
  align-items: center;            /* محاذاة على الـ Cross Axis */
  align-content: space-between;    /* توزيع الـ lines (محتاج flex-wrap) */
  flex-wrap: wrap;
  gap: 20px;
}
.item {
  flex-grow: 1;
  flex-shrink: 1;
  flex-basis: 200px;
  align-self: flex-end;    /* استثناء لعنصر واحد */
  order: 2;                 /* بصري بس، مش بيغيّر DOM order */
}
```

**⚠️ القاعدة الخاطئة الشائعة:** `justify = horizontal`, `align = vertical` — **غلط** لو `flex-direction: column`، الاتنين بيتبادلوا الأدوار.

**🆕 مشكلة Overflow الشهيرة:**
```css
.item {
  flex-shrink: 1;   /* موجودة، لكن العنصر لسه بيعمل overflow! */
  min-width: 0;      /* ✅ الحل — min-width الافتراضية = auto = min-content size */
}
```

**`flex` shorthand:**
| Shorthand | يعادل |
|---|---|
| `flex: initial` (default) | `0 1 auto` |
| `flex: auto` | `1 1 auto` |
| `flex: none` | `0 0 auto` |
| `flex: 1` | `1 1 0%` |

**🪤 فخ:** `align-items: center` مش شغالة؟ الأب عنده `height: auto` (من المحتوى بس) — مفيش مساحة زيادة للتسنتر فيها. لازم الأب يكون عنده height صريح.

**🎤 مقابلة:** *"A common real-world bug is a flex item refusing to shrink below its content size — `min-width` defaults to `auto`, resolving to min-content; `min-width: 0` fixes it."*

---

## 8️⃣ CSS Grid
📎 **الفصل الكامل على GitHub:** [chapter-8-css-grid.md](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-8-css-grid.md)

```css
.container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  grid-template-areas:
    "header header"
    "sidebar main"
    "footer footer";
  gap: 24px;
}
.item {
  grid-column: span 2;      /* الأشهر عمليًا */
  grid-area: header;
}
```

**محاذاة Grid (مستويات التحكم الثلاث):**
```css
justify-items / align-items      /* محاذاة المحتوى جوه كل خلية (كل العناصر) */
justify-self / align-self         /* استثناء لعنصر واحد */
justify-content / align-content    /* محاذاة الـ Grid كله جوه الـ container */
```

**`auto-fit` vs `auto-fill`:**
```
auto-fit  → الفراغات تتطوي، العناصر تتمدد لتملأ المساحة
auto-fill → الفراغات تفضل موجودة كـ tracks فاضية
```

**Explicit vs Implicit:** Explicit = عرّفتيه انتِ صراحة. Implicit = المتصفح ضافه تلقائي لو العناصر زادت عن الـ tracks المحددة (`grid-auto-rows`/`grid-auto-columns` بتتحكم في حجمهم).

**🎤 مقابلة:** *"Grid's own alignment layer — `justify-items` for content within cells, `justify-self` for a single override, `justify-content` for the whole track grid within its container."*

---

## 9️⃣ Responsive Design
📎 **الفصل الكامل على GitHub:** [chapter-9-responsive-design.md](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-9-responsive-design.md)

**⚠️ الشرط الأول قبل أي حاجة تانية:**
```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```
من غيره، الموبايل بيزوّم أوت والـ Media Queries عمليًا مش بتتفعّل.

```css
/* Mobile First — الأساس للموبايل، تحسين تدريجي للأكبر */
.card { width: 100%; }
@media (min-width: 768px) { .card { width: 50%; } }
@media (min-width: 1024px) { .card { width: 33.33%; } }
```

**Breakpoints:** 768px/1024px مجرد convention (من Bootstrap) مش قانون CSS. القاعدة الصح: **content-driven** — البريك بوينت لما التصميم نفسه يتكسر بصريًا، مش رقم ثابت.

```css
/* Container Queries — تجاوب حسب حجم الأب، مش الشاشة */
.sidebar { container-type: inline-size; container-name: card; }
@container card (min-width: 400px) { .card { display: flex; } }
```

**🆕 Dynamic Viewport Units:**
```css
.hero {
  height: 100vh;   /* fallback */
  height: 100dvh;  /* بيتحدث مع ظهور/اختفاء شريط عنوان الموبايل */
}
```

**🎤 مقابلة:** *"Responsive design starts with the viewport meta tag. I treat breakpoints as content-driven, use `clamp()` for fluid typography, and container queries for component-level responsiveness."*

---

## 🔟 Units & Values
📎 **الفصل الكامل على GitHub:** [chapter-10-css-units-values.md](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-10-css-units-values.md)

| Unit | نسبي لـ | استخدام مثالي |
|---|---|---|
| `px` | ثابتة | border, أيقونات |
| `%` | الأب المباشر | عروض متجاوبة |
| `em` | سياق العنصر/أبوه | مكونات مرتبطة بحجم خطها |
| `rem` | الـ `html` (root) | Typography, spacing موحد |
| `vw`/`vh` | الـ viewport | أبعاد مرتبطة بالشاشة |
| `vmin`/`vmax` | أصغر/أكبر بُعد | عناصر متناسبة مع أي orientation |
| `ch` | عرض حرف الصفر | عرض نص مقروء (`max-width: 65ch`) |
| `fr` | مساحة الـ Grid | توزيع أعمدة/صفوف Grid |

**⚠️ فخ `line-height` مع `em` (Compounding):**
```css
.parent { font-size: 16px; line-height: 1.5em; }  /* بتتحسب فورًا لـ 24px الثابتة */
.child { font-size: 24px; }  /* هيورث 24px الثابتة، مش نسبة 1.5 الجديدة! */

/* ✅ الحل: قيمة بدون وحدة */
.parent { line-height: 1.5; }  /* الرقم نفسه بيتوارث، بيتحسب لكل عنصر لوحده */
```

```css
calc(100% - 40px)       /* ⚠️ لازم مسافة حوالين +/- وإلا بتتجاهل بصمت */
min(90%, 1200px)         /* أصغر قيمة — سقف أقصى */
max(20px, 5vw)             /* أكبر قيمة — حد أدنى */
clamp(2rem, 5vw, 4rem)       /* min + preferred + max */
```

**🎤 مقابلة:** *"A classic pitfall is using `em` for `line-height`, which bakes in a computed pixel value that children inherit rigidly — a unitless value avoids that. I also always include spaces around `+`/`-` inside `calc()`, since omitting them silently invalidates the whole declaration."*

---

## 1️⃣1️⃣ Colors & Backgrounds
📎 **الفصل الكامل على GitHub:** [chapter-11-colors-backgrounds.md](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-11-colors-backgrounds.md)

```css
background-size: cover;    /* يملأ، ممكن يقص */
background-size: contain;   /* كامل، ممكن فراغ */
object-fit: cover;           /* نفس منطق cover لكن لـ <img> حقيقية */
```

**⚠️ الفرق الأهم في الفصل: `opacity` vs Alpha Color**
```css
.card { opacity: 0.5; }              /* ❌ بيأثر على العنصر وكل محتوياته (النص كمان) */
.card { background: rgb(0 0 0 / 0.5); }  /* ✅ الشفافية للخلفية بس، النص فاضل واضح */
```

```css
color: currentColor;   /* بتاخد نفس قيمة color الحالية — مفيدة مع border/SVG fill */
background: conic-gradient(from 0deg, red, yellow, blue);  /* النوع التالت للتدرجات */
```

**WCAG Contrast:** نص عادي 4.5:1 (AA)، نص كبير 3:1. القاعدة: **Color + Text/Icon**، مش لون لوحده لتوصيل معنى.

**🎤 مقابلة:** *"Opacity fades the entire element tree including text, while an alpha channel on the background keeps text fully legible — that's the key distinction I check for overlay designs."*

---

## 1️⃣2️⃣ Typography
📎 **الفصل الكامل على GitHub:** [chapter-12-typography.md](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-12-typography.md)

```css
body {
  font-family: "Inter", Arial, sans-serif;  /* دايمًا fallback stack */
  line-height: 1.5;   /* unitless — موصى بيه */
  text-align: start;   /* بدل left — بيتكيف مع RTL/LTR */
}
```

**Ellipsis (لازم التلاتة مع بعض):**
```css
.title {
  white-space: nowrap;    /* منع النزول لسطر جديد */
  overflow: hidden;         /* إخفاء الزيادة */
  text-overflow: ellipsis;   /* شكل الإخفاء (...) */
}
```

**🆕 كلمات طويلة بتكسر الـ Layout (باج شائع مع محتوى المستخدم):**
```css
.comment-text { overflow-wrap: break-word; }  /* الحل القياسي */
.url-display { word-break: break-all; }        /* أشد صرامة */
```

```css
text-transform: uppercase;   /* بصري بس — الـ DOM/screen reader بيفضل زي ما هو */
text-wrap: balance;           /* توزيع متوازن لأسطر العناوين (خاصية حديثة) */
-webkit-line-clamp: 3;         /* قص متعدد الأسطر */
```

**🎤 مقابلة:** *"For overflow, I distinguish single-line ellipsis (needs `white-space`+`overflow`+`text-overflow` together) from long unbroken words breaking layout, which `overflow-wrap: break-word` handles separately."*

---

## 1️⃣3️⃣ CSS Functions (Math & Color)
📎 **الفصل الكامل على GitHub:** [chapter-13-css-functions-math-and-color.md](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-13-css-functions-math-and-color.md)

```css
calc(100% - 40px)              /* حسابات، تجمع وحدات مختلفة */
min(90%, 1200px, 50vw)          /* بتقبل أكتر من قيمتين */
max(20px, 5vw)
clamp(2rem, 5vw, 4rem)

rgb(42 75 141 / 0.5)             /* الصيغة الحديثة، بدون فواصل */
hsl(220 54% 36%)                  /* Hue/Saturation/Lightness */
color-mix(in srgb, var(--primary) 90%, black)   /* خلط لونين */
oklch(60% 0.15 250)                                /* متسقة بصريًا (perceptual) */
```

**⚠️ Browser Support — `oklch()`/`color-mix()` حديثتين نسبيًا:**
```css
.button {
  background: #2A4B8D;              /* Fallback أولًا */
  background: oklch(55% 0.15 250);   /* المتصفحات الحديثة بتاخد ده */
}
```

**🎤 مقابلة:** *"I use `color-mix()` to derive hover/active states from a base token, and I'm moving toward `oklch()` for perceptual consistency — always with a traditional color fallback declared first."*

---

## 1️⃣4️⃣ CSS Variables & Theming
📎 **الفصل الكامل على GitHub:** [chapter-14-css-variables-and-theming.md](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-14-css-variables-and-theming.md)

```css
:root {
  --blue-700: #2a4b8d;                 /* Primitive */
  --color-primary: var(--blue-700);      /* Semantic */
  --button-bg: var(--color-primary);      /* Component */
}
.button { background: var(--button-bg); }
```

```css
color: var(--text-color, #16213a);   /* fallback لو المتغيّر مش موجود/صالح */

[data-theme="dark"] { --bg-primary: #111827; }  /* App-level theme */
@media (prefers-color-scheme: dark) { :root { --bg-primary: #111827; } }  /* System preference */
```

**⚠️ محدوديتين مهمتين:**
```css
/* ❌ var() مش بتشتغل جوه شرط @media خالص */
@media (min-width: var(--breakpoint)) { }

/* ❌ مينفعش تلصقي وحدة على متغيّر مباشرة */
margin-top: var(--space)px;
/* ✅ الحل */
margin-top: calc(var(--space) * 1px);
```

```css
@property --angle {              /* تسجيل نوع عشان الـ animation يشتغل سلس */
  syntax: '<angle>';
  inherits: false;
  initial-value: 0deg;
}
```

**🎤 مقابلة:** *"Components consume tokens — theme controls tokens. Custom properties can't be referenced inside a media query condition; for animating them smoothly, I register them with `@property`."*

---

## 1️⃣5️⃣ Transitions & Animations
📎 **الفصل الكامل على GitHub:** [chapter-15-transitions-and-animations.md](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-15-transitions-and-animations.md)

```css
.button {
  transition: transform 200ms ease, opacity 200ms ease;  /* ✅ حددي الخصائص، متستخدميش all */
}
transform: translateX(20px) scale(1.05) rotate(45deg);
```

**⚠️ `transform` مش دايمًا GPU مضمون** — غالبًا compositor-friendly، لكن المتصفح هو اللي بيقرر.

```css
.card:hover { will-change: transform; }  /* تلميح للمتصفح — استخدام موضعي بس، مش عام */
```

**🆕 مشكلة `height: auto` (Accordion بيقفز بدل ما يتحرك ناعم):**
```css
/* ✅ الحل الحديث */
.accordion { display: grid; grid-template-rows: 0fr; transition: grid-template-rows 300ms; }
.accordion.open { grid-template-rows: 1fr; }
```

```css
@keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
.modal {
  animation: fadeIn 300ms ease-out forwards;  /* forwards = يحتفظ بحالة النهاية */
}
```

**Timing Functions:** `ease-out` → عناصر داخلة للشاشة (modal/toast). `linear` → حركة مستمرة (loader).

**Accessibility:**
```css
@media (prefers-reduced-motion: reduce) {
  .modal { animation: none; }   /* قللي/شيلي الحركة، مش الـ functionality */
}
```

**🎤 مقابلة:** *"For accordions, I avoid transitioning `height: auto` directly since the browser can't interpolate to an undefined endpoint — I use `grid-template-rows: 0fr to 1fr` instead."*

---

## 1️⃣6️⃣ Advanced CSS
📎 **الفصل الكامل على GitHub:** [chapter-16-advanced-css.md](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-16-advanced-css.md)

```css
/* Logical Properties — أساس RTL */
.card { padding-inline: 24px; margin-inline-start: 16px; }

/* CSS Nesting */
.button {
  &:hover { transform: translateY(-2px); }   /* ⚠️ لازم & وإلا descendant غلط! */
}
```

**⚠️ فخ Nesting خطير:**
```css
.button { &:hover {} }   /* ✅ = .button:hover */
.button { :hover {} }     /* ❌ = .button :hover (descendant!) مختلف تمامًا */
```

```css
@container (min-width: 500px) { .card { display: grid; } }  /* Component-level responsive */

@layer reset, base, components, utilities;   /* ترتيب الكتابة = ترتيب الأولوية */
```

**🆕 نقطة حرجة عن `@layer`:** أي CSS **من برة أي layer** بيكسب **دايمًا**، بغض النظر عن ترتيب الـ layers.

```css
:is(.a, .b) { }    /* بتاخد أعلى specificity من جواها */
:where(.a, .b) { }  /* specificity = صفر دايمًا — مثالية لـ base styles */
.card:has(.badge) { }  /* Parent selector! ⚠️ احذري الأداء لو استخدمتيها بشكل عام جدًا */
```

**🎤 مقابلة:** *"Omitting `&` before a pseudo-class inside nesting creates an unintended descendant selector. And unlayered CSS always wins over any layered rule regardless of layer order."*

---

## 1️⃣7️⃣ RTL & Internationalization
📎 **الفصل الكامل على GitHub:** [chapter-17-rtl-and-internationalization.md](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-17-rtl-and-internationalization.md)

```html
<html lang="ar" dir="rtl">
```

**القاعدة الذهبية:** متفكريش Left/Right، فكري Start/End.

```css
margin-inline-start: 24px;    /* بدل margin-left */
padding-inline-end: 16px;      /* بدل padding-right */
inset-inline-end: 0;             /* بدل right (حتى في positioning!) */
inline-size / block-size;         /* بدل width / height */
```

**⚠️ `row-reverse` مش "خاصية RTL":**
```css
flex-direction: row-reverse;  /* بتعكس الـ main axis — مفهوم مختلف تمامًا عن dir="rtl" */
/* غالبًا dir="rtl" + display:flex عادي كفاية، من غير row-reverse خالص */
```

**Icon Mirroring — قاعدة الحسم:**
| بتتقلب | مبتتقلبش |
|---|---|
| أسهم تنقل (Next/Back), Undo/Redo | Logo, Camera, Play/Pause, Search, Heart |

```css
[dir="rtl"] .icon-directional { transform: scaleX(-1); }
:dir(rtl) .icon { transform: scaleX(-1); }  /* 🆕 بيتبع الاتجاه المحسوب حتى لو موروث، مش بس [dir] الصريح */
```

**🆕 مشكلة الـ Scrollbar:** بيتقلب مكانه في RTL (بيبان شمال) — أي `position: fixed/absolute` بـ `right: 0` ممكن يتصادم معاه. الحل: `inset-inline-end` بدل `right`.

```css
.order-id { direction: ltr; unicode-bidi: isolate; }  /* لجزئيات محددة بس: order ID, email, URL */
:lang(ar) { line-height: 1.7; }  /* Typography مختلفة لكل لغة */
```

**🎤 مقابلة:** *"`:dir(rtl)` matches the computed direction even when inherited, while `[dir='rtl']` only matches an explicit attribute. I also watch for the native scrollbar flipping sides in RTL."*

---

## 1️⃣8️⃣ Accessibility (a11y)
📎 **الفصل الكامل على GitHub:** [chapter-18-accessibility-a11y-in-css.md](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-18-accessibility-a11y-in-css.md)

```css
button:focus-visible {   /* بس وقت الـ keyboard navigation، مش عند الضغط بالماوس */
  outline: 2px solid var(--color-primary);
  outline-offset: 3px;
}
/* ❌ خطر جدًا من غير بديل: button { outline: none; } */
```

```css
@media (prefers-color-scheme: dark) { }   /* تفضيل النظام (مختلف عن app-level data-theme) */
@media (prefers-contrast: more) { }        /* المستخدم طالب تباين أعلى (حر في الألوان) */
@media (forced-colors: active) {           /* 🆕 النظام فارض palette محدودة بالكامل (Windows HC) */
  .card { border: 1px solid CanvasText; }   /* لازم system color keywords */
}
```

```css
.sr-only {
  position: absolute; width: 1px; height: 1px; padding: 0; margin: -1px;
  overflow: hidden; clip-path: inset(50%); white-space: nowrap; border: 0;
  /* ⚠️ clip-path مش clip: rect() القديمة (deprecated) */
  /* ⚠️ ولا display:none — بيشيلها من accessibility tree كمان */
}
```

**Color Contrast (WCAG):** نص عادي 4.5:1 (AA)، نص كبير 3:1.
**🆕 Touch Target:** حد أدنى **44×44px** (WCAG 2.5.5) لأي عنصر تفاعلي على اللمس.

| | مساحة | Keyboard/Interaction | Screen Reader |
|---|---|---|---|
| `display:none` | ❌ | ❌ | ❌ |
| `visibility:hidden` | ✅ | ❌ | ❌ |
| `opacity:0` | ✅ | ⚠️ ممكن يفضل قابل للتفاعل! | ✅ |

**🎤 مقابلة:** *"I distinguish `prefers-contrast`, which respects user color choices at higher contrast, from `forced-colors`, which overrides colors entirely with system values."*

---

## 1️⃣9️⃣ CSS Architecture
📎 **الفصل الكامل على GitHub:** [chapter-19-css-architecture.md](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-19-css-architecture.md)

```css
/* BEM */
.card { }              /* Block */
.card__title { }        /* Element */
.card--featured { }      /* Modifier */
```

```css
/* CSS Modules (React) */
/* Button.module.css → import styles → className={styles.button} */
/* composes: مشاركة declarations بين classes من غير تكرار */
.primary { composes: button-base from "./base.module.css"; }
```

```html
<!-- Tailwind (Utility-First) -->
<button class="rounded-md bg-blue-600 px-4 py-2 hover:bg-blue-700">Save</button>
```

**CSS-in-JS — Runtime vs Zero-Runtime:**
```
Runtime (styled-components, Emotion) → بيولّد CSS وقت التشغيل، محتاج React Context
                                         → 🆕 بيجبر الـ component يبقى Client Component
                                         → بيتعارض مع React Server Components (RSC)
Zero-Runtime (Vanilla Extract, Panda) → CSS ثابت وقت الـ build، من غير تكلفة runtime
```

| Architecture | مناسب لـ |
|---|---|
| BEM | Traditional CSS، من غير build tools |
| CSS Modules | React/Next isolation |
| Tailwind | سرعة + اتساق، SaaS/React |
| CSS-in-JS | Dynamic styling (احذري RSC conflicts) |

**🎤 مقابلة:** *"Runtime CSS-in-JS solutions require a React Context, forcing components to be client-side — conflicting with React Server Components. Zero-runtime solutions resolve to static CSS at build time."*

---

## 2️⃣0️⃣ Browser Compatibility
📎 **الفصل الكامل على GitHub:** [chapter-20-browser-compatibility-and-progressive-enhancement.md](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-20-browser-compatibility-and-progressive-enhancement.md)

```css
.card { display: block; }              /* Baseline أولًا */
@supports (display: grid) {              /* Enhancement */
  .card { display: grid; }
}
@supports (display: grid) and (gap: 1rem) { }
@supports selector(:has(a)) {              /* 🆕 فحص دعم الـ selector نفسه، مش property/value */
  .card:has(.badge) { border-color: blue; }
}
```

**Feature Detection مش Browser Detection:**
```js
if ("IntersectionObserver" in window) { }   /* ✅ القدرة، مش اسم المتصفح */
```

| | Graceful Degradation | Progressive Enhancement |
|---|---|---|
| البداية | تجربة متقدمة كاملة | Baseline بسيط |
| الاتجاه | Top-down (fallback لو فشل) | Bottom-up (enhancement لو دعم) |

**⚠️ نقطة دقيقة:** `@supports` بترجع true لو المتصفح "فاهم الـ syntax" بس — مش ضمانة إن التنفيذ خالي من bugs معروفة. **95% browser support ≠ 95% مناسب لمشروعك** — يعتمد على مين الـ 5% الباقيين بالنسبة لجمهورك.

**🎤 مقابلة:** *"I follow Progressive Enhancement — solid baseline first, modern features via `@supports`. `@supports selector(:has(a))` lets me feature-detect selector support specifically."*

---

## 2️⃣1️⃣ CSS Performance
📎 **الفصل الكامل على GitHub:** [chapter-21-css-performance.md](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-21-css-performance.md)

```
DOM/CSS Change → Style → Layout (Reflow) → Paint → Composite
```

| المرحلة | بتتفعّل مع | مثال |
|---|---|---|
| Layout | width, height, margin, top, left | مكلفة (بتأثر على عناصر تانية) |
| Paint | background, color, box-shadow | متوسطة |
| Composite | **transform**, **opacity** | أرخص غالبًا (مش مضمون GPU دايمًا) |

```css
/* ✅ Animation-friendly */
.modal { transform: translateY(-20px); opacity: 0; }
.modal.open { transform: translateY(0); opacity: 1; }
```

```css
.widget { contain: layout paint; }   /* عزل الجزء ده عن باقي الصفحة */

.section {
  content-visibility: auto;             /* تأجيل rendering للمحتوى برة الشاشة */
  contain-intrinsic-size: auto 500px;    /* 🆕 حجم تقديري + تذكر آخر حجم حقيقي */
}
```

**⚠️ `content-visibility: auto` ≠ `display: none`** — العنصر لسه جزء من الصفحة، بس شغله بيتأجل. **متفترضيش نسبة تحسّن ثابتة (زي 70%/80%) — قيسي بنفسك بـ DevTools.**

```
Layout Thrashing = تناوب Write/Read متكرر (JS) → إعادة حساب layout متكررة
will-change = Hint له تكلفة ذاكرة، مش "زرار أسرع"
```

**🎤 مقابلة:** *"I prefer animating `transform`/`opacity` since they can often stay within compositing. For long pages, `content-visibility: auto` defers rendering for off-screen content — but I never assume a fixed performance percentage, I measure with DevTools first."*

---

## 2️⃣2️⃣ Testing & Debugging Tools
📎 **الفصل الكامل على GitHub:** [chapter-22-testing-and-debugging-tools.md](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-22-testing-and-debugging-tools.md)

```
UI Problem → Inspect → Identify source → Test hypothesis → Fix → Verify
```

| الأداة | الاستخدام |
|---|---|
| Grid Inspector | Tracks/Gaps/Placement بصريًا |
| Flexbox Inspector | توزيع المساحة على المحاور |
| Styles panel | مين القواعد المتنافسة (فيها crossed-out) |
| Computed panel | القيمة النهائية الفعلية |

**🆕 أدوات سريعة:**
```css
* { outline: 1px solid red; }   /* أسرع تشخيص بصري — مبيأثرش على layout زي border */
```
**Force pseudo-class state** جوه DevTools Elements panel (`:hov`) — لفحص `:hover`/`:focus`/`:active` بثبات من غير ما تفضلي ماسكة الماوس.

```
Visual Regression Testing: Baseline screenshot → New commit → Compare → Fail/Review
Percy = منصة عامة. Chromatic = مرتبطة بـ Storybook.
Stylelint = ESLint للـ CSS — syntax errors, duplicate declarations, naming.
```

**🎤 مقابلة:** *"My process: inspector for layout, Computed styles for the cascade result, forced pseudo-class states for hover/focus debugging, and the classic `outline: 1px solid red` for a fast first pass."*

---

## 2️⃣3️⃣ Senior Decision Map (خريطة القرار الشاملة)
📎 **الفصل الكامل على GitHub:** [chapter-23-senior-css-interview-questions.md](https://github.com/Hanan525-eng/frontend-interview-handbook/blob/main/docs/css/chapter-23-senior-css-interview-questions.md)

```
                 CSS Problem
                      │
          ┌───────────┴───────────┐
          ↓                       ↓
      Layout?                 Styling?
          │                       │
     ┌────┴────┐             Cascade؟
     ↓         ↓                  │
   Flex      Grid            Specificity؟
     │         │                  │
     └────┬────┘                Layer؟
          │                       │
          ↓                       ↓
   Positioning؟              Inheritance؟
          │                       │
Containing Block               Source Order
Stacking Context
          │
          ↓
    Responsive؟ → Viewport ولا Container؟
          │
          ↓
        RTL؟ → Logical Properties؟
          │
          ↓
   Accessibility؟
          │
          ↓
     Performance؟
          │
          ↓
   Measure → Fix Root Cause
```

### أهم 15 سؤال قبل أي مقابلة:

1. اشرحي الـ CSS Cascade (Origin → Specificity → Source Order)
2. إزاي بتشتغل الـ Specificity؟ (الخانات مستقلة عن بعض)
3. لو الـ specificity متساوية؟ (Source Order)
4. ليه نتجنب `!important`؟
5. Flexbox vs Grid — امتى تستخدمي كل واحدة؟
6. إزاي `position: absolute` بتحدد containing block بتاعها؟ (مش بس position، كمان transform/filter)
7. ليه `z-index` مش بتشتغل دايمًا؟ (Stacking Contexts)
8. إزاي بتختاري breakpoints؟ (Content-driven مش أرقام أجهزة)
9. Media Queries vs Container Queries؟
10. ليه Logical Properties مهمة للـ RTL؟
11. ليه منشيلش focus styles من غير بديل؟
12. اشرحي Layout, Paint, Composite
13. ليه transform/opacity شائعين للـ animations؟ (مش "GPU دايمًا")
14. إزاي تشخّصي مشكلة CSS performance؟ (Measure أولًا)
15. إزاي تنظّمي CSS لمشروع React/Next.js كبير؟

### الفرق بين إجابة Junior وSenior

| Junior | Senior |
|---|---|
| يحفظ properties | يفهم trade-offs |
| يستخدم `!important` | يفهم الـ Cascade |
| يزوّد `z-index` | يفهم stacking contexts |
| "Grid = 2D" وبس | يعرف امتى Grid فعلًا مناسب |
| "transform = GPU" | يعرف compositor behavior الحقيقي |
| يصلح الشكل الظاهري | يدوّر على root cause |
| يركّز على Desktop بس | يفكر responsive/RTL/a11y من البداية |

### القاعدة الذهبية النهائية

> **Senior CSS مش عن حفظ خصائص أكتر — هو فهم ليه المتصفح بيطلّع نتيجة معينة، اختيار الـ layout model الصح، التحكم في الـ Cascade، واتخاذ قرارات تفضل قابلة للصيانة، accessible، responsive، وperformant مع نمو التطبيق.**

---

## 🔁 Quick Copy-Paste Patterns (جاهزة لأي مشروع جديد)

```css
/* === Reset أساسي === */
*, *::before, *::after { box-sizing: border-box; }
body { margin: 0; line-height: 1.5; }

/* === Container متجاوب === */
.container { width: min(90%, 1200px); margin-inline: auto; }

/* === Grid Cards متجاوب من غير Media Queries === */
.cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1.5rem;
}

/* === Typography Fluid === */
h1 { font-size: clamp(2rem, 5vw, 4rem); }

/* === RTL-Ready Card === */
.card {
  padding-inline: 24px;
  margin-inline-start: 16px;
  border-inline-start: 4px solid var(--color-primary);
  text-align: start;
}

/* === Accessible Focus === */
button:focus-visible { outline: 2px solid var(--color-primary); outline-offset: 2px; }

/* === Screen Reader Only === */
.sr-only {
  position: absolute; width: 1px; height: 1px; padding: 0; margin: -1px;
  overflow: hidden; clip-path: inset(50%); white-space: nowrap; border: 0;
}

/* === Dark Mode جاهز === */
:root { --bg: #fff; --text: #16213a; }
[data-theme="dark"] { --bg: #111827; --text: #fff; }
@media (prefers-color-scheme: dark) { :root { --bg: #111827; --text: #fff; } }

/* === Ellipsis سطر واحد === */
.truncate { white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }

/* === منع كلمة طويلة من كسر الـ layout === */
.comment { overflow-wrap: break-word; }

/* === Reduced Motion === */
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after { animation-duration: 0.01ms !important; transition-duration: 0.01ms !important; }
}
```

---

*آخر تحديث: يغطي الفصول 1–23 كاملة من CSS Handbook — من Fundamentals لحد Senior Interview Questions.*   

