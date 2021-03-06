---
id: 5900f4d51000cf542c50ffe8
title: 'Проблема 361: Підпослідовність послідовності Thue-Morse'
challengeType: 5
forumTopicId: 302022
dashedName: problem-361-subsequence-of-thue-morse-sequence
---

# --description--

Послідовність Thue-Morse $\\{T_n\\}$ є виконанням двійкової послідовності:

- $T_0 = 0$
- $T_{2n} = T_n$
- $T_{2n + 1} = 1 - T_n$

Перші кілька термінів $\\{T_n\\}$ подаються так: $01101001\color{red}{10010}1101001011001101001\ldots$.

Ми визначаємо $\\{A_n\\}$ як відсортовану послідовність цілих чисел так, що двійковий вираз кожного елемента відображається як підпослідовність у$\\{T_n \\}$. Наприклад, десяткове число 18 записується як 10010 у двійковій системі. 10010 відображається у $\\{T_n\\}$ ($T_8$ to $T_{12}$), тому 18 є елементом $\\{A_n\\}$. Десяткове число 14 записується як 1110 у двійковій системі. 1110 ніколи не відображається в $\\{T_n\\}$, тому 14 не є елементом $\\{A_n\\}$.

Перші кілька термінів $A_n$ наведені наступним чином:

$$\begin{array}{cr}   n   & 0 & 1 & 2 & 3 & 4 & 5 & 6 & 7 &  8 &  9 & 10 & 11 & 12 & \ldots \\\\
  A_n & 0 & 1 & 2 & 3 & 4 & 5 & 6 & 9 & 10 & 11 & 12 & 13 & 18 & \ldots \end{array}$$

Ми також можемо підтвердити, що $A_{100} = 3251$ та $A_{1000} = 80\\,852\\,364\\,498$.

Знайдіть останні 9 цифр $\displaystyle\sum_{k = 1}^{18} A_{{10}^k}$.

# --hints--

`subsequenceOfThueMorseSequence()` повинен повернути `178476944`.

```js
assert.strictEqual(subsequenceOfThueMorseSequence(), 178476944);
```

# --seed--

## --seed-contents--

```js
function subsequenceOfThueMorseSequence() {

  return true;
}

subsequenceOfThueMorseSequence();
```

# --solutions--

```js
// solution required
```
