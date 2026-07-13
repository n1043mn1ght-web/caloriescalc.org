# CaloriesCalc.org — Repository Structure Guide

## Текущая проблема
Все файлы лежат в корне репозитория вперемешку.
При 100+ страницах продуктов это станет неуправляемым.

## Целевая структура репозитория

```
caloriescalc.org/
│
├── index.html                        ← TDEE Calculator (главная)
├── bmr-calculator.html
├── macro-calculator.html
├── protein-calculator.html
├── bmi-calculator.html
├── calorie-deficit-calculator.html
├── about.html
├── terms.html
├── privacy.html
├── 404.html                          ← (нужно создать)
│
├── foods/                            ← Калории в продуктах
│   ├── index.html                    ← Каталог всех продуктов (A–Z)
│   ├── banana.html
│   ├── apple.html
│   ├── chicken-breast.html
│   ├── brown-rice.html
│   └── ... (100+ страниц)
│
├── recipes/                          ← Рецепты с КБЖУ
│   ├── index.html                    ← Каталог рецептов
│   ├── chicken-salad.html
│   ├── oatmeal-breakfast.html
│   └── ...
│
├── articles/                         ← SEO статьи
│   ├── how-to-lose-20-pounds.html
│   ├── 1200-calorie-meal-plan.html
│   ├── best-protein-powders.html
│   └── ...
│
├── exercises/                        ← Калории при упражнениях
│   ├── index.html
│   ├── running.html
│   ├── cycling.html
│   └── ...
│
├── meal-planner/                     ← Meal Planner (потом)
│   └── index.html
│
├── assets/                           ← Все статические файлы
│   ├── css/
│   │   ├── main.css                  ← Общие стили (из <style> блоков)
│   │   └── ad-layout.css
│   ├── js/
│   │   └── calculators.js            ← Общий JS (потом)
│   └── img/
│       └── icon.png
│
├── icon.png                          ← Дубль в корне для совместимости
├── site.webmanifest
├── robots.txt
└── sitemap.xml
```

## Как мигрировать поэтапно

### Этап 1 — Сейчас (не трогаем существующие страницы)
Просто создать папки и начать класть новые страницы туда:
- Создать папку `foods/`
- Создать папку `articles/`
- Первые страницы продуктов класть в `foods/`

### Этап 2 — Когда накопится 20+ страниц продуктов
- Создать `foods/index.html` — каталог всех продуктов
- Добавить ссылку "Foods" в nav всех страниц

### Этап 3 — После 50+ страниц
- Вынести общие `<style>` в `assets/css/main.css`
- Подключать через `<link rel="stylesheet" href="/assets/css/main.css">`
- Это сильно уменьшит размер каждой страницы

### Этап 4 — При 100+ страницах
- Рассмотреть статический генератор (Eleventy / Hugo)
- Общий nav и footer в шаблоне — не копировать в каждый файл

---

## Шаблон страницы продукта (foods/banana.html)

URL: caloriescalc.org/foods/banana.html
Title: "Calories in Banana — Nutrition Facts | CaloriesCalc"
H1: "How Many Calories in a Banana?"

Структура страницы:
1. Hero — ключевые цифры (калории на 100г, на 1 штуку среднего)
2. Таблица КБЖУ — protein/carbs/fat/fiber
3. Сравнение порций (маленький / средний / большой / 100г)
4. Как вписать в дневную норму (блок с TDEE Calculator)
5. Похожие продукты (Related foods)
6. FAQ (сколько калорий в банане без кожуры, в жареном банане...)

---

## Шаблон категории продуктов (foods/index.html)

URL: caloriescalc.org/foods/
Title: "Calorie Counter — Food Nutrition Database | CaloriesCalc"
H1: "Calories in Foods — Full Nutrition Database"

Структура:
1. Поиск по продуктам (простой input + JS фильтр)
2. Популярные продукты (топ-20 карточками)
3. По категориям: Fruits / Vegetables / Proteins / Grains / Dairy / Snacks
4. Алфавитный список A–Z

---

## SEO стратегия для foods/ страниц

Каждая страница продукта таргетирует запрос:
- "calories in banana" — 165K запросов/мес
- "calories in apple" — 90K запросов/мес
- "calories in chicken breast" — 74K запросов/мес
- "calories in rice" — 60K запросов/мес
- "calories in egg" — 55K запросов/мес

KD этих запросов: 15–35 — достижимо для нового домена за 4–8 месяцев.
100 страниц продуктов = потенциально 200–500K визитов/мес суммарно.

---

## Nav для будущего (когда добавятся секции)

```html
<div class="nav-links">
  <a href="/">TDEE</a>
  <a href="/bmr-calculator.html">BMR</a>
  <a href="/macro-calculator.html">Macros</a>
  <a href="/protein-calculator.html">Protein</a>
  <a href="/bmi-calculator.html">BMI</a>
  <a href="/calorie-deficit-calculator.html">Deficit</a>
  <a href="/foods/">Foods</a>          <!-- добавить когда будет 5+ страниц -->
  <a href="/recipes/">Recipes</a>      <!-- добавить когда будет 5+ рецептов -->
  <a href="/articles/">Articles</a>    <!-- добавить при первых статьях -->
  <a href="/about.html">About</a>
</div>
```

---

## Приоритет создания контента

### Сейчас (максимальный ROI):
1. foods/banana.html — 165K запросов, KD 18
2. foods/apple.html — 90K запросов, KD 15
3. foods/chicken-breast.html — 74K запросов, KD 22
4. foods/egg.html — 55K запросов, KD 16
5. foods/rice.html — 60K запросов, KD 20
6. foods/avocado.html — 49K запросов, KD 14

### После первых 10 foods страниц:
7. articles/how-to-lose-20-pounds.html — KD 18
8. articles/1200-calorie-meal-plan.html — KD 22
9. foods/index.html — каталог

### Когда домен наберёт авторитет (6–12 мес):
10. exercises/ секция
11. meal-planner/ (требует больше JS)
12. recipes/ секция
