
JavaScript Senior Front-End Handbook
│
│  Legend:  🟢 Core (يومي)   🟠 Advanced   🔴 Deep Dive   🛠 Build it yourself
│
│  Rules:
│   1. Language semantics > Engine trivia
│   2. مش كل الموضوعات بنفس الوزن (Core → Advanced → Deep Dive)
│   3. كل موضوع يترتبط بمشروع حقيقي (React / Next.js / ERP / SaaS / RTL / Auth / Dashboards / Large Tables)
│   4. كل فصل ينتهي بـ 🧠 Senior Thinking
│
├── 1. Core JavaScript & Values
│   ├── 🟢 Primitive vs Object Values (pass by value / pass by sharing)
│   ├── 🟢 Dynamic Typing
│   ├── 🟢 Type Coercion
│   ├── 🟢 ToPrimitive / ToBoolean / ToNumber / ToString (Abstract Operations)
│   ├── 🟢 == vs === (Abstract Equality Algorithm)
│   ├── 🟢 typeof / instanceof / Object.prototype.toString
│   ├── 🟢 Operators: Logical, Nullish Coalescing, Optional Chaining
│   ├── 🟢 Shallow vs Deep Copy / structuredClone
│   ├── 🟢 Strict Mode
│   ├── 🟠 Wrapper Objects (Boxing)
│   ├── 🟠 Numbers: Floating Point (0.1 + 0.2), NaN, -0, BigInt
│   ├── 🟠 Object.is / SameValue vs SameValueZero
│   ├── 🟠 Strings & Unicode (UTF-16, code points: Arabic, Emoji, length, slicing)
│   ├── 🟢 Built-ins: Date, Intl, JSON
│   ├── Regular Expressions
│   │   ├── 🟢 Pattern Syntax: Character Classes, Quantifiers
│   │   ├── 🟢 Groups: Capturing / Non-capturing / Named / Backreferences
│   │   ├── 🟢 Flags
│   │   ├── 🟠 Lookahead / Lookbehind
│   │   ├── 🟠 Unicode Regex (u / v flags)
│   │   └── 🟠 Regex Performance & Backtracking (أساس فهم ReDoS)
│   └── 🧠 Senior Thinking
│       ├── ليه تمرير object لدالة ممكن يغيّر الأصلي، ومتى إعادة التعيين لا تغيّره؟
│       ├── ليه string.length بيغلط مع Emoji والعربي في مدخلات المستخدم؟
│       └── متى structuredClone كافي ومتى لا (functions, class instances)؟
│
├── 2. Variables, Scope & Execution
│   ├── 🟢 var / let / const
│   ├── 🟢 Block / Function / Global Scope / globalThis
│   ├── 🟢 Lexical Scope & Scope Chain
│   ├── 🟢 Hoisting (function declarations / var / let-const / function expressions / class declarations)
│   ├── 🟢 TDZ
│   ├── 🟢 IIFE
│   ├── 🟢 Closures (practical uses, closures in loops)
│   ├── 🟠 Execution Context (Creation vs Execution)
│   └── 🧠 Senior Thinking
│       ├── فين الـ closures بتظهر فعلياً في React (stale closures في الـ hooks)؟
│       └── إزاي closure ممكن يسبب memory leak؟
│
├── 3. Functions & this
│   ├── 🟢 First-Class & Higher-Order Functions
│   ├── 🟢 Function Declarations vs Expressions vs Arrow Functions
│   ├── 🟢 Parameters: default, rest, arguments object
│   ├── 🟢 this: Default / Implicit / Explicit / new / Lexical
│   ├── 🟢 call / apply / bind          🛠 bind polyfill
│   ├── 🟢 new operator                 🛠 custom new
│   ├── 🟠 new.target
│   ├── 🟢 Currying & Partial Application   🛠 curry
│   ├── 🟢 Composition & pipe           🛠 compose / pipe
│   ├── 🟢 Recursion
│   ├── 🔴 TCO (ملاحظة فقط: دعم محدود في الـ engines)
│   └── 🧠 Senior Thinking
│       ├── ليه this بيضيع في الـ event handlers والـ callbacks، وإزاي نحله؟
│       └── متى Arrow Function غلط استخدامها؟
│
├── 4. Objects & Prototypes
│   ├── 🟢 Property Descriptors
│   ├── 🟢 Getters / Setters
│   ├── 🟢 Enumeration: for...in vs Object.keys/entries, Property Order
│   ├── 🟢 Prototype Chain
│   ├── 🟢 prototype vs __proto__ / Object.create (شرح دقيق: prototype ≠ parent object)
│   ├── 🟢 Constructor Functions → Classes
│   ├── 🟢 super & Inheritance
│   ├── 🟢 Private Fields
│   ├── 🟢 Object Immutability (freeze / seal / preventExtensions)
│   ├── 🟠 Static Members & Static Blocks
│   ├── 🟠 Composition vs Inheritance / Mixins
│   ├── 🟠 instanceof mechanics         🛠 custom instanceof
│   └── 🧠 Senior Thinking
│       ├── متى Composition أفضل من Inheritance في مشروع حقيقي؟
│       └── إزاي أحمي الـ state من التعديل غير المقصود؟
│
├── 5. Arrays, Collections & Iteration
│   ├── 🟢 Array Mechanics (holes, length, sort stability)
│   ├── 🟢 Mutating vs Non-mutating Methods
│   ├── 🟢 map / filter / reduce / flat …   🛠 Array polyfills
│   ├── 🟢 Destructuring / Rest / Spread
│   ├── 🟢 Map / Set
│   ├── 🟢 Iteration Protocols (Iterable / Iterator)
│   ├── 🟠 WeakMap / WeakSet
│   ├── 🟠 Generators
│   ├── 🟠 Async Iterators / for await
│   ├── 🟠 Typed Arrays / ArrayBuffer
│   ├── 🔴 WeakRef / FinalizationRegistry
│   ├── 🔴 SharedArrayBuffer / Atomics
│   ├── 🔴 Iterator Helpers
│   └── 🧠 Senior Thinking
│       ├── Object أم Map أم Array في جداول كبيرة (Large Tables)؟
│       └── إزاي أتجنب الـ mutations اللي بتكسر الـ rendering في React؟
│
├── 6. Error Handling
│   ├── 🟢 try / catch / finally
│   ├── 🟢 Error Types & Stack Traces
│   ├── 🟢 Custom Errors
│   ├── 🟢 Error Propagation (sync vs async)
│   ├── 🟢 Unhandled Rejections / Global Error Handlers
│   ├── 🟠 Defensive Programming
│   └── 🧠 Senior Thinking
│       ├── إزاي أصمم error handling لطبقة الـ API في الـ SaaS؟
│       └── إيه اللي المستخدم يشوفه، وإيه اللي يتسجّل للـ debugging؟
│
├── 7. Metaprogramming
│   ├── 🟠 Symbols (registry, use cases)
│   ├── 🟠 Well-Known Symbols (iterator, toPrimitive, hasInstance, toStringTag …)
│   ├── 🟠 Proxy
│   ├── 🟠 Reflect
│   └── 🧠 Senior Thinking
│       └── متى Proxy حل مناسب (validation, reactivity) ومتى تعقيد زيادة؟
│
├── 8. Asynchronous JavaScript
│   ├── 🟢 Callbacks & Inversion of Control
│   ├── 🟢 Call Stack & Runtime APIs
│   ├── 🟢 Event Loop (Tasks, Microtasks, queueMicrotask)
│   ├── 🟢 Timers (setTimeout clamping, drift)
│   ├── 🟢 Promise States & Resolution   🛠 Promise polyfill
│   ├── 🟢 async / await
│   ├── 🟢 Promise.all / allSettled / race / any
│   ├── 🟢 AbortController / Cancellation
│   ├── 🟢 Concurrency Patterns (limit, retry, sequential vs parallel)   🛠 Promise pool
│   ├── 🟢 Race Conditions
│   ├── 🟠 Thenables
│   ├── 🟠 requestAnimationFrame / requestIdleCallback
│   ├── 🟠 Promise.withResolvers
│   ├── 🔴 Node.js Event Loop (nextTick, setImmediate, phases)
│   └── 🧠 Senior Thinking
│       ├── متى Promise.all ومتى لا؟ وإيه اللي يحصل لو request واحد فشل؟
│       ├── لو عندي 500 request، إزاي أعمل concurrency limit؟
│       ├── إزاي ألغي العملية؟
│       └── إزاي أتعامل مع race condition في search / autocomplete؟
│
├── 9. Browser Runtime
│   ├── 🟢 DOM
│   ├── 🟢 Event Architecture (capturing / bubbling)
│   ├── 🟢 Event Delegation
│   ├── 🟢 Rendering Pipeline (Critical Rendering Path, reflow / repaint)
│   ├── 🟢 Fetch API
│   ├── 🟢 Storage: Web Storage / Cookies / IndexedDB
│   ├── 🟠 Streams
│   ├── 🟠 Observers (Intersection / Mutation / Resize)
│   ├── 🟠 WebSockets / SSE
│   ├── 🟠 Web Workers
│   ├── 🟠 History API
│   ├── 🔴 Service Workers
│   ├── 🔴 Web Components / Shadow DOM
│   └── 🧠 Senior Thinking
│       ├── إزاي أنفّذ infinite scroll و lazy loading بكفاءة؟
│       └── أنهي مخزن أستخدم لأنهي بيانات ولماذا؟
│
├── 10. Modules & Tooling
│   ├── 🟢 ESM vs CommonJS
│   ├── 🟢 Module Resolution & Circular Dependencies
│   ├── 🟢 Dynamic Import & Code Splitting
│   ├── 🟢 Package Managers, semver, package.json (exports)
│   ├── 🟢 Bundlers & Tree Shaking
│   ├── 🟢 Linting / Formatting
│   ├── 🟠 Transpilation & Polyfilling (Babel / SWC)
│   ├── 🟠 Source Maps
│   ├── 📌 ملاحظة: TypeScript مرحلة كاملة لاحقة (نذكر العلاقة JS → TS فقط)
│   └── 🧠 Senior Thinking
│       └── إزاي أقلل حجم الـ bundle في تطبيق Next.js كبير؟
│
├── 11. Memory, Performance & Security
│   ├── Performance
│   │   ├── 🟢 Debouncing / Throttling   🛠 both
│   │   ├── 🟢 Memoization               🛠 memoize
│   │   ├── 🟢 Core Web Vitals / Long Tasks
│   │   ├── 🟢 Lazy Loading / Virtualization
│   │   ├── 🟢 Profiling
│   │   ├── 🟢 Memory Leaks (common patterns)
│   │   └── 🟠 Garbage Collection Basics
│   ├── Security
│   │   ├── 🟢 XSS / Sanitization / CSP
│   │   ├── 🟢 CSRF
│   │   ├── 🟢 CORS / SameSite Cookies
│   │   ├── 🟢 Auth Concepts: Authentication vs Authorization
│   │   ├── 🟢 Tokens: Format / Transport / Storage (JWT) — وعلاقتها بـ Cookie Security و XSS و CSRF
│   │   ├── 🟠 Trusted Types
│   │   ├── 🟠 Prototype Pollution
│   │   ├── 🟠 ReDoS (بعد أساسيات Regex)
│   │   └── 🟠 Supply Chain Security
│   └── 🧠 Senior Thinking
│       ├── ليه "localStorage مش آمن / cookies آمنة" اختزال مخل؟ وإيه التفاصيل الحقيقية؟
│       └── إزاي أخلي جدول بآلاف الصفوف يفضل سريع؟
│
├── 12. Testing & Debugging
│   ├── 🟢 Unit / Integration / E2E
│   ├── 🟢 Mocking & Testable Design
│   ├── 🟢 Testing Async Code (Promises, Timers, fetch, AbortController, Race Conditions)
│   ├── 🟢 DevTools Debugging (breakpoints, async stack, performance panel)
│   └── 🧠 Senior Thinking
│       └── إيه اللي يستاهل يتختبر وإيه اللي لأ؟
│
├── 13. Design Patterns & Architecture
│   ├── 🟢 Factory / Module / Observer / Pub-Sub / Strategy
│   ├── 🟠 Singleton / Builder / Decorator / Proxy
│   ├── 🟠 Command / State / Mediator / Iterator
│   ├── 🟢 Functional Programming (pure functions, immutability)
│   ├── 🟠 Dependency Injection
│   ├── 🟠 Event-Driven Architecture
│   ├── 🟢 SOLID / Clean Code
│   └── 🧠 Senior Thinking
│       ├── إيه المشكلة اللي بحاول أحلها؟ وهل محتاج Pattern أصلاً؟
│       └── (نبدأ من المشكلة، مش من الـ Pattern)
│
├── 14. Engine Internals   🔴 Deep Dive
│   ├── V8 Architecture
│   ├── Parsing & AST
│   ├── Ignition / TurboFan (Interpreter / JIT)
│   ├── Deoptimization
│   ├── Hidden Classes (Shapes)
│   ├── Inline Caches & Polymorphism / Megamorphic
│   ├── GC Internals (generational)
│   ├── 📌 الهدف: نفهم ليه أنماط معينة تأثر على الـ optimization، مش نحفظ تفاصيل كل إصدار
│   └── 🧠 Senior Thinking
│       └── إيه أنماط الكود اللي تكسر الـ optimization في الواقع؟
│
├── 15. Senior Interview Scenarios
│   ├── 🛠 debounce / throttle
│   ├── 🛠 deep clone
│   ├── 🛠 EventEmitter
│   ├── 🛠 Promise pool
│   ├── 🛠 LRU cache
│   └── 🛠 flatten / curry / compose
│
└── 16. Staying Senior
    ├── 🟠 Reading the ECMAScript Spec
    ├── 🟠 Following TC39 Proposals
    ├── 🟠 Modern Features — تصنيفها حسب الـ Status وقت الدراسة (Standardized / Stage 3 / Stage 2 …)
    │        (Temporal, Decorators, Records/Tuples — نراجع حالتها الحالية وقتها)
    └── 🧠 Senior Thinking
        └── إزاي أتحقق من معنى feature بنفسي بدل ما أعتمد على الحفظ؟