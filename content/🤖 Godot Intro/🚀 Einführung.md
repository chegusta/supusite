

## Grundlegende Ideen und Konzepte
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

---

## Godot Engine: Konzepte

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
audiostreamplayer.stream = my_stream # assigns stream that is saved in variable to audio player
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



