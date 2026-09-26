# 🟢 Chapter 1 — Lesson 1: Primitive vs Object Values
### Pass by Value / Pass by Sharing

هذا المفهوم بسيط ظاهريًا، لكن عليه بُني فهمنا لاحقًا لـ:

- Mutation
- Copying
- Function arguments
- React state (`useState`, Redux, Zustand)
- `spread` / `structuredClone`
- Immutability
- Bugs الناتجة عن shared references

---

## 1. Why it exists — ما المشكلة؟

الكمبيوتر محتاج طريقة يحفظ بيها البيانات ويرجع لها. لو كل البيانات في البرنامج حجمها ثابت (زي رقم أو حرف)، الموضوع سهل. لكن التطبيقات الحقيقية فيها بيانات حجمها متغير ومركّب (زي قائمة مستخدمين، أو state لجدول ERP فيه آلاف الصفوف).

لو كل ما نمرر object لدالة كان بيتنسخ بالكامل في مكان جديد، الأداء هيبقى سيء جداً مع البيانات الكبيرة. عشان كده JavaScript بتفرّق بين نوعين من القيم:

```js
const age = 25;
const user = {
  name: "Hanan",
  age: 25
};
```

```
25
↓
Primitive Value

{ name: "Hanan", age: 25 }
↓
Object Value
```

السؤال اللي بيبدأ منه الفهم الحقيقي:

> ماذا يحدث عندما أنقل هذه القيمة إلى متغير آخر، أو أمررها إلى function؟

```js
let a = 10;
let b = a;
b = 20;
console.log(a); // 10
```

`a` فضلت `10`. لكن:

```js
const user1 = { name: "Hanan" };
const user2 = user1;
user2.name = "Ahmed";
console.log(user1.name); // "Ahmed"
```

هنا `user1.name` اتغيرت لـ `"Ahmed"` رغم إننا عدّلنا على `user2`. **ليه؟** هنا يبدأ الـ senior thinking.

---

## 2. Concept — Primitive Values

```
Primitive
├── string
├── number
├── bigint
├── boolean
├── undefined
├── symbol
└── null
```

```js
typeof "Hanan";   // "string"
typeof 25;        // "number"
typeof true;      // "boolean"
typeof undefined; // "undefined"
typeof 123n;      // "bigint"
typeof Symbol();  // "symbol"
typeof null;      // "object"  ← quirk تاريخي في اللغة، مش دليل إن null Object فعلاً
```

## 3. Concept — Object Values

```js
const user = { name: "Hanan" };
const numbers = [1, 2, 3];
const fn = function () {};
const date = new Date();
```

`Array`, `Function`, `Date`, `Map`, `Set`, `RegExp` كلها Object values من منظور الـ object model في JavaScript.

---

## 4. Mental Model 🧠

فكرة شائعة جداً لازم نتخلص منها:

> ❌ "Primitive = Stack" / ❌ "Object = Heap"

دي **تفاصيل تنفيذ (implementation detail)** ممكن تختلف من محرك (engine) لتاني، وليست قاعدة في مواصفة اللغة (spec) نفسها. الاعتماد عليها كإجابة أساسية بيدّي إحساس فهم زائف. الفهم الصحيح هو:

```
Variables
   ↓
hold / refer to
   ↓
Values
```

مع Object:

```
user ──────────────┐
                    ↓
                 Object
                    ↑
                    │
another variable ───┘
```

متغيران ممكن يشيروا لنفس الـ Object value.

**تشبيه:**
- الـ **Primitive** زي ورقة مكتوب فيها رقم تليفون: لو اديتي صاحبتك نسخة منها وهي غيّرت رقمها، ورقتك ما بتتأثرش.
- الـ **Object** زي مفتاح شقة: لو اديتيها نسخة من المفتاح، والشقة هي الـ Object في الذاكرة، لو غيّرت حاجة جوه الشقة (mutation) هتلاقيها لما ترجعي بمفتاحك. لكن لو اشترت شقة جديدة بمفتاح جديد (reassignment)، شقتك الأصلية ما بيحصلهاش حاجة.

---

## 5. How JavaScript actually behaves

JavaScript **دايماً Pass by Value**. لكن مع الـ objects، القيمة اللي بتتنسخ وتتمرر هي **قيمة المرجع (reference)** نفسها، مش الـ object كامل. المصطلح الأدق لده:

> **Pass by sharing**

- Primitive → القيمة الحقيقية بتتنسخ.
- Object → قيمة الـ reference بتتنسخ، والاتنين (الأصلي والنسخة) بيشاوروا على نفس الـ object.

---

## 6. Code Examples (Predict first ✍️)

### مثال أ — Primitive

```js
let count = 10;

function increment(num) {
  num = num + 1;
  console.log("Inside:", num);
}

increment(count);
console.log("Outside:", count);
```
توقعي قبل ما تشغلي: إيه الناتج؟

**الناتج:** `Inside: 11` ثم `Outside: 10`. `num` نسخة منفصلة تماماً عن `count`.

### مثال ب — Object Mutation

```js
const user = { name: "Hanan", role: "Developer" };

function updateRole(person) {
  person.role = "Senior UX/UI Engineer";
}

updateRole(user);
console.log(user.role);
```
**الناتج:** `"Senior UX/UI Engineer"`. `person` و`user` بيشاوروا على نفس الـ object، فالتعديل الداخلي بيسمع في الأصل.

### مثال ج — Object Reassignment (التريكة الصعبة)

```js
let config = { theme: "light" };

function resetConfig(cfg) {
  cfg = { theme: "dark" };
}

resetConfig(config);
console.log(config.theme);
```
**الناتج:** `"light"`. جوه الدالة، `cfg = {...}` غيّرت المتغير المحلي بس ليشاور على object جديد تماماً، والـ `config` الخارجي فضل يشاور على القديم.

### مثال د — نفس الفكرة بدون function

```js
let user1 = { name: "Hanan" };
let user2 = user1;
user2 = { name: "Ahmed" };

console.log(user1.name); // "Hanan"
console.log(user2.name); // "Ahmed"
```

قبل `user2 = {...}` كان الاثنان يشيران لنفس الـ Object A. بعدها:
```
user1 ──→ Object A { name: "Hanan" }
user2 ──→ Object B { name: "Ahmed" }
```

---

## 7. Mutation vs Reassignment (أهم فكرة في الدرس)

```
Mutation
→ نغيّر حاجة داخل الـ Object نفسه
→ user.name = "Ahmed"

Reassignment
→ نغيّر الـ reference اللي المتغير ماسكها
→ user = { name: "Ahmed" }
```

هذا الفرق هيظهر تاني في: React state، Redux، Zustand، memoization، shallow comparison، وأي مكان فيه immutability.

---

## 8. Common Mistakes / Misconceptions

**❌ "JavaScript objects are passed by reference"**
غير دقيقة. الأدق: الـ function arguments بتتمرر by value، والقيمة بالنسبة للـ objects هي reference لنفس الـ object — **pass by sharing**.

**❌ "`const` تمنع تعديل الـ object"**
```js
const user = { name: "Hanan" };
user.name = "Ahmed"; // ✅ شغال
user = {};           // ❌ TypeError
```
`const` بتمنع reassignment للمتغير، مش mutation للمحتوى.

**❌ "`spread` بيعمل نسخة كاملة (deep copy)"**
```js
const user = { name: "Hanan", address: { city: "Fayoum" } };
const copy = { ...user };
copy.address.city = "Cairo";
console.log(user.address.city); // "Cairo"
```
الـ `spread` بيعمل **shallow copy** بس — المستوى الأول ينفصل، لكن أي object متداخل جواه لسه reference مشترك. (ملاحظة: `structuredClone` بيعمل deep copy، لكنه ما بيقدرش ينسخ functions.)

---

## 9. Real Front-End Example — ERP / React

```js
const company = {
  name: "Company A",
  settings: { currency: "EGP", language: "ar" }
};

const draft = { ...company };
draft.settings.currency = "USD";

console.log(company.settings.currency); // "USD" ⚠️
```

الـ top-level انفصل (`company` و`draft` objects مختلفة)، لكن `settings` لسه reference مشترك. ده نوع الأخطاء الخطير جداً في: ERP forms، nested state، filters، dashboard configuration، permissions، large data tables.

**مثال React مباشر:**

```jsx
// ❌ خطأ شائع بيكسر الـ re-render
const [user, setUser] = useState({ name: "Hanan", preferences: { theme: "dark" } });

const toggleTheme = () => {
  user.preferences.theme = "light"; // mutation مباشر
  setUser(user); // نفس الـ reference! React مش هتعمل re-render
};
```

```jsx
// ✅ الطريقة الصحيحة
setUser(prevUser => ({
  ...prevUser,
  preferences: { ...prevUser.preferences, theme: "light" }
}));
```

React بتقارن الـ objects بالـ reference (زي `Object.is`)، فلو الـ reference ما اتغيرش، React هتفتكر إن مفيش حاجة اتغيرت.

---

## 10. Interview Question 🎯

> **Is JavaScript pass-by-reference or pass-by-value?**

إجابة ضعيفة وشائعة: *"pass-by-value for primitives and pass-by-reference for objects"* ❌

الإجابة الأدق:

> JavaScript is pass-by-value. For objects, the value being passed is a reference to the same object, so both the caller and the function parameter can mutate that shared object. This is often described as pass-by-sharing.

---

## 🧠 Senior Thinking

لما تشوفي:
```js
const a = something;
const b = a;
```

**متسأليش فوراً:** "هل اتعملت نسخة؟"
**اسألي:** "نوع القيمة اللي اتنسخت إيه، primitive ولا reference؟" وبعدها: "أنا بعمل mutation ولا reassignment؟"

السؤالين دول وحدهم بيحلوا نسبة كبيرة من الـ bugs المرتبطة بالـ state والـ data.

---

## 🛠 Practice — Build It

اكتبي function اسمها `updateUserName(user, newName)` بحيث:

```js
const user = { name: "Hanan", age: 25 };
const updatedUser = updateUserName(user, "Ahmed");

// المطلوب:
// user.name === "Hanan"      (لم يتغير)
// updatedUser.name === "Ahmed"
```

يعني من غير mutation للـ object الأصلي. حاولي تنفذيها الأول.

## 💥 Practice — Break It

```js
const state = { user: { name: "Hanan" } };
const nextState = { ...state };
nextState.user.name = "Ahmed";
console.log(state.user.name);
```

**Predict first ✍️** قبل ما تشغلي الكود، جاوبي:
1. هيطبع إيه؟ وليه؟
2. هل `state === nextState`؟
3. هل `state.user === nextState.user`؟
4. إيه اللي لازم يتغيّر عشان نحدّث `name` من غير mutation؟

---

## 🔄 Recap

```
Primitive → Value itself
Object    → Reference to an object

JavaScript → Pass-by-value
           → Object reference is the value being copied
           → "Pass-by-sharing"

Mutation      ≠ Reassignment
const         ≠ Immutable Object
spread        → shallow copy فقط
```

---

## ✅ Self-Check

**1. Define** — عرّفي الفرق بين Primitive Value وObject Value بكلامك، من غير ما ترجعي للشرح.

**2. Predict** — جاوبي على 3 أكواد جديدة (اكتبيها بنفسك أو اطلبيها مني) فيها مزيج من mutation وreassignment، واكتبي توقعك قبل التشغيل.

**3. Why** — اكتبي فقرة قصيرة: "الفرق بين Primitive وObject موجود عشان..." بدون استخدام "Stack/Heap" كإجابة أساسية.

**4. Apply** — إمتى تفضّلي تعملي mutation، وإمتى تفضّلي reassignment / copy؟ (مثال عام: تحديث عنصر في قائمة طويلة معروضة في جدول).

**5. Debug** — لو ظهرلك bug إن الـ UI مش بيعمل re-render رغم إنك "غيّرتي" الـ state، هل تعرفي أول 3 حاجات تفحصيها؟ لو الإجابة لأ، ارجعي لقسم "Common Mistakes" و"Front-End Example" فوق.

> قاعدة: لو بند واحد من الخمسة ما اتحقّقش، الموضوع لسه ما اتقنش.

---

**الدرس الجاي في نفس الفصل:** 🟢 Dynamic Typing — ولماذا JavaScript تسمح للمتغير نفسه أن يحمل أنواعًا مختلفة، وعلاقة ذلك بالـ runtime وType Coercion.