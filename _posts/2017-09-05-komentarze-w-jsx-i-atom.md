Siedzę właśnie nad kolejną aplikacją pisaną z nieocenioną pomocą React-a. Wszystko super, ale od zawsze denerwował mnie jeden drobiazg -- **wstawianie komentarzy w JSX**.

Na początek: czym jest JSX? To, jak mówią, ["syntax extension to JavaScript"](https://facebook.github.io/react/docs/introducing-jsx.html), czyli rozszerzenie składni języka JavaScript. Logiczne zatem, że komentarze powinno się wstawiać tak jak w JS. Niezupełnie... 

Ze względu na dziwną mieszankę składniową w JSX (taki JS-owo-HTML-owy konglomerat), nie można tu stosować ani komentarzy HTML-owych, czyli `<!-- -->`, ani (bezpośrednio) javascriptowych (`//`, `/* */`). Spójrzmy na przykład:

```javascript
render() {
  return (
    <div>
      <A />
      <B />
    </div>
  )
}
```

Jeżeli chcemy zakomentować komponent `A`, musimy najpierw potraktować go jako JavaScript (czyli otoczyć blokiem `{ }`), a nastepnie w tym JavaScripcie wstawić komentarz blokowy:
```diff
    ...
-     <A />
+     {/* <A /> */}
      <B />
    ...
```

Trzeba się nieźle namachać klawiaturą ;)

W większości edytorów są podpięte przyjemne skróty klawiaturowe do wstawiania komentarzy, ale zwykle tylko tych jednowierszowych, a już na pewno w standardzie nie ma takich czarów, jakie tu są potrzebne. Nie inaczej jest w [Atomie](https://atom.io/), którego używam do aplikacji webowych. Do przełączania komentarza w zaznaczonych liniach służy skrót `Ctrl-/`. I tyle.

Do tej pory nie udało mi się zmotywować, by wpisać w google magicznych słów "jsx comment atom", i jak dureń wstawiałem te `{/*` i `*/}`... Wczoraj się stało! Skromna paczuszka **jsx-comment** robi co do niej należy. W dodatku funkcja jest dostępna pod przyjaznym skrótem `Ctrl-Alt-/`. Nic więcej do szczęścia nie trzeba!
