# Dashboard / SaaS / ERP / admin UI-ийн бүтцийн хэв маяг

## Яагаад

Админ, ERP, SaaS апп-ыг хэрэглэгч өдөр бүр олон цагаар хэрэглэнэ. Landing page шиг «сэтгэгдэл төрүүлэх» биш, **урьдчилан таамаглаж болох, хурдан, алдаанаас хамгаалсан** байх нь гол. Доорх хэв маягууд нь Linear, Stripe Dashboard, GitHub, Notion, Atlassian, Material 3, Carbon зэрэг системүүдэд давтагддаг нийтлэг шийдлүүд. Товч/форм/table-ийн суурь, modal, toast-ыг 06-components.md хариуцна — энд зөвхөн **бүтэц** ба **урсгал**.

## App shell

| Хэсэг | Хэмжээ | Тайлбар |
|---|---|---|
| Sidebar (дэлгэсэн) | 240–280px | 256px хамгийн түгээмэл; label + icon |
| Sidebar (хумьсан) | 56–64px | зөвхөн icon, hover-т tooltip (label-гүй icon хориотой) |
| Top bar | 48–64px | breadcrumb/хайлт/tenant/профайл; sticky |
| Content padding | 24–32px (desktop) / 16px (mobile) | 03-spacing-layout.md-г үз |
| Content max-width | 1280–1440px (форм, текст) · fluid (table, chart) | хуудасны төрлөөр сонго, хольж болно |

- **Sidebar ≤1024px-д drawer болно** (overlay + focus trap + Esc); 1024–1280px-д хумьсан горимоор эхлүүл.
- Хумьсан/дэлгэсэн төлөвийг хадгал (`localStorage`); доод хэсэг (settings/profile) `position: sticky; bottom: 0`; sidebar өнгө content-оос нэг шатлалаар ялгаатай (01-color.md).

## Navigation

- **Дээд түвшний цэс ≤7**; хэтэрвэл бүлэглэ (group label 11–12px uppercase muted, бүлэг хооронд 16–24px).
- Active төлөв = **accent bar (зүүн талд 2–3px) + font-weight 500–600 + background** — зөвхөн өнгөөр тэмдэглэхгүй (07-accessibility.md, WCAG 1.4.1).
- Гүн ≥3 (Захиалга → #1042 → Засах) бол **breadcrumbs** заавал; 2 түвшинд «← Буцах» хангалттай. Сүүлийн элемент линк биш, `aria-current="page"`. Хуудас доторх tab `h1`-ийн доор, URL-тай.
- Хуудас бүр: **`h1` = хуудасны нэр (зүүн), primary action = баруун дээд**, нэг мөрөнд. Primary товч нэг л байна.

## Хуудасны загварууд

### Overview (нүүр)

- Дараалал: **KPI мөр → chart → table**. KPI 3–4 ширхэг (6-аас олонгүй); card бүр: label (12–13px muted) → утга (24–32px, `tabular-nums`) → өөрчлөлт (`▲ 12%`, өнгө + тэмдэг хоёулаа).
- Хугацааны шүүлтүүр (7d/30d/90d) дээд талд нэг газар, бүх widget-д нийтлэг; table 5–10 мөр + «Бүгдийг үзэх».

### List → Detail

| Хэлбэр | Хэзээ |
|---|---|
| **Тусдаа route** (`/orders/1042`) | Detail нь 1 дэлгэцээс урт, засвартай, хуваалцах URL хэрэгтэй — default |
| **Master-detail** (зүүн list 320–400px + баруун panel) | Мөр хооронд хурдан шилжих (мэйл, чат, тикет); ≥1280px-д л, URL-тай, доош route болно |
| **Side sheet / drawer** (480–640px) | Унших + 1–3 талбар засах; list-ийн контекст алдагдахгүй |

- Detail-ээс буцахад list-ийн scroll байрлал, шүүлтүүр хадгалагдсан байна (URL query-д хадгал).

### Settings

- Зүүн талд босоо tab (200–240px), баруун талд хэсгүүд; **хэсэг бүрийн max-width 640–720px** — форм бүтэн өргөнөөр сунахгүй.
- Хадгалах хоёр горим, хольж болохгүй:
  - **Autosave** — toggle, select, ганц талбар; «Хадгалагдлаа» 2 сек (toast биш, inline текст).
  - **Явцуу «Хадгалах»** — олон талбартай форм; товч **sticky footer**-т (56–64px), өөрчлөлт байхгүй үед disabled, «Болих» хажууд.

### Auth хуудсууд

- Нэг багана, card өргөн 400–440px, дэлгэцийн төвд; лого дээр, «Бүртгүүлэх/Нэвтрэх» шилжилт доор.
- Талбар ≤3 (email, нууц үг, [remember]); SSO товчнууд дээр, `— эсвэл —` divider-тэй. Алдаа «Имэйл эсвэл нууц үг буруу» — аль нь гэдгийг хэлэхгүй.

## Density (нягтралын горим)

| Горим | Table мөр | Товч/input | Body font | Хэрэглээ |
|---|---|---|---|---|
| Compact | 32px | 28–32px | 13px | ERP, санхүү, олон мөр |
| Comfortable (default) | 44–48px | 36–40px | 14px | ихэнх SaaS |

- Хэрэглэгчид **toggle өг, сонголтыг хадгал** (user setting, `localStorage` биш account түвшинд).
- Compact горимд ч touch target ≥24×24px (WCAG 2.5.8); mobile-д compact санал болгохгүй.

## Table — гүнзгийрүүлсэн

Суурь (зэрэгцүүлэлт, zebra, header, sticky) 06-components.md-д бий. Энд үйлдлүүд.

- **Sort**: сум зөвхөн идэвхтэй багана дээр харагдана; бусад багананд hover үед муted сум. Header дарахад asc → desc → default гэсэн 3 шат. Сортлогдсон баганыг URL-д хадгал.
- **Filter**: table-ийн дээр chip хэлбэрээр (`Төлөв: Идэвхтэй ×`); «Шүүлтүүр» товч дээр **идэвхтэй тоо badge** (`Шүүлтүүр (3)`); ≥2 шүүлтүүр үед «Бүгдийг цэвэрлэх». Шүүлтүүр URL query-д.
- **Search**: debounce **250–300ms**, ≥2 тэмдэгтээс эхэлнэ, үр дүнгийн тоог харуул («128 үр дүн»), input-д цэвэрлэх `×`. Хайлт хийж байхад spinner input дотор, table-ийг skeleton болгохгүй.
- **Pagination сонголт**:

| Хэлбэр | Хэзээ |
|---|---|
| Offset (1 2 3 … 40) | ≤10k мөр, хэрэглэгч тодорхой хуудас руу үсрэх хэрэгтэй |
| Cursor (Өмнөх / Дараах) | >10k мөр, байнга өөрчлөгддөг өгөгдөл; нийт тоо ойролцоогоор |
| Infinite scroll | **зөвхөн feed/лог**; table-д хэрэглэхгүй (footer хүрэхгүй, байрлал алдагдана) |

- Page size: **25 / 50 / 100**, default 25 (compact-д 50); сонголтыг хадгал. Footer-т «1–25 / 1,284».
- **Selection + bulk bar**: checkbox багана 40–48px; ≥1 сонгоход header-ийн оронд **sticky bulk bar** гарна: «3 сонгосон · [Экспорт] [Архивлах] [Устгах] · Бүгдийг сонгох (1,284)». Destructive bulk үйлдэл заавал confirm. «Бүх хуудсыг сонгох» нь тусдаа, тодорхой линк.
- **Row action**: inline icon ≤2 (засах, үзэх), бусад нь `⋯` overflow menu-д; destructive нь menu-ийн хамгийн доор, divider-ийн дараа, улаан. Мөрийг бүхэлд нь clickable болговол action товчнууд `stopPropagation`.
- **Mobile**: эхний багана (нэр/ID) `position: sticky; left: 0` + баруун талд сүүдэр; ≤3 чухал багана үлдээж, бусдыг detail рүү.
- Truncation: `white-space: nowrap; overflow: hidden; text-overflow: ellipsis` + `title` attribute (эсвэл tooltip); багана `min-width`-тэй, `max-width` 240–320px.
- Тоо, огноо, мөнгө — баруун, `tabular-nums` (02-typography.md); огноо нэг формат (`2026-08-20` эсвэл `20 авг 2026`), relative («3 цагийн өмнө») бол `title`-д абсолют огноо.
- **Status багана = badge: icon + текст**, өнгө ганцаараа биш; төлөвийн нэр ≤2 үг; status-ын өнгөний багц ≤5 (neutral/info/success/warning/danger).

## Detail хуудас

- **Header блок**: breadcrumb → `h1` (нэр/ID) + status badge нэг мөрөнд → meta мөр (үүсгэсэн, эзэмшигч, сүүлд зассан; 13px muted, `·`-ээр тусгаарла) → actions баруун талд (primary 1 + secondary 1–2 + `⋯`). Header `position: sticky; top: 0`.
- Хэсэг ≤3 бол нэг хуудсанд дараалуулж (anchor link-тэй); **>3 бол tab**. Tab-ын нэр 1–2 үг, тоотой байж болно («Төлбөр (4)»).

## Апп доторх форм

| Талбарын тоо | Хэлбэр |
|---|---|
| 1 | Inline edit (дарахад input болно, Enter/blur хадгална, Esc буцна) |
| 2–3 | Modal (480–560px) эсвэл popover |
| 4–8 | Side sheet / drawer (560–640px) |
| >8 эсвэл олон хэсэгтэй | Тусдаа хуудас, URL-тай (`/orders/new`) |

- **Unsaved-changes guard**: өөрчлөлттэй байхад навигаци, modal хаах, tab хаах үед асуу (`beforeunload` + router guard). Асуулт: «Хадгалаагүй өөрчлөлт байна» · [Үлдэх] [Хаях] — «Болих» гэсэн хоёрдмол үг хэрэглэхгүй.

## Feedback ба хугацаа

| Хугацаа | Шаардлага |
|---|---|
| ≤100ms | Шууд хариу мэт — ямар ч indicator хэрэггүй (hover, toggle, inline edit) |
| ≤1s | Урсгал тасрахгүй — товч loading төлөвт, курсор/spinner |
| ≤10s | Анхаарал хадгална — skeleton эсвэл progress; юу болж байгааг текстээр |
| >10s | **Progress bar + хувь/ETA**, цуцлах боломж, background-д шилжүүлж дуусахад мэдэгдэл |

- **Skeleton-ийг 300ms хойшлуул** (хурдан хариу дээр анивчихгүй); skeleton гарсан бол ≥500ms байлга (флаш хоёр талдаа).
- **Optimistic UI** зөвхөн: (1) амжилтын магадлал өндөр, (2) буцаах хялбар, (3) хариу ≤1s. Төлбөр, устгах, илгээх — optimistic биш. Алдвал төлөвийг буцааж, **алдааг тухайн элементийн дэргэд** харуул.

## Destructive үйлдэл

- Confirm dialog: гарчиг нь асуулт («“Захиалга #1042”-г устгах уу?»), body-д үр дагавар 1 өгүүлбэр, товч нь **үйлдлийн нэр** («Устгах», «Тийм» биш), улаан, баруун талд; «Болих» зүүнд нь. Default focus «Болих» дээр.
- **Буцаах боломжгүй** (аккаунт, tenant, DB) → **type-to-confirm**: нэрийг бичүүлнэ, таарахаас нааш товч disabled.
- **Undo toast (5 сек)** — буцаах боломжтой үйлдэлд confirm-ийн оронд илүү: устгалт soft-delete, 5 сек дараа л бодит. Олон тооны (bulk) үйлдэлд confirm + Undo хоёулаа.

## Эрхгүй (permission-denied) төлөв

| Дүрэм | Хэзээ |
|---|---|
| **Нуух** | Үүрэгт огт хамааралгүй модуль/цэс (кассчинд «Billing settings»); нуугаад хуудсыг хоосон орхихгүй |
| **Disable + tooltip** | Тухайн контекстэд байх ёстой, гэхдээ одоо хориотой үйлдэл («Зөвхөн админ баталгаажуулна») |
| **Харуулж тайлбарлах** | Хуудас руу шууд URL-аар орсон: 403 хуудас — хэн зөвшөөрөл өгөхийг + хүсэлт илгээх товч |

## Хоосон төлөвийн хоёр төрөл

| | First-run (анхны) | Filtered (шүүлтүүрийн үр дүн 0) |
|---|---|---|
| Copy | Юу болох, яагаад хэрэгтэйг 1–2 өгүүлбэр | «“xyz”-д таарах бичлэг алга» |
| CTA | Primary «Шинээр үүсгэх» + «Импортлох»/«Заавар» | «Шүүлтүүрийг цэвэрлэх» (secondary) |
| Зураг | Illustration болно, ≤200px | Зураггүй, icon хангалттай |
| Өндөр | Бүтэн content талбай | Table header үлдэж, доор нь 160–240px |

- Filtered хоосон төлөвт table-ийн header, шүүлтүүр chip-үүд **алга болохгүй** — үгүй бол цэвэрлэх аргагүй.

## Notifications · Keyboard · Multi-tenant · Audit

- **Notifications center**: top bar icon + тоо badge → popover 360–400px, сүүлийн 10–20, «Бүгдийг үзэх» → хуудас. Мөр бүр: avatar · текст (`line-clamp: 2`) · relative цаг · уншаагүй цэг; «Бүгдийг уншсан болгох». Toast түр, center нь архив.
- **Keyboard**: `?` shortcut жагсаалт · `/` хайлтад focus · `Esc` modal/drawer/popover хаах · **`Cmd/Ctrl+K` command palette** (навигаци + үйлдэл + хайлт, fuzzy, сүүлийн 5 үйлдэл дээр). Shortcut-ыг tooltip-д харуул (`Хадгалах ⌘S`); input дотор single-key shortcut идэвхгүй. Focus дүрэм — 07-accessibility.md.
- **Multi-tenant**: switcher sidebar-ын дээд хэсэгт, ≥8 tenant бол хайлттай; **tenant нэр бүх хуудсанд ил** (нэг tenant-тай ч нэр үлдэнэ). Орчин (staging) ба impersonation төлөв — хаагдахгүй өнгөт баннер (32–40px) дээд талд.
- **Audit / History**: detail-ийн «Түүх» tab эсвэл баруун sidebar-т timeline: avatar · «**Бат** төлөвийг *Шинэ → Баталгаажсан* болгосон» · цаг (`title`-д абсолют). Бичлэг = хэн · юу (хуучин → шинэ) · хэзээ; урт текстэд «Ялгааг харах» diff; шинээс хуучин руу, 20-оор.

## Хуудас бүрт байх ёстой

1. `h1` хуудасны нэр + primary action баруун дээд, нэг мөрөнд.
2. Гүн ≥3 бол breadcrumb; sidebar-т active цэс bar + weight-тэй.
3. Loading (300ms-ийн дараах skeleton) / empty (first-run ба filtered тусдаа) / error (retry-тэй) төлөвүүд.
4. Шүүлтүүр, сорт, хуудас, tab — бүгд URL-д; refresh/хуваалцахад хадгалагдана.
5. Destructive үйлдэл confirm (үйлдлийн нэртэй товч) эсвэл 5 сек Undo; буцаашгүй бол type-to-confirm.
6. Хадгалаагүй өөрчлөлтийн guard.
7. Эрхгүй үйлдэл: нуух/disable+tooltip/тайлбарлах дүрмийн аль нэг нь ухамсартай сонгогдсон.
8. Tenant нэр ба орчны баннер ил.
9. `Esc` хаана, `/` хайлт, `Cmd+K` palette, focus-visible ажиллана.
10. ≤1024px-д sidebar drawer, table эхний багана sticky, action-ууд overflow-д.

## Эх сурвалж

- Nielsen Norman Group — "Response Times: The 3 Important Limits" (nngroup.com/articles/response-times-3-important-limits)
- Nielsen Norman Group — "Breadcrumbs: 11 Design Guidelines for Desktop and Mobile" (nngroup.com/articles/breadcrumbs)
- Nielsen Norman Group — "Confirmation Dialogs Can Prevent User Errors — If Not Overused" (nngroup.com/articles/confirmation-dialog)
- Nielsen Norman Group — "Infinite Scrolling: When to Use It, When to Avoid It" (nngroup.com/articles/infinite-scrolling-tips)
- web.dev — "RAIL model" (web.dev/articles/rail)
- WCAG 2.2 — 1.4.1 Use of Color, 2.4.8 Location, 2.5.8 Target Size (Minimum), 3.3.4 Error Prevention (w3.org/TR/WCAG22)
- Material Design 3 — "Navigation drawer", "Navigation rail", "Data tables" (m3.material.io/components)
- Apple HIG — "Sidebars", "Undo and redo", "Loading" (developer.apple.com/design/human-interface-guidelines)
- IBM Carbon Design System — "Data table" pattern, "Notifications" pattern (carbondesignsystem.com)
- Refactoring UI — Adam Wathan & Steve Schoger (hierarchy, empty states, table design бүлгүүд)
