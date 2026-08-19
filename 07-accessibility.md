# Accessibility

Албан ёсны цорын ганц «стандарт» бол **WCAG 2.2** (AA түвшин нь практик жишиг). Бусад нь convention.

## Contrast

- Энгийн текст (<24px): **≥4.5:1**
- Том текст (≥24px эсвэл ≥18.7px bold): **≥3:1**
- UI компонент, icon, input border (non-text): **≥3:1**
- Disabled төлөв contrast шаардлагаас чөлөөлөгддөг — гэхдээ уншигдахуйц байлга.
- Шалгах: browser DevTools, эсвэл APCA (шинэ үеийн алгоритм, WCAG 3-д орно).

## Zoom ба хэмжээ

- **200% zoom-д** контент алдагдахгүй, хэвтээ scroll үүсэхгүй байх ёстой — rem + fluid layout үүнийг шийднэ.
- WCAG font-size-ийн доод хэмжээ заадаггүй; харин zoom + reflow шаарддаг.
- `user-scalable=no`, `maximum-scale=1` хэзээ ч тавихгүй.

## Keyboard

- Бүх interactive элемент Tab-аар хүрэгдэж, Enter/Space-ээр ажиллана.
- **Focus-visible** төлөв тод байх: 2px outline + 2px offset, accent өнгөөр. `outline: none`-ыг орлуулах юмгүйгээр бүү бич.
- Tab дараалал нь визуал дарааллыг дагана; `tabindex` эерэг утгаар бүү хэрэглэ.
- Modal — focus trap; хаагдахад анхны trigger рүү focus буцаана.
- Skip link («Гол контент руу») — nav ихтэй хуудсанд.

## Semantic HTML

- `div`+onClick биш `button`; `span` биш `a` (навигацид).
- Heading дараалал алгасахгүй: h1 → h2 → h3 (харагдац нь class-аар, бүтэц нь tag-аар).
- Landmark-ууд: `header/nav/main/footer` — screen reader-ийн навигаци.
- Icon-only товчид `aria-label`; чимэглэлийн icon-д `aria-hidden="true"`.
- Форм: `label[for]` заавал холбоотой; алдааг `aria-describedby`-гаар талбартай холбо.

## Өнгөнөөс хамаарахгүй байх

- Статусыг зөвхөн өнгөөр илэрхийлэхгүй — icon/label давхар (ногоон/улаан color blindness-д ижил харагдаж болно).
- Линк текст дотроо зөвхөн өнгөөр ялгарч байвал underline нэм.

## Touch

- Touch target **≥44×44px** (Apple HIG) / 48px (Material). Жижиг текстэн линк ч padding-аар хүрнэ.
- Target хоорондын зай ≥8px — андуурч дарахаас сэргийлнэ.

## Motion

- `prefers-reduced-motion: reduce`-ийг хүндэл (05-motion.md-г үз).
- Автоматаар тоглодог video/carousel-д зогсоох боломж заавал.

## Шалгах хэрэгслүүд

- Lighthouse (Chrome DevTools) — эхний шүүлт
- axe DevTools — дэлгэрэнгүй
- Гараар: Tab-аар л бүх хуудсаа тойрч үзэх — хамгийн хурдан бодит тест
- VoiceOver (macOS: Cmd+F5) — жинхэнэ screen reader туршилт
