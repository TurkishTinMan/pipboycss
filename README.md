## Pip-boy css con i keyframes

Ovviamente per iniziare scriviamo il codice html di riferimento
```
<div id="pipbody">
    <div class="scan"> <>
    <p>Bacon ipsum dolor amet venison sausage cupim, hamburger jerky chuck boudin turkey. Kielbasa capicola bresaola, short ribs short loin boudin turkey t-bone drumstick jerky sirloin salami. Chuck cow capicola bacon, venison short ribs meatloaf corned beef andouille tri-tip turducken hamburger drumstick jerky. Sausage pork belly pig shank bacon. Short loin rump boudin turkey bresaola sausage frankfurter turducken drumstick pork belly pastrami short ribs cupim tenderloin. Salami pastrami tenderloin t-bone bacon. Swine spare ribs porchetta tenderloin, andouille doner salami leberkas beef pancetta pig alcatra tri-tip bresaola tongue.</p>
    <p>Flank sausage doner andouille. Swine shank fatback drumstick, picanha meatloaf brisket shoulder short loin kielbasa kevin chicken flank jerky. Alcatra flank bresaola beef ribs chicken pork belly prosciutto jerky pig doner swine shank capicola. Tri-tip andouille rump frankfurter short loin tail. Tongue rump doner kevin cow, shankle jowl beef ribs. Shankle pork chop hamburger flank bresaola shoulder burgdoggen doner ball tip ham hock andouille.
    </p>
</div>

```
Iniziamo aggiungendo regole css per il div, che lo renderanno nero, e tondo, come uno schermo:
```
.pipboy{
    background-color:#000;  
    background-image:radial-gradient(#444, #111); 
    border-radius:30px;padding:30px;
}
```

Cambiamo il font e creiamo il primo keyframe, il colore del testo, infatti non sarà regolare:

```
@keyframes colorPulse {
  0%, 100% {
    color:#0c0;
  }
  50% {
    color:#080;
  }
}
.pipboy{
    ...
    animation:colorPulse 5s infinite ease-in-out;
}
```

Rendiamo relative il padre di scan e lui assoluto, in questo modo potremmo farlo muovere relativamente nell'animazione:
```
@keyframes wave {
  0{bottom:100%;opacity: 0;}
  100%{bottom:0px; opacity: 0.25;}
}
.pipboy{
    ...
    position:relative;
}
.scan{
    width: 100%;
    height: 80px;
    background: linear-gradient(rgba(0,0,0,0),#7ff12a);
    position: absolute;
    animation:wave 5s infinite ease-in-out;
    z-index: 99;
    opacity: 0;
    bottom:100%;
    left: 0px;
}
```