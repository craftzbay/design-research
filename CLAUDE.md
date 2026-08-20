# design-research

Вэб дизайны жишиг, стандарт, практик дүрмүүдийн лавлах репо (Markdown баримтууд). Код байхгүй — зөвхөн баримт. Responsive сайт, SaaS/dashboard UI, landing page-д хамаарна. GitHub Pages: https://craftzbay.github.io/design-research/

## Стек ба бүтэц

- Зөвхөн Markdown, root-д хавтгай байрласан, дугаарласан 14 баримт (`00-sources` … `13-checklist`) + `README.md` (агуулгын хүснэгт, cheat sheet, ашиглах урсгал) + `references/` (жишиг зургууд — амтны сан).
- `_config.yml` — Jekyll (`jekyll-theme-cayman`, `jekyll-relative-links`); GitHub Pages өөрөө build хийнэ, локал build/test/lint байхгүй.
- Нэмэлт баримтууд (2026-08-20): `09-localization-mn` (монгол хэл) · `10-dashboard-patterns` · `11-data-viz` · `12-landing` · `13-checklist` (pre-ship) · `00-sources`. Баримт бүр `## Эх сурвалж`-аар төгсдөг — шинэ дүрэм нэмэхдээ эх сурвалжгүй тоо бичихгүй.
- Баримтууд: `01-color` (60-30-10, palette, contrast, dark) · `02-typography` (family, modular scale, rem, clamp) · `03-spacing-layout` (4/8px scale, breakpoint, grid) · `04-visual-details` (radius, shadow, border, icon) · `05-motion` (100-400ms, ease-out, transform+opacity) · `06-components` (товч, форм, table, 4 төлөв, modal/toast) · `07-accessibility` (WCAG 2.2 AA) · `08-design-tokens` (primitive→semantic→component, light/dark, Tailwind v4 `@theme`).

## Бусад проектод хэрхэн ашиглах

- Шинэ UI эхлүүлэхэд эндээс эхэл: `08-design-tokens.md`-ийн semantic token багцыг суурь болгож, проектын өөрийн сонголтыг (scale, суурь px, өнгө) тухайн репогийн өөрийн docs-д бич — энд биш.
- Энэ репо нь ерөнхий жишиг; проект-тусгай шийдвэр (жишээ нь nexus-mini: minor third 1.2 scale, 14px суурь — ERP нягт) энд орохгүй.
- Код бичихдээ баримтын дүрмийг мөрд: hex-ийг шууд биш semantic token-оор, текстэд rem, зайд 4/8px scale, contrast ≥4.5:1, `prefers-reduced-motion`-ыг хүндэл.

## Инварантууд

- Шинэ сэдэв = дараагийн дугаартай файл (`09-*.md`) + `README.md`-ийн хүснэгт ба cheat sheet-ийг шинэчил.
- Баримт Монгол кирилл прозоор; нэр томьёо, CSS/token нэр, код English.
- Файл бүр `# Гарчиг` → `## Яагаад`/зарчим → тодорхой тоон дүрэм гэсэн загвартай; зөвлөмж биш, шалгаж болох дүрэм бич (тоо, хязгаар, жишээ код).
- Файлын нэрийг бүү өөрчил — README болон бусад репогийн холбоосууд relative path-аар заадаг.

## Шалгах

- Markdown-ы relative холбоосууд бодит файл руу заадаг эсэх (`grep -o '](0[0-9]-[a-z-]*\.md)' README.md`).
- Push-ийн дараа GitHub Pages хуудас шинэчлэгдсэн эсэхийг харах; локал verify хэрэггүй.
