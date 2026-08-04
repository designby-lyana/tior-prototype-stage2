# Changelog — TIOR / OponyToMy (Stage 2)

Формат: дата → зміна → commit.

## 2026-08-04

- **Wyniki wyszukiwania (mobile):** додано ЕТАЛОННУ картку товару (Product Card v2, затверджений вигляд) першою карткою в список результатів пошуку. Джерело макету — файл "product card 3 breakpoints.html". Нова розмітка йде під класами `.pr-redesign`/`.pr-font-v2`, весь новий код позначено коментарями `NOWA FUNKCJA`/`KONIEC NOWEJ FUNKCJI` в HTML і CSS — щоб відрізнити від решти карток, які поки лишаються в попередньому стилі. Додано 4 нові CSS-токени (`--radius-md`, `--radius-xs-v2`, `--color-season-summer`, `--color-season-winter`), решта карток і базові стилі не змінювались.

## 2026-07-28

- **Чекаут (Podsumowanie zamówienia):** прибрано чекбокс "Potwierdzam szczegóły zamówienia i akceptuję warunki." Замінено на дрібний текст під кнопкою "Złóż zamówienie" — той самий патерн, що й на формі "Skontaktuj się": "Składając zamówienie, akceptujesz Regulamin i Politykę prywatności OponyToMy." (commit `f4ee0e6`)
