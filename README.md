<!-- _Fork_ deze deeltaak en ga aan de slag. 
Onderstaande outline ga je gedurende deze taak in jouw eigen GitHub omgeving uitwerken. 
De instructie vind je in: [docs/INSTRUCTIONS.md](docs/INSTRUCTIONS.md) -->

# 📅 04-12-2023 | User Story & Gebruiker

Hier meer informatie over waar de onderstaande wireflow op is gebaseerd.

**Gebruiker:** ```De buurtbewoners van Amsterdam West.``` <br>
**User Stoty:** ```Als stichting of bewoner kan ik een initiatief aanmelden via een contactformulier op de website.```

# 📅 04-12-2023 | Wireflow

Ik heb eigenlijk twee verschillende scenario's uitgebeeld voor mijn wireflow, bekijk ze hieronder!

![image](https://github.com/itsValyria/fix-the-flow-wireflow/assets/76444716/618e63b6-70fb-4ecd-bf83-8bde8d377969)

# 📅 07-12-2023 | Wireflow

Vandaag heb ik de JavaScript voor deze wireflow geschreven, enkel alleen voor de bovenste rij. De invalid e-mail ben ik nog niet aan begonnen wegens tijdgebrek.

Ik heb hierbij de volgende bronnen geraadpleegt:
1. [MDN - Blur event](https://developer.mozilla.org/en-US/docs/Web/API/Element/blur_event)
2. [MDN - classList property](https://developer.mozilla.org/en-US/docs/Web/API/Element/classList)
3. Op het einde een klein beetje trouble shooting (= het ook toepassen op de dropdown) met mijn vriend ^^

Eerst maak ik een item voor de form aan. In dit geval is het een text input voor de voornaam van de persoon die de form invult. Hier voeg ik een ID aan toe zodat ik deze in de JavaScript code kan aanroepen.

```html
<label for="fname">Voornaam<span>*</span></label>
<input type="text" id="vnaam" name="voornaam" placeholder="Jouw voornaam.." required>
```

Dan schrijf ik de JavaScript die dus met het ID dit stukje code aanroept. Wanneer de element out of focus gaat (ook wel blurred genoemd) voert de functie ```checkIfEmpty``` uit.

```js
let vnaam = document.getElementById('vnaam');
vnaam.addEventListener('blur', () => {
  checkIfEmpty(vnaam);
});
```

Hier declare ik wat de functie ```checkIfEmpty``` nou eigenlijk doet. Hij kijkt of de element value 0 is, of te wel, leeg. Indien dit het geval is, triggered hij de class ```form__invalid--visible``` waardoor de border van het veld rood wordt. Indien er wel wat in het veld staat,  dus de input value is **niet** 0, dan haalt hij die class weg, als die er was door bijvoorbeeld een vorige poging.

```js
function checkIfEmpty(element) {
  if(element.value == null || element.value == '') {
    element.classList.add('form__invalid--visible')
    document.getElementById('invalidFieldMessage').classList.add('form__invalid--message');
  } else {
    element.classList.remove('form__invalid--visible')
    document.getElementById('invalidFieldMessage').classList.remove('form__invalid--message');
  }
}
```

Zie hier het eindresultaat:

![image](https://github.com/itsValyria/fix-the-flow-wireflow/assets/76444716/0e8676c8-ab08-44ee-ab27-47b3a8c7fb56)
![image](https://github.com/itsValyria/fix-the-flow-wireflow/assets/76444716/7d128592-9bed-4740-a9ea-7651d3713404)

PS: De focus ring is hier oranje en hoort zwart te zijn, dit moet ik nog aanpassen. Hij was eerst wel zwart, maar toen magisch niet meer!




## Licentie

This project is licensed under the terms of the [MIT license](./LICENSE).
