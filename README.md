# Lambda Bootcamp

## Innan du sätter igång

**Samtliga Basic- och medelövningar kräver att din Lambdafunktion anropas via _egen URL_. Den skapas under `Configuration`sen `Lambda URL`, välj sedan `None`. Nu ska du se en fin URL som leder direkt till din Lambdafunktion, ex.**

```
https://atj0pr0sitjwrhg5k53jf5a0ltyse.lambda-url.eu-north-1.on.aws/
```

**Vid advanced så kommer fler tjänster involveras. Tänk då på att du troligtvis behöver ändra din IAM för Lambdafunktionen.**

## Basics

1. Skapa en funktion som vid anrop returnerar textsträngen:

```
Hejsan hallå, din snea tå!
```

2. Skapa en funktion som vid anrop returnerar vilken route du än anger.

```
<lamba_URL>/hello // hello
<lambda_URL>/pannkaka // pannkaka
<lambda_URL>/lsfjhsadfyusdfhjkasdhjkf // lsfjhsadfyusdfhjkasdhjkf
```

3. Skapa en funktion som på routen `/cat` returnerar textsträngen "Mjau!" och vid routen `/dog`returnerar "Woff!".

```
<lamba_URL>/cat // Mjau!
<lambda_URL>/dog // Woff!
```

4. Skapa en funktion som vid anrop returnerar vilken metod (GET, PUT, POST, PATCH etc ) som används. Testa anropa den med några olika metoder via en _http-klient_, ex. [Postman](https://postman.com).

```
GET <lamba_URL> // GET
POST <lamba_URL> // POST
PATCH <lambda_URL> // PATCH
```

5. Skapa en funktion som slumpar fram ett skämt ur en array med 5st fördefinerade skämt. Ju sämre skämt, desto bättre.

```
GET <lamba_URL>/joke // Where does bad light end up? - In prism.
```

6. Skapa en funktion som vid alla andra metoder än PUT returerar error:

```js
{
    statusCode: 403,
    body: JSON.stringify({ message: 'Method not allowed.'})
}
```

7. Skapa en funktion som tar emot en POST med nedan JSON. Funktionen ska returnera ett svar där texten står omvänt.

```json
{
  "text": "Hello there!" // !ereht olleH
}
```

## Mer än Basic

8. Gör en funktion som genererar ett _slumpat lösenord_. Man ska kunna justera längden genom att skicka in en param.
   ex. <lambda_URL>/password/30 <--- genererar ett 30 tecken långt lösenord

9. Gör övning 8, men gör lösenordsgeneratorn konfigurerbar genom att posta in ett object med följande params:

```js
{
    length: Number, // Lösenordets minsta längd
    capital: Boolean, // Lösenordet innehåller minst 1 stor bokstav
    lower: Boolean, // Lösenordet innehåller minst 1 liten bokstav
    numbers: Boolean, // Lösenordet innehåller minst 1 siffra
    symbols: Boolean // Lösenordet innehåller minst 1 symbol
}
```

10. Gör en lambda funktion som vid en POST översätter följande text från [rövarspråket](https://sv.wikipedia.org/wiki/R%C3%B6varspr%C3%A5ket).

```
RoRövovarorsospoproråkoketot äror SoSvoverorigogesos kokänondodasostote kokododsospoproråkok,
momedod unondodanontotagog foföror dodenon koknonacockokadode/soskokrorivovnona momororsosekokododenon.
DoDetot äror alolloltotsoså dodetot momesostot anonvovänondoda totaloladode kokododsospoproråkoketot
ocochoh hoharor fofunonnonitotsos i sosnonarortot övoveror sosexoxtotio åror.
Omom dodu äror enon avov dodemom sosomom foförorsostotåror dodetot kokanon dodu
koklolicockoka popå sosjojörorövovarorfoflolagoggoganon totilollol hohögogeror
ocochoh loläsosa vovidodarore popå rorövovarorsospoproråkoketot.
