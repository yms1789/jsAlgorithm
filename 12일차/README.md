## ๐ reverse

- ๋ฌธ์  ์ ํ: Udemy ์ฝ๋ฉ์ฐ์ต(์ฌ๊ท)
- ๋ฌธ์  ๋ด์ฉ
  - ์ฌ๊ท๋ฅผ ์ฌ์ฉํด์ ์๋ ฅ๋ฐ์ ๋ฌธ์์ด์ ์ญ์์ผ๋ก ๋ฆฌํดํ๋ ๋ฌธ์ 
  - ex)
    ```jsx
    reverse('awesome') // 'emosewa'
    reverse('rithmschool') //'loohcsmhtir'
    ```
- solution
  - ์๋ ฅ๋ฐ์ ๋ฌธ์์ด์ ์ฒซ๋ฒ์งธ ๋ฌธ์๋ฅผ ๋งจ ๋ค๋ก ๋๋ฆฌ๋ ๊ณผ์ ์ ์ฌ๊ท๋ฅผ ์ฌ์ฉํด์ ๋ฐ๋ณตํจ

## ๐ isPalindrome
- ๋ฌธ์  ์ ํ: Udemy ์ฝ๋ฉ์ฐ์ต(์ฌ๊ท)
- ๋ฌธ์  ๋ด์ฉ
  - ์ฌ๊ท๋ฅผ ์ฌ์ฉํด์ ์๋ ฅ๋ฐ์ ๋ฌธ์์ด์ด ํ๋ฌธ์ธ์ง ์๋์ง๋ฅผ ๋ฆฌํดํ๋ ๋ฌธ์ 
  - ex)
    ```jsx
    isPalindrome('awesome') // false
    isPalindrome('foobar') // false
    isPalindrome('tacocat') // true
    isPalindrome('amanaplanacanalpanama') // true
    isPalindrome('amanaplanacanalpandemonium') // false
    ```
- solution
  - ์ฌ๊ท๋ฅผ ์ด์ฉํด ๋ฌธ์์ด ์ ๋ค๋ฅผ 1๊ธ์์ฉ ์๋ผ๋
  - ์๋ ฅ๋ฐ์ ๋ฌธ์์ด์ ์ฒซ๋ฒ์งธ ๋ฌธ์์ ๋ง์ง๋ง๋ถ์๋ฅผ ๋น๊ตํด์ ๊ฐ์ง ์์ผ๋ฉด `false` ๋ฆฌํด
  - ๋ฌธ์์ด์ ๊ธธ์ด๊ฐ ๋๋  ๋ ๊น์ง ๋ฌธ์์ด์ ์ ๋ค๊ฐ ๊ฐ๋ค๋ฉด true ๋ฆฌํด

- ๋ค๋ฅธ ์ฌ๋ ํ์ด
  ```jsx
  function isPalindrome(str){
    if(str.length === 1) return true;
    if(str.length === 2) return str[0] === str[1];
    if(str[0] === str.slice(-1)) return isPalindrome(str.slice(1,-1))
    return false;
  }
  ```

