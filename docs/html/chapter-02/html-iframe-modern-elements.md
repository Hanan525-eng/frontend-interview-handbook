# الفصل العاشر و الحادي عشر

# HTML iframe

# 10.1 iframe Basics

---

# السؤال الأول

# What is the `<iframe>` element in HTML, and how is it used?

## الإجابة

> The `<iframe>` (Inline Frame) element embeds another HTML document or external resource inside the current web page. It allows content from another page or website to be displayed within a rectangular frame.
> 

---

## لماذا تهتم الشركات بهذا السؤال؟

لأن `<iframe>` يُستخدم لدمج محتوى خارجي داخل صفحات الويب، مثل:

- Google Maps
- YouTube Videos
- PDF Documents
- Power BI Dashboards
- Google Docs
- Payment Pages

وفهم خصائصه الأساسية ضروري قبل تعلم إعداداته الأمنية.

---

# 1. `<iframe>`

---

## الإجابة

> The `<iframe>` element embeds another webpage or external resource inside the current HTML document.
> 

---

## المثال

```
<iframesrc="https://example.com"></iframe>
```

---

## ماذا يحدث؟

يعرض الصفحة الموجودة في:

```
https://example.com
```

داخل صفحة موقعك.

---

## الاستخدامات الشائعة

- Embedded Videos
- Maps
- Documents
- Dashboards
- Third-party Widgets

---

# 2. `src`

---

## الإجابة

> The `src` attribute specifies the URL of the page or resource to display inside the iframe.
> 

---

## المثال

```
<iframesrc="https://www.youtube.com/embed/VIDEO_ID"></iframe>
```

---

## ماذا يحدث؟

يعرض فيديو YouTube داخل الصفحة.

---

# 3. `title`

---

## الإجابة

> The `title` attribute provides a text description of the iframe for accessibility.
> 

---

## المثال

```
<iframesrc="https://example.com"title="Company Dashboard"></iframe>
```

---

## لماذا هو مهم؟

تستخدمه:

- Screen Readers
- Accessibility Tools

لمساعدة المستخدمين على معرفة محتوى الـ iframe.

---

## هل هو اختياري؟

تقنيًا نعم.

لكن عمليًا يُعتبر من **أفضل الممارسات**، وتوصي به معايير الوصول (Accessibility).

---

# 4. `width`

---

## الإجابة

> The `width` attribute specifies the width of the iframe.
> 

---

## المثال

```
<iframesrc="https://example.com"width="800"></iframe>
```

---

## ماذا يحدث؟

يجعل عرض الـ iframe:

```
800px
```

---

# 5. `height`

---

## الإجابة

> The `height` attribute specifies the height of the iframe.
> 

---

## المثال

```
<iframesrc="https://example.com"width="800"height="500"></iframe>
```

---

## ماذا يحدث؟

يجعل ارتفاع الـ iframe:

```
500px
```

---

# 6. `name`

---

## الإجابة

> The `name` attribute assigns a name to the iframe so it can be referenced by links, forms, or JavaScript.
> 

---

## المثال

```
<iframename="contentFrame"src="about.html"></iframe>
```

---

## مثال مع رابط

```
<iframename="contentFrame"src="home.html"></iframe><ahref="about.html"target="contentFrame">

    About</a>
```

---

## ماذا يحدث؟

عند الضغط على الرابط:

بدلًا من فتح صفحة جديدة،

سيتم تحميل:

```
about.html
```

داخل الـ iframe نفسه.

---

# مثال عملي متكامل

```
<iframesrc="https://www.youtube.com/embed/VIDEO_ID"title="HTML Tutorial"width="800"height="450"name="videoFrame"></iframe>
```

---

# مقارنة بين الخصائص

| Attribute | Purpose |
| --- | --- |
| `<iframe>` | تضمين صفحة أو مورد خارجي |
| `src` | تحديد عنوان المورد |
| `title` | وصف الإطار لتحسين Accessibility |
| `width` | تحديد العرض |
| `height` | تحديد الارتفاع |
| `name` | تسمية الإطار لاستخدامه مع الروابط أو JavaScript |

---

# أشهر أسئلة المقابلات

### What is the purpose of the `<iframe>` element?

> It embeds another webpage or external resource inside the current page.
> 

---

### Which attribute specifies the embedded page?

```
src
```

---

### Why should you use the `title` attribute?

> To improve accessibility by describing the iframe's content.
> 

---

### What does the `name` attribute do?

> It allows the iframe to be referenced by links, forms, or JavaScript.
> 

---

### Can an iframe display content from another website?

✅ نعم، إذا كان الموقع الآخر يسمح بذلك. بعض المواقع تمنع تضمين صفحاتها داخل iframes باستخدام سياسات أمنية مثل `X-Frame-Options` أو `Content-Security-Policy`.

---

# استخدامات في المشاريع الحقيقية

| Project | Why use iframe? |
| --- | --- |
| شركة تعرض موقعها على الخريطة | Google Maps Embed |
| منصة تعليمية | YouTube Video |
| لوحة تحكم | Power BI Dashboard |
| نظام إدارة مستندات | PDF Viewer أو Google Docs |
| صفحة تواصل | خريطة أو نموذج خارجي |

---

# Best Practices

- استخدم `title` دائمًا لتحسين إمكانية الوصول.
- حدد `width` و`height` بما يناسب تصميم الصفحة.
- استخدم iframe فقط عند الحاجة إلى تضمين محتوى خارجي.
- تأكد من أن المصدر (`src`) موثوق وآمن.
- اجعل الـ iframe متجاوبًا (Responsive) باستخدام CSS عند الحاجة.

---

# Senior Notes

هناك عدة نقاط يقع فيها كثير من المطورين:

### 1. ليس كل موقع يمكن تضمينه

بعض المواقع تمنع عرض صفحاتها داخل `<iframe>` لأسباب أمنية، لذلك قد ترى رسالة مثل:

> **Refused to display in a frame**
> 

وهذا سلوك طبيعي تحدده إعدادات الموقع الآخر.

---

### 2. `name` أصبح استخدامه محدودًا

في التطبيقات الحديثة مثل **React** و**Next.js** نادرًا ما يُستخدم `name` مع الروابط، لكنه لا يزال موجودًا في HTML ويظهر في المشاريع القديمة أو عند التعامل مع أنظمة خارجية.

---

### 3. `<iframe>` ليس بديلًا عن التنقل داخل التطبيق

إذا كنت تبني تطبيق React أو Next.js، فلا تستخدم `<iframe>` للتنقل بين صفحات التطبيق. استخدم نظام التوجيه (Routing)، واجعل iframe مخصصًا فقط لتضمين محتوى خارجي.

---

# 10.1 أساسيات الـ iframe في HTML (`<iframe>` Basics)

### مثال الكود:

HTML

```
<!DOCTYPE html>
<html lang="ar">
<head>
  <meta charset="UTF-8">
  <title>iFrame Basics Example</title>
  <style>
    iframe {
      width: 100%;
      height: 400px;
      border: 2px solid #e2e8f0;
      border-radius: 8px;
    }</style>
</head>
<body>

  <h2>تضمين محتوى خارجي (Embedding External Content)</h2>

  <!-- 1. تضمين صفحة مستند خارجي عبر الخاصية src -->
  <iframe
    src="https://example.com"
    title="مستند خارجي توضيحي"
    loading="lazy">
    متصفحك لا يدعم إطار iframe.
  </iframe>

  <!-- 2. تضمين خارجي مخصص ومؤمن بالـ Sandbox -->
  <iframe
    src="https://www.youtube.com/embed/dQw4w9WgXcQ"
    title="مشغل فيديو يوتيوب"
    width="560"
    height="315"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen>
  </iframe>

</body>
</html>
```

### السؤال:

**ما هو عنصر `<iframe>` في HTML، وكيف يُستخدم؟**

*(بالإنجليزي: What is the `<iframe>` element in HTML, and how is it used?)*

### الإجابة النموذجية للمقابلة (Interview Answer):

> **عنصر `<iframe>` (Inline Frame) هو عنصر HTML يُستخدم لتضمين مستند HTML خارجي آخر داخل الصفحة الحالية:**
> 
> - **طبيعة العمل:** ينشئ سياق تصفح مستقل تماماً (Browsing Context) يحتوي على كائن `window` و `document` منفصلين عن الصفحة الأب.
> - **أشهر الاستخدامات:** تضمين خراط جوجل (Google Maps)، فيديوهات يوتيوب (YouTube Videos)، بوابات الدفع الإلكتروني (Payment Gateways)، والإعلانات الخارجية (Third-party Ads).
> - **الممارسة الأفضل:** يُشترط دائماً إضافة خاصية `title` لضمان إمكانية الوصول (Accessibility)، واستخدام خصائص الأمان مثل `sandbox` للحماية من هجمات XSS و Clickjacking.

### الشرح بالتفصيل:

عنصر الـ `<iframe>` هو بمثابة "نافذة داخل نافذة"؛ يتيح لك جلب موقع أو تطبيق ويب كامل وعرضه داخل جزء محدد من صفحتك دون التحويل إليه.

تعال نفصل أهم الخصائص والمفاهيم المرتبطة به:

#### 1. الخصائص الأساسية (Core Attributes)

- **`src`:** يحدد مسار أو رابط (URL) الصفحة المراد تضمينها.
- **`title`:** **(إجباري لتوافقية الوصول)** يصف محتوى الـ iframe لمكفوفين والبرامج الناطقة (Screen Readers).
- **`width` و `height`:** يحددان أبعاد الإطار (يفضل التنسيق بـ CSS، لكن خصائص HTML تمنع تذبذب تخطيط الصفحة Layout Shift).
- **`loading="lazy"`:** يمنع تحميل محتوى الـ iframe حتى يقترب المستخدم من التمرير إليه، مما يرفع أداء الصفحة وسرعتها.

#### 2. خصائص التحكم والأمان (Security & Permissions)

تضمين محتوى خارجي يفتح أبواباً للمخاطر الأسبانية والبرمجية، ولذلك تتوفر خصائص للحماية:

- **`sandbox`:** أهم خاصية أمان على الإطلاق! تفرض قيوداً صارمة على المحتوى المدفوع داخل الـ iframe (تمنع تشغيل الجافاسكريبت، ارسال النماذج، أو فتح نوافذ جديدة) إلا إذا سمحت بها صراحة مثل: `sandbox="allow-scripts allow-forms"`.
- **`allow`:** تحدد الصلاحيات والأجهزة التي يمكن للمحتوى المدفوع الوصول إليها (مثل الكاميرا، الميكروفون، وضعيّات الشاشة الكاملة `fullscreen`).

#### 3. فخ المقابلة الشهير: سياسة الأصل الواحد (Same-Origin Policy) والـ Cross-Origin

غالبًا ما يسأل مسؤول المقابلة: **"هل يمكن لكود الجافاسكريبت في الصفحة الرئيسية التحكم بمحتوى الـ iframe أو قراءة بياناته؟"**

**الإجابة الحاسمة:**

- **إذا كان الـ iframe من نفس النطاق (Same-Origin):** نعم، يمكن للصفحة الأب الوصول لـ DOM الخاص بالـ iframe عبر `iframe.contentDocument` أو `iframe.contentWindow`.
- **إذا كان من نطاق مختلف (Cross-Origin):** **لا، يمنع المتصفح ذلك تماماً** لدواعي الأمان بموجب (Same-Origin Policy). والطريقة الوحيدة الآمنة للتواصل بينهما هي استخدام واجهة `window.postMessage()`.

#### 4. مشكلة الـ Clickjacking وكيفية حظر التضمين

إذا حاول موقع خبيث تضمين موقعك داخل `<iframe>` لتضليل المستخدمين بالنقر على أزرار وهمية (Clickjacking)، يمكنك منع موقعك من الظهور داخل أي iframe خارجي عبر إرسال HTTP Headers من السيرفر:

- **`X-Frame-Options: DENY`** أو `SAMEORIGIN`.
- أو عبر Content Security Policy: **`frame-ancestors 'none'`**.

#### الكلمات المفتاحية للحفظ (Keywords):

- **Browsing Context:** سياق تصفح منفصل له DOM و Window خاصين به.
- **Same-Origin Policy (SOP):** سياسة الأمان التي تمنع التداخل بين النطاقات المختلفة.
- **Sandbox Attribute:** خاصية العزل الأمني للمحتوى المُضمّن.
- **Clickjacking Protection:** الحماية من الاستغلال عبر إطارات التضمين.

#### جملتك النموذجية في المقابلة:

> **"The `<iframe>` element creates a nested browsing context used to embed external HTML documents, such as maps, payment frames, or media. It runs with its own separate document and window object. To ensure accessibility, a descriptive `title` attribute must always be provided. For security, we use the `sandbox` attribute to restrict untrusted content and enforce permissions using `allow`. Access between the parent page and iframe DOM is governed by the Same-Origin Policy, requiring `postMessage()` for cross-origin communication."**
> 

هذا الموضوع من **أهم وأعمق أسئلة المقابلات لمصممي ومطوري الواجهات (Frontend / Full-stack Engineers)**؛ لأنه يختبر فهمك لبنية الأمان في المتصفح (Browser Security Architecture) وليس مجرد كتابة كود HTML.

إليك شرح تفصيلي وعملي للمفهومين مع الأمثلة وكيف توضحها في المقابلة بثقة.

## 1. سياسة الأصل الواحد (Same-Origin Policy - SOP)

### ما هو "الأصل" (Origin) في المتصفح؟

لكي يعتبر المتصفح موقعين أنهما من **"نفس الأصل" (Same-Origin)**، يجب أن يتطابقوا في **3 عناصر متكاملة**:

1. **البروتوكول (Protocol):** مثل `http://` أو `https://`
2. **النطاق (Domain / Host):** مثل `example.com`
3. **المنفذ (Port):** مثل `:80` أو `:443` أو `:3000`

> **قاعدة ذهبية:** إذا اختلف عنصر واحد فقط من هذه الثلاثة، يعتبر المتصفح الطلب **Cross-Origin** فوراً!
> 

#### أمثلة للتوضيح (مقارنة مع الصفحة الأصلية: `https://mycompany.com/app`):

| الرابط المُضمّن في הـ iframe | هل هو Same-Origin؟ | السبب |
| --- | --- | --- |
| `https://mycompany.com/profile` | **نعم (Same-Origin)** | نفس البروتوكول والنطاق والمنفذ. |
| `http://mycompany.com/profile` | **لا (Cross-Origin)** | اختلاف البروتوكول (`http` مقابل `https`). |
| `https://api.mycompany.com` | **لا (Cross-Origin)** | اختلاف النطاق الفرعي (Subdomain). |
| `https://mycompany.com:8080` | **لا (Cross-Origin)** | اختلاف المنفذ (`8080` مقابل المنفذ الافتراضي `443`). |
| `https://google.com` | **لا (Cross-Origin)** | نطاق مختلف تماماً. |

### سيناريو الكود: كيف يتعامل المتصفح مع الـ DOM؟

#### حالة 1: نفس الأصل (Same-Origin)

تخيل أن لديك موقع يدير لوحة تحكم، وجزء منها معروض في iframe من نفس الموقع.

JavaScript

```
// الصفحة الأب (Parent Page)
const myIframe = document.getElementById('my-iframe');

// الوصول الآمن للـ DOM الداخلي للـ iframe
const iframeDoc = myIframe.contentDocument || myIframe.contentWindow.document;

// يمكنك قراءة وتعديل أي عنصر بالداخل بحرية!
iframeDoc.querySelector('h1').innerText = "تم التعديل من الصفحة الأب!";
```

#### حالة 2: أصل مختلف (Cross-Origin)

تخيل أنك ضمنت صفحة من `https://bank-login.com` داخل موقعك.

JavaScript

```
const bankIframe = document.getElementById('bank-iframe');

try {
  // المحاولة القسرية لقراءة بيانات الـ iframe
  console.log(bankIframe.contentDocument.body.innerHTML);
} catch (error) {
  // يطلق المتصفح خطأ أمني مباشر!
  // Uncaught DOMException: Blocked a frame with origin "https://mycompany.com"
  // from accessing a cross-origin frame.
}
```

### الحل الآمن للتواصل بين Cross-Origin: واجهة `window.postMessage()`

إذا كان الـ iframe يتبع لنطاق مختلف (مثلاً بوابة دفع مثل Stripe أو PayPal) وتحتاج الصفحة الرئيسية للتواصل معها لمعرفة هل نجحت عملية الدفع أم لا، نستخدم بروتوكول الرسائل الموثق `postMessage`:

JavaScript

```
// 1. الصفحة الأب ترسل رسالة للـ iframe
const paymentIframe = document.getElementById('payment-frame');
paymentIframe.contentWindow.postMessage(
  { action: 'PROCESS_PAYMENT', amount: 100 },
  'https://checkout.stripe.com' // تحديد النطاق المستهدف بدقة لدواعي الأمان
);

// 2. كود الـ iframe يستقبل الرسالة ويعالجها
window.addEventListener('message', (event) => {
  // التحقق الإجباري من أصل الرسالة قبل معالجتها!
  if (event.origin !== 'https://mycompany.com') return;

  console.log('وصلت الرسالة من الأب:', event.data);
});
```

## 2. هجمة الـ Clickjacking وكيفية الحظر

### كيف تعمل الهجمة بأسلوب مبسط؟

1. يقوم هكر بإنشاء موقع جذاب (مثل: "اضغط هنا للفوز بآيفون مجاناً!").
2. يضع زراً في صفحته يقول "احصل على الهدية".
3. يقوم بتضمين موقعك الحقيقي (مثلاً: موقع بنك أو فيسبوك) داخل `<iframe>` فوق الزر تماماً.
4. يجعل الـ `<iframe>` شفافاً بالكامل باستخدام CSS (`opacity: 0`).
5. عندما يضغط المستخدم على زر "الهدية"، فهو في الحقيقة ينقر على زر "تحويل أموال" أو "حذف الحساب" داخل موقعك المخفي، لأن الجلسة (Session/Cookies) الخاصة بالمستخدم لا تزال فعالة في متصفحه!

### أسلوب الدفاع: كيف يمنع السيرفر التضمين؟

الحماية لا تتم من كود الجافاسكريبت بالواجهة (Frontend)، بل تفرضها **ترويسات الأمان (HTTP Security Headers)** التي يرسلها خادم الويب (Server / Nginx / Node.js) عند طلب الصفحة:

#### 1. الترويسة الكلاسيكية: `X-Frame-Options`

- **`X-Frame-Options: DENY`**
    - **المعنى:** يمنع أي موقع على كوكب الأرض (بما في ذلك موقعك أنت) من تضمين هذه الصفحة داخل `<iframe>`.
- **`X-Frame-Options: SAMEORIGIN`**
    - **المعنى:** يسمح بتضمين الصفحة فقط إذا كان الموقع الذي يضمنها هو **نفس الأصل (Same-Origin)**.

#### 2. الترويسة الحديثة والمرنة: `Content-Security-Policy (CSP)`

تعتبر `X-Frame-Options` قديمة نوعاً ما، والمقياس الحديث هو استخدام توجيه `frame-ancestors` داخل CSP:

HTTP

```
Content-Security-Policy: frame-ancestors 'none';
```

*(تكافئ DENY - تمنع الجميع).*

HTTP

```
Content-Security-Policy: frame-ancestors 'self';
```

*(تكافئ SAMEORIGIN - تسمح لنفس النطاق فقط).*

HTTP

```
Content-Security-Policy: frame-ancestors 'self' https://trusted-partner.com;
```

*(ميزة حديثة: تسمح لنفسك + مواقع معينة محددة بالاسم بتضمين موقعك).*

## ملخص الإجابة السريعة للمقابلة (Elevator Pitch)

> "سياسة **Same-Origin Policy** هي خط الدفاع الأساسي في المتصفح. تمنع الجافاسكريبت في نطاق معين من قراءة الـ DOM أو بيانات `iframe` ينتمي لنطاق آخر (معتمدًا على البروتوكول، النطاق، والمنفذ)، وإذا احتجنا للتواصل بينهما نستخدم **`window.postMessage()`** حصراً بشكل آمن.
> 
> 
> أما لمنع هجمات **Clickjacking** (تضمين موقعنا في إطار شفاف لمخادعة المستخدم)، نتحكم في ذلك من السيرفر عبر إرسال ترويسات أمان مثل **`X-Frame-Options: SAMEORIGIN`** أو التوجيه الأحدث **`Content-Security-Policy: frame-ancestors`**."
> 

# 10.2 iframe Security & Performance

---

# السؤال الثاني

# What are the `sandbox`, `allow`, `referrerpolicy`, and `loading` attributes, and why are they important for iframes?

## الإجابة

> Modern iframes provide several attributes that improve security, privacy, permissions, and performance. The most important are `sandbox`, `allow`, `referrerpolicy`, and `loading`.
> 

---

## لماذا تهتم الشركات بهذا السؤال؟

لأن تضمين محتوى من مواقع خارجية قد يعرّض التطبيق لمخاطر أمنية أو يؤثر على الأداء إذا لم يتم تقييده بشكل صحيح.

---

# 1. `sandbox`

---

## الإجابة

> The `sandbox` attribute restricts what content inside an iframe is allowed to do.
> 

بدون `sandbox`، يحصل المحتوى المضمّن على صلاحياته العادية (ضمن سياسات المتصفح والموقع).

أما عند استخدامه، فيتم تقييد هذه الصلاحيات، ثم يمكنك السماح ببعضها بشكل صريح.

---

## المثال

```
<iframesrc="https://example.com"sandbox></iframe>
```

---

## ماذا يحدث؟

يتم تشغيل الصفحة داخل بيئة مقيدة (Sandbox)، مما يقلل المخاطر الأمنية.

---

## أشهر القيم

| Value | Purpose |
| --- | --- |
| `allow-scripts` | يسمح بتشغيل JavaScript |
| `allow-forms` | يسمح بإرسال النماذج |
| `allow-popups` | يسمح بفتح نوافذ جديدة |
| `allow-same-origin` | يعامل الصفحة كأنها من نفس الأصل (إذا انطبق ذلك) |
| `allow-downloads` | يسمح ببدء عمليات التنزيل |

---

# 2. `allow`

---

## الإجابة

> The `allow` attribute grants specific browser features to the iframe.
> 

---

## المثال

```
<iframesrc="https://example.com"allow="fullscreen; camera; microphone"></iframe>
```

---

## ماذا يحدث؟

يسمح للمحتوى باستخدام الميزات المحددة فقط، مثل:

- Fullscreen
- Camera
- Microphone
- Geolocation (إذا كانت مدعومة)

---

# 3. `referrerpolicy`

---

## الإجابة

> The `referrerpolicy` attribute controls what referrer information is sent when loading the iframe.
> 

---

## المثال

```
<iframesrc="https://example.com"referrerpolicy="no-referrer"></iframe>
```

---

## ماذا يحدث؟

لن يتم إرسال عنوان الصفحة الحالية (Referrer) إلى الموقع الخارجي.

---

## أشهر القيم

| Value | Purpose |
| --- | --- |
| `no-referrer` | لا يرسل أي Referrer |
| `origin` | يرسل اسم النطاق فقط |
| `strict-origin-when-cross-origin` | القيمة الافتراضية في أغلب المتصفحات الحديثة |

---

# 4. `loading`

---

## الإجابة

> The `loading` attribute controls when the iframe should be loaded.
> 

---

## القيم

- `eager`
- `lazy`

---

## المثال

```
<iframesrc="https://example.com"loading="lazy"></iframe>
```

---

## ماذا يحدث؟

لن يتم تحميل الـ iframe إلا عندما يقترب من منطقة العرض (Viewport)، مما يحسن سرعة تحميل الصفحة.

---

# مقارنة بين الخصائص

| Attribute | Purpose |
| --- | --- |
| `sandbox` | تقييد صلاحيات الـ iframe |
| `allow` | منح ميزات محددة للمحتوى |
| `referrerpolicy` | التحكم في معلومات الـ Referrer |
| `loading` | تحسين أداء تحميل الصفحة |

---

# أشهر أسئلة المقابلات

### Which attribute restricts iframe capabilities?

```
sandbox
```

---

### Which attribute grants browser permissions?

```
allow
```

---

### Which attribute improves iframe loading performance?

```
loading="lazy"
```

---

### Which attribute controls referrer information?

```
referrerpolicy
```

---

### Why is `sandbox` important?

> It reduces the security risks of embedding third-party content by restricting what the embedded page can do.
> 

---

# Best Practices

- استخدم `sandbox` مع أي iframe يعرض محتوى من جهة خارجية، إلا إذا كنت تحتاج صلاحيات محددة.
- امنح أقل عدد ممكن من الصلاحيات في `allow` (Principle of Least Privilege).
- استخدم `loading="lazy"` للإطارات الموجودة أسفل الصفحة لتحسين الأداء.
- اختر `referrerpolicy` بما يتناسب مع متطلبات الخصوصية.

---

# Senior Notes

### 1. لا تستخدم `allow="*"`

امنح فقط الميزات التي يحتاجها المحتوى فعلًا.

---

### 2. انتبه إلى `allow-same-origin`

عند دمجه مع:

```
sandbox
```

قد يغير طريقة تعامل الصفحة مع سياسة الأصل (Origin)، لذا استخدمه فقط عند الحاجة وبعد فهم تأثيره.

---

### 3. `loading="lazy"` لا يناسب كل الحالات

إذا كان الـ iframe يمثل محتوى أساسيًا يظهر مباشرة للمستخدم (مثل فيديو في أعلى الصفحة)، فقد يكون `eager` أو القيمة الافتراضية هو الخيار الأنسب.

# 10.3 iframe Security Best Practices

---

# السؤال الثالث

# How can you securely use an iframe in a web application?

## الإجابة

> When embedding external content with an iframe, developers should follow security best practices such as understanding the Same-Origin Policy, preventing Clickjacking, respecting X-Frame-Options and Content Security Policy (CSP), and using iframes only when appropriate.
> 

---

## لماذا تهتم الشركات بهذا السؤال؟

لأن `<iframe>` يسمح بعرض محتوى من مواقع أخرى، وإذا استُخدم بطريقة غير صحيحة فقد يؤدي إلى:

- Security Risks
- Privacy Issues
- Performance Problems
- Poor User Experience

---

# 1. Same-Origin Policy (SOP)

---

## ما هي؟

> The Same-Origin Policy (SOP) is a browser security mechanism that prevents a webpage from freely accessing data from another origin.
> 

---

## ما هو Origin؟

يتكون من ثلاثة أجزاء:

- Protocol (HTTP / HTTPS)
- Domain
- Port

مثال:

```
https://example.com:443
```

إذا اختلف أحد هذه الأجزاء، يُعتبر Origin مختلفًا.

---

## لماذا هو مهم مع iframe؟

إذا قمت بتضمين:

```
<iframesrc="https://another-site.com"></iframe>
```

فلن تتمكن غالبًا من الوصول إلى محتوى الصفحة الداخلية باستخدام JavaScript بسبب سياسة Same-Origin Policy.

---

## ماذا يمنع؟

- قراءة DOM الخاص بالموقع الآخر.
- الوصول إلى Cookies الخاصة به.
- الوصول إلى Local Storage الخاصة به.

---

# 2. Clickjacking

---

## ما هو؟

> Clickjacking is an attack that tricks users into clicking hidden or disguised elements inside an iframe.
> 

---

## مثال

تخيل أن موقعًا خبيثًا يضع زرًا شفافًا فوق زر:

```
Delete Account
```

أنت تعتقد أنك تضغط زرًا عاديًا.

لكنك في الحقيقة ضغطت زرًا داخل iframe.

---

## كيف نحمي مواقعنا؟

باستخدام:

- X-Frame-Options
- CSP frame-ancestors

---

# 3. X-Frame-Options

---

## ما هو؟

> X-Frame-Options is an HTTP response header that controls whether a webpage can be embedded inside an iframe.
> 

---

## أشهر القيم

| Value | Meaning |
| --- | --- |
| `DENY` | يمنع تضمين الصفحة داخل أي iframe. |
| `SAMEORIGIN` | يسمح بالتضمين فقط من نفس الموقع. |

> **ملاحظة:** القيمة `ALLOW-FROM` كانت مدعومة في بعض المتصفحات القديمة، لكنها لم تعد تُستخدم عمليًا. في المشاريع الحديثة يُعتمد على **Content Security Policy (frame-ancestors)** بدلًا منها.
> 

---

## ماذا يحدث إذا كان الموقع يمنع التضمين؟

قد تظهر رسالة مثل:

```
Refused to display 'https://example.com'
in a frame because it set 'X-Frame-Options'.
```

---

# 4. Content Security Policy (frame-ancestors)

---

## ما هو؟

> The `frame-ancestors` directive in Content Security Policy specifies which websites are allowed to embed the current page inside an iframe.
> 

---

## مثال

```
Content-Security-Policy:
frame-ancestors 'self';
```

---

## ماذا يعني؟

لا يسمح بتضمين الصفحة إلا من نفس الموقع.

---

## لماذا يُفضل على X-Frame-Options؟

لأنه:

- أكثر مرونة.
- يسمح بتحديد أكثر من مصدر.
- هو الحل الحديث الموصى به.

---

# متى تستخدم iframe؟

استخدمه عندما تحتاج إلى تضمين محتوى خارجي مثل:

- Google Maps
- YouTube Videos
- PDF Viewer
- Power BI Dashboards
- Google Docs
- نماذج أو Widgets من خدمات خارجية

---

# متى لا تستخدم iframe؟

لا تستخدمه من أجل:

- التنقل بين صفحات تطبيقك.
- عرض صفحات React أو Next.js الخاصة بك.
- بناء Layout الموقع.

بدلًا من ذلك استخدم:

- React Router
- Next.js App Router
- Components

---

# مقارنة سريعة

| Topic | Purpose |
| --- | --- |
| Same-Origin Policy | حماية البيانات بين المواقع المختلفة |
| Clickjacking | منع خداع المستخدم بالنقر على عناصر مخفية |
| X-Frame-Options | التحكم في إمكانية تضمين الصفحة داخل iframe |
| CSP (`frame-ancestors`) | تحديد المواقع المسموح لها بتضمين الصفحة |

---

# أشهر أسئلة المقابلات

### What is the Same-Origin Policy?

> It is a browser security mechanism that restricts interactions between documents from different origins.
> 

---

### What is Clickjacking?

> It is an attack that tricks users into clicking hidden or disguised content inside an iframe.
> 

---

### What is the purpose of X-Frame-Options?

> It controls whether a webpage can be embedded inside an iframe.
> 

---

### Which modern mechanism replaces most X-Frame-Options use cases?

> Content Security Policy (`frame-ancestors`).
> 

---

### When should you use an iframe?

> When embedding trusted external content such as videos, maps, or documents.
> 

---

### When should you avoid using an iframe?

> When building the main pages of your application or when a normal routing/component solution is more appropriate.
> 

---

# Best Practices

- استخدم `<iframe>` فقط عند الحاجة إلى تضمين محتوى خارجي.
- فعّل `sandbox` وامنح أقل عدد ممكن من الصلاحيات.
- استخدم `loading="lazy"` للإطارات غير الظاهرة عند تحميل الصفحة.
- استخدم `title` لتحسين إمكانية الوصول.
- إذا كنت تدير الخادم، استخدم **Content Security Policy (`frame-ancestors`)** للتحكم في من يمكنه تضمين صفحاتك.
- لا تعتمد على iframe كوسيلة لبناء واجهة تطبيق حديثة.

---

# Senior Notes

هناك عدة نقاط يقع فيها كثير من المطورين:

### 1. لا تخلط بين سياسات المتصفح وخصائص HTML

- `sandbox` و`allow` و`loading` هي **خصائص HTML**.
- Same-Origin Policy وX-Frame-Options وContent Security Policy هي **آليات أمنية يوفرها المتصفح أو الخادم**، وليست خصائص داخل عنصر `<iframe>`.

---

### 2. معظم مشاكل iframe ليست أخطاء برمجية

إذا رفض موقع خارجي أن يظهر داخل iframe، فغالبًا السبب هو إعدادات أمنية مثل:

- `X-Frame-Options`
- `Content Security Policy (frame-ancestors)`

وليس خطأ في كود HTML الخاص بك.

---

### 3. كيف يفكر الـ Senior؟

لا يسأل:

> **كيف أضع أي موقع داخل iframe؟**
> 

بل يسأل أولًا:

> **هل هذا الموقع يسمح بالتضمين؟ وهل أحتاج فعلًا إلى iframe؟**
> 

إذا كانت الإجابة نعم، فإنه يضيف القيود الأمنية المناسبة (`sandbox` و`allow`) ويحرص على الأداء (`loading="lazy"`).

---

# الفصل الحادي عشر

# Modern HTML Elements

# 11.1 Interactive Elements

---

# السؤال الاول

# What are the `<dialog>`, `<details>`, and `<summary>` elements, and when should you use them?

## الإجابة

> The `<dialog>`, `<details>`, and `<summary>` elements are interactive HTML elements that provide built-in browser functionality without requiring much JavaScript. They improve accessibility, simplify development, and reduce the amount of custom code needed for common UI patterns.
> 

---

## لماذا تهتم الشركات بهذا السؤال؟

لأن هذه العناصر توفر حلولًا جاهزة لمهام شائعة مثل:

- Modal Dialogs
- FAQ Sections
- Expand/Collapse Panels
- Disclosure Widgets

مما يقلل الاعتماد على JavaScript ويحسن Accessibility.

---

# 1. `<dialog>`

---

## الإجابة

> The `<dialog>` element represents a dialog box or modal window that can be opened and closed using JavaScript.
> 

---

## المثال

```
<dialogid="myDialog"><h2>Delete Account</h2><p>Are you sure?</p><buttononclick="myDialog.close()">

        Cancel</button></dialog><buttononclick="myDialog.showModal()">

    Open Dialog</button>
```

---

## ماذا يحدث؟

عند الضغط على الزر:

يفتح المتصفح نافذة Modal.

---

## أهم الدوال

| Method | Purpose |
| --- | --- |
| `show()` | يفتح Dialog عادي |
| `showModal()` | يفتح Dialog كنافذة Modal تمنع التفاعل مع الصفحة |
| `close()` | يغلق Dialog |

---

## متى يستخدم؟

- Delete Confirmation
- Login Popup
- Settings Dialog
- Notifications
- Confirmation Windows

---

# 2. `<details>`

---

## الإجابة

> The `<details>` element creates an expandable and collapsible section.
> 

---

## المثال

```
<details><summary>

        What is HTML?</summary><p>

        HTML stands for HyperText Markup Language.</p></details>
```

---

## ماذا يحدث؟

افتراضيًا:

يعرض فقط:

```
▶ What is HTML?
```

وعند الضغط:

يفتح المحتوى.

---

## هل يحتاج JavaScript؟

❌ لا.

المتصفح يقوم بكل شيء.

---

## الاستخدامات

- FAQ
- Documentation
- Help Sections
- Product Specifications

---

# 3. `<summary>`

---

## الإجابة

> The `<summary>` element defines the visible heading of a `<details>` element.
> 

---

## المثال

```
<details><summary>

        Show More</summary><p>

        Additional information.</p></details>
```

---

## ماذا يحدث؟

يصبح:

```
▶ Show More
```

وعند الضغط:

يظهر المحتوى.

---

## هل يمكن استخدامه وحده؟

❌ لا.

يجب أن يكون داخل:

```
<details>
```

---

# مقارنة بين العناصر

| Element | Purpose |
| --- | --- |
| `<dialog>` | إنشاء نافذة Dialog أو Modal |
| `<details>` | إنشاء قسم قابل للفتح والإغلاق |
| `<summary>` | عنوان قسم `<details>` |

---

# استخدامات في المشاريع الحقيقية

## FAQ

```
▶ What is React?

▶ What is HTML?

▶ What is CSS?
```

أفضل حل:

```
<details><summary>
```

---

## صفحة الإعدادات

```
Delete Account

↓

Are you sure?
```

أفضل حل:

```
<dialog>
```

---

## صفحة Documentation

```
▶ Installation

▶ Configuration

▶ Deployment
```

يمكن تنفيذها بالكامل باستخدام:

```
<details><summary>
```

---

# أشهر أسئلة المقابلات

### What is the purpose of the `<dialog>` element?

> It represents a dialog box or modal window.
> 

---

### Which method opens a modal dialog?

```
showModal()
```

---

### Which element creates an expandable section?

```
<details>
```

---

### Which element defines the clickable heading?

```
<summary>
```

---

### Can `<summary>` exist without `<details>`?

❌ No.

---

### Do `<details>` and `<summary>` require JavaScript?

❌ No.

The browser provides the expand/collapse behavior by default.

---

# Best Practices

- استخدم `<dialog>` للنوافذ المؤقتة بدلًا من بناء Modal بالكامل من الصفر إذا كان دعم المتصفحات في مشروعك مناسبًا.
- استخدم `<details>` و`<summary>` في أقسام FAQ والتوثيق.
- اجعل نص `<summary>` واضحًا لأنه يمثل نقطة التفاعل الرئيسية.
- لا تستخدم JavaScript لإضافة سلوك فتح/إغلاق إذا كان `<details>` يفي بالغرض.

---

# Senior Notes

هناك عدة نقاط يقع فيها كثير من المطورين:

### 1. `<dialog>` ليس مجرد `<div>`

كثير من المطورين ينشئون Modal باستخدام:

```
<divclass="modal">
```

لكن `<dialog>` عنصر دلالي (Semantic) صُمم لهذا الغرض، ويوفر سلوكًا مدمجًا مثل إدارة التركيز (Focus) عند استخدام `showModal()`، مع إمكانية التحكم فيه عبر JavaScript.

---

### 2. استخدم `<details>` بدلًا من JavaScript عند الإمكان

إذا كان المطلوب مجرد فتح وإغلاق محتوى، فإن `<details>` أبسط وأكثر قابلية للوصول (Accessible) من كتابة كود JavaScript مخصص.

---

### 3. متى لا تستخدم هذه العناصر؟

- إذا كان تصميم الـ Modal أو سلوكه معقدًا جدًا (Animations متقدمة، إدارة حالة معقدة، تكديس عدة نوافذ)، فقد تعتمد على مكتبة واجهة مستخدم مثل Radix UI أو Headless UI.
- إذا كنت تحتاج Accordion بسلوك خاص (مثل السماح بفتح عنصر واحد فقط)، فقد تضيف JavaScript فوق `<details>` أو تستخدم مكونًا مخصصًا.

# 11.1 العناصر التفاعلية في HTML5 الحديثة (`Interactive Elements`)

### مثال الكود:

HTML

```
<!DOCTYPE html>
<html lang="ar">
<head>
  <meta charset="UTF-8">
  <title>Interactive Elements Example</title>
  <style>
    /* تنسيق نافذة الـ Modal عند فتحها */
    dialog::backdrop {
      background-color: rgba(0, 0, 0, 0.6);
      backdrop-filter: blur(4px);
    }
    dialog {
      border: none;
      border-radius: 8px;
      padding: 20px;
      box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
    }
    details {
      border: 1px solid #cbd5e1;
      padding: 10px;
      border-radius: 6px;
      margin-top: 10px;
    }
    summary {
      font-weight: bold;
      cursor: pointer;
    }</style>
</head>
<body>

  <!-- 1. استخدام <details> و <summary> لقائمة الأسئلة الشائعة (Accordion) -->
  <details>
    <summary>ما هي ميزة استخدام <details> مقارنة بـ JavaScript؟</summary>
    <p>توفر استجابة تفاعلية أصلية بدون الحاجة لكتابة كود JS للتحكم بالظهور والإخفاء، وتدعم إمكانية الوصول (Accessibility) تلقائياً.</p>
  </details>

  <hr>

  <!-- 2. استخدام <dialog> لبناء نافذة منبثقة (Modal) -->
  <button id="openModalBtn">افتح النافذة المنبثقة</button>

  <dialog id="myModal">
    <h3>تأكيد الإجراء</h3>
    <p>هل أنت تأكد من أنك تريد المتابعة في هذه العملية؟</p>

    <!-- إغلاق الـ Dialog تلقائياً باستخدام <form method="dialog"> -->
    <form method="dialog">
      <button value="cancel">إلغاء</button>
      <button value="confirm">موافق</button>
    </form>
  </dialog>

  <script>
    const dialog = document.getElementById('myModal');
    const openBtn = document.getElementById('openModalBtn');

    // فتح النافذة المنبثقة كـ Modal مع طبقة معتمة (Backdrop)
    openBtn.addEventListener('click', () => {
      dialog.showModal();
    });

    // التقاط قيمة الزر الذي أُغلق به الـ Dialog
    dialog.addEventListener('close', () => {
      console.log('تم إغلاق النافذة بنتيجة:', dialog.returnValue);
    });</script>

</body>
</html>
```

### السؤال:

**ما هي عناصر `<dialog>`, `<details>`, و `<summary>`، ومتى يجب عليك استخدامها؟**

*(بالإنجليزي: What are the `<dialog>`, `<details>`, and `<summary>` elements, and when should you use them?)*

### الإجابة النموذجية للمقابلة (Interview Answer):

> **هي عناصر HTML5 تفاعلية أصلية (Native Interactive Elements) تُغني عن الاعتماد المفرط على مكتبات JavaScript لبناء عناصر الواجهة الشائعة:**
> 
> - **`<details>` و `<summary>`:** تُستخدم لبناء أجزاء طي وفرد المحتوى (Accordion / Collapsible Section). يمثل `<summary>` العنوان القابل للنقر، بينما يحتوي `<details>` على المحتوى المخفي الذي يظهر فقط عند فتح العنصر.
> - **`<dialog>`:** يُستخدم لبناء النوافذ المنبثقة (Modals & Dialog Boxes) مع دعم كامل وبنائي لإدارة التركيز (Focus Management)، واختصارات اللوحة (زر `Esc` للإغلاق)، وطبقة الخلفية المعتمة الرسمية عبر `::backdrop`.

### الشرح بالتفصيل:

قبل توفر هذه العناصر، كان بناء "Accordion" أو "Modal" يتطلب عشرات الأسطر من الجافاسكريبت للتحكم بخصائص `display: none` أو إضافة مكتبات أمان وإمكانية الوصول مثل ARIA Attributes. الآن، المتصفح يتكفل بذلك بأسلوبNative آمن وموفر للأداء.

#### 1. عنصر الـ Accordion: `<details>` و `<summary>`

يوفر هذا الثنائي طريقة بسيطة لإخفاء وإظهار التفاصيل:

- **طبيعة العمل:** يمتلك عنصر `<details>` خاصية منطقية (Boolean Attribute) تُسمى **`open`**. عند وجودها يكون المحتوى ظاهراً، وعند إزالتها يختفي المحتوى.
- **دور `<summary>`:** يوضع كـ **أول عنصر ابن** داخل `<details>`، ويعمل كـ Toggle Switch مدمج. إذا لم تضعه، سيضع المتصفح عنواناً افتراضياً من عنده (مثل "Details").
- **أشهر حالات الاستخدام:**
    - صفحات الأسئلة الشائعة (FAQ Sections).
    - شريط الفلاتر الجانبي في مواقع التسوق (Product Filters).
    - الأقسام الإضافية للمعلومات المتقدمة في الاستمارات.

#### 2. عنصر النافذة المنبثقة: `<dialog>`

يمثل الحل القياسي من HTML لبناء النوافذ الحوارية والـ Modals:

- **طرق الفتح عبر JavaScript:**
    - **`dialog.showModal()` [الأهم]:** يفتح النافذة كـ **Modal حقيقي**؛ يقطع التفاعل مع بقية الصفحة، ينشئ طبقة خلفية معتمة تُنسق بـ `::backdrop` في CSS، ويسمح بالإغلاق عبر زر `Esc`.
    - **`dialog.show()`:** يفتح النافذة كـ Non-modal Dialog (يمكن للمستخدم التفاعل مع بقية العناصر في الصفحة أثناء فتحها).
- **طريقة الإغلاق الذكية بدون JS:** يمكنك وضع نموذج داخل الـ Dialog بـ **`method="dialog"`**. عند الضغط على أي زر داخل هذا النموذج، سيعمل تلقائياً على إغلاق الـ Dialog وتخزين قيمة الزر (`value`) في الخاصية `dialog.returnValue`.
- **أشهر حالات الاستخدام:**
    - رسائل التأكيد والتحذير (Confirmation Popups).
    - استمارات تسجيل الدخول السريعة (Login Modals).
    - إشعارات النظام المهمة.

#### 3. فخ المقابلة الشهير: إمكانية الوصول (Accessibility) وتحديد التركيز (Focus Trap)

غالباً ما يسأل مسؤول المقابلة: **"لماذا يُفضل استخدام عنصر `<dialog>` الأصلي بدلاً من بناء Modal مخصص بـ `<div>` و JavaScript؟"**

**الإجابة الحاسمة:**

- **إدارة التركيز التلقائية (Focus Management):** عند فتح `<dialog>` عبر `showModal()`، ينقل المتصفح تلقائياً تركيز لوحة المفاتيح (Tab Focus) إلى أول عنصر تفاعلي داخل النافذة، ويقوم بعمل **Focus Trap** (يمنع مستخدم لوحة المفاتيح من التنقل خارج النافذة المنبثقة إلى بقية عناصر الصفحة).
- **دعم قارئات الشاشة (Screen Readers):** يعلن المتصفح فوراً عن وجود النافذة كـ `role="dialog"` وقارئ الشاشة يستوعب سياقها دون الحاجة لإضافة `aria-modal="true"` أو ضبط وسم ARIA معقد يدوياً.
- **زر الخروج المدمج:** ينصاع المتصفح تلقائياً لزر `Escape` في لوحة المفاتيح لإغلاق النافذة وإعادة التركيز للعنصر الذي فتحها (Focus Restoration).

#### الكلمات المفتاحية للحفظ (Keywords):

- **Native Accordion:** المكون المدمج بـ `<details>` و `<summary>`.
- **`showModal()` vs `show()`:** الفرق بين النافذة الحاكمة (Modal) وغير الحاكمة.
- **`::backdrop`:** المكون الرسومي في CSS الخاص بخلفية الـ Dialog.
- **Focus Trap:** حصر تنقل لوحة المفاتيح داخل النافذة المنبثقة لدواعي إمكانية الوصول.

#### جملتك النموذجية في المقابلة:

> **"The `<details>` and `<summary>` elements provide a native, zero-JavaScript accordion interface where `<summary>` acts as the clickable heading and `<details>` manages the collapsible state via the `open` attribute. The `<dialog>` element offers a standardized native modal API. Opening it with `.showModal()` automatically establishes a backdrop pseudo-element (`::backdrop`), enforces a keyboard focus trap, enables `Escape` key dismissal, and properly announces the modal context to screen readers without complex custom ARIA attributes."**
> 

## 11.2 Template Elements

### `<template>`

---

# السؤال الثاني

## What is the `<template>` element, and when should you use it?

### الإجابة

> The `<template>` element is used to define an HTML fragment that is not rendered immediately when the page loads. Its content can later be cloned and inserted into the document using JavaScript or used by Web Components.
> 

بمعنى أبسط:

`<template>` يسمح لك بتجهيز **HTML جاهز** بدون أن يظهر للمستخدم مباشرة.

---

# 1. كيف يعمل `<template>`؟

مثال:

```
<templateid="userCardTemplate"><articleclass="user-card"><h2>User Name</h2><p>User Email</p></article></template>
```

عند تحميل الصفحة:

❌ لن يظهر الـ card.

المتصفح يحتفظ بالمحتوى داخل الـ template، لكنه لا يعرضه كجزء من الصفحة.

---

# 2. لماذا نستخدمه؟

لنفترض أن عندك:

```
100 Users
```

وكل User يحتاج إلى:

```
Card
 ├── Name
 ├── Email
 └── Avatar
```

بدل كتابة نفس HTML مئة مرة، يمكنك إنشاء Template واحد:

```
<templateid="userTemplate"><articleclass="user-card"><imgclass="avatar"><h2class="name"></h2><pclass="email"></p></article></template>
```

ثم تستخدمه عدة مرات باستخدام JavaScript.

---

# 3. استخدام `<template>` مع JavaScript

```
<templateid="userTemplate"><articleclass="user-card"><h2class="name"></h2><pclass="email"></p></article></template><divid="users"></div><script>consttemplate=document.getElementById("userTemplate");constusersContainer=document.getElementById("users");constuserCard=template.content.cloneNode(true);userCard.querySelector(".name").textContent="Hanan";userCard.querySelector(".email").textContent="hanan@example.com";usersContainer.appendChild(userCard);</script>
```

---

# 4. ما هو `template.content`؟

هذه نقطة مهمة جدًا في المقابلات.

محتوى `<template>` لا يتم التعامل معه كأطفال عاديين داخل DOM.

للوصول إليه نستخدم:

```
template.content
```

وهو يمثل محتوى الـ template كـ **DocumentFragment**.

---

# 5. ما هو `cloneNode(true)`؟

```
template.content.cloneNode(true)
```

يقوم بإنشاء نسخة من محتوى الـ template.

الـ `true` تعني:

> Clone the element and all of its descendants.
> 

أي أنه ينسخ الـ HTML الموجود بالكامل، وليس العنصر الرئيسي فقط.

---

# دورة العمل

```
<template>
     ↓
template.content
     ↓
cloneNode(true)
     ↓
Modify Content
     ↓
appendChild()
     ↓
DOM
     ↓
User sees it
```

---

# هل `<template>` يظهر للمستخدم؟

❌ لا.

هذه نقطة مهمة جدًا.

```
<template><h1>Hello</h1></template>
```

لن يظهر:

```
Hello
```

على الصفحة.

يجب أولًا استخدام محتواه وإضافته إلى الـ DOM.

---

# أين يستخدم في المشاريع الحقيقية؟

## 1. Web Components

من أهم استخداماته.

يمكن استخدام:

```
<template>
```

لتعريف بنية Component داخل Web Component.

---

## 2. Dynamic HTML

إذا كنت تبني واجهة باستخدام Vanilla JavaScript وتحتاج إلى إنشاء نفس الـ UI عدة مرات.

مثلاً:

```
Product Card
Product Card
Product Card
Product Card
```

يمكن أن يكون لديك Template واحد.

---

## 3. Reusable UI Structures

مثل:

- User Cards
- Product Cards
- Notifications
- Table Rows
- List Items

---

# `<template>` vs HTML عادي

| HTML | `<template>` |
| --- | --- |
| يظهر للمستخدم | لا يظهر مباشرة |
| جزء من الصفحة | Fragment غير مُفعّل |
| يُرسم عند تحميل الصفحة | يحتاج إلى استخدامه |
| يمكن أن يكون محتوى مرئيًا | يستخدم كمخطط/قالب |

---

# أشهر أسئلة المقابلات

### What is the purpose of `<template>`?

> It defines an HTML fragment that is not rendered immediately and can be cloned and inserted later.
> 

---

### Does `<template>` render its content?

❌ No.

---

### How do you access template content?

```
template.content
```

---

### What does `cloneNode(true)` do?

> It creates a deep clone of the template content, including its descendants.
> 

---

### What type of object is `template.content`?

> It is a `DocumentFragment`.
> 

---

### Why is `<template>` useful?

> It allows reusable HTML structures to be defined once and instantiated multiple times.
> 

---

# Best Practices

- استخدم `<template>` عندما تحتاج إلى HTML structure قابلة لإعادة الاستخدام.
- استخدم `template.content` للوصول إلى المحتوى.
- استخدم `cloneNode(true)` عند الحاجة إلى نسخة كاملة.
- لا تتوقع أن يظهر محتوى `<template>` تلقائيًا.
- في التطبيقات الحديثة التي تستخدم React أو Vue، غالبًا ستتعامل مع مفهوم Components بدل استخدام `<template>` يدويًا.

---

# Senior Notes

### 1. `<template>` لا يقوم بنفس وظيفة React Component

في React تكتب:

```
<UserCard/>
```

والـ Component system يتولى إنشاء الـ UI.

أما `<template>` فهو **HTML-native mechanism** لتعريف Fragment يمكن استنساخه واستخدامه لاحقًا.

---

### 2. `<template>` مهم جدًا عند دراسة Web Components

وهنا سيصبح أكثر أهمية عندما نصل إلى:

```
<slot>
```

لأن `<template>` غالبًا يُستخدم مع **Shadow DOM وCustom Elements** لبناء Web Components.

---

### 3. لماذا لا نستخدم `<div hidden>` بدلًا منه؟

يمكن إخفاء HTML باستخدام `hidden`، لكن هذا ليس نفس المفهوم.

`<template>` مصمم تحديدًا ليكون **inert template content** لا يتم عرضه أو تفعيله كجزء طبيعي من الصفحة حتى تقوم أنت باستنساخه واستخدامه.

نقدر نقول ان ل <template>  زي ال  Component مظبوط

أيوه **من ناحية الفكرة العامة** ممكن تشبهيه بالـ Component، لكن **مش نفس الشيء**.

فكري فيها كده:

> `<template>` = **قالب HTML قابل لإعادة الاستخدام**
> 
> 
> React Component = **وحدة UI كاملة قابلة لإعادة الاستخدام**
> 

مثال:

```
<templateid="user-card"><article><h2class="name"></h2><pclass="email"></p></article></template>
```

ده يقول:

**"أنا جهزت شكل الـ User Card، ولما أحتاجه أعمل منه نسخة."**

وهذا قريب جدًا من فكرة:

```
<UserCard/>
```

لكن الفرق المهم:

| `<template>` | React Component |
| --- | --- |
| HTML Native | جزء من React |
| مجرد Template | UI + Logic + State + Props |
| لا يظهر وحده | Component يتم Render له |
| يحتاج JS لاستنساخه واستخدامه | React يدير الـ rendering |
| لا يملك State بنفسه | يمكن أن يمتلك State |
| محدود في الوظائف | أكثر قوة ومرونة |

### إذن في دماغك احفظيها هكذا:

```
<template>
    ↓
HTML Blueprint
    ↓
Clone
    ↓
Insert into DOM
```

بينما:

```
React Component
    ↓
Props / State / Logic
    ↓
Render
    ↓
UI
```

**فلو سألوك في Interview:**

> Is `<template>` the same as a React Component?
> 

الإجابة الأفضل:

> **No. `<template>` is a native HTML mechanism for defining reusable, non-rendered HTML fragments, while a React Component is a reusable UI unit that can contain markup, logic, state, and props.**
> 

# 11.2 عنصر القوالب في HTML (`<template>` Element)

### مثال الكود:

HTML

```
<!DOCTYPE html>
<html lang="ar">
<head>
  <meta charset="UTF-8">
  <title>Template Element Example</title>
  <style>
    .card {
      border: 1px solid #e2e8f0;
      padding: 16px;
      margin-bottom: 10px;
      border-radius: 8px;
      background-color: #f8fafc;
    }</style>
</head>
<body>

  <h2>قائمة المنتجات (Dynamic Products)</h2>
  <div id="product-list"></div>

  <!-- 1. تعريف الهيكل الخامل (Inert Template) الذي لن يظهر للعيان ولن تُحمل صوره فوراً -->
  <template id="product-card-template">
    <div class="card">
      <h3 class="product-name"></h3>
      <p class="product-price"></p>
    </div>
  </template>

  <script>
    // بيانات قادمة من API فرضي
    const products = [
      { name: 'حاسوب محمول', price: '1200$' },
      { name: 'هاتف ذكي', price: '800$' }
    ];

    const template = document.getElementById('product-card-template');
    const container = document.getElementById('product-list');

    products.forEach(product => {
      // 2. استنساخ محتوى القالب (DocumentFragment) بأسلوب عميق (Deep Clone)
      const clone = template.content.cloneNode(true);

      // 3. ملء البيانات داخل النسخة
      clone.querySelector('.product-name').textContent = product.name;
      clone.querySelector('.product-price').textContent = product.price;

      // 4. إدراج النسخة المستنسخة في الـ DOM الفعلي
      container.appendChild(clone);
    });</script>

</body>
</html>
```

### السؤال:

**ما هو عنصر `<template>`، ومتى يجب عليك استخدامه؟**

*(بالإنجليزي: What is the `<template>` element, and when should you use it?)*

### الإجابة النموذجية للمقابلة (Interview Answer):

> **عنصر `<template>` هو آلية مدمجة في HTML تُستخدم لتخزين هيكل DOM خامل (Inert DOM Structure) يتم إخفاؤه تلقائيًا وعدم تنفيذه أثناء تحميل الصفحة الأولى:**
> 
> - **طبيعة العمل:** يظل المحتوى الداخلي للقالب غائبًا عن شجرة الـ DOM الرئيسية؛ حيث لا تُعرض العناصر، ولا تُنفذ السكريبتات (`<script>`)، ولا تُحمل الموارد الخارجية (مثل الصور `<img src>`) إلا عند استنساخ المحتوى برمجياً واستخدامه بـ JavaScript.
> - **أشهر الاستخدامات:** إنشاء قوائم بيانات ديناميكية قادمة من APIs، وإصدار أجزاء واجهة متكررة، وبناء مكونات الويب المخصصة (**Web Components**) بالاقتران مع الـ **Shadow DOM**.

### الشرح بالتفصيل:

قبل توفر عنصر `<template>`، كان مطورو الواجهات يلجأون لطرق غير قياسية لتخزين قوالب الـ HTML الديناميكية؛ إما بكتابة نصوص HTML مطولة داخل سلاسل نصية بـ JavaScript (مثل `innerHTML`) أو بإخفاء عناصر DOM حقيقية باستخدام `display: none`.

#### 1. خمول المحتوى (Inert Behavior)

يتميز المحتوى الموجود داخل `<template>` بما يلي:

- **`template.content`:** يمثل كائنًا من نوع **`DocumentFragment`** يحتفظ بجميع العناصر الفرعية للقالب خارج الـ Document Tree الرئيسية.
- **عدم تحميل الموارد فوراً:** إذا كان داخل القالب `<img src="large-image.jpg">` أو `<script src="script.js">`، فإن المتصفح **لن يجلب الصورة ولن ينفذ السكريبت** حتى يتم استنساخ القالب وإدراجه فعلياً في الصفحة.
- **الغياب عن الاستعلامات:** أي استعلام بـ `document.querySelector()` للبحث عن عناصر داخل القالب سيفشل ولن يجدها إلا إذا بحثت بداخل `template.content`.

#### 2. متى نستخدم `<template>`؟

1. **الـ Web Components (Shadow DOM):** يمثل العمود الفقري لبناء إعادة استغلال العناصر المخصصة (Custom Elements).
2. **عرض القوائم الديناميكية (Dynamic Lists & Tables):** عند استقبال قوائم أو مصفوفات بيانات من الـ Backend ورغبتك في حقنها داخل الواجهة دون تكرار كتابة وسم HTML داخل سكريبتات الجافاسكريبت.
3. **أجهزة الرندر الجانبية بالعميل (Client-side Rendering):** لبناء أجزاء تفاعلية آمنة وسريعة بديلة عن مكتبات التمبلت الخارجية البسيطة.

#### 3. فخ المقابلة الشهير: المقارنة بين `<template>` والحلول القديمة

غالبًا ما يسأل مسؤول المقابلة: **"لماذا نفضل استخدام `<template>` بدلاً من استخدام عنصر `<div>` مخفي بـ `display: none` أو بناء الـ HTML بسلاسل نصية عبر `innerHTML`؟"**

**الإجابة الحاسمة:**

- **مقارنةً بـ `display: none`:**
عنصر الـ `<div>` المخفي بـ CSS يُعتبر جزءاً حقيقياً من شجرة الـ DOM. يقوم المتصفح بتحميل كل وسائط وسكريبتات العنصر المخفي فوراً مما يستهلك الباندويث ويزيد زمن التحميل، كما أنه يدخل في حسابات الأداء ومحركات البحث. بينما `<template>` خامل تماماً ولا يستهلك أي موارد حتى يُستنسخ.
- **مقارنةً بـ `innerHTML`:**
بناء العناصر باستخدام الـ Strings وسكبها في `innerHTML` يُعرض التطبيق لمخاطر الثغرات الأمنية مثل **XSS (Cross-Site Scripting)**، بالإضافة إلى ضياع أداء المتصفح في إعادة تحليل الـ HTML من جديد (Parsing Cost). أما `<template>` فيستخدم عناصر DOM حقيقية وآمنة وتضمن التكوين السريع بـ `cloneNode(true)`.

#### الكلمات المفتاحية للحفظ (Keywords):

- **Inert DOM:** المحتوى الخامل الذي لا يعالج ولا يُعرض تلقائياً.
- **`DocumentFragment`:** الهيكل الخفيف الذي يتواجد داخل `template.content`.
- **`cloneNode(true)`:** أداة استنساخ محتوى القالب بشرط التمرير العميق لجميع الأبناء.
- **Web Components & Shadow DOM:** البيئة الرئيسية والأكثر شيوعاً لاستخدام عنصر القوالب.

#### جملتك النموذجية في المقابلة:

> **"The `<template>` element is a standard HTML5 mechanism for declaring markup fragments that remain inert until instantiated via JavaScript. Unlike elements hidden with `display: none`, a template’s content sits inside a `DocumentFragment` (`template.content`), meaning scripts won't execute and media assets like images won't download until explicitly cloned using `cloneNode(true)` and appended to the active DOM. It provides a safer, more performant alternative to `innerHTML` string concatenation and serves as a core foundational piece for Web Components and Shadow DOM architectures**
> 

## 11.3 Web Components Basics

### `<slot>`

---

# السؤال الثالث

## What is the `<slot>` element, and how is it used in Web Components?

### الإجابة

> The `<slot>` element is a placeholder inside a Web Component that allows content from the component's consumer to be inserted into the component's Shadow DOM.
> 

ببساطة:

**`<slot>` = مكان فارغ داخل الـ Component، يسمح للمستخدم بإدخال محتوى من الخارج.**

---

# الفكرة الأساسية

تخيلي أننا أنشأنا Component اسمه:

```
<user-card>
```

ونريد أن نسمح للمستخدم بتحديد المحتوى الذي يظهر داخله.

يمكن أن يكون لدينا:

```
<user-card><span>Hanan</span></user-card>
```

والـ Web Component نفسه يحتوي على:

```
<slot></slot>
```

فالـ `<slot>` يقول:

> "ضع هنا المحتوى الذي وضعه المستخدم داخل `<user-card>`."
> 

---

# مثال بسيط

داخل Web Component:

```
<templateid="userCardTemplate"><divclass="card"><slot></slot></div></template>
```

ثم المستخدم يكتب:

```
<user-card><h2>Hanan</h2></user-card>
```

النتيجة تكون تقريبًا:

```
┌─────────────────┐
│ Hanan           │
└─────────────────┘
```

لأن:

```
<h2>Hanan</h2>
```

تم إدخاله في:

```
<slot>
```

---

# لماذا نحتاج `<slot>`؟

لأن Web Component قد يكون لديه **هيكل ثابت**، لكنه يحتاج أن يسمح للمستخدم بتغيير جزء من المحتوى.

مثلاً لدينا:

```
Card
 ├── Header
 ├── Content
 └── Footer
```

يمكن أن يكون الـ Component مسؤولًا عن الـ layout، بينما المستخدم يحدد المحتوى.

---

# Named Slots

وهذه نقطة مهمة جدًا.

يمكن أن يكون لدينا أكثر من Slot.

مثلاً:

```
<template><articleclass="card"><header><slotname="title"></slot></header><main><slotname="content"></slot></main></article></template>
```

ثم المستخدم:

```
<user-card><h2slot="title">
        Hanan</h2><pslot="content">
        Front-End Developer</p></user-card>
```

النتيجة:

```
┌────────────────────────┐
│ Hanan                  │
│                        │
│ Front-End Developer    │
└────────────────────────┘
```

---

# كيف يعمل `slot`؟

الفكرة:

```
Consumer
   │
   │ content
   ▼
<user-card>
   │
   ▼
<slot>
   │
   ▼
Shadow DOM
```

أي أن الـ Component يحدد **المكان**، والمستخدم يحدد **المحتوى**.

---

# Default Slot

إذا كتبت:

```
<slot></slot>
```

بدون `name`، فهذا يسمى:

**Default Slot**

مثال:

```
<my-card><p>Hello World</p></my-card>
```

و:

```
<slot></slot>
```

سيستقبل:

```
<p>Hello World</p>
```

---

# Named Slot

إذا كتبت:

```
<slotname="title"></slot>
```

فالمحتوى الذي يحمل:

```
slot="title"
```

هو الذي سيتم وضعه هناك.

مثال:

```
<my-card><h2slot="title">
        Product</h2></my-card>
```

---

# `<slot>` vs `<template>`

وهنا الربط المهم جدًا مع القسم السابق.

| `<template>` | `<slot>` |
| --- | --- |
| يعرّف HTML Template | يحدد مكان إدخال المحتوى |
| المحتوى لا يظهر مباشرة | يعرض محتوى يتم تمريره إليه |
| يمكن استنساخه | يستخدم داخل Web Components |
| Blueprint | Placeholder |

فكري فيها:

```
<template>
     ↓
ما هو شكل الـ Component؟
```

بينما:

```
<slot>
     ↓
أين أضع المحتوى الذي أعطاني إياه المستخدم؟
```

---

# أين يستخدم في المشاريع الحقيقية؟

يظهر `<slot>` بشكل أساسي في:

- Web Components
- Design Systems
- Custom Elements
- Lit
- Stencil
- بعض مكتبات الـ UI التي تعتمد على Web Components

مثلاً يمكن بناء:

```
<custom-button>
    Save</custom-button>
```

والـ Component نفسه يحدد شكل الزر، بينما:

```
Save
```

يدخل إلى Slot.

---

# هل سأستخدم `<slot>` في React؟

غالبًا **لا**.

في React ستستخدم غالبًا:

```
<Button>
    Save</Button>
```

ويتم تمرير `Save` كـ:

```
children
```

أي أن React لديه مفهوم مشابه:

```
HTML Web Components
        ↓
      <slot>

React
        ↓
      children
```

لكن الآليتين **ليستا نفس الشيء**.

---

# أشهر أسئلة المقابلات

### What is the purpose of `<slot>`?

> It provides a placeholder inside a Web Component for inserting content supplied by the component's consumer.
> 

---

### What is a default slot?

```
<slot></slot>
```

هو Slot بدون `name`، ويستقبل المحتوى غير المخصص لـ named slot.

---

### What is a named slot?

```
<slotname="title"></slot>
```

يسمح بتحديد المكان الذي سيتم فيه وضع محتوى معين.

---

### How do you assign content to a named slot?

باستخدام:

```
slot="title"
```

مثال:

```
<h2slot="title">
    Product</h2>
```

---

### Is `<slot>` commonly used in React?

> No. React typically uses `children` for a similar composition pattern.
> 

---

# Best Practices

- استخدم `<slot>` عند بناء Web Components.
- استخدم Named Slots عندما يكون لديك أكثر من منطقة محتوى.
- استخدم Default Slot للمحتوى الأساسي.
- لا تستخدم `<slot>` في مشروع React عادي لمجرد أنك تعرفه؛ استخدم آلية React المناسبة مثل `children`.

---

# Senior Notes

أهم شيء يجب فهمه هنا هو مفهوم:

## Composition

بدل أن تجعل الـ Component يتحكم في كل المحتوى، أنت تعطي المستخدم إمكانية تركيب المحتوى داخل الهيكل الذي تحدده.

مثلاً:

```
Component
│
├── Header
│     └── <slot name="header">
│
├── Content
│     └── <slot>
│
└── Footer
      └── <slot name="footer">
```

الـ Component يتحكم في **Structure**.

والمستخدم يتحكم في **Content**.

وهذا هو السبب في أن `<slot>` مهم جدًا عند بناء **Reusable Web Components وDesign Systems**.

---

# 🎯 الخلاصة التي تحفظيها

لو سألوك:

> **What is `<slot>`?**
> 

لا تقولي فقط:

> "It is used in Web Components."
> 

الأفضل:

> **`<slot>` is a placeholder inside a Web Component that allows consumers to inject their own content into the component's Shadow DOM.**
> 

ثم لو سألوك عن React:

> **React uses `children` for a similar composition pattern, while Web Components use slots.**
> 

# 11.3 أساسيات مكونات الويب وعنصر الـ Slot (`<slot>`)

### مثال الكود:

HTML

```
<!DOCTYPE html>
<html lang="ar">
<head>
  <meta charset="UTF-8">
  <title>Web Components Slot Example</title>
</head>
<body>

  <!-- استخدام المكون المخصص وإمرارات البيانات عبر الـ Slots -->
  <user-card>
    <!-- Light DOM Content -->
    <span slot="username">أحمد محمود</span>
    <span slot="role">مطور واجهات أمامية</span>
    <p>هذا النص يوضع في الـ Slot الافتراضي (Default Slot) لأنه لا يحمل اسم شريحة.</p>
  </user-card>

  <!-- تعريف المكون المخصص بـ JavaScript -->
  <script>
    class UserCard extends HTMLElement {
      constructor() {
        super();

        // 1. إنشاء Shadow DOM منفصل ومغلق/مفتوح
        const shadow = this.attachShadow({ mode: 'open' });

        // 2. تصميم قالب المكون بالداخلي مع تحديد أماكن الـ Slots
        shadow.innerHTML = `
          <style>
            .card {
              border: 2px solid #3b82f6;
              padding: 16px;
              border-radius: 8px;
              font-family: sans-serif;
              background-color: #f0f9ff;
            }
            .title { color: #1e40af; margin: 0; }
            .badge { background: #dbeafe; padding: 2px 8px; border-radius: 4px; font-size: 0.8em; }</style>

          <div class="card">
            <h3 class="title">
              <!-- Slot مسمى للـ username -->
              <slot name="username">اسم افتراضي</slot>
            </h3>
            <p>
              الصفة: <span class="badge"><slot name="role">زائر</slot></span>
            </p>
            <hr>
            <div>
              <!-- Default Slot لتمرير المحتوى العام -->
              <slot>لا يوجد محتوى إضافي.</slot>
            </div>
          </div>
        `;
      }
    }

    // 3. تسجيل المكون في المتصفح
    customElements.define('user-card', UserCard);</script>

</body>
</html>
```

### السؤال:

**ما هو عنصر `<slot>`، وكيف يُستخدم في مكونات الويب (Web Components)؟**

*(بالإنجليزي: What is the `<slot>` element, and how is it used in Web Components?)*

### الإجابة النموذجية للمقابلة (Interview Answer):

> **عنصر `<slot>` هو أداة نائبة (Placeholder / Outlet) دلالية تُستخدم داخل الـ Shadow DOM الملحق بـ Web Components لتمكين عملية إسقاط وتوزيع المحتوى (Content Projection):**
> 
> - **آلية العمل:** يسمح للمطور بإدراج عناصر HTML عادية من الـ Light DOM (الخارجي) لتعرض داخل أماكن محددة ومخصصة مسبقاً داخل الـ Shadow DOM (الداخلي) للمكون.
> - **أنواعه:** ينقسم إلى **Default Slot** (يستقبل المحتوى غير المعنون) و **Named Slots** (تستخدم الخصائص `name` و `slot` للتوجيه الدقيق).
> - **الميزة:** يوفر محتوى افتراضيًا fallback إذا لم يمرر المستخدم أي بيانات، ويحافظ على فصل هيكل المكون المخصص عن البيانات الممررة إليه.

### الشرح بالتفصيل:

تعتبر **Web Components** تقنية تسمح بإنشاء عناصر HTML مخصصة وإعادة استخدامها (مثل `<user-card>`). ولكن لكي تكون هذه المكونات مرنة، يجب أن تسمح للمستخدم بتمرير محتوى خارجي لداخلها، وهنا يأتي دور عنصر الـ **`<slot>`**.

عملية دمج الـ Light DOM مع الـ Shadow DOM تُسمى في المتصفح بـ **Shadow Tree Composition**.

#### 1. أنواع الـ Slots وتطبيقها

- **الـ Named Slots (الشرائح المحددة بالاسم):**
    - تُعرف داخل الـ Shadow DOM بإعطائها خاصية الاسم: `<slot name="header"></slot>`.
    - يتم استدعاؤها وتعبئتها من الخارج بتحديد الخاصية `slot` على العنصر المستهدف: `<h1 slot="header">العنوان</h1>`.
- **الـ Default Slot (الشريحة الافتراضية / Unnamed):**
    - تكون بدون خاصية `name`: `<slot></slot>`.
    - تقوم بالتقاط واستقبال أي عنصر أو نص يوضع داخل المكون المخصص ولم يُحدد له اسم `slot` خاص.
- **المحتوى البديل (Fallback / Default Content):**
    - يمكنك كتابة نص أو عناصر داخل وسم `<slot>تيكست افتراضي</slot>`. إذا لم يمرر المستخدم أي محتوى من الخارج، سيقوم المتصفح تلقائياً بظهار هذا المحتوى البديل.

#### 2. تنسيق محتوى الـ Slots عبر CSS (`::slotted`)

قد يتساءل مسؤول المقابلة عن كيفية تنسيق المحتوى الممرر عبر الـ Slot:

- المحتوى الممرر للـ Slot يظل تقنياً موجوداً في الـ **Light DOM** (خارج الـ Shadow DOM).
- لتنسيقه من داخل أنماط الـ Shadow DOM، نستخدم أداة التحديد المخصصة في CSS: **`::slotted()`**.
- **مثال:**CSS
    
    ```
    /* تنسيق كل عنصر p يُمرر داخل أي slot */
    ::slotted(p) {
      color: #475569;
      font-size: 14px;
    }
    ```
    

#### 3. فخ المقابلة الشهير: هل يتحرك عنصر الـ Slot في الـ DOM فعلياً؟

غالبًا ما يسأل مسؤول المقابلة: **"عندما نمرر عنصرًا بـ `slot="username"` هل ينتقل هذا العنصر فعلياً بداخل الـ Shadow DOM ومستند الـ DOM الداخلي؟"**

**الإجابة الحاسمة:**

- **لا، لا ينتقل ولا يُعاد ترتيبه في شجرة الـ DOM حقيقة!**
- العنصر يظل موجوداً شجرياً ومكانياً في الـ **Light DOM الأصلي** للمستند.
- ما يفعله المتصفح هو عملية **"عرض بصري فقط" (Visual Projection)**؛ حيث يقوم محرك الرندر بإسقاط وتوجيه الصورة البصرية للعنصر لتبدو وكأنها مستقرة داخل الـ Shadow DOM في تلك البقعة، بينما يحتفظ العنصر بسياق الأحداث (Events) وأنماط CSS القادمة من الصفحة الرئيسية.

#### الكلمات المفتاحية للحفظ (Keywords):

- **Content Projection:** التمرير والإسقاط للمحتوى من الخارج للداخل.
- **Light DOM vs Shadow DOM:** الفرق بين المستند الأصلي والمكون المعزول.
- **Named Slots vs Default Slot:** الشرائح المعنونة مقابل الشرائح العامة.
- **`::slotted()` Pseudo-element:** محدد CSS الخاص بتنسيق عناصر الـ Slot.

#### جملتك النموذجية في المقابلة:

> **"The `<slot>` element serves as a placeholder inside a Web Component’s Shadow DOM that enables content projection from the outer Light DOM. Developers can utilize a Default Slot for capturing general children, or Named Slots (`<slot name="...">`) matched with the `slot="..."` attribute on outer elements for precise placement. Notably, slotted elements are only visually projected into the Shadow DOM tree without actually moving nodes in the DOM. These elements can be styled from within the Shadow DOM using the `::slotted()` CSS pseudo-element**
>