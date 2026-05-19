# Андрій & Анна — весільне запрошення

Статичний мобільний сайт-запрошення (`index.html`).

## Публікація

1. Ініціалізуйте репозиторій: `git init`
2. Додайте файли: `git add .`
3. Закомітьте: `git commit -m "Wedding invitation site"`
4. Завантажте на GitHub і увімкніть **GitHub Pages** (гілка `main`, папка `/` root).

Або будь-який статичний хостинг: скопіюйте всю папку проєкту на сервер.

## Індивідуальні запрошення

Кожен гість відкриває **своє** посилання — у блоці **Hero** з’являється персональне «Дорогі …» / «Дорога …».

| № | Гості | Параметр `?invite=` |
|---|--------|---------------------|
| 1 | Олександр та Каріна | `oleksandr-karyna` |
| 2 | Ірина та Єлизавета | `iryna-yelyzaveta` |
| 3 | Катерина та Віктор | `kateryna-vitya` |
| 4 | Валерій та Анна | `valera-anna` |
| 5 | Олександр та Вікторія | `oleksandr-viktoria` |
| 6 | Ірина та Ігор | `iryna-igor` |
| 7 | Оксана, Анатолій, Юлія, Ольга, Артем та Емілія | `oksana-family` |
| 8 | Тетяна | `tetyana` |
| 9 | Сергій та Анастасія | `serhiy-anastasia` |

**Приклад:** `https://YOUR-SITE-URL/index.html?invite=oleksandr-karyna`  
Також працює номер: `?invite=1` … `?invite=9`.

Сторінка **`invites.html`** — список усіх посилань для копіювання (вкажіть адресу сайту у полі зверху). Не публікуйте її в загальний доступ, якщо не потрібно.

## Превʼю посилання (Telegram, Instagram, Viber)

У `index.html` у `<head>` налаштовано **Open Graph**: картинка `assets/og-preview.jpg` (конверт 1200×630). Шлях відносний — працює на GitHub Pages і будь-якому HTTPS без ручної заміни домену.

**Важливо:** надсилайте **опубліковане HTTPS-посилання** (не `file://` і не локальний файл). Приклад:  
`https://username.github.io/Wedding/index.html?invite=oleksandr-karyna`

Перевірка:
- [@webpagebot](https://t.me/webpagebot) у Telegram — надішліть посилання на сайт
- [Facebook Sharing Debugger](https://developers.facebook.com/tools/debug/) — «Scrape Again», якщо превʼю застаріле

Якщо картинка не оновилась — збільште `?v=` у `og-preview.jpg?v=2` у `<head>`.

## Обовʼязкові файли

| Шлях | Призначення |
|------|-------------|
| `index.html` | Сторінка |
| `Video.mp4` | Інтро та фон hero |
| `pare.png` | Фото пари |
| `assets/envelope.png` | Постер конверта |
| `assets/envelop.mp4` | Відео конверта |
| `assets/icon.png` | Favicon |
| `assets/og-preview.jpg` | Превʼю посилання в месенджерах (Open Graph) |
| `assets/vowelle-studio.png` | Лого студії |
| `assets/calendar-heart.svg` | Іконка календаря |
| `colors/*.png` | Палітра одягу |
| `divider/*.png` | Декоративні розділювачі |

Файли `envelope.png`, `envelop.mp4`, `icon.png`, `colors.png` у **корені** — дублікати; у git не потрібні (див. `.gitignore`). Використовуйте копії в `assets/`.

## Великі відео

`Video.mp4` та `assets/envelop.mp4` важкі для git. За потреби підключіть [Git LFS](https://git-lfs.com/) або хостіть відео на CDN і оновіть `src` у `index.html`.

## Локальний перегляд

Відкрийте `index.html` у браузері або через локальний сервер (наприклад, Live Server у VS Code), щоб коректно працювали відео та `.ics`.

## Поведінка завантаження

Перед стартом інтро-анімації сторінка чекає буферизації відео, постера конверта, ключових зображень і шрифтів (`window.__introMediaReady`). Після тапу по конверту анімація не стартує «порожньою».
