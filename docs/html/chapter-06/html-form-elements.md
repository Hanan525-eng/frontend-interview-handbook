# **الفصل** السادس

# Form Elements

# 6.1 Text Input Elements

---

# السؤال الاولي

# What is the `<textarea>` element in HTML, and when should you use it?

---

## الإجابة

> The `<textarea>` element is used to create a multi-line text input control, allowing users to enter large amounts of plain text.

---

## لماذا نهتم بهذا العنصر؟

ليس كل النصوص قصيرة.

بعض البيانات تحتاج إلى أكثر من سطر، مثل:

- Comments
- Feedback
- Messages
- Product Reviews
- Blog Content
- User Bio
- Address

ولهذا لا يمكن استخدام:

```
<inputtype="text">
```

في هذه الحالات.

---

# متى نستخدم `<textarea>`؟

استخدمه عندما يحتاج المستخدم إلى إدخال نص متعدد الأسطر.

مثل:

- Contact Forms
- Customer Feedback
- Support Tickets
- Product Reviews
- Description Fields
- Notes

---

# المثال الأساسي

```
<labelfor="message">
    Message</label><textareaid="message"name="message"></textarea>
```

---

## ماذا يعرض؟

يعرض مربع نص كبير يسمح للمستخدم بكتابة عدة أسطر.

---

# مثال مع Placeholder

```
<textareaname="comment"placeholder="Write your comment..."></textarea>
```

---

# تحديد الحجم

يمكن تحديد الحجم باستخدام:

```
rows
```

و

```
cols
```

---

## المثال

```
<textarearows="6"cols="40"></textarea>
```

---

## ماذا يعني؟

### rows

عدد الأسطر الظاهرة.

---

### cols

عدد الأعمدة (العرض التقريبي بالأحرف).

---

## هل يستخدم المطورون rows و cols دائمًا؟

ليس بالضرورة.

في التطبيقات الحديثة غالبًا يتم التحكم في الحجم باستخدام CSS.

مثال:

```
textarea {

width:100%;

height:180px;

}
```

---

# القيمة الافتراضية

بعكس `<input>`،

لا تستخدم:

```
value=""
```

---

بل تكتب القيمة بين الوسمين.

مثال:

```
<textarea>

Hello World</textarea>
```

---

وهذه نقطة مهمة جدًا.

---

# لماذا؟

لأن:

```
<textareavalue="Hello">
```

❌ غير صحيح.

---

والصحيح هو:

```
<textarea>

Hello</textarea>
```

---

# أشهر الخصائص

يدعم:

- name
- id
- placeholder
- required
- readonly
- disabled
- minlength
- maxlength
- autocomplete
- autofocus

كما يدعم الخصائص العامة لجميع عناصر HTML مثل:

- class
- style
- title
- aria-\*

---

# أشهر أسئلة المقابلات

### Can a textarea contain multiple lines?

✅ Yes.

---

### Does textarea use the value attribute?

❌ No.

---

### Where is the default value stored?

Between the opening and closing tags.

---

### Can textarea be resized?

✅ نعم.

وفي معظم المتصفحات يمكن للمستخدم تغيير حجمه من الزاوية السفلية.

---

## منع تغيير الحجم

```
textarea{

resize:none;

}
```

---

أو

```
textarea{

resize:vertical;

}
```

---

أو

```
textarea{

resize:horizontal;

}
```

---

# الفرق بين `<input>` و `<textarea>`

| Feature                | `<input type="text">` | `<textarea>`                         |
| ---------------------- | --------------------- | ------------------------------------ |
| عدد الأسطر             | سطر واحد              | عدة أسطر                             |
| يدعم `value` Attribute | ✅ نعم                | ❌ لا                                |
| القيمة الافتراضية      | `value=""`            | بين الوسمين                          |
| مناسب للتعليقات        | ❌ لا                 | ✅ نعم                               |
| قابل لتغيير الحجم      | ❌ لا                 | ✅ نعم (افتراضيًا في معظم المتصفحات) |

---

# مثال عملي

```
<form><labelfor="review">

Review</label><textareaid="review"name="review"rows="5"placeholder="Write your review..."required></textarea><buttontype="submit">

Submit</button></form>
```

---

# أشهر أسئلة المقابلات

### When should you use textarea instead of text input?

عندما يحتاج المستخدم إلى إدخال نص متعدد الأسطر.

---

### Can textarea contain HTML?

لا.

ما يكتبه المستخدم يُعامل كنص عادي (Plain Text)، وليس كعناصر HTML قابلة للتنفيذ.

---

### Which attributes control the visible size?

```
rows
```

و

```
cols
```

---

### Can CSS override rows and cols?

✅ Yes.

---

# Best Practices

- استخدم `<textarea>` للنصوص الطويلة فقط.
- اربطه دائمًا بـ `<label>`.
- استخدم `placeholder` كإرشاد وليس كبديل عن `<label>`.
- استخدم CSS للتحكم في الحجم بدلًا من الاعتماد على `rows` و`cols` فقط.
- استخدم `maxlength` إذا كانت هناك حدود لعدد الأحرف.

---

# Senior Notes

هناك عدة نقاط يقع فيها كثير من المطورين:

### 1. لا تستخدم `value`

هذا خطأ شائع:

```
<textareavalue="Hello"></textarea>
```

القيمة لن تظهر.

الصحيح:

```
<textarea>Hello</textarea>
```

---

### 2. `textarea` لا يحافظ على التنسيق البصري

رغم أنه يدعم الأسطر الجديدة، فإنه لا يفسر HTML الذي يكتبه المستخدم. إذا كتب المستخدم:

```
<b>Hello</b>
```

فسيُعرض ويُرسل كنص عادي، وليس كنص عريض.

---

### 3. التحكم في الحجم

لا تعتمد على `rows` و`cols` لبناء واجهات حديثة، بل استخدم CSS مع `width` و`height` أو `min-height`، وفكر فيما إذا كنت تريد السماح للمستخدم بتغيير الحجم باستخدام خاصية `resize`.

## حقول النصوص الطويلة (`<textarea>`)

### مثال الكود:

HTML

```
<!-- نموذج لإرسال تعليق أو رسالة دعم -->
<form action="/submit-feedback" method="POST">
  <label for="user-message">رسالتك أو ملاحظاتك:</label>
  <br />

  <textarea
    id="user-message"
    name="userMessage"
    rows="6"
    cols="50"
    placeholder="اكتب ملاحظاتك التفصيلية هنا..."
    maxlength="500"
    required
  >هذا نص افتراضي يمكن للمستخدم تعديله.</textarea>

  <br />
  <button type="submit">إرسال</button>
</form>
```

### السؤال:

**ما هو عنصر `<textarea>` في HTML، ومتى يجب عليك استخدامه؟**

_(بالإنجليزي: What is the `<textarea>` element in HTML, and when should you use it?)_

### الإجابة النموذجية للمقابلة (Interview Answer):

> **عنصر `<textarea>` هو عنصر إدخال متعدد الأسطر (Multi-line text input control) يُستخدم عندما نطلب من المستخدم كتابة نصوص طويلة أو ممتدة مثل التعليقات، الملاحظات، أو المقالات. على عكس حقل `<input type="text">` أحادي السطر، يتيح عنصر `<textarea>` إدخال الفواصل الزمانية والأسطر الجديدة (Line breaks)، كما يتميز بأنه عنصر ذو فتح وإغلاق (`<textarea>...</textarea>`) يضع نص القيمة الافتراضية داخل المحتوى وليس عبر خاصية `value`.**

### الشرح بالتفصيل:

في هذا الدرس من الفصل السادس، ننتقل من حقول الإدخال البسيطة (`<input>`) إلى العناصر المستقلة التي تُشكل واجهات النماذج المعقدة. عنصر `<textarea>` هو الحقل الأساسي للنصوص الممتدة.

مهندس الواجهات (UI Engineer) المحترف يجب أن يفهم الاختلافات الجوهرية بينه وبين حقل النص العادي، وكيفية التحكم في أبعاده وسلوكه.

#### 1. متى نستخدم `<textarea>` بدلاً من `<input type="text">`؟

- **`input type="text"`:** مخصص للنصوص القصيرة جداً المكونة من **سطر واحد فقط** (مثل: الاسم الأول، البريد الإلكتروني، عنوان المقال). لا يقبل الضغط على زر `Enter` لإنشاء سطر جديد.
- **`<textarea>`:** مخصص للنصوص الطويلة التي تتطلب **أسطرًا متعددة** (مثل: الوصف الوظيفي، رسالة التواصل، كتابة مقال، أو إضافة تعليق).

#### 2. الخصائص الأساسية لعنصر `<textarea>`

| **الخاصية (Attribute)**       | **الوظيفة والشرح**                                               |
| ----------------------------- | ---------------------------------------------------------------- |
| **`rows`**                    | تحدد عدد الأسطر الظاهرة أفقياً لارتفاع الحقل (الارتفاع المبدئي). |
| **`cols`**                    | تحدد عدد الأعمدة/الحروف الظاهرة بعرض الحقل (العرض المبدئي).      |
| **`maxlength` / `minlength`** | تحدد الحد الأقصى والأدنى لعدد الحروف المسموح بكتابتها.           |
| **`placeholder`**             | نص توضيحي مؤقت يختفي بمجرد بدء الكتابة.                          |
| **`readonly` / `disabled`**   | يجعل الحقل للقراءة فقط، أو يطلبه تماماً من التفاعل.              |

#### 3. لمحة ذكاء للـ UI Engineer (أخطاء شائعة وسؤال الفخ)

الـ Interviewer ممكن يسألك: **"ما هي الأخطاء الشائعة عند التعامل مع `<textarea>` في HTML و CSS، وكيف تتغلب عليها؟"**

**الإجابة الذكية:**

1. **فخ مسافات النص الافتراضي (Whitespace Bug):**
   - عنصر `<textarea>` **ليس عنصرًا مفرغًا (Not Void)**، بل له وسم فتح ووسم إغلاق (`<textarea></textarea>`).
   - أي مسافة أو سطر جديد تتركه بين وسم الفتح والإغلاق في كود HTML سيعتبره المتصفح نساً أصلياً (Value) وستظهر مسافات فارغة للمستخدم داخل الحقل!
   - **الحل:** كتابة الوسمين ملاصقين لبعضهما تماماً إذا لم تكن هناك قيمة افتراضية: `<textarea></textarea>`.
2. **التحكم في إعادة التكبير والتصغير (CSS `resize` Property):**
   - بشكل افتراضي، تتيح المتصفحات مقبضاً في الزاوية السفلية للمستخدم لتكبير وتصغير الحقل بحرية، مما قد يفسد تصميم الصفحات (Layout Break).
   - **الحل:** يتم التحكم به في CSS عبر خاصية `resize`:
     - `resize: vertical;` (يسمح بالتكبير رأسياً فقط لحماية عرض الصفحة).
     - `resize: none;` (يلغي إمكانية التكبير تماماً).

#### الكلمات المفتاحية للحفظ (Keywords):

- **Multi-line Text Control:** عنصر إدخال نصوص متعدد الأسطر.
- **Closing Tag Required:** يتطلب وسم إغلاق مصاحب ولا يستخدم خاصية `value` في الـ HTML.
- **`rows` and `cols`:** خصائص التحكم بالأبعاد المبدئية في HTML.
- **CSS `resize` Property:** خاصية التنسيق للتحكم في تحجيم الحقل من قبل المستخدم.

# 6.2 Selection Elements

---

# السؤال الثاني

# What are the Selection Elements in HTML, and when should you use each one?

---

## الإجابة

> Selection elements allow users to choose one or more values from predefined options or suggested values. The main selection elements are `<select>`, `<option>`, `<optgroup>`, and `<datalist>`.

---

## لماذا تهتم الشركات بهذا السؤال؟

لأن اختيار عنصر الإدخال المناسب يؤثر على:

- User Experience (UX)
- Accessibility
- Form Usability
- Data Consistency

كما أن الفرق بين `<select>` و`<datalist>` من أشهر أسئلة مقابلات الـ Front-End.

---

# 1. `<select>`

---

## الإجابة

> The `<select>` element creates a drop-down list that allows users to choose one or more predefined options.

---

## متى نستخدمه؟

- Country
- Language
- Currency
- Category
- Department
- Payment Method

---

## المثال

```
<labelfor="country">
    Country</label><selectid="country"name="country"><optionvalue="eg">Egypt</option><optionvalue="sa">Saudi Arabia</option><optionvalue="ae">UAE</option></select>
```

---

## ماذا يحدث؟

يعرض المتصفح قائمة منسدلة تحتوي على الخيارات المحددة.

---

## أشهر الخصائص

يدعم:

- name
- id
- required
- disabled
- autofocus

كما يدعم خصائص خاصة مثل:

- multiple
- size

---

## اختيار أكثر من قيمة

```
<selectname="skills"multiple><option>HTML</option><option>CSS</option><option>JavaScript</option></select>
```

---

## ماذا يحدث؟

يمكن للمستخدم اختيار أكثر من عنصر.

---

## أشهر أسئلة المقابلات

### Can a select allow multiple selections?

✅ نعم.

باستخدام:

```
multiple
```

---

### Which attribute changes the number of visible options?

```
size
```

---

# 2. `<option>`

---

## الإجابة

> The `<option>` element defines an individual selectable item inside a `<select>` or `<datalist>` element.

---

## المثال

```
<optionvalue="html">
    HTML</option>
```

---

## القيمة المرسلة

إذا اختار المستخدم:

```
HTML
```

فقد تُرسل:

```
html
```

---

## ماذا لو لم نكتب `value`؟

إذا لم تحدد `value`، فسيتم استخدام النص الموجود داخل `<option>` كقيمة مرسلة.

---

## أشهر الخصائص

- value
- selected
- disabled
- label

---

## تحديد خيار افتراضي

```
<optionvalue="eg"selected>

    Egypt</option>
```

---

## تعطيل خيار

```
<optiondisabled>

Coming Soon</option>
```

---

# 3. `<optgroup>`

---

## الإجابة

> The `<optgroup>` element groups related options within a `<select>` element.

---

## لماذا نستخدمه؟

لتقسيم القوائم الطويلة إلى مجموعات منطقية.

---

## المثال

```
<selectname="language"><optgrouplabel="Frontend"><option>HTML</option><option>CSS</option></optgroup><optgrouplabel="Backend"><option>Node.js</option><option>PHP</option></optgroup></select>
```

---

## ماذا يحدث؟

يعرض المتصفح عنوانًا لكل مجموعة من الخيارات.

---

## أشهر الخصائص

- label
- disabled

---

## أشهر أسئلة المقابلات

### Can users select an optgroup?

❌ لا.

هو مجرد عنصر لتنظيم الخيارات.

---

# 4. `<datalist>`

---

## الإجابة

> The `<datalist>` element provides a list of suggested values for an `<input>` element while still allowing users to enter custom values.

---

## لماذا هو مختلف؟

بعكس `<select>`،

يمكن للمستخدم كتابة قيمة جديدة غير موجودة في القائمة.

---

## المثال

```
<labelfor="browser">

Browser</label><inputlist="browsers"id="browser"name="browser"><datalistid="browsers"><optionvalue="Chrome"><optionvalue="Firefox"><optionvalue="Edge"><optionvalue="Safari"></datalist>
```

---

## ماذا يحدث؟

عند الكتابة:

يعرض المتصفح اقتراحات.

لكن يمكن للمستخدم كتابة أي قيمة أخرى.

---

## أشهر أسئلة المقابلات

### Can users enter values not listed in a datalist?

✅ نعم.

---

### Does datalist replace select?

❌ لا.

لكل منهما استخدام مختلف.

---

# مقارنة بين `<select>` و`<datalist>`

| Feature                     | `<select>` | `<datalist>` |
| --------------------------- | ---------- | ------------ |
| قائمة مغلقة                 | ✅ نعم     | ❌ لا        |
| يسمح بكتابة قيمة جديدة      | ❌ لا      | ✅ نعم       |
| يعتمد على `<input>`         | ❌ لا      | ✅ نعم       |
| مناسب للبيانات الثابتة      | ✅ نعم     | أحيانًا      |
| يعرض اقتراحات أثناء الكتابة | ❌ لا      | ✅ نعم       |

---

# مقارنة بين عناصر Selection

| Element      | Purpose                   |
| ------------ | ------------------------- |
| `<select>`   | إنشاء قائمة منسدلة        |
| `<option>`   | تعريف خيار داخل القائمة   |
| `<optgroup>` | تجميع الخيارات            |
| `<datalist>` | تقديم اقتراحات لحقل إدخال |

---

# أشهر أسئلة المقابلات

### What is the difference between `select` and `datalist`?

> A `<select>` restricts users to predefined options, while a `<datalist>` suggests options but still allows custom input.

---

### Can an option exist without a select?

❌ لا.

إلا عند استخدامها داخل `<datalist>`.

---

### Which element groups related options?

```
<optgroup>
```

---

### Which attribute selects the default option?

```
selected
```

---

### Can a select have multiple selected options?

✅ نعم.

إذا استخدمت:

```
multiple
```

---

# Best Practices

- استخدم `<select>` عندما تكون الخيارات ثابتة ويجب تقييد المستخدم بها.
- استخدم `<datalist>` عندما تريد تقديم اقتراحات مع السماح بإدخال قيم مخصصة.
- استخدم `value` داخل كل `<option>` بدلًا من الاعتماد على النص المعروض.
- استخدم `<optgroup>` لتنظيم القوائم الطويلة وتحسين تجربة المستخدم.
- أضف `<label>` دائمًا لكل عنصر اختيار لتحسين إمكانية الوصول (Accessibility).

---

# Senior Notes

هناك عدة نقاط مهمة يقع فيها كثير من المطورين:

### 1. `select` ليس بديلًا عن `datalist`

إذا كنت تريد إجبار المستخدم على اختيار قيمة من القائمة:

✅ استخدم:

```
<select>
```

أما إذا كنت تريد تقديم اقتراحات فقط مع السماح بإدخال قيمة جديدة:

✅ استخدم:

```
<datalist>
```

---

### 2. `option` بدون `value`

إذا لم تحدد:

```
value
```

فإن النص الظاهر للمستخدم سيُرسل كقيمة.

يفضل دائمًا تحديد `value` بشكل صريح، خاصة إذا كانت القيمة المرسلة تختلف عن النص المعروض.

---

### 3. لا تخلط بين `multiple` و`size`

- `multiple` يسمح باختيار أكثر من خيار.
- `size` يحدد عدد الخيارات الظاهرة في نفس الوقت، لكنه **لا يسمح باختيار متعدد بمفرده**.

# 6.2 عناصر القوائم المنسدلة والتحديد (`<select>`, `<option>`, `<optgroup>`, `<datalist>`)

### مثال الكود:

HTML

```
<!-- 1. القائمة المنسدلة التقليدية (Select Dropdown) مع المجموعات -->
<label for="country">اختر الدولة:</label>
<select id="country" name="country" required>
  <option value="" disabled selected>-- اختر من القائمة --</option>

  <optgroup label="الشرق الأوسط">
    <option value="EG">مصر</option>
    <option value="SA">المملكة العربية السعودية</option>
    <option value="AE">الإمارات العربية المتحدة</option>
  </optgroup>

  <optgroup label="أوروبا">
    <option value="FR">فرنسا</option>
    <option value="DE">ألمانيا</option>
  </optgroup>
</select>

<br /><br />

<!-- 2. حقل الإكمال التلقائي (Datalist) -->
<label for="browser">اختر المتصفح أو اكتب اسماً جديداً:</label>
<input type="text" id="browser" name="browser" list="browsers-list" placeholder="ابدأ الكتابة..." />

<datalist id="browsers-list">
  <option value="Chrome"></option>
  <option value="Firefox"></option>
  <option value="Safari"></option>  <option value="Edge"></option>
</datalist>
```

### السؤال:

**ما هي عناصر التحديد (Selection Elements) في HTML، ومتى يجب عليك استخدام كل منها؟**

_(بالإنجليزي: What are the Selection Elements in HTML, and when should you use each one?)_

### الإجابة النموذجية للمقابلة (Interview Answer):

> **عناصر التحديد في HTML تشمل `<select>`، `<option>`، `<optgroup>`، وعنصر `<datalist>`. نستخدم `<select>` مع عناصر `<option>` عند الحاجة لتقديم قائمة منسدلة مغلقة يختار منها المستخدم خياراً واحداً (أو أكثر)، بينما نستخدم `<optgroup>` لتجميع الخيارات ذات الصلة تحت عناوين رئيسية داخل القائمة. أما `<datalist>` فيُستخدم لتقديم اقتراحات إكمال تلقائي (Autocomplete Suggestions) مع السماح للمستخدم بكتابة قيم حرة غير موجودة بالقائمة.**

### الشرح بالتفصيل:

عند التفكير في عناصر اختيار البيانات، كثيراً ما يختلط الأمر بين الأزرار التشعبية (`radio`/`checkbox`) وبين القوائم المنسدلة. كمهندس واجهات (UI Engineer)، اختيار العنصر المناسب يمنح مستخدمي جهازك أفضل تجربة استخدام (UX) ويوفر المساحة على الشاشة.

تعال نفصص هذه العناصر الأربعة بعناية:

#### 1. تفكيك العناصر الأربعة ووظائفها

#### أولاً: `<select>` (الحاوية الرئيسية للقائمة)

- **الوظيفة:** ينشئ قائمة منسدلة (Dropdown Menu).
- **أبرز الخصائص (Attributes):**
  - `multiple`: تتيح للمستخدم تحديد أكثر من خيار معاً بالضغط على `Ctrl` أو `Cmd`.
  - `size`: تحدد عدد الخيارات الظاهرة مباشرة على الشاشة دون فتح القائمة المنسدلة.

#### ثانياً: `<option>` (العنصر/الخيار الفردي)

- **الوظيفة:** يمثل كل خيار داخل القائمة.
- **الخصائص الجوهرية:**
  - `value`: القيمة الحقيقية التي تُرسل للباك إند عند اختيار هذا العنصر (قد تكون رمزاً مثل `"EG"` بدلاً من الكلمة المكتوبة للمستخدم `"مصر"`).
  - `selected`: تجعل هذا الخيار محدداً بشكل افتراضي عند فتح الصفحة.
  - `disabled`: تعطيل خيار معين لمنع اختياره.

#### ثالثاً: `<optgroup>` (مجموعات الخيارات)

- **الوظيفة:** تقسيم خيارات القائمة طويلة إلى أقسام منطقية ذات عناوين رئيسية (مثلاً: تقسيم الدول حسب القارات).
- **الخاصية الأساسية:** `label` لتحديد عنوان المجموعات المكتوب.

#### رابعاً: `<datalist>` (قائمة الإكمال التلقائي التفاعلية)

- **الوظيفة:** عنصر يدمج بين حقل النص العادي والقائمة المنسدلة. يربط بحقل `<input>` عادي باستخدام خاصية `list`.
- **الفرق الجوهري:** يمنح المستخدم اقتراحات أثناء الكتابة، **ولكنه لا يجبره عليها**؛ حيث يمكنه كتابة أي نص غير مدرج في القائمة.

#### 2. جدول المقارنة والأنواع 🔍

| **العنصر**                  | **طريقة العرض وتفاعل المستخدم**     | **هل يسمح بقيم خارجية؟**        | **أفضل حالة استخدام (Use Case)**                                |
| --------------------------- | ----------------------------------- | ------------------------------- | --------------------------------------------------------------- |
| **`<select>` + `<option>`** | قائمة منسدلة مغلقة ومحددة الخيارات. | **لا** (يجب اختيار من القائمة). | اختيار الدولة، تحديد الشهر، اختيار خطة الاشتراك.                |
| **`<optgroup>`**            | عناوين فرعية منسقة داخل القائمة.    | -                               | تقسيم المنتجات حسب الفئة، الدول حسب القارات.                    |
| **`<datalist>`**            | حقل كتابة مع شريط اقتراحات تلقائية. | **نعم** (يقبل أي نص حر).        | البحث التفاعلي، اختيار المدينة مع إمكانية كتابة اسم قرية جديدة. |

#### 3. لمحة ذكاء للـ UI Engineer (سؤال الفخ للمقابلة)

الـ Interviewer ممكن يسألك: **"متى تختار استخدام `<select>` المنسدلة، ومتى تختار أزرار الراديو (`<input type="radio">`)؟"**

**الإجابة الذكية:**

- **قاعدة الخيارات الأربعة (Rule of 4):**
  - إذا كان عدد الخيارات **قليلاً جداً (2 إلى 4 خيارات)**، يُفضل استخدام أزرار الراديو (`radio buttons`) لأنها تعرض جميع الخيارات أمام المستخدم مباشرة بدلاً من إجباره على الضغط لفتح قائمة منسدلة (صغرة للضغط وقراءات أسرع).
  - إذا كان عدد الخيارات **كبيراً (أكثر من 5 خيارات، كقائمة الدول مثلاً)**، يجب استخدام القائمة المنسدلة `<select>` حتى لا تستهلك مساحة كبيرة من الواجهة وتسبب تشتتاً بصرياً.

#### الكلمات المفتاحية للحفظ (Keywords):

- **Standard Dropdown (`<select>`):** القائمة المنسدلة المغلقة للخيارات الثابتة.
- **Option Groups (`<optgroup>`):** تقسيم الخيارات تحت عناوين فرعية داخل القائمة.
- **Autocomplete Suggestions (`<datalist>`):** حقل نصوص تفاعلي يوفر اقتراحات اختيار مرنة.
- **The `multiple` Attribute:** خاصية تسمح باختيار عناصر متعددة داخل عنصر `select`.

#### جملتك النموذجية في المقابلة:

> **"Selection elements structure structured choices: `<select>` paired with `<option>` creates closed dropdown menus for fixed choices, while `<optgroup>` groups related options visually. For flexible UX, `<datalist>` binds to a text input to offer autocomplete suggestions while still permitting custom text input. As a rule of thumb, we use radio buttons for short choice sets (under 4) and `<select>` for larger lists to save layout space**

# Form Grouping Elements

---

# السؤال الثالث

# What are the Form Grouping Elements in HTML, and when should you use them?

## الإجابة

> Form grouping elements are used to organize related form controls into logical sections. The main grouping elements are `<fieldset>` and `<legend>`.

---

## لماذا تهتم الشركات بهذا السؤال؟

لأن تنظيم النماذج لا يحسن الشكل فقط، بل يحسن أيضًا:

- Accessibility (إمكانية الوصول)
- User Experience (UX)
- Semantic HTML
- قابلية صيانة الكود

كما أن استخدام `<fieldset>` و`<legend>` يعتبر من أفضل الممارسات في النماذج الكبيرة.

---

# 1. `<fieldset>`

---

## الإجابة

> The `<fieldset>` element groups related form controls into a single logical section.

---

## متى نستخدمه؟

عندما يحتوي النموذج على مجموعة من الحقول المرتبطة بنفس الفكرة.

مثل:

- Personal Information
- Billing Address
- Shipping Address
- Payment Details
- Contact Information

---

## المثال

```
<form><fieldset><labelfor="firstName">
            First Name</label><inputtype="text"id="firstName"name="firstName"><labelfor="lastName">
            Last Name</label><inputtype="text"id="lastName"name="lastName"></fieldset></form>
```

---

## ماذا يحدث؟

يقوم المتصفح بتجميع هذه العناصر داخل قسم واحد، وغالبًا يعرض إطارًا (Border) حولها بشكل افتراضي.

---

## أشهر الخصائص

يدعم جميع الخصائص العامة، بالإضافة إلى:

```
disabled
```

---

## تعطيل مجموعة كاملة

```
<fieldsetdisabled>

    ...</fieldset>
```

---

## ماذا يحدث؟

يتم تعطيل جميع عناصر النموذج الموجودة داخله تلقائيًا.

---

## أشهر أسئلة المقابلات

### Can a fieldset disable multiple form controls?

✅ نعم.

وهذه إحدى أهم مميزاته.

---

# 2. `<legend>`

---

## الإجابة

> The `<legend>` element provides a caption or title for a `<fieldset>`.

---

## لماذا نستخدمه؟

لإعطاء عنوان واضح للمجموعة.

---

## المثال

```
<fieldset><legend>

        Personal Information</legend><inputtype="text"name="firstName"><inputtype="text"name="lastName"></fieldset>
```

---

## ماذا يحدث؟

يعرض المتصفح عنوانًا للمجموعة.

كما يستخدمه قارئو الشاشة (Screen Readers) لوصف مجموعة الحقول للمستخدم.

---

## لماذا هو مهم؟

بدونه، قد يصعب على مستخدمي التقنيات المساعدة فهم العلاقة بين الحقول داخل المجموعة.

---

## أشهر أسئلة المقابلات

### Can legend exist without fieldset?

يمكن للمتصفح عرضه، لكن الاستخدام الصحيح والدلالي هو أن يكون داخل `<fieldset>` ليصف هذه المجموعة.

---

# مثال عملي

```
<form><fieldset><legend>

            Payment Method</legend><label><inputtype="radio"name="payment"value="card">

            Credit Card</label><label><inputtype="radio"name="payment"value="paypal">

            PayPal</label></fieldset></form>
```

---

## ماذا يحدث؟

يتم تجميع جميع خيارات الدفع تحت عنوان واحد.

وهذا يحسن:

- تنظيم النموذج.
- تجربة المستخدم.
- إمكانية الوصول.

---

# مقارنة بين `fieldset` و`legend`

| Element      | Purpose                                   |
| ------------ | ----------------------------------------- |
| `<fieldset>` | تجميع عناصر النموذج المرتبطة              |
| `<legend>`   | عنوان للمجموعة الموجودة داخل `<fieldset>` |

---

# أشهر أسئلة المقابلات

### Why should you use fieldset?

لتجميع الحقول المرتبطة منطقيًا وتحسين Accessibility.

---

### What is the purpose of legend?

يوفر عنوانًا وصفيًا لمجموعة الحقول داخل `<fieldset>`.

---

### Can fieldset contain multiple input types?

✅ نعم.

يمكن أن يحتوي على:

- inputs
- textarea
- select
- radio
- checkbox
- button
- وغيرها من عناصر النماذج.

---

### Which element can disable an entire group of controls?

```
<fieldsetdisabled>
```

---

### Does legend improve accessibility?

✅ نعم.

لأنه يصف المجموعة كاملة لقارئات الشاشة، مما يسهل التنقل وفهم العلاقة بين الحقول.

---

# Best Practices

- استخدم `<fieldset>` لتقسيم النماذج الطويلة إلى أقسام منطقية.
- ضع `<legend>` كأول عنصر داخل `<fieldset>`.
- اجعل نص `<legend>` واضحًا ومختصرًا.
- استخدم `<fieldset>` خاصةً مع مجموعات `radio` و`checkbox` لأنها تمثل مجموعة واحدة من الخيارات.

---

# Senior Notes

هناك عدة نقاط يغفل عنها كثير من المطورين:

### 1. `fieldset` ليس عنصرًا للتصميم

الغرض الأساسي منه هو **تنظيم النموذج دلاليًا (Semantic Structure)** وتحسين إمكانية الوصول، وليس مجرد رسم إطار حول العناصر.

---

### 2. `legend` ليس عنوانًا مرئيًا فقط

قد يظن البعض أنه مجرد نص أعلى الإطار، لكنه في الحقيقة عنصر مهم تعتمد عليه **قارئات الشاشة** لشرح مجموعة الحقول للمستخدم.

---

### 3. `disabled` على `fieldset`

عند إضافة:

```
<fieldsetdisabled>
```

سيتم تعطيل جميع عناصر النموذج الموجودة داخله تلقائيًا، وهو أفضل من تعطيل كل عنصر على حدة عندما تريد منع التفاعل مع قسم كامل.

---

كمل Form Grouping Elements

السؤال

What are the Form Grouping Elements in HTML, and when should you use them?

# 6.3 عناصر تجميع النماذج (`<fieldset>` و `<legend>`)

### مثال الكود:

HTML

```
<form action="/register" method="POST">
  <!-- المجمّع الأول: معلومات الحساب الشخصي -->
  <fieldset>
    <legend>معلومات الحساب</legend>

    <label for="username">اسم المستخدم:</label>
    <input type="text" id="username" name="username" required />

    <label for="email">البريد الإلكتروني:</label>
    <input type="email" id="email" name="email" required />
  </fieldset>

  <!-- المجمّع الثاني: طريقة الشحن (تحتوي على أزرار اختيار متنافية) -->
  <fieldset>
    <legend>اختر طريقة الشحن المناسبة</legend>

    <input type="radio" id="standard" name="shipping" value="standard" checked />
    <label for="standard">شحن عادي (3 - 5 أيام)</label>

    <input type="radio" id="express" name="shipping" value="express" />
    <label for="express">شحن سريع (خلال 24 ساعة)</label>
  </fieldset>

  <!-- المجمّع الثالث: مجموعات معطلة بالكامل برمجياً -->
  <fieldset disabled>
    <legend>معلومات الكوبون (معطل حالياً)</legend>

    <label for="coupon">رمز الخصم:</label>
    <input type="text" id="coupon" name="coupon" />
  </fieldset>

  <button type="submit">تسجيل الحساب</button>
</form>
```

### السؤال:

**ما هي عناصر تجميع النماذج (Form Grouping Elements) في HTML، ومتى يجب عليك استخدامها؟**

_(بالإنجليزي: What are the Form Grouping Elements in HTML, and when should you use them?)_

### الإجابة النموذجية للمقابلة (Interview Answer):

> **عناصر تجميع النماذج في HTML هي `<fieldset>` و `<legend>`. يُستخدم عنصر `<fieldset>` لتجميع حقول المدخلات والعناصر المرتبطة ببعضها منطقياً داخل إطار موحد، بينما يُستخدم عنصر `<legend>` لتقديم عنوان أو وصف نصي لهذه المجموعة. نستخدمهما لتنظيم النماذج الطويلة والمعقدة بصرياً، ولتحسين إمكانية الوصول (Accessibility) حيث تقرأ قارئات الشاشة (Screen Readers) محتوى الـ `<legend>` مع كل حقل داخل المجموعة.**

### الشرح بالتفصيل:

عند بناء النماذج المعقدة (مثل نماذج إدخال البيانات المالكة أو إتمام عمليات الشراء Checkout Forms)، قد يتشتت المستخدم وتتداخل البيانات. كمهندس واجهات (UI Engineer)، لا تقتصر وظيفتك على بناء حقول تعمل بشكل صحيح فحسب، بل على تنظيمها دلالياً (Semantically) وبصرياً.

تعال نفصص هذين العنصرين بعناية:

#### 1. تفكيك العناصر ووظائفها

#### أولاً: عنصر `<fieldset>`

- **الوظيفة:** يعمل كحاوية هيكلية (Semantic Container) لتجمِيع عناصر الإدخال والـ Labels المنتمية لغرض واحد (مثل: بيانات العنوان، معلومات الدفع، خيارات الشحن).
- **خاصية التعطيل الجماعي (`disabled` attribute):**
  - إذا أضفت خاصية `disabled` على عنصر `<fieldset>`، فإن المتصفح **يعطل جميع حقول الإدخال والأزرار الموجودة داخله دفعة واحدة** دُون الحاجة لكتابة `disabled` على كل حقل بشكل منفصل!

#### ثانياً: عنصر `<legend>`

- **الوظيفة:** يمثل العنوان الرئيسي للمجموعة (Caption / Label for the fieldset).
- **المكان المشروط:** **يجب أن يكون أول عنصر ابن (First Child)** داخل عنصر `<fieldset>` مباشرة ليقرأه المتصفح وقارئات الشاشة بشكل صحيح.

#### 2. متى يجب عليك استخدام عناصر التجميع؟ (Use Cases)

1. **المجموعات ذات الخيارات المتنافية (`Radio Groups`):**

   عند وجود مجموعة أزرار راديو (مثل خيارات طريقة الدفع أو نوع الحساب)، وضعها داخل `<fieldset>` ومعه `<legend>` يعطي سياقاً واضحاً للمستخدم ولتقنيات التخصيص والأجهزة المساعدة.

2. **النماذج الطويلة متعددة الأقسام (Multi-section Forms):**

   فصل البيانات الشخصية، بيانات العنوان، وبيانات الفوترة إلى كتل منظمة ومستقلة.

3. **التحكم البرمجي الموحد (Group Disabling):**

   عندما تريد تعطيل قسم كامل من النموذج بناءً على اختيار المستخدم (مثلاً: إخفاء وتعطيل قسم "عنوان الفوترة" إذا كان يطابق "عنوان الشحن").

#### 3. لمحة ذكاء للـ UI Engineer (سؤال الفخ للمقابلة)

الـ Interviewer ممكن يسألك: **"لماذا لا نكتفي بوضع `<div>` مع وسم `<h3>` بدلاً من استخدام `<fieldset>` و `<legend>`؟ وما تأثير ذلك على إمكانية الوصول (Accessibility)؟"**

**الإجابة الذكية:**

1. **فرق الأهمية لدعم إمكانية الوصول (Screen Readers & Accessibility):**
   - عند استخدام `<div>` و `<h3>`، لن تفهم قارئات الشاشة (مثل NVDA أو JAWS) أن حقول الإدخال تابعة لهذا العنوان.
   - عند التنقل باستخدام زر `Tab` بين حقول الراديو مثلاً داخل `<fieldset>`، ستنطق قارئة الشاشة عنوان الـ `<legend>` أولاً ثم اسم الحقل (مثلاً: _"طريقة الشحن: شحن عادي، محدد"_). هذا يضمن عدم ضياع السياق للمستخدمين ذوي الاحتياجات الخاصة.
2. **التحكم بالسلوك الإفتراضي (Form State Behavior):**
   - الـ `<div>` لا يقبل خاصية `disabled` لتعطيل العناصر التي بداخله تلقائياً، بينما يوفر `<fieldset>` هذه الميزة الهيكلية الهامة.

#### الكلمات المفتاحية للحفظ (Keywords):

- **Semantic Grouping:** التجميع الدلالي للحقول المرتبطة.
- **Accessible Forms:** تحسين إمكانية الوصول لنطق السياق عبر قارئات الشاشة.
- **`<legend>` as First Child:** اشتراط موقع العنوان كأول عنصر داخل المجمّع.
- **Fieldset Disabling:** تعطيل كافة الحقول الداخلية بإضافة `disabled` على الـ fieldset.

#### جملتك النموذجية في المقابلة:

> **"`<fieldset>` and `<legend>` provide semantic grouping for form controls. `<fieldset>` groups related inputs visually and semantically, while `<legend>` serves as the accessible label for the entire group. This is vital for complex forms and radio button groups because screen readers announce the legend content when navigating through child inputs. Additionally, applying the `disabled` attribute to a `<fieldset>` neatly disables all enclosed controls at once**

# 6.4 Output Elements

---

# السؤال الرابع

# What is the `<output>` element in HTML, and when should you use it?

## الإجابة

> The `<output>` element represents the result of a calculation or user action. It is commonly used to display dynamically generated values associated with form controls.

---

## لماذا تهتم الشركات بهذا السؤال؟

لأن `<output>` هو العنصر الدلالي (Semantic Element) المخصص لعرض النتائج داخل النماذج، بدلاً من استخدام عناصر عامة مثل `<div>` أو `<span>`.

استخدامه يجعل الكود أكثر وضوحًا ويحسن إمكانية الوصول (Accessibility).

---

# متى نستخدم `<output>`؟

يستخدم لعرض نتائج مثل:

- Calculator Result
- Total Price
- BMI Result
- Loan Calculator
- Tax Calculation
- Live Form Calculations

---

# المثال الأساسي

```
<form><labelfor="quantity">
        Quantity</label><inputtype="number"id="quantity"value="2"><labelfor="price">
        Price</label><inputtype="number"id="price"value="50"><p>
        Total:<outputid="total">
            100</output></p></form>
```

---

## ماذا يحدث؟

يعرض `<output>` النتيجة المحسوبة.

وفي التطبيقات العملية يتم تحديثه باستخدام JavaScript.

---

# مثال عملي مع JavaScript

```
<labelfor="age">
    Age</label><inputtype="number"id="age"value="20"><p>

    Next Year:<outputid="nextAge">
        21</output></p>
```

---

ثم:

```
constage=document.querySelector("#age");constoutput=document.querySelector("#nextAge");age.addEventListener("input", () => {output.value=Number(age.value)+1;

});
```

---

## ماذا يحدث؟

كلما تغير العمر،

تتغير قيمة `<output>` مباشرة.

---

# أشهر الخصائص

يدعم جميع الخصائص العامة مثل:

- id
- class
- style

كما يدعم خصائص خاصة مثل:

- `for`
- `name`

---

## الخاصية `for`

تستخدم لربط عنصر `<output>` بعناصر الإدخال التي يعتمد عليها.

---

## المثال

```
<outputfor="quantity price"id="total"></output>
```

---

### ماذا تعني؟

أن قيمة `<output>` تعتمد على:

- quantity
- price

---

> **ملاحظة:** الخاصية `for` تعطي علاقة دلالية بين عناصر الإدخال ونتيجة الحساب، لكنها **لا تقوم بالحساب أو التحديث تلقائيًا**. ما زلت بحاجة إلى JavaScript لتحديث القيمة.

---

# أشهر أسئلة المقابلات

### Does `<output>` perform calculations?

❌ لا.

هو يعرض النتيجة فقط.

---

### What updates an output element?

عادةً JavaScript.

---

### Is output a replacement for JavaScript?

❌ لا.

JavaScript هو المسؤول عن الحساب.

---

# الفرق بين `<output>` و `<span>`

| Feature                            | `<output>` | `<span>` |
| ---------------------------------- | ---------- | -------- |
| عنصر دلالي (Semantic)              | ✅ نعم     | ❌ لا    |
| مخصص لعرض نتائج العمليات           | ✅ نعم     | ❌ لا    |
| عنصر عام للاستخدامات المختلفة      | ❌ لا      | ✅ نعم   |
| يمكن ربطه بعناصر النموذج عبر `for` | ✅ نعم     | ❌ لا    |

---

# مثال عملي

حساب السعر الإجمالي:

```
<form><labelfor="quantity">

        Quantity</label><inputid="quantity"type="number"value="1"><labelfor="price">

        Price</label><inputid="price"type="number"value="100"><p>

        Total:<outputid="total"for="quantity price">

            100</output></p></form>
```

---

# أشهر أسئلة المقابلات

### What is the purpose of the output element?

> It displays the result of a calculation or user action.

---

### Can output replace span?

يمكنه عرض النص مثل `span`، لكنه مصمم خصيصًا لعرض نتائج العمليات داخل النماذج، لذلك يكون الاختيار الأفضل عندما يكون هذا هو الغرض.

---

### Which attribute associates output with form controls?

```
for
```

---

### Does output submit data with the form?

❌ لا.

إذا كنت تحتاج إلى إرسال القيمة إلى الخادم، فيجب وضعها في عنصر نموذج مناسب (مثل `input` مخفي إذا كان ذلك مناسبًا) أو إرسالها عبر JavaScript.

---

# Best Practices

- استخدم `<output>` لعرض نتائج العمليات الحسابية داخل النماذج.
- حدّث قيمته باستخدام JavaScript عند تغير بيانات الإدخال.
- استخدم الخاصية `for` لتوضيح العلاقة بين عناصر الإدخال والنتيجة.
- لا تستخدم `<output>` لعرض نصوص عامة لا تمثل نتيجة عملية أو حساب.

---

# Senior Notes

هناك عدة نقاط يغفل عنها كثير من المطورين:

### 1. `<output>` عنصر دلالي وليس عنصرًا للحساب

الكثير يظن أن `<output>` يحسب النتائج بنفسه.

الحقيقة أنه:

- يعرض النتيجة فقط.
- لا يحتوي على أي منطق حسابي.

---

### 2. لا تعتمد على النص الداخلي بعد بدء التحديث

يمكن تحديث قيمة العنصر باستخدام:

```
output.value=total;
```

أو:

```
output.textContent=total;
```

يفضل الالتزام بطريقة واحدة داخل المشروع للحفاظ على الاتساق.

---

### 3. لا تستخدم `<output>` بدلًا من `<div>`

إذا كنت تعرض:

- رسالة.
- تنبيهًا.
- وصفًا.
- نصًا عاديًا.

فاستخدم العناصر المناسبة مثل:

```
<div>
```

أو

```
<p>
```

أما إذا كنت تعرض **نتيجة عملية أو حساب**، فاستخدم:

```
<output>
```

# عنصر المخرجات والحسابات (`<output>`)

### مثال الكود:

HTML

```
<!-- نموذج حسابي تفاعلي لحساب إجمالي السعر مع ضريبة المبيعات -->
<form oninput="result.value = parseFloat(price.value) + (parseFloat(price.value) * (parseFloat(tax.value) / 100))">

  <!-- الحقل الأول: سعر المنتج -->
  <label for="price">سعر المنتج ($):</label>
  <input type="number" id="price" name="price" value="100" min="0" />

  <br /><br />

  <!-- الحقل الثاني: نسبة الضريبة بواسطة شريط السحب -->
  <label for="tax">نسبة الضريبة (%):</label>
  <input type="range" id="tax" name="tax" value="14" min="0" max="30" />

  <br /><br />

  <!-- عنصر المخرجات: يعرض نتيجة الحساب التلقائي -->
  <label for="result">السعر الإجمالي شامل الضريبة:</label>
  <output id="result" name="totalResult" for="price tax">114</output> $

</form>
```

### السؤال:

**ما هو عنصر `<output>` في HTML، ومتى يجب عليك استخدامه؟**

_(بالإنجليزي: What is the `<output>` element in HTML, and when should you use it?)_

### الإجابة النموذجية للمقابلة (Interview Answer):

> **عنصر `<output>` في HTML هو عنصر دلالي (Semantic Element) يُستخدم لعرض نتائج العمليات الحسابية أو نصوص المخرجات الناتجة عن تفاعل المستخدم مع الحقول أو النماذج (Form Calculations). على عكس حقول الإدخال العادية المخصصة للقراءة فقط (`readonly inputs`)، يُعامل المتصفح وقارئات الشاشة عنصر `<output>` كمنطقة قراءة ديناميكية تعبر عن نتيجة، كما يوفر خاصية `for` لربط النتيجة بالحقول التي ساهمت في حسابها.**

### الشرح بالتفصيل:

غالبًا ما يحتاج مهندس الواجهات (UI Engineer) لإنشاء حاسبات تفاعلية داخل الموقع (مثل: حاسبة القروض، حساب قيمة الخصم، أداة تقييم، أو محول العملات). في الماضي، كان المطورون يضعون النتيجة داخل `<span>` أو `<div>` أو حقل `<input readonly>`. لكن مع إدخال HTML5، أصبح عنصر `<output>` هو الخيار القياسي والمعياري لتمثيل هذه البيانات.

تعال نفصص هذا العنصر بعناية:

#### 1. الخصائص الجوهرية لعنصر `<output>`

| **الخاصية (Attribute)** | **الوظيفة والشرح**                                                                                                                       |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| **`for`**               | خاصية فائقة الأهمية تتيح ربط عنصر المخرجات بالمعرفات (`id`) الخاصة بالحقول التي دخلت في الحساب، مفصولة بمسافات (مثل: `for="price tax"`). |
| **`form`**              | يربط عنصر المخرجات بالنموذج التابع له في حال تم وضعه خارج وسم الـ `<form>`.                                                              |
| **`name`**              | يحدد اسم العنصر للوصول إليه عبر البرمجة (مثل `form.elements.totalResult`).                                                               |

#### 2. متى يجب عليك استخدامه؟ (Use Cases)

1. **الحاسبات التفاعلية في الواجهة (Interactive Calculators):**

   مثل حاسبة التمويل العقاري، حساب سعر الشحن المتوقع، أو حساب إجمالي سلة المشتريات.

2. **عرض قيم مدخلات النطاق (`input type="range"`):**

   إظهار القيمة الرقمية الحالية لـ Range slider بجانبه مباشرة أثناء سحب المستخدم له.

3. **نتائج معالجة النصوص أو التحويلات (Converters):**

   عرض النتائج المحولة (مثل تحويل الحرارة من مئوي إلى فهرنهايت) مباشرة للمستخدم.

#### 3. لمحة ذكاء للـ UI Engineer (سؤال الفخ للمقابلة)

الـ Interviewer ممكن يسألك: **"لماذا لا نستخدم `<input type="text" readonly>` أو `<span>` لعرض النتائج الحسابية بدلاً من `<output>`؟"**

**الإجابة الذكية:**

1. **الدلالة وإمكانية الوصول (Accessibility & Live Regions):**
   - استخدام `<span>` لا يملك أي معنى دلالي (No Semantics)، وقارئات الشاشة لن تتعرف عليه كناتج عملية حسابية.
   - حقل `<input readonly>` مصمم لتلقي بيانات يرسلها النموذج للسيرفر ولكن لا يمكن تعديلها بكتيب، وليس لنتائج العمليات الحسابية الديناميكية.
   - عنصر `<output>` مصمم خريصاً لهذا الغرض، وتتعامل معه قارئات الشاشة كـ **Live Region** (تقرأ القيمة الجديدة للمستخدم كفيف البصر فوراً وبشكل تلقائي عند تغيّر الناتج دون الحاجة للتحرك إليه).
2. **إمكانية إعادة ضبط النموذج (Form Reset Behavior):**
   - عند الضغط على زر `<button type="reset">` في النموذج، يعود عنصر `<output>` تلقائياً إلى القيمة النصية الأصلية التي كانت مكتوبة داخله عند تحميل الصفحة!

#### الكلمات المفتاحية للحفظ (Keywords):

- **Semantic Calculation Output:** عنصر دلالي مخصص لعرض نواتج العمليات الحسابية والتفاعلية.
- **The `for` Attribute:** خاصية ربط المخرجات بالحقول المدخلة المسؤولة عن النتيجة.
- **Accessible Live Region:** مساعدة تقنيات القراءة التلقائية بنطق النتيجة فور تغيرها.
- **Form Reset Value:** العودة التلقائية للقيمة المبدئية عند عمل Reset للنموذج.

#### جملتك النموذجية في المقابلة:

> **"The `<output>` element is an HTML5 semantic control designed to display calculation results or output from user interactions. Unlike generic `<span>` elements or `readonly` inputs, `<output>` conveys semantic meaning to accessibility tools, automatically behaving as a live region for screen readers. It also features a `for` attribute to explicitly link the output to the input fields used in the computation, and it naturally resets to its initial content upon form resets**

خاصية **`for`** في عنصر `<output>` تعتبر من الميزات الذكية والدلالية (Semantic) في HTML5.

تعال نوضحها بشكل تبسيطي وعملي جداً:

## 1. الفكرة الأساسية بأبسط صورة

تخيل أن لديك معمل حسابات:

- لديك **مدخل أول**: السعر (`id="price"`).
- لديك **مدخل ثانٍ**: الضريبة (`id="tax"`).
- لديك **لوحة شاشة للنتيجة**: عنصر `<output>`.

عندما تكتب:

HTML

```
<output for="price tax">114</output>
```

أنت تقول للمتصفح ولقارئات الشاشة ولأي أداة تقرأ الكود:

**"الرقم الظاهر في هذه الشاشة لم يأتِ من الفراغ، بل هو نتيجة معالجة حقل السعر (`price`) وحقل الضريبة (`tax`) معاً."**

## 2. لماذا هي "فائقة الأهمية"؟ (3 أسباب جوهرية)

### أ) إمكانية الوصول وذوو الهمم (Accessibility - a11y) ♿

هذا هو السبب الأول والأهم على الإطلاق!

- المستخدم كفيف البصر الذي يستعمل **قارئ الشاشة (Screen Reader)** لا يرى الصفحة بعينيه، بل يسمعها.
- عندما ينتقل قارئ الشاشة إلى عنصر `<output>`، فإن وجود خاصية `for="price tax"` يجعله ينطق للمستخدم:
  _"عنصر المخرجات للـ Price والـ Tax يساوي 114"_.
- هذا يعطي المستخدم **سياقاً كاملاً (Context)** وفهماً فورياً للصلة بين العناصر، بدلاً من أن يقرأ له المتصفح مجرد رقم مجرد مثل _"114"_ دون أن يعرف المستخدم من أين جاء هذا الرقم!

### ب) توثيق الكود وتنظيمه (Self-Documenting Code) 🧩

عندما يعمل فريق كامل من المطورين على نموذج حاسبة معقد يحتوي على 15 حقل إدخال و4 نواتج مختلفة:

- بمجرد النظر إلى خاصية `for` في عنصر `<output>`، يفهم المطور فوراً ما هي الحقول المرتبطة بهذا الناتج بدون الحاجة لتتبع أكواد الجافاسكريبت المعقدة لمعرفة العلاقات!

### ج) الربط البرمجي السلس (JavaScript DOM Linking) 💻

تسمح لك خاصية `for` بالوصول للحقول المرتبطة عبر الجافاسكريبت بسهولة من خلال خاصية `htmlFor`.

## 3. مقارنة سريعة لتتضح الصورة

### ❌ الطريقة القديمة / الخاطئة (بدون ربط):

HTML

```
<label>السعر:</label>
<input type="number" id="price" />

<label>الضريبة:</label>
<input type="number" id="tax" />

<!-- الناتج غير مرتبط بأي شيء - المتصفح يراه كعنصر تائه! -->
<span>114</span>
```

- **النتيجة:** عدم وجود أي دلالة هكلية (No Semantics)، وقارئ الشاشة لن يفهم العلاقة.

### ✅ الطريقة المعيارية الاحترافية (باستخدام `for`):

HTML

```
<label for="price">السعر:</label>
<input type="number" id="price" name="price" value="100" />

<label for="tax">الضريبة:</label>
<input type="number" id="tax" name="tax" value="14" />

<!-- هنا ربطنا الناتج بالحقلين بكل وضوح -->
<output for="price tax">114</output>
```

- **ملاحظة قوية:** نضع الـ `id` الخاص بكل حقل داخل `for` مفصولة **بمسافة فقط** (وليس بفاصلة `,`).

## جملتك للمقابلة الشخصية (Interview Summary):

> **"خاصية `for` في عنصر `<output>` تُنشئ رابطاً دلالياً (Explicit Semantic Relationship) بين حقل المخرجات وحقول الإدخال التي نتج عنها الحساب عبر الـ `id` الخاص بها. فائدتها الكبرى تكمن في تحسين إمكانية الوصول (Accessibility)، حيث تتيح لقارئات الشاشة نطق السياق والمصدر الذي جاءت منه هذه النتيجة للمستخدم."**

# Progress Indicators

---

# السؤال الخامس

# What are the Progress Indicator Elements in HTML, and when should you use each one?

---

## الإجابة

> Progress indicator elements are used to visually represent progress or measurements. The two main elements are `<progress>` and `<meter>`.

---

## لماذا تهتم الشركات بهذا السؤال؟

لأن الكثير من المطورين يخلطون بين `<progress>` و`<meter>` رغم أن لكل منهما غرضًا مختلفًا.

فهم الفرق بينهما يدل على فهم جيد لـ **Semantic HTML** واختيار العنصر المناسب لكل حالة.

---

# 1. `<progress>`

---

## الإجابة

> The `<progress>` element represents the progress of a task that is currently in progress.

---

## متى نستخدمه؟

يستخدم لعرض مدى تقدم عملية لم تكتمل بعد.

مثل:

- File Upload
- Download Progress
- Installation Progress
- Form Completion
- Data Processing
- Loading Tasks

---

## المثال

```
<labelfor="upload">
    Upload Progress</label><progressid="upload"value="40"max="100"></progress>
```

---

## ماذا يحدث؟

يعرض شريط تقدم (Progress Bar).

في هذا المثال:

- القيمة الحالية = 40
- الحد الأقصى = 100

أي أن نسبة الإنجاز هي:

```
40%
```

---

## أشهر الخصائص

يدعم:

- value
- max

---

## ماذا تعني؟

### value

القيمة الحالية.

---

### max

القيمة القصوى.

إذا لم تحدد `max`،

فالقيمة الافتراضية هي:

```
1
```

---

## شريط تقدم غير محدد

إذا حذفت:

```
value
```

سيظهر شريط تقدم غير محدد (Indeterminate Progress)، ويستخدم عندما لا يمكن معرفة نسبة الإنجاز، مثل انتظار استجابة من الخادم.

```
<progress></progress>
```

---

## أشهر أسئلة المقابلات

### Can progress show unknown progress?

✅ نعم.

بحذف الخاصية:

```
value
```

---

# 2. `<meter>`

---

## الإجابة

> The `<meter>` element represents a measurement within a known range.

---

## متى نستخدمه؟

لعرض قيمة لها حد أدنى وحد أقصى.

مثل:

- Disk Usage
- Battery Level
- CPU Usage
- Exam Score
- Temperature
- Storage Capacity

---

## المثال

```
<labelfor="battery">
    Battery</label><meterid="battery"value="75"min="0"max="100"></meter>
```

---

## ماذا يحدث؟

يعرض شريطًا يمثل مستوى البطارية.

وليس تقدم عملية.

---

## أشهر الخصائص

يدعم:

- value
- min
- max
- low
- high
- optimum

---

## ماذا تعني؟

### value

القيمة الحالية.

---

### min

أقل قيمة.

---

### max

أعلى قيمة.

---

### low

الحد الذي تعتبر بعده القيمة منخفضة.

---

### high

الحد الذي تعتبر بعده القيمة مرتفعة.

---

### optimum

أفضل قيمة أو النطاق المثالي.

---

## المثال

```
<metervalue="80"min="0"max="100"low="30"high="80"optimum="100"></meter>
```

---

## أشهر أسئلة المقابلات

### Can meter show progress?

❌ لا.

هو يعرض **قياسًا (Measurement)** وليس **تقدم مهمة (Task Progress)**.

---

# مقارنة بين `<progress>` و`<meter>`

| Feature               | `<progress>` | `<meter>` |
| --------------------- | ------------ | --------- |
| يعرض تقدم مهمة        | ✅ نعم       | ❌ لا     |
| يعرض قياسًا ضمن نطاق  | ❌ لا        | ✅ نعم    |
| يدعم `min`            | ❌ لا        | ✅ نعم    |
| يدعم `max`            | ✅ نعم       | ✅ نعم    |
| يمكن أن يكون غير محدد | ✅ نعم       | ❌ لا     |

---

# أمثلة عملية

## تقدم رفع ملف

```
<progressvalue="65"max="100"></progress>
```

---

## نسبة البطارية

```
<metervalue="65"min="0"max="100"></meter>
```

---

# أشهر أسئلة المقابلات

### What is the difference between progress and meter?

> `<progress>` represents the completion of a task, while `<meter>` represents a value within a known range.

---

### Which element is used for file uploads?

```
<progress>
```

---

### Which element is used for battery level?

```
<meter>
```

---

### Can progress omit the value attribute?

✅ نعم.

وسيظهر كشريط تقدم غير محدد.

---

### Does meter require a range?

نعم، يُستخدم لتمثيل قيمة ضمن نطاق معروف، لذا يفضل تحديد `min` و`max` حتى يكون المعنى واضحًا.

---

# Best Practices

- استخدم `<progress>` عند عرض تقدم مهمة جارية.
- استخدم `<meter>` عند عرض قياس أو مستوى ضمن نطاق معروف.
- اربط العنصر دائمًا بـ `<label>` عند وجود وصف مناسب.
- لا تستخدم `<meter>` لمحاكاة شريط تحميل أو رفع ملفات.

---

# Senior Notes

هناك عدة نقاط يقع فيها كثير من المطورين:

### 1. `progress` ≠ `meter`

رغم أن شكلهما قد يكون متشابهًا، إلا أن معناهما مختلف تمامًا.

مثال:

رفع ملف:

```
65% Uploaded
```

✅ الصحيح:

```
<progress>
```

أما:

بطارية الجهاز:

```
65% Battery
```

✅ الصحيح:

```
<meter>
```

---

### 2. لا تعتمد على الشكل

شكل `<progress>` و`<meter>` يختلف من متصفح إلى آخر ومن نظام تشغيل إلى آخر.

إذا احتجت تصميمًا مخصصًا، استخدم CSS مع مراعاة الحفاظ على الدلالة (Semantics) وإمكانية الوصول.

---

### 3. `meter` ليس بديلًا لـ `progress`

إذا كانت القيمة تمثل **مدى اكتمال مهمة**، فاستخدم:

```
<progress>
```

أما إذا كانت تمثل **حالة أو مستوى** (مثل البطارية، استهلاك الذاكرة، درجة الحرارة)، فاستخدم:

```
<meter>
```

---

كمل Progress Indicators

السؤال

What are the Progress Indicator Elements in HTML, and when should you use each one?

# 6.5 مؤشرات التقدم والقياس (`<progress>` و `<meter>`)

### مثال الكود:

HTML

```
<!-- 1. مؤشر التقدم (Progress Bar): عملية تنزيل جارية -->
<label for="file-download">جاري تحميل الملف:</label>
<progress id="file-download" value="70" max="100">70%</progress>

<br /><br />

<!-- 2. مؤشر القياس (Gauge / Meter): قياس سعة التخزين -->
<label for="disk-usage">مساحة القرص الصلب المستعملة:</label>
<meter
  id="disk-usage"
  value="85"
  min="0"
  max="100"
  low="30"
  high="80"
  optimum="20">
  85%
</meter>
```

### السؤال:

**ما هي عناصر مؤشرات التقدم (Progress Indicator Elements) في HTML، ومتى يجب عليك استخدام كل منها؟**

_(بالإنجليزي: What are the Progress Indicator Elements in HTML, and when should you use each one?)_

### الإجابة النموذجية للمقابلة (Interview Answer):

> **عناصر مؤشرات التقدم والقياس في HTML هي `<progress>` و `<meter>`. يُستخدم عنصر `<progress>` لتمثيل تقدم عملية جارية وله نقطة بداية ونهاية (مثل رفع ملف أو تحميل صفحة). بينما يُستخدم عنصر `<meter>` لعرض قيمة سكونية أو قياس محدد ضمن نطاق معروف (Gauge / Scalar Measurement)، مثل نسبة شحن البطارية، استخدام الذاكرة، أو قوة كلمة المرور.**

### الشرح بالتفصيل:

غالباً ما يقع الكثير من المطورين في خطأ استخدام عنصر `<progress>` لكل أنواع المؤشرات البصرية، أو بناء مؤشرات باستخدام أوسام `<div>` وتنسيقات CSS فقط. لكن كمهندس واجهات (UI Engineer) محترف، يجب أن تفرق دلالياً وبصرياً بين **مؤشر العملية المتقدمة (Progress)** وبين **مؤشر المقياس المستقر (Meter)**.

تعال نفصص العنصرين والفرق الجوهري بينهما:

#### 1. تفكيك العنصرين ووظائفهما

#### أولاً: عنصر `<progress>` (مؤشر التقدم المستمر)

- **الوظيفة:** يمثل عملية تتغير قيمتها تدريجياً مع الوقت نحو الاكتمال (Task Completion).
- **الخصائص الأساسية:**
  - `value`: القيمة الحالية للتقدم.
  - `max`: القيمة النهائية للعملية (الافتراضي هو `1.0`).
- **خاصية مميزة (Indeterminate State):** إذا كتبت الوسم بدون تحديد خاصية `value` (مثل `<progress></progress>`)، سيظهر شريط متحرك بلا نهاية ليعبر عن عملية قيد الانتظار ولكن نسبة إنجازها غير معروفة بعد (مثل البحث أو الاتصال بالسيرفر).

#### ثانياً: عنصر `<meter>` (مؤشر المقياس والقياسات)

- **الوظيفة:** يمثل قياساً ثابتاً أو لحظياً يقع ضمن نطاق محدد مقدماً برقم أدنى وأقصى (Static Gauge).
- **الخصائص الأساسية:**
  - `value`: القيمة الحالية للمقياس (إجبارية).
  - `min` و `max`: الحدود الدنيا والقصوى للمقياس (الافتراضي من `0` إلى `1`).
  - `low` و `high` و `optimum`: تقسيم النطاق إلى مناطق (منخفضة، مرتفعة، والقيمة المثالية). المتصفح يغير لون الشريط تلقائياً (مثلاً للأخضر، الأصفر، أو الأحمر) بناءً على مدى قرب القيمة الحالية من المنطقة المثالية!

#### 2. جدول المقارنة والفرق الجوهري 🔍

| وجه المقارنة            | عنصر `<progress>`                                       | عنصر `<meter>`                                   |
| ----------------------- | ------------------------------------------------------- | ------------------------------------------------ |
| **طبيعة البيانات**      | ديناميكية تتغير باتجاه النهاية (تكتمل بالوصول لـ 100%). | قياس لحظي ثابت أو متذبذب ضمن حدود معروفة.        |
| **الحد الأدنى (`min`)** | لا يوجد (يبدأ دائماً من 0).                             | **يوجد** وتستطيع تحديده عبر خاصية `min`.         |
| **المناطق التقييمية**   | لا يدعم تحديد قيم جيدة أو سيئة.                         | يدعم (`low`, `high`, `optimum`) لتغيير الألوان.  |
| **أفضل حالة استخدام**   | رفع ملف، تحميل صفحة، خطوات إنهاء الطلب.                 | قياس درجة الحرارة، نسبة البطارية، قوة كلمة السر. |

#### 3. لمحة ذكاء للـ UI Engineer (سؤال الفخ للمقابلة)

الـ Interviewer ممكن يسألك: **"كيف نستخدم عنصر `<meter>` لتقييم قوة كلمة المرور، ولماذا لا يصح استخدام `<progress>` لهذا الغرض؟"**

**الإجابة الذكية:**

1. **الفرق الدلالي (Semantic Meaning):**
   - قوة كلمة المرور هي **مقياس للكتلة والجودة (Quality Gauge)** وليست عملية لها بداية ونهاية تتجه للاكتمال التلقائي، لذا فإن استخدام `<progress>` يعتبر خطأ دلالياً (Semantic Error).
2. **الاستفادة من الألوان التلقائية بـ `<meter>`:**
   - باستخدام الخصائص `low="30"` و `high="80"` و `optimum="100"`:
     - إذا كانت قوة كلمة السر 20، المتصفح سيلون الشريط تلقائياً بالأحمر (منطقة ضعيفة).
     - إذا كانت القوة 50، سيلونه بالأصفر (منطقة متوسطة).
     - إذا كانت القوة 90، سيلونه بالأخضر (منطقة ممتازة).

#### الكلمات المفتاحية للحفظ (Keywords):

- **Task Completion (`<progress>`):** مؤشر إنجاز المهام والعمليات الجارية.
- **Scalar Gauge (`<meter>`):** مؤشر القياسات المقاسة ضمن نطاق محدد.
- **Indeterminate State:** حالة الترقب في `progress` عند غياب خاصية `value`.
- **Optimum Values:** القيم المثالية في `meter` التي تحفز التلوين التلقائي.

#### جملتك النموذجية في المقابلة:

> **"`<progress>` and `<meter>` serve distinct semantic roles. We use `<progress>` to communicate the completion status of an ongoing task—like a file upload or download—which can also run in an indeterminate state if `value` is omitted. Conversely, `<meter>` acts as a scalar gauge for a static measurement within a known range, such as disk space, battery level, or password strength. `<meter>` additionally supports thresholds like `low`, `high`, and `optimum` to automatically influence visual styling."**

جاهزون لمتابعة الدروس المتبقية في HTML Forms؟

لكن ف كلا الحالتين يجب ربطهم بالجافاسكريبت ولا اي

سؤال ممتاز جداً وفي صميم عمل مهندس الواجهات (UI Engineer)!

الإجابة المختصرة هي: **ليس بالضرورة في كل الحالتين!** هناك حالة يمكن لـ HTML تشغيلها تلقائياً بدون أي جافاسكريبت، بينما تحتاج الحالة الأخرى للجافاسكريبت لتحدث قيمتها.

تعال نفصصها بوضوح شديد:

## 1. عنصر `<progress>` (هل يحتاج جافاسكريبت؟)

### **نعم، غالباً يحتاج جافاسكريبت.**

- **لماذا؟** لأن عملية مثل "رفع ملف" أو "تحميل بيانات من السيرفر" هي عمليات ديناميكية تجري في الخلفية عبر الـ Browser/Network.
- **دور الجافاسكريبت:** يقوم بقراءة نسبة التحقيق الحقيقية (مثلاً عبر `Axios` أو `Fetch API` أو `XMLHttpRequest`) وتحديث قيمة `progress.value` باستمرار في الـ DOM.

> **استثناء بسيط (بدون جافاسكريبت):** إذا كنت تستخدم `<progress>` كمؤشر خطوة في نموذج متعدد الخطوات (Multi-step Form)، يمكنك تغيير قيمة `value="1"` في الصفحة الأولى، ثم في الصفحة الثانية تحمل صفحة HTML جديدة بها `value="2"` يدوياً من السيرفر بدون جافاسكريبت.

## 2. عنصر `<meter>` (هل يحتاج جافاسكريبت؟)

### **اعتماداً على حالة الاستخدام:**

#### أ) حالات **لا تحتاج** جافاسكريبت على الإطلاق (HTML فقط) ❌ JS

إذا كانت القيمة قادمة جاهزة ومحسوبة مباشرة من السيرفر (Server-Side Rendered) أثناء تحميل الصفحة:

HTML

```
<!-- مثال: عرض نسبة المساحة المتبقية في حساب المستخدم القادمة من الباك إند -->
<p>مساحة التخزين المستعملة:</p>
<meter value="85" min="0" max="100" low="30" high="80" optimum="20">85%</meter>
```

- **هنا المتصفح سيرسم المقياس ويلونه تلقائياً بالأحمر أو الأخضر فور تحميل الصفحة وبدون كتابة سطر جافاسكريبت واحد!**

#### ب) حالات **تحتاج** جافاسكريبت 🟢 JS

إذا كانت القيمة تتغير **تفاعلياً أمام عين المستخدم دون إعادة تحميل الصفحة**:

- **مثال:** فحص قوة كلمة المرور أثناء كتابة المستخدم لها، أو حساب شريط التقييم أثناء تحريك شريط السحب (Slider).

## ملخص المقارنة في جدول سريع:

| العنصر           | هل يعمل بدون JavaScript؟                                                           | متى تحتاج JavaScript؟                                            |
| ---------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------- |
| **`<progress>`** | **محدود جداً** (يظهر فقط كشريط متحرك ثابت بدون نسبة إنجاز حقيقية `indeterminate`). | لتحديث نسبة التحميل/الرفع الفعلية من السيرفر لحظة بلحظة.         |
| **`<meter>`**    | **نعم وبقوة!** (ممتاز جداً للبيانات القادمة جاهزة من الباك إند كقيمة سكونية).      | للتفاعل المباشر مع كتابة المستخدم في الحقول (مثل قوة كلمة السر). |
