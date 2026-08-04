# Changelog — TIOR / OponyToMy (Stage 2)

Формат: дата → зміна → commit.

## 2026-08-04

- **Fix:** картка №2 (дублікат) з'являлась одразу при вході на екран результатів, хоча мала бути прихована до кліку. Причина: приховування було на inline `style="display:none"`, а `runResultsSearch()` (запускається автоматично при кожному вході на screenResults через `resetResultsPagination()`) явно скидає `style.display=''` для ВСІХ `.product-row` — це й "розкривало" картку №2 без кліку. Також id="refCardTwin" не працював як довгостроковий якір — пагінація (`buildResultsCard`) клонує картки з пулу і зрізає `id` з кожного клону. Виправлено: видимість тепер керується класом `.ref-card-twin` / `.is-revealed` (CSS, `!important`) замість inline style, а JS шукає картку №2 як `.nextElementSibling` клікнутої картки №1 (із запасним варіантом через `.querySelector`) замість `getElementById`. Лічильник "N produktów" (`updateFilterState`) також оновлено, щоб не рахувати приховану картку №2. Перевірено симуляцією кліків + повторного входу на екран (jsdom).
- **Wyniki wyszukiwania (mobile):** картка №2 — дублікат еталонної картки №1 (Nokian), прихована за замовчуванням, з'являється одразу під карткою №1 по кліку на іконки "авто + сезон" в картці №1 (toggle, повторний клік ховає назад). Новий JS `toggleRefCardTwin()` і атрибути на `.pr-attrs-left` позначено коментарями `NOWA FUNKCJA`.
- **Wyniki wyszukiwania (mobile):** додано ЕТАЛОННУ картку товару (Product Card v2, затверджений вигляд) першою карткою в список результатів пошуку. Джерело макету — файл "product card 3 breakpoints.html". Нова розмітка йде під класами `.pr-redesign`/`.pr-font-v2`, весь новий код позначено коментарями `NOWA FUNKCJA`/`KONIEC NOWEJ FUNKCJI` в HTML і CSS — щоб відрізнити від решти карток, які поки лишаються в попередньому стилі. Додано 4 нові CSS-токени (`--radius-md`, `--radius-xs-v2`, `--color-season-summer`, `--color-season-winter`), решта карток і базові стилі не змінювались.

## 2026-07-28

- **Чекаут (Podsumowanie zamówienia):** прибрано чекбокс "Potwierdzam szczegóły zamówienia i akceptuję warunki." Замінено на дрібний текст під кнопкою "Złóż zamówienie" — той самий патерн, що й на формі "Skontaktuj się": "Składając zamówienie, akceptujesz Regulamin i Politykę prywatności OponyToMy." (commit `f4ee0e6`)
