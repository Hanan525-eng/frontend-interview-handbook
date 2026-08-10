```
│   ├── What is CSS?
│   ├── CSS Syntax
│   ├── Properties & Values
│   ├── Comments
│   ├── How CSS is applied
│   └── CSS Rules
```

## السؤال الاول

## **What is CSS?**

#### الإجابة

**CSS — Cascading Style Sheets** هي اللغة المسؤولة عن تحديد **presentation and visual styling** لعناصر HTML.

بمعنى أن HTML يحدد:

> **What the content is**
> 

بينما CSS يحدد:

> **How the content looks and is laid out**
> 

مثال:

html

```html
<h1>Hello World</h1>
```

هذا يحدد أن العنصر هو heading.

لكن:

css

```css
h1 {
  color: blue;
  font-size: 2rem;
}
```

يحدد كيف سيظهر هذا الـ heading.

---

#### العلاقة بين HTML وCSS

يمكن تبسيطها:

```
HTML
  ↓
Structure & Meaning
  ↓
CSS
  ↓
Presentation & Layout
  ↓
Rendered UI
```

لكن مهم ألا نفهم أن CSS مجرد ألوان وخطوط.

CSS مسؤولة أيضًا عن:

- Layout
- Spacing
- Sizing
- Positioning
- Responsive Design
- Animation
- Visual states
- Accessibility-related presentation

---

### 1.2 CSS Syntax

الصيغة الأساسية لقاعدة CSS:

css

```css
selector {
  property: value;
}
```

مثال:

css

```css
button {
  background-color: blue;
  padding: 12px 20px;
}
```

نقسمها:

```
button           → Selector
background-color → Property
blue              → Value
background-color: blue; → Declaration
```

#### Selector

يحدد **العناصر التي ستطبق عليها القاعدة**.

css

```css
button
```

#### Property

يحدد **ما الذي نريد تغييره**.

css

```css
background-color
```

#### Value

يحدد **القيمة التي ستأخذها الخاصية**.

css

```css
blue
```

#### Declaration

هي:

css

```css
property: value;
```

مثال:

css

```css
color: red;
```

#### CSS Rule

الـ Rule كاملة:

css

```css
button {
  color: red;
  padding: 10px;
}
```

---

## 1.3 Properties & Values

الـ **Property** هي الخاصية التي نريد التحكم فيها، مثل:

```
color, font-size, margin, padding, display, position
```

والـ **Value** هي القيمة التي نحددها لهذه الخاصية، مثلاً:

css

```css
color: red;
font-size: 16px;
display: flex;
```

لاحظ أن الـ value ليست دائمًا مجرد كلمة. يمكن أن تكون:

```
16px, 50%, 1.5, flex, #155DFC, calc(100% - 20px)
```

أو function:

css

```css
color: rgb(21 93 252);
width: calc(100% - 2rem);
```

#### نقطة مهمة للمقابلة

ليس كل Property تقبل أي Value.

مثلاً `display: flex;` صحيح، لكن `display: blue;` غير صالح لأن `blue` ليست قيمة صحيحة لـ `display`.

---

## 1.4 Comments

تُستخدم التعليقات لشرح الكود أو تعطيل جزء منه مؤقتًا.

الصيغة:

css

```css
/* This is a CSS comment */
```

مثال:

css

```css
/* Main navigation */
.navbar {
  display: flex;
}
```

يمكن أن تمتد على أكثر من سطر:

css

```css
/*
  This section controls
  the main layout.
*/
```

#### مهم

CSS لا تستخدم `//comment` كصيغة standard للتعليقات. الصيغة الصحيحة دايمًا: `/* comment */`

---

## 1.5 How CSS is Applied

هناك ثلاث طرق أساسية لتطبيق CSS على HTML.

### 1. Inline CSS

داخل العنصر نفسه:

html

```html
<button style="color: red;">Save</button>
```

**الميزة**: مباشر وسريع لحالة محددة.

**العيوب**:

- صعب maintainability
- يكرر styles
- يفصل الـ presentation عن reusable styles
- لا يناسب المشاريع الكبيرة

لذلك لا يُستخدم عادة كحل أساسي في التطبيقات الكبيرة.

### 2. Internal CSS

داخل `<style>`:

html

```html
<head>
  <style>
    button {
      color: red;
    }
  </style>
</head>
```

مفيد عندما تكون الـ styles مرتبطة بوثيقة HTML معينة، لكن في التطبيقات الكبيرة غالبًا نحتاج نفصل الـ CSS ونعيد استخدامه.

### 3. External CSS

ملف CSS منفصل:

css

```css
/* styles.css */
button {
  color: red;
}
```

html

```html
<link rel="stylesheet" href="styles.css">
```

الطريقة الأفضل للمشاريع الكبيرة لأنها تسمح بـ:

- Reusability
- Maintainability
- Separation of concerns
- Browser caching
- تنظيم أفضل للـ styles

الـ external stylesheet المرتبط باستخدام `<link rel="stylesheet">` يدخل ضمن موارد المتصفح التي تؤثر في الـ rendering، ويربط ذلك مباشرة بـ **CSSOM** والـ **Critical Rendering Path**.

---

## 1.6 CSS Rules

قاعدة CSS تتكون من:

```
Selector + Declaration Block
```

مثال:

css

```css
.card {
  padding: 20px;
  border-radius: 8px;
}
```

```
CSS Rule
│
├── Selector (.card)
│
└── Declaration Block
    │
    ├── Declaration (padding: 20px;)
    │   ├── Property
    │   └── Value
    │
    └── Declaration (border-radius: 8px;)
        ├── Property
        └── Value
```

---

## 🎯 Interview Question

#### What is the difference between a CSS declaration and a CSS rule?

**Declaration**: `color: red;` — هي `property + value`.

**CSS Rule**:

css

```css
button {
  color: red;
}
```

فتتكون من `Selector + Declaration Block`.

---

## 🎯 Senior Note

أهم شيء في هذا الفصل ألا تحفظي:

> CSS = colors and styling.
> 

الأدق:

> **CSS is a declarative language used to describe the presentation, layout, and visual behavior of a document.**
> 

وده مهم جدًا لأن الفصول القادمة ستبني على هذا المفهوم:

```
CSS Fundamentals → Selectors → Cascade → Box Model → Layout → Responsive Design → Modern CSS
```

---

### 📋 Chapter Summary — مراجعة سريعة

#### جدول المقارنة: طرق تطبيق CSS

| الطريقة | التكنيك | الأولوية والاستخدام |
| --- | --- | --- |
| **Inline CSS** | `style="..."` داخل العنصر | أعلى Specificity (1,0,0,0)، لكن سيئة للـ maintainability |
| **Internal CSS** | داخل `<style>` في الـ `<head>` | مناسبة لصفحة واحدة استثنائية أو تجارب سريعة |
| **External CSS** | ملف `.css` مربوط بـ `<link>` | **Best Practice**: Reusability + Caching + Separation of concerns |

#### 🪤 فخ المقابلة الشهير

**السؤال**: "ماذا يحدث إذا أضفنا تنسيقًا لنفس العنصر بالطرق الثلاث في نفس الوقت؟"

**الإجابة**:

- التنسيق المكتوب بأسلوب **Inline CSS** يمتلك **أعلى Specificity (1,0,0,0)** ويغلب التنسيقات الأخرى بشكل عام، **بغض النظر عن ترتيب كتابته في الكود** (ما لم توجد `!important`).
- إذا تعادلت الـ **Specificity** بين Internal و External، يطبَّق التنسيق المكتوب **أخيرًا** في شفرة الـ HTML، بناءً على قاعدة **Cascade Source Order**.

#### Keywords للحفظ

```
CSS · Cascading Style Sheets · Selector · Property · Value
Declaration · Declaration Block · CSS Rule
Inline CSS · Internal CSS · External CSS
Stylesheet · CSSOM · Specificity · Source Order
```

#### 🎤 جملتك النموذجية في المقابلة

> **"CSS (Cascading Style Sheets) decorates the presentation layer of the DOM by binding declaration blocks to specific selectors. A CSS Rule combines a selector with properties and values inside curly braces. While CSS can be embedded inline or internally, linking an External Stylesheet via the `<link>` tag is the standard industry best practice—maximizing caching capabilities, maintainability, and clean separation of concerns."**
> 

---