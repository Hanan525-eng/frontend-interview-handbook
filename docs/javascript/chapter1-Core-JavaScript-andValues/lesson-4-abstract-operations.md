# 🟢 Chapter 1 — Lesson 4: Abstract Operations
### `ToPrimitive` / `ToBoolean` / `ToNumber` / `ToString`

في الدرس اللي فات فهمنا إن الجافاسكريبت بتعمل `Type Coercion`. الدرس ده بيفتح الصندوق الأسود ويوريكي **بالظبط** إزاي التحويل ده بيحصل جوه اللغة.

---

## 1. Why it exists

في الدرس اللي فات شفنا:

```js
"5" - 2 // 3
```

وقلنا إن ده `Implicit Coercion`. لكن السؤال الأعمق:

> "الجافاسكريبت حوّلت القيمة" — ده معناه إيه بالظبط؟ وإزاي؟

مواصفة اللغة (`ECMAScript Specification`) بتوصف عمليات داخلية محددة بدقة، اسمها `Abstract Operations`، زي:

```
ToPrimitive
ToBoolean
ToNumber
ToString
```

**مهم:** دول مش دوال بتناديها في كودك بالشكل ده:

```js
ToNumber(value); // ❌ ده مش موجود كده في الكود
```

هي خطوات داخلية بتستخدمها الجافاسكريبت وقت تنفيذ عمليات معينة. فهمها بيحوّلك من حافظة أمثلة متفرقة (`"5" + 2 = "52"`) لحد فاهم **القاعدة اللي بتولّد كل الأمثلة دي**.

---

## 2. Concept — الصورة الكبيرة

```
                 عملية في الجافاسكريبت
                         │
                         ▼
                 هل محتاجة تحويل القيمة؟
                         │
          ┌──────────────┼──────────────┐
          ▼              ▼              ▼
     ToPrimitive      ToBoolean      ToNumber
          │                             │
          ▼                             ▼
       Primitive                      Number

                  وفيه كمان:
                   ToString
```

الهدف مش حفظ كل خطوة في الـ `Spec`، لكن إنك تقدري تسألي نفسك: **أنهي تحويل حصل، وليه، والنتيجة إيه؟**

---

## 3. `ToBoolean` — أبسط عملية

`ToBoolean` بتحوّل أي قيمة لـ `true` أو `false`، بناءً على قائمة ثابتة اسمها `Falsy Values` (شفناها في الدرس اللي فات):

```js
Boolean(1)        // true
Boolean(0)        // false
Boolean("Hello")  // true
Boolean("0")      // true  ← نص غير فاضي، حتى لو شكله "صفر"!
```

النقطة المهمة: `0` (رقم) مختلف تماماً عن `"0"` (نص):

```
0    → falsy
"0"  → truthy
```

`ToBoolean` بتظهر في أي مكان بيتحقق من صحة قيمة:

```js
if (value) { }
value && doSomething();
const result = value || defaultValue;
```

---

## 4. `ToNumber`

```js
Number("42")       // 42
Number("  42  ")   // 42   ← المسافات بتتجاهل
Number("")         // 0    ← مفاجأة شائعة
Number("Hanan")    // NaN
Number(true)       // 1
Number(false)      // 0
Number(null)       // 0
Number(undefined)  // NaN  ← لاحظي الفرق عن null
```

`null` و`undefined` ليهم نفس المعنى المنطقي ("مفيش قيمة")، لكن `ToNumber` بتتعامل معاهم مختلف تماماً. دي من أكتر النقط اللي بتسبب bugs لو اتفترضت غلط.

---

## 5. `ToString`

```js
String(42)         // "42"
String(true)        // "true"
String(null)        // "null"
String(undefined)   // "undefined"
```

وهنا بيبان ليه `+` بتعمل دمج نصوص:

```
"Age: " + 25
     ↓
"Age: " + ToString(25)
     ↓
"Age: " + "25"
     ↓
"Age: 25"
```

**تنبيه:** مش كل حالات `+` بتتفسر بـ `ToString` بس. لو طرف من الطرفين `Object`، بتتدخل `ToPrimitive` الأول، وده موضوع الفقرة الجاية.

---

## 6. `ToPrimitive` — أهم عملية في الدرس

لحد دلوقتي كل العمليات واضحة الهدف (`Boolean`, `Number`, `String`). لكن إيه اللي بيحصل لو الجافاسكريبت عندها `Object` ومحتاجة قيمة `Primitive` منه؟

```js
const user = { name: "Hanan" };
console.log(user + "");
```

هنا عندنا `Object + String`. الجافاسكريبت **مش قادرة تجمع Object زي ما هو**، فبتسأل:

> "إيه القيمة الأولية (`Primitive`) المناسبة للـ `Object` ده؟"

وهنا بتتدخل `ToPrimitive`.

### إزاي `ToPrimitive` بتقرر؟

بتجرّب دالتين جوه الـ `Object` بترتيب معين، حسب نوع التحويل المطلوب (`hint`):

- **لو محتاجة Number** (`hint: "number"`): تنادي `valueOf()` الأول، ولو مرجعتش `Primitive`، تنادي `toString()`.
- **لو محتاجة String** (`hint: "string"`): تنادي `toString()` الأول، ولو مرجعتش `Primitive`، تنادي `valueOf()`.
- **لو مفيش تفضيل واضح** (`hint: "default"`, زي حالة `+`): الترتيب الافتراضي زي `"number"` (يعني `valueOf()` الأول)، **إلا كائن `Date` اللي معمول عكسي تماماً** (هنوضحه تحت).

```
Object
  │
  ▼
ToPrimitive
  │
  ▼
Primitive
  │
  ├──────────────┐
  ▼              ▼
ToNumber       ToString
```

### مثال بسيط

```js
const obj = {
  valueOf() {
    return 10;
  }
};
console.log(obj + 5);
```

```
obj + 5
→ ToPrimitive(obj)  → valueOf() بترجع 10
→ 10 + 5
→ 15
```

### `Symbol.toPrimitive` — التحكم الكامل

ممكن تتحكمي بنفسك في سلوك `ToPrimitive` للـ `Object` بالكامل:

```js
const user = {
  name: "Hanan",
  score: 100,
  [Symbol.toPrimitive](hint) {
    if (hint === "number") return this.score;
    if (hint === "string") return `User: ${this.name}`;
    return this.score; // default
  }
};

console.log(+user);          // hint: "number"  → 100
console.log(`${user}`);      // hint: "string"  → "User: Hanan"
console.log(user + " pts");  // hint: "default" → "100 pts"
```

> ملاحظة صياغة: `[Symbol.toPrimitive]` لازم تتكتب بين `[ ]` (مش `Symbol.toPrimitive` مباشرة) لأنها اسم خاصية محسوبة (`computed property name`)، مش اسم عادي.

تفاصيل `Symbol.toPrimitive` و`Well-Known Symbols` هنتعمق فيها لاحقاً في فصل `Objects & Prototypes`. المطلوب دلوقتي بس إنك تفهمي المبدأ.

---

## 7. استثناء مهم: `Date`

كائن `Date` معمول بطريقة خاصة في اللغة: مع `hint: "default"`، بيفضّل `toString()` **قبل** `valueOf()` (عكس القاعدة العامة). عشان كده:

```js
const startDate = new Date("2026-01-01");
const endDate = new Date("2026-01-10");

console.log(startDate + endDate);
// نص غريب: دمج تاريخين كنصوص (toString اتنادت)

console.log(endDate - startDate);
// 777600000  ← الفرق بالـ milliseconds (ToNumber اتفرضت)
```

`-` دايماً بتفرض `hint: "number"` (زي باقي العمليات الحسابية غير `+`)، فـ `Date` بترجع الـ `timestamp` بتاعها كرقم. أما `+` فبتدّي `hint: "default"`، و`Date` تحديداً بتختار `toString()` فيها، فبيحصل دمج نصوص مش طرح.

```js
const diffInDays = (endDate - startDate) / (1000 * 60 * 60 * 24); // 9
```

---

## 8. Code Examples (Predict first ✍️)

### مثال أ — نفس القيمة، تحويلات مختلفة

```js
console.log(Number(null));
console.log(Number(undefined));
console.log(Boolean(null));
console.log(Boolean(undefined));
console.log(String(null));
console.log(String(undefined));
```

<details>
<summary>الإجابة</summary>

```
0
NaN
false
false
"null"
"undefined"
```

`null` و`undefined` بيتصرفوا **نفس الحاجة** مع `ToBoolean` (الاتنين falsy)، لكن **مختلفين** مع `ToNumber` (`0` مقابل `NaN`). ده دليل إن مفيش "قاعدة واحدة شاملة"، كل عملية (`ToBoolean`/`ToNumber`/`ToString`) ليها منطقها الخاص.
</details>

### مثال ب — `valueOf()` وتأثيرها الجانبي (side effect)

```js
const counter = {
  num: 10,
  valueOf() {
    return this.num--;
  }
};

console.log(counter + 1);
console.log(counter + 1);
console.log(counter + 1);
```

<details>
<summary>الإجابة</summary>

```
11
10
9
```

`this.num--` هي `post-decrement`: بترجع القيمة **الحالية الأول**، وبعدين تنقص بواحد.

```
المرة 1: num=10 → valueOf() ترجع 10، وnum بقت 9  →  10+1 = 11
المرة 2: num=9  → valueOf() ترجع 9،  وnum بقت 8  →  9+1  = 10
المرة 3: num=8  → valueOf() ترجع 8،  وnum بقت 7  →  8+1  = 9
```

كل استدعاء لـ `valueOf()` **غيّر حالة الـ object نفسه**. ده مبدأ خطير ومهم: `ToPrimitive` مش عملية "قراءة بريئة"، ممكن يكون ليها أثر جانبي لو الـ object مكتوب كده.
</details>

---

## 9. Common Mistakes / Misconceptions

**❌ افتراض إن `Number(undefined)` بترجع `0` زي `null`**
`null → 0` لكن `undefined → NaN`. الخلط بينهم بيسبب حسابات غلط لما دالة متستلمش argument.

**❌ الاعتقاد إن `ToPrimitive` دايماً بتنادي `valueOf()` أول حاجة**
ده صح بس مع `hint: "number"` أو `"default"` في الحالة العامة. مع `hint: "string"` الترتيب معكوس. وكائن `Date` عنده استثناء خاص حتى مع `"default"`.

**❌ التعامل مع `ToPrimitive` كـ "تحويل آمن بدون أثر جانبي"**
زي ما شفنا في مثال `counter`، `valueOf()` ممكن تغيّر حالة الـ object. استخدام objects بالشكل ده في production محتاج حذر شديد.

---

## 10. Real Front-End Example

```js
// ❌ طريقة خطأ لحساب الفرق بين تاريخين
const sum = startDate + endDate; // نص مدموج غريب

// ✅ الطرح يجبر ToNumber فيرجع الفرق بالـ milliseconds
const diffInDays = (endDate - startDate) / (1000 * 60 * 60 * 24);
```

نفس المبدأ بيظهر في أي حساب بيستخدم تواريخ في جداول أو تقارير ERP: لازم نستخدم `-` أو `.getTime()` صراحة بدل الاعتماد على `+`.

---

## 11. Interview Question 🎯

> **How can you make an object so that `if (a == 1 && a == 2 && a == 3)` evaluates to `true`?**

```js
const a = {
  value: 1,
  valueOf() {
    return this.value++;
  }
};

if (a == 1 && a == 2 && a == 3) {
  console.log("Magic!"); // هيتنفذ!
}
```

الإجابة الكاملة:

> Each `==` comparison triggers `ToPrimitive` on `a`, which calls `valueOf()`. Since `valueOf()` increments and returns `this.value` each time it's called, `a` evaluates to a different number on each comparison. This demonstrates that `==` can be manipulated through object internals, which is one reason senior engineers default to `===` — it never triggers this kind of implicit, stateful coercion.

---

## 🧠 Senior Thinking

في مقابلة سينيور ممكن يسألوك:

> **Why does JavaScript behave differently with `"5" + 2` and `"5" - 2`؟**

الإجابة الضعيفة: *"لأن `+` للجمع و`-` للطرح"* ❌

الإجابة القوية:

> The operators have different coercion semantics. `-` always requires numeric operands, so `ToNumber` is applied. `+` can perform either numeric addition or string concatenation; when either operand is (or becomes, via `ToPrimitive`) a string, string concatenation is selected and the other operand goes through `ToString`.

**السؤال الأعم اللي السينيور بيسأله لنفسه:** ليه الجافاسكريبت وزّعت التحويل على 4 عمليات منفصلة (`ToPrimitive`/`ToBoolean`/`ToNumber`/`ToString`) بدل قاعدة واحدة شاملة؟ الإجابة: لأن كل سياق (شرط، عملية حسابية، دمج نصوص، عملية على object) له معنى مختلف، ومحتاج تحويل مختلف يراعي المعنى ده.

---

## 🛠 Practice — Build It

اكتبي `Object` اسمه `money`، بحيث:

```js
console.log(money + 50);       // رقم: 150
console.log(`${money}`);       // نص: "$100"
```

استخدمي `[Symbol.toPrimitive](hint)` عشان تتحكمي في الناتج حسب الـ `hint`، على افتراض إن الرصيد الأساسي `100`.

## 💥 Practice — Break It

```js
const cleanObj = Object.create(null);
console.log(cleanObj + " test");
```

**Predict first ✍️** إيه اللي هيحصل؟

<details>
<summary>الإجابة</summary>

```
TypeError: Cannot convert object to primitive value
```

`Object.create(null)` بتنشئ object **من غير Prototype خالص**، يعني مفيش `valueOf()` ولا `toString()` موروثين. لما `ToPrimitive` تحاول تستدعيهم، تلاقيهم مش موجودين، فالعملية بتفشل بـ `TypeError`.
</details>

---

## 🔄 Recap

```
Abstract Operations = خطوات داخلية في الـ Spec، مش دوال تناديها مباشرة

ToBoolean  → أي قيمة → true/false (حسب Falsy Values)
ToNumber   → أي قيمة → رقم (null→0, undefined→NaN)
ToString   → أي قيمة → نص
ToPrimitive → Object → Primitive (عبر valueOf/toString حسب hint)

hint "number"  → valueOf() الأول
hint "string"  → toString() الأول
hint "default" → زي number، إلا Date (عكسي: toString الأول)

valueOf() ممكن يكون ليها أثر جانبي (side effect) — مش عملية قراءة بريئة دايماً
```

---

## ✅ Self-Check

**1. Define** — عرّفي `Abstract Operations` بكلامك، ووضّحي الفرق الجوهري بين `ToPrimitive` والتلاتة التانيين.

**2. Predict** — جاوبي على 2-3 أكواد جديدة فيها `valueOf()`/`toString()` مخصصة، واكتبي توقعك قبل التشغيل.

**3. Why** — اكتبي فقرة: "الجافاسكريبت قسّمت التحويل لعمليات منفصلة (`ToBoolean`/`ToNumber`/`ToString`/`ToPrimitive`) عشان..."

**4. Apply** — إمتى تكتبي `valueOf()` أو `[Symbol.toPrimitive]` مخصصة في `object` حقيقي (مش تمرين)؟ ومتى تتجنبي ده؟

**5. Debug** — لاقيتي `object` بتاع فلوس في الكود بيدّي نتائج غريبة لما بيتجمع مع رقم. إيه أول حاجة تفحصيها؟

> قاعدة: لو بند واحد من الخمسة ما اتحقّقش، الموضوع لسه ما اتقنش.

---

**الدرس الجاي في نفس الفصل:** 🟢 `typeof` / `instanceof` / `Object.prototype.toString` — إزاي نكتشف نوع أي قيمة بدقة، وليه `typeof` لوحدها مش كفاية دايماً.