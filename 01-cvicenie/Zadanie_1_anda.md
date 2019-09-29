# Zaujímavé JavaScript aplikácie 

- AR.js - Efficient Augmented Reality for the Web - 60fps on mobile!
- Colyseus - Multiplayer Game Server for Node.js
- Tone.js - A Web Audio framework for making interactive music in the browser

## AR.js

### Ukážka aplikácie

    <!doctype HTML>
    <html>
    <script src="https://aframe.io/releases/0.9.2/aframe.min.js"></script>
    <script src="https://raw.githack.com/jeromeetienne/AR.js/1.7.7/aframe/build/aframe-ar.js"></script>
    <body style='margin : 0px; overflow: hidden;'>
     <a-scene embedded arjs>
       <a-marker preset="hiro">
           <a-box position='0 0.5 0' material='color: yellow;'></a-box>
       </a-marker>
       <a-entity camera></a-entity>
     </a-scene>
    </body>
    </html>
    
<img src="https://cloud.githubusercontent.com/assets/252962/23068128/40343608-f51a-11e6-8cb3-900e37a7f658.jpg"/>

### Charakteristika

JavaScript knižnica na vloženie AR do browsera. 
Používa knižnicu artoolkit ktorá funguje pomocou markerov, zároveň používa aj three.js.
Keďže je umiestnená priamo v prehliadači, je možné ju spustiť aj na prehliadačoch pre Android a iOS. Snahou je priniesť
AR na všetky prehliadače pri vysokom FPS s jednoduchou implementáciou

## Colyseus

### Ukážka aplikácie

<https://colyseus.io/>

### Charakteristika

Mutliplayer Server postavený nad Node.js, umožňuje integráciu s viacerými klientami, napríklad pomocou Unity, HTML5 a podobne.
Používa Web Sockety na komunikáciu medzi serverom a klientami, vytvorí room pre každý socket a spracuváva komunikáciu.
Prínos tejto knižnice spočíva v uľahčení nastavovania server-client komunikácie, keďže poskytuje implementáciu aj pre server
 aj pre klient.
Jeho veľkou výhodou je implementovanie Redis databázy, ktorá umožňuje skvelé horizontálne škálovanie, keďže je veľmi rýchla
Backend je postavený na Express frameworku. Keďže je to knižnica, na stránke ktorá je vyššie spomenutá sú aj ukázané hry,
ktoré boli vytvorené. 

## Tone.js

### Ukážka aplikácie
<https://tonejs.github.io/>

Zahratie napísaných nôt v definovaných intervaloch

    var synth = new Tone.FMSynth().toMaster()
    
    //schedule a series of notes to play as soon as the page loads
    synth.triggerAttackRelease('C4', '4n', '8n')
    synth.triggerAttackRelease('E4', '8n', Tone.Time('4n') + Tone.Time('8n'))
    synth.triggerAttackRelease('G4', '16n', '2n')
    synth.triggerAttackRelease('B4', '16n', Tone.Time('2n') + Tone.Time('8t'))
    synth.triggerAttackRelease('G4', '16', Tone.Time('2n') + Tone.Time('8t')*2)
    synth.triggerAttackRelease('E4', '2n', '0:3')
    
Zaujímavé je napríklad zobrazenie jednoduchého klavíra

    const synth = new Tone.AMSynth().toMaster()
    
    //attach a listener to the keyboard events
    document.querySelector('tone-keyboard').addEventListener('noteon', e => {
      synth.triggerAttack(e.detail.name)
    })
    
    document.querySelector('tone-keyboard').addEventListener('noteoff', e => {
      synth.triggerRelease()
    })

### Charakteristika

JavaScript knižnica na produkovanie a syntetizovanie zvukov a tónov. 
Je umiestnená v browseri, kde vieme vyprodukovať rôzne tóny a modifikovať zvuk.
Jej prínos pre svet JS je, že umožňuje naprogramovať hudbu, bez potreby nejakého drahého software, či reálneho nástroja.
Bolo by napríklad možné, zložiť celú skladbu ako jeden skript.



