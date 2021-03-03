# answer for junyi-software-engineer-test

1. 字串反轉

(A)
```javascript
function reverseString(word) {
  const iterator = word[Symbol.iterator]()
  let theChar = iterator.next()
  const reArr = []

  while (!theChar.done && theChar.value !== ' ') {
    reArr.unshift(theChar.value)
    theChar = iterator.next()
  }

  const reWord = reArr.join('')
  return reWord
}
```

(B)
```javascript
function reverseWordInSentence(sentence) {
  const words = sentence.split(' ')
  const antiArr = []

  words.forEach(word => {
    antiArr.push(reverseString(word)) // from (A)
  })

  const antiSentence = antiArr.join(' ')
  return antiSentence
}
```

---

2. 扣除 3 和 5 的倍數，但保留 3 和 5 的公倍數
```javascript
function countCommonMultiple(num) {
  const arr = []

  for (let i = 1; i <= num; i++) {
    if (((i % 3) && (i % 5)) || !(i % 15)) {
      arr.push(i)
    }
  }

  return arr.length
}
```

---

3. 找出三個袋子中的筆

解題關鍵是「標示都是錯的」，這代表只要打開其中一個袋子，其他兩個可以直接推論出來。舉例來說（標示以 [] 表示）：

三個袋子的內容與分別為：鉛筆[混合]、原子筆[鉛筆]、混合[原子筆]。

當拿到我拿到一個「鉛筆[混合]」的袋子，就剩下裝有『原子筆』與『混合』的袋子，以及標有 [鉛筆] 與 [混合] 的標示。然而，因為全部都標錯了，所以『原子筆』袋子一定得配上 [混合] 的標示，另外的『混合』袋子就得是 [鉛筆] 的標示了。

所以，開一個就一定能推出其他兩個。

---

4. 迪士尼付的錢去哪裡

正確算出 900 元的方式為：
```
三個人付的 270 * 3 元（810 元）+ 服務生退還的 90 元 = 900 元
```

而被服務生私吞的 60 元其實包含在沒被退還的 810 元當中，也就是每個人多付了 20 元給服務生（20 元 * 3 = 60 元）。

所以按題目中的推算方式，並不能得出原始的總數 900 元。