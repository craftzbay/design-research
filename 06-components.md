# Компонентын жишиг

## Товч (Button)

- **Иерархи 3 түвшин**: primary (accent fill) · secondary (outline/ghost) · tertiary (text-only). Нэг view-д primary **нэг л байх** ёстой.
- Хэмжээ: өндөр 32px (compact UI) / 36-40px (default) / 44-48px (marketing, mobile).
- Padding: хэвтээ нь босоогоосоо ~2 дахин (жишээ: 10px 20px).
- Төлөвүүд бүгд байх: default / hover / active / focus-visible / disabled / loading.
- Loading үед хэмжээ өөрчлөгдөхгүй — текстийг spinner-ээр солихдоо width хадгал.
- Destructive үйлдэл (устгах) — улаан, гэхдээ primary улаан товч ганц алхамд шууд устгахгүй, баталгаажуулалттай.

## Форм

- **Label заавал, дээр нь** — placeholder-ийг label болгон хэрэглэхгүй (бичиж эхлэхээр алга болж контекст алдагдана).
- Input өндөр товчтой ижил (36-44px), font-size ≥16px (iOS zoom-ээс сэргийлнэ).
- Алдааг **талбарын доор, улаан текст + icon-той**, submit дарсны дараа эсвэл blur дээр харуул — бичиж байх үед нь биш.
- Ганц баганаар — хоёр багана форм бөглөх дарааллыг эвддэг (нэр/овог мэтийн жижиг хос л зэрэгцэж болно).
- Required-ийг `*`-ээр биш, харин цөөн optional талбараа «(заавал биш)» гэж тэмдэглэх нь илүү.
- Autocomplete attribute-уудыг өг (`autocomplete="email"` гэх мэт) — UX + password manager.

## Table (data-нягт UI)

- Тоон багана **баруун зэрэгцээ + tabular-nums** (`font-variant-numeric: tabular-nums`), текст зүүн.
- Мөрийн өндөр: compact 40px / default 48-52px.
- Zebra striping ЭСВЭЛ row border — хоёуланг нь биш.
- Header: 12-13px, 500-600 weight, muted өнгө, uppercase бол letter-spacing нэм.
- Урт table-д sticky header; mobile-д хэвтээ scroll (`overflow-x: auto`) эсвэл card болгон эвхэх.
- Хоосон нүд: `—` (em dash), 0 болон хоосныг ялга.

## Card

- Padding: 16px (compact) / 24px (default).
- Нэг card = нэг ойлголт; card дотор card-аас зайлсхий.
- Бүхэлдээ clickable бол hover төлөвтэй + доторх линкүүд nested interactive болохоос сэргийл.

## Empty / Loading / Error төлөвүүд

Компонент бүр 4 төлөвтэй гэж төлөвлө: **loading / empty / error / success**.

- **Empty state**: юу байхгүйг хэлээд дараагийн үйлдлийг зааж өг (CTA-тай). Хоосон table биш «Одоогоор бүртгэл алга. [Шинээр нэмэх]».
- **Loading**: layout-тай ижил хэлбэрийн skeleton — контент ирэхэд үсрэлтгүй.
- **Error**: юу болсныг + юу хийж болохыг (retry товч). Техник алдааны код хэрэглэгчид ил гаргахгүй.
- Optimistic UI: хурдан үйлдлүүдэд (like, toggle) серверийг хүлээлгүй UI-гаа шинэчил, алдвал буцаа.

## Modal / Dialog

- Өргөн: alert 400px / форм 480-560px / том контент 720px+. Full-screen нь mobile-д.
- Focus trap + Esc хаана + overlay дарахад хаагдана (форм бөглөж байсан бол баталгаажуул).
- Modal доторх modal — дизайны алдааны шинж; nested хэрэгтэй бол flow-гоо эргэнэ хар.

## Toast / Notification

- Байрлал нэг л газар (ихэвчлэн баруун дээд/доод).
- Success 3-5 сек өөрөө алга болно; error нь хэрэглэгч хаатал үлдэнэ.
- Үйлдэлтэй toast (Undo) — устгах мэтийн үйлдлийн стандарт хамгаалалт.

## Tabs

- **Нэг мөрөнд ≤6 tab** — илүү бол dropdown/sidebar nav руу шилж.
- Идэвхтэй tab: 2px underline indicator + текст өнгө контраст; зөвхөн өнгөөр ялгахгүй (07-accessibility.md-г үз).
- Tab өндөр 40-48px, хоорондын зай 16-24px; label 1-2 үг, icon бол заавал текст-тэй.
- Keyboard: `←`/`→` tab солино, `Tab` нь panel руу орно; `role="tablist"` / `role="tab"` / `aria-selected`.
- Идэвхтэй tab-ыг URL-тай sync хий (`?tab=billing` эсвэл `#billing`) — refresh, share хийхэд хадгалагдана.
- Tab дотор tab бүү үүрлүүл — хоёр дахь түвшин нь segmented control эсвэл sub-nav.
- Tab солиход scroll position дээр байрлал үсрэхгүй байх: panel-ийн min-height тогтоо.

## Dropdown / Menu

- **≤8 item**; илүү бол дээр нь хайлтын талбар нэм (combobox болгоно).
- Мөрийн өндөр 36-40px, хэвтээ padding 12px, panel өргөн 180-280px, border-radius 8px, shadow md.
- Логик бүлэгт хуваахдаа 1px divider + 4-8px зай; бүлэг бүр ≤4-5 item.
- Destructive үйлдэл (Устгах) хамгийн сүүлд, divider-ээр тусгаарлаад улаан текст.
- Icon хэрэглэвэл бүх item-д, эсвэл нэгэнд ч биш — холимог нь зэрэгцээ алдагдуулна. Icon 16px, текстээс 8-12px зайтай.
- Keyboard: `↑`/`↓` явна, `Enter` сонгоно, `Esc` хаана, эхний үсгээр үсэрнэ; фокус эхлээд эхний item дээр.
- Trigger товчин дээр `aria-haspopup="menu"` + `aria-expanded`; viewport-оос гарах бол автоматаар дээш/хажуу тийш эргэнэ.
- Одоогийн сонголтыг checkmark-аар тэмдэглэ (select-маягийн menu).

## Tooltip vs Popover

| | Tooltip | Popover |
|---|---|---|
| Нээх | hover + keyboard focus | click / tap |
| Агуулга | зөвхөн текст, ≤1 мөр (~60 тэмдэгт) | гарчиг, текст, товч, форм ч болно |
| Хаах | hover/focus алдагдахад | гадна дарах, `Esc`, хаах товч |
| Mobile | байхгүй (hover үгүй) | ажиллана |

- Tooltip нээгдэх хоцрогдол **300-500ms**, хаагдах 0-100ms; нэг tooltip нээлттэй үед дараагийнх нь хоцрогдолгүй.
- Tooltip-д тавьсан мэдээлэл **зайлшгүй бол болохгүй** — зөвхөн нэмэлт тайлбар; чухал мэдээлэл харагдах текст байна.
- Icon-only товч бүр tooltip + `aria-label` хоёулантай.
- Tooltip дотор interactive элемент тавихгүй; хэрэгтэй бол popover.
- Popover өргөн 240-360px, padding 16px, заагч сум (arrow) заавал биш; нээгдэхэд фокус дотор нь орно, хаахад trigger руу буцна.
- Mobile-д tooltip-ийн оронд: харагдах helper text, эсвэл `(i)` товч → popover/bottom sheet.

## Badge / Status

- **Статус = icon + текст**, зөвхөн өнгөт цэг биш (өнгө ялгадаггүй хэрэглэгч + хэвлэхэд).
- Semantic өнгө дээд тал нь 5: neutral / info / success / warning / danger. 6 дахь «статус» гарвал өнгө биш текстээр ялга.
- Хэмжээ: өндөр 20-24px, текст 11-12px, хэвтээ padding 6-8px, 500-600 weight.
- Өнгөт фон: 100-200 түвшний зөөлөн фон + 700-800 текст (ижил hue) — контраст ≥4.5:1 (01-color.md-г үз).
- Uppercase + `letter-spacing: 0.04-0.06em` хэрэглэж болно, гэхдээ зөвхөн 11-12px-д; Кирилл uppercase-д зай бага зэрэг их (0.06em).
- Тооны badge (notification count): pill (`border-radius: 9999px`), min-width 18-20px, 99-өөс дээш бол «99+».
- Presence (online/offline): 8-10px цэг, аватарын баруун доод буланд, 2px фонтой ижил өнгийн ring.
- Badge-ийг товч биш — дарагддаг бол tag/chip эсвэл filter.

## Avatar

- Хэмжээ тогтмол 3-4 шат: **24 / 32 / 40px** (+ 64-96px profile хуудсанд); тойрог хэрэглэгчид, квадрат (radius 6-8px) байгууллага/workspace-д.
- Зураггүй бол initials fallback: нэр, овгийн эхний үсэг (Кириллд ч мөн адил — «Батболд Сүхбат» → «БС»), 1-2 үсэг, uppercase, хэмжээний 40-45% font-size.
- Initials-ийн фон: нэрний hash-аас тогтмол сонгосон 6-8 зөөлөн өнгө — refresh бүрт солигддоггүй.
- Зураг: `object-fit: cover`, `alt`-д нэр (зөвхөн чимэглэл бол `alt=""`).
- Статус ring: 2px ring + 2px фон өнгийн offset (`box-shadow: 0 0 0 2px var(--bg), 0 0 0 4px var(--ring)`).
- Avatar group: давхцал −8px (32px) / −6px (24px), **≤4 харуулаад «+N»**; давхцсан хэсэг 2px фон өнгийн border-той.
- Ачаалж байхад initials-ийг шууд харуул (skeleton биш) — зураг ирэхэд солино.

## Tag / Chip

- Өндөр 24-32px, текст 12-13px, padding 4-8px / 8-12px, border-radius 6px эсвэл pill.
- Устгах `×` нь **hit target ≥24×24px** (харагдах icon 12-14px байсан ч) + `aria-label="Устгах: {нэр}"`.
- Гурван төрлийг хольж болохгүй:
  - **Input chip** — хэрэглэгчийн оруулсан утга (email, tag); устгагдана.
  - **Filter chip** — toggle, сонгогдвол checkmark + фон; олон сонгож болно.
  - **Choice chip** — radio шиг, нэгийг л сонгоно.
- Олон chip-ийг **wrap** хий, хэвтээ scroll биш (scroll нь далд chip-үүдийг нуудаг; mobile-д л 1 мөр scroll болно).
- Chip-ийн урт текст: max-width 160-200px + ellipsis, бүтнийг title/tooltip-оор.
- Input chip талбарт `Backspace` сүүлийн chip-ийг сонгож, дахин дарахад устгана; `Enter`/`,` шинэ chip үүсгэнэ.
- Сонгогдсон filter chip-үүдийн тоог «Шүүлтүүр (3)» гэж харуул + «Цэвэрлэх» нэг товч.

## Select vs Radio vs Checkbox

| Сонголтын тоо | Нэгийг сонгох | Олныг сонгох |
|---|---|---|
| 2-5 | radio (бүгд харагдана) | checkbox |
| 6-15 | `<select>` | multi-select combobox |
| 15+ | searchable combobox | searchable multi-combobox + сонгосон chip |

- **≤5 сонголт бол radio/checkbox** — нэг дарахад харагдана, select нь нэмэлт click.
- Boolean: үр дүн нь **шууд** (дарангуут хадгалагдана) бол switch; форм submit-ээр хадгалагддаг бол checkbox.
- Radio-д default сонголт заавал байх (эсвэл ухамсартайгаар «Сонгоогүй»); checkbox-д default нь ихэвчлэн unchecked.
- Radio/checkbox-ийн hit target: бүх label дарагдана, мөрийн өндөр ≥32px, icon 16-20px.
- Switch-ийн label нь төлөв биш, тохиргооны нэр: «Мэдэгдэл» (On/Off биш «Идэвхтэй/Идэвхгүй» гэж label өөрчлөхгүй).
- Native `<select>` mobile-д хамгийн сайн — custom select зөвхөн хайлт, icon, бүлэглэл хэрэгтэй үед.
- Сонголтын тоо тодорхойгүй (API-аас ирдэг) бол босгоор компонент сол: `n <= 5 ? radio : n <= 15 ? select : combobox`.

## Date / Time

- Харуулах: **≤7 хоногийн доторх бол харьцангуй** («3 минутын өмнө», «өчигдөр 14:20»), түүнээс хуучин бол абсолют.
- Харьцангуй цаг үргэлж `title`/tooltip-оор абсолют утгатай: `<time datetime="2026-08-20T14:20:00+08:00" title="2026-08-20 14:20">`.
- Абсолют формат нэг л байна: `yyyy-MM-dd HH:mm` (24 цаг); жил орхих нь зөвхөн энэ жилийн огноонд, тухайн газар нь ойлгомжтой үед.
- Хүснэгт, лог, тайланд харьцангуй биш абсолют — эрэмбэлэх, харьцуулахад хэрэгтэй.
- Харьцангуй цагийг 60 сек тутам шинэчил, «0 секундын өмнө» биш «дөнгөж сая».
- Picker: эхлээд **native `<input type="date">` / `type="datetime-local"`** (mobile keyboard, locale, хүртээмж бэлэн); custom picker зөвхөн range, preset («Сүүлийн 7 хоног»), disabled өдрүүд хэрэгтэй үед.
- Custom range picker: 2 сар зэрэгцээ (desktop) / 1 сар (mobile), preset жагсаалт зүүн талд, сонгосон муж фон өнгөөр.
- Гараар бичих боломж үргэлж үлдээ (picker дангаараа биш) + format placeholder «2026-08-20».
- Timezone: хадгалахдаа UTC, харуулахдаа хэрэглэгчийн бүс; олон бүсийн хэрэглэгчтэй бол товчлол нэм («14:20 ULAT») — дэлгэрэнгүйг 09-i18n.md-г үз.

## File upload

- Drag-drop зон + **«Файл сонгох» товч хоёулаа** (drag нь mobile, keyboard-д байхгүй); зон бүхэлдээ дарагдана.
- Зөвшөөрөх төрөл, дээд хэмжээ, тоог **урьдчилан бич**: «PNG, JPG, PDF · нэг файл ≤10MB · хамгийн ихдээ 5»; `accept` attribute-аар давхар хязгаарла.
- Файл бүрт өөрийн мөр: нэр (ellipsis), хэмжээ, progress bar (0-100%), cancel `×`.
- Алдаа файл тус бүрээр (нэг файл унавал бусад нь үргэлжилнэ): «too-big.pdf — 10MB-аас хэтэрсэн (14MB)».
- Зургийн preview thumbnail 48-64px, квадрат `object-fit: cover`; бусад төрөлд file-type icon.
- Upload амжилттай бол устгах/солих товч; форм submit хүртэл upload-ыг хойшлуулахгүй (сонгонгуут эхэлнэ) — гэхдээ submit-ээс өмнө бүгд дууссан эсэхийг шалга.
- Drag зон хэмжээ: өндөр ≥120px, dashed 2px border, drag-over төлөвт фон + border өнгө солигдоно.
- Урт upload (>10 сек) — хуудас солиход анхааруулга (`beforeunload`).

## Search

- `<input type="search">` + `role="searchbox"`-ийн оронд native семантик; icon зүүн, clear `×` баруун (утгатай үед л).
- Бичихэд хайдаг бол **debounce 250-300ms** + хамгийн сүүлийн хүсэлт л үр дүн өгнө (race-ээс сэргийл); ≥2 тэмдэгтээс эхэлнэ.
- `/` товч фокус авчирна (текст талбарт байхгүй үед), `Esc` цэвэрлээд фокус гаргана.
- Үр дүнгийн тоо ил: «128 илэрц · «батболд»»; 0 бол юу бичсэнийг давтаад **санал** өг («Зөв бичгийг шалга», ойролцоо хайлт, шүүлтүүр арилгах).
- Таарсан хэсгийг `<mark>`-аар тодруул (bold, өнгөт фон биш); Кирилл/латин, том/жижиг үсэг ялгахгүй.
- Хайлт хийхэд URL шинэчил (`?q=`) — back, share ажиллана; хуудас солиход утга хадгалагдана.
- Loading: талбарт жижиг spinner, өмнөх үр дүнг арилгахгүй (layout үсрэхгүй).
- Autocomplete dropdown: ≤8 санал, `↑`/`↓` + `Enter`, сүүлийн хайлтууд эхэнд.

## Command palette / shortcuts

- `Cmd+K` (macOS) / `Ctrl+K` (бусад) нээнэ; platform-ыг таниад зөвхөн тохирох тэмдэгтийг харуул (`⌘K` vs `Ctrl K`).
- Fuzzy match (дараалал хадгалсан үсэг тааруулах), typo-д тэсвэртэй; хайлтын талбар дээр, үр дүн ≤10 харагдана, scroll-тай.
- **Хоосон үед сүүлд ашигласан 5-8 үйлдэл** эхэнд, дараа нь бүлэг тус бүрийн түгээмэл.
- Мөр бүр: icon + нэр + (баруун талд) shortcut hint бүдэг өнгөөр; бүлгийн гарчиг 11-12px uppercase.
- `?` (текст талбарт байхгүй үед) бүх shortcut-ийн help sheet нээнэ; shortcut-уудыг бүлэглэн (Navigation / Edit / View) хүснэгтээр.
- Shortcut-ийг tooltip-д давхар харуул: «Хадгалах ⌘S».
- Single-key shortcut (`g` `i` мэт) нь текст талбарт идэвхгүй; browser-ийн default-тай зөрчилдөхгүй (`Cmd+L`, `Cmd+T`, `Cmd+W` бүү авч хэрэглэ).
- Palette өргөн 560-640px, дэлгэцийн дээрээс 15-20% зайд; `Esc` хаана, фокус trigger руу буцна.

## Multi-step форм

- **≤5 алхам**; илүү бол алхмуудыг нэгтгэ эсвэл хоёр тусдаа flow болго.
- Stepper: дугаар + label («1 Мэдээлэл · 2 Хаяг · 3 Төлбөр»), одоогийн алхам bold, дууссан нь checkmark; mobile-д «2/4 · Хаяг» гэсэн товч хувилбар.
- Алхам бүрийг **тухайн алхамд нь** validate хий, дараагийн руу шилжихээс өмнө; бүх алдааг сүүлд овоолохгүй.
- «Буцах» үргэлж боломжтой, оруулсан утга хадгалагдана; дууссан алхам руу stepper-ээс шууд очиж болно (дараагийнх руу биш).
- Draft автоматаар хадгалагдана (localStorage эсвэл сервер) — хуудас хаагаад буцаж ирэхэд «Үргэлжлүүлэх» сонголт.
- Submit-ийн өмнө **summary алхам**: бүх утгыг алхам тус бүрээр харуулаад «Засах» линктэй.
- Товчнууд: баруун «Үргэлжлүүлэх» (primary), зүүн «Буцах» (secondary); сүүлд «Илгээх»; `Enter` = үргэлжлүүлэх.
- Алхам бүр 3-7 талбар; нэг алхамд 1-2 талбар бол нэгтгэ.
- Progress %-ийг ойролцоогоор биш алхмаар хэмж — «60%» биш «3/5».

## Confirmation хэв маяг

| Үйлдлийн эрсдэл | Хэв маяг |
|---|---|
| Буцаах боломжтой (нэг бичлэг устгах, архивлах) | шууд гүйцэтгээд Undo-той toast |
| Буцаахгүй, дунд зэрэг (төслөө устгах, гишүүн хасах) | modal confirm |
| Сүйрлийн (бүх өгөгдөл, аккаунт, production DB) | type-to-confirm |

- **Эхний сонголт soft delete + Undo 5-10 сек** — confirm modal-ыг хэрэглэгч уншихгүй дардаг; Undo нь ойлгож амждаг.
- Modal confirm: гарчигт үйлдэл + объектын нэр («"Q3 тайлан" төслийг устгах уу?»), ерөнхий «Итгэлтэй байна уу?» биш; үр дагаврыг 1 өгүүлбэрээр.
- Confirm товч нь үйлдлийн үг («Устгах»), «OK»/«Тийм» биш; destructive бол улаан; default фокус Cancel дээр.
- Type-to-confirm: объектын нэрийг яг бичүүлнэ (`project-name`), бичтэл товч disabled; copy-paste-ийг зориуд хаахгүй (хүртээмж).
- **Давхар баталгаажуулалт хэзээ ч байхгүй** (modal → дахин modal) — хоёр дахь нь эхнийхийн утгыг устгана.
- Олон зүйл устгахад тоог бич: «14 файл устгах».
- Буцаах боломжгүйг «Энэ үйлдлийг буцаах боломжгүй» гэж тодорхой хэл, зөвхөн ингэж хэлэх ёстой үед.

## Pagination

- **Offset pagination + хуудасны дугаар**: ≤7 товч харагдана (1 … 4 5 6 … 40), одоогийн нь тод; prev/next icon + текст.
- Байршил, тоо ил: «1–25 / 1,240» (хязгаар, нийт); нийт тоолох нь удаан бол «1–25 / 1,000+».
- Хуудасны хэмжээ сонгогч 25 / 50 / 100 (default 25); сонголт URL/preference-д хадгалагдана.
- Хуудас `?page=3&size=50` URL-д — back, refresh, share ажиллана; шүүлтүүр өөрчлөгдвөл page=1 руу буцна.
- Том (>10k) эсвэл амьд өөрчлөгддөг жагсаалтад **cursor pagination + «Цааш үзэх» товч** — offset нь мөр давхцуулна/алгасна.
- Infinite scroll зөвхөн feed-д (шийдвэр гаргадаггүй, «дуусах» хэрэггүй контент); footer хэрэгтэй хуудсанд хэзээ ч биш; дотор нь ч «Цааш үзэх» fallback + scroll position сэргээх.
- Хуудас солиход жагсаалтын эхэнд scroll, фокус жагсаалтын гарчиг руу; `aria-current="page"` одоогийн дугаарт.
- Mobile-д дугааруудыг prev/next + «3 / 40» болгон цөөл.
- Table-д pagination доор, сонголт/нийт мөрийн тоо зүүн, дугаар баруун.

## Onboarding / first-run

- **Empty state өөрөө onboarding**: хоосон дэлгэц бүр юу хийхийг заана + нэг primary CTA (дээрх «Empty / Loading / Error»-г үз); тусдаа tour ихэвчлэн хэрэггүй.
- Checklist ≤3-5 алхам («Профайл бөглөх · Эхний төсөл үүсгэх · Гишүүн урих»), гүйцэтгэсэн нь checkmark, прогресс «2/3»; dashboard-ын булан/sidebar-д, modal биш.
- Хаах боломжтой (dismiss) + буцааж нээх зам (Тусламж цэсэнд); хаасныг серверт хадгал — дахин гарч ирэхгүй.
- Modal tour хийх бол **≤3 алхам**, алгасах товч алхам бүрт, нэг л удаа; 4+ алхамтай tour-ыг хэн ч дуусгадаггүй.
- Tooltip-маягийн заавар (coachmark) нэг удаад 1 л; тухайн feature-ийг анх харахад, эхний минутад бүгдийг биш.
- Эхний утга автоматаар бэлд (sample data, default төсөл) — хоосон биш «бэлэн» мэдрэмж; sample-ийг тодорхой тэмдэглээд нэг товчоор устгана.
- Заавал бөглөх зүйлийг бүртгэлийн дараа биш, хэрэглэх мөчид асуу (progressive): төлбөрийн мэдээллийг эхний төлбөрт.
- «Шинэ» badge нь 7-14 хоног л, дараа нь алга болно.

## Эх сурвалж

- Apple Human Interface Guidelines — Components: Buttons, Text fields, Toggles, Pickers, Menus, Popovers, Alerts, Action sheets, Tab bars, Segmented controls, Progress indicators — developer.apple.com/design/human-interface-guidelines/components
- Material Design 3 — Components: Buttons, Text fields, Tabs, Menus, Tooltips, Badges, Chips, Checkbox, Radio button, Switch, Date pickers, Dialogs, Snackbar, Search, Navigation — m3.material.io/components
- W3C WAI-ARIA Authoring Practices Guide (APG) — Patterns: Tabs, Menu and Menubar, Menu Button, Tooltip, Dialog (Modal), Combobox, Radio Group, Switch, Listbox, Grid — w3.org/WAI/ARIA/apg/patterns/
- WCAG 2.2 — 1.4.1 Use of Color, 1.4.3 Contrast (Minimum), 2.1.1 Keyboard, 2.4.3 Focus Order, 2.5.8 Target Size (Minimum), 3.3.1 Error Identification, 4.1.2 Name, Role, Value — w3.org/TR/WCAG22/
- Nielsen Norman Group — «Tabs, Used Right»; «Drop-Down Menus: Use Sparingly»; «Tooltip Guidelines»; «Popups: 10 Problematic Trends and Alternatives»; «Checkboxes vs. Radio Buttons»; «Listboxes vs. Dropdown Lists»; «Toggle-Switch Guidelines»; «Date-Input Form Fields: UX Design Guidelines»; «Confirmation Dialogs Can Prevent User Errors — If Not Overused»; «Infinite Scrolling Is Not for Every Website»; «Onboarding Tutorials vs. Contextual Help»; «Empty State»; «Search-Log Analysis: The Most Overlooked Opportunity in Web UX» — nngroup.com/articles/
- Refactoring UI (Adam Wathan, Steve Schoger) — «Hierarchy is Everything», «Designing Text», «Working with Color», «Finishing Touches» бүлгүүд — refactoringui.com
- MDN Web Docs — `<input type="date">`, `<input type="search">`, `<time>`, `<select>`, `<dialog>`, `autocomplete` attribute, Popover API — developer.mozilla.org
- web.dev — «Building a tooltip component», «Building a dialog component», «Building a tabs component» (GUI Challenges) — web.dev
- Shopify Polaris — Components: Tabs, Popover, Badge, Avatar, Tag, Pagination, DropZone — polaris.shopify.com/components
- GOV.UK Design System — Components: Date input, File upload, Pagination, Radios, Checkboxes, Select; Patterns: Confirm a phone number, Check answers — design-system.service.gov.uk
