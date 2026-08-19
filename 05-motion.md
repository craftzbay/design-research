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
