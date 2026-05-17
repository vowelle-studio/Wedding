# Андрій & Анна — весільне запрошення

Статичний мобільний сайт-запрошення (`index.html`).

## Публікація

1. Ініціалізуйте репозиторій: `git init`
2. Додайте файли: `git add .`
3. Закомітьте: `git commit -m "Wedding invitation site"`
4. Завантажте на GitHub і увімкніть **GitHub Pages** (гілка `main`, папка `/` root).

Або будь-який статичний хостинг: скопіюйте всю папку проєкту на сервер.

## Превʼю посилання (Telegram, Instagram, Viber)

У `index.html` у `<head>` є теги **Open Graph** — саме вони показують картинку конверта при надсиланні посилання.

1. Після публікації сайту замініть у `index.html` усі **`YOUR-SITE-URL`** на вашу реальну HTTPS-адресу (без слеша в кінці), наприклад:  
   `https://username.github.io/Wedding`
2. Картинка превʼю: `assets/og-preview.jpg` (обрізаний конверт 1200×630).
3. Перевірка:
   - [Telegram Instant View / preview](https://t.me/webpagebot) — надішліть боту посилання на сайт
   - [Facebook Sharing Debugger](https://developers.facebook.com/tools/debug/) — для Instagram теж використовує OG
4. Якщо картинка не оновилась — месенджери кешують превʼю; скиньте кеш у Sharing Debugger або змініть URL (наприклад додайте `?v=2`).

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
