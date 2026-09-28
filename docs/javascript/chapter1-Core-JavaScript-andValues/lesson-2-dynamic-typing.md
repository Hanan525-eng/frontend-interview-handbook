# 🟢 Chapter 1 — Lesson 2: Dynamic Typing
### الـ Type بيتبع الـ Value مش الـ Variable

الدرس ده أساس لفهم:

- Type Coercion (الدرس الجاي)
- `typeof`
- ليه بتظهر `TypeError` وإحنا شغالين (Runtime) مش قبلها
- بيانات الـ API والـ forms وإزاي نتعامل معاها بأمان
- ليه TypeScript موجودة، وإيه حدودها

---

## 1. Why it exists — ما المشكلة؟

في لغات زي Java أو TypeScript لازم تحددي نوع المتغير وقت تعريفه:

```ts
// TypeScript
let age: number = 25;
age = "Hanan"; // ❌ الخطأ بيتكشف قبل ما الكود يشتغل
```

في JavaScript:

```js
let age = 25;
age = "Hanan";
age = true;
// ✅ كله شغال، ومفيش اعتراض
```

JavaScript اتصممت سنة 1995 في Netscape كلغة سكريبت خفيفة وسهلة لتفاعل صفحات الويب، فاتبنت على المرونة والبداية السريعة من غير ما تعلني نوع كل متغير. المقابل لده إن أخطاء الأنواع بتتأجل لوقت التشغيل.

السؤال اللي بيبدأ منه الفهم:

> إزاي JavaScript بتسمح لنفس المتغير إنه يشاور على قيم أنواعها مختلفة؟ وإيه التمن اللي بندفعه مقابل المرونة دي؟

---

## 2. Concept — إيه هو Dynamic Typing؟

> **في JavaScript الـ Type مرتبط بالـ Value، مش بالـ Variable. والقواعد المرتبطة بالأنواع بتتطبق وقت التشغيل، لما العملية تتنفذ فعلاً.**

يعني لازم نفرّق بين ثلاث حاجات:

```
Variable  →  Value  →  Type
```

لما نقول `let x = 10` وبنقول "x نوعه number"، ده اختصار مفيد في الكلام، لكن الأدق إن **القيمة `10`** هي اللي نوعها number.

---

## 3. Mental Model 🧠

```
let value = 10;
value ────► 10        (number)

value = "Hanan";
value ────► "Hanan"   (string)

value = true;
value ────► true      (boolean)
```

المتغير نفسه ما بقاش "number ثم string ثم boolean". هو بس **اتربط** بقيم أنواعها مختلفة.

**ملاحظة على تشبيه الصندوق:** لو حبيتي تتخيلي المتغير كصندوق بيشيل القيمة، ده مقبول مع الـ primitives. لكن مع الـ objects الصندوق بيشيل **reference** لمكان الـ object (زي ما شفنا في الدرس الأول). عشان كده الصورة الأدق دايماً: متغير **بيشاور على** قيمة (مش "القيمة اللي جواه")، والقيمة هي اللي ليها Type.

---

## 4. How JavaScript actually behaves

### أ) الأنواع موجودة فعلاً

```js
typeof "Hello";   // "string"
typeof 42;        // "number"
typeof true;      // "boolean"
typeof undefined; // "undefined"  ← نوع مستقل بذاته، مش boolean
typeof 10n;       // "bigint"
typeof Symbol();  // "symbol"
typeof {};        // "object"
typeof [];        // "object"     ← الـ arrays objects
typeof null;      // "object"     ← quirk تاريخي (زي ما شفنا في الدرس الأول)
```

```
Dynamic Typing ≠ No Types
Dynamic Typing = أنواع موجودة + بتتحدد/بتتعامل معاها وقت التشغيل
               + المتغير ممكن يشاور على قيم أنواعها مختلفة
```

> **تنبيه:** `undefined` بتتصرف زي `false` جوه الـ `if` (بنسميها falsy)، لكن ده مش معناه إنها boolean. كونها falsy موضوع تاني (ToBoolean) هنشرحه في الدرس الجاي.

### ب) الـ assignment مبيفحصش النوع، العمليات هي اللي بتفرق

JavaScript ما بتعترض لما تعملي `value = "Hello"` بعد ما كان `10`. لكن لما تنفذي **عملية** على القيمة، النتيجة بتبقى واحدة من التلاتة دول:

1. **تشتغل عادي:** `10 * 2` ← `20`
2. **تحوّل النوع بصمت (Coercion):** `"5" * 2` ← `10`، و`"Hello" * 2` ← `NaN` (من غير أي error!)
3. **ترمي TypeError:** زي `null.theme`

النوعين التاني والتالت هما مصدر أغلب bugs الأنواع في الواقع. والتاني ده بالذات هو موضوع الدرس الجاي (Type Coercion).

### ج) `let` و`const` مالهمش علاقة بتغيير الـ Type

```js
let a = 10;
a = "Hello";   // ✅ let بيسمح بإعادة الربط (reassignment)

const b = 10;
b = "Hello";   // ❌ TypeError: Assignment to constant variable.
```

`const` بيمنع **reassignment** للمتغير نفسه. السبب مش إن `10` ما ينفعش تبقى string، السبب إن المتغير ما ينفعش يتربط بقيمة تانية أصلاً (حتى لو من نفس النوع).

### د) Mutation مش Dynamic Typing

```js
let data = { name: "Hanan" };
data.name = "Ahmed";  // mutation للـ object (الدرس الأول)
data = [1, 2, 3];     // reassignment لقيمة نوعها اتغير
```

### هـ) Static vs Dynamic — الصورة الكبيرة

| | Static (TypeScript/Java) | Dynamic (JavaScript) |
|---|---|---|
| متى بيتفحص النوع؟ | قبل التشغيل (build) | وقت التشغيل، لما العملية تتنفذ |
| الخطأ بيظهر فين؟ | في الـ editor أو الـ build | عند المستخدم لو ماتلقطش |
| الـ Type مرتبط بإيه؟ | بالمتغير (annotation) | بالـ value |

> **ملاحظة:** مصطلح "Weakly typed" بيتقال كتير على JavaScript، لكنه مصطلح غير محدد بدقة وبيتستخدم بمعاني مختلفة. اللي بيقصدوه غالباً هو **Implicit Coercion** (تحويل الأنواع تلقائياً في العمليات)، وده موضوع الدرس الجاي. فبنستخدم المصطلحين الدقيقين: **Dynamic Typing** و**Type Coercion**.

---

## 5. Code Examples (Predict first ✍️)

### مثال أ — الـ typeof مع قيمة متغيرة

```js
let value = 10;
console.log(typeof value);

value = "Hello";
console.log(typeof value);

value = [1, 2, 3];
console.log(typeof value);

value = null;
console.log(typeof value);
```

<details>
<summary>الإجابة</summary>

```
"number"
"string"
"object"
"object"
```

الـ array نوعه `"object"` برضه (الـ arrays objects). و`null` نتيجتها `"object"` بسبب الـ quirk التاريخي. الـ `typeof` بيقرا نوع **القيمة الحالية** اللي المتغير بيشاور عليها.
</details>

### مثال ب — عمليات على أنواع مختلفة

```js
console.log("5" * 2);
console.log("Hello" * 2);
```

<details>
<summary>الإجابة</summary>

```
10
NaN
```

مفيش أي error في الحالتين. JavaScript حاولت تحوّل الـ string لرقم. مع `"5"` نجحت، ومع `"Hello"` طلعت `NaN`. ده بالظبط نوع الـ bug الصامت اللي هنتكلم عنه في Type Coercion.
</details>

### مثال ج — TypeError وقت التشغيل

```js
let config = { theme: "dark" };
config = null;
console.log(config.theme);
```

<details>
<summary>الإجابة</summary>

```
TypeError: Cannot read properties of null (reading 'theme')
```

JavaScript ما اعترضتش على `config = null`. الخطأ ظهر **بعدين**، وقت ما العملية `config.theme` اتنفذت فعلاً على قيمة `null`.
</details>

---

## 🎯 Extra Practice — 3 أكواد جديدة (Predict)

اكتبي توقعك لكل سطر `console.log` **قبل** ما تفتحي الإجابة.

### كود 1 — تغيير النوع خطوة بخطوة

```js
let x = 42;
console.log(typeof x);

x = "42";
console.log(typeof x);

x = x * 1;
console.log(typeof x);

x = undefined;
console.log(typeof x);

x = [42];
console.log(typeof x);
```

<details>
<summary>الإجابة</summary>

```
"number"
"string"
"number"
"undefined"
"object"
```

- `"42" * 1` ← الـ string اتحوّلت لرقم `42` (Coercion).
- `typeof undefined` بترجع `"undefined"`: نوع مستقل بذاته. **مش `"boolean"`**، حتى لو `undefined` بتتصرف زي `false` في الـ `if`.
- الـ array نوعه `"object"`.
</details>

---

### كود 2 — متى يظهر الخطأ بالظبط؟

```js
let user = { name: "Hanan" };
console.log(user.name);

user = undefined;
console.log("before");
console.log(user.name);
console.log("after");
```

**اسألي نفسك:** إيه اللي هيتطبع بالترتيب؟ هل `"after"` هتتطبع؟ والخطأ بيظهر في أنهي سطر بالظبط؟

<details>
<summary>الإجابة</summary>

```
Hanan
before
TypeError: Cannot read properties of undefined (reading 'name')
```

`"after"` **مش هتتطبع**: الـ `TypeError` ما اتمسكش (uncaught)، فالسكريبت وقف عند السطر اللي حصل فيه الخطأ.

الخطأ ظهر عند السطر `user.name` (وقت تنفيذ العملية)، **مش** عند `user = undefined`. JavaScript سمحت بالـ assignment، والعملية هي اللي فشلت.
</details>

---

### كود 3 — mutation مقابل reassignment مع `const`

```js
const items = ["a", "b"];
items.push("c");
console.log(items.length);

items = "abc";
console.log(items);
```

**اسألي نفسك:** هيطبع إيه في أول `console.log`؟ إيه اللي هيحصل عند `items = "abc"`؟ وهل تاني `console.log` هتشتغل؟

<details>
<summary>الإجابة</summary>

```
3
TypeError: Assignment to constant variable.
```

- `items.push("c")` **mutation** لنفس الـ array، فاشتغلت عادي والـ length بقت `3`.
- `items = "abc"` **reassignment**، و`const` بيمنعه، فبيرمي `TypeError` محدد (مش بس "مش هتشتغل").
- تاني `console.log` ما اتنفذتش لأن الخطأ وقف الكود.
</details>

---

## 6. Common Mistakes / Misconceptions

**❌ "JavaScript مفيهاش Types"**
عندها types واضحة. اللي مفيهاش هو إعلان النوع على المتغير.

**❌ "Dynamic Typing معناها إن أي عملية تنفع على أي نوع"**
فيه قواعد للعمليات، وفيه Coercion، وفيه `TypeError`.

**❌ "`let` هو اللي بيخلي JavaScript dynamic"**
JavaScript نفسها dynamically typed. `let` بيسمح بإعادة الربط، بس ده مش سبب الـ dynamic typing.

**❌ "`const` بيمنع تغيير الـ Type"**
`const` بيمنع reassignment فقط.

**❌ "`undefined` نوعها boolean" (أو "زي false")**
`undefined` نوع مستقل. كونها falsy في الـ `if` مالوش علاقة بنوعها.

**❌ استخدام نفس الاسم لقيم أنواعها مختلفة في نفس الدالة**
```js
let id = "42";        // string
id = { value: 42 };   // فجأة object
```
الكود شغال، لكن اللي هيقرأه (أو أنتِ بعد شهر) هيتوه في تتبع نوع القيمة في كل سطر.

**❌ افتراض شكل البيانات القادمة من خارج الكود**
API أو form أو `localStorage`: JavaScript مش هتقولك إن الـ shape مش زي ما توقعتي.

---

## 7. Real Front-End Examples

### مثال 1 — قيمة الـ input دايماً string

```jsx
const [quantity, setQuantity] = useState(10); // number في البداية

const handleChange = (e) => {
  setQuantity(e.target.value); // ⚠️ string حتى لو input type="number"
};

const handleAddStock = () => {
  console.log(quantity + 5);
};
```

لو المستخدم كتب `5`:

```
quantity = "5"     (بقت string بصمت)
"5" + 5  →  "55"   (دمج نصوص مش جمع!)
```

المتغير `quantity` بدأ number وبقى string من غير ما JavaScript تقولك أي حاجة.

**الحل:** نحوّل النوع عند الحدود (لحظة استقبال القيمة من الـ input):

```jsx
const [input, setInput] = useState("10");   // اللي المستخدم كتبه (string)
const quantity = Number(input);              // القيمة الرقمية المشتقة

const handleChange = (e) => setInput(e.target.value);
const handleAddStock = () => {
  if (Number.isNaN(quantity)) return;        // حماية من قيم غير صالحة
  console.log(quantity + 5);
};
```

> نقطة تصميم: `Number("")` بترجع `0`. يعني الحقل الفاضي هيتحسب صفر. لو ده مش السلوك المطلوب لازم نتعامل معاه صراحة. (الدرس الجاي هيشرح ليه.)

### مثال 2 — شكل رد الـ API

```js
const response = await fetch("/api/users");
const data = await response.json();

data.users.map(renderUser);  // 💥 لو users طلعت null
```

JavaScript مش هتحذرك وقت الكتابة إن `users` ممكن تبقى `null`. الحل إننا نتحقق عند الحدود:

```js
const users = Array.isArray(data.users) ? data.users : [];
users.map(renderUser);
```

---

## 8. Interview Question 🎯

> **What's the difference between dynamic typing and static typing?**

إجابة ناقصة: *"في JavaScript تقدري تغيّري نوع المتغير."* (وصف للسطح بس)

الإجابة الأدق:

> In dynamic typing, types belong to values rather than variables, and type rules are enforced at runtime when operations execute. In static typing, types are checked before the program runs. TypeScript adds static checking at build time on top of JavaScript, but its types are erased at runtime, so data coming from outside the app (APIs, forms, storage) still needs runtime validation.

📌 **ملاحظة (Deep Dive — الفصل 14):** محركات زي V8 بتحسّن الكود بناءً على الأنواع اللي بتشوفها فعلاً، فثبات الأنواع في الكود بيساعد الأداء. التفاصيل هتتشرح في فصل Engine Internals، مش هنا.

---

## 🧠 Senior Thinking

السؤال مش: "هل JavaScript dynamic typed؟" ده سؤال مبتدئ.

السؤال الأهم:

> **طالما JavaScript dynamic typed، إزاي أخلي الكود متوقّع (predictable) في مشروع كبير؟**

الإجابة بتبدأ من عند **حدود النظام** (المكان اللي بيانات من برة بتدخل منه):

```
API / Form / localStorage / URL params
              ↓
   تحقق + تحويل نوع مرة واحدة هنا (boundary)
              ↓
   Shape ثابت وواضح للـ state
              ↓
   باقي الكود يشتغل على أنواع مضمونة
```

- كل متغير ياخد نوع واحد طول حياته في الدالة.
- TypeScript بتساعد وقت التطوير (مرحلة لاحقة في الخطة).
- Runtime validation ضرورية للبيانات الخارجية لأن TypeScript types بتتمسح وقت التشغيل.

---

## 🛠 Practice — Build It  ⏸ (مؤجل لحد ما نخلص Type Coercion)

**الموقف:** المستخدم بيكتب كمية في حقل input، مثلاً `12`. اللي بيوصلك من الحقل دايماً **string** (`"12"`) مش رقم.

**المطلوب:** دالة `toNumberOrNull(value)` تاخد النص ده وترجّع:

- **الرقم** لو المدخل رقم صالح.
- **`null`** لو المدخل فاضي، أو مسافات بس، أو مش رقم.

```js
function toNumberOrNull(value) {
  // اكتبي الجسم هنا
}
```

| المدخل | المطلوب يرجع |
|---|---|
| `"12"` | `12` |
| `"0"` | `0` |
| `""` (فاضي) | `null` |
| `"   "` (مسافات) | `null` |
| `"abc"` | `null` |

**ليه `null` مش `0`؟** لأن `0` كمية صالحة (مخزون صفر مثلاً). لازم يبقى فيه إشارة تفرّق بين "المستخدم كتب صفر" و"المستخدم مكتبش حاجة".

**تحضير قبل ما نرجعله:** جربي في الـ Console وشوفي النتايج بس (من غير ما تفسّري):

```js
Number("")
Number("   ")
Number("abc")
Number("12")
```

هتلاقي إن `Number("")` بترجع `0` مش `NaN`، وده الفخ اللي التمرين مبني عليه. بعد ما نخلص Type Coercion هنفهم ليه، ونرجع نحله.

## 💥 Practice — Break It

```js
let price = "200";

price = price + 50;
console.log(price, typeof price);

price = price - 10;
console.log(price, typeof price);
```

**Predict first ✍️** قبل التشغيل: قيمة ونوع `price` بعد كل خطوة؟

<details>
<summary>الإجابة</summary>

```
"20050" "string"
20040 "number"
```

`+` لما يكون أحد طرفيه string بيعمل دمج نصوص. أما `-` فمعمول للأرقام بس، فبيحوّل الـ string لرقم. نفس المتغير غيّر نوعه مرتين في سطرين. ده تمهيد للدرس الجاي.
</details>

---

## 🔄 Recap

```
Variable ──► Value ──► Type
النوع بيتبع القيمة، مش المتغير

Dynamic Typing ≠ No Types
الـ assignment مبيفحصش النوع، والعمليات هي اللي بتتفاعل معاه (تشتغل / Coercion / TypeError)

let / const  →  reassignment، مالهمش علاقة بتغيير الـ Type
undefined    →  نوع مستقل، مش boolean
TypeScript   →  static checking وقت البناء، وبتتمسح وقت التشغيل
```

---

## ✅ Self-Check

**1. Define** — عرّفي Dynamic Typing بكلامك، وفيها جملة "الـ Type بيتبع الـ Value"، ووضّحي ليه ده مش معناه "مفيش Types".

**2. Predict** — جاوبي على الأكواد الجديدة في قسم Extra Practice، واكتبي توقعك قبل ما تفتحي الإجابة.

**3. Why** — اكتبي فقرة قصيرة: "JavaScript اتصممت dynamic typed عشان... والتمن اللي بندفعه هو..."

**4. Apply** — إمتى المرونة دي مفيدة وإمتى بنحتاج نحميها بـ validation؟ (مثال عام: قيمة جاية من form أو من API مقابل متغير محلي جوه دالة صغيرة).

**5. Debug** — ظهر `TypeError: Cannot read properties of null` عند المستخدمين بعد ما الـ API اتغير. إيه أول 3 حاجات هتفحصيها؟

> قاعدة: لو بند واحد من الخمسة ما اتحقّقش، الموضوع لسه ما اتقنش.

### ✍️ صياغات دقيقة (لتفادي الالتباس)

| ❌ بدل ما تقولي | ✅ قولي |
|---|---|
| "القيمة اللي جواه" | "القيمة اللي بيشاور عليها" |
| "`x` نوعه number" | "القيمة `10` نوعها number" |
| "لازم نحدد الـ type" | "لازم نتحقق من النوع أو نحوّله" |
| "JS خفيفة في التعامل مع المتصفحات" | "JS لغة سكريبت خفيفة وسهلة لتفاعل صفحات الويب" |
| "مش هتشتغل" (لسطر بيرمي خطأ) | "هترمي `TypeError: ...`" (اسم الخطأ ورسالته) |
| "`undefined` زي boolean" | "`undefined` نوع مستقل، بس بتتصرف كـ falsy" |

### 📝 نموذج إجابات (اقري بعد ما تكتبي إجابتك بنفسك)

<details>
<summary>1. Define</summary>

> **Dynamic Typing** معناها إن الـ Type بيتبع الـ Value مش الـ Variable: المتغير بيشاور على قيمة، والقيمة هي اللي ليها نوع، وممكن نربط نفس المتغير بقيمة نوعها مختلف لأن JavaScript مبتفحصش النوع لحظة الـ assignment.
>
> ودي **مش معناها "مفيش Types"**، لأن كل قيمة ليها نوع فعلي (`typeof` بيقراه) والعمليات بتتصرف حسبه: بتشتغل، أو Coercion، أو `TypeError`. اللي مش موجود هو **إعلان النوع على المتغير** وفحصه قبل التشغيل.
</details>

<details>
<summary>3. Why</summary>

> اتصممت JavaScript كلغة سكريبت خفيفة وسهلة لتفاعل صفحات الويب من غير إعلان أنواع. **التمن** إن أخطاء الأنواع بتتأجل لوقت التشغيل: بتظهر عند المستخدم كـ `TypeError`، أو بتعدّي بصمت كنتيجة غلط (زي `"5" + 5` ← `"55"`، أو `NaN`). عشان كده بنتحقق من النوع أو نحوّله عند حدود البيانات الخارجية.
</details>

<details>
<summary>4. Apply</summary>

| الموقف | القرار |
|---|---|
| متغير محلي جوه دالة صغيرة، نوعه واضح ومش بيتغير | المرونة كفاية |
| قيمة جاية من **form input** | تحويل صريح للنوع عند الاستقبال (`Number(...)`) + فحص `NaN` |
| رد **API** أو `localStorage` أو URL params | فحص الشكل والنوع قبل الاستخدام (زي `Array.isArray`) |
| مشروع كبير بأكتر من مطور | TypeScript وقت التطوير، **بالإضافة** لفحص وقت التشغيل للبيانات الخارجية |

**القاعدة:** كل ما البيانات جاية من مكان **مش بتتحكمي فيه**، حطي فحص عند الحدود. وكل ما القيمة جوه كودك ونوعها معروف، المرونة كفاية.
</details>

<details>
<summary>5. Debug</summary>

أول 3 حاجات بالترتيب:

1. **إيه القيمة الفعلية عند السطر اللي فيه الخطأ؟** أطبعها وأشوف نوعها (`console.log` أو `debugger`)، وأعرف أنهي property هي `null` بالظبط (الرسالة نفسها بتقول `reading '...'`).
2. **القيمة دي جت منين؟** أرجع خطوة خطوة: من الـ API response ← لـ state ← للـ component. وأقارن شكل الرد الجديد بالقديم (هل `users` بقت `null` بدل array؟).
3. **هل فيه مسار بتكون فيه القيمة فاضية؟** زي حالة الـ loading قبل ما الرد يوصل، أو رد فاضي، أو request فشل. ولو لقيت المسار، الحل يبقى فحص عند الحدود (زي `Array.isArray(data.users) ? data.users : []`) مش مجرد "ترقيع" في السطر اللي وقع.
</details>

---

**الدرس الجاي في نفس الفصل:** 🟢 Type Coercion — إزاي JavaScript بتحوّل الأنواع تلقائياً في العمليات، وليه `"5" + 5` و`"5" - 5` بيدّوا نتائج مختلفة، وبعدها نرجع لتمرين `toNumberOrNull`.