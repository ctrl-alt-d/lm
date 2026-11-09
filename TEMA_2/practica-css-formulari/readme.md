# Pràctica conjunta: donem estil a un formulari

Transformarem un formulari d'inscripció sense estils en una pàgina clara i agradable. L'HTML ja està escrit: el repte és decidir **quin element seleccionem, on escrivim el CSS i què canvia a la pantalla**.

Repassem la [sessió 6](../html06.md) i les propietats bàsiques de la [sessió 7](../html07.md). La segona part introdueix la [sessió 8](../html08.md) des de zero. No cal haver-la fet abans ni saber Flexbox, Grid o JavaScript.

## Material i manera de treballar

- Copia la carpeta [inici](./inici/) al teu ordinador. Treballa sobre aquesta còpia.
- Obre `index.html` i `estils.css` a l'editor i obre `index.html` al navegador. No cal cap servidor ni instal·lar res.
- Mantén l'editor i el navegador visibles. Desa i actualitza després de cada canvi.
- A cada pas, una persona proposa el selector, una altra la propietat i una tercera explica el resultat. Tothom ho aplica al seu ordinador.
- Abans de provar una regla, prediu què canviarà. Després comprova-ho amb el navegador.

El botó és de demostració i no envia dades. Ens centrarem en l'aparença del formulari.

**Durada orientativa:** 60 minuts per als passos 0–4 i 30 minuts més per als passos 5–7. Podem deixar la segona part per al dia que comencem el model de caixa.

## Què hem d'aconseguir?

Al final, la pàgina tindrà un fons gris clar, una capçalera blava, una zona central blanca, textos d'ajuda discrets i un avís destacat. A la segona part hi afegirem espai entre els camps, vores i controls més còmodes.

| Recurs | On el farem servir |
| --- | --- |
| Fitxer extern `estils.css` | Gairebé tots els estils de la pàgina |
| Bloc `<style>` | Una prova amb el color de l'avís |
| Atribut `style="…"` | Una prova sobre el mateix avís |
| Selector d'etiqueta | `body`, `header`, `h1`, `p`… |
| Selector de classe | Textos d'ajuda i camps que comparteixen estil |
| Selector d'ID | Un únic avís de places limitades |

## Pas 0. Mirem el formulari sense CSS · 5 min

1. Localitza la capçalera, el contingut principal, els grups de camps i el peu.
2. Clica una etiqueta de camp. Què passa amb el control associat?
3. Localitza un `id` i el `for` que hi apunta. Aquests IDs ja tenen una funció: no els canviïs.
4. Proposa tres millores visuals que puguem fer amb CSS.

**Per comentar:** el navegador ja mostra mides, marges i vores encara que nosaltres no hàgim escrit CSS. Són els seus estils per defecte.

## Pas 1. Connectem el CSS i seleccionem etiquetes · 10 min

Al `<head>`, substitueix el comentari del pas 1 per:

```html
<link rel="stylesheet" href="estils.css">
```

Escriu les primeres regles a `estils.css`:

```css
body {
  font-family: Arial, sans-serif;
  font-size: 16px;
  line-height: 1.5;
  color: #243247;
  background-color: #eef2f6;
}
```

Entre tots, completa aquestes regles:

| Selector | Propietats i valors |
| --- | --- |
| `header` | Fons `#173b65`, text blanc i text centrat |
| `h1` | Mida de lletra de `32px` |
| `main` | Fons blanc |
| `footer` | Text centrat i color `#526071` |

**Comprovació:** si canvies temporalment el fons de `body`, la pàgina ha de canviar. Si no passa, revisa el nom del fitxer, l'enllaç i si has desat.

## Pas 2. Una classe, diversos elements · 15 min

Una classe és un nom reutilitzable: a l'HTML escrivim `class="ajuda"` i al CSS la seleccionem amb `.ajuda`.

1. Afegeix `class="ajuda"` als dos paràgrafs d'ajuda: el del correu i el dels comentaris. Conserva els seus IDs.
2. Escriu una sola regla `.ajuda` amb color `#526071` i mida de lletra `14px`.
3. Afegeix les classes següents als elements indicats. Les farem servir ara i a la segona part.

| Classe | Elements que la reben |
| --- | --- |
| `camp` | Els quatre `div` que agrupen nom, correu, taller i comentaris amb les seves etiquetes |
| `control` | Els inputs de nom i correu, el `select` i el `textarea` |
| `etiqueta` | Els quatre `label` d'aquests camps |

No apliquis `control` als botons de ràdio ni a la casella de selecció: no volem que tinguin la mateixa amplada que un camp de text.

Al CSS, dona negreta a `.etiqueta` amb `font-weight: bold;`. Dona a `.control` la mateixa font i mida que el seu pare amb `font-family: inherit;` i `font-size: inherit;`: alguns controls tenen una tipografia pròpia del navegador.

**Comprovació:** canvia una vegada el color de `.ajuda`. Han de canviar els dos textos, però no la resta de paràgrafs. Un element pot tenir un ID i una classe alhora.

## Pas 3. Un ID per a un element concret · 10 min

Al paràgraf que comença amb «Places limitades», afegeix `class="avis"` i `id="avis-places"`. L'ID ha de ser únic dins de la pàgina.

Afegeix aquestes regles al fitxer extern:

```css
p {
  font-size: 16px;
}

.avis {
  color: #1d4ed8;
  background-color: #fff3cd;
}

#avis-places {
  color: #7a4100;
  font-weight: bold;
}
```

Prediu i comprova:

- Quin color tindrà l'avís? Quin selector l'ha decidit?
- Per què es manté el fons groc de `.avis`?
- Els dos textos `.ajuda` passen a tenir `16px` encara que la regla `p` sigui més avall al fitxer?

## Pas 4. El mateix estil en tres llocs · 20 min

Farem un experiment amb **la propietat `color` del mateix avís**. Anota el color que preveus abans de cada canvi.

1. Al `<head>`, després del `<link>`, afegeix:

   ```html
   <style>
     #avis-places {
       color: #6b21a8;
     }
   </style>
   ```

2. Compara aquesta regla amb `#avis-places` del fitxer extern. Tenen el mateix selector, però colors diferents. Quin veus?
3. Mou temporalment el bloc `<style>` abans del `<link>`. Què canvia? Torna'l a deixar després.
4. Afegeix `style="color: #b91c1c;"` al paràgraf de l'avís. Quin color veus ara?
5. A l'inspector del navegador, selecciona l'avís i busca les declaracions de `color` que apareixen ratllades.
6. **Neteja final:** elimina l'atribut `style` i tot el bloc `<style>`. Deixa els estils al fitxer extern i comprova que l'avís torna a ser marró.

En aquestes proves fem servir declaracions normals nostres, sense `!important` ni capes de cascada. Entre els selectors provats, l'ID té més especificitat que la classe i la classe que l'etiqueta. A igual especificitat, guanya la declaració que apareix més tard. L'estil en línia preval sobre aquestes regles. Un bloc `<style>` no guanya sempre pel fet d'estar dins de l'HTML.

**Punt de parada:** fins aquí hem repassat com s'aplica CSS. Podem continuar en una altra classe.

## Pas 5. Descobrim el model de caixa · 15 min

Ara introduirem contingut nou. Inspecciona el paràgraf de l'avís i localitza el dibuix de la seva caixa a les eines del navegador.

```text
Marge exterior → Vora → Espai interior → Contingut
margin          border  padding          text
```

Afegeix les propietats **d'una en una** a la regla `.avis` que ja tens:

```css
border: 2px solid #b77900;
padding: 12px;
margin-bottom: 24px;
```

1. Passa de `padding: 12px` a `padding: 24px`. Què passa amb el fons i l'espai entre el text i la vora?
2. Torna a `12px` i passa de `margin-bottom: 24px` a `48px`. On apareix l'espai? El marge es pinta de groc?
3. Recupera els valors originals abans de continuar.

Aplica ara aquests valors al fitxer extern. Afegeix les propietats a les regles existents quan el selector ja hi sigui.

| Selector | Propietats i valors |
| --- | --- |
| `body` | `margin: 0;` |
| `header` | `padding: 24px;` |
| `main` | `width: 80%;`, `max-width: 640px;`, `margin: 24px auto;`, `padding: 24px;`, `border: 1px solid #cbd5e1;` |
| `fieldset` | `margin: 0 0 20px;`, `padding: 16px;`, `border: 1px solid #cbd5e1;` |
| `.camp` | `margin-bottom: 16px;` |
| `.etiqueta` | `display: block;`, `margin-bottom: 6px;` |
| `footer` | `padding: 16px;` |

Aquí `max-width` limita l'amplada quan la finestra és gran; `auto` reparteix el marge horitzontal i centra `main`. Amb dos valors, `margin: 24px auto` indica primer dalt/baix i després esquerra/dreta. `display: block` posa cadascuna de les quatre etiquetes damunt del seu control; els labels dels ràdios i de la casella continuen al costat.

## Pas 6. Dimensions dels camps i del botó · 10 min

1. A `.control`, afegeix `width: 100%;`, `padding: 10px;` i `border: 1px solid #94a3b8;`.
2. Per incloure el farcit i la vora dins de l'amplada indicada, afegeix aquesta regla al començament del CSS:

   ```css
   * {
     box-sizing: border-box;
   }
   ```

   `*` selecciona tots els elements. Així, el `100%` dels controls ja inclou el seu `padding` i el seu `border`; els marges queden fora.

3. Dona al `textarea` una `height` de `100px`. Evita fixar l'altura de tota la pàgina: ha de poder créixer amb el contingut.
4. Dona al `button` fons `#173b65`, text blanc, font heretada, `padding: 12px 20px;` i `border: 2px solid #173b65;`.
5. Recorre el formulari amb la tecla Tab. Conserva l'indicador de focus del navegador i comprova que pots escriure i seleccionar opcions.

**Mini repte de caixa:** imagina una caixa amb `width: 200px`, `height: 80px`, `padding: 10px`, `border: 2px solid` i `margin: 20px`. Amb `box-sizing: content-box`, quant mesura de vora a vora? Quina amplada ocupa si hi sumes els marges laterals? I amb `border-box`? Fes el càlcul abans de provar-ho a l'inspector.

## Pas 7. Comprovació conjunta · 5 min

- [ ] El formulari carrega el seu fitxer CSS extern.
- [ ] Sabem mostrar com hem provat `<style>` i `style="…"` i per què els hem retirat.
- [ ] Una mateixa classe dona estil als dos textos d'ajuda.
- [ ] L'avís té un ID únic i conserva el fons definit per la classe.
- [ ] Sabem explicar què passa quan competeixen dues declaracions de `color`.
- [ ] Distingim l'espai exterior (`margin`) de l'interior (`padding`).
- [ ] Els camps tenen espai i els ràdios i la casella mantenen una mida natural.
- [ ] Les etiquetes continuen associades als camps i podem navegar amb Tab.

Per acabar, cadascú canvia dos colors i una mida, i explica quins selectors ha utilitzat. Desa `index.html` i `estils.css` junts. Si es demana lliurament, adjunta aquests dos fitxers i tres frases: què selecciona una classe, què selecciona un ID i en què es diferencien `margin` i `padding`.

La [guia docent](./guia-docent.md) conté les respostes, les pauses de posada en comú i la solució de referència.
