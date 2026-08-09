# HTML SEO & Social Metadata

## 12.1 Heading Hierarchy
## 12.2 Structured Data
## 12.3 Social Metadata

# Browser Rendering

## 13.1 HTML Parser
## 13.2 DOM
## 13.3 Render Tree    


# الفصل الثاني عشر

# HTML SEO & Social Metadata

## 12.1 Heading Hierarchy

يشمل:

- `<h1>`
- `<h2>`
- `<h3>`
- `<h4>`
- `<h5>`
- `<h6>`
- Heading Structure
- SEO & Accessibility

---

# السؤال الاول

## What is heading hierarchy in HTML, and why is it important for SEO and accessibility?

### لإجابة

> Heading hierarchy is the structured organization of HTML headings from `<h1>` to `<h6>`. It communicates the structure and hierarchy of the page's content to users, search engines, and assistive technologies.
> 

بمعنى أبسط:

العناوين ليست مجرد **حجم خط**.

هي تمثل **هيكل المحتوى**.

---

# 1. `<h1>`

يمثل العنوان الرئيسي للصفحة أو القسم ذي الصلة.

```
<h1>Frontend Interview Handbook</h1>
```

مثلاً في صفحة منتج:

```
<h1>Elegant Evening Dress</h1>
```

---

# 2. `<h2>`

يمثل قسمًا رئيسيًا داخل الصفحة.

```
<h1>Frontend Interview Handbook</h1><h2>HTML</h2><h2>CSS</h2><h2>JavaScript</h2>
```

هنا:

```
h1
├── h2 HTML
├── h2 CSS
└── h2 JavaScript
```

---

# 3. `<h3>`

يمثل قسمًا فرعيًا داخل `<h2>`.

```
<h2>HTML</h2><h3>Forms</h3><h3>Semantic HTML</h3><h3>Accessibility</h3>
```

الهيكل:

```
h1
└── h2 HTML
    ├── h3 Forms
    ├── h3 Semantic HTML
    └── h3 Accessibility
```

---

# 4. `<h4>`

يستخدم عندما تحتاج إلى مستوى إضافي داخل `<h3>`.

```
<h3>Forms</h3><h4>Input Elements</h4><h4>Validation</h4>
```

---

# 5. `<h5>`

مستوى فرعي داخل `<h4>`.

```
<h4>Input Elements</h4><h5>Text Inputs</h5><h5>Numeric Inputs</h5>
```

---

# 6. `<h6>`

أعمق مستوى من مستويات العناوين.

```
<h5>Text Inputs</h5><h6>Input Attributes</h6>
```

عمليًا، معظم صفحات الويب لن تحتاج إلى الوصول إلى `<h6>`.

---

# أهم قاعدة

## لا تختاري Heading بناءً على حجمه!

خطأ:

> "أريد عنوانًا كبيرًا، إذن سأستخدم `<h1>`."
> 

هذا ليس الهدف من الـ headings.

الحجم يمكن التحكم فيه باستخدام CSS:

```
h2 {
    font-size:32px;
}
```

إذن:

```
HTML → يحدد معنى وهيكل العنوان
CSS  → يحدد شكله وحجمه
```

---

# Heading Structure

تخيلي صفحة Product:

```
<h1>Elegant Evening Dress</h1>

    <h2>Product Details</h2>

        <h3>Material</h3>

        <h3>Size</h3>

        <h3>Color</h3>

    <h2>Reviews</h2>

        <h3>Customer Reviews</h3>

    <h2>Related Products</h2>
```

هذا هيكل منطقي:

```
h1
│
├── h2
│   ├── h3
│   └── h3
│
├── h2
│   └── h3
│
└── h2
```

---

# هل يجب أن تكون المستويات متتالية دائمًا؟

هنا توجد نقطة مهمة جدًا للمقابلات.

ليس معنى Heading Hierarchy أنك **ممنوعة تمامًا** من الانتقال من:

```
<h2>
```

إلى:

```
<h4>
```

لكن من الأفضل أن يكون الهيكل **منطقيًا ومتسقًا**.

مثال جيد:

```
<h1>Products</h1><h2>Dresses</h2><h3>Evening Dresses</h3>
```

أما:

```
<h1>Products</h1><h4>Dresses</h4>
```

فهذا يجعل العلاقة الهيكلية أقل وضوحًا.

---

# هل يجب أن يكون هناك `<h1>` واحد فقط؟

هذه من الأسئلة القديمة المشهورة.

الإجابة الحديثة:

**لا توجد قاعدة HTML تمنع وجود أكثر من `<h1>`.**

لكن في أغلب الصفحات، وجود **عنوان رئيسي واضح واحد** يجعل بنية الصفحة أسهل للفهم.

مثلاً:

```
<h1>Women's Dresses</h1><section><h2>Evening Dresses</h2></section><section><h2>Casual Dresses</h2></section>
```

هذا هيكل ممتاز.

---

# SEO

محركات البحث تستخدم العناوين لفهم **بنية ومحتوى الصفحة**.

مثلاً:

```
<h1>Women's Evening Dresses</h1><h2>Long Dresses</h2><h2>Short Dresses</h2><h2>Designer Dresses</h2>
```

هذا يعطي سياقًا أوضح للمحتوى.

لكن مهم جدًا:

> **Headings ليست وسيلة سحرية لتحسين ترتيب الصفحة في Google.**
> 

SEO يعتمد على عوامل كثيرة، والـ headings تساعد في فهم المحتوى، لكنها ليست وحدها عامل الترتيب.

---

# Accessibility

وهنا الـ Heading Hierarchy تصبح أكثر أهمية.

مستخدم الـ Screen Reader يمكنه التنقل بين العناوين بدل قراءة الصفحة كاملة.

مثلاً:

```
H1 — Product Details

H2 — Description

H2 — Specifications

H2 — Reviews

H3 — Customer Reviews
```

فيستطيع المستخدم فهم بنية الصفحة بسرعة.

---

# مثال سيئ

```
<h1>Product</h1><h4>Description</h4><h2>Reviews</h2><h6>Customers</h6>
```

المشكلة ليست أن HTML لن يعمل.

المشكلة أن **الهيكل غير منطقي**.

---

# مثال أفضل

```
<h1>Product</h1><h2>Description</h2><h2>Reviews</h2><h3>Customer Reviews</h3>
```

---

# Headings vs `<div>`

خطأ شائع:

```
<divclass="heading">
    Product Details</div>
```

حتى لو جعلناه شكله مثل:

```
PRODUCT DETAILS
```

فهو لا يحمل معنى Heading.

الأفضل:

```
<h2>Product Details</h2>
```

ثم CSS لتحديد الشكل.

---

# أشهر أسئلة المقابلات

### What is the purpose of heading elements?

> They define the hierarchical structure of content on a page.
> 

---

### How many heading levels does HTML provide?

**6**

من:

```
<h1>
```

إلى:

```
<h6>
```

---

### Is `<h1>` only used for styling?

❌ لا.

هو عنصر دلالي يمثل عنوانًا رئيسيًا.

---

### Can you have multiple `<h1>` elements?

نعم، HTML لا يمنع ذلك، لكن في الصفحة المعتادة يُفضّل وجود عنوان رئيسي واضح يساعد على فهم المحتوى.

---

### Should you choose headings based on font size?

❌ No.

> Choose headings based on semantic hierarchy, then use CSS for visual styling.
> 

---

### Why are headings important for accessibility?

> They provide a navigable structure that helps screen-reader users understand and move through the page.
> 

---

### Do headings directly guarantee better SEO rankings?

❌ No.

> Proper headings help search engines understand page structure and content, but they do not guarantee higher rankings.
> 

---

# Best Practices

### ✅ استخدمي Heading بناءً على المعنى

وليس الحجم.

### ✅ حافظي على هيكل منطقي

```
h1
 ├── h2
 │    ├── h3
 │    └── h3
 └── h2
```

### ✅ استخدمي CSS للمظهر

لا تختاري `<h1>` لأنك تريدين Font Size أكبر.

### ✅ اجعلي العنوان واضحًا

بدل:

```
<h2>Click Here</h2>
```

استخدمي:

```
<h2>Customer Reviews</h2>
```

---

# Senior Notes

## 1. Heading hierarchy ليست مجرد قاعدة SEO

هي جزء من:

**Semantic HTML + Accessibility + SEO**

وهذه نقطة مهمة جدًا.

---

## 2. لا تبني الـ headings بناءً على التصميم

لو التصميم:

```
عنوان كبير
عنوان صغير
عنوان كبير
```

هذا لا يعني:

```
<h1><h3><h1>
```

المفروض أن تحددي **الهيكل الدلالي أولًا**، ثم تجعلي التصميم مطابقًا له باستخدام CSS.

---

## 3. `<section>` وHeading مرتبطان

إذا كنتِ تبنين:

```
<section><h2>Reviews</h2></section>
```

فالعنوان يوضح موضوع هذا القسم.

وهذا يجعل:

**Semantic Structure**

أوضح بكثير من:

```
<div><div>Reviews</div></div>
```

---

# 🎯 الخلاصة

احفظيها بهذه الطريقة:

```
<h1>
    Main Page Topic
        ↓
<h2>
    Major Section
        ↓
<h3>
    Subsection
        ↓
<h4>
    Sub-subsection
        ↓
<h5>
        ↓
<h6>
```

والقاعدة الذهبية:

> **HTML headings define content hierarchy; CSS defines visual appearance.**
> 

# 12.1 هرمية العناوين في HTML (`Heading Hierarchy`)

### مثال الكود:

HTML

```
<!DOCTYPE html>
<html lang="ar">
<head>
  <meta charset="UTF-8">
  <title>Heading Hierarchy Example</title>
</head>
<body>

  <!-- 1. العنوان الرئيسي الوحيد للصفحة (Page Title) -->
  <h1>دليل تعلم تطوير الواجهات الأمية (Frontend Development)</h1>

  <main>
    <!-- 2. القسم الأول: موضوع رئيسي فرعي -->
    <section>
      <h2>1. أساسيات لغة HTML</h2>
      <p>تعتبر HTML الهيكل البنائي الأساسي لجميع صفحات الويب...</p>

      <!-- 3. تفرع فرعي من h2 -->
      <h3>1.1 العناصر الدلالية (Semantic HTML)</h3>
      <p>تساعد العناصر الدلالية في تحسين محركات البحث...</p>

      <h3>1.2 إمكانية الوصول (Accessibility)</h3>
      <p>تضمن وصول جميع المستخدمين للمحتوى بسهولة...</p>
    </section>

    <!-- 4. القسم الثاني: موضوع رئيسي فرعي آخر -->
    <section>
      <h2>2. تنسيقات CSS</h2>
      <p>تُستخدم CSS لإضافة التنسيقات والجماليات...</p>

      <h3>2.1 نظام Flexbox</h3>
      <!-- تفرع أكثر عمقاً من h3 -->
      <h4>2.1.1 محاذاة العناصر (Alignment)</h4>
      <p>طريقة التحكم في محاذاة الأبناء...</p>
    </section>
  </main>

</body>
</html>
```

### السؤال:

**ما هي هرمية العناوين في HTML، ولماذا هي مهمة لتحسين محركات البحث (SEO) وإمكانية الوصول (Accessibility)؟**

*(بالإنجليزي: What is heading hierarchy in HTML, and why is it important for SEO and accessibility?)*

### الإجابة النموذجية للمقابلة (Interview Answer):

> **هرمية العناوين (Heading Hierarchy) هي الهيكل الترتيبي المنطقي للمحتوى الذي يتم التعبير عنه بوسوم العناوين من `<h1>` إلى `<h6>`:**
> 
> - **مفهوم الهرمية:** يعبر `<h1>` عن العنوان الرئيسي للصفحة، وتأتي الوسوم من `<h2>` إلى `<h6>` لتُمثل الأقسام والتفريعات الأكثر تخصيصاً بالترتيب التنازلي دون تخطي للمستويات (Don't skip levels).
> - **الأهمية لـ SEO:** تعتمد محركات البحث (مثل Google Crawlers) على هذا الهيكل لفهم الموضوع الأساسي للصفحة، شبكة علاقات الأفكار، والكلمات المفتاحية الموزعة دلالياً.
> - **الأهمية لـ Accessibility:** تستخدم قارئات الشاشة (Screen Readers) العناوين كمؤشر تنقل رئيسي (Navigation Map) يتيح للمكفوفين القفز المباشر بين أقسام الصفحة بضغطة زر.

### الشرح بالتفصيل:

وسوم العناوين ليست مجرد نصوص كبيرة أو عريضة (Bold Text)، بل هي **وسوم دلالية هيكلية (Semantic Structural Elements)** تُشكل الجدول المرجعي (Table of Contents) لأي صفحة ويب.

#### 1. القواعد الذهبية لبناء الهرمية السليمة

- **قاعدة الـ `<h1>` الوحيد:** يجب أن تحتوي الصفحة على **`<h1>` واحد فقط** يعبر عن عنوان أو موضوع الصفحة الرئيسي. (استثناء نادر: المكونات المعزولة في HTML5، ولكن الممارسة الأفضل عالمياً هي `<h1>` واحد لكل صفحة).
- **التسلسل المنطقي (No Level Skipping):** لا تجعل التسلسل ينط من `<h2>` مباشرة إلى `<h4>` فقط لأن حجم الخط في `<h4>` يناسب التصميم.
- **الفصل التام عن الشكل (Decoupling Content from Styling):** يُحدد وسم العنوان **المعنى والدلالة فقط**، بينما يتم التحكم في الحجم واللون والشكل بالكامل عن طريق **CSS**.

#### 2. الأهمية بالنسبة لمحركات البحث (SEO Impact)

- **فهم بنية الصفحة (Content Outline):** تقوم عناكب البحث بتحليل العناوين لمعرفة أي الأجزاء تمثل أفكاراً رئيسية وأيها تفاصيل فرعية.
- **استخلاص مقتطفات البحث الممتازة (Featured Snippets):** عندما يبحث المستخدم عن سؤال، تقوم Google أحياناً بإنشاء قائمة إجابة سريعة تلقائياً في صفحة النتائج بالاعتماد المباشر على تسلسل الـ `<h2>` والـ `<h3>` في موقعك.
- **توزيع الكلمات المفتاحية (Keyword Weight):** تعطي محركات البحث وزناً أعمق للكلمات الموجودة داخل وسوم العناوين مقارنة بالنصوص العادية داخل `<p>`.

#### 3. الأهمية بالنسبة لإمكانية الوصول (Accessibility & Screen Readers)

- **شجرة التنقل (Heading Navigation):** مستخدمو قارئات الشاشة (مثل NVDA أو JAWS) لا يقرؤون الصفحة من الأعلى للأسفل كلمة بكلمة. بدلاً من ذلك، يستخدمون اختصار لوحة المفاتيح **(زر H)** لعرض قائمة العناوين والقفز فوراً للقسم الذي يهمهم.
- **إدراك العلاقات:** عند الانتقال من `<h2>` إلى `<h3>` يستوعب المستخدم الكفيف أن المحتوى الحالي هو جزء فرعي تابع للقسم السابق مباشرة.

#### 4. فخ المقابلة الشهير: تكبير النص بدلاً من استخدام وسوم العناوين

غالباً ما يسأل مسؤول المقابلة: **"إذا أردت جعل عنوان فرعي يبدو بحجم صغير، هل أستخدم `<p class="title">` بدلاً من `<h3>` لتجنب التنسيق الافتراضي؟"**

**الإجابة الحاسمة:**

- **خطأ جسيم!** استخدام `<p>` أو `<div>` وتكبيره بـ CSS يحرم قارئات الشاشة ومحركات البحث من معرفة أن هذا النص يمثل عنواناً، مما يدمر الـ SEO والـ Accessibility.
- **الحل الصحيح:** استخدم وسم العنوان الدلالي الصحيح بناءً على مكانه في الهرمية (مثلاً `<h3>`)، ثم عدّل حجمه ولونه كما تشاء في ملف الـ CSS باستخدام `font-size`.

#### الكلمات المفتاحية للحفظ (Keywords):

- **Document Outline:** المخطط الهيكلي العام للمستند.
- **No Level Skipping:** عدم تخطي مستويات العناوين.
- **Screen Reader Navigation Map:** خريطة تنقل قارئات الشاشة بضغطة زر.
- **Semantic Meaning vs CSS Styling:** الفصل بين الدلالة البرمجية والتنسيق البصري.

#### جملتك النموذجية في المقابلة:

> **"Heading hierarchy in HTML establishes a logical document outline using tags from `<h1>` to `<h6>`. It is crucial for SEO because search engine crawlers rely on it to parse the page's core structure and semantic relationship between topics. For accessibility, it acts as a primary navigation system for screen reader users, who jump through headings to explore content. We should strictly avoid skipping heading levels and must always separate semantic structure from visual styling—using CSS for size adjustments rather than picking an incorrect heading tag for design reasons**
> 

## 12.2 Structured Data

يشمل:

- Structured Data
- Schema.org
- JSON-LD
- الاستخدامات
- Rich Results

---

# السؤال الثاني

## What is Structured Data, and how does JSON-LD help search engines understand web pages?

### الإجابة

> Structured Data is a standardized way of describing the meaning and properties of content on a webpage so that search engines can better understand it. Schema.org provides commonly used vocabulary, while JSON-LD is a format that can be used to express this structured information.
> 

بمعنى أبسط:

بدل أن يرى محرك البحث:

```
iPhone 16
$999
In Stock
```

فقط كنصوص داخل الصفحة، يمكننا إعطاؤه معلومات منظمة تقول:

```
This is a Product.
Its name is iPhone 16.
Its price is 999.
Its availability is In Stock.
```

---

# 1. ما هو Structured Data؟

Structured Data هو **بيانات منظمة تصف محتوى الصفحة ومعناه** بطريقة يمكن للآلات ومحركات البحث فهمها.

مثلاً صفحة منتج يمكن أن تحتوي على:

```
Product
├── name
├── image
├── description
├── brand
├── offers
│   ├── price
│   └── availability
└── aggregateRating
```

وهذا مختلف عن مجرد كتابة المعلومات كنص عادي.

---

# 2. Schema.org

## ما هو Schema.org؟

> Schema.org is a shared vocabulary for describing entities and their properties on web pages.
> 

يعني Schema.org يوفر لنا **Vocabulary** جاهزًا.

مثل:

```
Product
Article
Recipe
Event
Organization
Person
LocalBusiness
Review
```

وكل نوع لديه خصائص مناسبة.

مثلاً:

```
Product
 ├── name
 ├── image
 ├── brand
 ├── offers
 └── aggregateRating
```

---

# 3. JSON-LD

## ما هو JSON-LD؟

> JSON-LD (JavaScript Object Notation for Linked Data) is a JSON-based format used to express structured data.
> 

مثال:

```
<scripttype="application/ld+json">
{"@context":"https://schema.org","@type":"Product","name":"Elegant Evening Dress","description":"A long evening dress.","offers": {"@type":"Offer","price":"1500","priceCurrency":"EGP"
  }
}</script>
```

لاحظي أن:

```
"@context":"https://schema.org"
```

يحدد الـ vocabulary المستخدم.

بينما:

```
"@type":"Product"
```

يحدد نوع الـ entity.

---

# 4. لماذا JSON-LD مهم؟

لأنه يسمح لنا بفصل **Structured Data** عن الـ HTML المرئي.

يعني يمكن أن يكون عندك:

```
<h1>Elegant Evening Dress</h1><p>Beautiful evening dress...</p>
```

ثم تضيفين:

```
<scripttype="application/ld+json">
...</script>
```

لتمثيل البيانات المنظمة.

---

# 5. لماذا نستخدم JSON-LD؟

لأنه:

- سهل القراءة.
- مبني على JSON.
- يمكن وضعه داخل `<script>`.
- لا يحتاج إلى إضافة Attributes كثيرة إلى عناصر HTML.
- مناسب جدًا لإضافة Structured Data بشكل منفصل عن الـ UI.

---

# 6. استخدامات Structured Data

يمكن استخدام Structured Data لوصف أنواع مختلفة من المحتوى.

### Product

```
Product
Price
Availability
Rating
```

مفيد لمواقع:

- E-commerce
- Product Catalogs

---

### Article

```
Article
Headline
Author
Date Published
Image
```

مفيد لـ:

- Blogs
- News Websites
- Editorial Content

---

### Recipe

```
Recipe
Ingredients
Cooking Time
Rating
Calories
```

---

### Event

```
Event
Name
Date
Location
```

---

### Organization

```
Organization
Name
Logo
URL
```

---

# 7. Rich Results

هذه نقطة مهمة جدًا.

## ما هي Rich Results؟

> Rich Results are enhanced search results that may display additional information beyond the standard title, URL, and description.
> 

بدل نتيجة بحث عادية:

```
Elegant Evening Dress
example.com
Beautiful evening dress...
```

قد تظهر معلومات إضافية مثل:

```
Elegant Evening Dress

★★★★★
4.8

EGP 1,500

In stock
```

بحسب نوع المحتوى وأهلية الصفحة ومتطلبات محرك البحث.

---

# العلاقة بين Structured Data وRich Results

احفظيها بهذا الشكل:

```
Structured Data
       ↓
يساعد محرك البحث على فهم المحتوى
       ↓
Search Engine evaluates eligibility
       ↓
Possible Rich Result
```

لكن:

> **Structured Data does NOT guarantee a Rich Result.**
> 

هذه نقطة مهمة جدًا في المقابلات.

---

# 8. هل Structured Data يؤثر مباشرة على Ranking؟

لا نقول:

> "أضفت JSON-LD إذن Google سيرفع ترتيبي."
> 

هذا غير صحيح.

الأصح:

> Structured Data helps search engines understand the content and can make pages eligible for certain enhanced search features, but it does not guarantee higher rankings or Rich Results.
> 

---

# 9. مثال حقيقي لمنتج

تخيلي متجرًا:

```
Elegant Evening Dress
★★★★★ 4.8
EGP 1,500
In Stock
```

يمكن تمثيله Structured Data تقريبًا هكذا:

```
<scripttype="application/ld+json">
{"@context":"https://schema.org","@type":"Product","name":"Elegant Evening Dress","image": ["https://example.com/dress.jpg"
  ],"description":"Elegant evening dress.","offers": {"@type":"Offer","price":"1500","priceCurrency":"EGP","availability":"https://schema.org/InStock"
  }
}</script>
```

لاحظي أن هذه البيانات **تصف المنتج**، لكنها لا تستبدل المحتوى الظاهر للمستخدم.

---

# 10. هل يجب أن يكون Structured Data مطابقًا للمحتوى الظاهر؟

نعم، وهذه نقطة مهمة جدًا.

لا تضعي Structured Data لمعلومات غير موجودة أو غير صحيحة على الصفحة.

مثلاً إذا الصفحة تقول:

```
EGP 1,500
```

لا تضعي في Structured Data:

```
"price":"500"
```

أو معلومات غير معروضة للمستخدم.

البيانات المنظمة يجب أن تعكس المحتوى الحقيقي للصفحة.

---

# أشهر أسئلة المقابلات

### What is Structured Data?

> It is a standardized way of describing the meaning and properties of webpage content so that search engines can better understand it.
> 

---

### What is Schema.org?

> Schema.org provides a shared vocabulary for describing entities and their properties using structured data.
> 

---

### What is JSON-LD?

> JSON-LD is a JSON-based format used to represent structured data.
> 

---

### What is the relationship between Schema.org and JSON-LD?

> Schema.org provides the vocabulary, while JSON-LD is one format used to express that vocabulary.
> 

مثال:

```
Schema.org
    ↓
Vocabulary

JSON-LD
    ↓
Representation Format
```

---

### Does Structured Data guarantee Rich Results?

❌ No.

> It can make eligible content understandable to search engines and eligible for certain rich result features, but it does not guarantee that they will be displayed.
> 

---

### Does Structured Data guarantee better rankings?

❌ No.

---

### Why is JSON-LD commonly used?

> Because it provides a clean, machine-readable way to express structured data without mixing it heavily into the visible HTML markup.
> 

---

# Best Practices

### ✅ استخدمي Schema.org vocabulary

بدل اختراع properties خاصة بك.

### ✅ اجعلي البيانات دقيقة

يجب أن تعكس المحتوى الحقيقي.

### ✅ استخدمي النوع المناسب

مثلاً:

```
Product
```

للمنتج، وليس:

```
Article
```

### ✅ لا تضيفي Structured Data لمجرد إضافتها

استخدميها عندما يكون نوع المحتوى مناسبًا ومفيدًا.

### ✅ اختبري Structured Data

قبل إطلاق الصفحة، يجب التأكد من أن الـ markup صحيح وأنه يطابق متطلبات محرك البحث المستهدف.

---

# Senior Notes

## 1. Schema.org ≠ JSON-LD

هذه من أهم النقاط:

```
Schema.org
     =
Vocabulary
```

بينما:

```
JSON-LD
     =
Format
```

مثلًا:

```
"@type":"Product"
```

الـ `Product` هنا من vocabulary الخاص بـ Schema.org.

---

## 2. JSON-LD ليس JavaScript Application Code

رغم أن:

```
<scripttype="application/ld+json">
```

موجود داخل `<script>`، فهو ليس JavaScript يتم تنفيذه كتطبيق.

إنه JSON-LD data مخصصة لوصف البيانات المنظمة.

---

## 3. Structured Data لا يغني عن Semantic HTML

لا تقولي:

> "سأضع JSON-LD وأستغني عن `<h1>`, `<article>`, `<nav>`..."
> 

لا.

كل واحد له وظيفة مختلفة:

```
Semantic HTML
      ↓
بنية ومعنى الصفحة للمستخدم والمتصفح وAccessibility

Structured Data
      ↓
وصف منظم للمحتوى للآلات ومحركات البحث
```

ويعملان معًا.

---

# 🎯 الخلاصة

احفظي العلاقة بهذه الصورة:

```
Web Page
   │
   ├── Semantic HTML
   │       ↓
   │   Page Structure
   │
   └── Structured Data
           ↓
       Schema.org
           ↓
        JSON-LD
           ↓
    Search Engine Understanding
           ↓
      Possible Rich Results
```

وأهم جملة في هذا القسم:

> **Schema.org provides the vocabulary, JSON-LD provides the format, and Structured Data helps search engines understand the content and may make eligible pages available for Rich Results**
> 

# 12.2 البيانات المنظمة بـ Schema.org و JSON-LD (`Structured Data & JSON-LD`)

### مثال الكود:

HTML

```
<!DOCTYPE html>
<html lang="ar">
<head>
  <meta charset="UTF-8">
  <title>وظيفة مطور واجهات أمامية - مثال البيانات المنظمة</title>

  <!-- إدراج البيانات المنظمة بصيغة JSON-LD داخل وسوم <script> في الـ <head> -->
  <script type="application/ld+json">
  {
    "@context": "https://schema.org",
    "@type": "JobPosting",
    "title": "مطور واجهات أمامية (Frontend Developer)",
    "description": "نبحث عن مطور واجهات إحترافي يجيد التعامل مع HTML5, CSS3, و JavaScript...",
    "datePosted": "2026-08-01",
    "validThrough": "2026-09-01",
    "employmentType": "FULL_TIME",
    "hiringOrganization": {
      "@type": "Organization",
      "name": "شركة التقنية الحديثة",
      "sameAs": "https://example.com"
    },
    "jobLocation": {
      "@type": "Place",
      "address": {
        "@type": "PostalAddress",
        "addressLocality": "القاهرة",
        "addressCountry": "EG"
      }
    },
    "baseSalary": {
      "@type": "MonetaryAmount",
      "currency": "USD",
      "value": {
        "@type": "QuantitativeValue",
        "value": 3000,
        "unitText": "MONTH"
      }
    }
  }</script>
</head>
<body>
  <h1>وظيفة: مطور واجهات أمامية</h1>
  <p>تفاصيل الوظيفة المعروضة للمستخدمين بالصفحة...</p>
</body>
</html>
```

### السؤال:

**ما هي البيانات المنظمة (Structured Data)، وكيف يساهم استخدام صيغة JSON-LD في مساعدة محركات البحث على فهم صفحات الويب؟**

*(بالإنجليزي: What is Structured Data, and how does JSON-LD help search engines understand web pages?)*

### الإجابة النموذجية للمقابلة (Interview Answer):

> **البيانات المنظمة (Structured Data) هي طريقة معيارية لتزويد محركات البحث بمعلومات وتفاصيل صريحة ومصنفة حول محتوى الصفحة باستخدام قاموس موحد يُعرف بـ Schema.org:**
> 
> - **مفهوم Structured Data:** تقوم بتحويل النص العادي بالصفحة إلى بيانات تفهمها الآلة (Machine-Readable Context)؛ مما يسمح لمحركات البحث بإدراك نوع المحتوى بشكل قاطع (هل الصفحة عبارة عن منتج، مقال، وصفة طعام، وظيفة، أو تقييم؟).
> - **دور JSON-LD:** يُعتبر الصيغة المعيارية الموصى بها رسمياً من Google لكتابة البيانات المنظمة. يرمز لـ *JavaScript Object Notation for Linked Data*، ويتميز بأنه يُكتب ككائن JSON خفيف ومستقل داخل كود `<script type="application/ld+json">` في الـ `<head>`، مما يفصل البيانات تماماً عن هيكل HTML والتنسيق البصري دون التأثير على أداء الصفحة.
> - **النتيجة (Rich Results):** تحويل النتيجة العادية في محرك البحث إلى "نتيجة غنية" تحتوي على نجوم التقييم، الأسعار، صور المنتجات، أو تفاصيل الوظائف فوراً بصفحة النتائج (SERP).

### الشرح بالتفصيل:

محركات البحث ذكية جداً، ولكن عندما تقرأ نصاً مثل "بيتزا بـ 50 ريال"، فهي تحتاج لتخمين السياق. **البيانات المنظمة** تزيل هذا التخمين عبر استخدام تصنيفات متفق عليها بين المحركات الكبرى (Google, Bing, Yahoo) عبر منظمة **Schema.org**.

#### 1. القاموس المعياري: Schema.org

هو المكتبة الشاملة التي تحتوي على المفردات وأنواع البيانات القياسية، مثل:

- **`Article` / `BlogPosting`:** للمقالات والأخبار.
- **`Product`:** للمنتجات التجارية (يتضمن السعر `price` والتوافر `availability`).
- **`Recipe`:** لوصفات الطعام (وقت الطهي، السعرات الحرارية).
- **`JobPosting`:** لإعلانات الوظائف.
- **`FAQPage`:** لصفحات الأسئلة الشائعة.

#### 2. لماذا نفضل JSON-LD على الصيغ القديمة (Microdata / RDFa)؟

قبل ظهور JSON-LD، كان المطورون يضطرون لتطعيَم عناصر الـ HTML نفسها بخصائص مخصصة مثل `itemscope` و `itemprop` (Microdata).

| **وجه المقارنة** | **Microdata / RDFa** | **JSON-LD** |
| --- | --- | --- |
| **مكان الكود** | مدمج ومشتت داخل وسوم الـ HTML بالـ Body | متمركز في مكان واحد داخل كود `<script>` بالـ Head |
| **سهولة الصيانة** | صعبة؛ أي تعديل بالـ UI قد يكسر البيانات المنظمة | سهلة جداً؛ الكود منفصل تماماً عن التصميم البصري |
| **التأثير على الأداء** | قد يزيد تعقيد الـ DOM Parsing | خفيف جداً ويتم تحليله بسرعة عبر محركات البحث |
| **توصية Google** | مدعومة ولكن لا يُنصح بها | **التوصية الرسمية الأولى والأفضل (Gold Standard)** |

#### 3. النتائج الغنية (Rich Results / Rich Snippets)

عندما توفر بيانات منظمة صحيحة، يمنحك محرك البحث مظهرًا استثنائيًا في نتائج البحث:

- **بطاقات التقييم:** إظهار التقييم بالنجوم (⭐️⭐️⭐️⭐️⭐️) وعدد المراجعين تحت رابط الموقع.
- **بطاقات المنتجات:** عرض سعر المنتج وحالة التوفر (In Stock) مباشرة في نتيجة البحث.
- **Breadcrumbs:** إظهار المسار الهيكلي للمقال/الصفحة بشكل منظم أعلى العنوان.

#### 4. فخ المقابلة الشهير: حشو البيانات والبيانات المخادعة (Spammy Structured Data)

غالباً ما يسأل مسؤول المقابلة: **"هل يمكننا إضافة JSON-LD يحتوي على معلومات لا تظهر للمستخدم في الصفحة لرفع التقييمات في Google؟"**

**الإجابة الحاسمة:**

- **خطأ جسيم يعرض الموقع للعقوبات (Manual Action Penalties)!**
- تشترط سياسات Google الشديدة أن تكون البيانات المكتوبة داخل JSON-LD **مطابقة تماماً** للمحتوى المرئي الذي يستطيع المستخدم العادي قراءته بالصفحة.
- إضافة تقييمات وهمية أو أسعار غير موجودة في الـ HTML الرئيسي تُصنف كـ **Structured Data Spam**، وتؤدي لحرمان الموقع كاملاً من إمكانية الظهور بـ Rich Results.

#### الكلمات المفتاحية للحفظ (Keywords):

- **Machine-Readable Context:** محتوى مفهوم برمجياً للآلة وليس للقيم البصرية فقط.
- **Schema.org Vocabulary:** القاموس الموحد المعترف به عالمياً لتصنيف البيانات.
- **JSON-LD (`application/ld+json`):** التنسيق البرمجي المنفصل والموصى به من Google.
- **Rich Results (Rich Snippets):** النتيجة التفاعلية المتميزة على صفحة نتائج محرك البحث (SERP).

#### جملتك النموذجية في المقابلة:

> **"Structured Data is a standardized format powered by Schema.org vocabularies that explicitly conveys page content semantics to search engines. JSON-LD (JavaScript Object Notation for Linked Data) is Google's strongly recommended implementation method. It encapsulates structured data within a clean, standalone `<script type="application/ld+json">` block, decoupling search semantics from presentation-layer HTML. Implementing JSON-LD enables search engines to effortlessly render Rich Results (like star ratings, prices, or job details) directly on SERPs without degrading DOM performance or maintainability**
> 

## 12.3 Social Metadata

يشمل:

### Open Graph

- `og:title`
- `og:description`
- `og:image`
- `og:url`
- `og:type`

### Twitter/X Cards

- `twitter:card`
- `twitter:title`
- `twitter:description`
- `twitter:image`

---

# السؤال الثالث

## What are Open Graph and Twitter/X Card meta tags, and why are they used?

### الإجابة

> Open Graph and Twitter/X Card metadata control how a webpage is represented when its URL is shared on social media and messaging platforms.
> 

بمعنى أبسط:

عندما شخص يشارك:

```
https://example.com/product
```

على منصة اجتماعية، أنت لا تريد أن تظهر مجرد:

```
example.com
```

بل تريد أن يظهر:

```
┌──────────────────────────────┐
│                              │
│        Product Image         │
│                              │
├──────────────────────────────┤
│ Elegant Evening Dress        │
│ Beautiful evening dress...   │
│ example.com                  │
└──────────────────────────────┘
```

وهنا يأتي دور **Social Metadata**.

---

# 1. Open Graph

Open Graph هو معيار للـ metadata يسمح لك بتحديد كيف يتم تمثيل الصفحة عند مشاركتها.

تتم إضافته داخل:

```
<head>
```

مثال:

```
<metaproperty="og:title"content="Elegant Evening Dress"><metaproperty="og:description"content="Discover our elegant evening dress."><metaproperty="og:image"content="https://example.com/dress.jpg"><metaproperty="og:url"content="https://example.com/dresses/evening"><metaproperty="og:type"content="website">
```

لاحظي استخدام:

```
property="..."
```

بدل:

```
name="..."
```

وهذه نقطة مهمة.

---

# 2. `og:title`

يمثل عنوان الصفحة الذي يظهر عند مشاركة الرابط.

```
<metaproperty="og:title"content="Elegant Evening Dress">
```

ليس بالضرورة أن يكون نفس `<title>`، لكن غالبًا من الأفضل أن يكون متوافقًا معه.

---

# 3. `og:description`

وصف الصفحة الذي قد يظهر في Preview.

```
<metaproperty="og:description"content="Discover elegant evening dresses.">
```

يجب أن يكون:

- واضحًا.
- مختصرًا.
- مرتبطًا فعليًا بمحتوى الصفحة.

---

# 4. `og:image`

الصورة التي تستخدم في الـ Social Preview.

```
<metaproperty="og:image"content="https://example.com/images/dress.jpg">
```

وهذه من أهم الـ tags لأن الصورة غالبًا تكون الجزء الأكثر وضوحًا في Preview.

---

# 5. `og:url`

يحدد الـ URL الأساسي للصفحة التي يتم تمثيلها.

```
<metaproperty="og:url"content="https://example.com/dresses/evening">
```

مثلاً إذا كان نفس المحتوى يمكن الوصول إليه من أكثر من URL، فهذا يساعد على تحديد الرابط الذي يمثل الصفحة.

لكن لا تخلطي بينه وبين:

```
<linkrel="canonical">
```

لأنهما يؤديان وظائف مختلفة.

```
canonical
    ↓
Search Engine canonicalization

og:url
    ↓
Social sharing representation
```

---

# 6. `og:type`

يحدد نوع المحتوى.

مثلاً:

```
<metaproperty="og:type"content="website">
```

يمكن أن يكون النوع المناسب مختلفًا حسب المحتوى وحالة الاستخدام.

---

# مثال كامل

```
<head><title>Elegant Evening Dress</title><metaname="description"content="Discover elegant evening dresses."><metaproperty="og:title"content="Elegant Evening Dress"><metaproperty="og:description"content="Discover elegant evening dresses."><metaproperty="og:image"content="https://example.com/dress.jpg"><metaproperty="og:url"content="https://example.com/dresses/evening"><metaproperty="og:type"content="website"></head>
```

---

# 7. Twitter/X Cards

بالنسبة إلى X، توجد مجموعة metadata تستخدم أسماء:

```
twitter:*
```

رغم أن المنصة أصبحت X.

مثال:

```
<metaname="twitter:card"content="summary_large_image"><metaname="twitter:title"content="Elegant Evening Dress"><metaname="twitter:description"content="Discover elegant evening dresses."><metaname="twitter:image"content="https://example.com/dress.jpg">
```

---

# 8. `twitter:card`

يحدد نوع الـ Card.

مثلاً:

```
<metaname="twitter:card"content="summary_large_image">
```

من الأنواع الشائعة:

```
summary
summary_large_image
```

وأكثر ما ستشاهدينه في المشاريع:

```
summary_large_image
```

عندما تريدين Preview بصورة كبيرة.

---

# 9. `twitter:title`

عنوان الـ Card.

```
<metaname="twitter:title"content="Elegant Evening Dress">
```

---

# 10. `twitter:description`

وصف الـ Card.

```
<metaname="twitter:description"content="Discover elegant evening dresses.">
```

---

# 11. `twitter:image`

الصورة المستخدمة في Card.

```
<metaname="twitter:image"content="https://example.com/dress.jpg">
```

---

# Open Graph vs Twitter/X Cards

| Open Graph | Twitter/X Cards |
| --- | --- |
| `og:title` | `twitter:title` |
| `og:description` | `twitter:description` |
| `og:image` | `twitter:image` |
| `og:url` | — |
| `og:type` | `twitter:card` |
| تستخدم عبر منصات تدعم Open Graph | مرتبطة بتنسيق X Cards |

---

# هل يجب كتابة الاثنين؟

في المشاريع الحقيقية:

**نعم، غالبًا من الأفضل توفير الاثنين.**

مثلاً:

```
<metaproperty="og:title"content="Product Name"><metaproperty="og:description"content="Product description"><metaproperty="og:image"content="https://example.com/product.jpg"><metaproperty="og:url"content="https://example.com/product"><metaproperty="og:type"content="website"><metaname="twitter:card"content="summary_large_image"><metaname="twitter:title"content="Product Name"><metaname="twitter:description"content="Product description"><metaname="twitter:image"content="https://example.com/product.jpg">
```

هذا يعطيك تغطية أفضل للمنصات التي تعتمد هذه metadata.

---

# هل Open Graph له علاقة بـ SEO؟

هنا لازم نفرق.

**Open Graph ليس عامل SEO مباشرًا بالمعنى المعتاد.**

وظيفته الأساسية:

```
URL
 ↓
Social Platform
 ↓
Preview
```

وليس:

```
URL
 ↓
Google Ranking
```

---

# SEO Metadata vs Social Metadata

| Metadata | الهدف |
| --- | --- |
| `<title>` | عنوان الصفحة في المتصفح ومحركات البحث |
| `description` | وصف الصفحة لمحركات البحث وغيرها |
| `canonical` | تحديد النسخة الأساسية من URL |
| Open Graph | Social Preview |
| Twitter/X Cards | X Social Preview |
| JSON-LD | Structured information |

---

# مثال حقيقي في E-commerce

تخيلي عندك:

```
Product:
Elegant Evening Dress

Price:
1,500 EGP

Image:
dress.jpg
```

عند مشاركة الرابط:

```
https://store.com/products/evening-dress
```

نريد Preview مثل:

```
┌───────────────────────────────┐
│                               │
│          DRESS IMAGE          │
│                               │
├───────────────────────────────┤
│ Elegant Evening Dress         │
│ Discover our elegant...       │
│ store.com                     │
└───────────────────────────────┘
```

الـ Open Graph / X metadata هي التي تساعد المنصة على بناء هذا الـ preview.

---

# أشهر أسئلة المقابلات

### What is Open Graph?

> Open Graph is a metadata protocol used to control how web pages are represented when shared on social platforms.
> 

---

### What does `og:image` do?

> It specifies the image that can be used in the social sharing preview.
> 

---

### What is the difference between `og:title` and `<title>`?

`<title>` هو عنوان الصفحة الأساسي المستخدم في المتصفح ويمكن أن يظهر في نتائج البحث.

بينما:

```
og:title
```

يحدد العنوان المستخدم في **Social Preview**.

---

### What is `twitter:card`?

> It specifies the type of Twitter/X Card used when a URL is shared.
> 

---

### Is Open Graph an SEO ranking factor?

ليس هذا هو الغرض الأساسي منه؛ هو أساسًا **Social Sharing Metadata**.

---

### Should you use both Open Graph and Twitter/X metadata?

> Yes, when you want predictable social previews across platforms that use these metadata systems.
> 

---

# Best Practices

### ✅ استخدمي Absolute URLs للصور

بدل:

```
<metaproperty="og:image"content="/images/product.jpg">
```

يفضل:

```
<metaproperty="og:image"content="https://example.com/images/product.jpg">
```

خصوصًا لأن المنصة تحتاج إلى الوصول للصورة من خارج موقعك.

---

### ✅ استخدمي صورة مناسبة للـ Social Preview

لا تختاري صورة صغيرة أو غير مناسبة.

---

### ✅ اجعلي العنوان والوصف متوافقين مع الصفحة

لا تكتبي:

```
Best iPhone Ever!!!
```

إذا كانت الصفحة عن:

```
Women's Dresses
```

---

### ✅ اختبري Social Preview

بعد إضافة metadata، يجب اختبار كيفية ظهور الرابط عند مشاركته، لأن الـ preview قد لا يظهر بالشكل المتوقع بسبب:

- Cache
- Image accessibility
- Incorrect metadata
- URL problems
- Platform-specific behavior

---

# Senior Notes

## 1. لا تعتمدي على Open Graph كبديل لـ SEO

هذا خطأ شائع.

```
SEO
├── Semantic HTML
├── Metadata
├── Structured Data
├── Performance
└── Many other factors

Social Sharing
├── Open Graph
└── X/Twitter Cards
```

---

## 2. `og:url` ليس بديلًا عن `canonical`

هذه نقطة Interview ممتازة:

```
<linkrel="canonical"href="https://example.com/product"/>
```

هدفه الأساسي هو **Canonicalization** لمحركات البحث.

بينما:

```
<metaproperty="og:url"content="https://example.com/product"/>
```

خاص بتمثيل الصفحة في Open Graph / Social Sharing.

قد يتطابقان في القيمة، لكن **وظيفتهما مختلفة**.

---

## 3. لا تحفظي الـ tags فقط

كمطور Front-End، المهم أن تفكري:

> "لو المستخدم شارك هذه الصفحة، كيف أريد أن تظهر؟"
> 

ومن هنا تعرفين أنك تحتاجين:

```
og:title
og:description
og:image
og:url
og:type
```

ثم إذا كنتِ تستهدفين X أيضًا:

```
twitter:card
twitter:title
twitter:description
twitter:image
```

---

# 🎯 الخلاصة

الصورة الكبيرة للفصل أصبحت:

```
HTML SEO & Social Metadata
│
├── 12.1 Heading Hierarchy
│       ├── h1 → h6
│       ├── Structure
│       └── SEO + Accessibility
│
├── 12.2 Structured Data
│       ├── Schema.org
│       ├── JSON-LD
│       └── Rich Results
│
└── 12.3 Social Metadata
        ├── Open Graph
        │   ├── og:title
        │   ├── og:description
        │   ├── og:image
        │   ├── og:url
        │   └── og:type
        │
        └── Twitter/X Cards
            ├── twitter:card
            ├── twitter:title
            ├── twitter:description
            └── twitter:image
```

### والجملة التي أريدك أن تحفظيها:

> **SEO metadata helps search engines understand and represent a page, Structured Data describes the meaning of its content, while Open Graph and Twitter/X Cards control how the page is represented when shared socially**
> 

# 12.3 البيانات الوصفية لمنصات التواصل الاجتماعي (`Social Metadata`)

### مثال الكود:

HTML

```
<!DOCTYPE html>
<html lang="ar">
<head>
  <meta charset="UTF-8">
  <title>تعلم تطوير الواجهات الأمامية - كورس شامل</title>
  <meta name="description" content="دليل تعليمي متكامل لتعلم HTML, CSS, و JavaScript من الصفر حتى الاحتراف.">

  <!-- 1. بروتوكول Open Graph (خاص بـ Facebook, LinkedIn, WhatsApp, Slack, وغيرها) -->
  <meta property="og:site_name" content="أكاديمية المطورين">
  <meta property="og:type" content="article">
  <meta property="og:title" content="تعلم تطوير الواجهات الأمامية - كورس شامل 2026">
  <meta property="og:description" content="دليل تعليمي متكامل لتعلم HTML, CSS, و JavaScript من الصفر حتى الاحتراف.">
  <meta property="og:image" content="https://example.com/images/frontend-course-og.jpg">
  <meta property="og:url" content="https://example.com/courses/frontend">
  <meta property="og:locale" content="ar_AR">

  <!-- 2. بطاقات منصة Twitter / X -->
  <meta name="twitter:card" content="summary_large_image">
  <meta name="twitter:site" content="@DevelopersAcad">
  <meta name="twitter:title" content="تعلم تطوير الواجهات الأمامية - كورس شامل 2026">
  <meta name="twitter:description" content="دليل تعليمي متكامل لتعلم HTML, CSS, و JavaScript من الصفر حتى الاحتراف.">
  <meta name="twitter:image" content="https://example.com/images/frontend-course-twitter.jpg">
</head>
<body>
  <h1>دورة تطوير الواجهات الأمامية</h1>
  <p>محتوى الصفحة الفعلي للمستخدمين...</p>
</body>
</html>
```

### السؤال:

**ما هي وسوم Open Graph وبطاقات Twitter/X Meta Tags، ولماذا يُستخدمان؟**

*(بالإنجليزي: What are Open Graph and Twitter/X Card meta tags, and why are they used?)*

### الإجابة النموذجية للمقابلة (Interview Answer):

> **وسوم Open Graph و Twitter Cards هي مجموعات من وسوم الميتا (`<meta>`) تُضاف في كود الـ `<head>` للتحكم المباشر في كيفية عرض الروابط وطريقة ظهورها عند مشاركتها على منصات التواصل الاجتماعي وتطبيقات المحادثة:**
> 
> - **بروتوكول Open Graph (OG):** تم إنشاؤه بواسطة Facebook وأصبح معيارًا عالميًا تستخدمه معظم المنصات (مثل LinkedIn و WhatsApp و Slack و Discord) لتحويل الرابط إلى بطاقة تفاعلية تحتوي على صورة عنوان ووصف غني.
> - **بطاقات Twitter/X Cards:** وسوم مخصصة لمنصة X (تويتر سابقاً) لتحديد حجم وطريقة عرض البطاقة المنشورة على التايم لاين.
> - **سبب الاستخدام:** تمنع ظهور الروابط العشوائية أو الصور غير المناسبة عند المشاركة، مما يزيد بشكل مباشر من معدل النقر مقابل الظهور (**CTR - Click-Through Rate**) ويعزز احترافية العلامة التجارية.

### الشرح بالتفصيل:

عندما ينسخ مستخدم رابط موقعك ويشاركه في محادثة WhatsApp أو ينشره على LinkedIn، يقوم البوت (Crawler) التابع للمنصة بزيارة صفحتك وقراءة وسوم الـ Meta Tags ليصنع "معاينة بطاقة" (Link Preview Snippet).

#### 1. وسوم Open Graph المحددة (OG Properties)

تُكتب باستخدام الخصائص `property="og:..."` و `content="..."`:

| **الوسم** | **الوظيفة والدور** |
| --- | --- |
| **`og:title`** | العنوان الرئيسي الذي يظهر على البطاقة (يُفضل أن يكون جذاباً ومركّزاً بحدود 60 حرفاً). |
| **`og:description`** | وصف مختصر ومغري يعطي فكرة عن المحتوى (بحدود 155-200 حرف). |
| **`og:image`** | **الوسم الأكثر أهمية!** رابط الصورة المصغرة للبطاقة. |
| **`og:url`** | الرابط الدائم (Canonical URL) للصفحة المعروضة. |
| **`og:type`** | نوع المحتوى (مثل `website`, `article`, `product`, `video.other`). |

#### 2. وسوم بطاقات Twitter / X Cards

تُكتب باستخدام الخصائص `name="twitter:..."` و `content="..."`:

- **`twitter:card`:** يُحدد نمط الشكل البصري للبطاقة في منصة X. أهم أنواعه:
    - `summary_large_image`: يظهر صورة كبرى وعريضة فوق العنوان (وهو الأكثر استخداماً للمقالات والمنتجات).
    - `summary`: يظهر صورة مربعة صغيرة بجانب العنوان والنص.
- **`twitter:title` / `twitter:description` / `twitter:image`:** خصائص مطابقة لخصائص OG لضمان إتاحة التنسيق المخصص لمنصة X إذا كانت تحتاج لتصميم مغاير.

#### 3. فخ المقابلة الشهير: أبعاد الصورة المجهزة والممارسات الخاطئة

غالباً ما يسأل مسؤول المقابلة: **"ما هي المشاكل الشائعة التي تجعل صورة الـ OG لا تظهر أو تظهر بشكل مكسور أو مشوه عند مشاركة الرابط؟"**

**الإجابة الحاسمة:**

1. **الأبعاد والنسبة (Aspect Ratio & Dimensions):** الصورة المثالية لـ OG يجب أن تكون بنسبة **1.91:1** وبأبعاد قياسية موصى بها **1200 × 630 بكسل** (وبحد أدنى 600 × 315 بكسل). الصورة المربعة جدًا سيتم قصها أو عدم إظهارها بشكل جيد.
2. **روابط الصور النسبية (Relative vs Absolute URLs):** **خطأ شائع!** يجب أن يكون رابط الصورة **رابطًا مطلقًا وشاملاً (Absolute URL)** يبدأ بـ `https://` وليس رابطًا نسبيًا (مثل `/images/thumb.jpg`). البوتات لن تستطيع الوصول للصور ذات الروابط النسبية.
3. **التخزين المؤقت للمنصات (Social Caching):** تُخزن منصات مثل Facebook و X بيانات الـ OG لموقعك مؤقتًا. إذا عدلت وسوم الميتا وتريد تجديد المعاينة فورًا، يجب استخدام أدوات التطهير الرسمية مثل **Facebook Sharing Debugger** أو **Twitter Card Validator** لإجبار المنصة على مسح الـ Cache وقراءة البيانات الجديدة.

#### الكلمات المفتاحية للحفظ (Keywords):

- **Open Graph Protocol (OG):** المعيار القياسي لبطاقات المشاركة الاجتماعية من Facebook.
- **Link Preview Snippet:** المعاينة البصرية الناتجة عن المشاركة.
- **Absolute URLs for Media:** ضرورة استخدام الروابط المطلقة الكاملة لوسوم الصور.
- **`summary_large_image`:** العرض العريض الأكثر جائبية ببطاقات منصة X.

#### جملتك النموذجية في المقابلة:

> **"Open Graph and Twitter Card meta tags are specialized HTML head attributes that instruct social platforms (like Facebook, LinkedIn, X, WhatsApp, and Slack) on how to dynamically render structured link previews when a URL is shared. Open Graph (`og:title`, `og:image`, `og:description`) establishes the foundational protocol, while Twitter-specific tags (`twitter:card`) refine presentation on X. Using these tags with absolute image URLs (optimally 1200x630px) ensures professional presentation, prevents arbitrary site scraping, and dramatically increases Click-Through Rates (CTR**
> 

# 

# الفصل الثالث عشر

# Browser Rendering

يشمل:

- HTML Parser
- DOM
- Render Tree

وسنربطهم مع بعض لأن فهم العلاقة بينهم أهم من حفظ تعريف كل واحد منفصلًا.

---

# 13.1 HTML Parser

## السؤال

### What is the HTML Parser?

> The HTML Parser is the browser component responsible for reading HTML markup and converting it into a structured representation that can be used to build the DOM.
> 

بمعنى أبسط:

المتصفح يستقبل:

```
<html><body><h1>Hello</h1><p>Welcome</p></body></html>
```

ولا يتعامل معها كـ String فقط.

الـ Parser يبدأ في:

```
HTML
 ↓
Read / Parse
 ↓
Understand Tags
 ↓
Build DOM
```

---

# ماذا يفعل HTML Parser؟

عندما يصل HTML إلى المتصفح:

```
HTML Response
      ↓
HTML Parser
      ↓
DOM
```

الـ Parser يقوم بقراءة الـ HTML وتحليله وتحويله إلى بنية يستطيع المتصفح التعامل معها.

---

# مثال

HTML:

```
<body><h1>Hello</h1><p>Welcome</p></body>
```

بعد Parsing يصبح لدينا مفهوم شجري:

```
body
├── h1
│   └── "Hello"
│
└── p
    └── "Welcome"
```

وهذا هو الـ DOM Tree.

---

# نقطة مهمة

الـ HTML Parser لا يقوم بكل عملية Rendering.

لا تقولي:

> HTML Parser renders the page.
> 

الأصح:

> **The HTML Parser parses HTML and builds the DOM.**
> 

ثم هناك مراحل أخرى في عملية الـ rendering.

---

# 13.2 DOM

## السؤال

### What is the DOM?

> The DOM (Document Object Model) is a programming interface and tree representation of an HTML document that allows scripts and browser components to access and manipulate its structure and content.
> 

ببساطة:

**DOM = تمثيل الصفحة كـ Tree داخل المتصفح.**

---

# مثال

لدينا:

```
<html><body><h1>Hello</h1><p>Welcome</p></body></html>
```

الـ DOM يمكن تبسيطه إلى:

```
Document
└── html
    └── body
        ├── h1
        │   └── "Hello"
        │
        └── p
            └── "Welcome"
```

---

# لماذا DOM مهم؟

لأن JavaScript يستطيع التعامل معه.

مثلاً:

```
document.querySelector("h1");
```

أو:

```
document.querySelector("h1").textContent="Hello Hanan";
```

هنا JavaScript يتعامل مع الـ DOM.

---

# DOM ليس HTML نفسه

هذه نقطة مهمة جدًا.

الـ HTML هو:

```
Source / Markup
```

أما DOM فهو:

```
In-memory representation
```

يعني:

```
HTML
 ↓
Parser
 ↓
DOM
```

ويمكن للـ JavaScript تعديل الـ DOM دون أن يعني ذلك أن الـ original HTML source نفسه تغير.

---

# DOM Tree

مثال:

```
<div><h1>Hello</h1><p>Frontend Developer</p></div>
```

يمكن تمثيله:

```
div
├── h1
│   └── "Hello"
│
└── p
    └── "Frontend Developer"
```

كل عنصر يصبح Node في الشجرة.

---

# 13.3 Render Tree

## السؤال

### What is the Render Tree?

> The Render Tree is a representation built from the DOM and relevant CSS information that contains the nodes needed to determine what should be rendered visually.
> 

بمعنى:

ليس كل شيء موجود في DOM يجب أن يظهر على الشاشة.

لذلك المتصفح يحتاج إلى بنية تمثل العناصر التي سيتم استخدامها في عملية الرسم.

---

# العلاقة بين DOM وRender Tree

بشكل مبسط:

```
HTML
  ↓
HTML Parser
  ↓
DOM
  ↓
CSS
  ↓
Style Information
  ↓
Render Tree
```

الـ Render Tree يستخدم:

```
DOM
+
Computed / Relevant CSS
```

لتحديد ما الذي سيتم رسمه.

---

# مثال مهم

لدينا:

```
<div><h1>Hello</h1><pclass="hidden">
        Secret</p></div>
```

و:

```
.hidden {
    display:none;
}
```

الـ DOM يحتوي على:

```
div
├── h1
└── p
```

لكن العنصر:

```
display:none;
```

لا يتم رسمه بصريًا، ولذلك لا يكون جزءًا من الـ Render Tree المستخدم للرسم.

---

# نقطة Interview مهمة جدًا

## `display: none` vs `visibility: hidden`

### `display: none`

```
.hidden {
    display:none;
}
```

العنصر:

- موجود في DOM.
- لا يظهر.
- لا يأخذ مساحة Layout.
- لا يدخل في Render Tree كعنصر مرئي.

---

### `visibility: hidden`

```
.hidden {
    visibility:hidden;
}
```

العنصر:

- موجود في DOM.
- غير مرئي.
- ما زال يأخذ مساحة في Layout.

وهنا يجب الانتباه إلى أن تفاصيل rendering الداخلية في المتصفح أكثر تعقيدًا من مجرد قاعدة "DOM → Render Tree"، لكن هذه هي الصورة المناسبة للمقابلات الأساسية والمتوسطة.

---

# الصورة الكاملة

هذا هو أهم شيء في الفصل:

```
HTML
 │
 ▼
HTML Parser
 │
 ▼
DOM
 │
 ├───────────────┐
 │               │
 ▼               ▼
CSS             JavaScript
 │
 ▼
Style Information
 │
 └───────┬───────┘
         ▼
    Render Tree
         │
         ▼
       Layout
         │
         ▼
       Paint
         │
         ▼
      Composite
         │
         ▼
       Screen
```

**لكن:** في هذا الفصل سنركز فقط على:

```
HTML Parser
DOM
Render Tree
```

وسنترك:

```
Layout
Paint
Composite
```

لفصل Rendering Pipeline إذا قررنا إضافته لاحقًا.

---

# الفرق بينهم

| Concept | وظيفته |
| --- | --- |
| HTML Parser | يحلل HTML |
| DOM | يمثل بنية HTML داخل المتصفح |
| Render Tree | يمثل ما يحتاجه المتصفح للرسم اعتمادًا على DOM والـ CSS |

احفظيها:

```
Parser
   ↓
DOM
   ↓
Render Tree
```

---

# أشهر أسئلة المقابلات

### What happens after the browser receives HTML?

إجابة مبسطة:

> The browser parses the HTML and builds the DOM. CSS is parsed separately, and the browser combines the relevant DOM and styling information to determine what should be rendered.
> 

---

### What is the DOM?

> A tree-based representation of the document that allows the browser and JavaScript to access and manipulate its structure.
> 

---

### Is the DOM the same as HTML?

❌ No.

> HTML is markup, while the DOM is the browser's in-memory representation of the document.
> 

---

### What is the Render Tree?

> It represents the content and styling information needed to determine what is rendered visually.
> 

---

### Does `display: none` remain in the DOM?

✅ Yes.

لكن لا يتم رسمه كعنصر مرئي.

---

### Does `display: none` take space?

❌ No.

---

### Does `visibility: hidden` take space?

✅ Yes.

---

# Senior Notes

هنا أريد أن نضيف نقطة مهمة جدًا للـ Handbook:

## لا تحفظي Rendering كخط مستقيم مبسط جدًا

الواقع الداخلي للمتصفح أكثر تعقيدًا من:

```
HTML → DOM → Render Tree → Screen
```

لكن هذه الصورة ممتازة لفهم الأساس.

وعندما ندخل لاحقًا في **Web Performance**، سنحتاج إلى فهم مراحل مثل:

```
Style Calculation
Layout
Paint
Composite
```

وسنربطها بمشاكل مثل:

- Reflow / Layout
- Repaint
- Rendering Performance
- CSS performance
- JavaScript DOM manipulation

---

# 🎯 الخلاصة

لو سألك الـ Interviewer:

> **Explain how HTML becomes a rendered page.**
> 

لا تحتاجين إلى شرح عشرات التفاصيل في البداية.

قولي:

> **The browser parses the HTML and builds the DOM. It also processes CSS and determines the styles that apply to the DOM elements. The browser then builds the information needed for rendering, performs layout and painting, and finally displays the result on the screen.**
> 

والجزء الذي نراجعه الآن تحديدًا:

```
HTML
  ↓
HTML Parser
  ↓
DOM
  ↓
CSS + DOM
  ↓
Render Tree
```

# الفصل الثالث عشر: كيفية معالجة المتصفح لصفحة الويب (`Browser Rendering Architecture`)

### مثال الكود والربط بين المفاهيم:

HTML

```
<!DOCTYPE html>
<html lang="ar">
<head>
  <meta charset="UTF-8">
  <title>Browser Rendering Process</title>
  <style>
    /* عنصر غير معروض تماماً (غير موجود في الـ Render Tree) */
    .hidden-box { display: none; }

    /* عنصر معروض وموجود في الـ Render Tree */
    .visible-box { color: blue; }</style>
</head>
<body>

  <h1>خطوات معالجة الصفحة داخل المتصفح</h1>
  <p class="visible-box">هذا النص سيظهر للمستخدم.</p>
  <p class="hidden-box">هذا النص لن يظهر ولن يدخل في الـ Render Tree.</p>

  <script>
    // تغيير الـ DOM برمجيًا مما يجبر المتصفح على إعادة بناء الـ Render Tree ورسم الصفحة
    const p = document.querySelector('.visible-box');
    p.style.color = 'red';</script>

</body>
</html>
```

### السؤال:

**كيف يعمل محرك معالجة المتصفح (Browser Rendering Engine)، وما هي أدوار الـ HTML Parser، والـ DOM، والـ Render Tree وكيف ترتبط هذه العناصر مع بعضها؟**

### الإجابة النموذجية للمقابلة (Interview Answer):

> **عملية الـ Rendering هي السلسلة التي يحول بها المتصفح أكواد الـ HTML و CSS و JavaScript إلى بكسلات مرئية على الشاشة عبر مراحل مترابطة متتالية:**
> 
> 1. **محلل الـ HTML (HTML Parser):** يستقبل نصوص الـ HTML الخام على شكل أكواد ثنائية (Bytes)، ويقوم بتحويلها إلى رموز (Tokens)، ثم كائنات (Nodes)، ليبني في النهاية **شجرة الـ DOM**.
> 2. **شجرة الـ DOM (Document Object Model):** هي التمثيل الهيكلي شجري الشكل للمحتوى بذاكرة المتصفح.
> 3. **شجرة العرض (Render Tree):** هي نتاج **دمج شجرة الـ DOM مع شجرة الـ CSSOM**، وتحتوي **فقط** على العناصر المرئية التي ستُعرض فعلياً على الشاشة مع كامل أنماط تنسيقها.

### الشرح بالتفصيل والربط بين المكونات:

لنفهم كيف تترابط هذه المكونات، يجب أن نتبع رحلة الملف من اللحظة التي يصل فيها من السيرفر حتى يظهر كصورة على شاشة المستخدم:

```
[Bytes] ➔ [Tokens] ➔ [Nodes] ➔ [DOM Tree]
                                     │
                                     ├─► [Render Tree] ➔ [Layout / Reflow] ➔ [Paint]
                                     │
[CSS Bytes] ➔ ... ➔ [CSSOM Tree] ────┘
```

#### 1. المرحلة الأولى: تحليل النصوص ورسم الـ DOM (`HTML Parser & DOM`)

عند تحميل الصفحة، يتلقى المتصفح ملف الـ HTML بأسلوب التدفق (Streaming Bytes):

- **التحويل لرموز (Tokenization):** يقرأ الـ **HTML Parser** البايتات ويحولها إلى كائنات معيارية (مثل: `StartTag: body`، `StartTag: p`، `EndTag: p`).
- **بناء الـ DOM:** تتحول هذه الرموز إلى عقد (Nodes) مرتبطة بعلاقات أب وأبنائه (Parent-Child Relationships). هذا البناء الشجري في الذاكرة هو الـ **DOM**.
- **التعامل مع السكريبتات (Parser Blocking):** إذا اعترض المحلل وسم `<script>` عريض (بدون `async` أو `defer`)، يتوقف الـ HTML Parser تماماً عن بناء الـ DOM حتى يتم تحميل الملف وتنفيذه بالكامل.

#### 2. المرحلة الثانية: تحليل أنماط CSS (`CSSOM Tree`)

بالتوازي أو بعد معالجة الـ HTML، يقرأ المتصفح ملفات التنسيق وبناء شجرة أخرى تُسمى **CSSOM** (*CSS Object Model*)، وهي الشجرة التي تمثل قواعد وأساليب التنسيق المطبقة على كل عنصر.

#### 3. المرحلة الثالثة: عملية الربط التكاملي (`Building the Render Tree`)

هنا يلتقي الـ **DOM** مع الـ **CSSOM** لتكوين الـ **Render Tree**:

- **تصفية العناصر غير المرئية:** لا تحتوي شجرة الـ Render Tree على الوسوم المخفية مثل `<head>` أو `<script>` أو `<meta>`.
- **تأثير الخصائص المباشرة (مثل `display: none`):**
    - أي عنصر يمتلك تنسيق `display: none` **يوجد في الـ DOM ولكنه يُستبعد تماماً من الـ Render Tree**.
    - العنصر الذي يمتلك `visibility: hidden` أو `opacity: 0` **يظل موجوذاً داخل الـ Render Tree** لأنه يحجز مساحة بصرية بالصفحة.

#### 4. المرحلة الرابعة والحديثة: التخطيط والرسم (`Layout & Paint`)

بعد اكتمال الـ Render Tree، يكمل المتصفح الخطوات الأخيرتين:

1. **مرحلة التخطيط (Layout / Reflow):** يحسب المتصفح الأحجام الدقيقة والمواقع الجغرافية بالبكسل لكل عنصر بناءً على حجم شاشة المستخدم.
2. **مرحلة الرسم (Paint & Composite):** يتم تحويل العناصر والمعلومات البصرية إلى بكسلات حقيقية تُطبع على الشاشة وتُقسم على طبقات (Layers) للتعامل مع العرض السلس.

#### فخ المقابلة الشهير: الفرق بين الـ DOM والـ Render Tree وتأثير `display: none`

غالباً ما يسأل مسؤول المقابلة: **"هل العناصر ذات التنسيق `display: none` تكون موجودة في الـ DOM؟ وهل تظهر في الـ Render Tree؟"**

**الإجابة الحاسمة:**

- **في الـ DOM:** **نعم، تكون موجودة.** يمكن استدعاؤها والتعديل عليها بـ JavaScript عن طريق `document.querySelector()`.
- **في الـ Render Tree:** **لا، تكون غير موجودة إطلاقاً.** لأن الـ Render Tree مخصص فقط للعناصر التي تؤثر بصرياً في مرحلتي الـ Layout والـ Paint.

#### الكلمات المفتاحية للحفظ (Keywords):

- **HTML Parser & Tokenization:** عملية تحويل بايتات HTML إلى كائنات ونودز.
- **DOM Tree:** التمثيل الشجري للمحتوى بالذاكرة.
- **CSSOM:** شجرة أشكال وأنماط الـ CSS المطبقة.
- **Render Tree:** الشجرة الناتجة عن دمج DOM + CSSOM وتستبعد العناصر غير المرئية (`display: none`).
- **Layout / Reflow:** حساب أبعاد وأماكن العناصر على الشاشة.

#### جملتك النموذجية في المقابلة:

> **"The browser rendering engine processes HTML using a Parser to convert raw bytes into tokens, nodes, and ultimately the DOM tree. Concurrently, it parses CSS to form the CSSOM tree. The engine then merges these two structures into the Render Tree, which contains only visible nodes—excluding tags like `<head>` or elements styled with `display: none`. Finally, the browser executes the Layout phase to compute precise geometry and positions, followed by Painting to render actual pixels onto the screen."**
>