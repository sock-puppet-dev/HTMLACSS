# HTML & CSS: Design and Build Websites - шпаргалка

Эта шпаргалка сделана по книге Jon Duckett, но с поправками на современную HTML/CSS-практику. Книга 2011 года отлично объясняет базу: структуру документа, смысл тегов, каскад, блочную модель, формы и визуальное мышление. Но часть приемов уже устарела: Flash, верстка на `float`, фиксированные сетки, XHTML-слэш в пустых тегах, старые HTML5-полифиллы для IE.

Главная мысль: HTML описывает смысл и структуру, CSS описывает внешний вид, JavaScript добавляет поведение.

## Как учить

1. Открывай пример из главы.
2. Переписывай код руками, не копируй.
3. Меняй 2-3 свойства и смотри, что ломается.
4. Записывай в этот файл: тег/свойство, зачем оно, минимальный пример, современная заметка.
5. После главы делай мини-проект на 20-40 минут.

## HTML в 2026 году: что учить полностью

HTML сегодня - не просто набор тегов. Это язык структуры документа, семантики, форм, встроенных медиа, доступности, метаданных, базовой безопасности и связей страницы с браузером, поиском, скринридерами и JavaScript.

Главный источник истины - WHATWG HTML Living Standard. Для ежедневного обучения удобнее MDN: там проще объяснения, примеры, совместимость и пометки об устаревших возможностях.

Важно не пытаться заучить весь стандарт подряд. Правильная стратегия:

1. Выучить скелет документа.
2. Понимать семантические элементы.
3. Уметь размечать текст, ссылки, изображения, таблицы и формы.
4. Знать доступность HTML: `alt`, `label`, заголовки, landmarks, фокус.
5. Использовать современные встроенные элементы: `details`, `summary`, `dialog`, `template`, `slot`, `picture`, `source`.
6. Понимать, что не нужно использовать: Flash, `frameset`, `center`, `font`, layout-таблицы, presentational attributes.
7. Проверять себя валидатором и браузерными DevTools.

Навигатор раздела:

- документ и `head`;
- категории элементов;
- семантика страницы;
- заголовки;
- текстовая семантика;
- ссылки;
- изображения;
- видео и аудио;
- таблицы;
- формы;
- нативная интерактивность;
- templates и Web Components;
- global attributes;
- ARIA и доступность;
- SEO и метаданные;
- безопасность;
- производительность;
- валидация;
- устаревшие практики;
- учебный план;
- финальный чеклист.

### 1. Документ и head

Минимум для современной страницы:

```html
<!doctype html>
<html lang="ru">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Понятный заголовок страницы</title>
    <meta name="description" content="Краткое описание страницы.">
    <link rel="stylesheet" href="/css/styles.css">
  </head>
  <body>
    <main>
      <h1>Главная тема страницы</h1>
    </main>
  </body>
</html>
```

Что знать:

- `doctype` должен быть `<!doctype html>`.
- `html lang` обязателен как привычка. Он помогает доступности, поиску и автопереводу.
- `charset="utf-8"` ставь в начале `head`.
- `viewport` нужен для мобильной адаптивности.
- `title` должен быть уникальным и понятным.
- `description` не гарантирует сниппет в поиске, но остается полезным.
- CSS подключай через `<link rel="stylesheet">`.
- JavaScript обычно подключают в конце `body` или через `defer` в `head`.

Скрипт:

```html
<script src="/js/app.js" defer></script>
```

- `defer` загружает скрипт параллельно и выполняет после разбора HTML.
- `async` подходит для независимых скриптов, например аналитики.
- `type="module"` включает ES modules и по умолчанию ведет себя как `defer`.

```html
<script type="module" src="/js/app.js"></script>
```

### 2. Категории HTML-элементов

HTML проще понимать не как длинный список, а как группы:

- Document metadata: `title`, `meta`, `link`, `style`, `base`.
- Sectioning and landmarks: `header`, `nav`, `main`, `section`, `article`, `aside`, `footer`.
- Text content: `p`, `h1`-`h6`, `ul`, `ol`, `li`, `dl`, `dt`, `dd`, `blockquote`, `figure`, `figcaption`, `hr`, `pre`.
- Inline text semantics: `a`, `em`, `strong`, `small`, `s`, `cite`, `q`, `dfn`, `abbr`, `time`, `code`, `kbd`, `samp`, `var`, `sub`, `sup`, `mark`, `span`, `br`, `wbr`.
- Images and media: `img`, `picture`, `source`, `audio`, `video`, `track`.
- Embedded content: `iframe`, `embed`, `object`, `canvas`, `svg`.
- Tables: `table`, `caption`, `thead`, `tbody`, `tfoot`, `tr`, `th`, `td`, `colgroup`, `col`.
- Forms: `form`, `label`, `input`, `button`, `select`, `option`, `textarea`, `fieldset`, `legend`, `datalist`, `output`, `progress`, `meter`.
- Interactive: `details`, `summary`, `dialog`.
- Web Components and templates: `template`, `slot`.

### 3. Семантика страницы

Семантика отвечает на вопрос: "что это за часть документа?"

```html
<header>
  <a href="/">Brand</a>
  <nav aria-label="Основная навигация">
    <a href="/articles">Статьи</a>
    <a href="/contacts">Контакты</a>
  </nav>
</header>

<main>
  <article>
    <h1>Как работает HTML</h1>
    <p>HTML описывает структуру и смысл содержимого.</p>
  </article>
</main>

<footer>
  <p>&copy; 2026</p>
</footer>
```

Как выбирать:

- `main` - главное содержимое страницы. Обычно один раз.
- `header` - вводная область страницы или раздела.
- `footer` - нижняя область страницы или раздела.
- `nav` - крупная навигация.
- `article` - самостоятельная единица контента: статья, пост, новость, карточка товара, комментарий.
- `section` - тематический раздел, обычно с заголовком.
- `aside` - дополнительный контент: сайдбар, related links, примечания.
- `div` - нейтральный контейнер, когда смысла нет.
- `span` - нейтральный inline-контейнер, когда смысла нет.

Правило: сначала ищи смысловой тег. Если подходящего нет, бери `div` или `span`.

### 4. Заголовки и структура документа

```html
<main>
  <h1>HTML</h1>

  <section>
    <h2>Семантика</h2>
    <p>...</p>
  </section>

  <section>
    <h2>Формы</h2>

    <section>
      <h3>Label</h3>
      <p>...</p>
    </section>
  </section>
</main>
```

Хорошая практика:

- Один главный `h1` на страницу - надежная учебная привычка.
- Не выбирай `h3` только потому, что он визуально меньше. Размер делает CSS.
- Не перескакивай с `h1` сразу на `h4` без причины.
- У `section` обычно должен быть заголовок.
- Логотип в `header` не обязан быть `h1` на каждой странице.

### 5. Текстовая семантика

Используй элементы по смыслу:

```html
<p>
  <strong>Важно:</strong> не используй HTML для оформления.
  Для визуального стиля нужен <em>CSS</em>.
</p>

<p>
  Спецификация <abbr title="HyperText Markup Language">HTML</abbr>
  развивается как Living Standard.
</p>

<p>
  Опубликовано <time datetime="2026-04-30">30 апреля 2026</time>.
</p>

<pre><code>npm run build</code></pre>
```

Часто нужные элементы:

- `strong` - важность.
- `em` - смысловое ударение.
- `b` - визуальное выделение без важности.
- `i` - термин, название, голос, настроение.
- `small` - мелкое примечание, юридический текст.
- `s` - информация больше не актуальна.
- `mark` - подсветка релевантного фрагмента.
- `code` - фрагмент кода.
- `pre` - предформатированный блок.
- `kbd` - пользовательский ввод.
- `time` - дата/время в машинно-читаемом формате.
- `abbr` - аббревиатура.

### 6. Ссылки и URL

```html
<a href="/about">О проекте</a>
<a href="#faq">Перейти к FAQ</a>
<a href="mailto:name@example.com">name@example.com</a>
<a href="tel:+380441234567">+38 044 123 45 67</a>
<a href="https://example.com" target="_blank" rel="noopener">Внешний сайт</a>
```

Правила:

- Текст ссылки должен быть понятен вне контекста.
- Не пиши "тут", "сюда", "click here" как единственный текст ссылки.
- Если открываешь новую вкладку через `target="_blank"`, добавляй `rel="noopener"`.
- Для скачивания можно использовать `download`, но браузер может ограничить его для внешних URL.

```html
<a href="/files/report.pdf" download>Скачать отчет PDF</a>
```

### 7. Изображения

Обычное изображение:

```html
<img
  src="/images/profile.jpg"
  alt="Анна читает книгу у окна"
  width="800"
  height="600"
  loading="lazy">
```

Правила `alt`:

- Если изображение несет смысл, опиши смысл.
- Если изображение декоративное, используй `alt=""`.
- Не начинай alt с "изображение" или "картинка", скринридер и так понимает элемент.
- Если картинка-ссылка, `alt` должен описывать действие/назначение ссылки.

Responsive images:

```html
<img
  src="/images/card-800.jpg"
  srcset="/images/card-400.jpg 400w, /images/card-800.jpg 800w, /images/card-1200.jpg 1200w"
  sizes="(max-width: 600px) 100vw, 600px"
  alt="Карточка товара на столе"
  width="800"
  height="600">
```

Art direction:

```html
<picture>
  <source media="(max-width: 600px)" srcset="/images/hero-mobile.jpg">
  <source media="(min-width: 601px)" srcset="/images/hero-desktop.jpg">
  <img src="/images/hero-desktop.jpg" alt="Команда работает за ноутбуками">
</picture>
```

Производительность:

- Ставь `width` и `height`.
- Для изображений ниже первого экрана используй `loading="lazy"`.
- Для главного hero-изображения обычно не ставь lazy.
- Для важного изображения можно использовать `fetchpriority="high"`, но осторожно.
- Контентные изображения - через `img`/`picture`, декоративные - через CSS background.

### 8. Видео, аудио и субтитры

```html
<video controls width="800" poster="/images/poster.jpg">
  <source src="/video/lesson.webm" type="video/webm">
  <source src="/video/lesson.mp4" type="video/mp4">
  <track kind="subtitles" src="/captions/lesson-ru.vtt" srclang="ru" label="Русский">
  Ваш браузер не поддерживает видео.
</video>
```

```html
<audio controls>
  <source src="/audio/interview.mp3" type="audio/mpeg">
  Ваш браузер не поддерживает аудио.
</audio>
```

Правила:

- Не включай видео/аудио автоматически со звуком.
- Для обучающих видео добавляй субтитры через `track`.
- `autoplay` в современных браузерах обычно работает только с `muted`.
- Для фонового видео добавляй доступную альтернативу и не мешай чтению.

### 9. Таблицы

Таблицы - только для данных.

```html
<table>
  <caption>Сравнение тарифов</caption>
  <thead>
    <tr>
      <th scope="col">Тариф</th>
      <th scope="col">Цена</th>
      <th scope="col">Проекты</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Basic</th>
      <td>$9</td>
      <td>3</td>
    </tr>
  </tbody>
</table>
```

Учить:

- `caption` - название таблицы.
- `th` - заголовочная ячейка.
- `scope="col"` и `scope="row"` помогают доступности.
- `thead`, `tbody`, `tfoot` структурируют большие таблицы.
- `colspan` и `rowspan` усложняют доступность, используй только когда нужно.

Не использовать:

- Таблицы для layout.
- `border`, `cellpadding`, `cellspacing` как HTML-оформление. Это CSS.

### 10. Формы

Формы - один из самых важных разделов HTML.

```html
<form action="/signup" method="post">
  <div>
    <label for="email">Email</label>
    <input
      id="email"
      name="email"
      type="email"
      autocomplete="email"
      required>
  </div>

  <div>
    <label for="password">Пароль</label>
    <input
      id="password"
      name="password"
      type="password"
      autocomplete="new-password"
      minlength="8"
      required>
  </div>

  <button type="submit">Создать аккаунт</button>
</form>
```

Что обязательно знать:

- `label` связывается с полем через `for` и `id`.
- У отправляемых полей должен быть `name`.
- `required`, `minlength`, `maxlength`, `min`, `max`, `step`, `pattern` дают базовую HTML-валидацию.
- `autocomplete` помогает пользователю и менеджерам паролей.
- `placeholder` не заменяет `label`.
- Проверка на клиенте не заменяет проверку на сервере.

Типы `input`, которые важно знать:

- `text`
- `email`
- `password`
- `search`
- `url`
- `tel`
- `number`
- `date`
- `time`
- `datetime-local`
- `checkbox`
- `radio`
- `file`
- `hidden`
- `range`
- `color`
- `submit`

Мобильная клавиатура:

```html
<label for="code">Код подтверждения</label>
<input
  id="code"
  name="code"
  inputmode="numeric"
  autocomplete="one-time-code">
```

Дополнительные элементы:

```html
<fieldset>
  <legend>Способ связи</legend>

  <label>
    <input type="radio" name="contact" value="email">
    Email
  </label>

  <label>
    <input type="radio" name="contact" value="phone">
    Телефон
  </label>
</fieldset>
```

```html
<label for="city">Город</label>
<input id="city" name="city" list="cities">
<datalist id="cities">
  <option value="Киев">
  <option value="Львов">
  <option value="Одесса">
</datalist>
```

```html
<label for="message">Сообщение</label>
<textarea id="message" name="message" rows="5"></textarea>
```

Кнопки:

```html
<button type="button">Открыть меню</button>
<button type="submit">Отправить</button>
<button type="reset">Сбросить</button>
```

Всегда явно ставь `type` у `button`, особенно внутри формы.

### 11. Нативная интерактивность

Раскрывающийся блок:

```html
<details>
  <summary>Что такое HTML?</summary>
  <p>HTML описывает структуру и смысл веб-страницы.</p>
</details>
```

Модальное окно:

```html
<dialog id="confirm-dialog">
  <form method="dialog">
    <p>Удалить файл?</p>
    <button value="cancel">Отмена</button>
    <button value="confirm">Удалить</button>
  </form>
</dialog>
```

Для открытия `dialog` нужен JavaScript:

```js
document.querySelector("#confirm-dialog").showModal();
```

Popover:

```html
<button popovertarget="menu-popover">Меню</button>

<div id="menu-popover" popover>
  <a href="/profile">Профиль</a>
  <a href="/settings">Настройки</a>
</div>
```

Что знать:

- `details`/`summary` подходят для FAQ и простого раскрытия.
- `dialog` подходит для модальных окон, если нужно именно модальное поведение.
- `popover` подходит для легких всплывающих панелей, меню, подсказок.
- `inert` делает область неактивной для фокуса и взаимодействия.

```html
<main inert>
  Контент временно неактивен.
</main>
```

### 12. Шаблоны и Web Components

`template` хранит HTML, который не рендерится сразу:

```html
<template id="card-template">
  <article class="card">
    <h2></h2>
    <p></p>
  </article>
</template>
```

`slot` используется внутри Web Components:

```html
<user-card>
  <span slot="name">Анна</span>
</user-card>
```

На старте достаточно понимать:

- `template` - безопасный контейнер для будущего DOM.
- `slot` - место, куда компонент принимает внешний контент.
- Web Components состоят из Custom Elements, Shadow DOM и templates.

### 13. Global attributes

Глобальные атрибуты можно использовать на большинстве HTML-элементов.

Самые важные:

- `id` - уникальный идентификатор.
- `class` - классы для CSS/JS.
- `lang` - язык элемента.
- `title` - дополнительная подсказка, не полагайся на него для важной информации.
- `hidden` - скрывает элемент.
- `inert` - отключает взаимодействие с областью.
- `tabindex` - управляет фокусом, использовать осторожно.
- `contenteditable` - редактируемый пользователем контент.
- `spellcheck` - проверка орфографии.
- `translate` - можно ли переводить текст.
- `dir` - направление текста: `ltr`, `rtl`, `auto`.
- `data-*` - свои данные для JS.
- `role` и `aria-*` - доступность, когда нативной семантики не хватает.

Пример `data-*`:

```html
<button data-action="save" data-id="42">Сохранить</button>
```

Правило для `tabindex`:

- `tabindex="0"` добавляет элемент в естественный порядок фокуса.
- `tabindex="-1"` позволяет фокусировать программно, но убирает из Tab-порядка.
- Положительные значения вроде `tabindex="5"` почти всегда плохая идея.

### 14. ARIA и доступность

Главное правило ARIA: если можно использовать нативный HTML-элемент или атрибут с нужной семантикой, используй его.

Лучше:

```html
<button type="button">Открыть</button>
```

Хуже:

```html
<div role="button" tabindex="0">Открыть</div>
```

Базовая доступность HTML:

- У страницы понятный `title`.
- У `html` указан `lang`.
- Заголовки образуют логичную структуру.
- Интерактивные элементы доступны с клавиатуры.
- Кнопки сделаны через `button`, ссылки через `a href`.
- У изображений правильный `alt`.
- У полей формы есть `label`.
- Ошибки формы связаны с полями текстом.
- Не передавай смысл только цветом.
- Не убирай видимый `focus`.

ARIA нужна для сложных компонентов:

```html
<button
  type="button"
  aria-expanded="false"
  aria-controls="main-menu">
  Меню
</button>

<nav id="main-menu" aria-label="Основная навигация" hidden>
  ...
</nav>
```

Но ARIA не добавляет поведение сама. Если написал `aria-expanded`, JavaScript должен менять значение при открытии/закрытии.

### 15. SEO и социальные метаданные

Базовый `head`:

```html
<title>HTML шпаргалка 2026</title>
<meta name="description" content="Современная шпаргалка по HTML для изучения в 2026 году.">
<link rel="canonical" href="https://example.com/html-guide">
```

Open Graph:

```html
<meta property="og:title" content="HTML шпаргалка 2026">
<meta property="og:description" content="Современная HTML-карта для обучения.">
<meta property="og:image" content="https://example.com/cover.jpg">
<meta property="og:url" content="https://example.com/html-guide">
<meta property="og:type" content="article">
```

Structured data обычно добавляют через JSON-LD:

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "HTML шпаргалка 2026"
}
</script>
```

Важно:

- SEO начинается с нормальной структуры: `title`, `h1`, понятный текст, ссылки, alt.
- Не делай несколько страниц с одинаковым `title`.
- Не прячь важный текст только в изображениях.
- Structured data не заменяет видимый контент.

### 16. Безопасность HTML

Главные риски:

- XSS через вставку непроверенного HTML.
- Небезопасные `iframe`.
- Reverse tabnabbing у ссылок с `target="_blank"` без `rel="noopener"`.
- Утечка referrer-информации.

Правила:

```html
<a href="https://external.example" target="_blank" rel="noopener noreferrer">
  Внешняя ссылка
</a>
```

```html
<iframe
  src="https://example.com/embed"
  title="Встроенная карта"
  sandbox
  loading="lazy">
</iframe>
```

- Не вставляй пользовательский HTML без очистки.
- Для `iframe` добавляй `title`.
- Для недоверенного `iframe` используй `sandbox` и выдавай только нужные разрешения.
- Не храни секреты в HTML.
- Не полагайся на скрытые поля формы как на защиту.

### 17. Производительность HTML

HTML влияет на скорость загрузки сильнее, чем кажется.

Полезные привычки:

- Пиши простой HTML, не создавай лишнюю вложенность.
- Ставь размеры изображениям: `width`, `height`.
- Используй `loading="lazy"` для изображений и iframe ниже первого экрана.
- Главный CSS подключай рано.
- Скрипты подключай с `defer`, если они не должны блокировать парсинг.
- Используй `preload` только для действительно критичных ресурсов.
- Используй `preconnect` только для важных внешних доменов.

```html
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link rel="preload" href="/fonts/inter.woff2" as="font" type="font/woff2" crossorigin>
```

Не надо ставить `preload` на все подряд. Это может ухудшить загрузку.

### 18. Валидация и качество

Проверяй HTML:

- Nu Html Checker: https://validator.w3.org/nu/
- DevTools в браузере.
- Lighthouse для доступности, SEO и производительности.
- axe DevTools или похожие инструменты для accessibility.

Что валидатор помогает ловить:

- незакрытые теги;
- неправильную вложенность;
- дублирующиеся `id`;
- устаревшие элементы/атрибуты;
- ошибки в таблицах и формах;
- отсутствие нужных атрибутов.

### 19. Что не учить как современную практику

Устарело или не нужно в новых проектах:

- `font`, `center`, `big`, `strike`.
- `frameset`, `frame`, `noframes`.
- `acronym`.
- `align`, `bgcolor`, `border`, `cellpadding`, `cellspacing` как HTML-оформление.
- Flash: `object`/`embed` для Flash-плееров.
- Таблицы для сетки страницы.
- Layout через прозрачные GIF, spacer images.
- XHTML-слэш как необходимость: `<br />`, `<img />`.
- `type="text/css"` для stylesheet как обязательный атрибут.
- `type="text/javascript"` для обычного script как обязательный атрибут.

Можно знать исторически, но не строить на этом новые проекты.

### 20. Учебный план HTML на 2026

Неделя 1: основа документа

- `doctype`, `html`, `head`, `body`.
- `title`, `meta`, `link`.
- Заголовки, абзацы, списки, ссылки.
- Практика: личная страница.

Неделя 2: семантика

- `header`, `nav`, `main`, `section`, `article`, `aside`, `footer`.
- `figure`, `figcaption`, `time`.
- Практика: статья блога.

Неделя 3: медиа и таблицы

- `img`, `picture`, `srcset`, `sizes`, `loading`.
- `audio`, `video`, `track`.
- `table`, `caption`, `th`, `scope`.
- Практика: страница рецепта или обзора товара.

Неделя 4: формы

- `form`, `label`, `input`, `textarea`, `select`, `button`.
- Валидация: `required`, `minlength`, `pattern`, `type`.
- `autocomplete`, `inputmode`, `fieldset`, `legend`.
- Практика: регистрация + обратная связь.

Неделя 5: доступность и интерактивность

- клавиатура, focus, alt, labels, landmarks.
- `details`, `summary`, `dialog`, `popover`.
- базовая ARIA: `aria-label`, `aria-expanded`, `aria-controls`.
- Практика: FAQ, модальное окно, меню.

Неделя 6: качество

- SEO-метаданные.
- Open Graph.
- Валидация HTML.
- Lighthouse/a11y проверка.
- Практика: закончить мини-сайт из 3-5 страниц.

### 21. Финальный HTML-чеклист

Перед тем как считать страницу готовой:

- Есть `<!doctype html>`.
- У `html` есть правильный `lang`.
- Есть `meta charset`.
- Есть `meta viewport`.
- Есть уникальный `title`.
- Есть понятный `meta description`, если страница публичная.
- Есть один основной `main`.
- Есть логичная структура заголовков.
- Ссылки имеют понятный текст.
- `a` используется для переходов, `button` для действий.
- Все важные изображения имеют полезный `alt`.
- Декоративные изображения имеют `alt=""`.
- У изображений есть `width` и `height`, когда размеры известны.
- Формы имеют `label`.
- У отправляемых полей есть `name`.
- Ошибки формы понятны текстом.
- Таблицы используются только для данных.
- У таблиц есть `caption`, если название нужно пользователю.
- Интерактивные элементы доступны с клавиатуры.
- Видимый focus не удален.
- `iframe` имеет `title`.
- Внешние `_blank` ссылки имеют `rel="noopener"`.
- HTML проходит Nu Html Checker без серьезных ошибок.

## Современный HTML-шаблон

```html
<!doctype html>
<html lang="ru">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Название страницы</title>
    <link rel="stylesheet" href="css/styles.css">
  </head>
  <body>
    <header>
      <h1>Главный заголовок</h1>
    </header>

    <main>
      <p>Основное содержимое страницы.</p>
    </main>
  </body>
</html>
```

Важно:

- `<!doctype html>` включает современный режим браузера.
- `lang="ru"` помогает поиску, переводчикам и скринридерам.
- `meta charset="utf-8"` задает кодировку.
- `meta viewport` нужен для нормальной адаптивности на телефонах.
- `type="text/css"` у `<link>` сегодня обычно не пишут.
- В HTML пустые элементы пишут так: `<br>`, `<hr>`, `<img>`, `<input>`, `<meta>`, `<link>`. XHTML-стиль `<br />` из книги не нужен.










## Глава 1. Structure

HTML-документ состоит из элементов. Элемент обычно имеет открывающий тег, содержимое и закрывающий тег.

```html
<p>Это абзац.</p>
```

База:

- `<html>` - корневой элемент страницы.
- `<head>` - служебная информация для браузера, поисковиков и вкладки.
- `<title>` - название страницы во вкладке браузера.
- `<body>` - видимое содержимое страницы.
- `<h1>` ... `<h6>` - заголовки от главного к менее важным.
- `<p>` - абзац.

Атрибуты:

```html
<p lang="en-US">Paragraph in English.</p>
```

- `lang` - имя атрибута.
- `"en-US"` - значение атрибута.
- `lang="en-US"` - атрибут целиком.

Правило: атрибуты пишутся в открывающем теге и уточняют элемент.

Практика: создай страницу с `h1`, двумя `h2`, несколькими `p` и разными языками через `lang`.

## Глава 2. Text

Заголовки:

```html
<h1>Главная тема страницы</h1>
<h2>Раздел</h2>
<h3>Подраздел</h3>
```

Используй заголовки по смыслу, а не ради размера. Размер меняется CSS.

Текстовые элементы:

- `<b>` - визуально жирный текст без дополнительной важности.
- `<strong>` - важный текст.
- `<i>` - визуально выделенный текст, например термин или название.
- `<em>` - смысловое ударение.
- `<sup>` - верхний индекс: `10<sup>2</sup>`.
- `<sub>` - нижний индекс: `H<sub>2</sub>O`.
- `<br>` - перенос строки внутри текста, не для отступов.
- `<hr>` - тематический разделитель.
- `<blockquote>` - длинная цитата.
- `<q>` - короткая встроенная цитата.
- `<abbr>` - аббревиатура.
- `<cite>` - название источника/произведения.
- `<dfn>` - первое определение термина.
- `<address>` - контактная информация автора или владельца страницы/раздела.
- `<ins>` - добавленный текст.
- `<del>` - удаленный текст.
- `<s>` - больше не актуальный текст.

Устарело:

- `<acronym>` не используй. Сегодня достаточно `<abbr>`.

Пример:

```html
<p>
  <strong>Важно:</strong> HTML отвечает за смысл,
  а <em>CSS</em> отвечает за внешний вид.
</p>
```

Практика: возьми текст статьи и разметь его семантически: заголовки, абзацы, цитату, аббревиатуру, важное предупреждение.

## Глава 3. Lists

Списки:

```html
<ul>
  <li>Молоко</li>
  <li>Хлеб</li>
</ul>

<ol>
  <li>Открыть файл</li>
  <li>Запустить браузер</li>
</ol>

<dl>
  <dt>HTML</dt>
  <dd>Язык разметки для структуры веб-страниц.</dd>
</dl>
```

- `<ul>` - unordered list, порядок не важен.
- `<ol>` - ordered list, порядок важен.
- `<li>` - list item.
- `<dl>` - description list.
- `<dt>` - термин.
- `<dd>` - описание.

Практика: сделай страницу рецепта: ингредиенты через `ul`, шаги через `ol`, термины через `dl`.

## Глава 4. Links

Ссылка:

```html
<a href="https://developer.mozilla.org/">MDN</a>
```

Типы ссылок:

```html
<a href="about.html">Внутренняя страница</a>
<a href="mailto:name@example.com">Email</a>
<a href="#contacts">К разделу на странице</a>
<a href="https://example.com" target="_blank" rel="noopener">В новой вкладке</a>
```

Современно:

- Текст ссылки должен объяснять, куда ведет ссылка. Плохо: "click here". Лучше: "открыть документацию MDN".
- Для внешних ссылок в новой вкладке добавляй `rel="noopener"`.
- Не злоупотребляй `target="_blank"`: пользователь сам может открыть ссылку в новой вкладке.

Практика: сделай мини-сайт из 3 страниц и навигацию между ними.

## Глава 5. Images

Базовое изображение:

```html
<img src="images/cat.jpg" alt="Рыжий кот лежит на окне" width="600" height="400">
```

Важно:

- `src` - путь к картинке.
- `alt` - текстовая альтернатива. Если картинка декоративная, можно `alt=""`.
- `width` и `height` помогают браузеру заранее зарезервировать место и уменьшить скачки layout.
- Не используй HTML-атрибуты `align`. Выравнивание делается через CSS.

Подпись к изображению:

```html
<figure>
  <img src="images/print-01.jpg" alt="Ботаническая иллюстрация Helianthus">
  <figcaption>Helianthus</figcaption>
</figure>
```

Современно:

```html
<img
  src="images/photo-800.jpg"
  srcset="images/photo-400.jpg 400w, images/photo-800.jpg 800w"
  sizes="(max-width: 600px) 400px, 800px"
  alt="Описание изображения"
  loading="lazy">
```

Практика: сделай галерею из 6 изображений с `figure`, `figcaption`, осмысленным `alt` и CSS-выравниванием.

## Глава 6. Tables

Таблицы нужны для табличных данных, не для макета страницы.

```html
<table>
  <caption>Расписание занятий</caption>
  <thead>
    <tr>
      <th scope="col">День</th>
      <th scope="col">Тема</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Понедельник</th>
      <td>HTML</td>
    </tr>
  </tbody>
</table>
```

Элементы:

- `<table>` - таблица.
- `<caption>` - заголовок таблицы.
- `<tr>` - строка.
- `<th>` - ячейка-заголовок.
- `<td>` - обычная ячейка.
- `<thead>`, `<tbody>`, `<tfoot>` - смысловые группы строк.
- `colspan` - объединить столбцы.
- `rowspan` - объединить строки.
- `scope` - помогает связать заголовок с ячейками.

Практика: сверстай таблицу расходов за неделю.

## Глава 7. Forms

Форма:

```html
<form action="/subscribe" method="post">
  <label for="email">Email</label>
  <input id="email" name="email" type="email" required>

  <button type="submit">Подписаться</button>
</form>
```

Главное:

- `action` - куда отправлять данные.
- `method="get"` - данные в URL, подходит для поиска/фильтров.
- `method="post"` - данные в теле запроса, подходит для форм отправки.
- `name` нужен, чтобы поле попало в отправленные данные.
- `label` должен быть связан с полем через `for` и `id`.

Частые поля:

- `type="text"` - обычный текст.
- `type="password"` - пароль.
- `type="email"` - email с базовой проверкой.
- `type="url"` - URL с базовой проверкой.
- `type="search"` - поиск.
- `type="date"` - дата.
- `type="file"` - файл.
- `textarea` - многострочный текст.
- `select` и `option` - выпадающий список.
- `radio` - один вариант из группы.
- `checkbox` - независимый выбор.

Группировка:

```html
<fieldset>
  <legend>Способ связи</legend>

  <label>
    <input type="radio" name="contact" value="email">
    Email
  </label>
</fieldset>
```

Современно:

- Используй `<button>`, а не картинку-кнопку, если нет особой причины.
- HTML-валидация полезна, но проверку на сервере она не заменяет.
- `placeholder` не заменяет `label`.

Практика: сделай форму регистрации с email, паролем, датой рождения, чекбоксом согласия и понятными label.

## Глава 8. Extra Markup

Комментарии:

```html
<!-- Временная заметка для разработчика -->
```

`id` и `class`:

```html
<section id="pricing" class="section section-pricing">
  ...
</section>
```

- `id` уникален на странице. Подходит для якорей и точечных связей.
- `class` можно повторять. Это основной способ выбирать элементы в CSS.

Блочные и строчные элементы:

- Блочные обычно занимают всю доступную ширину: `div`, `p`, `section`, `article`.
- Строчные занимают ширину содержимого: `span`, `a`, `strong`, `em`.

`div` и `span`:

- `<div>` - нейтральный блочный контейнер.
- `<span>` - нейтральный строчный контейнер.
- Если есть смысловой тег, используй его вместо `div`.

`iframe`:

```html
<iframe
  src="https://example.com"
  title="Описание встроенного содержимого"
  loading="lazy">
</iframe>
```

Важно: у `iframe` всегда должен быть понятный `title`.

Meta:

```html
<meta name="description" content="Краткое описание страницы.">
```

Практика: перепиши страницу, заменяя лишние `div` на `header`, `main`, `section`, `article`, `nav`, `footer`, где это уместно.

## Глава 9. Flash, Video & Audio

Самая устаревшая глава.

Не учить как рабочую технологию:

- Flash movie.
- Flash video.
- Flash MP3 player.
- `<object>`/`embed` для Flash.

Сегодня использовать:

```html
<video controls width="640" poster="images/poster.jpg">
  <source src="video/movie.webm" type="video/webm">
  <source src="video/movie.mp4" type="video/mp4">
  Ваш браузер не поддерживает видео.
</video>

<audio controls>
  <source src="audio/song.mp3" type="audio/mpeg">
  Ваш браузер не поддерживает аудио.
</audio>
```

Важно:

- `controls` включает стандартные элементы управления.
- `poster` задает картинку до старта видео.
- Несколько `source` помогают браузеру выбрать поддерживаемый формат.
- Не включай автозапуск со звуком.

Практика: сделай страницу с видео, аудио и текстовой альтернативой.

## Глава 10. Introducing CSS

CSS-правило:

```css
p {
  color: #333;
  font-size: 16px;
}
```

- `p` - selector.
- `color` - property.
- `#333` - value.
- `color: #333;` - declaration.

Подключение CSS:

```html
<link rel="stylesheet" href="css/styles.css">
```

Приоритет:

1. Inline style: `style=""`, избегай в обычной верстке.
2. `id`-селекторы.
3. `class`, атрибуты, псевдоклассы.
4. теги и псевдоэлементы.
5. порядок в файле: при равном весе побеждает правило ниже.

Хорошая привычка:

- Пиши CSS во внешнем файле.
- Используй классы для стилизации.
- Не повышай специфичность без нужды.
- Не используй `!important`, пока не понимаешь, почему он понадобился.

Практика: возьми HTML без стилей и оформи его только через внешний CSS.

## Глава 11. Color

Способы записи цвета:

```css
.box {
  color: #222;
  background-color: rgb(245, 245, 245);
  border-color: hsl(210 20% 80%);
}
```

Популярно сегодня:

- HEX: `#ffffff`, `#fff`.
- RGB/RGBA: `rgb(255 255 255)`, `rgb(0 0 0 / 0.6)`.
- HSL: `hsl(210 80% 50%)`, удобно менять оттенок/насыщенность/светлоту.

Контраст:

- Текст должен хорошо читаться на фоне.
- Не передавай смысл только цветом. Добавляй текст, иконку или форму.

Практика: сделай палитру сайта: фон, основной текст, вторичный текст, акцент, граница, состояние ошибки.

## Глава 12. Text

Базовые свойства:

```css
body {
  font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  font-size: 16px;
  line-height: 1.5;
}

h1 {
  font-size: 2rem;
  font-weight: 700;
}
```

Частые свойства:

- `font-family` - шрифт.
- `font-size` - размер.
- `font-weight` - насыщенность.
- `font-style` - стиль, например `italic`.
- `line-height` - высота строки.
- `text-align` - выравнивание текста.
- `text-transform` - регистр.
- `text-decoration` - подчеркивание и другие линии.
- `text-shadow` - тень текста, использовать осторожно.
- `letter-spacing` - расстояние между буквами.
- `word-spacing` - расстояние между словами.

Единицы:

- `rem` - удобно для размеров шрифта и отступов, зависит от корневого размера.
- `em` - зависит от размера шрифта текущего элемента.
- `px` - точный размер, хорош для границ и мелких деталей.

Подключение шрифтов:

```css
@font-face {
  font-family: "MyFont";
  src: url("../fonts/myfont.woff2") format("woff2");
  font-weight: 400;
  font-style: normal;
  font-display: swap;
}
```

Современно:

- Основной веб-формат шрифтов: `woff2`.
- Добавляй `font-display: swap`, чтобы текст быстрее появился.
- Не делай слишком длинные строки. Хороший ориентир: 60-80 символов.

Практика: оформи статью: заголовок, лид, обычные абзацы, цитату, ссылку, список.

## Глава 13. Boxes

Каждый элемент в CSS - прямоугольная коробка.

```css
.card {
  box-sizing: border-box;
  width: 320px;
  padding: 16px;
  border: 1px solid #ddd;
  margin: 24px;
}
```

Box model:

- content - содержимое.
- padding - внутренний отступ.
- border - граница.
- margin - внешний отступ.

Современная база:

```css
*,
*::before,
*::after {
  box-sizing: border-box;
}
```

Свойства:

- `width`, `height`.
- `min-width`, `max-width`.
- `min-height`, `max-height`.
- `overflow`.
- `border`.
- `border-radius`.
- `box-shadow`.
- `display`.
- `visibility`.

Важно:

- `display: none` убирает элемент из layout.
- `visibility: hidden` прячет, но место остается.
- `overflow: auto` добавляет прокрутку, если содержимое не помещается.
- `margin: 0 auto` центрирует блочный элемент с заданной шириной.

Практика: сделай карточку товара с изображением, заголовком, описанием и кнопкой.

## Глава 14. Tables, Lists & Forms

Списки:

```css
ul {
  list-style-type: square;
  list-style-position: outside;
}
```

Таблицы:

```css
table {
  width: 100%;
  border-collapse: collapse;
}

th,
td {
  padding: 0.75rem;
  border-bottom: 1px solid #ddd;
  text-align: left;
}
```

Формы:

```css
input,
select,
textarea,
button {
  font: inherit;
}

input,
select,
textarea {
  width: 100%;
  padding: 0.625rem 0.75rem;
  border: 1px solid #bbb;
  border-radius: 4px;
}

input:focus,
textarea:focus {
  outline: 3px solid rgb(0 120 255 / 0.25);
  border-color: rgb(0 120 255);
}
```

Современно:

- Не убирай `outline` без замены. Фокус нужен для клавиатуры.
- Делай кликабельную область форм достаточно большой.
- Ошибки формы показывай текстом, не только красной рамкой.

Практика: стилизуй форму из главы 7 так, чтобы ее было удобно пройти клавиатурой.

## Глава 15. Layout

Книга много учит layout через `float`, fixed width, liquid layout и старые 960-grid подходы. Это полезно понимать исторически, но современный layout лучше строить через Flexbox и CSS Grid.

Позиционирование:

```css
.badge {
  position: absolute;
  top: 8px;
  right: 8px;
}
```

- `static` - обычное положение.
- `relative` - сдвиг относительно обычного положения; создает контекст для absolute-детей.
- `absolute` - позиционирование относительно ближайшего positioned-родителя.
- `fixed` - относительно окна браузера.
- `sticky` - обычный поток + "прилипание" при скролле.
- `z-index` - порядок наложения, работает в контексте позиционирования/слоев.

Float:

- Сегодня `float` в основном для обтекания изображения текстом.
- Не используй `float` как основной способ сетки.

Flexbox, когда элементы идут в одну ось:

```css
.nav {
  display: flex;
  gap: 1rem;
  align-items: center;
  justify-content: space-between;
}
```

Grid, когда нужны строки и столбцы:

```css
.gallery {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
  gap: 1rem;
}
```

Responsive:

```css
.layout {
  display: grid;
  gap: 1rem;
}

@media (min-width: 768px) {
  .layout {
    grid-template-columns: 2fr 1fr;
  }
}
```

Практика: перепиши один пример из главы 15 с `float` на `flex` или `grid`.

## Глава 16. Images in CSS

Фон:

```css
.hero {
  background-color: #222;
  background-image: url("../images/header.jpg");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
}
```

Свойства:

- `background-image`.
- `background-repeat`.
- `background-position`.
- `background-size`.
- `background-attachment`.
- `background` - shorthand.

Важно:

- Контентные изображения должны быть через `<img>`.
- Декоративные изображения можно делать фоном через CSS.
- Спрайты из книги исторически полезны, но сегодня часто используют SVG-иконки, icon fonts реже, а для картинок - оптимизированные файлы.
- Для адаптивных изображений используй `srcset`, `sizes`, `picture`.

Градиент:

```css
.button {
  background: linear-gradient(180deg, #ffffff, #e9eef5);
}
```

Практика: сделай hero-блок с фоновым изображением, затем проверь читаемость текста поверх него.

## Глава 17. HTML5 Layout

Семантическая структура:

```html
<body>
  <header>
    <nav aria-label="Основная навигация">
      ...
    </nav>
  </header>

  <main>
    <article>
      <h1>Название статьи</h1>
      <p>Текст статьи.</p>
    </article>

    <aside>
      <h2>Похожие материалы</h2>
    </aside>
  </main>

  <footer>
    <p>&copy; 2026</p>
  </footer>
</body>
```

Элементы:

- `<header>` - вводная часть страницы или раздела.
- `<nav>` - блок навигации.
- `<main>` - главное содержимое страницы, обычно один раз.
- `<section>` - тематический раздел, обычно с заголовком.
- `<article>` - самостоятельный материал: статья, пост, карточка новости.
- `<aside>` - дополнительный контент.
- `<footer>` - нижняя часть страницы или раздела.
- `<figure>` и `<figcaption>` - иллюстрация и подпись.

Осторожно с примером из книги:

- `header, section, footer... { display: block; }` был нужен для старых браузеров. Сегодня не нужен.
- `html5shiv` для старого IE не нужен.
- `hgroup` лучше не брать как обязательную привычку. Часто достаточно `h1`/`h2` и обычного `p` для подзаголовка.
- `text-indent: -9999px` для скрытия текста логотипа сейчас лучше заменять аккуратными accessibility-паттернами или нормальным текстом/изображением с `alt`.

Практика: сделай страницу блога с `header`, `nav`, `main`, несколькими `article`, `aside`, `footer`.

## Что устарело в книге

Не использовать в новых проектах:

- Flash и Flash-плееры.
- `<acronym>`.
- HTML-атрибуты для оформления вроде `align`, `bgcolor`, `border` у таблиц.
- Таблицы для layout.
- Основную сетку на `float`.
- Фиксированную 960px-сетку как единственный layout.
- `type="text/css"` как обязательный атрибут у stylesheet.
- `type="text/javascript"` как обязательный атрибут у обычного script.
- XHTML-манеру `/>` как необходимость в HTML.
- IE-specific HTML5 shiv.

Учить как исторический контекст:

- `float` layout.
- CSS sprites.
- reset под старые браузеры.
- старые форматы веб-шрифтов вроде EOT.

Учить обязательно:

- семантика HTML.
- доступные формы.
- box model.
- cascade/specificity/inheritance.
- responsive layout.
- Flexbox.
- CSS Grid.
- media queries.
- responsive images.
- базовая доступность: `alt`, `label`, focus states, структура заголовков.

## Мини-чеклист HTML

- На странице есть `<!doctype html>`.
- У `<html>` есть `lang`.
- В `<head>` есть `charset`, `viewport`, `title`.
- Один главный `h1`.
- Заголовки не перескакивают без причины.
- Ссылки имеют понятный текст.
- Картинки имеют правильный `alt`.
- Поля формы связаны с `label`.
- Таблицы используются для данных, не для сетки.
- Интерактивные элементы доступны с клавиатуры.

## Мини-чеклист CSS

- CSS подключен внешним файлом.
- Есть `box-sizing: border-box`.
- Используются классы, а не чрезмерно сложные селекторы.
- Layout сделан через `flex`/`grid`, если это сетка.
- Есть адаптация под узкие экраны.
- Состояния `:hover`, `:focus`, `:active` продуманы.
- Текст читаемый: нормальный размер, контраст, line-height.
- Нет магических фиксированных высот там, где контент может меняться.

## Как выбирать тег

- Это навигация? `<nav>`.
- Это основное содержимое страницы? `<main>`.
- Это самостоятельная статья/пост/новость? `<article>`.
- Это тематический блок с заголовком? `<section>`.
- Это дополнительная боковая информация? `<aside>`.
- Это изображение с подписью? `<figure>` + `<figcaption>`.
- Это просто контейнер без смысла? `<div>`.
- Это маленький кусок текста без смысла? `<span>`.

## Быстрый словарь

- Element - HTML-элемент: `<p>text</p>`.
- Tag - тег: `<p>` или `</p>`.
- Attribute - атрибут: `href="..."`.
- Selector - CSS-выборка: `.card`.
- Declaration - CSS-объявление: `color: red;`.
- Property - CSS-свойство: `color`.
- Value - значение: `red`.
- Cascade - правила, по которым CSS решает конфликт.
- Specificity - вес селектора.
- Inheritance - наследование CSS-свойств.
- Box model - content, padding, border, margin.
- Normal flow - обычный поток документа.
- Responsive design - дизайн, который адаптируется под размеры экрана.

## Контрольные мини-проекты

1. Личная страница: заголовки, текст, список, картинка, ссылки.
2. Рецепт: `article`, `figure`, `ul`, `ol`, таблица питательности.
3. Форма обратной связи: `label`, разные `input`, `textarea`, `fieldset`.
4. Галерея: `figure`, `figcaption`, CSS Grid, responsive images.
5. Блог: `header`, `nav`, `main`, `article`, `aside`, `footer`.
6. Карточки товаров: Flexbox/Grid, кнопки, состояния `hover` и `focus`.

## Полезные современные источники

- WHATWG HTML Living Standard: https://html.spec.whatwg.org/multipage/
- MDN HTML elements reference: https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements
- MDN global attributes: https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes
- MDN constraint validation: https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Constraint_validation
- MDN dialog element: https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/dialog
- MDN Popover API: https://developer.mozilla.org/en-US/docs/Web/API/Popover_API
- MDN responsive design: https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/CSS_layout/Responsive_Design
- MDN Flexbox: https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Flexible_box_layout/Basic_concepts
- MDN CSS Grid: https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Grid_layout/Basic_concepts
- MDN responsive images: https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Responsive_images
- MDN void elements: https://developer.mozilla.org/en-US/docs/Glossary/Void_element
- Adobe Flash end of life: https://helpx.adobe.com/enterprise/kb/eol-adobe-flash-shockwave-player.html
