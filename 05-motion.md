# Motion / Animation

## Duration — богино байх тусмаа мэргэжлийн

| Хэрэглээ | Хугацаа |
|---|---|
| Hover, color/opacity шилжилт | 100-150ms |
| Dropdown, tooltip, жижиг элемент | 150-200ms |
| Modal, drawer, panel | 200-300ms |
| Хуудасны шилжилт, том элемент | 300-400ms |

- 400ms-ээс урт UI animation бараг хэзээ ч хэрэггүй — хэрэглэгчийг хүлээлгэдэг.
- Орох нь гарахаасаа удаан: enter 250ms бол exit 150-200ms.

## Easing

- **ease-out** (`cubic-bezier(0, 0, 0.2, 1)`) — UI-ийн default: хурдан эхэлж зөөлөн зогсоно. Орж ирэх элементэд.
- **ease-in** — гарч буй элементэд (эхэндээ удаан, түргэсч алга болно).
- **ease-in-out** — байрлалаа солиж буй элементэд.
- `linear` зөвхөн opacity/spinner-т.
- Spring physics (Framer Motion гэх мэт) — drag, gesture-т байгалиас; энгийн UI-д заавал биш.

## Юуг хөдөлгөх вэ — performance

- Зөвхөн **transform ба opacity** — GPU-гоор явдаг, reflow үүсгэдэггүй.
- `width/height/top/left/margin`-ыг бүү animate хий — layout thrashing. Хэмжээний animation хэрэгтэй бол `transform: scale()` эсвэл FLIP техник.
- `will-change`-ийг зөвхөн шаардлагатай үед, animation дуусмагц авах.

## Хаана хөдөлгөөн хэрэгтэй вэ

- **Feedback**: товч дарагдсан (scale 0.97 гэх мэт), form алдаа (сэгсрэх биш — өнгө+текст хангалттай).
- **Орон зайн ойлголт**: drawer хаанаас гарч ирснээ харуулах, modal төвөөс scale+fade.
- **Continuity**: list-ээс detail руу шилжихэд элемент «үргэлжлэх» (shared element transition, View Transitions API).
- **Skeleton/loading**: pulse эсвэл shimmer — spinner-ээс илүү тайван.

Хаана хэрэггүй: scroll-д автоматаар олон юм үсэрч орж ирэх, autoplay carousel, хуудас болгонд орох animation. Хөдөлгөөн нь мэдээлэл дамжуулахгүй бол чимээ.

## prefers-reduced-motion

Заавал хүндэтгэх — vestibular эмгэгтэй хүнд том хөдөлгөөн бодит өвчин үүсгэдэг:

```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    transition-duration: 0.01ms !important;
  }
}
```

Эсвэл нарийн хандвал: том шилжилтүүдийг fade-ээр орлуулж, жижиг feedback-ийг үлдээж болно.

## Практик дүрэм

Эргэлзвэл: **150-250ms, ease-out, transform+opacity, нэг зүйл л хөдөлнө**. Хоёр ба түүнээс олон зүйл зэрэг анимэйшнтэй бол ихэнхдээ нэгийг нь хасах хэрэгтэй.

## Нэмэлт техникүүд

- **`display:none` → харагдах шилжилт** (popover, `<dialog>`, dropdown) одоо JS-гүй:

```css
[popover] {
  opacity: 0; transform: translateY(-4px);
  transition: opacity 150ms, transform 150ms, display 150ms allow-discrete, overlay 150ms allow-discrete;
}
[popover]:popover-open { opacity: 1; transform: none; }
@starting-style { [popover]:popover-open { opacity: 0; transform: translateY(-4px); } }
```

`@starting-style` = орох үеийн эхлэх утга; `transition-behavior: allow-discrete` (товчлолоор `display ... allow-discrete`) = гарахдаа transition дуустал `display`-г хойшлуулна. `overlay`-г `<dialog>`/popover-д давхар бич.

- **Stagger**: list элемент дараалан орж ирэх бол **≤5 элемент**, алхам **30-50ms**, нийт **≤300ms**. 6 дахиас хойш delay өгөхгүй (бүгд зэрэг). `animation-delay: calc(var(--i) * 40ms)`.
- **Scroll-driven animation** (`animation-timeline: view()`, `scroll()`) — progress bar, reveal-on-scroll-д JS observer-гүй. Хуудсанд 1-2 газар; reveal-ийг `prefers-reduced-motion`-д заавал унтраа. Хэрэглээний цар хүрээ: opacity/transform л, duration-гүй (scroll-оор удирдагдана).
- **View Transitions API**: `document.startViewTransition(() => updateDOM())` — DOM солигдохын өмнө/дараах snapshot-ыг crossfade хийнэ; ижил `view-transition-name: card-12` өгсөн элемент хоёр төлөвийн хооронд «нисдэг» (shared element). Нэр хуудсанд давхардахгүй байх ёстой. Default 250ms crossfade; `::view-transition-old(root)`/`::view-transition-new(root)`-ээр удирдана. Multi-page-д `@view-transition { navigation: auto; }`. Дэмжээгүй browser-т функц байхгүй бол шууд `updateDOM()` дууд.

## Эх сурвалж

- WCAG 2.2 — SC 2.3.3 Animation from Interactions (AAA), 2.2.2 Pause, Stop, Hide, 2.3.1 Three Flashes — w3.org/TR/WCAG22/
- MDN — `prefers-reduced-motion`, `@starting-style`, `transition-behavior`, Scroll-driven animations, View Transition API — developer.mozilla.org
- web.dev — «Animations and performance»; «Four new CSS features for smooth entry and exit animations»; «Smooth transitions with the View Transition API»
- Material 3 — Motion: Easing and duration tokens — m3.material.io/styles/motion
- Apple HIG — Motion
- Nielsen Norman Group — «Animation Duration and Motion Characteristics in User Interface Design»; «The Role of Animation and Motion in UX»
- Emil Kowalski — «Animations on the web» (course notes; 150-300ms, ease-out)
