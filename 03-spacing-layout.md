# Spacing ба Layout

## Spacing scale — 4px/8px систем

Зайг дур мэдэн биш тогтмол шатлалаас сонгоно:

```
4 · 8 · 12 · 16 · 24 · 32 · 48 · 64 · 96 · 128
```

- Жижиг зай (component дотор): 4/8/12/16
- Дунд зай (component хооронд): 24/32
- Том зай (section хооронд): 48/64/96+
- Tailwind-ийн spacing scale (`p-1`=4px, `p-2`=8px…) яг энэ систем.

**Зарчим**: холбоотой зүйлс ойр, холбоогүй нь хол (proximity). Гарчиг нь дараагийн контентдоо өмнөх section-ээсээ илүү ойр байх ёстой — `margin-top > margin-bottom`.

## Container ба хуудасны өргөн

| Хэрэглээ | Max-width |
|---|---|
| Урт текст (blog, docs) | 65-75ch (~720px) |
| Ерөнхий контент сайт | 1140-1280px |
| Dashboard/ERP | 1440-1536px, эсвэл full-width + padding |
| Форм | 400-560px |

Хажуугийн padding: mobile 16px, tablet 24px, desktop 32px+.

## Breakpoints

Түгээмэл жишиг (Tailwind):

```
sm: 640px · md: 768px · lg: 1024px · xl: 1280px · 2xl: 1536px
```

- **Mobile-first**: суурь стилиэ жижиг дэлгэцэд бичээд `min-width` query-гээр өргөжүүл.
- Breakpoint-ыг төхөөрөмжөөр биш **контентоор** сонго — layout эвдэрч эхэлсэн цэг дээр л breakpoint тавь.
- 3-4 breakpoint ихэнх сайтад хүрэлцдэг; бүх breakpoint бүрд бүх зүйлийг өөрчлөх шаардлагагүй.

## Grid

- **12 багана** — сонгодог, уян хатан (2/3/4/6 хуваагдана).
- CSS Grid + `gap` — margin-аар зай барихаас илүү цэвэр.
- Card grid-д: `grid-template-columns: repeat(auto-fill, minmax(280px, 1fr))` — breakpoint бичилгүйгээр өөрөө responsive болно.
- Gutter: mobile 16px, desktop 24-32px.

## Responsive зарчмууд

- Хэвтээ scroll хэзээ ч үүсгэхгүй — өргөн контент (table, code) өөрийн `overflow-x: auto` саванд.
- Зураг: `max-width: 100%; height: auto` + `aspect-ratio`-оор layout shift-ээс сэргийл.
- Sidebar → mobile-д drawer/bottom nav болдог; table → card эсвэл хэвтээ scroll.
- Touch target: 44×44px-ээс доошгүй (линк, товч, icon).
- Hover-т тулгуурласан UI mobile-д ажиллахгүй — чухал үйлдлийг hover-ийн цаана бүү нуу.

## Мэдэх ёстой нюансууд

- **8px grid-ээс гарах нь алдаа биш** — optical alignment (нүдэнд зөв харагдах) нь математик alignment-аас чухал. Icon текстийн хажууд байрлахдаа 1-2px шилжих нь хэвийн.
- Vertical rhythm: line-height + margin нийлээд тогтмол хэмнэл үүсгэвэл хуудас «амьсгалтай» харагдана.
- Whitespace бол feature — багтаах гэж шахахаар хуудас хямд харагддаг. Эргэлзвэл зайг нэм.
