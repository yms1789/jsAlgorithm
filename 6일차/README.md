## ๐ ํฌ๋ ์ธ ์ธํ๋ฝ๊ธฐ ๊ฒ์

- ๋ฌธ์  ์ ํ: ์คํ / ํ
- Solution
  1. ํฌ๋ ์ธ์ ์๋์ํจ๋ค.(moves)
  2. moves์ ํด๋นํ๋ board์ ์ด ์ค ๊ฐ์ฅ ์์ ์๋ ๊ฐ์ ํ์
    - ๋ง์ฝ, ํด๋น ์ด์ ๊ฐ์ด ์๋ฌด๊ฒ๋ ์๋ค๋ฉด, moves ์ธ๋ฑ์ค๋ฅผ 1 ๋ํด์ฃผ๊ณ , ๋ค์ ํฌ๋ ์ธ ์์น์์ ๋ค์ ์ธํ์ ์ฐพ๋๋ค.
  3. ํ์ํ ๊ฐ์ basket์ ๊ฐ์ push.
  - basket์ ๊ฐ์ด 2๊ฐ ์ด์ ๋ค์ด์๋ค๋ฉด, pushํ ๊ฐ๊ณผ ๋ฐ๋ก ์ด์ ์ ๋ค์ด์๋ ๊ฐ์ด ๋์ผํ์ง ํ์ธ
    - ๋์ผํ๋ค๋ฉด ๋ ๊ฐ์ basket์์ ์ ๊ฑฐํ๊ณ  answer + 2
    - ๋ค๋ฅด๋ค๋ฉด ์๋ฌด์ผ๋ ์ผ์ด๋์ง ์๋๋ค.
  4. ์ ๊ณผ์ ์ moves์ ๋๊น์ง ๋ฐ๋ณตํ๋ค.
  5. answer๋ฅผ ๋ฆฌํด
- ๋ค๋ฅธ ์ฌ๋์ ํ์ด
  ```jsx
  // board์ ํ, ์ด์ ๋ฐ๊ฟ์ ํด๊ฒฐ
  const transpose = matrix =>
    matrix.reduce(
        (result, row) => row.map((_, i) => [...(result[i] || []), row[i]]),
        []
    );

  const solution = (board, moves) => {
    const stacks = transpose(board).map(row =>
        row.reverse().filter(el => el !== 0)
    );
    const basket = [];
    let result = 0;

    for (const move of moves) {
        const pop = stacks[move - 1].pop();
        if (!pop) continue;
        if (pop === basket[basket.length - 1]) {
            basket.pop();
            result += 2;
            continue;
        }
        basket.push(pop);
    }

    return result;
  };
  ```
  - transpose
    - ```reduce```์ ```map```์ ํ์ฉํ์ฌ board ๋ฐฐ์ด์ ํ ๊ฐ๋ค์ ์ด๋ก ์ฎ๊น
      - |๋ฐ๋๊ธฐ ์ |๋ฐ๋ ํ|
        |:--:|:--:|
        |
        0 0 0 4 3 | 0 0 0 0 0
        0 0 2 2 5 | 0 0 1 0 3
        0 1 5 4 1 | 0 2 5 0 1
        0 0 0 4 3 | 4 2 4 4 2
        0 3 1 2 1 | 3 5 1 3 1
        |
    - ์ฐธ๊ณ : [JS 2์ฐจ์ ๋ฐฐ์ด ํ, ์ด ๋ฐ๊พธ๊ธฐ](https://velog.io/@dyongdi/JS-2%EC%B0%A8%EC%9B%90-%EB%B0%B0%EC%97%B4%EC%9D%98-%ED%96%89%EA%B3%BC-%EC%97%B4-%EB%B0%94%EA%BE%B8%EA%B8%B0-Transposing-a-2D-array-in-JavaScript)

## ๐ Valid Anagram

- ๋ฌธ์  ์ ํ: Frequency Counter
- ๋ฌธ์ 
  > ๋ ๊ฐ์ ๋ฌธ์์ด์ด ์ฃผ์ด์ง๋ฉด ๋ ๋ฒ์งธ ๋ฌธ์์ด์ด ์ฒซ ๋ฒ์งธ ๋ฌธ์์ด์ ์๋๊ทธ๋จ์ธ์ง ํ์ธํ๋ ํจ์๋ฅผ ์์ฑํ๋ผ.  
    ***์ ํ์ฌํญ: ์๋ ฅ ๊ฐ์ ์๋ฌธ์ ์ํ๋ฒณ์ผ๋ก ์ด๋ฃจ์ด์ง ๋ฌธ์์ด***
- ์์
  ```jsx
  validAnagram('', '') // true
  validAnagram('aaz', 'zza') // false
  validAnagram('anagram', 'nagaram') // true
  validAnagram("rat","car") // false) // false
  validAnagram('awesome', 'awesom') // false
  validAnagram('amanaplanacanalpanama', 'acanalmanplanpamana') // false
  validAnagram('qwerty', 'qeywrt') // true
  validAnagram('texttwisttime', 'timetwisttext') // true
  ```
- Solution
  1. ๋ ๋ฌธ์์ด์ ์ ๋ณด๋ฅผ ๊ฐ์ฒด์ ๋ด๋๋ค.(key๋ ๋ฌธ์์ด์ ๊ฐ ๋ฌธ์, value: ๋ฌธ์์ด ๋ด ๋ฌธ์ ๊ฐ์)
  2. ๋ฌธ์์ด์ ๊ธธ์ด๋งํผ ๋ฐ๋ณตํ๋ฉด์ ์ฒซ ๋ฒ์งธ ๋ฌธ์์ด์ ์๋ ๋ฌธ์๊ฐ ๋ ๋ฒ์งธ ๋ฌธ์์ด์ ํฌํจ๋์ด์์ง ์๋ค๋ฉด false ๋ฆฌํด
  3. ์ฒซ ๋ฒ์งธ ๋ฌธ์์ด ๋ด ํน์  ๋ฌธ์ ๊ฐ์์ ๋ ๋ฒ์งธ ๋ฌธ์์ด์ ํน์  ๋ฌธ์ ๊ฐ์๊ฐ ๊ฐ์์ง ํ๋จ, ๊ฐ์ง ์๋ค๋ฉด false ๋ฆฌํด
  4. ์์ ์กฐ๊ฑด ์ธ์๋ true ๋ฆฌํด

- ๋ค๋ฅธ ์ฌ๋ ํ์ด
  ```jsx
  // ๋ฌธ์์ด ์ ๋ณด๋ฅผ ๋ด์ ๊ฐ์ฒด๋ฅผ ๋ ๊ฐ๋ฅผ ์์ฑํ์ง ์๊ณ  ํ๋๋ง ์์ฑํจ
  function valiidAnagram(first, second){
    if(first.length !== second.length){
      return false;
    }

    const lookup = {};

    for(let i = 0; i < first.length; i++){
      let letter = first[i];
      lookup[letter] ? lookup[letter] +=1 : lookup[letter] = 1;
    }
    for(let i = 0; i < second.length; i++){
      let letter = second[i];
      if(!lookup[letter]){
        return false;
      } else{
        lookup[letter] -= 1;
      }
    }
    return true;
  }
  ```
  1. ์ฒซ ๋ฒ์งธ ๋ฌธ์์ด ์ ๋ณด๋ฅผ ๊ฐ์ฒด(lookup)์ ๋ด์
  2. ๋๋ฒ ์งธ ๋ฌธ์์ด ๊ธธ์ด๋งํผ ๋ฐ๋ณต๋ฌธ์ ๋๋ฉด์
      -  lookup ๊ฐ์ฒด ๋ด ๋๋ฒ์งธ ๋ฌธ์์ด์ i๋ฒ์งธ ๋ฌธ์(letter) ๊ฐ์๊ฐ 0์ด๋ผ๋ฉด false ๋ฆฌํด
      - ์๋ค๋ฉด ํด๋น ๋ฌธ์์ ๊ฐ์๋ฅผ -1 ํด์ค
  3. ๋ฐ๋ณต๋ฌธ์ ์ ๋ถ ๋ค ๋์๋ค๋ฉด, ๋ ๋ฌธ์์ด์ ์๋๊ทธ๋จ ๋ฌธ์์ด์ด๋ฏ๋ก true ๋ฆฌํด