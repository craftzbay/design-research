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
