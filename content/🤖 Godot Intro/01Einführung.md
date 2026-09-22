---
title: 01 🚀 Einführung
socialDescription: blablöadf
socialImage: quartz/static/og-image.png
---

# Game Engines
Game Engines stellen Funktionen, die man für die Entwicklung von Computerspielen erwarten würde, in Software-Form zur Verfügung. Zu dieser Funktionalität zählen z.B. Physics, Rendering, evtl. eine Script-Sprache, usw. Game Engines ermöglichen, relativ schnell zu Ergebnissen zu kommen. Sie nehmen uns viel Arbeit ab, aber auch die Kontrolle, die man z.B. mit custom Game Engines oder [Frameworks](https://gamefromscratch.com/the-best-game-development-frameworks/) hätte.

## Beliebte "gratis" Game Engines
Es gibt *einige* beliebte Game Engines, die (vorerst) ohne Kosten genutzt werden können. In weiterer Folge sind drei gelistet, jeweils mit einer *persönlichen* Beurteilung (für meine Use Cases).

### Unreal Engine (Epic Games)

+ High-End Graphics für Filmindustrie & AAA-Games
+ Viele fortgeschrittene Tools, programmierbar in C++ oder Blueprints (Visual Scripting)
+ Marketplace-Ökosystem (Fab)
+ Source-available (Source Code einsehbar)
+ sehr groß (mehrere GB)

### Unity (Unity Technologies): 
+ High-End Graphics bis 2D - große Flexibilität
+ Im Mobile und Indiebereich sehr beliebt
+ Relativ Modular, Packages können installiert werden über Unity Store
+ Scripting in C#

### Godot Engine 
* Free & Open Source
* "Community-driven" (bis zu einem gewissen Grad...)
* Flexibel (2D/3D)
* leicht, kompakt & läuft auf älterer Hardware
* Python-ähnliche Scriptsprache GDScript & C#



# Godot Engine: Konzepte

### Scene
Der Begriff *Scene* im Kontext von Godot kann mehrere Konzepte ausdrücken. Eine Scene ist üblicherweise eine Datei (.tscn), in der eine Hierarchie von verschiedenen Objekten (*Nodes*) und Komponenten erstellt werden kann. Diese umfassen Beispielsweise Objekte, die Bilder rendern (z.B. `Sprite2D`), Audio abspielen (`AudioStreamPlayer`) oder Kollisionsabfragen durchführen können (`Area2D`).

Scenes sind somit eine zusammenhängende Einheit. Wir können aber aus einzelnen Scenes "herauszoomen", und sie in andere Scenes einbetten. Eine Scene kann somit eine Komposition von Funktionen sein, die einen Player Character erstellen, aber auch ein UI-System kann eine Scene sein. Ein Level ist ebenfalls eine Scene, in der andere Scenes eingebettet werden können.

Scenes könnten in etwa so aussehen:

```
 🎮 PlayerScene
    ⭕ CollisionBox
    😎 PlayerSprite
    💚 Health
```

oder auch so...


```
🗺️ Level
    🎮 PlayerScene (from above :) )
    🟢 UIScene
	💯 Points
	⏰ Time Left
```

### Node
_Nodes_ erfüllen bestimmte Aufgaben bzw. Stellen Funktionen zur Verfügung. Eine `Area2D` erkennt zum Kollisionen mit anderen Objekten, ob die Maus in ihrem Einflussbereich ist, usw. Ein `Button`-Node fungiert aus clickbare UI-Oberfläche, die Beispielsweise das Spiel starten kann. 

Diese Funktionen können in der Editor UI (unter Inspector) bearbeitet werden. Das wahre Potenzial entfaltet sich jedoch erst mit Scripting.

>[!info]
>Jede Node hat bestimmte Eigenschaften und Funktionen (properties und methods). In der Node `AudioStreamPlayer` sind z.>B. folgende Elemente zu finden:
>    * `autoplay`: spielt Sound beim Start ab
>	* `AudioStream`: die Audiodatei
>	* `play()`: Funktion, die den Sound abspielt, wenn wir ihn brauchen


### GDScript
_GDScript_ ist Godots eigene Scriptsprache. Sie ist Python ähnlich und ermöglicht uns, unser Spiel interaktiver und komplexer zu machen:

```python
func my_goofy_function():
	var friends = get_friends()
	if friends:
		eat_ice_cream_with(friends)
	else:
		print("You have no friends :(")
```

Wir verwenden Scripts, um auf bestimmte Eigenschaften von Nodes zuzugreifen, Funktionen aufzurufen und die Elemente unseres Spiels generell miteinander zu verbinden. 

Im ersten Tutorial werden wir manchmal auf Methods oder Properties von Nodes zugreifen. Dafür verwenden wir `.` (Punkt).


```
audiostreamplayer.stream = my_stream # assigns stream 
#that is saved in variable to audio player

audiostreamplayer.play() # plays attached stream

sprite.flip_h = true # flips sprite horizontally
```

> [!info]
> Wir können `#` nutzen, um Kommentare in unseren Code einzufügen. Diese werden vom Compiler ignoriert und können uns helfen, uns später im Code wieder zurechtzufinden.
>```
># variable that stores my age
>var age = 22
>
># variable that stores whether I'm alive
>var alive = true
>
># TODO: implement death mechanics
>```

---

### Signals (Optional)
Ein weiteres wichtiges Konzept sind `Signals`. Jede Node "dokumentiert", was mit ihr passiert. Z.B. haben `AudioStreamPlayer`s ein Signal namens `finished()`. Sobald der Player das Abspielen der Datei beendet hat, sendet er dieses Signal aus ("Hey, ich bin fertig!"). 

Andere Nodes können so programmiert werden, dass sie auf dieses Signal hören und dann bestimmte Funktionen ausführen. Wir können Signale auch selbst programmieren.

>[!tip]- Illustratives Beispiel
> Wir programmieren ein Spiel, in dem Spieler:innen einen Hebel betätigen können, um eine Tür zu öffnen. Sobald Spieler:innen den Hebel betätigen, schickt er ein Signal aus ("Wurde betätigt!"). Dieses Signal wurde von uns definiert.
>
>Angenommen, unsere Hebel-Scene besteht aus folgender Hierarchie: ![[signal_hierarchy_example.png]] 
>
>`Area2D` sorgt dafür, dass über >`CollisionShape2D` erkannt wird, >wenn jemand die Area betritt. Das >Signal `area_entered` von >`Area2D` wird aktiviert. >Daraufhin sendet die Funktion, >die daran gekoppelt ist unser >eigenes Signal namens `activated`.
>>[!warning]Achtung
Es folgt kein echter `GDScript-Code, sondern eine vereinfachte Darstellung`
>```python {5}
># button script
>signal activated
>
>area_entered():
>	activated.emit()
>```
> Unser Tor-Objekt könnte so programmiert sein, dass es "zuhört", wann dieses Signal gesendet wird.
>```python
># door script
>listen_to(activated).call(open)
>
>open():
># opens door

# Godot Documentation
[Hier](https://docs.godotengine.org/en/stable/index.html) ist die sehr überschaubare Dokumentation von Godot Engine. Die meisten Funktionen, Signals, usw. können hier gefunden werden.



#### 👉 Weiter mit [🐕 Desktop Pet!](02DesktopPet)
