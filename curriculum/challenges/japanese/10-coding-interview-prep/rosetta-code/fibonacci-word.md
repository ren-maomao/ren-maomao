---
id: 5992e222d397f00d21122931
title: フィボナッチ列
challengeType: 5
forumTopicId: 302269
dashedName: fibonacci-word
---

# --description--

[文書で説明されているように](https://hal.archives-ouvertes.fr/docs/00/36/79/72/PDF/The_Fibonacci_word_fractal.pdf)、フィボナッチ列は、フィボナッチ数列と類似した方法で作成されます。

<pre>F_Word<sub>1</sub> を <strong>1</strong> と定義します
F_Word<sub>2</sub> を <strong>0</strong> と定義します
F_Word<sub>3</sub> を F_Word <sub>1</sub> と結びついた F_Word<sub>2</sub> として作成します 例: <strong>01</strong>
F_Word<sub>n</sub> を F_word <sub>n-2</sub> と結びついた F_Word<sub>n-1</sub> として作成します
</pre>

# --instructions--

`n` までのフィボナッチ列を返す関数を作成します。 関数のパラメータとして `n` が与えられます。 この関数はオブジェクトの配列を返します。 オブジェクトは `{ N: 1, Length: 1, Entropy: 0, Word: '1' }` の形式である必要があります。

# --hints--

`fibWord` という関数です。

```js
assert(typeof fibWord === 'function');
```

`fibWord(5)` は配列を返します。

```js
assert(Array.isArray(fibWord(5)));
```

`fibWord(5)` は `[{ N:1, Length:1, Entropy:0, Word:"1" },{ N:2, Length:1, Entropy:0, Word:"0" },{ N:3, Length:2, Entropy:1, Word:"01" },{ N:4, Length:3, Entropy:0.9182958340544896, Word:"010" },{ N:5, Length:5, Entropy:0.9709505944546688, Word:"01001" }]` を返します。

```js
assert.deepEqual(fibWord(5), ans);
```

# --seed--

## --after-user-code--

```js
let ans=[ { N: 1, Length: 1, Entropy: 0, Word: '1' },

  { N: 2, Length: 1, Entropy: 0, Word: '0' },

  { N: 3, Length: 2, Entropy: 1, Word: '01' },

  { N: 4, Length: 3, Entropy: 0.9182958340544896, Word: '010' },

  { N: 5, Length: 5, Entropy: 0.9709505944546688, Word: '01001' }];
```

## --seed-contents--

```js
function fibWord(n) {

}
```

# --solutions--

```js
function fibWord(n) {
    function entropy(s) {
         //create an object containing each individual char
      //and the amount of iterations per char
        function prob(s) {
            var h = Object.create(null);
            s.split('').forEach(function(c) {
               h[c] && h[c]++ || (h[c] = 1);
            });
            return h;
        }

        s = s.toString(); //just in case
        var e = 0, l = s.length, h = prob(s);

        for (var i in h ) {
            var p = h[i]/l;
            e -= p * Math.log(p) / Math.log(2);
        }
        return e;
    }
    var wOne = "1", wTwo = "0", wNth = [wOne, wTwo], w = "", o = [];

    for (var i = 0; i < n; i++) {
        if (i === 0 || i === 1) {
            w = wNth[i];
        } else {
            w = wNth[i - 1] + wNth[i - 2];
            wNth.push(w);
        }
        var l = w.length;
        var e = entropy(w);

        if (l <= 21) {
            o.push({
                N: i + 1,
                Length: l,
                Entropy: e,
                Word: w
            });
        } else {
            o.push({
                N: i + 1,
                Length: l,
                Entropy: e,
                Word: "..."
            });
        }
    }
  return o;
}
```
