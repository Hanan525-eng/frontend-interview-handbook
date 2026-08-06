# الفصل السابع

# HTML Media

# 7.1 Responsive Images

---

# السؤال الاول

# What are the `<picture>` and `<source>` elements in HTML, and when should you use them?

## الإجابة

> The `<picture>` element allows developers to provide multiple versions of an image for different screen sizes, resolutions, or image formats. The `<source>` element defines these alternative image sources, while the `<img>` element acts as the fallback image.
> 

---

## لماذا تهتم الشركات بهذا السؤال؟

لأن الصور تمثل جزءًا كبيرًا من حجم صفحات الويب، واستخدام العنصر المناسب يساعد على:

- تحسين الأداء (Performance)
- دعم الشاشات المختلفة
- دعم صيغ الصور الحديثة
- تحسين تجربة المستخدم (UX)
- تحسين Core Web Vitals

كما أن الفرق بين `<img>` و`<picture>` من أشهر أسئلة مقابلات Front-End.

---

# 1. `<picture>`

---

## الإجابة

> The `<picture>` element is a container that allows the browser to choose the most appropriate image based on screen size, resolution, or supported image format.
> 

---

## متى نستخدمه؟

- Responsive Images
- Art Direction
- Different Image Formats
- Mobile/Desktop Images
- Performance Optimization

---

## لماذا لا نستخدم `<img>` فقط؟

لأن:

```
<imgsrc="banner.jpg">
```

يعرض نفس الصورة لجميع الأجهزة.

أما:

```
<picture>

...<img></picture>
```

فيتيح للمتصفح اختيار الصورة الأنسب.

---

# المثال الأساسي

```
<picture><sourcemedia="(max-width: 768px)"srcset="mobile.jpg"><imgsrc="desktop.jpg"alt="Banner"></picture>
```

---

## ماذا يحدث؟

إذا كان عرض الشاشة أقل من:

```
768px
```

يعرض:

```
mobile.jpg
```

أما إذا كانت الشاشة أكبر:

يعرض:

```
desktop.jpg
```

---

## لماذا نستخدمه؟

لأن تحميل صورة أصغر على الهاتف:

- أسرع
- أقل استهلاكًا للبيانات
- أفضل للأداء

---

# أشهر الاستخدامات

- Hero Images
- Landing Pages
- Product Images
- News Websites
- E-commerce

---

# 2. `<source>`

---

## الإجابة

> The `<source>` element specifies one or more alternative media resources for elements such as `<picture>`, `<audio>`, and `<video>`.
> 

---

## داخل `<picture>`

يستخدم لتحديد الصور البديلة.

---

## المثال

```
<picture><sourcesrcset="image.webp"type="image/webp"><imgsrc="image.jpg"alt="Image"></picture>
```

---

## ماذا يحدث؟

إذا كان المتصفح يدعم:

```
WebP
```

يعرض:

```
image.webp
```

وإلا:

يعرض:

```
image.jpg
```

---

## لماذا؟

لأن:

WebP

أصغر حجمًا من:

JPEG

في أغلب الحالات.

---

# دعم أكثر من صيغة

```
<picture><sourcesrcset="image.avif"type="image/avif"><sourcesrcset="image.webp"type="image/webp"><imgsrc="image.jpg"alt="Landscape"></picture>
```

---

## ماذا يحدث؟

المتصفح يحاول:

1. 

AVIF

↓

1. 

WebP

↓

1. 

JPEG

---

وهذا يسمى:

Progressive Fallback.

---

# أشهر الخصائص

## srcset

يحدد الصورة البديلة.

---

## media

يحدد متى تستخدم الصورة.

---

## type

يحدد نوع الصورة.

مثل:

```
image/webp
```

أو

```
image/avif
```

---

# Responsive Images

يمكن استخدام:

```
media="(max-width:768px)"
```

لتغيير الصورة حسب حجم الشاشة.

---

## مثال

```
<picture><sourcemedia="(max-width:600px)"srcset="small.jpg"><sourcemedia="(max-width:1024px)"srcset="medium.jpg"><imgsrc="large.jpg"alt="Mountain"></picture>
```

---

## ماذا يحدث؟

الهاتف:

↓

small.jpg

---

التابلت:

↓

medium.jpg

---

سطح المكتب:

↓

large.jpg

---

# Art Direction

أحيانًا لا نريد فقط صورة أصغر.

بل صورة مختلفة بالكامل.

مثال:

الهاتف:

صورة مقربة.

---

سطح المكتب:

صورة كاملة.

وهذا أحد أهم استخدامات:

```
<picture>
```

---

# الفرق بين `<img>` و `<picture>`

| Feature | `<img>` | `<picture>` |
| --- | --- | --- |
| صورة واحدة | ✅ نعم | ❌ لا |
| يدعم Responsive Images | محدود (مع `srcset` و`sizes`) | ✅ نعم |
| يدعم Art Direction | ❌ لا | ✅ نعم |
| يدعم أكثر من صيغة | محدود | ✅ نعم |
| يحتاج `<source>` | ❌ لا | ✅ نعم |

---

# أشهر أسئلة المقابلات

### What is the purpose of the picture element?

> It allows the browser to choose the most appropriate image for different devices or supported formats.
> 

---

### Why is img still required inside picture?

لأنه يعمل كـ:

Fallback Image.

---

### Can picture exist without img?

❌ لا.

يجب أن يحتوي على:

```
<img>
```

كعنصر احتياطي.

---

### What does source do?

يوفر مصادر بديلة للوسائط.

---

### Does source display anything?

❌ لا.

هو يحدد فقط الملفات التي يمكن للمتصفح اختيارها.

---

### Which element actually renders the image?

```
<img>
```

---

# مقارنة بين `src` و`srcset`

| `src` | `srcset` |
| --- | --- |
| صورة واحدة | عدة صور محتملة |
| يستخدم مع `<img>` | يستخدم مع `<source>` أو `<img>` |
| لا يختار بين عدة ملفات | يسمح للمتصفح باختيار الأنسب |

---

# Best Practices

- استخدم `<picture>` عندما تحتاج إلى صور مختلفة حسب الجهاز أو صيغة الملف.
- استخدم `<img>` كعنصر احتياطي داخل `<picture>`.
- استخدم صيغ حديثة مثل AVIF وWebP مع توفير JPEG أو PNG كبديل.
- لا تنس كتابة `alt` داخل `<img>` لتحسين إمكانية الوصول.
- استخدم الصور الأصغر للأجهزة المحمولة لتحسين الأداء.

---

# Senior Notes

هناك عدة نقاط يقع فيها كثير من المطورين:

### 1. `<picture>` لا يعرض الصور

الذي يعرض الصورة فعليًا هو:

```
<img>
```

أما:

```
<picture>
```

فهو يساعد المتصفح على اختيار الصورة المناسبة.

---

### 2. `<source>` ليس خاصًا بالصور

يمكن استخدامه أيضًا داخل:

- `<audio>`
- `<video>`

ولهذا ستراه مرة أخرى في الأقسام التالية من هذا الفصل.

---

### 3. متى تستخدم `<picture>` ومتى تستخدم `srcset` داخل `<img>`؟

- إذا كنت تريد **نفس الصورة بأحجام أو دقات مختلفة فقط**، فيمكن استخدام `srcset` مع `<img>`.
- أما إذا كنت تريد **صورًا مختلفة تمامًا** حسب الجهاز (Art Direction) أو دعم صيغ متعددة مثل AVIF وWebP مع بدائل، فاستخدم `<picture>` مع `<source>`.

---

## إذا اعتمدتِ على `<img>` فقط

يمكنك عمل Responsive Images باستخدام:

```
<imgsrc="image.jpg"srcset="
    image-480.jpg 480w,
    image-768.jpg 768w,
    image-1200.jpg 1200w"sizes="(max-width: 768px) 100vw, 50vw"alt="Example">
```

وهذا يغطي حوالي **80-90%** من مواقع الويب الحديثة.

بل في React وNext.js، معظم المطورين يستخدمون:

- `<img>`
- أو `<Image>` في Next.js

ولا يكتبون `<picture>` إلا نادرًا.

---

## لكن هل `<picture>` له بديل كامل؟

**لا.**

هناك حالتان لا يستطيع `<img>` وحده حلهما بشكل مثالي.

### 1. Art Direction

مثلاً لديك صورة بانر.

على الكمبيوتر تريد الصورة كاملة:

```
👨‍👩‍👧‍👦 + الخلفية كاملة
```

أما على الهاتف تريد صورة مقصوصة:

```
👨 فقط
```

هذه ليست نفس الصورة بحجم مختلف، بل **صورتان مختلفتان**.

هنا تحتاج:

```
<picture><sourcemedia="(max-width:768px)"srcset="mobile-banner.jpg"><imgsrc="desktop-banner.jpg"alt=""></picture>
```

ولا يمكن لـ `srcset` وحده أن يختار **صورتين مختلفتين** حسب التصميم.

---

### 2. دعم صيغ متعددة

مثلاً:

```
AVIF
↓

WebP
↓

JPEG
```

يمكنك جعل المتصفح يختار أفضل صيغة مدعومة.

وهذا أيضًا يتم بسهولة مع:

```
<picture><sourcesrcset="image.avif"type="image/avif"><sourcesrcset="image.webp"type="image/webp"><imgsrc="image.jpg"alt=""></picture>
```

---

# لكن في الواقع العملي...

لو سألتيني عن خبرتي مع المشاريع الحديثة.

في حوالي:

- React
- Next.js
- Vue
- Angular

فإن استخدام `<picture>` قليل جدًا.

أغلب المشاريع تعتمد على:

- `<img>`
- أو Next.js `<Image>`

وتستخدم:

- `srcset`
- `sizes`

وهذا يكفي لمعظم الحالات.

## 7.1 الصور المتجاوبة (`<picture>` و `<source>`)

### مثال الكود:

HTML

```
<!-- استخدام عنصر picture للتحكم في الصورة بحسب حجم الشاشة وتوافر الصيغ الحديثة -->
<picture>
  <!-- 1. التكيف حسب حجم الشاشة (Art Direction) -->
  <source media="(min-width: 1024px)" srcset="hero-desktop.webp" type="image/webp" />
  <source media="(min-width: 768px)" srcset="hero-tablet.webp" type="image/webp" />

  <!-- 2. توفير صيغة حديثة عالية الضغط للمتصفحات الداعمة (Format Switching) -->
  <source srcset="hero-mobile.webp" type="image/webp" />

  <!-- 3. الصورة الاحتياطية المباشرة (Fallback) - إجبارية في جميع الحالات -->
  <img src="hero-fallback.jpg" alt="صورة غلاف الموقع الرئيسية" loading="lazy" />
</picture>
```

### السؤال:

**ما هما عنصرا `<picture>` و `<source>` في HTML، ومتى يجب عليك استخدامهما؟**

*(بالإنجليزي: What are the `<picture>` and `<source>` elements in HTML, and when should you use them?)*

### الإجابة النموذجية للمقابلة (Interview Answer):

> **عنصر `<picture>` هو حاوية دلالية في HTML5 تُستخدم مع وسم واحد أو أكثر من عناصر `<source>` بالإضافة إلى عنصر `<img>` احتياطي، لتنفيذ تقنية الصور المتجاوبة (Responsive Images). نستخدمهما بشكل أساسي في حالتين: التوجيه الفني للصور (Art Direction) لتقديم قصات وتصميمات مختلفة بحسب أحجام الشاشات المختلفة، أو تبديل صيغ الصور (Format Switching) لتقديم صيغ حديثة وعالية الضغط مثل AVIF أو WEBP للمتصفحات الداعمة مع إبقاء صيغة تقليدية كـ JPEG للمتصفحات القديمة.**
> 

### الشرح بالتفصيل:

في الشاشات الحديثة ذات الأحجام والأنواع المتعددة (من الهواتف المحمولة الصغيرة إلى شاشات الدقة الفائقة Desktop)، أصبح استخدام وسم `<img>` بمفرده غير كافٍ لضمان الأداء العالي وتجربة المستخدم الممتازة. كمهندس واجهات (UI Engineer)، يمنحك عنصر `<picture>` التحكم الكامل في الصورة التي يتم تحميلها بناءً على ظروف جهاز المستخدم.

تعال نفصص كيفية عمل هذه العناصر:

#### 1. متى نستخدم `<picture>` و `<source>`؟ (الحالات الأساسية)

#### أ) التوجيه الفني للصور (Art Direction)

- **المشكلة:** الصورة الأفقية العريضة التي تبدو ممتازة على شاشة الديسكتوب، قد تظهر صغيرة جداً وغير واضحة عند تصغيرها لتناسب شاشة الموبايل الطولية.
- **الحل باستخدام `<picture>`:** يتيح لك تقديم صورة مختلفة تماماً ومقصوصة بشكل طولي (Cropped/Vertical) تناسب شاشات الموبايل باستخدام خاصية `media`.

#### ب) تبديل صيغ الصور لسرعة التحميل (Format Switching)

- **المشكلة:** الصيغ الحديثة للصور مثل **AVIF** و **WEBP** تقدم ضغطاً هائلاً للأحجام (أصغر بنسبة 30% - 50% مقارنة بـ JPEG) مع الحفاظ على نفس الجودة، ولكن بعض المتصفحات القديمة جداً قد لا تدعمها.
- **الحل باستخدام `<picture>`:** نضع ملف الـ WEBP أو AVIF داخل عنصر `<source type="image/webp">`؛ إذا كان المتصفح يدعمها سيحملها فوراً، وإذا كان لا يدعمها سيتجاهلها ويذهب للـ `<img>` التابعة للـ JPEG تلقائياً دون أي خطأ.

#### 2. الخصائص الجوهرية لعنصر `<source>`

| **الخاصية (Attribute)** | **الوظيفة والشرح** |
| --- | --- |
| **`media`** | قبول الاستعلامات الشرطية (Media Queries) مثل `(min-width: 1024px)` لتحديد متى تُطبق هذه الصورة. |
| **`srcset`** | يحدد مسار الصورة (أو مسارات متعددة بكثافات مختلفة مثل `1x`, `2x`). |
| **`type`** | يحدد نوع وصيغة صورة الملف المصدري (MIME type) مثل `image/webp` أو `image/avif`. |

#### 3. لمحة ذكاء للـ UI Engineer (سؤال الفخ للمقابلة)

الـ Interviewer ممكن يسألك: **"أين يتم رسم الصورة فعلياً على الشاشة داخل عنصر `<picture>`؟ وماذا يحدث إذا نسيت كتابة وسم `<img>` الداخلي؟"**

**الإجابة الذكية:**

1. **وسم `<img>` هو النواة الحقيقية (Core Render Element):**
    - عنصر `<picture>` وعناصر `<source>` هي مجرد **أدوات توجيه وقواعد (Rules Wrapper)** تقدم خيارات للمتصفح ليختار منها.
    - المتصفح يختار أفضل مسار موجود داخل `<source>` ويضعه **داخل عنصر `<img>`** الموجود بالمجموعة لرسمه على الشاشة وتطبيق تنسيقات الـ CSS عليه.
2. **النسيان القاتل:**
    - إذا نسيت إضافة وسم `<img>` في نهاية كود `<picture>`، **لن تظهر أي صورة على الشاشة على الإطلاق!** لأن عناصر `<source>` لا تملك القدرة على رسم الصورة بنفسها.

#### الكلمات المفتاحية للحفظ (Keywords):

- **Art Direction:** تقديم تصميمات وقصات مختلفة للصور بحسب الشاشة.
- **Format Switching:** تقديم صيغ حديثة مثل WebP/AVIF للسرعة مع وجود Fallback.
- **`srcset` and `media` Attributes:** خصائص تحديد شرط الحجم والمسار.
- **Mandatory Fallback `<img>`:** وسم الصورة الإجباري للرسم والتوافق.

#### جملتك النموذجية في المقابلة:

> **"The `<picture>` element is a responsive image wrapper that offers fine-grained control via child `<source>` tags before falling back to a standard `<img>`. We use it for Art Direction to serve differently cropped images based on media queries, and for Format Switching to deliver high-performance formats like AVIF or WebP to supporting browsers while seamlessly serving JPEG to legacy ones. Crucially, the embedded `<img>` tag is what actually gets rendered in the DOM**
> 

# HTML Media

# 7.2 Audio

---

# السؤال الثاني

# What are the `<audio>` and `<source>` elements in HTML, and when should you use them?

---

## الإجابة

> The `<audio>` element is used to embed sound content into a web page. The `<source>` element specifies one or more audio files, allowing the browser to choose the first supported format.
> 

---

## لماذا تهتم الشركات بهذا السؤال؟

لأن تشغيل الملفات الصوتية يجب أن يكون متوافقًا مع جميع المتصفحات، واستخدام أكثر من صيغة صوتية يضمن أفضل توافق ممكن.

كما أن معرفة خصائص `<audio>` مثل `controls` و`autoplay` و`preload` من الأسئلة الشائعة في مقابلات Front-End.

---

# 1. `<audio>`

---

## الإجابة

> The `<audio>` element embeds audio content such as music, podcasts, voice recordings, or sound effects into a web page.
> 

---

## متى نستخدمه؟

- Music Players
- Podcasts
- Voice Messages
- Sound Effects
- Language Learning
- Accessibility Audio

---

## المثال الأساسي

```
<audiocontrols><sourcesrc="music.mp3"type="audio/mpeg"></audio>
```

---

## ماذا يحدث؟

يعرض المتصفح مشغلًا صوتيًا يحتوي على أدوات التحكم مثل:

- Play
- Pause
- Timeline
- Volume

---

# لماذا نستخدم `<source>`؟

لأن المتصفحات لا تدعم جميع صيغ الصوت بنفس الشكل.

---

## المثال

```
<audiocontrols><sourcesrc="music.mp3"type="audio/mpeg"><sourcesrc="music.ogg"type="audio/ogg"></audio>
```

---

## ماذا يحدث؟

يحاول المتصفح تشغيل:

1. MP3

↓

1. OGG

↓

إذا لم يجد صيغة مدعومة ينتقل إلى التالية.

---

# أشهر الخصائص

## controls

يعرض أدوات التحكم.

```
controls
```

---

## autoplay

يشغل الصوت تلقائيًا.

```
autoplay
```

> **ملاحظة:** معظم المتصفحات الحديثة تمنع التشغيل التلقائي للصوت إذا لم يكن مكتومًا (Muted).
> 

---

## loop

يعيد تشغيل الملف بعد انتهائه.

```
loop
```

---

## muted

يشغل الملف بدون صوت.

```
muted
```

---

## preload

يحدد كيفية تحميل الملف قبل التشغيل.

القيم:

```
none
metadata
auto
```

---

### none

لا يحمل الملف مسبقًا.

---

### metadata

يحمل معلومات الملف فقط.

---

### auto

يسمح للمتصفح بتحميل الملف بالكامل إذا رأى ذلك مناسبًا.

> **ملاحظة:** القيمة `auto` هي مجرد تلميح (Hint)، والمتصفح قد يتصرف بشكل مختلف حسب الظروف.
> 

---

# مثال متكامل

```
<audiocontrolspreload="metadata"><sourcesrc="podcast.mp3"type="audio/mpeg"><sourcesrc="podcast.ogg"type="audio/ogg">

    Your browser does not support the audio element.</audio>
```

---

## ماذا يحدث؟

إذا لم يدعم المتصفح أيًا من الصيغ،

سيظهر النص:

```
Your browser does not support the audio element.
```

---

# أشهر أسئلة المقابلات

### Which attribute displays the audio controls?

```
controls
```

---

### Can audio play automatically?

✅ نعم.

لكن معظم المتصفحات تمنع التشغيل التلقائي للصوت غير المكتوم.

---

### Why use multiple source elements?

لدعم أكثر من صيغة صوتية وتحسين التوافق بين المتصفحات.

---

### Does source display anything?

❌ لا.

هو يحدد فقط الملفات التي يمكن للمتصفح تشغيلها.

---

# مقارنة بين `<audio>` و`<source>`

| Element | Purpose |
| --- | --- |
| `<audio>` | إنشاء مشغل صوت |
| `<source>` | تحديد ملفات الصوت البديلة |

---

# أشهر أسئلة المقابلات

### Which element actually plays the audio?

```
<audio>
```

---

### Can source be used without audio?

يمكن استخدامه أيضًا داخل:

- `<video>`
- `<picture>`

لكنه لا يعرض أي شيء بمفرده.

---

### Which audio format is most commonly supported?

```
MP3
```

---

# Best Practices

- استخدم `controls` إذا كنت تريد السماح للمستخدم بالتحكم في التشغيل.
- وفر أكثر من صيغة صوتية عند الحاجة إلى دعم متصفحات متنوعة.
- استخدم `preload="metadata"` عندما لا يكون من الضروري تحميل الملف كاملًا.
- أضف نصًا احتياطيًا داخل `<audio>` للمتصفحات القديمة.

---

# Senior Notes

هناك عدة نقاط يقع فيها كثير من المطورين:

### 1. لا تعتمد على `autoplay`

حتى إذا أضفت:

```
autoplay
```

فقد تمنع معظم المتصفحات تشغيل الصوت تلقائيًا لحماية تجربة المستخدم.

---

### 2. `controls` ينشئ واجهة المتصفح

شكل مشغل الصوت يختلف بين:

- Chrome
- Firefox
- Safari
- Edge

ولا يمكن تخصيص جميع أجزائه باستخدام CSS.

إذا كنت تحتاج إلى تصميم مخصص بالكامل، فستحتاج إلى بناء مشغل صوت باستخدام JavaScript.

---

### 3. `<source>` لا يشغل الصوت

العنصر:

```
<source>
```

يحدد فقط ملفات الصوت.

أما التشغيل وإدارة الحالة فيتم بواسطة:

```
<audio>
```

---

# تشغيل الصوتيات (`<audio>` و `<source>`)

### مثال الكود:

HTML

```
<!-- مشغل صوتيات متجاوب يدعم أكثر من صيغة لتضمن التوافق التام -->
<audio controls preload="metadata">
  <!-- 1. الصيغة الأولى والأعلى كفاءة (Ogg) -->
  <source src="podcast.ogg" type="audio/ogg" />

  <!-- 2. الصيغة الأكثر انتشاراً وتوافقاً (MP3) -->
  <source src="podcast.mp3" type="audio/mpeg" />

  <!-- 3. نص احتياطي للمتصفحات القديمة جداً التي لا تدعم تشغيل الصوت -->
  متصفحك لا يدعم تشغيل عنصر الصوت في HTML5.
</audio>
```

### السؤال:

**ما هما عنصرا `<audio>` و `<source>` في HTML، ومتى يجب عليك استخدامهما؟**

*(بالإنجليزي: What are the `<audio>` and `<source>` elements in HTML, and when should you use them?)*

### الإجابة النموذجية للمقابلة (Interview Answer):

> **عنصر `<audio>` في HTML5 يُستخدم لتضمين وتشغيل المقاطع الصوتية مباشرة داخل صفحات الويب دون الحاجة لمكتبات خارجية أو إضافات (Plugins). ويُستخدم عنصر `<source>` بداخله لتقديم خيارات مصادر متعددة بصيغ مختلفة (مثل MP3 أو OGG) لضمان توافق الصوت مع كافة المتصفحات، حيث يختار المتصفح أول صيغة يدعمها تلقائياً ويقوم بتشغيلها.**
> 

### الشرح بالتفصيل:

قبل تقديم HTML5، كان تشغيل الصوتيات يتطلب إضافات ثقيلة وغير آمنة مثل Flash Player. اليوم، يوفر مشغل الصوت الأصلي (Native Audio Control) أداءً عالياً وتوافقاً تاماً مع أجهزة الموبايل والدليل الشامل لإمكانية الوصول.

تعال نفصص الخصائص وطريقة الاستخدام بعناية:

#### 1. الخصائص الجوهرية لعنصر `<audio>`

| **الخاصية (Attribute)** | **الوظيفة والشرح** |
| --- | --- |
| **`controls`** | إظهار واجهة التشغيل المدمجة بالمتصفح (زر التشغيل/الإيقاف، شريط الصوت، والتحكم بالوقت). بدون هذه الخاصية يكون المشغل مخفياً! |
| **`preload`** | يحدد كيف يتصرف المتصفح مع تحميل الملف قبل التشغيل:

• `none`: عدم تحميل أي شيء لتقديم أفضل أداء للشبكة.

• `metadata`: تحميل المعلومات الأساسية فقط (المدة، الحجم).

• `auto`: تحميل الملف بالكامل بمجرد فتح الصفحة. |
| **`autoplay`** | تشغيل الصوت تلقائياً بمجرد فتح الصفحة (مقيدة جداً في المتصفحات الحديثة). |
| **`loop`** | إعادة تشغيل المقطع الصوتي تلقائياً بلا نهاية عند انتهائه. |
| **`muted`** | بدء تشغيل الصوت في وضع كتم الصوت المبدئي. |

#### 2. متى نستخدم `<audio>` و `<source>` معاً؟ (Cross-Browser Compatibility)

نستخدم عنصر `<source>` المدمج بدلاً من كتابة خاصية `src` مباشرة داخل وسم `<audio>` لضمان **تعدد الصيغ المصدرية (Multi-format Fallback)**:

- **صيغة MP3 (`audio/mpeg`):** الصيغة الأكثر شيوعاً وتعمل تقريباً على جميع المتصفحات والأنظمة.
- **صيغة Ogg (`audio/ogg`):** صيغة مفتوحة المصدر وعالية الضغط مدعومة بقوة في Firefox و Chrome.
- **صيغة WAV (`audio/wav`):** غير مضغوطة عالية الجودة ولكن حجمها كبير جداً.

عند تقديم صيغ مختلفة داخل أوسمة `<source>`، يقرأ المتصفح الأوسمة من الأعلى للأسفل، ويشغل **أول صيغة يتعرف عليها فقط** ويهمل الباقي.

#### 3. لمحة ذكاء للـ UI Engineer (سؤال الفخ للمقابلة)

الـ Interviewer ممكن يسألك: **"لماذا ترفض المتصفحات الحديثة (مثل Chrome و Safari) خاصية `autoplay` على عنصر الصوت عند فتح الصفحة مباشرة؟"**

**الإجابة الذكية:**

- **سياسة تجربة المستخدم والأمان (User Experience & Autoplay Policy):**
    - المتصفحات تمنع الصوت التلقائي فور فتح الصفحة لمنع إزعاج المستخدم أو استهلاك بيانات الموبايل بدون إذنه.
    - لا يتم تفعيل الـ `autoplay` بملف يحتوي على صوت إلا إذا تفاعل المستخدم أولاً مع الصفحة (User Interaction) مثل الضغط على أي زر أو النقر في أي مكان داخل الواجهة، أو إذا أضيفت خاصية `muted` للوسم.

#### الكلمات المفتاحية للحفظ (Keywords):

- **Native Audio Player:** المشغل الأصلي للصوتيات في المتصفح.
- **`controls` Attribute:** خاصية إظهار أزرار التحكم بالصوت للـ UI.
- **Format Fallback Mechanism:** دعم صيغ متعددة عبر `<source>` لضمان التوافق.
- **Autoplay Restrictions:** قيود المتصفحات على التشغيل التلقائي للصوتيات.

#### جملتك النموذجية في المقابلة:

> **"The `<audio>` element provides native media capabilities to play audio files directly in the browser without plugins. Combining it with child `<source>` tags allows us to implement fallback mechanisms across various audio codecs—like MP3 and Ogg—ensuring cross-browser compatibility. We control player behavior through attributes like `controls`, `preload`, and `loop`, keeping in mind that modern browsers strictly block unmuted `autoplay` until explicit user interaction occurs**
> 

# 7.3 Video

---

# السؤال الثالث

# What are the `<video>`, `<source>`, and `<track>` elements in HTML, and when should you use them?

## الإجابة

> The `<video>` element embeds video content into a web page. The `<source>` element provides one or more video files, while the `<track>` element adds timed text such as subtitles, captions, or descriptions.
> 

---

## لماذا تهتم الشركات بهذا السؤال؟

لأن الفيديو من أكثر الوسائط استخدامًا في التطبيقات الحديثة، كما أن دعم الترجمات (Subtitles) وإمكانية الوصول (Accessibility) أصبح من المتطلبات الأساسية في كثير من المشاريع.

---

# 1. `<video>`

---

## الإجابة

> The `<video>` element embeds video content that users can play directly in the browser.
> 

---

## متى نستخدمه؟

- Online Courses
- Product Demonstrations
- Tutorials
- Marketing Videos
- Video Galleries
- Training Platforms

---

## المثال الأساسي

```
<videocontrols><sourcesrc="video.mp4"type="video/mp4"></video>
```

---

## ماذا يحدث؟

يعرض المتصفح مشغل فيديو يحتوي على أدوات مثل:

- Play
- Pause
- Timeline
- Volume
- Fullscreen

---

# أشهر الخصائص

## controls

يعرض أدوات التحكم.

```
controls
```

---

## autoplay

يشغل الفيديو تلقائيًا.

```
autoplay
```

> **ملاحظة:** معظم المتصفحات تسمح بالتشغيل التلقائي فقط إذا كان الفيديو مكتومًا (`muted`).
> 

---

## muted

يشغل الفيديو بدون صوت.

```
muted
```

---

## loop

يعيد تشغيل الفيديو تلقائيًا بعد انتهائه.

```
loop
```

---

## poster

يعرض صورة قبل تشغيل الفيديو.

```
poster="thumbnail.jpg"
```

---

## preload

يحدد كيفية تحميل الفيديو.

القيم:

```
none
metadata
auto
```

---

## width و height

لتحديد أبعاد الفيديو.

```
width="640"
height="360"
```

---

# مثال متكامل

```
<videocontrolswidth="640"poster="thumbnail.jpg"preload="metadata"><sourcesrc="movie.mp4"type="video/mp4"></video>
```

---

# 2. `<source>`

---

## الإجابة

> The `<source>` element specifies one or more video files, allowing the browser to play the first supported format.
> 

---

## المثال

```
<videocontrols><sourcesrc="movie.mp4"type="video/mp4"><sourcesrc="movie.webm"type="video/webm"></video>
```

---

## ماذا يحدث؟

يحاول المتصفح تشغيل:

1. MP4

↓

1. WebM

↓

ثم ينتقل إلى الصيغة التالية إذا لم يدعم الأولى.

---

# أشهر الخصائص

- src
- type

---

## أشهر الصيغ

- MP4
- WebM
- Ogg

---

# 3. `<track>`

---

## الإجابة

> The `<track>` element provides timed text for a video, such as subtitles, captions, descriptions, or chapter information.
> 

---

## لماذا نستخدمه؟

لإضافة:

- Subtitles
- Captions
- Descriptions
- Chapters

---

## المثال

```
<videocontrols><sourcesrc="movie.mp4"type="video/mp4"><tracksrc="subtitles-en.vtt"kind="subtitles"srclang="en"label="English"></video>
```

---

## ماذا يحدث؟

يمكن للمستخدم تشغيل الترجمة من داخل مشغل الفيديو.

---

# أشهر الخصائص

## src

ملف الترجمة.

---

## kind

يحدد نوع المسار.

القيم الشائعة:

- subtitles
- captions
- descriptions
- chapters
- metadata

---

## srclang

لغة الترجمة.

مثال:

```
srclang="en"
```

---

## label

الاسم الذي يظهر للمستخدم.

---

## default

يجعل هذا المسار هو الافتراضي.

```
default
```

---

# مثال متكامل

```
<videocontrolswidth="720"poster="cover.jpg"><sourcesrc="course.mp4"type="video/mp4"><sourcesrc="course.webm"type="video/webm"><tracksrc="captions-en.vtt"kind="captions"srclang="en"label="English"default>

    Your browser does not support the video element.</video>
```

---

# مقارنة بين العناصر

| Element | Purpose |
| --- | --- |
| `<video>` | تشغيل الفيديو |
| `<source>` | تحديد ملفات الفيديو البديلة |
| `<track>` | إضافة الترجمات أو النصوص الزمنية |

---

# أشهر أسئلة المقابلات

### What is the purpose of the video element?

> It embeds video content into a web page.
> 

---

### Why use multiple source elements?

لدعم أكثر من صيغة فيديو وتحسين التوافق بين المتصفحات.

---

### What does the track element do?

> It provides subtitles, captions, descriptions, or other timed text.
> 

---

### Which attribute displays video controls?

```
controls
```

---

### Which attribute displays a preview image?

```
poster
```

---

### Which file format is used for subtitles?

```
WebVTT (.vtt)
```

---

### Can a video have multiple tracks?

✅ نعم.

يمكن إضافة أكثر من مسار للغات مختلفة أو أنواع مختلفة من النصوص.

---

# مقارنة بين Audio وVideo

| Feature | `<audio>` | `<video>` |
| --- | --- | --- |
| تشغيل الصوت | ✅ نعم | ✅ نعم |
| عرض الصورة | ❌ لا | ✅ نعم |
| يدعم `poster` | ❌ لا | ✅ نعم |
| يدعم `<track>` | ❌ لا | ✅ نعم |
| يدعم `<source>` | ✅ نعم | ✅ نعم |

---

# Best Practices

- استخدم MP4 كصيغة أساسية لأنه الأكثر دعمًا.
- وفر أكثر من صيغة عند الحاجة إلى توافق أوسع.
- استخدم `poster` لتحسين تجربة المستخدم قبل بدء التشغيل.
- أضف ترجمات باستخدام `<track>` لتحسين إمكانية الوصول.
- استخدم `preload="metadata"` إذا لم يكن من الضروري تحميل الفيديو كاملًا عند فتح الصفحة.

---

# Senior Notes

هناك عدة نقاط يقع فيها كثير من المطورين:

### 1. لا تعتمد على `autoplay`

معظم المتصفحات تمنع التشغيل التلقائي للفيديو إذا كان يحتوي على صوت.

إذا كان لابد من التشغيل التلقائي، فعادةً يُستخدم:

```
<videoautoplaymutedplaysinline>
```

ويُستخدم `playsinline` خصوصًا على الأجهزة المحمولة لمنع تشغيل الفيديو في وضع ملء الشاشة تلقائيًا.

---

### 2. استخدم `<track>` لتحسين Accessibility

وجود ترجمات ليس مجرد ميزة إضافية، بل يساعد:

- ضعاف السمع.
- المستخدمين الذين يشاهدون الفيديو بدون صوت.
- التطبيقات التعليمية.

---

### 3. `<source>` لا يشغل الفيديو

العنصر:

```
<source>
```

يحدد فقط ملفات الفيديو.

أما التشغيل وإدارة الفيديو فتتم بواسطة:

```
<video>
```

---

### 4. لا تعتمد على شكل مشغل الفيديو

واجهة `<video controls>` تختلف بين:

- Chrome
- Firefox
- Safari
- Edge

إذا احتجت مشغلًا بتصميم خاص، فغالبًا ستستخدم JavaScript ومكتبات مثل Video.js أو Plyr مع الحفاظ على دعم إمكانية الوصول.

# 7.3 الفيديو والترجمة (`<video>`, `<source>`, `<track>`)

### مثال الكود:

HTML

```
<!-- مشغل فيديو متجاوب وعالي الأداء يضم الخيارات التوافقية والترجمة -->
<video controls poster="thumbnail.jpg" preload="metadata" width="800">
  <!-- 1. مصادر الفيديو بصيغ مختلفة لمنع مشاكل التوافق (Format Fallback) -->
  <source src="course-intro.webm" type="video/webm" />
  <source src="course-intro.mp4" type="video/mp4" />

  <!-- 2. ملف الترجمة والنصوص التوضيحية لجميع المستخدمين (Accessibility) -->
  <track
    src="subtitles-ar.vtt"
    kind="subtitles"
    srclang="ar"
    label="العربية"
    default
  />
  <track
    src="subtitles-en.vtt"
    kind="subtitles"
    srclang="en"
    label="English"
  />

  <!-- 3. نص احتياطي يظهر فقط للمتصفحات القديمة جداً -->
  متصفحك لا يدعم تشغيل عنصر الفيديو في HTML5.
</video>
```

### السؤال:

**ما هي عناصر `<video>` و `<source>` و `<track>` في HTML، ومتى يجب عليك استخدام كل منها؟**

*(بالإنجليزي: What are the `<video>`, `<source>`, and `<track>` elements in HTML, and when should you use them?)*

### الإجابة النموذجية للمقابلة (Interview Answer):

> **تُستخدم هذه العناصر الثلاثة معاً لبناء مشغل فيديو دلالي، متجاوب، وشامل لإمكانية الوصول (Accessible):**
> 
> - **عنصر `<video>`:** هو الحاوية الرئيسية التي تعرض مشغل الفيديو واجهة التفاعل.
> - **عنصر `<source>`:** يوضع داخل الفيديو لتقديم صيغ مختلفة (مثل MP4 و WebM) حتى يختار المتصفح الصيغة الأفضل المدعومة لديه.
> - **عنصر `<track>`:** يُستعمل لإضافة ملفات النص والتسميات التوضيحية (Subtitles / Captions) بصيغة `.vtt` لدعم الترجمة وإمكانية الوصول لضعاف السمع.

### الشرح بالتفصيل:

في تطوير الواجهات الحديثة، تضمين الفيديو لم يعد يقتصر على وضع رابط وتكبير الشاشة. كمهندس واجهات (UI Engineer)، يجب أن توازن بين **سلاسة التشغيل والأداء**، **التوافق بين المتصفحات**، و**معايير إمكانية الوصول (Accessibility - a11y)**.

تعال نفصص وظائف وخصائص هذه العناصر الثلاثة:

#### 1. تفكيك العناصر الثلاثة ووظائفها

#### أولاً: عنصر `<video>`

- **الوظيفة:** الحاوية البرمجية والهيكلية لعرض المشغل.
- **أهم الخصائص:**
    - `controls`: إظهار أزرار التحكم الافتراضية للمتصفح (تشغيل، إيقاف، مستوى الصوت، الشاشة الكاملة).
    - `poster`: تحديد صورة غلاف (Thumbnail) تظهر للمستخدم قبل الضغط على زر التشغيل.
    - `playsinline`: **خاصية جوهرية للموبايل**؛ تمنع هواتف iPhone/Android من فتح الفيديو في وضع الشاشة الكاملة الإجباري وتسمح بتشغيله داخل مكان الصفحة نفسه.
    - `muted`: كتم الصوت مبدئياً (وهي شرط إجباري إذا أردت تشغيل الفيديو تلقائياً عبر `autoplay`).

#### ثانياً: عنصر `<source>`

- **الوظيفة:** تقديم خيارات معددة للصيغ الصوتية والمرئية لضمان عمل الفيديو على جميع الأجهزة والمتصفحات.
- **أهم الصيغ المستخدمة:**
    - **WebM (`video/webm`):** صيغة حديثة توفر ضغطاً هائلاً وأحجام ملفات أصغر، مدعومة بقوة في Chrome و Firefox.
    - **MP4 (`video/mp4`):** الصيغة الأكثر شيوعاً والتوافقية مع كافة المتصفحات والأنظمة (خاصة Safari و iOS).

#### ثالثاً: عنصر `<track>`

- **الوظيفة:** ربط ملفات نصية خارجية بصيغة **WebVTT (`.vtt`)** لعرض نصوص الترجمة أو الشروحات الصوتية.
- **أنواع خاصية `kind`:**
    - `subtitles`: ترجمة النصوص للغات مختلفة.
    - `captions`: نصوص توضيحية لضعاف السمع (تصف الأصوات والمؤثرات مثل: *[صوت موسيقى هادئة]*).
    - `descriptions`: وصف صوتي للأحداث الصامتة للمكفوفين.
- **الخصائص الجوهرية:**
    - `srclang`: رمز اللغة (مثل `ar` أو `en`).
    - `label`: الاسم الذي يظهر للمستخدم في قائمة خيارات الترجمة المنسدلة بالمشغل.
    - `default`: تحديد هذا الملف ليكون مفاداً ومفعلاً تلقائياً عند تشغيل الفيديو.

#### 2. لمحة ذكاء للـ UI Engineer (سؤال الفخ للمقابلة)

الـ Interviewer ممكن يسألك: **"كيف تجعل الفيديو يعمل خلفيةً للموقع (Background Video) بدون أزرار تحكم وبطريقة آمنة لا تتأثر بحظر التشغيل التلقائي (Autoplay Policy)؟"**

**الإجابة الذكية:**

لتشغيل فيديو خلفية بشكل سلس ودون أن يحظره المتصفح، يجب دمج الأوسمة التالية معاً بالضرورة:

HTML

```
<video autoplay loop muted playsinline>
  <source src="bg-video.mp4" type="video/mp4" />
</video>
```

1. **`autoplay`:** للتشغيل التلقائي.
2. **`muted`:** **بدونها سيمنع المتصفح التشغيل التلقائي فوراً!** التشغيل التلقائي مسموح فقط للفيديوهات الصامتة.
3. **`loop`:** لإعادة الفيديو تلقائياً كخلفية مستمرة.
4. **`playsinline`:** لمنع هواتف iOS من قفز الفيديو لوضع ملء الشاشة وتخريب تصميم الواجهة.

#### الكلمات المفتاحية للحفظ (Keywords):

- **Native Media Player:** مشغل الميديا المدمج في HTML5.
- **Format Fallback:** توفير صيغ مختلفة مثل MP4 و WebM للتوافق.
- **WebVTT Standard (`.vtt`):** الامتداد المعياري لملفات ترجمة عنصر `<track>`.
- **Accessibility Captions:** دعم ضعاف السمع واللغات عبر خيارات `kind`.
- **Inline Mobile Playback (`playsinline`):** تشغيل الفيديو داخل سياق الصفحة في الموبايل.

#### جملتك النموذجية في المقابلة:

> **"HTML5 video delivery relies on three complementary elements: `<video>` acts as the UI wrapper with attributes like `controls`, `poster`, and `playsinline` for mobile optimization; `<source>` handles multi-codec fallbacks—typically WebM for performance and MP4 for universal support; and `<track>` integrates WebVTT files to supply accessible subtitles and captions (`kind="subtitles"`). For background videos, combining `autoplay`, `loop`, `muted`, and `playsinline` bypasses browser autoplay restrictions while maintaining clean visual presentation**
>