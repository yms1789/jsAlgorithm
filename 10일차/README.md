## π λ΄μ 

- λ¬Έμ  μ ν: μν
- solution
  - a λ°°μ΄μ κ° μμλ€κ³Ό b λ°°μ΄μ μμλ€μ κ³±ν΄μ μλ‘ λνλ©΄ λλ λ¬Έμ 
  - λ°λ³΅λ¬Έμ μ¬μ©ν΄μ a, bμ iλ²μ§Έ μΈλ±μ€λΌλ¦¬ κ³±ν κ°μ λν΄μ λ¦¬ν΄
  
- λ€λ₯Έ μ¬λ νμ΄
  ```jsx
  function solution(a, b) {
    return a.reduce((acc, _, i) => (acc += a[i] * b[i]), 0);
  }
  ```
  - `reduce` λ©μλλ₯Ό μ¬μ©ν΄μ λ³μ `acc`μ κ° λ°°μ΄ μμλ€μ κ°μ λν΄μ λ¦¬ν΄ν΄μ€
