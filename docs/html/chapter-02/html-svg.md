# الفصل الثامن

# SVG (Scalable Vector Graphics)

# 8.1 SVG Basics

---

# السؤال الاول

# What is the `<svg>` element in HTML, and what are the `viewBox`, `width`, and `height` attributes?

---

## الإجابة

> The `<svg>` element is used to embed Scalable Vector Graphics (SVG) directly into an HTML document. SVG images are resolution-independent, meaning they remain sharp at any size. The `viewBox`, `width`, and `height` attributes define the drawing area and how the SVG is displayed.
> 

---

## لماذا تهتم الشركات بهذا السؤال؟

لأن SVG أصبح المعيار الأساسي لـ:

- Icons
- Logos
- Charts
- Illustrations
- Maps
- UI Graphics

وفهم `viewBox` من أكثر النقاط التي تميز مطور الـ Mid-Level عن الـ Junior.

---

# ما هو SVG؟

SVG اختصار لـ:

```
Scalable Vector Graphics
```

وهو تنسيق رسومي يعتمد على **الرياضيات (Vectors)** بدلاً من البكسلات (Pixels).

---

## لماذا نستخدم SVG؟

لأنه:

- لا يفقد الجودة عند التكبير.
- حجمه صغير في كثير من الحالات.
- يمكن تنسيقه باستخدام CSS.
- يمكن التحكم فيه باستخدام JavaScript.
- مناسب للشاشات عالية الدقة (Retina).

---

## مقارنة بين SVG والصور العادية

| Feature | SVG | PNG / JPEG |
| --- | --- | --- |
| يعتمد على Vectors | ✅ | ❌ |
| يفقد الجودة عند التكبير | ❌ | ✅ |
| يمكن تعديله بـ CSS | ✅ | ❌ |
| يمكن تحريكه بـ JavaScript | ✅ | ❌ |
| مناسب للأيقونات والشعارات | ✅ | ✅ |

---

# 1. `<svg>`

---

## الإجابة

> The `<svg>` element defines the SVG drawing canvas.
> 

---

## المثال الأساسي

```

```

[](data:image/svg+xml;utf8,%3Csvg%20width%3D%22200%22%20height%3D%22200%22%3E%0A%0A%3C%2Fsvg%3E)

---

## ماذا يحدث؟

ينشئ مساحة رسم (Drawing Canvas) بعرض:

```
200px
```

وارتفاع:

```
200px
```

---

## هل يعرض شيئًا؟

❌ لا.

لن يظهر شيء حتى تضيف عناصر رسم مثل:

- `<rect>`
- `<circle>`
- `<line>`
- `<path>`

---

# مثال

```

```

[](data:image/svg+xml;utf8,%3Csvg%20width%3D%22200%22%20height%3D%22200%22%3E%0A%0A%20%20%20%20%3Ccircle%20cx%3D%22100%22%20cy%3D%22100%22%20r%3D%2260%22%20fill%3D%22blue%22%3E%0A%0A%20%20%20%20%3C%2Fcircle%3E%0A%0A%3C%2Fsvg%3E)

---

## ماذا يحدث؟

يعرض دائرة زرقاء داخل مساحة الرسم.

---

# 2. `width`

---

## الإجابة

> The `width` attribute defines the displayed width of the SVG.
> 

---

## المثال

```

```

[](data:image/svg+xml;utf8,%3Csvg%20width%3D%22400%22%3E%3C%2Fsvg%3E)

---

يعرض الـ SVG بعرض:

```
400px
```

---

# 3. `height`

---

## الإجابة

> The `height` attribute defines the displayed height of the SVG.
> 

---

## المثال

```

```

[](data:image/svg+xml;utf8,%3Csvg%20width%3D%22400%22%20height%3D%22250%22%3E%3C%2Fsvg%3E)

---

يعرض الـ SVG بارتفاع:

```
250px
```

---

# 4. `viewBox`

---

## الإجابة

> The `viewBox` attribute defines the internal coordinate system of the SVG.
> 

---

## الصيغة

```
viewBox="min-x min-y width height"
```

---

## المثال

```

```

[](data:image/svg+xml;utf8,%3Csvg%20viewBox%3D%220%200%20100%20100%22%3E%3C%2Fsvg%3E)

---

## ماذا تعني القيم؟

```
0
```

بداية المحور X

```
0
```

بداية المحور Y

```
100
```

عرض مساحة الرسم الداخلية

```
100
```

ارتفاع مساحة الرسم الداخلية

---

## لماذا هو مهم؟

لأنه يجعل SVG:

- Responsive
- قابلًا للتكبير والتصغير
- يحافظ على نسب الأبعاد

---

# مثال عملي

```

```

[](data:image/svg+xml;utf8,%3Csvg%20width%3D%22300%22%20height%3D%22300%22%20viewBox%3D%220%200%20100%20100%22%3E%0A%0A%20%20%20%20%3Ccircle%20cx%3D%2250%22%20cy%3D%2250%22%20r%3D%2240%22%20fill%3D%22red%22%3E%0A%0A%20%20%20%20%3C%2Fcircle%3E%0A%0A%3C%2Fsvg%3E)

---

## ماذا يحدث؟

رغم أن:

```
width = 300
height = 300
```

إلا أن جميع عناصر الرسم تعتمد على نظام إحداثيات داخلي حجمه:

```
100 × 100
```

ثم يقوم المتصفح بتكبيره ليملأ المساحة المعروضة.

---

# الفرق بين `width` و`height` و`viewBox`

| Attribute | Purpose |
| --- | --- |
| `width` | يحدد العرض الظاهر للـ SVG |
| `height` | يحدد الارتفاع الظاهر للـ SVG |
| `viewBox` | يحدد نظام الإحداثيات الداخلي الذي تُرسم عليه العناصر |

---

# أشهر أسئلة المقابلات

### What is SVG?

> SVG is a vector-based image format used to create scalable graphics in web pages.
> 

---

### What does the svg element do?

> It defines the SVG drawing area.
> 

---

### Does SVG lose quality when resized?

❌ لا.

لأنه يعتمد على الرسومات المتجهية (Vectors).

---

### What is the purpose of viewBox?

> It defines the internal coordinate system and enables responsive scaling.
> 

---

### Can an SVG exist without width and height?

✅ نعم.

يمكن الاعتماد على `viewBox` مع CSS لتحديد الحجم، لكن إذا لم تحدد أبعادًا أو أنماطًا مناسبة فقد لا يظهر بالحجم المتوقع.

---

### What is the difference between width and viewBox?

`width` و`height` يحددان **الحجم الظاهر**، بينما `viewBox` يحدد **نظام الإحداثيات الداخلي** الذي تُرسم بداخله الأشكال.

---

# Best Practices

- استخدم `viewBox` في جميع ملفات SVG تقريبًا.
- اجعل `width` و`height` قابلين للتحكم عبر CSS عند الحاجة إلى تصميم متجاوب.
- استخدم SVG للأيقونات والشعارات والرسومات البسيطة.
- لا تستخدم SVG للصور الفوتوغرافية؛ استخدم JPEG أو WebP أو AVIF لذلك.

---

# Senior Notes

هناك عدة نقاط يقع فيها كثير من المطورين:

### 1. `viewBox` أهم من `width` و`height`

كثير من المبتدئين يعتقدون أن تغيير `width` أو `height` يكفي لجعل SVG متجاوبًا.

في الواقع، وجود `viewBox` هو الذي يسمح للمتصفح بتكبير أو تصغير الرسم مع الحفاظ على النسب الصحيحة.

---

### 2. `width` و`height` لا يغيران الرسم الداخلي

إذا غيرت:

```
width="500"
```

فلن تتغير إحداثيات الأشكال.

الذي يتغير هو **حجم العرض فقط**.

---

### 3. SVG جزء من DOM

على عكس الصور العادية (`<img>`)، يمكن استهداف عناصر SVG مباشرة باستخدام:

- CSS
- JavaScript

وهذا يسمح بتغيير الألوان، وإضافة التفاعلات، وإنشاء الرسوم المتحركة دون الحاجة إلى استبدال الصورة.

## أساسيات الـ SVG (`<svg>`, `viewBox`, `width`, `height`)

### مثال الكود:

HTML

```
<!-- رسم دائرة داخل حاوية SVG متجانسة ومتجاوبة -->
<svg
  width="200"
  height="200"
  viewBox="0 0 100 100"
  xmlns="http://www.w3.org/2000/svg"
  aria-label="أيقونة دائرة خضراء"
  role="img"
>
  <!-- رسم دائرة في مركز النظام الإحداثي الداخلي (50, 50) بنصف قطر 40 -->
  <circle cx="50" cy="50" r="40" fill="#10b981" stroke="#047857" stroke-width="4" />
</svg>
```

### السؤال:

**ما هو عنصر `<svg>` في HTML، وما الفرق بين خصائص الأبعاد (`width` / `height`) وخاصية `viewBox`؟**

*(بالإنجليزي: What is the `<svg>` element in HTML, and what is the difference between physical dimensions (`width`/`height`) and the `viewBox` attribute?)*

### الإجابة النموذجية للمقابلة (Interview Answer):

> **عنصر `<svg>` يُستخدم لتضمين رسومات متجهة (Vector Graphics) قابلة للتكبير والتصغير دون أن تفقد جودتها (Pixelation). الفرق الجوهري بين الأبعاد وخاصية الـ `viewBox` هو أن `width` و `height` يحددان الإطار الفعلي والحجم الذي تشغله الرسمة على الشاشة بالبكسل، بينما تُحدد خاصية `viewBox` نظام الإحداثيات الداخلي (Internal coordinate system) ونسبة العرض إلى الارتفاع (Aspect Ratio) لتقسيم المساحة وتكبير/تصغير الأشكال الداخلية بالنسبة لهذا الإطار.**
> 

### الشرح بالتفصيل:

تعتبر رسومات الـ SVG جزءاً لا يستغنى عنه لأي مهندس واجهات (UI Engineer) حديث؛ فهي تُستخدم لبناء الأيقونات، الشعارات (Logos)، والرسوم التوضيحية التفاعلية. السر الحقيقي في قوة الـ SVG وررعتها في التجاوب (Responsiveness) يكمن في فهم المعادلة بين إطار العرض والأبعاد الداخلية.

تعال نفصص الخصائص الأربعة الأساسية بأسهل طريقة ممكنة:

#### 1. تفكيك الخصائص وتوضيح الفرق

#### أولاً: عنصر `<svg>`

- **الوظيفة:** الحاوية الرئيسية (Canvas Wrapper) التي تعرّف مساحة الرسم المتجه داخل كود HTML.

#### ثانياً: الأبعاد الخارجية (`width` و `height`)

- **الوظيفة:** تُحدد **المساحة الفيزيائية (Viewport)** التي سيحتلها عنصر الـ SVG داخل الصفحة (غالباً بالبكسل أو النسبة المئوية `%`).
- **التشبيه:** تشبه "إطار الصورة الخشبي" المعلق على الحائط؛ تحديد حجم الإطار الخارجي فقط.

#### ثالثاً: خاصية الإحداثيات الداخلية (`viewBox`)

- **الوظيفة:** تُعرف نافذة الرؤية الداخلية ونظام الشبكة الإحداثية (Coordinate System).
- **التصميم والتكوين:** تأخذ دائماً **4 أرقام تفصل بينها مسافات**:Plaintext
    
    ```
    viewBox="min-x min-y width height"
    ```
    
    - `min-x` و `min-y`: نقطة بداية الإحداثيات من الزاوية العلوية اليسرى (عادة تكون `0 0`).
    - `width` و `height`: العرض والارتفاع المفهومان **داخلياً** داخل الرسمة.
- **التشبيه:** تشبه "عدسة التكبير والتصغير (Zoom)" التي تحدد ما تراه داخل الإطار الخشبي وكيفية تمدده.

#### 2. كيف تتفاعل الخصائص معاً للتجاوب (Responsive SVG)؟

إذا أردت جعل أيقونة أو رسمة SVG متجاوبة 100% مع حجم الشاشة دون أن تتشوه:

HTML

```
<!-- SVG متجاوب تماماً يملأ الحاوية الأبوية مع الحفاظ على أبعاده الداخلية -->
<svg viewBox="0 0 100 100" style="width: 100%; height: auto;">
  <rect width="100" height="100" fill="#3b82f6" />
</svg>
```

- **ما يحدث هنا:** حذف خاصيتي `width` و `height` المباشرتين (أو ضبطهما بـ CSS)، واكتفينا بـ `viewBox="0 0 100 100"`.
- **النتيجة:** ستقوم الرسمة بتكبير وتصغير نفسها تلقائياً بحسب مساحة العنصر الأب، مع الحفاظ الدقيق على نسبة العرض للارتفاع 1:1.

#### 3. لمحة ذكاء للـ UI Engineer (سؤال الفخ للمقابلة)

الـ Interviewer ممكن يسألك: **"ماذا يحدث إذا كانت نسبة أبعاد `width/height` الخارجية تفصل عن نسبة أبعاد `viewBox` الداخلية (مثل width=400 height=200 مع viewBox 0 0 100 100)؟"**

**الإجابة الذكية:**

- بشكل افتراضي، يقوم المتصفح بتطبيق خاصية تُسمى **`preserveAspectRatio`**.
- يقوم المتصفح بتوسيط العناصر داخل المساحة الإضافية (Centering) وحماية الأشكال من التمدد أو التشوّه (Distortion)، عن طريق التكبير المتناسب حتى يملأ الأصغر حافة.
- إذا أردت إجبار الـ SVG على التمدد والتمطط لملء الأبعاد الخارجية بغض النظر عن النسبة الداخلية، نكتب: `preserveAspectRatio="none"`.

#### الكلمات المفتاحية للحفظ (Keywords):

- **Vector vs Raster:** الرسم المتجه القابل للتكبير بدون فقدان جودة مقترناً بالـ SVG.
- **Viewport (`width`/`height`):** الأبعاد الفيزيائية الخارجية للعنصر في الصفحة.
- **Coordinate System (`viewBox`):** نظام الإحداثيات الداخلي المكون من 4 قيم (`min-x min-y width height`).
- **`preserveAspectRatio`:** الخاصية المسؤولة عن كيفية مقياس الرسمة عند اختلاف النسبة المئوية للأبعاد.

#### جملتك النموذجية في المقابلة:

> **"The `<svg>` element embeds scalable vector graphics using a dual-dimension system. `width` and `height` establish the physical viewport size in the CSS layout, whereas the `viewBox` attribute (`min-x min-y width height`) defines the internal coordinate system and aspect ratio. Mastering `viewBox` is key to responsive SVG design because it controls how internal shapes scale to fill their outer container without distortion."**
> 

جاهزون لمتابعة باقي دروس الـ SVG في الفصل الثامن؟

الذهاب إلى 8.2 الأشكال الأساسية في SVG (rect, circle, path...)

# )

# 8.2 SVG Shapes

# 8.2.1 Basic Shapes

---

# السؤال الثاني

# What are the basic SVG shape elements, and when should you use them?

## الإجابة

> SVG provides several basic shape elements for drawing simple geometric graphics. The most commonly used are `<rect>`, `<circle>`, `<ellipse>`, and `<line>`.
> 

---

## لماذا تهتم الشركات بهذا السؤال؟

لأن هذه العناصر هي اللبنات الأساسية لأي رسم داخل SVG، وتستخدم في:

- Icons
- Charts
- Diagrams
- Dashboards
- UI Components
- Illustrations

وفهمها ضروري قبل الانتقال إلى العنصر الأكثر تقدمًا وهو `<path>`.

---

# 1. `<rect>`

---

## الإجابة

> The `<rect>` element draws a rectangle.
> 

---

## أشهر الخصائص

- `x`
- `y`
- `width`
- `height`
- `rx`
- `ry`

---

## ماذا تعني؟

| Attribute | Description |
| --- | --- |
| `x` | موضع البداية على المحور الأفقي |
| `y` | موضع البداية على المحور الرأسي |
| `width` | عرض المستطيل |
| `height` | ارتفاع المستطيل |
| `rx` | نصف قطر الزوايا الأفقية |
| `ry` | نصف قطر الزوايا الرأسية |

---

## المثال

```

```

[](data:image/svg+xml;utf8,%3Csvg%20width%3D%22200%22%20height%3D%22120%22%3E%0A%0A%20%20%20%20%3Crect%20x%3D%2220%22%20y%3D%2220%22%20width%3D%22120%22%20height%3D%2260%22%20fill%3D%22royalblue%22%3E%3C%2Frect%3E%0A%0A%3C%2Fsvg%3E)

---

## مستطيل بزوايا دائرية

```
<rectx="20"y="20"width="120"height="60"rx="12"ry="12"fill="tomato"/>
```

---

# 2. `<circle>`

---

## الإجابة

> The `<circle>` element draws a circle.
> 

---

## أشهر الخصائص

- `cx`
- `cy`
- `r`

---

| Attribute | Description |
| --- | --- |
| `cx` | مركز الدائرة أفقيًا |
| `cy` | مركز الدائرة رأسيًا |
| `r` | نصف القطر |

---

## المثال

```

```

[](data:image/svg+xml;utf8,%3Csvg%20width%3D%22200%22%20height%3D%22200%22%3E%0A%0A%20%20%20%20%3Ccircle%20cx%3D%22100%22%20cy%3D%22100%22%20r%3D%2260%22%20fill%3D%22seagreen%22%3E%3C%2Fcircle%3E%0A%0A%3C%2Fsvg%3E)

---

# 3. `<ellipse>`

---

## الإجابة

> The `<ellipse>` element draws an ellipse.
> 

---

## أشهر الخصائص

- `cx`
- `cy`
- `rx`
- `ry`

---

| Attribute | Description |
| --- | --- |
| `cx` | مركز الشكل أفقيًا |
| `cy` | مركز الشكل رأسيًا |
| `rx` | نصف القطر الأفقي |
| `ry` | نصف القطر الرأسي |

---

## المثال

```

```

[](data:image/svg+xml;utf8,%3Csvg%20width%3D%22220%22%20height%3D%22180%22%3E%0A%0A%20%20%20%20%3Cellipse%20cx%3D%22110%22%20cy%3D%2290%22%20rx%3D%2280%22%20ry%3D%2245%22%20fill%3D%22gold%22%3E%3C%2Fellipse%3E%0A%0A%3C%2Fsvg%3E)

---

## الفرق بين Circle وEllipse

الدائرة لها نصف قطر واحد:

```
r
```

أما الشكل البيضاوي فيستخدم نصفي قطر:

```
rx
ry
```

---

# 4. `<line>`

---

## الإجابة

> The `<line>` element draws a straight line between two points.
> 

---

## أشهر الخصائص

- `x1`
- `y1`
- `x2`
- `y2`

---

| Attribute | Description |
| --- | --- |
| `x1` | نقطة البداية أفقيًا |
| `y1` | نقطة البداية رأسيًا |
| `x2` | نقطة النهاية أفقيًا |
| `y2` | نقطة النهاية رأسيًا |

---

## المثال

```

```

[](data:image/svg+xml;utf8,%3Csvg%20width%3D%22220%22%20height%3D%22120%22%3E%0A%0A%20%20%20%20%3Cline%20x1%3D%2220%22%20y1%3D%2260%22%20x2%3D%22200%22%20y2%3D%2260%22%20stroke%3D%22black%22%20stroke-width%3D%224%22%3E%3C%2Fline%3E%0A%0A%3C%2Fsvg%3E)

---

## ماذا يحدث؟

يرسم خطًا مستقيمًا بين نقطتين.

---

# مقارنة بين العناصر

| Element | Purpose |
| --- | --- |
| `<rect>` | رسم مستطيل |
| `<circle>` | رسم دائرة |
| `<ellipse>` | رسم شكل بيضاوي |
| `<line>` | رسم خط مستقيم |

---

# أشهر أسئلة المقابلات

### Which SVG element draws a rectangle?

```
<rect>
```

---

### Which SVG element draws a circle?

```
<circle>
```

---

### What is the difference between circle and ellipse?

> A circle uses one radius (`r`), while an ellipse uses two radii (`rx` and `ry`).
> 

---

### Which SVG element draws a straight line?

```
<line>
```

---

### Which attribute rounds the corners of a rectangle?

```
rx
```

ويمكن أيضًا استخدام:

```
ry
```

---

# Best Practices

- استخدم `<rect>` للأزرار والبطاقات والأشكال المستطيلة.
- استخدم `<circle>` للأيقونات والمؤشرات والعناصر الدائرية.
- استخدم `<ellipse>` عندما تحتاج إلى شكل بيضاوي حقيقي، وليس دائرة ممدودة.
- استخدم `<line>` لتمثيل العلاقات أو المحاور في الرسوم البيانية.
- استخدم `stroke` و`stroke-width` عند رسم الخطوط، لأن `fill` لا يؤثر على `<line>`.

---

# Senior Notes

هناك عدة نقاط يقع فيها كثير من المطورين:

### 1. جميع الإحداثيات تعتمد على `viewBox`

القيم مثل:

```
x
y
cx
cy
```

ليست مرتبطة بحجم العنصر الظاهر (`width` و`height`) مباشرة، بل بنظام الإحداثيات الذي يحدده `viewBox`.

---

### 2. `<line>` لا يستخدم `fill`

العنصر:

```
<line>
```

ليس له مساحة داخلية، لذلك لا يظهر أي تأثير لخاصية:

```
fill
```

ويجب استخدام:

```
stroke
stroke-width
```

---

### 3. يمكن تنسيق جميع الأشكال باستخدام CSS

يمكن تطبيق خصائص مثل:

- `fill`
- `stroke`
- `stroke-width`
- `opacity`

إما مباشرة كخصائص SVG أو عبر ملفات CSS، مما يسهل إعادة استخدام الأشكال وتغيير مظهرها.

---

# 8.2 أشكال الـ SVG الأساسية (`<rect>`, `<circle>`, `<ellipse>`, `<line>`, `<polyline>`, `<polygon>`)

### مثال الكود:

HTML

```
<!-- تجميع الأشكال الأساسية داخل لوحة SVG واحدة -->
<svg viewBox="0 0 400 200" width="100%" height="auto" xmlns="http://www.w3.org/2000/svg">
  <!-- 1. مستطيل بحواف دائرية -->
  <rect x="10" y="10" width="100" height="60" rx="10" ry="10" fill="#3b82f6" />

  <!-- 2. دائرة -->
  <circle cx="180" cy="40" r="30" fill="#10b981" />

  <!-- 3. شكل بيضاوي -->
  <ellipse cx="280" cy="40" rx="40" ry="20" fill="#f59e0b" />

  <!-- 4. خط مستقيم -->
  <line x1="10" y1="120" x2="110" y2="180" stroke="#ef4444" stroke-width="4" />

  <!-- 5. خط متعدد النقاط (مفتوح) -->
  <polyline points="140,180 160,130 180,160 200,120" fill="none" stroke="#8b5cf6" stroke-width="3" />

  <!-- 6. مضلع مغلق (مثلث) -->
  <polygon points="280,120 240,180 320,180" fill="#ec4899" />
</svg>
```

### السؤال:

**ما هي أشكال الـ SVG الأساسية (Basic Shape Elements)، ومتى يجب عليك استخدام كل منها؟**

*(بالإنجليزي: What are the basic SVG shape elements, and when should you use them?)*

### الإجابة النموذجية للمقابلة (Interview Answer):

> **أشكال الـ SVG الأساسية هي أوسمة مدمجة تُستخدم لبناء الرسومات الهندسية البسيطة دون الحاجة لكتابة مسارات معقدة (Complex Paths). تشمل هذه الأشكال: `<rect>` للمستطيلات والمربعات، `<circle>` للدقائق والدواءر، `<ellipse>` للأشكال البيضاوية، `<line>` للخطوط المستقيمة المنفردة، `<polyline>` للخطوط المتصلة المفتوحة، و `<polygon>` للمضلعات المغلقة ذات الأضلاع المستقيمة. نستخدمها لأنها أسهل في القراءة، وأسرع في الأداء، وأسهل بكثير في التحريك والتحكم عبر CSS والجافاسكريبت.**
> 

### الشرح بالتفصيل:

عند بناء الأيقونات أو الرسوم التوضيحية داخل الـ SVG، يفضل دائماً استخدام الأشكال الهندسية المباشرة (Basic Shapes) بدلاً من استخدام وسم المسارات العام `<path>` طالما كان الشكل هندسياً منتظماً. هذا يجعل كود الـ HTML أسهل في الصيانة وتعديل الخصائص برمجياً.

تعال نفصص الأشكال الستة الأساسية وخصائصها:

#### 1. تفكيك الأشكال الستة وخصائصها الجوهرية

#### أولاً: `<rect>` (المستطيلات والمربعات)

- **الاستخدام:** رسم الكروت، الأزرار، الإطارات، والشاشات.
- **أهم الخصائص:**
    - `x`, `y`: نقطة بداية الزاوية العلوية اليسرى.
    - `width`, `height`: العرض والارتفاع.
    - `rx`, `ry`: نصف قطر انحناء الزوايا (لعمل Rounded Corners).

#### ثانياً: `<circle>` (الدقائق والدائريات)

- **الاستخدام:** الأيقونات الدائرية، مؤشرات الحالة (Status Indicators)، ونقاط البيانات في الرسوم البيانية.
- **أهم الخصائص:**
    - `cx`, `cy`: إحداثيات مركز الدائرة (Center X / Center Y).
    - `r`: نصف قطر الدائرة (Radius).

#### ثالثاً: `<ellipse>` (الأشكال البيضاوية)

- **الاستخدام:** الظلال تحت العناصر، الأشكال البيضاوية، والعيون في الرسومات التوضيحية.
- **أهم الخصائص:**
    - `cx`, `cy`: مركز الشكل البيضاوي.
    - `rx`: نصف القطر الأفقي (Horizontal Radius).
    - `ry`: نصف القطر الراسي (Vertical Radius).

#### رابعاً: `<line>` (الخط المستقيم المنفرد)

- **الاستخدام:** الفواصل (Dividers)، الأسهم، وتسطير النصوص.
- **أهم الخصائص:**
    - `x1`, `y1`: نقطة بداية الخط.
    - `x2`, `y2`: نقطة نهاية الخط.
    - *(ملاحظة: يجب إضافة `stroke` و `stroke-width` ليظهر الخط).*

#### خامساً: `<polyline>` (سلسلة خطوط متصلة مفتوحة)

- **الاستخدام:** رسم المخططات البيانية الخطية (Line Charts)، أو المسارات المكسورة غير المغلقة.
- **أهم الخصائص:**
    - `points`: سلسلة من أزواج الإحداثيات (`x,y`) تفصل بينها مسافات أو فواصل.
    - *(ملاحظة: لضمان عدم تعبئة الشكل الداخلي نضع `fill="none"`).*

#### سادساً: `<polygon>` (المضلعات المغلقة)

- **الاستخدام:** المثلثات، النجوم، الأشكال السداسية، وأيقونات التنبيه.
- **أهم الخصائص:**
    - `points`: أزواج الإحداثيات.
    - **الفرق عن polyline:** يربط المتصفح تلقائياً آخر نقطة بأول نقطة ليغلق الشكل بالكامل.

#### 2. جدول الملخص المباشر 🔍

| العنصر | الوظيفة | الخصائص المفتاحية | أفضل حالة استخدام |
| --- | --- | --- | --- |
| **`<rect>`** | مستطيل / مربع | `x`, `y`, `width`, `height`, `rx`, `ry` | أزرار، كروت، إطارات |
| **`<circle>`** | دائرة منتظمة | `cx`, `cy`, `r` | أيقونات، نقاط الرسم البياني |
| **`<ellipse>`** | شكل بيضاوي | `cx`, `cy`, `rx`, `ry` | ظلال العناصر، أشكال دائرية مضغوطة |
| **`<line>`** | خط مستقيم | `x1`, `y1`, `x2`, `y2` | خطوط الفصل، الأسهم |
| **`<polyline>`** | خطوط متصلة مفتوحة | `points="x1,y1 x2,y2 ..."` | الرسوم البيانية المتعرجة |
| **`<polygon>`** | مضلع هندسي مغلق | `points="x1,y1 x2,y2 ..."` | المثلثات، النجوم، الأشكال المعقدة |

#### 3. لمحة ذكاء للـ UI Engineer (سؤال الفخ للمقابلة)

الـ Interviewer ممكن يسألك: **"ما الميزة الحقيقية لاستخدام `<circle>` أو `<rect>` بدلاً من رسمها بخصائص المسار العام `<path d="..." />`؟"**

**الإجابة الذكية:**

1. **سهولة التحريك والتعديل بـ CSS / JS (Animatable Properties):**
    - تحريك نصف قطر الدائرة `r` أو انحناء زوايا المستطيل `rx` في `<rect>` عبر CSS Transitions أو GSAP أسهل بكثير وأقل في حجم الكود مقارنة بتحريك إحداثيات المعقدة داخل سلسلة نصوص `path d="..."`.
2. مقروءية الكود (Code Readability):
    - كود الأشكال الأساسية واضح ومفهوم دلالياً لأي مطور يقرأ الصفحة، بينما الأرقام داخل `<path>` تحتاج لبرامج تصميم مثل Figma لفك تشفيرها.

#### الكلمات المفتاحية للحفظ (Keywords):

- **Declarative SVG Shapes:** الأشكال الهندسية الصريحة والمباشرة.
- **Center Coordinates (`cx`, `cy`):** إحداثيات مركز الدوائر والأشكال البيضاوية.
- **`polyline` vs `polygon`:** الفارق المتمثل في كتمان وإغلاق الشكل المضلع.
- **`rx` and `ry` for Corner Radius:** خاصية عمل حواف دائرية للمستطيلات.

#### جملتك النموذجية في المقابلة:

> **"SVG provides a set of declarative basic shape primitives: `<rect>`, `<circle>`, `<ellipse>`, `<line>`, `<polyline>`, and `<polygon>`. We use these elements instead of generic `<path>` commands when dealing with standard geometric forms. They make the SVG markup significantly cleaner, improve code readability, and allow for easier programmatic manipulation and CSS animation—such as transitioning a circle's radius (`r`) or a rectangle's corner radius (`rx`)."**
> 

# 2 Multi-Point Shapes

---

# السؤال الثالث

# What are the `<polyline>` and `<polygon>` elements in SVG, and what is the difference between them?

## لإجابة

> The `<polyline>` element draws a series of connected straight lines, while the `<polygon>` element draws a closed shape by automatically connecting the last point to the first point.
> 

---

## لماذا تهتم الشركات بهذا السؤال؟

لأن كلا العنصرين يعتمد على مجموعة من النقاط (Points)، لكن الفرق بينهما يؤثر على طريقة الرسم وإمكانية استخدام خصائص مثل `fill`.

---

# 1. `<polyline>`

---

## الإجابة

> The `<polyline>` element draws multiple connected straight lines without automatically closing the shape.
> 

---

## متى نستخدمه؟

- Line Charts
- Graphs
- Open Paths
- Timelines
- Technical Diagrams

---

## أشهر الخصائص

- `points`
- `stroke`
- `stroke-width`
- `fill`

---

## الخاصية `points`

تحدد جميع النقاط التي يمر بها الخط.

الصيغة:

```
points="x1,y1 x2,y2 x3,y3 ..."
```

---

## المثال

```

```

[](data:image/svg+xml;utf8,%3Csvg%20width%3D%22220%22%20height%3D%22120%22%3E%0A%0A%20%20%20%20%3Cpolyline%20points%3D%2220%2C90%2070%2C30%20120%2C70%20180%2C20%22%20fill%3D%22none%22%20stroke%3D%22royalblue%22%20stroke-width%3D%224%22%3E%3C%2Fpolyline%3E%0A%0A%3C%2Fsvg%3E)

---

## ماذا يحدث؟

يرسم خطوطًا مستقيمة متصلة بين جميع النقاط، لكنه **لا يصل آخر نقطة بأول نقطة**.

---

# 2. `<polygon>`

---

## الإجابة

> The `<polygon>` element draws a closed geometric shape by automatically connecting the last point to the first point.
> 

---

## متى نستخدمه؟

- Triangles
- Stars
- Hexagons
- Arrows
- Custom Shapes
- Icons

---

## أشهر الخصائص

- `points`
- `fill`
- `stroke`
- `stroke-width`

---

## المثال

```

```

[](data:image/svg+xml;utf8,%3Csvg%20width%3D%22220%22%20height%3D%22180%22%3E%0A%0A%20%20%20%20%3Cpolygon%20points%3D%22110%2C20%20190%2C150%2030%2C150%22%20fill%3D%22gold%22%20stroke%3D%22black%22%20stroke-width%3D%223%22%3E%3C%2Fpolygon%3E%0A%0A%3C%2Fsvg%3E)

---

## ماذا يحدث؟

يرسم مثلثًا، لأن المتصفح يربط تلقائيًا:

آخر نقطة ⟶ أول نقطة.

---

# الفرق بين `<polyline>` و `<polygon>`

| Feature | `<polyline>` | `<polygon>` |
| --- | --- | --- |
| يرسم عدة خطوط متصلة | ✅ نعم | ✅ نعم |
| يغلق الشكل تلقائيًا | ❌ لا | ✅ نعم |
| مناسب للمخططات البيانية | ✅ نعم | ❌ لا |
| مناسب للأشكال المغلقة | ❌ لا | ✅ نعم |
| يمكن استخدام `fill` عمليًا | ❌ غالبًا لا | ✅ نعم |

---

# أمثلة عملية

## خط مفتوح

```
<polylinepoints="20,80 80,20 140,80"fill="none"stroke="blue"stroke-width="4"/>
```

---

## شكل مغلق

```
<polygonpoints="20,80 80,20 140,80"fill="orange"stroke="black"/>
```

---

# أشهر أسئلة المقابلات

### What is the difference between polyline and polygon?

> A polyline draws connected lines without closing the shape, while a polygon automatically closes the shape by connecting the last point to the first point.
> 

---

### Which SVG element is used to draw an open shape?

```
<polyline>
```

---

### Which SVG element is used to draw a closed shape?

```
<polygon>
```

---

### Which attribute defines the points?

```
points
```

---

### Can a polygon be filled?

✅ نعم.

لأنه يمثل شكلًا مغلقًا.

---

### Can a polyline be filled?

من الناحية التقنية نعم، لكن لأن الشكل مفتوح، تكون النتيجة غالبًا غير متوقعة أو غير مفيدة، لذلك في معظم الحالات يُستخدم:

```
fill="none"
```

مع `<polyline>`.

---

# مقارنة مع `<line>`

| Element | Purpose |
| --- | --- |
| `<line>` | خط واحد بين نقطتين |
| `<polyline>` | عدة خطوط متصلة مفتوحة |
| `<polygon>` | عدة خطوط متصلة تُغلق تلقائيًا |

---

# Best Practices

- استخدم `<line>` عندما تحتاج إلى خط واحد فقط.
- استخدم `<polyline>` للمخططات البيانية والخطوط المفتوحة.
- استخدم `<polygon>` للأشكال الهندسية المغلقة.
- استخدم `fill="none"` مع `<polyline>` إذا كان الهدف رسم المسار فقط.
- استخدم `stroke` و`stroke-width` لتحسين وضوح الخطوط.

---

# Senior Notes

هناك عدة نقاط يقع فيها كثير من المطورين:

### 1. الفرق الحقيقي هو إغلاق الشكل

العنصران يستخدمان نفس الخاصية:

```
points
```

لكن:

- `<polyline>` لا يغلق الشكل.
- `<polygon>` يغلق الشكل تلقائيًا.

وهذا هو الفرق الجوهري بينهما.

---

### 2. لا تستخدم `<polygon>` لرسم مسارات مفتوحة

إذا كنت ترسم:

- Graph
- Timeline
- Chart

فاستخدم:

```
<polyline>
```

وليس:

```
<polygon>
```

---

### 3. متى تستخدم `<path>` بدلًا منهما؟

إذا احتجت إلى:

- منحنيات (Curves).
- أقواس (Arcs).
- أشكال معقدة.
- دمج خطوط مستقيمة ومنحنية في عنصر واحد.

فاستخدم:

```
<path>
```

لأنه أكثر مرونة وقوة من جميع عناصر الأشكال الأخرى.

---

# 8.2.3 SVG Path

---

# السؤال الرابع

# What is the `<path>` element in SVG, and what does the `d` attribute do?

## الإجابة

> The `<path>` element is the most powerful and flexible SVG shape element. It can draw straight lines, curves, arcs, and complex custom shapes using a series of drawing commands stored in the `d` attribute.
> 

---

## لماذا تهتم الشركات بهذا السؤال؟

لأن معظم الأيقونات (Icons) والشعارات (Logos) والرسومات المعقدة في SVG تعتمد على عنصر `<path>`.

كما أن فهم فكرة `d` يساعد المطور على قراءة ملفات SVG والتعامل معها حتى وإن لم يكتبها يدويًا.

---

# 1. `<path>`

---

## الإجابة

> The `<path>` element is used to create custom shapes by combining multiple drawing commands into a single element.
> 

---

## متى نستخدمه؟

- Icons
- Logos
- Illustrations
- Charts
- Maps
- Complex Graphics

---

## المثال

```

```

[](data:image/svg+xml;utf8,%3Csvg%20width%3D%22200%22%20height%3D%22200%22%20viewBox%3D%220%200%20100%20100%22%3E%0A%0A%20%20%20%20%3Cpath%20d%3D%22M20%2020%20L80%2020%20L50%2080%20Z%22%20fill%3D%22royalblue%22%3E%3C%2Fpath%3E%0A%0A%3C%2Fsvg%3E)

---

## ماذا يحدث؟

يرسم شكلًا مخصصًا (في هذا المثال مثلثًا) باستخدام أوامر موجودة داخل الخاصية:

```
d
```

---

# 2. ما هي الخاصية `d`؟

---

## الإجابة

> The `d` attribute contains a sequence of drawing commands that define the shape of the path.
> 

---

## مثال

```
d="M20 20 L80 20 L50 80 Z"
```

كل جزء من هذا النص يمثل أمرًا يرشد المتصفح إلى كيفية رسم الشكل.

---

# أشهر أوامر Path

| Command | Meaning |
| --- | --- |
| M | Move To |
| L | Line To |
| H | Horizontal Line |
| V | Vertical Line |
| C | Cubic Bézier Curve |
| S | Smooth Cubic Curve |
| Q | Quadratic Bézier Curve |
| T | Smooth Quadratic Curve |
| A | Arc |
| Z | Close Path |

---

# ماذا تعني هذه الأوامر؟

## M (Move To)

ينقل نقطة البداية دون رسم خط.

---

## L (Line To)

يرسم خطًا مستقيمًا إلى نقطة جديدة.

---

## H (Horizontal Line)

يرسم خطًا أفقيًا.

---

## V (Vertical Line)

يرسم خطًا رأسيًا.

---

## C (Cubic Bézier Curve)

يرسم منحنى باستخدام نقطتي تحكم.

---

## S (Smooth Cubic Curve)

يكمل منحنى Cubic بشكل سلس.

---

## Q (Quadratic Bézier Curve)

يرسم منحنى باستخدام نقطة تحكم واحدة.

---

## T (Smooth Quadratic Curve)

يكمل منحنى Quadratic بشكل سلس.

---

## A (Arc)

يرسم قوسًا.

---

## Z (Close Path)

يغلق الشكل بربط آخر نقطة بأول نقطة.

---

# مقارنة بين `<polygon>` و `<path>`

| Feature | `<polygon>` | `<path>` |
| --- | --- | --- |
| يرسم أشكالًا بسيطة | ✅ نعم | ✅ نعم |
| يدعم المنحنيات | ❌ لا | ✅ نعم |
| يدعم الأقواس | ❌ لا | ✅ نعم |
| يرسم أي شكل معقد | ❌ لا | ✅ نعم |
| الأكثر استخدامًا في الأيقونات | ❌ | ✅ |

---

# أشهر أسئلة المقابلات

### What is the purpose of the path element?

> It is used to draw custom and complex vector shapes.
> 

---

### What does the `d` attribute contain?

> A sequence of drawing commands that defines the path.
> 

---

### What is the most powerful SVG shape element?

```
<path>
```

---

### Do developers usually write SVG paths manually?

في معظم الحالات **لا**.

عادةً يتم توليدها بواسطة أدوات التصميم مثل:

- Figma
- Adobe Illustrator
- Sketch

ثم تُستخدم داخل المشروع كما هي.

---

### Do you need to memorize all path commands?

❌ لا.

يكفي أن تعرف وظيفتها العامة وكيف تقرأ ملفات SVG عند الحاجة.

---

# Best Practices

- استخدم `<path>` عندما لا تكفي الأشكال الأساسية مثل `<rect>` أو `<circle>`.
- احتفظ بمسارات SVG التي تنتجها أدوات التصميم كما هي، ولا تعدلها إلا عند الحاجة.
- استخدم أدوات مثل **SVGOMG** لتقليل حجم ملفات SVG قبل إضافتها إلى المشروع.
- لا تحاول كتابة مسارات معقدة يدويًا إلا إذا كانت هناك حاجة فعلية.

---

# Senior Notes

هناك عدة نقاط يقع فيها كثير من المطورين:

### 1. لا تحفظ أوامر Path

من غير المتوقع في المقابلات أو العمل اليومي أن تحفظ جميع أوامر:

```
M
L
H
V
C
S
Q
T
A
Z
```

الأهم هو أن تعرف أنها أوامر تحدد طريقة رسم الشكل داخل الخاصية `d`.

---

### 2. معظم ملفات SVG تُولد تلقائيًا

الأيقونات والرسومات التي تستخدمها في المشاريع غالبًا يتم تصديرها من أدوات التصميم، وليس كتابتها يدويًا.

---

### 3. اقرأ ولا تكتب

في المشاريع العملية، ستحتاج غالبًا إلى **قراءة** قيمة `d` أو استبدالها، أكثر من حاجتك إلى إنشائها من الصفر.

# SVG Styling

---

# السؤال الخامس

# What are the most common SVG styling attributes, and how do they affect SVG elements?

---

---

## الإجابة

> SVG elements can be styled using presentation attributes such as `fill`, `stroke`, `stroke-width`, `opacity`, and `fill-rule`. These attributes control the appearance of SVG shapes, including their color, outline, transparency, and filling behavior.
> 

---

## لماذا تهتم الشركات بهذا السؤال؟

لأن معظم التعديلات التي يجريها مطور Front-End على ملفات SVG تكون متعلقة بالألوان، والحدود، والشفافية، وليس برسم الأشكال نفسها.

كما أن الفرق بين `fill` و`stroke` من أكثر الأسئلة شيوعًا في المقابلات.

---

# 1. `fill`

---

## الإجابة

> The `fill` attribute defines the interior color of an SVG shape.
> 

---

## المثال

```

```

[](data:image/svg+xml;utf8,%3Csvg%20width%3D%22120%22%20height%3D%22120%22%3E%0A%0A%20%20%20%20%3Ccircle%20cx%3D%2260%22%20cy%3D%2260%22%20r%3D%2240%22%20fill%3D%22royalblue%22%3E%3C%2Fcircle%3E%0A%0A%3C%2Fsvg%3E)

---

## ماذا يحدث؟

يملأ الدائرة باللون:

```
royalblue
```

---

## إزالة التعبئة

```
fill="none"
```

---

## متى نستخدمه؟

- Icons
- Logos
- Shapes
- Charts

---

# 2. `stroke`

---

## الإجابة

> The `stroke` attribute defines the outline color of an SVG shape.
> 

---

## المثال

```
<rectx="20"y="20"width="80"height="60"fill="white"stroke="black"/>
```

---

## ماذا يحدث؟

يرسم حدًا أسود حول المستطيل.

---

# 3. `stroke-width`

---

## الإجابة

> The `stroke-width` attribute defines the thickness of the outline.
> 

---

## المثال

```
<circlecx="60"cy="60"r="40"stroke="red"stroke-width="6"fill="none"/>
```

---

## ماذا يحدث؟

يزيد سمك الحد إلى:

```
6
```

وحدات SVG.

---

# 4. `opacity`

---

## الإجابة

> The `opacity` attribute controls the transparency of an SVG element.
> 

---

## القيم

من:

```
0
```

إلى:

```
1
```

---

## المثال

```
<circlecx="60"cy="60"r="40"fill="green"opacity="0.5"/>
```

---

## ماذا يحدث؟

تظهر الدائرة بنسبة شفافية:

```
50%
```

---

# 5. `fill-rule`

---

## الإجابة

> The `fill-rule` attribute defines how the inside of complex or self-intersecting paths is determined.
> 

---

## القيم

- `nonzero`
- `evenodd`

---

## متى نستخدمه؟

يستخدم غالبًا مع:

```
<path>
```

وليس مع الأشكال البسيطة مثل:

- `<rect>`
- `<circle>`
- `<ellipse>`

---

## ماذا يفعل؟

عندما يحتوي الشكل على مسارات متداخلة أو متقاطعة، يحدد `fill-rule` أي المناطق تُعتبر داخل الشكل وبالتالي يتم ملؤها.

---

# مقارنة بين الخصائص

| Attribute | Purpose |
| --- | --- |
| `fill` | لون الجزء الداخلي |
| `stroke` | لون الحد الخارجي |
| `stroke-width` | سمك الحد |
| `opacity` | درجة الشفافية |
| `fill-rule` | طريقة ملء المسارات المعقدة |

---

# مثال متكامل

```

```

[](data:image/svg+xml;utf8,%3Csvg%20width%3D%22200%22%20height%3D%22200%22%3E%0A%0A%20%20%20%20%3Crect%20x%3D%2230%22%20y%3D%2230%22%20width%3D%22120%22%20height%3D%2280%22%20fill%3D%22skyblue%22%20stroke%3D%22navy%22%20stroke-width%3D%224%22%20opacity%3D%220.8%22%3E%3C%2Frect%3E%0A%0A%3C%2Fsvg%3E)

---

# أشهر أسئلة المقابلات

### Which attribute sets the fill color?

```
fill
```

---

### Which attribute sets the outline color?

```
stroke
```

---

### Which attribute controls the border thickness?

```
stroke-width
```

---

### Which attribute controls transparency?

```
opacity
```

---

### Which attribute is mainly used with complex paths?

```
fill-rule
```

---

### What is the difference between `fill` and `stroke`?

> `fill` colors the inside of the shape, while `stroke` colors its outline.
> 

---

# مقارنة بين CSS وSVG Styling

| Feature | CSS | SVG Presentation Attribute |
| --- | --- | --- |
| `fill` | ✅ | ✅ |
| `stroke` | ✅ | ✅ |
| `stroke-width` | ✅ | ✅ |
| `opacity` | ✅ | ✅ |

يمكن كتابة هذه الخصائص مباشرة داخل عناصر SVG أو تطبيقها من خلال CSS.

---

# Best Practices

- استخدم `fill` لتحديد اللون الداخلي للأشكال.
- استخدم `stroke` مع `stroke-width` عندما تحتاج إلى حدود واضحة.
- استخدم `opacity` بحذر حتى لا تؤثر على وضوح الرسومات.
- استخدم `fill-rule` فقط عند التعامل مع مسارات (`<path>`) معقدة أو متقاطعة.
- إذا كنت تستخدم نفس التنسيقات على عدة عناصر، فضعها في CSS لتسهيل الصيانة وإعادة الاستخدام.

---

# Senior Notes

هناك عدة نقاط يقع فيها كثير من المطورين:

### 1. `fill` و`stroke` يعملان معًا

ليس عليك الاختيار بينهما.

يمكن أن يحتوي الشكل على:

- لون داخلي (`fill`).
- وحد خارجي (`stroke`).

في الوقت نفسه.

---

### 2. `opacity` يؤثر على العنصر بالكامل

إذا أردت جعل **لون التعبئة فقط** شفافًا دون التأثير على الحد، فاستخدم:

- `fill-opacity`
- أو `stroke-opacity`

بدلًا من:

```
opacity
```

الذي يجعل العنصر بالكامل شفافًا.

---

### 3. `fill-rule` ليس للاستخدام اليومي

معظم مطوري Front-End لن يحتاجوا إلى تغييره يدويًا، لكنه يظهر كثيرًا في ملفات SVG المصدرة من أدوات مثل Figma أو Illustrator، لذا يكفي معرفة وظيفته العامة.

# 8.3 تنسيق وتحسين مظهر الـ SVG (SVG Styling)

### مثال الكود:

HTML

```
<!-- تنسيق عنصر SVG باستخدام الخصائص المباشرة (Presentation Attributes) وعبر CSS -->
<svg viewBox="0 0 300 120" width="100%" height="auto" xmlns="http://www.w3.org/2000/svg">
  <!-- 1. التنسيق عبر الخصائص المباشرة (Attributes) -->
  <rect
    x="10" y="10" width="80" height="80"
    fill="#3b82f6"
    stroke="#1d4ed8"
    stroke-width="4"
    rx="8"
  />

  <!-- 2. التنسيق المتقدم باستخدام خطوط الحواف والأطراف -->
  <path
    d="M 120 20 L 160 80 L 200 20"
    fill="none"
    stroke="#ef4444"
    stroke-width="8"
    stroke-linecap="round"
    stroke-linejoin="round"
  />

  <!-- 3. التنسيق المباشر عبر CSS الداخلي مع الشفافية -->
  <circle
    cx="250" cy="50" r="35"
    style="fill: #10b981; fill-opacity: 0.7; stroke: #047857; stroke-width: 3;"
  />
</svg>
```

### السؤال:

**ما هي خصائص التنسيق الأكثر شيوعاً في SVG، وكيف تؤثر على عناصر الرسم؟**

*(بالإنجليزي: What are the most common SVG styling attributes, and how do they affect SVG elements?)*

### الإجابة النموذجية للمقابلة (Interview Answer):

> **تنسيق عناصر الـ SVG يختلف عن عناصر HTML العادية؛ فنحن لا نستخدم `background-color` أو `border` بل نستخدم خصائص تقديمية خاصة (Presentation Attributes). أهم الخصائص الشائعة هي:**
> 
> - **`fill`:** لتحديد لون التعبئة الداخلي للشكل.
> - **`stroke`:** لتحديد لون الخط الخارجي أو حدود الشكل (Border).
> - **`stroke-width`:** لتحديد سمك خط الحدود.
> - **`stroke-linecap` و `stroke-linejoin`:** للتحكم في شكل نهايات الخطوط وزوايا التقائها (دائرية، حادة، أو مسطحة).
> - **`fill-opacity` و `stroke-opacity`:** للتحكم في درجة شفافية التعبئة والحدود بشكل منفصل.
> 
> **يمكن تطبيق هذه الخصائص كخصائص مباشرة (HTML Attributes)، أو كتابتها داخل ملف CSS خارجي، أو عبر خاصية `style`.**
> 

### الشرح بالتفصيل:

كمهندس واجهات (UI Engineer)، فهم خصائص التنسيق الخاصة بالـ SVG يمنحك قدرة فائقة على التحكم في الأيقونات والرسوم التوضيحية وتعديل ألوانها وتفاعلاتها عند التحويم (Hover States) أو تغيير الثيم (Dark / Light Mode) بسهولة عبر CSS دون الحاجة لإعادة تحميل صور جديدة.

تعال نفصص أهم الخصائص وكيفية تأثيرها:

#### 1. تفكيك خصائص التنسيق الأساسية 🎨

#### أولاً: خصائص التعبئة والشفافية (Fill & Opacity)

- **`fill`:** يُحدد لون، مدرج ألوان (Gradient)، أو نمط (Pattern) لتعبئة الجزء الداخلي للشكل. (القيمة الافتراضية هي اللون الأسود `#000000`). لتفريغ الشكل نستخدم `fill="none"`.
- **`fill-opacity`:** تتحكم في درجة شفافية التعبئة الداخلية فقط (من `0` شفاف تماماً إلى `1` معتم) دون التأثير على شفافية خط الحدود.
- **`opacity`:** تضبط الشفافية الإجمالية للعنصر بالكامل (التعبئة والحدود معاً).

#### ثانياً: خصائص الحدود والخطوط (Stroke Control)

- **`stroke`:** لون خط الرسم الخارجي. (الافتراضي لا يوجد خط حدود `none`).
- **`stroke-width`:** سمك خط الحدود (يُقاس بالبكسل أو وحدات الـ SVG).
- **`stroke-dasharray`:** يحول الخط المصلد إلى خط مقطّع (Dashed Line) عبر تحديد أطوال الشرطات والفواصل الفارغة (مثل `stroke-dasharray="5 5"`).

#### ثالثاً: خصائص حواف ونهايات الخطوط (Caps & Joins)

- **`stroke-linecap`:** تُحدد شكل **نهاية الخط المفتوح**.
    - `butt`: نهاية مسطحة حادة عند نقطة النهاية (الافتراضي).
    - `round`: نهاية دائرية ناعمة بارزة قتلياً.
    - `square`: نهاية مربعة مسطحة بارزة.
- **`stroke-linejoin`:** تُحدد شكل **الزاوية عند التقاء خطين**.
    - `miter`: زاوية حادة مدببة (الافتراضي).
    - `round`: زاوية دائرية ناعمة.
    - `bevel`: زاوية مشطوفة مسطحة.

#### 2. جدول الملخص المقارن 🔍

| **الخاصية (Attribute)** | **الخاصية المقابلة لها في CSS العادي** | **التأثير والوظيفة** |
| --- | --- | --- |
| **`fill`** | `background-color` | تلوين المساحة الداخلية للشكل. |
| **`stroke`** | `border-color` | تلوين الإطار الخارجي والخطوط. |
| **`stroke-width`** | `border-width` | تحديد سمك الحدود. |
| **`stroke-linecap`** | *لا يوجد مقابل مباشر* | تشكيل أطراف ونهايات الخطوط (`round`, `butt`). |
| **`stroke-linejoin`** | *لا يوجد مقابل مباشر* | تشكيل زوايا التقاء الخطوط (`round`, `miter`). |

#### 3. لمحة ذكاء للـ UI Engineer (سؤال الفخ للمقابلة)

الـ Interviewer ممكن يسألك: **"كيف نقوم بتنظيم أيقونات الـ SVG في المشروع لتتغير ألوانها تلقائياً مع لون النص عبر CSS (مثل لون زر المتصفح)؟"**

**الإجابة الذكية:**

- نستخدم القيمة الخاصة **`currentColor`** داخل خصائص الـ SVG!
- عندما نكتب `<path fill="currentColor">` أو نحددها في CSS:CSS
    
    ```
    svg path {
      fill: currentColor;
    }
    ```
    
    سيرث الـ SVG لون النص (`color`) المعين للعنصر الأب (Parent Element) تلقائياً! إذا تغير لون الزر على الـ Hover، ستتغير لون أجزاء الأيقونة فوراً دون الحاجة لكتابة CSS معقد للـ SVG نفسه.
    

#### الكلمات المفتاحية للحفظ (Keywords):

- **Presentation Attributes:** خصائص التقديم والتنسيق الخاصة بالـ SVG.
- **`fill` vs `stroke`:** الفارق بين لون التعبئة الداخلية ولون الإطار الخارجي.
- **Line Aesthetics (`stroke-linecap` / `stroke-linejoin`):** التحكم في جماليات ونعومة نهايات وزوايا الخطوط.
- **Dynamic Styling (`currentColor`):** ربط لون الـ SVG بلون النص الأب لتسهيل التفاعل والثيمات.

#### جملتك النموذجية في المقابلة:

> **"SVG styling relies on dedicated presentation attributes rather than standard CSS box-model properties. Primary attributes include `fill` for internal coloring and `stroke` combined with `stroke-width` for outline rendering. To refine line aesthetics, we use `stroke-linecap` (such as `round` or `butt`) for line endings and `stroke-linejoin` for corner joints. Modern UI engineering heavily leverages `fill="currentColor"` so that inline SVGs automatically inherit their parent container's CSS `color` property, enabling seamless hover states and theme switching**
> 

# 8.4 SVG Reusable Elements

---

# السؤال السادس

# What are the `<defs>`, `<symbol>`, and `<use>` elements in SVG, and why are they useful?

## الإجابة

> The `<defs>` element stores reusable SVG definitions without rendering them immediately. The `<symbol>` element defines reusable graphic templates, while the `<use>` element creates copies of previously defined SVG content.
> 

---

## لماذا تهتم الشركات بهذا السؤال؟

لأن إعادة استخدام الرسومات بدلاً من تكرارها:

- تقلل حجم الكود.
- تسهل صيانة ملفات SVG.
- تُستخدم في أنظمة الأيقونات (SVG Sprite).
- تُستخدم في Design Systems ومكتبات المكونات.

---

# 1. `<defs>`

---

## الإجابة

> The `<defs>` element stores SVG elements that are not rendered immediately but can be referenced later.
> 

---

## متى نستخدمه؟

- تخزين Shapes
- Symbols
- Gradients
- Patterns
- Filters

---

## المثال

```

```

[](data:image/svg+xml;utf8,%3Csvg%20width%3D%22200%22%20height%3D%22100%22%3E%0A%0A%20%20%20%20%3Cdefs%3E%0A%0A%20%20%20%20%20%20%20%20%3Ccircle%20id%3D%22myCircle%22%20cx%3D%2250%22%20cy%3D%2250%22%20r%3D%2230%22%20fill%3D%22royalblue%22%3E%3C%2Fcircle%3E%0A%0A%20%20%20%20%3C%2Fdefs%3E%0A%0A%3C%2Fsvg%3E)

---

## ماذا يحدث؟

لن تظهر الدائرة.

لأن العناصر الموجودة داخل:

```
<defs>
```

تُخزن فقط ولا تُرسم مباشرة.

---

# 2. `<symbol>`

---

## الإجابة

> The `<symbol>` element defines a reusable SVG graphic that can be instantiated multiple times using the `<use>` element.
> 

---

## متى نستخدمه؟

- Icon Libraries
- Design Systems
- Reusable Components

---

## المثال

```

```

[](data:image/svg+xml;utf8,%3Csvg%3E%0A%0A%20%20%20%20%3Csymbol%20id%3D%22star%22%20viewBox%3D%220%200%20100%20100%22%3E%0A%0A%20%20%20%20%20%20%20%20%3Cpolygon%20points%3D%2250%2C5%2061%2C39%2098%2C39%2068%2C60%2079%2C95%2050%2C73%2021%2C95%2032%2C60%202%2C39%2039%2C39%22%3E%3C%2Fpolygon%3E%0A%0A%20%20%20%20%3C%2Fsymbol%3E%0A%0A%3C%2Fsvg%3E)

---

## ماذا يحدث؟

يتم تعريف شكل نجمة، لكنه لا يظهر حتى يتم استخدامه.

---

# 3. `<use>`

---

## الإجابة

> The `<use>` element creates a copy of an existing SVG element referenced by its ID.
> 

---

## المثال

```

```

[](data:image/svg+xml;utf8,%3Csvg%20width%3D%22300%22%20height%3D%22120%22%3E%0A%0A%20%20%20%20%3Cdefs%3E%0A%0A%20%20%20%20%20%20%20%20%3Ccircle%20id%3D%22dot%22%20cx%3D%2220%22%20cy%3D%2220%22%20r%3D%2215%22%20fill%3D%22tomato%22%3E%3C%2Fcircle%3E%0A%0A%20%20%20%20%3C%2Fdefs%3E%0A%0A%20%20%20%20%3Cuse%20href%3D%22%23dot%22%3E%3C%2Fuse%3E%0A%0A%20%20%20%20%3Cuse%20href%3D%22%23dot%22%20x%3D%2260%22%3E%3C%2Fuse%3E%0A%0A%20%20%20%20%3Cuse%20href%3D%22%23dot%22%20x%3D%22120%22%3E%3C%2Fuse%3E%0A%0A%3C%2Fsvg%3E)

---

## ماذا يحدث؟

يعرض ثلاث دوائر.

بينما تم تعريف الدائرة مرة واحدة فقط.

---

# استخدام `<symbol>` مع `<use>`

```

```

[](data:image/svg+xml;utf8,%3Csvg%20width%3D%22300%22%20height%3D%22100%22%3E%0A%0A%20%20%20%20%3Csymbol%20id%3D%22square%22%20viewBox%3D%220%200%2050%2050%22%3E%0A%0A%20%20%20%20%20%20%20%20%3Crect%20width%3D%2250%22%20height%3D%2250%22%20fill%3D%22steelblue%22%3E%3C%2Frect%3E%0A%0A%20%20%20%20%3C%2Fsymbol%3E%0A%0A%20%20%20%20%3Cuse%20href%3D%22%23square%22%3E%3C%2Fuse%3E%0A%0A%20%20%20%20%3Cuse%20href%3D%22%23square%22%20x%3D%2280%22%3E%3C%2Fuse%3E%0A%0A%20%20%20%20%3Cuse%20href%3D%22%23square%22%20x%3D%22160%22%3E%3C%2Fuse%3E%0A%0A%3C%2Fsvg%3E)

---

## ماذا يحدث؟

يعرض ثلاثة مربعات.

بينما تم تعريف المربع مرة واحدة فقط.

---

# مقارنة بين العناصر

| Element | Purpose |
| --- | --- |
| `<defs>` | تخزين عناصر SVG بدون عرضها |
| `<symbol>` | تعريف عنصر قابل لإعادة الاستخدام |
| `<use>` | إنشاء نسخة من عنصر معرف مسبقًا |

---

# أشهر أسئلة المقابلات

### What is the purpose of the defs element?

> It stores reusable SVG definitions without rendering them immediately.
> 

---

### Does defs render anything?

❌ لا.

---

### What is the purpose of symbol?

> It defines reusable SVG graphics.
> 

---

### What does the use element do?

> It creates a copy of an existing SVG element.
> 

---

### Why use use instead of duplicating SVG code?

> It reduces code duplication, improves maintainability, and keeps SVG files smaller.
> 

---

### Which attribute references an existing element?

```
href="#icon"
```

---

# مقارنة بين `<defs>` و `<symbol>`

| `<defs>` | `<symbol>` |
| --- | --- |
| حاوية لتخزين عناصر SVG | تعريف عنصر SVG قابل لإعادة الاستخدام |
| قد يحتوي على أي عنصر SVG | يُستخدم عادةً مع `<use>` لإنشاء قوالب رسومية |
| لا يعرض محتواه مباشرة | لا يعرض محتواه مباشرة |

---

# Best Practices

- استخدم `<defs>` لتخزين العناصر التي ستُعاد استخدامها.
- استخدم `<symbol>` لإنشاء أيقونات أو رسومات قابلة لإعادة الاستخدام.
- استخدم `<use>` بدلاً من تكرار نفس الرسم عدة مرات.
- أعطِ كل عنصر معرفًا (`id`) واضحًا وسهل الفهم.
- حافظ على تنظيم الرسومات المشتركة داخل ملف SVG.

---

# Senior Notes

هناك عدة نقاط يقع فيها كثير من المطورين:

### 1. `<defs>` لا يعرض أي شيء

وجود عنصر داخل:

```
<defs>
```

لا يعني أنه سيظهر على الشاشة.

يجب الإشارة إليه باستخدام عناصر مثل:

```
<use>
```

أو مراجع SVG أخرى.

---

### 2. `<use>` ينشئ نسخة

العنصر:

```
<use>
```

لا ينقل العنصر الأصلي، بل ينشئ نسخة منه يمكن وضعها في أماكن مختلفة داخل نفس SVG.

---

### 3. الاستخدام الحقيقي في المشاريع

في المشاريع الحديثة، تُستخدم هذه العناصر غالبًا لبناء:

- SVG Sprite Sheets
- Icon Libraries
- Design Systems

بدلاً من كتابة نفس الأيقونة أو الشكل أكثر من مرة.

# إعادة استخدام وتجميع عناصر الـ SVG (`<defs>`, `<symbol>`, `<use>`, `<g>`)

### مثال الكود:

HTML

```
<svg style="display: none;">
  <!-- 1. مكتبة التعاريف الحاوية للعناصر غير المعروضة مباشرة -->
  <defs>
    <!-- رمز قابل لإعادة الاستخدام يملك نظام viewBox خاصاً به -->
    <symbol id="icon-star" viewBox="0 0 24 24">
      <polygon points="12,2 15,8 22,9 17,14 18,21 12,17 6,21 7,14 2,9 9,8" />
    </symbol>

    <!-- تجميعة أشكال لتحديد مظهر متكرر (Group) -->
    <g id="badge-shape">
      <rect x="0" y="0" width="80" height="30" rx="15" fill="#3b82f6" />
    </g>
  </defs>
</svg>

<!-- 2. استدعاء وإعادة استخدام الأيقونات والأشكال في أي مكان في الواجهة -->
<svg width="32" height="32" style="fill: #f59e0b;">
  <use href="#icon-star" />
</svg>

<svg width="32" height="32" style="fill: #ef4444;">
  <use href="#icon-star" />
</svg>

<svg width="80" height="30">
  <use href="#badge-shape" />
</svg>
```

### السؤال:

**ما هي عناصر `<defs>` و `<symbol>` و `<use>` في SVG، ولماذا هي مفيدة؟**

*(بالإنجليزي: What are the `<defs>`, `<symbol>`, and `<use>` elements in SVG, and why are they useful?)*

### الإجابة النموذجية للمقابلة (Interview Answer):

> **تُستخدم هذه العناصر لبناء أنظمة أيقونات (Icon Systems) وأجسام قابلة لإعادة الاستخدام داخل SVG مع تطبيق مبدأ عدم تكرار الكود (DRY - Don't Repeat Yourself):**
> 
> - **عنصر `<defs>`:** هو حاوية تخزين للأغراض والتعاريف التي لا يتم رسمها على الشاشة مباشرة (مثل الأيقونات، المدرجات اللونية Gradients، والأقنعة Masks).
> - **عنصر `<symbol>`:** يغلف الأشكال لبناء عنصر قابل للاستخدام كأيقونة، ويتميز بقبوله لخاصية `viewBox` الخاصة به للتحكم في مقياسه وتجاوبه بصورة مستقلة.
> - **عنصر `<use>`:** يقوم باستدعاء واستنسال (Instantiate) أي عنصر معرف سابقاً عبر معرّفه (`id`) ورسمه في الموقع والمقياس المطلوب.

### الشرح بالتفصيل:

عند التفكير في بناء نظام واجهات حديث (Design System) يضم العشرات من الأيقونات المكررة في القوائم والأزرار، تكرار أكواد الـ `<path>` يؤدي لضخامة حجم ملفات الـ HTML وتدهور الأداء. كمهندس واجهات (UI Engineer)، تمنحك هذه العناصر القدرة على إنشاء **مكتبة أيقونات SVG موحدة (SVG Sprite System)**.

تعال نفصص الدور الجوهري لكل عنصر:

#### 1. تفكيك العناصر الثلاثة ووظائفها

#### أولاً: عنصر `<defs>` (Definitions Wrapper)

- **الوظيفة:** اختصار لـ Definitions. يعمل كمستودع تخزين داخلي.
- **السلوك:** **أي عنصر يوضع داخل `<defs>` لا يظهر على الشاشة إطلاقاً** حتى يتم استدعاؤه صراحة باستخدام عنصر `<use>` أو الإشارة إليه عبر CSS (مثل الـ Gradients والـ Filters).

#### ثانياً: عنصر `<symbol>` (Template Container)

- **الوظيفة:** يعمل كقالب هيكلي (Template) لجمع مجموعة من عناصر الرسم وتسميتها بـ `id`.
- **الميزة الفائقة:** يمتلك خاصية **`viewBox`** و **`preserveAspectRatio`** مستقلة خاصة به! هذا يعني أنه يمكن تحجيم وتمديد الأيقونة بأي حجم مختلف داخل حقول `<use>` دون تشويه الإحداثيات الأصلية.

#### ثالثاً: عنصر `<use>` (Instantiation Engine)

- **الوظيفة:** يرسم نسخة حية من أي عنصر مسبق التعريف (`symbol`, `g`, `path`) باستخدام الخاصية `href="#id_name"`.
- **المرونة:** يتيح لك إعادة رسم الرسمة نفسها في أكثر من مكان بأحجام وألوان مختلفة باستخدام CSS، حيث تُجلب عناصر الـ SVG المعنية داخل Shadow DOM افتراضي وخفيف.

#### 2. الفارق بين `<symbol>` وعنصر التجميع العادي `<g>`

غالبًا ما يسأل المطورون عن الفرق بين وضع العناصر داخل المجمع `<g>` (Group) أو داخل `<symbol>`:

| وجه المقارنة | عنصر التجميع `<g>` | عنصر القالب `<symbol>` |
| --- | --- | --- |
| **الهدف الرئيسي** | تجميع مجموعة عناصر لتطبيق تنسيق مشترك (مثل `fill` أو `transform`). | بناء أيقونة وقالب مستقل قابل للنسخ والتكرار. |
| **الظهور الافتراضي** | **يظهر فوريًا على الشاشة** إذا لم يكن داخل `<defs>`. | **مخفي افتراضيًا** ولا يظهر إلا عند استدعائه بـ `<use>`. |
| **دعم `viewBox`** | لا يدعم `viewBox` لتحديد أبعاد مستقلة. | **يدعم `viewBox`** كاملاً للتكيف والتحجيم المتجاوب. |

#### 3. لمحة ذكاء للـ UI Engineer (سؤال الفخ للمقابلة)

الـ Interviewer ممكن يسألك: **"كيف نستخدم هذه الأوسمة لبناء مكتبة أيقونات متكاملة (SVG Sprite) تُحمل مرة واحدة فقط في الموقع؟"**

**الإجابة الذكية:**

- نضع ملف `sprite.svg` خارجي يحتوي على `<defs>` بداخلها كل الـ `<symbol>` الخاصة بأيقونات الموقع.
- في أي صفحة HTML، نستدعي أي أيقونة بسطر واحد فقط:HTML
    
    ```
    <svg class="icon">
      <use href="/assets/sprite.svg#icon-star" />
    </svg>
    ```
    
- **الفائدة الممتازة:** يتم تخزين ملف الـ Sprite في ذاكرة المتصفح المؤقتة (Browser Cache)، وتتغير ألوان الأيقونات بسهولة عبر CSS بفضل خاصية `fill: currentColor`.

#### الكلمات المفتاحية للحفظ (Keywords):

- **SVG Sprite System:** نظام مجمّع الأيقونات الموحد.
- **Invisible Storage (`<defs>`):** حاوية التخزين المخفية للتعاريف.
- **Encapsulated Templates (`<symbol>`):** قوالب رسم مستقلة تدعم `viewBox`.
- **Reusability and DRY (`<use>`):** استدعاء النسخ وتقليل حجم الكود.

#### جملتك النموذجية في المقابلة:

> **"`<defs>`, `<symbol>`, and `<use>` form the foundation of scalable SVG icon systems. `<defs>` acts as a non-rendering repository for reusable assets like gradients or masks. `<symbol>` defines a graphic template that includes its own `viewBox` for independent responsive scaling. Finally, `<use>` references these templates by ID (`href="#id"`) to instantiate them anywhere in the DOM. This structure minimizes markup duplication, leverages browser caching via SVG sprites, and enables dynamic styling with CSS."**
> 

طيب السؤال هل فعلا يتم العمل بها في المشاريع الحقيقة ام الان في طرق اخرى

**نعم، يتم العمل بها فعلياً وبكثرة في المشاريع الحقيقية، لكن النمط البرمجي (Architecture Pattern) هو الذي اختلف وتطوّر.**

في سوق العمل اليوم، ينقسم استخدام هذه التقنيات إلى قسمين: **طريقة معتمدة ومطلوبة في مشاريع ضخمة**، و**حلول حديثة بديلة** تم ابتكارها لتسهيل حياة المطورين.

### أولاً: هل يُستخدم `<defs>`, `<symbol>`, `<use>` في المشاريع الحقيقية؟

**نعم، وبشدة.** هذا الأسلوب يُسمى في السوق **SVG Sprite Sheet System**، وهو المعيار القياسي (Industry Standard) في العديد من الشركات الكبرى والمكتبات، للأسباب التالية:

1. **الأداء الفائق (Performance & Caching):** بدلاً من أن يحتوي ملف الـ HTML على آلاف الأسطر من أكواد الـ SVG المكررة، يتم تجميع كل أيقونات الموقع في ملف SVG واحد مستقر (مثل `icons-sprite.svg`). يرسل السيرفر هذا الملف **مرة واحدة فقط** ويتم حفظه في ذاكرة المتصفح (Browser Cache)، ثم تُستدعى الأيقونات عبر `<use href="/icons-sprite.svg#icon-name" />`.
2. **أنظمة التصميم الضخمة (Design Systems):** في المشاريع التي تبني مكتبة عناصر خاصة بها (Enterprise UI Kits)، يُفضل استخدام SVG Sprites للحفاظ على خفة أوزان الصفحات وحذف أي اعتمادات على مكتبات خارجية.

### ثانياً: الطرق الأخرى الحديثة المستعملة حالياً (Alternatives)

مع انتشار أطر العمل الحديثة مثل **React, Vue, Next.js, و Angular**، ظهرت أنماط أخرى تنافس أو تكمل طريقة الـ Sprites:

| الطريقة الحديثة | كيف تعمل؟ | متى تُستخدم في المشاريع الحقيقية؟ |
| --- | --- | --- |
| **1. الأيقونات كمكونات (Inline Components)** | تحويل ملف الـ SVG إلى مكون جاهز (مثل `<StarIcon/>`) عبر أدوات مثل `SVGR` أو مكتبات مثل **Lucide Icons** و **Heroicons**. | **الطريقة الأكثر انتشاراً حالياً** في مشاريع React / Next.js لأنها تتيح التفاعل الكامل مع الـ Component وحصانتها عبر TypeScript بسهولة. |
| **2. مكتبات الأيقونات البرمجية (Icon Libraries)** | استيراد الأيقونات جاهزة من مكتبات مثبتة بـ npm (مثل `react-icons` أو `font-awesome`). | في المشاريع السريعة والمستعجلة، حيث لا يريد الفريق إضاعة الوقت في تصميم كل أيقونة يدويًا. |
| **3. خطوط الأيقونات (Icon Fonts)** | تحويل مجموعة أشكال إلى خط شبيه بـ (Font-Awesome WOFF2). | **طريقة قديمة نسبياً** وبدأ يتراجع استخدامها لصالح الـ SVG بسبب مشاكل إمكانية الوصول (Accessibility) والتنسيق. |

### الخلاصة لمهندس الواجهات (UI Engineer):

- **في المشاريع الصغيرة والحديثة (React/Next.js):** ستجد أن أغلب الفرق تفضل **Lucide Icons** أو **Inline Component SVGs** لسهولة التطوير والتكامل مع الكود.
- **في المشاريع الضخمة، المنصات الكبيرة، ومواقع الخدمات (Enterprise Applications):** ستجد نظام **`<symbol>` + `<use>` (SVG Sprites)** هو الملك بلا منازع لأنه يقدم أفضل كفاءة شبكية (Network Efficiency) وحفظ ذاكرة ممتاز.

فهمك لـ `<defs>`, `<symbol>`, و `<use>` يجعلك ممتلكاً لأساسيات كيف تعمل مكتبات الواجهات تحت الإطار، وهو ما يميز المهندس المتمكن عن مجرد مجمع مكتبات في المقابلات الوظيفية!

تمام اريد ان افهم متي اقول لنفسي محتاجة استخدمهم يعني كيف استخدمهم في 
المشاريع الحقيقة و اي نوعية المشاريع لا بتحتاجهم فهمتني ؟  كل عناصر ال 
SVG

فهمك الدقيق لـ **"متى ولماذا"** تختارين التقنية هو ما يفرق بين مهندس واجهات متمكن (UI Engineer) ومطور ينقل الكود فقط.

إليك الدليل العملي الكامل لربط جميع عناصر SVG بالمشاريع الحقيقية:

### 1. الأشكال الأساسية (`<rect>`, `<circle>`, `<polygon>`, إلخ)

- **متى تقولين لنفسك: "سأكتب شكل أساسي بيدي"؟**
    - عند بناء **عناصر واجهة ديناميكية خفيفة جدًا** لا تستدعي فتح برنامج تصميم (Figma).
    - **مثال عملي:** مؤشر حالة المستخدم (دائرة خضراء للمتصل `online` حمراء للـ `offline`)، أو بطاقات التنبيهات (Badges)، أو زر إغلاق مربع بسيط (`<rect>`).
    - **مثال آخر:** رسم أشكال هندسية ناعمة تحيط بالنصوص أو الخلفيات وتتفاعل مع التحويم (Hover).
- **نوعية المشاريع التي تحتاجها:**
    - dashboards وواجهات الإدارة: لبناء النقاط الدليلية (Legend Dots)، والبطاقات الإحصائية، وأشرطة التقييم السريعة.

### 2. المسارات المتقدمة والأنماط (`<path>`, `fill`, `stroke`, `stroke-dasharray`)

- **متى تقولين لنفسك: "سأستخدم `<path>` وخصائص التنسيق الخاصة به"؟**
    - عند الحاجة لـ **أيقونات معقدة، شعارات (Logos)، رسوم توضيحية (Illustrations)، أو رسم حركة أنيميشن حية**.
    - **مثال عملي:** عند تنفيذ **Animation لرسم الأيقونة (Line Drawing Animation)**؛ مثل رسم علامة الصح `✔` خطوة بخطوة عند نجاح عملية الدفع، أو رسم خط متعرج في الرسم البياني عبر تحريك `stroke-dashoffset`.
- **نوعية المشاريع التي تحتاجها:**
    - **المنصات المالية والبنكية (Fintech):** للرسوم البيانية المخصصة (Custom Charts/Graphs) لتتبع الأسهم والتحويلات.
    - **المواقع التسويقية ذات الانطباع البصري العالي (Landing Pages):** لبناء الخلفيات المتموجة (SVG Waves)، والأسهم التفاعلية.

### 3. عناصر إعادة الاستخدام (`<defs>`, `<symbol>`, `<use>`)

- **متى تقولين لنفسك: "سأبني نظام SVG Sprite (`symbol` + `use`)"؟**
    - عندما ترغبين في **حجم ملفات صغير جداً وأعلى أداء للشبكة (Maximum Performance)** في مشروع يحتوي على **أكثر من 30 - 50 أيقونة تتكرر في عشرات الصفحات**.
    - **مثال عملي:** متجر إلكتروني ضخم يحتوي على أيقونة "عربة التسوق" و"المفضلة" و"النجمة" في 100 صفحة منتج. بدلاً من تكرار أكواد `path` في كل صفحة وتضخيم حجم الـ HTML، تضعين الأيقونات في ملف واحد استاتيكي `sprite.svg` وتستدعينها بـ `<use href="sprite.svg#shopping-cart">`.
- **نوعية المشاريع التي تحتاج هذا الأسلوب (SVG Sprite Sheet):**
    - **المتاجر الإلكترونية الضخمة (E-commerce Platforms):** مثل مواقع مثل Amazon أو Jumia حيث كل ميجابايت وكل مللي ثانية في التحميل تعني مكسب أو خسارة مالية.
    - **تطبيقات الويب التقدمية (PWAs):** التي تعمل أوفلاين وتطلب تخزين الأيقونات في الـ Cache لمرة واحدة فقط.
    - **المشاريع التي لا تستخدم أطر عمل حديثة (Multi-Page Apps / Server-Side Rendered):** مثل المشاريع المبنية بـ Django، Laravel، أو WordPress.
- **متى لا تحتاجين أسلوب (`symbol` + `use`)؟**
    - **في مشاريع React / Next.js / Vue الصغيرة والمستقلة:** حيث يفضل استخدام مكتبات الأيقونات الحديثة المعتمدة على المكونات مثل **Lucide Icons** أو **Heroicons**، لأن كل أيقونة تُجلب كـ Component مستقل (`<ShoppingCartIcon/>`) ويقوم الإطار بعمل Tree-shaking لتضمين الأيقونات المستعملة فقط.

### خريطة القرار السريعة (Decision Checklist):

| نوع العنصر في SVG | القرار السريع للبدء في استخدامه |
| --- | --- |
| **`<rect>` / `<circle>`** | احتاجه لأي شكل هندسي بسيط، سريع، ويحتاج تغيير أبعاده أو لونه بالـ CSS فوراً. |
| **`<path>`** | احتاجه لأي رسمة، شعر، أو أيقونة قادمة من Figma، أو عند الحاجة لتحريك رسم الخيوط (Stroke Animations). |
| **`<symbol>` + `<use>`** | احتاجه لبناء نظام أيقونات موحد ومستقر ومخزن في الـ Cache لرفع أداء موقع ضخم متعدد الصفحات. |

دعيني أربط لك كل ما درسناه بالواقع.

---

# الحالة الأولى: موقع شركة عادي (Corporate Website)

مثل:

- شركة عقارات
- شركة برمجة
- مطعم
- عيادة

ستستخدم SVG في:

✅ Logo

بدلاً من PNG

لأنه يبقى واضحًا مهما كبرت الشاشة.

---

أيقونات الخدمات

```
✓ Web Development
✓ UI Design
✓ Mobile App
```

كلها غالبًا SVG.

وليس PNG.

---

# الحالة الثانية

لو أنتِ تعملين Dashboard

مثل:

- Admin Panel
- CRM
- ERP

هنا ستستخدمين SVG كثيرًا.

مثلاً:

```
📊 Charts
📈 Analytics
⬆ Arrow
⬇ Arrow
✔ Success
⚠ Warning
❌ Error
```

كلها SVG.

---

# الحالة الثالثة

لو تعملين Design System

مثلاً:

شركة لديها

```
200 Icon
```

هل ستكتبين

```
<imgsrc="edit.svg"><imgsrc="delete.svg"><imgsrc="save.svg">
```

لا.

ستستخدمين

```
<symbol>

+

<use>
```

مرة واحدة فقط.

ثم

```

```

[](data:image/svg+xml;utf8,%3Csvg%3E%0A%0A%3Cuse%20href%3D%22%23edit%22%3E%3C%2Fuse%3E%0A%0A%3C%2Fsvg%3E)

---

# الحالة الرابعة

لو تعملين Landing Page

مثلاً Hero Section

يوجد

Illustration

أو

Blob Shape

أو

Wave

كلها SVG.

وليس PNG.

---

# متى أستخدم rect ؟

مثلاً

Card Background

Button Shape

Skeleton Loader

Progress Bar

كلها Rect.

---

# متى أستخدم circle ؟

Avatar Placeholder

Notification Dot

Status

Online

Offline

Badge

Loading

---

# متى أستخدم ellipse ؟

نادراً.

يستخدم غالبًا في

Shadow

Glow

Decoration

---

# متى أستخدم line ؟

Chart

Divider

Timeline

Connection

---

# متى أستخدم polygon ؟

نجمة

Star Rating

Arrow

Triangle

Hexagon

---

# متى أستخدم polyline ؟

Chart

Graph

Sparkline

Timeline

---

# متى أستخدم path ؟

هنا أهم نقطة.

تقريبًا

كل Icon في العالم

هو

Path.

مثلاً

Heroicons

Lucide

Material

كلها عبارة عن

```
<pathd="...">
```

وليس

circle

ولا

rect

---

# طيب هل سأكتب Path ؟

لا.

أنتِ لا تكتبينه.

بل

Figma

↓

Export SVG

↓

Ready

---

# طيب SVG Styling ؟

---

## fill

كل Icon

تريدين تغيير لونه.

```
fill:red;
```

---

## stroke

لو عندك

Outline Icons

مثل

Lucide

ستستخدمين

stroke.

---

## stroke-width

تكبير سمك الخط.

مثلاً

الأيقونة رفيعة.

تريدينها Bold.

---

## opacity

تريدين

Disabled Icon.

---

# defs

هذا يبدأ يظهر عندما يكون عندك

SVG كبير.

مثلاً

Illustration

فيه

100 Shape.

بدلاً من تكرار نفس الشكل.

تخزنينه.

---

# symbol

هذا يظهر أكثر في

Design System.

مثلاً

شركة لديها

```
400 Icons
```

كلهم داخل

Sprite.

---

# use

كلما احتجت نفس الأيقونة.

بدلاً من كتابة

```
<path>

....</path>
```

مرة أخرى.

تكتب

```
<usehref="#icon"/>
```

---

# طيب في React ماذا يحدث؟

مثلاً

```
<EditIcon/>
```

هل تعتقدين أنه رسم الأيقونة؟

لا.

في النهاية داخله

```
<path/>
```

---

# في المشاريع الحقيقية

لو فتحنا مشروع مثل

Stripe

أو

GitHub

أو

Notion

سنجد:

```
svg

path

fill

stroke
```

في كل مكان.

لكن لن نجلس ونكتب

```
M

L

C

Q

A
```

يدويًا.

---

# طيب هل ممكن أعمل مشروع كامل بدون SVG؟

نعم.

إذا كنت تستخدمين

Lucide

مثلاً

```
<House/><User/><Settings/>
```

فأنت لا تكتبين SVG إطلاقًا.

لكن المكتبة نفسها مبنية بالكامل على SVG.

---

# بعد 4 سنوات Front-End

المطور غالبًا:

✅ يعرف ما هو SVG.

✅ يعرف الفرق بين PNG وSVG.

✅ يعرف fill وstroke.

✅ يعرف viewBox.

✅ يعرف أن كل Icon عبارة عن Path.

لكن

❌ لا يحفظ أوامر

```
M
L
Q
C
A
```

ولا يرسم SVG يدويًا.

---

# خلاصة ذهنية أريدك أن تحفظيها

بدلاً من حفظ العناصر، اربطيها بالمشروع:

| لو رأيت في المشروع... | فكر في... |
| --- | --- |
| شعار (Logo) | SVG |
| أيقونة (Icon) | SVG + `<path>` |
| رسم بياني (Chart) | SVG (`<line>`، `<polyline>`، `<path>`) |
| نجمة تقييم | `<polygon>` أو `<path>` |
| دائرة حالة (Online/Offline) | `<circle>` |
| بطاقة أو شريط تقدم | `<rect>` |
| مكتبة أيقونات أو Design System | `<symbol>` + `<use>` + `<defs>` |
| تغيير لون أيقونة | `fill` أو `stroke` |
| أيقونة حدود فقط (Outline Icon) | `stroke` |
| صورة فوتوغرافية | **لا تستخدم SVG**، استخدم WebP أو AVIF أو JPEG |

# الفصل التاسع

# HTML Canvas

# 9.1 Canvas Basics

---

# السؤال الاول

# What is the `<canvas>` element in HTML, and how do you draw on it?

## الإجابة

> The `<canvas>` element provides a drawable area in an HTML document. It does not contain graphics by itself. Instead, JavaScript is used to obtain a rendering context and draw shapes, text, images, or animations.
> 

---

## لماذا تهتم الشركات بهذا السؤال؟

لأن Canvas يُستخدم في التطبيقات التي تحتاج إلى الرسم الديناميكي، مثل:

- Drawing Applications
- Games
- Charts
- Image Editors
- Signature Pads

وفهم العلاقة بين `<canvas>` وJavaScript من أساسيات العمل به.

---

# ما هو Canvas؟

Canvas هو عنصر HTML يوفر **مساحة رسم فارغة**.

على عكس SVG، فإن Canvas لا يحتوي على عناصر رسومية مستقلة، بل يرسم مباشرة على لوحة (Canvas) باستخدام JavaScript.

---

# 1. `<canvas>`

---

## الإجابة

> The `<canvas>` element creates a drawing surface that can be controlled using JavaScript.
> 

---

## المثال

```
<canvasid="myCanvas"width="400"height="250"></canvas>
```

---

## ماذا يحدث؟

ينشئ مساحة رسم.

لكن...

لن يظهر أي رسم حتى تستخدم JavaScript.

---

# هل يحتوي Canvas على رسومات؟

❌ لا.

بدون JavaScript سيظهر كمساحة فارغة.

---

# 2. `width`

---

## الإجابة

> The `width` attribute defines the internal drawing width of the canvas.
> 

---

## المثال

```
<canvaswidth="500"height="300"></canvas>
```

---

عرض مساحة الرسم هو:

```
500px
```

---

# 3. `height`

---

## الإجابة

> The `height` attribute defines the internal drawing height of the canvas.
> 

---

ارتفاع مساحة الرسم:

```
300px
```

---

# ملاحظة مهمة

هذه القيم تحدد **حجم الرسم الداخلي**.

وليست مجرد حجم العنصر في الصفحة.

---

# لماذا لا نستخدم CSS لتحديد الحجم؟

يمكن استخدام CSS لتغيير الحجم الظاهر، لكن هذا قد يؤدي إلى تمدد أو تشويه الرسم.

الأفضل غالبًا تحديد:

```
width
height
```

داخل عنصر `<canvas>` نفسه، ثم استخدام CSS فقط عند الحاجة مع مراعاة إعادة ضبط حجم الرسم.

---

# 4. الحصول على Context

---

## الإجابة

> Before drawing on a canvas, you must obtain a rendering context using the `getContext()` method.
> 

---

## الصيغة

```
constcanvas=document.getElementById("myCanvas");constctx=canvas.getContext("2d");
```

---

## ماذا يحدث؟

السطر الأول يحصل على عنصر:

```
<canvas>
```

والسطر الثاني يحصل على:

```
2D Rendering Context
```

وهو الكائن الذي يحتوي على جميع أوامر الرسم.

---

## لماذا يسمى Context؟

لأنه يمثل البيئة التي يتم من خلالها تنفيذ جميع عمليات الرسم.

بدون Context لا يمكن رسم أي شيء.

---

# 5. رسم أول شكل

---

بعد الحصول على Context يمكن استخدام إحدى دوال الرسم.

أبسط مثال هو رسم مستطيل ممتلئ.

```
<canvasid="myCanvas"width="300"height="200"></canvas><script>constcanvas=document.getElementById("myCanvas");constctx=canvas.getContext("2d");ctx.fillStyle="royalblue";ctx.fillRect(40,40,150,80);</script>
```

---

## ماذا يحدث؟

- يحصل على عنصر Canvas.
- يحصل على Context.
- يحدد لون الرسم.
- يرسم مستطيلًا أزرق.

---

# ماذا تعني أرقام `fillRect()`؟

```
ctx.fillRect(x,y,width,height);
```

| Parameter | Description |
| --- | --- |
| `x` | موضع البداية أفقيًا |
| `y` | موضع البداية رأسيًا |
| `width` | عرض المستطيل |
| `height` | ارتفاع المستطيل |

---

# دورة العمل مع Canvas

```
Create Canvas
      ↓
Get Canvas Element
      ↓
Get 2D Context
      ↓
Draw Shapes
```

---

# مقارنة بين HTML وCanvas

| HTML Element | Canvas |
| --- | --- |
| يعرض محتوى مباشرة | يحتاج JavaScript للرسم |
| عناصر داخل DOM | الرسم عبارة عن بكسلات |
| مناسب للمحتوى | مناسب للرسم الديناميكي |

---

# أشهر أسئلة المقابلات

### What is the purpose of the `<canvas>` element?

> It provides a drawable area that can be controlled using JavaScript.
> 

---

### Can you draw on a canvas using HTML only?

❌ لا.

يجب استخدام JavaScript.

---

### What does `getContext("2d")` return?

> It returns the 2D rendering context used to draw on the canvas.
> 

---

### What happens if you omit `getContext()`?

> You cannot draw anything because no rendering context is available.
> 

---

### What is the default canvas size?

إذا لم تحدد أبعادًا، فإن الحجم الافتراضي هو:

- Width: **300px**
- Height: **150px**

---

# Best Practices

- أعطِ عنصر `<canvas>` معرفًا (`id`) واضحًا للوصول إليه بسهولة.
- حدد `width` و`height` كخصائص للعنصر، وليس فقط عبر CSS.
- احصل على الـ Context مرة واحدة وأعد استخدامه.
- استخدم Canvas عندما تحتاج إلى رسم أو تحديث الرسومات باستمرار.

---

# Senior Notes

هناك عدة نقاط يقع فيها كثير من المطورين:

### 1. Canvas لا يحتوي على عناصر

عندما ترسم مستطيلًا داخل Canvas، فإنه **لا يصبح عنصر HTML**.

لا يمكنك لاحقًا كتابة:

```
document.querySelector("rect");
```

لأنه لا يوجد عنصر `<rect>` داخل الـ DOM كما في SVG.

---

### 2. الرسم دائم حتى تعيد رسمه

بعد رسم شكل، يبقى على اللوحة حتى تقوم بمسحه أو إعادة الرسم يدويًا باستخدام JavaScript.

---

### 3. Context هو نقطة البداية دائمًا

تقريبًا كل تطبيق Canvas يبدأ بهذه الأسطر:

```
constcanvas=document.getElementById("myCanvas");constctx=canvas.getContext("2d");
```

لذلك ستراها في معظم المشاريع والمكتبات التي تعتمد على Canvas.

---

# 9.1 أساسيات الـ Canvas في HTML (`<canvas>` Basics)

### مثال الكود:

HTML

```
<!DOCTYPE html>
<html lang="ar">
<head>
  <meta charset="UTF-8">
  <title>Canvas Basics Example</title>
  <style>
    canvas {
      border: 2px solid #333;
      background-color: #f9f9f9;
    }</style>
</head>
<body>

  <!-- 1. تعريف عنصر الـ Canvas بأبعاد الإحداثيات (Width & Height Attributes) -->
  <canvas id="myCanvas" width="400" height="200">
    متصفحك لا يدعم عنصر Canvas.
  </canvas>

  <script>
    // 2. الوصول إلى عنصر الـ Canvas
    const canvas = document.getElementById('myCanvas');

    // 3. الحصول على سياق الرسم ثنائي الأبعاد (2D Rendering Context)
    const ctx = canvas.getContext('2d');

    // 4. رسم مستطيل ملون (Filled Rectangle)
    ctx.fillStyle = '#3b82f6'; // تحديد لون التعبئة
    ctx.fillRect(50, 50, 150, 100); // رسم مستطيل: x=50, y=50, width=150, height=100

    // 5. رسم حدود مستطيل فقط (Stroked Rectangle)
    ctx.strokeStyle = '#ef4444'; // تحديد لون الحدود
    ctx.lineWidth = 4; // سمك الخط
    ctx.strokeRect(230, 50, 120, 100); // x=230, y=50, width=120, height=100</script>

</body>
</html>
```

### السؤال:

**ما هو عنصر `<canvas>` في HTML، وكيف تقوم بالرسم عليه؟**

*(بالإنجليزي: What is the `<canvas>` element in HTML, and how do you draw on it?)*

### الإجابة النموذجية للمقابلة (Interview Answer):

> **عنصر `<canvas>` هو مساحة رسومية بيضاء (Bitmap Container) يتم الرسم عليها ديناميكيًا باستخدام JavaScript حصراً:**
> 
> - **طبيعة العنصر:** يمثل مساحة فارغة من النقاط (Pixels). العنصر بمفرده لا يحتوي على أي إمكانيات رسم بدون كود JavaScript.
> - **آلية الرسم:** يتم الحصول على سياق الرسم (Rendering Context) عبر الدالة `canvas.getContext('2d')` (أو `'webgl'` للرسومات ثلاثية الأبعاد)، ثم استخدام واجهات برمجة التطبيقات (APIs) الخاصة به لرسم الأشكال، النصوص، الصور، والرسوم المتحركة برمجياً عبر نظام إحداثيات (Grid Coordinate System) يبدأ من الزاوية العليا اليسرى `(0,0)`.

### الشرح بالتفصيل:

الـ Canvas هو أحد أهم الابتكارات في HTML5، حيث نقل الويب من مجرد نصوص وصور استاتيكية إلى بيئة تفاعلية قادرة على تشغيل الألعاب والرسوم البيانية المعقدة مباشرة في المتصفح دون الحاجة لإضافات مثل Flash.

تعال نفصص المفهوم كاملاً:

#### 1. نظام الإحداثيات (Coordinate System)

يعتمد الـ Canvas على شبكة إحداثيات ثنائية الأبعاد:

- **النقطة الأصلية `(0, 0)`:** تقع في **الزاوية العليا اليسرى** للوحة.
- **محور `X`:** يزداد أفقيًا متطرقاً نحو اليمين.
- **محور `Y`:** يزداد رأسيًا متطرقاً نحو الأسفل.

#### 2. خطوات الرسم الأربعة الأساسية

للرسم على الـ Canvas، يجب دائمًا اتباع هذا التسلسل:

1. **إضافة العنصر للـ DOM:** تحديد الأبعاد عبر خاصيتي `width` و `height` في الـ HTML مباشرة وليس عبر CSS (سنفصل السبب في نقطة الفخ أدناه).
2. **الوصول للعنصر بـ JavaScript:** اختيار العنصر بـ `document.getElementById`.
3. **استخراج السياق (Context):** طلب الـ `2d` context الذي يوفر أدوات الرسم (`fillRect`, `beginPath`, `arc`, إلخ).
4. **تطبيق التنسيق ثم الرسم:** تحديد الألوان والأحجام (`fillStyle`, `strokeStyle`) ثم استدعاء أوامر الرسم.

#### 3. فخ المقابلة الشهير: الفارق بين خصائص أبعاد Canvas وتنسيقات CSS

غالبًا ما يسأل مسؤول المقابلة: **"ما الفرق بين تحديد `width` و `height` على عنصر `<canvas>` مباشرة وبين تحديدها عبر CSS؟"**

**الإجابة الحاسمة:**

- **خصائص الـ HTML (`width` & `height` attributes):** تحدد **عدد النقاط الحقيقية (Drawing Buffer/Resolution)** داخل اللوحة. القيمة الافتراضية إذا لم تحددها هي `300px` عرض و `150px` ارتفاع.
- **تنسيقات الـ CSS (`width` & `height` in CSS):** تحدد **حجم العرض الفعلي للعنصر على الشاشة (Display Size)**.
- **المشكلة إذا استخدمت CSS فقط:** إذا غيرت الحجم بـ CSS دون تعديل خصائص الـ HTML، سيقوم المتصفح بتمديد (Stretch) الصورة تماماً مثل تمديد صورة صغيرة بكسلية، مما يسبب **تضبب الرسمة (Blurry Canvas Issue)** وفساد الدقة.

#### 4. متى نستخدم Canvas مقارنة بـ SVG؟ (Canvas vs SVG)

| **وجه المقارنة** | **Canvas** | **SVG** |
| --- | --- | --- |
| **طبيعة الرسم** | رسومات بكسلية (Raster/Bitmap). | رسومات متجهة (Vector). |
| **الأداء مع الأجسام الكثيرة** | **أداء ممتاز جداً** مع ملايين العناصر لأن المتصفح لا يحتفظ بها في الـ DOM. | يقل الأداء مع كثرة العناصر لأن كل شكل عبارة عن عنصر DOM مستقل. |
| **التحكم بالتفاعل (Events)** | التفاعل معقد، يتطلب حساب إحداثيات النقرة بالماوس يدوياً. | سهل جداً، يمكن إضافة `addEventListener` لكل شكل كعنصر DOM عريض. |
| **أفضل استخدام** | الألعاب 2D/3D، معالجة الصور، والرسوم البيانية الكثيرة جداً. | الأيقونات، الواجهات المتجاوبة، الرسوم البيانية البسيطة والتفاعلية. |

#### الكلمات المفتاحية للحفظ (Keywords):

- **Bitmap Canvas:** لوحة رسومات بكسلية.
- **Rendering Context (`getContext('2d')`):** محرك وواجهة برمجة أرقام وأدوات الرسم.
- **Coordinate System `(0, 0)`:** شبكة الإحداثيات التي تبدأ من الأعلى لليسار.
- **Drawing Buffer vs CSS Size:** الفرق بين دقة الرسم وحجم العرض البصري.

#### جملتك النموذجية في المقابلة:

> **"The `<canvas>` element provides a pixel-based drawing surface in HTML5 that relies on JavaScript for rendering. To draw on it, we retrieve its rendering context via `canvas.getContext('2d')`, which gives us access to a rich set of drawing APIs. Canvas operates on a coordinate system with `(0,0)` at the top-left. Crucially, we must define its `width` and `height` attributes directly on the HTML element to establish the resolution buffer, rather than scaling it with CSS which would stretch the bitmap pixels**
> 

# 9.2 Drawing Basics

---

# السؤال الثاني

# What are the most common Canvas drawing methods, and how are they used?

## الإجابة

> The Canvas 2D API provides several drawing methods for creating shapes and paths. The most commonly used methods include `fillRect()`, `strokeRect()`, `clearRect()`, `beginPath()`, `moveTo()`, `lineTo()`, `arc()`, `stroke()`, and `fill()`.
> 

---

## لماذا تهتم الشركات بهذا السؤال؟

لأن هذه الدوال تمثل أساس الرسم باستخدام Canvas، وتُستخدم في:

- Whiteboard Apps
- Drawing Tools
- Games
- Charts
- Image Editors

---

# أولًا: Drawing Rectangles

---

## `fillRect()`

### الإجابة

> Draws a filled rectangle.
> 

---

### الصيغة

```
ctx.fillRect(x,y,width,height);
```

---

### المثال

```
ctx.fillStyle="royalblue";ctx.fillRect(20,20,120,80);
```

---

### ماذا يحدث؟

يرسم مستطيلًا ممتلئًا باللون المحدد.

---

## `strokeRect()`

### الإجابة

> Draws the outline of a rectangle.
> 

---

### المثال

```
ctx.strokeStyle="black";ctx.lineWidth=3;ctx.strokeRect(20,20,120,80);
```

---

### ماذا يحدث؟

يرسم إطارًا فقط دون تعبئة.

---

## `clearRect()`

### الإجابة

> Clears a rectangular area of the canvas.
> 

---

### المثال

```
ctx.clearRect(20,20,120,80);
```

---

### ماذا يحدث؟

يمسح المنطقة المحددة ويعيدها إلى حالتها الفارغة.

---

# ثانيًا: Drawing Paths

---

## `beginPath()`

### الإجابة

> Starts a new drawing path.
> 

---

### المثال

```
ctx.beginPath();
```

---

### لماذا نستخدمه؟

لفصل المسار الجديد عن المسارات السابقة.

---

## `moveTo()`

### الإجابة

> Moves the drawing cursor to a starting point without drawing.
> 

---

### المثال

```
ctx.moveTo(20,20);
```

---

## `lineTo()`

### الإجابة

> Draws a straight line from the current point to a new point.
> 

---

### المثال

```
ctx.beginPath();ctx.moveTo(20,20);ctx.lineTo(180,100);ctx.stroke();
```

---

### ماذا يحدث؟

يرسم خطًا مستقيمًا بين النقطتين.

---

## `arc()`

### الإجابة

> Draws a circle or an arc.
> 

---

### الصيغة

```
ctx.arc(x,y,radius,startAngle,endAngle);
```

---

### المثال

```
ctx.beginPath();ctx.arc(100,100,50,0,Math.PI*2
);ctx.stroke();
```

---

### ماذا يحدث؟

يرسم دائرة كاملة.

---

# ثالثًا: Rendering the Path

---

## `stroke()`

### الإجابة

> Draws the outline of the current path.
> 

---

### المثال

```
ctx.stroke();
```

---

## `fill()`

### الإجابة

> Fills the current path with the current fill color.
> 

---

### المثال

```
ctx.fillStyle="orange";ctx.fill();
```

---

# دورة رسم Path

```
beginPath()
      ↓
moveTo()
      ↓
lineTo()
      ↓
arc() (optional)
      ↓
stroke() أو fill()
```

---

# مقارنة بين الدوال

| Method | Purpose |
| --- | --- |
| `fillRect()` | رسم مستطيل ممتلئ |
| `strokeRect()` | رسم إطار مستطيل |
| `clearRect()` | مسح جزء من Canvas |
| `beginPath()` | بدء مسار جديد |
| `moveTo()` | تحديد نقطة البداية |
| `lineTo()` | رسم خط مستقيم |
| `arc()` | رسم دائرة أو قوس |
| `stroke()` | رسم حدود المسار |
| `fill()` | تعبئة المسار |

---

# أشهر أسئلة المقابلات

### Which method draws a filled rectangle?

```
ctx.fillRect()
```

---

### Which method draws only the rectangle outline?

```
ctx.strokeRect()
```

---

### Which method clears part of the canvas?

```
ctx.clearRect()
```

---

### Why should you call `beginPath()`?

> To start a new path and prevent it from connecting with previously drawn paths.
> 

---

### What is the difference between `stroke()` and `fill()`?

> `stroke()` draws the outline of the current path, while `fill()` fills the inside of the current path.
> 

---

### Which method draws a circle?

```
ctx.arc()
```

---

# Best Practices

- استخدم `beginPath()` قبل رسم مسار جديد.
- استخدم `stroke()` عند الحاجة إلى حدود فقط.
- استخدم `fill()` عند الحاجة إلى تعبئة الشكل.
- استخدم `clearRect()` عند تحديث الرسومات أو إنشاء رسوم متحركة.
- حافظ على ترتيب الرسم: إنشاء المسار ثم رسمه أو تعبئته.

---

# Senior Notes

هناك عدة نقاط يقع فيها كثير من المطورين:

### 1. `beginPath()` مهم جدًا

إذا لم تبدأ مسارًا جديدًا، فقد يعتبر Canvas أن الخطوط الجديدة امتداد للمسار السابق، مما يؤدي إلى نتائج غير متوقعة.

---

### 2. `stroke()` و`fill()` لا يرسمان شيئًا بمفردهما

هما يطبقان على **المسار الحالي** الذي أنشأته باستخدام دوال مثل `moveTo()` و`lineTo()` و`arc()`.

---

### 3. `clearRect()` لا يحذف عناصر

Canvas لا يحتوي على عناصر مستقلة، لذلك `clearRect()` يمسح بكسلات من اللوحة، وليس عناصر كما يحدث في DOM.

# 9.2 الطرق الأساسية للرسم في Canvas (`Canvas Drawing Methods`)

### مثال الكود:

HTML

```
<!DOCTYPE html>
<html lang="ar">
<head>
  <meta charset="UTF-8">
  <title>Canvas Drawing Methods Example</title>
  <style>
    canvas {
      border: 2px solid #1e293b;
      background-color: #ffffff;
    }</style>
</head>
<body>

  <canvas id="shapesCanvas" width="500" height="300">
    متصفحك لا يدعم Canvas.
  </canvas>

  <script>
    const canvas = document.getElementById('shapesCanvas');
    const ctx = canvas.getContext('2d');

    // 1. رسم المستطيلات المباشرة (Rectangles)
    ctx.fillStyle = '#10b981'; // لون التعبئة أخضر
    ctx.fillRect(20, 20, 100, 80); // مستطيل ممتلئ

    ctx.strokeStyle = '#6366f1'; // لون الحدود بنفسجي
    ctx.lineWidth = 3;
    ctx.strokeRect(140, 20, 100, 80); // مستطيل حدود فقط

    ctx.clearRect(40, 40, 30, 30); // تفريغ جزء من المستطيل الأول

    // 2. رسم مسار مخصص (Custom Path: المثلث)
    ctx.beginPath(); // بدء مسار جديد
    ctx.moveTo(300, 20);  // نقل نقطة الرسم الابتدائية
    ctx.lineTo(360, 100); // رسم خط للنقطة الثانية
    ctx.lineTo(240, 100); // رسم خط للنقطة الثالثة
    ctx.closePath();      // إغلاق المسار تلقائياً بالعودة لنقطة البداية
    ctx.fillStyle = '#f59e0b';
    ctx.fill();           // تعبئة المثلث

    // 3. رسم الأقواس والدوائر (Arcs & Circles)
    ctx.beginPath();
    // arc(x, y, radius, startAngle, endAngle, counterclockwise)
    ctx.arc(100, 200, 40, 0, Math.PI * 2); // دائرة كاملة (2 * PI)
    ctx.fillStyle = '#ef4444';
    ctx.fill();

    ctx.beginPath();
    ctx.arc(240, 200, 40, 0, Math.PI); // نصف دائرة (من 0 إلى PI)
    ctx.strokeStyle = '#0f172a';
    ctx.lineWidth = 5;
    ctx.stroke();

    // 4. رسم النصوص (Text)
    ctx.font = 'bold 20px Arial';
    ctx.fillStyle = '#0f172a';
    ctx.fillText('HTML Canvas', 330, 180); // نص ممتلئ

    ctx.strokeStyle = '#3b82f6';
    ctx.lineWidth = 1;
    ctx.strokeText('Interactive', 330, 210); // نص حدود فقط</script>

</body>
</html>
```

### السؤال:

**ما هي طرق الرسم الأكثر شيوعًا في Canvas، وكيف تُستخدم؟**

*(بالإنجليزي: What are the most common Canvas drawing methods, and how are they used?)*

### الإجابة النموذجية للمقابلة (Interview Answer):

> **تتوزع أكثر طرق الرسم شيوعًا في Canvas API إلى 4 فئات رئيسية:**
> 
> 1. **المستطيلات المباشرة (Direct Rectangles):** مثل `fillRect()`, `strokeRect()`, و `clearRect()` وهي الأشكال الوحيدة الجاهزة للرسم المباشر بدون مسارات.
> 2. **المسارات والخطوط (Paths & Lines):** تُبنى بالدوال `beginPath()`, `moveTo()`, `lineTo()`, و `closePath()` متبوعة بـ `fill()` للتعبئة أو `stroke()` لرسم الحدود.
> 3. **الأقواس والدوائر (Arcs & Circles):** تُبنى بواسطة `arc(x, y, radius, startAngle, endAngle)` مع الاعتماد على الراديان (Radians).
> 4. **النصوص والصور (Text & Images):** مثل `fillText()`, `strokeText()` للنصوص، و `drawImage()` لرسم وإدراج الصور على اللوحة.

### الشرح بالتفصيل:

توفر الـ Canvas 2D Context مجموعة غنية جداً من الـ APIs للرسم البرمجي. لا تحتوي Canvas على عناصر جاهزة للـ "دائرة" أو "المثلث" كـ HTML Elements، بل تعتمد على أدوات بناء المسارات برمجياً.

تعال نفصل هذه الطرق حسب الاستخدام:

#### 1. طرق رسم المستطيلات (Rectangle Methods)

تعتبر المستطيلات هي الأشكال البدائية الوحيدة التي تمتلك دالّة رسم مباشرة دون الحاجة للبدء بمسار (`beginPath`):

- **`fillRect(x, y, width, height)`:** ترسم مستطيلًا ممتلئًا باللون المحجوز في `ctx.fillStyle`.
- **`strokeRect(x, y, width, height)`:** ترسم حدود مستطيل بالسمك واللون المحجوزين في `ctx.lineWidth` و `ctx.strokeStyle`.
- **`clearRect(x, y, width, height)`:** تمسح محتوى المساحة المحددة وتجعلها شفافة تمامًا (تُستخدم بكثرة في مسح اللوحة عند عمل Animation).

#### 2. طرق رسم المسارات المخصصة (Path Methods)

لأي شكل هندسي آخر (مثلث، مضلع، خط متعرج)، نستخدم دورة حياة المسار (Path Life Cycle):

- **`beginPath()`:** تعلن للمتصفح بدء مسار رسم جديد وفصل الأشكال الحالية عن السابقة.
- **`moveTo(x, y)`:** تحرك "قلم الرسم" إلى نقطة البداية دون رسم خط.
- **`lineTo(x, y)`:** ترسم خطًا وهميًا من النقطة الحالية إلى النقطة `(x, y)`.
- **`closePath()`:** ترسم خطًا مستقيمًا تلقائيًا ينتهي عند نقطة البداية الأولى لإغلاق الشكل.
- **`fill()` / `stroke()`:** أمر التنفيذ المالي أو البصري؛ `fill()` لتعبئة داخل المسار باللون، و `stroke()` لتلوين خط الحدود.

#### 3. طرق رسم الأقواس والدوائر (Arc Methods)

- **الدالة:** `arc(x, y, radius, startAngle, endAngle, counterclockwise)`
- **كيفية تحديد الزوايا:** لا تعتمد Canvas على الدرجات (Degrees) بل على **الراديان (Radians)**.
    - المعاملة الحسابية: `Radians = (Math.PI / 180) * Degrees`.
    - **الدائرة الكاملة:** تبدأ من angle `0` وتنتهي عند `Math.PI * 2`.
    - **نصف الدائرة:** تبدأ من `0` وتنتهي عند `Math.PI`.

#### 4. طرق رسم النصوص والصور (Text & Image Methods)

- **`fillText(text, x, y)`:** ترسم نصًا ممتلئًا. يتم التحكم بالحجم والخط عبر `ctx.font = '20px Arial'`.
- **`strokeText(text, x, y)`:** ترسم حروف النص كحدود فرغاء فقط.
- **`drawImage(image, x, y, width, height)`:** تأخذ عنصر صورة HTML (`<img>`) أو صورة محملة برمجياً وترسمها بكسلياً داخل اللوحة، مع إمكانية قصها وتحجيمها.

#### 5. لمحة ذكاء للـ UI Engineer (سؤال الفخ للمقابلة)

الـ Interviewer ممكن يسألك: **"ماذا يحدث إذا نسيت كتابة `beginPath()` أثناء رسم أكثر من شكل في Canvas؟"**

**الإجابة الذكية:**

> "إذا لم نستخدم `beginPath()` قبل رسم شكل جديد، سيحتفظ المتصفح بالمسارات القديمة داخل الـ Drawing Buffer. وعند استدعاء `stroke()` أو `fill()` لاحقاً، سيقوم المتصفح بإعادة رسم وتلوين الأشكال القديمة مرة أخرى مع الشكل الجديد، مما يسبب مشكلة في الأداء وتداخل التنسيقات والألوان."
> 

#### الكلمات المفتاحية للحفظ (Keywords):

- **Path Life Cycle (`beginPath`, `closePath`):** دورة بناء المسارات البرمجية.
- **Stroke vs Fill:** الفرق بين التعبئة الداخلية وتلوين الحواف.
- **Radians Conversion:** تحويل الزوايا إلى راديان باستخدام `Math.PI`.
- **ClearRect:** أداة المسح الأساسية للتنظيف والإنيميشن.

#### جملتك النموذجية في المقابلة:

> **"The Canvas API provides direct methods for rectangles like `fillRect` and `clearRect`, but most other shapes are built using paths. Path creation relies on `beginPath()`, moving the virtual pen with `moveTo()`, defining segments using `lineTo()` or `arc()`, and finally executing the render with `fill()` or `stroke()`. Arcs require angles in radians rather than degrees (`Math.PI * 2` for a full circle). For rendering text and media, we use `fillText()` and `drawImage()`. Managing paths correctly with `beginPath()` is essential to prevent unintended re-renders of older shapes**
> 

# 9.3 Canvas vs SVG

---

# السؤال الثالث

# What is the difference between Canvas and SVG, and when should you choose each one?

## الإجابة

> Canvas and SVG are both used to display graphics in web applications, but they work in different ways. Canvas is bitmap-based and draws graphics as pixels, while SVG is vector-based and represents graphics as scalable DOM elements.
> 

---

## لماذا تهتم الشركات بهذا السؤال؟

لأن اختيار التقنية المناسبة يؤثر على:

- Performance
- Scalability
- Accessibility
- Interactivity
- Maintainability

وفي كثير من المشاريع، يكون القرار بين استخدام **Canvas** أو **SVG** قرارًا معماريًا (Architectural Decision).

---

# أولًا: كيف يعمل SVG؟

SVG ينشئ عناصر حقيقية داخل الـ DOM.

مثال:

```

```

[](data:image/svg+xml;utf8,%3Csvg%3E%0A%0A%20%20%20%20%3Ccircle%20cx%3D%2250%22%20cy%3D%2250%22%20r%3D%2230%22%3E%3C%2Fcircle%3E%0A%0A%3C%2Fsvg%3E)

المتصفح يعرف أن هناك عنصرًا اسمه:

```
circle
```

ويمكنك:

- تغييره بـ CSS.
- إضافة Event Listener.
- الوصول إليه بـ JavaScript.

---

# كيف يعمل Canvas؟

Canvas لا ينشئ عناصر.

هو عبارة عن لوحة رسم.

مثال:

```
ctx.arc(...);ctx.fill();
```

بعد تنفيذ الرسم:

لا يوجد عنصر:

```
circle
```

داخل الـ DOM.

بل مجرد بكسلات.

---

# الفرق الأساسي

```
SVG
↓

DOM Elements

↓

Each Shape Exists
```

---

```
Canvas
↓

Pixels

↓

One Drawing Surface
```

---

# مقارنة شاملة

| Feature | SVG | Canvas |
| --- | --- | --- |
| نوع الرسومات | Vector | Bitmap |
| قابل للتكبير دون فقدان الجودة | ✅ نعم | ❌ لا |
| يعتمد على DOM | ✅ نعم | ❌ لا |
| يمكن استهداف كل عنصر بـ CSS | ✅ نعم | ❌ لا |
| يدعم الأحداث لكل عنصر | ✅ نعم | ❌ لا (تحتاج لتنفيذها يدويًا) |
| مناسب للرسومات الثابتة | ✅ نعم | ⚠️ ممكن لكن ليس الأفضل |
| مناسب للرسومات المتغيرة باستمرار | ❌ أقل كفاءة | ✅ نعم |
| مناسب للأيقونات والشعارات | ✅ ممتاز | ❌ غير مناسب |
| مناسب للألعاب والرسم الحر | ❌ | ✅ ممتاز |

---

# متى تستخدم SVG؟

استخدم SVG عندما تكون الرسومات:

- Icons
- Logos
- UI Illustrations
- Flowcharts
- Diagrams
- Maps
- Buttons
- Design Systems

---

## مثال

موقع شركة يحتوي على:

- Logo
- أيقونات الخدمات
- أسهم التنقل

كلها:

```
SVG
```

---

# متى تستخدم Canvas؟

استخدم Canvas عندما تحتاج إلى:

- Games
- Drawing Applications
- Whiteboards
- Image Editors
- Live Charts
- Data Visualization
- Signature Pads

---

## مثال

لوحة رسم مثل:

```
Paint
```

ستستخدم:

```
Canvas
```

وليس SVG.

---

# مثال من المشاريع الحقيقية

## موقع متجر إلكتروني

ستجد:

- Logo → SVG
- Shopping Cart Icon → SVG
- Search Icon → SVG

---

## لعبة Snake

ستستخدم:

Canvas.

لأن الشاشة يعاد رسمها عشرات المرات في الثانية.

---

## Dashboard مالي

إذا كان يحتوي على:

- أيقونات
- أزرار
- مؤشرات ثابتة

فاستخدم SVG.

أما إذا كان يحتوي على:

- رسم بياني لحظي يتحدث كل جزء من الثانية

فقد يكون Canvas هو الخيار الأنسب.

---

# المزايا والعيوب

## SVG

### المزايا

- لا يفقد الجودة عند التكبير.
- كل عنصر يمكن التحكم به.
- سهل التنسيق باستخدام CSS.
- مناسب لمحركات البحث وإمكانية الوصول.
- ممتاز للأيقونات والشعارات.

### العيوب

- الأداء قد يتأثر عند وجود آلاف العناصر.
- أقل كفاءة في الرسوم التي يعاد رسمها باستمرار.

---

## Canvas

### المزايا

- سريع في إعادة الرسم.
- مناسب للألعاب والرسوم المتحركة.
- جيد لمعالجة الصور والرسم الحر.
- يتعامل بكفاءة مع عدد كبير من العمليات الرسومية.

### العيوب

- لا يحتوي على عناصر داخل DOM.
- لا يمكن تنسيق جزء معين باستخدام CSS.
- دعم Accessibility محدود ويحتاج إلى حلول إضافية.
- عند تغيير الرسم غالبًا تحتاج إلى إعادة رسم المشهد بالكامل.

---

# أشهر أسئلة المقابلات

### What is the main difference between Canvas and SVG?

> SVG is vector-based and DOM-based, while Canvas is bitmap-based and pixel-based.
> 

---

### Which one is better for icons?

✅ SVG.

---

### Which one is better for games?

✅ Canvas.

---

### Which one scales without losing quality?

✅ SVG.

---

### Which one provides better CSS styling support?

✅ SVG.

---

### Which one is generally better for animations involving thousands of moving objects?

✅ Canvas.

---

### Can you attach an event listener directly to a shape?

- SVG → ✅ Yes.
- Canvas → ❌ No, not directly.

---

# Best Practices

- استخدم SVG للأيقونات، الشعارات، والرسومات الثابتة.
- استخدم Canvas للتطبيقات التي تعتمد على الرسم المستمر أو التحديث المتكرر.
- لا تستخدم Canvas فقط لأنه "أسرع"، بل لأن طبيعة المشروع تحتاج إليه.
- إذا كان العنصر يحتاج إلى تفاعل مباشر أو تنسيق عبر CSS، فكر في SVG أولًا.

---

# Senior Notes

هناك عدة نقاط يقع فيها كثير من المطورين:

### 1. لا تسأل: أيهما أفضل؟

السؤال الصحيح هو:

> **أيهما أنسب لهذا المشروع؟**
> 

لا توجد تقنية أفضل بشكل مطلق.

---

### 2. معظم مواقع الويب تستخدم SVG أكثر

في تطبيقات Front-End التقليدية مثل:

- React
- Next.js
- Angular
- Vue

ستتعامل مع SVG أكثر بكثير من Canvas.

---

### 3. Canvas لا يعني دائمًا أداءً أفضل

Canvas يتفوق عندما تكون لديك **عمليات رسم كثيرة ومتكررة**، مثل الألعاب أو الرسوم المتحركة المعقدة. أما إذا كنت تعرض بضعة أيقونات أو رسومات بسيطة، فإن SVG يكون غالبًا الخيار الأسهل والأوضح.

---

# طريقة التفكير في المشاريع (Decision Tree)

```
هل الرسومات عبارة عن أيقونات أو شعارات أو عناصر واجهة؟
            │
            ├── نعم → استخدم SVG
            │
            └── لا
                 │
                 ▼
هل يتم إعادة الرسم عشرات أو مئات المرات في الثانية؟
                 │
                 ├── نعم → استخدم Canvas
                 │
                 └── لا
                      │
                      ▼
هل تحتاج إلى التحكم بكل عنصر عبر CSS أو JavaScript؟
                      │
                      ├── نعم → SVG
                      │
                      └── لا → Canvas
```

**9.3 المقارنة بين الـ Canvas والـ SVG (`Canvas vs SVG`)
جدول المقارنة المباشر:وجه المقارنةHTML CanvasSVG (Scalable Vector Graphics)طبيعة الرسم (Type)رسومات بكسلية (Raster / Bitmap):** يعتمد على النقاط المحددة بالبكسل.**رسومات متجهة (Vector):** يعتمد على المعادلات الرياضية والأشكال الهندسية.**نموذج كائن المستند (DOM)لا يوجد (Immediate Mode):** يرسم على اللوحة فوراً وينسى العناصر؛ لا تظهر الأشكال في الـ DOM.**موجود (Retained Mode):** كل شكل هو عنصر DOM مستقل (`<rect>`, `<circle>`) يمكن الوصول إليه عبر JS/CSS.**الدقة والتكبير (Scalability)**تفقد دقتها وتصبح مكسرة (Pixelated) عند التكبير إذا لم تُعد كتابة الأبعاد.قابلة للتكبير والتصغير إلى اللانهائية **دون أي فقدان للجودة**.**الأداء مع الكائنات الكثيرةأداء ممتاز جداً:** يتعامل مع آلاف إلى ملايين الأجسام في وقت واحد دون إرهاق الـ DOM.**يقل الأداء:** كثرة عناصر الـ DOM (أكثر من بضعة آلاف) تسبب بطءاً واضحاً ومتصفحاً ثقيلاً.**حجم مساحة الرسم (Screen Size)**يقل الأداء مع الشاشات الضخمة جداً (لأن عدد البكسلات التي يجب تحديثها يزيد).يتأثر بحجم وتعقيد الرسمة وليس بحجم الشاشة نفسه.**إمكانية التفاعل (Event Handling)**معقدة؛ يجب حساب إحداثيات نقرة الماوس ($x, y$) يدوياً لمعرفة الشكل المنقور عليه.سهلة جداً؛ يمكن إضافة `addEventListener` أو حوادث `hover` بـ CSS لكل عنصر مباشرة.**التنسيق (Styling)**يتم بالكامل عن طريق JavaScript APIs.يتم باستخدام CSS و HTML Presentation Attributes (`fill`, `stroke`).**إمكانية الوصول والـ SEO**ضعيفة جداً (محتواها عبارة عن محتوى بكسلي غير مفهوم للمحركات).ممتازة جداً (نصوص وأشكال قابلة للقراءة والبحث عبر `title` و `aria`).
**السؤال:**
**ما هو الفرق بين Canvas و SVG، ومتى يجب عليك اختيار كل منهما؟**
*(بالإنجليزي: What is the difference between Canvas and SVG, and when should you choose each one?)*
**الإجابة النموذجية للمقابلة (Interview Answer):الفرق الجوهري يكمن في طريقة المعالجة والـ DOM:**
• **SVG يعتمد على Retained Mode (Vector):** كل جزء هو عنصر DOM مستقل يتيح التفاعل بـ CSS/JS ودقة عالية لا تتأثر بالتكبير، ولكنه يستهلك الذاكرة عند كثرة العناصر.
• **Canvas يعتمد على Immediate Mode (Raster):** يرسم البكسلات مباشرة على اللوحة عبر JavaScript دون إنشاء عناصر DOM، مما يمنحه أداءً هائلاً للرسومات الكثيفة والمتحركة ولكنه يفتقد للتفاعل المباشر وإمكانية التكبير التلقائي.
**نختار SVG للايقونات، الواجهات المتجاوبة، والرسوم البيانية البسيطة التفاعلية. ونختار Canvas للألعاب، معالجة الصور والفيديو اللحظية، والرسوم البيانية الضخمة التي تحتوي على آلاف نقاط البيانات.
الشرح بالتفصيل:**
كمهندس واجهات (UI Engineer)، يُطلب منك اختيار الأداة المناسبة لبناء الحل التقني بأعلى كفاءة. لا توجد تقنية "أفضل" مطلقاً، بل توجد **"التقنية المناسبة للحالة المناسبة"**.
تعال نفصل متى تختار كل منهما بناءً على حالات الاستخدام الحقيقية:
**1. متى تختار الـ SVG؟ (When to choose SVG)**
تختار الـ SVG عندما تكون **الدقة والتفاعل** هما الأولوية القصوى:
• **أنظمة الأيقونات والشعارات (Icon Systems & Logos):** لتضمن ظهورها بحجم حاد ونقي على جميع الشاشات (Retina Displays).
• **مكونات الواجهات المتجاوبة (Responsive UI Components):** مثل الأزرار، الخلفيات المتموجة (Waves)، والإطارات.
• **الرسوم البيانية التفاعلية البسيطة (Interactive Charts):** مثل المخططات التي تحتوي على عشرات العناصر وتريد ظهور نص توضيحي (Tooltip) جميل عند تحويم الماوس (`hover`) على كل شريط أو نقطة.
• **الرسوم المتحركة المستمرة الخفيفة (CSS Animations):** التي تعتمد على تحريك حواف الأشكال وخلفياتها دون استهلاك جافاسكريبت كثيف.
**2. متى تختار الـ Canvas؟ (When to choose Canvas)**
تختار الـ Canvas عندما يكون **الأداء والسرعة وتحديث البكسلات** هم الأولوية القصوى:
• **تطوير الألعاب ثنائية وثلاثية الأبعاد (2D & 3D Web Games):** التي تتطلب تحديث الصفحة 60 مرة في الثانية (60 FPS) وتحريك مئات الأجسام المتصادمة (باستخدام 2D Context أو WebGL/Three.js).
• **معالجة وتعديل الصور والفيديو (Image & Video Processing):** تطبيق الفلاتر (Blur, Crop, Color Correction) على مستوى البكسل اللحظي.
• **الرسوم البيانية الضخمة وتصور البيانات (Big Data Visualization):** مثل رسم الخرائط الحرارية (Heatmaps) أو مخططات الأسهم الحية التي تحتوي على 100,000 نقطة بيانات.
• **التطبيقات التفاعلية الحرة (Drawing Apps / Whiteboards):** مثل تطبيقات الرسم الحر بالفرشاة (مثل Figma أو Canva Canvas Engine).
**3. لمحة ذكاء للـ UI Engineer (سؤال الفخ للمقابلة)**
الـ Interviewer ممكن يسألك: **"كيف تجعل رسمة Canvas تفاعلية مع نقرة المستخدم على دائرية معينة بالرغم من عدم وجود عناصر DOM داخلها؟"**
**الإجابة الذكية:**
• نستخدم دالة مدمجة في Canvas API تُسمى **`ctx.isPointInPath(path, x, y)`** أو **`ctx.isPointInStroke(x, y)`**.
• عندما ينقر المستخدم على اللوحة، نلتقط إحداثيات النقرة ($x, y$) من حادثة الماوس (`event.clientX/Y`) ونمررها لهذه الدالة لتخبرنا برمجياً هل هذه الإحداثيات تقع داخل حدود المسار المطلوب أم لا!
**الكلمات المفتاحية للحفظ (Keywords):**
• **Retained Mode (SVG) vs Immediate Mode (Canvas):** طريقة تعامل المتصفح والـ DOM مع العناصر.
• **Vector Scalability:** قدرة الـ SVG على التمدد والتحجم بدون فقدان الجودة.
• **DOM Node Bottleneck:** مشكلة بطء الـ SVG عند كثرة عناصر الـ DOM.
• **Pixel Manipulation:** قدرة الـ Canvas على تعديل البكسلات المباشرة.
**جملتك النموذجية في المقابلة:"The core architectural difference between Canvas and SVG lies in rendering mode and DOM involvement. SVG is a retained-mode vector format where every element exists in the DOM, making it highly accessible, easy to style via CSS, and perfectly scalable—ideal for UI icons, responsive graphics, and light interactive charts. Canvas, by contrast, is an immediate-mode raster surface that renders pixels procedurally via JavaScript without maintaining DOM nodes; this yields superior rendering performance for high-frequency applications like 2D/3D games, big data visualizations, and pixel manipulation**