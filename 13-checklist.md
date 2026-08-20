# Pre-ship шалгах хуудас

## Яагаад

Дүрмүүд 01-08 файлд бий; энэ нь тэдгээрийг **хуудас/компонент бүр дээр нэг удаа, дараалалтай** давах хуудас. Бүх `[ ]` тэмдэглэгдээгүй бол «дууссан» гэж хэлэхгүй. Claude ч, хүн ч ижил жагсаалтаар явна.

## Төлөвүүд

- [ ] loading / empty / error / success 4 төлөв бүгд хэрэгжсэн (06-components.md)
- [ ] permission-denied төлөв тусдаа — хоосон хуудас биш, «эрх хүрэхгүй» + буцах зам
- [ ] skeleton нь эцсийн layout-тай ижил хэлбэр, өндөртэй — контент ирэхэд үсрэлт 0 (06-components.md)
- [ ] empty state-д юу байхгүй + CTA товч байна (06-components.md)
- [ ] error төлөвд retry эсвэл дараагийн алхам бий; техник код хэрэглэгчид харагдахгүй
- [ ] **Loading үед товч/талбарын хэмжээ өөрчлөгдөхгүй, давхар submit боломжгүй** (06-components.md)

## Өнгө & contrast

- [ ] Энгийн текст фонтойгоо ≥4.5:1 (01-color.md, 07-accessibility.md)
- [ ] Том текст (≥24px / ≥18.7px bold), icon, input border ≥3:1 (07-accessibility.md)
- [ ] Accent hue 1 л байна; semantic 2-3-аас хэтрээгүй (01-color.md)
- [ ] Статус өнгөөр дангаар биш — icon эсвэл label давхар (07-accessibility.md)
- [ ] Dark mode-д бүх хуудас нээж үзсэн; hex биш semantic token (08-design-tokens.md)
- [ ] **Focus ring хоёр theme-д хоёуланд харагдана: 2px outline + 2px offset** (07-accessibility.md)

## Типограф

- [ ] font-size бүгд rem; `62.5%` трюк байхгүй (02-typography.md)
- [ ] input/select/textarea ≥16px — iOS zoom үүсэхгүй (02-typography.md)
- [ ] Нийт font-size ≤8, weight ≤4, family ≤2 (+mono) (02-typography.md)
- [ ] Body line-height 1.5-1.7, гарчиг 1.1-1.3 (02-typography.md)
- [ ] Урт текстийн мөр `max-width: 65ch`-ээс хэтрэхгүй (02-typography.md)
- [ ] **Өө Үү Ёё glyph сонгосон font-д бүрэн бий — fallback font руу унаагүй** (02-typography.md)
- [ ] Урт монгол label (товч, tab, table header, nav) layout эвдэхгүй — wrap эсвэл truncate шийдэгдсэн

## Зай & layout

- [ ] Бүх зай 4/8 scale-ээс (4·8·12·16·24·32·48·64) (03-spacing-layout.md)
- [ ] **320px өргөнд хэвтээ scroll байхгүй** (03-spacing-layout.md)
- [ ] 200% zoom-д контент алдагдахгүй, хэвтээ scroll байхгүй (07-accessibility.md)
- [ ] Touch target ≥44×44px, хоорондын зай ≥8px (07-accessibility.md)
- [ ] Fixed header/bottom bar `env(safe-area-inset-*)` тооцсон
- [ ] Container max-width тогтоосон: контент 1140-1280px, dashboard 1440-1536px, форм 400-560px (03-spacing-layout.md)
- [ ] Өргөн table/code өөрийн `overflow-x: auto` саванд (03-spacing-layout.md)

## Компонент

- [ ] **Нэг view-д primary товч 1 л байна** (06-components.md)
- [ ] Label талбарын дээр; placeholder label-ийн оронд биш (06-components.md)
- [ ] Алдаа талбарын доор, `aria-describedby`-гаар холбогдсон (06-components.md, 07-accessibility.md)
- [ ] Тоон багана баруун зэрэгцээ + `tabular-nums`; хоосон нүд `—` (06-components.md)
- [ ] Truncate хийсэн текст бүрт `title` эсвэл tooltip бий
- [ ] Icon-only товч бүрт `aria-label` (04-visual-details.md)
- [ ] Modal: focus trap, Esc хаана, хаагдахад focus trigger рүү буцна (06-components.md)
- [ ] Destructive үйлдэл баталгаажуулалттай эсвэл Undo toast-той (06-components.md)

## Motion

- [ ] UI transition ≤300ms; hover 100-150ms (05-motion.md)
- [ ] Зөвхөн transform/opacity animate хийсэн — width/height/top/left биш (05-motion.md)
- [ ] **`prefers-reduced-motion: reduce` хүндэтгэсэн** (05-motion.md)

## A11y

- [ ] **Зөвхөн Tab-аар хуудсыг бүхэлд нь тойрч, бүх үйлдлийг Enter/Space-ээр хийж чадна** (07-accessibility.md)
- [ ] Heading дараалал h1→h2→h3 алгасаагүй; h1 нэг л байна (07-accessibility.md)
- [ ] `header/nav/main/footer` landmark бүгд бий (07-accessibility.md)
- [ ] `<html lang="mn">` / `lang="en"` идэвхтэй хэлээ дагана
- [ ] Зураг бүрт утгатай `alt`; чимэглэлийнх `alt=""` эсвэл `aria-hidden`
- [ ] Async үр дүн (хайлт, хадгалсан, алдаа) `aria-live` бүсээр зарлагддаг

## Performance

- [ ] LCP ≤2.5s, INP ≤200ms, CLS ≤0.1 (Lighthouse mobile дээр) (12-landing.md)
- [ ] Зураг бүрт `width/height` эсвэл `aspect-ratio`; fold-ийн доорхи `loading="lazy"` (04-visual-details.md)
- [ ] Hero/LCP зураг preload, WebP/AVIF + srcset (04-visual-details.md)
- [ ] Font `font-display: swap`, үндсэн woff2 preload, нийт font ≤2 файл (02-typography.md)
- [ ] **Ачаалахад layout shift нүдэнд харагдахгүй — skeleton/aspect-ratio-гоор барьсан**

## Локалчлал

- [ ] **Бүх string i18n-ээр; EN/MN хоёуланд түлхүүр бий, fallback түлхүүр нэр харагдахгүй** (09-localization-mn.md)
- [ ] Огноо `yyyy-MM-dd HH:mm`, UTC+8-аар харуулна; timezone нэг газар тогтоосон (09-localization-mn.md)
- [ ] Мөнгө `₮` + мянгатын тусгаарлагч (`1,250,000₮`), tabular-nums (09-localization-mn.md)
- [ ] MN UI-д hardcoded англи үг (Save, Cancel, Loading…) байхгүй

## Контент

- [ ] Dashboard хуудас: sidebar/breadcrumb/primary action/empty-first-run дүрэм (10-dashboard-patterns.md); chart бүр 11-data-viz.md-ийн checklist-ээр

- [ ] Public copy-д дотоод email, staging URL, IP байхгүй
- [ ] Алдааны мессеж хүний хэлээр — «500 Internal Server Error» биш «Хадгалж чадсангүй. Дахин оролдоно уу»
- [ ] Товчны label үйл үг: «Хадгалах», «Устгах» — «OK», «Тийм» биш
- [ ] Хоосон/placeholder текст (Lorem ipsum, TODO) үлдээгүй

## Хэрхэн ажиллуулах

1. Browser-ийг 320px / 768px / 1280px өргөнд нээж хуудас бүрийг гүйлгэнэ.
2. 200% zoom (Cmd/Ctrl +) — хэвтээ scroll, давхцал хайна.
3. Хулганагүй: зөвхөн Tab/Shift+Tab/Enter/Esc-ээр бүх flow-г дуустал явна.
4. Dark mode асааж 1-3-ыг давтана.
5. Lighthouse (mobile) + axe DevTools — алдаа 0, performance ≥90.
6. Desktop + mobile screenshot аваад хажуу хажууд нь харж эцсийн нүдний шалгалт.

## Эх сурвалж

- WCAG 2.2 — SC 1.4.3 Contrast (Minimum), 1.4.4 Resize Text, 1.4.10 Reflow, 1.4.11 Non-text Contrast, 2.1.1 Keyboard, 2.4.7 Focus Visible, 2.5.8 Target Size (Minimum), 3.1.1 Language of Page, 4.1.3 Status Messages — https://www.w3.org/TR/WCAG22/
- web.dev — "Web Vitals" (LCP/INP/CLS thresholds) — https://web.dev/articles/vitals
- web.dev — "Optimize Cumulative Layout Shift" — https://web.dev/articles/optimize-cls
- MDN — `prefers-reduced-motion`, `env()` (safe-area-inset), `font-display`, ARIA live regions — https://developer.mozilla.org
- Nielsen Norman Group — "Designing Empty States", "Error-Message Guidelines" — https://www.nngroup.com
- Apple HIG — "Layout" (safe area), "Buttons" (44pt target) — https://developer.apple.com/design/human-interface-guidelines/
- Material 3 — "Accessibility", "States" — https://m3.material.io
