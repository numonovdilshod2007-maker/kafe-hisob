# Kafe hisobi

Magazindan kafega berilgan narsalar va kafedan olingan pullarni hisoblab boradigan shaxsiy vebsahifa.

## Joylashtirish (deploy) qadamlari

1. Bu papkani GitHub'ga yangi repository sifatida yuklang (masalan `kafe-hisob` nomi bilan).
2. https://vercel.com ga kiring, "Add New Project" tugmasini bosing.
3. Yaratgan GitHub repositoryingizni tanlang va "Import" qiling.
4. Framework: "Other" qoldiring, boshqa hech narsa o'zgartirmasdan "Deploy" tugmasini bosing.
5. Bir necha soniyadan so'ng sizga doimiy manzil (masalan `kafe-hisob.vercel.app`) beriladi.

Shu manzilni telefoningizning bosh ekraniga qo'shib qo'yishingiz mumkin — shunda u xuddi ilova kabi ochiladi.

## Eslatma

Ma'lumotlar brauzeringizning xotirasida (localStorage) saqlanadi. Ya'ni:
- Shu telefon/kompyuterdagi shu brauzerda doim saqlanib qoladi.
- Boshqa qurilmadan kirsangiz, ma'lumotlar ko'rinmaydi (chunki har bir qurilma o'zining xotirasida saqlaydi).
- Brauzer "tarix va keshni tozalash" qilinsa, ma'lumot o'chib ketishi mumkin.
