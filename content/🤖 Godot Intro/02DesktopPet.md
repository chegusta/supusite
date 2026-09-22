---
title: 02 🐕 Desktop Pet
---

# Was ist das Ziel?
Wir erstellen ein kleines interaktives Tierchen, das angeklickt werden kann. Sobald User:innen damit interagieren, werden ein Ton und eine Animation abgespielt.

## Übersicht der Schritte
* [[GodotGlossary#Area2D|Area2D]]erkennt gemeinsam mit `CollisionShape2D` Maus-Click
* [[GodotGlossary#AnimatedSprite2D|AnimatedSprite2D]] spielt Sprite Sheet-Animationen ab
* [[GodotGlossary#AudioStreamPlayer|AudioStreamPlayer]] spielt Sound ab
* **GDScript**: 
	* Signal des Maus-Clicks erkennen und Funktionen aktivieren (Animation & Audio abspielen)
	* `print`-Funktion nutzen, um uns beim Coden zu helfen

# Implementierung

## Projekteinstellungen
Wir öffnen zuerst unter `Project > Project Settings` die Optionen für unser Projekt. Unter `Display > Window` lassen sich die Optionen für `Viewport Width` und `Viewport Height` finden. Wir können auch die Suchfunktion unter `Filter Settings` verwenden, um die Optionen schnell zu finden. Diese bestimmen die Größe unseres Programmfensters, also die größe des laufenden Spiels.

>[!tip] Editor-Sprache
> Sollte deine Godot-Version auf Deutsch sein, kannst du in den Editoreinstellungen die Sprache ändern. Ihr könnt ihr im Suchfeld nach "Sprache" suchen).

Da wir schon hier sind, können wir noch eine weitere Einstellung machen, die uns später helfen wird. Oben im Reiter `Input Map` > `Add New Action`: Name ist beliebig, aber wir verwenden einfach "Interact" > `Add`. Wir gehen dann zur neu erstellen Kategorie "LeftMouseClick" und clicken rechts auf das Plus-Symbol. Wir klicke danach auf `Listening for Input` und schon hat Godot unseren Mausclick registiert.

> [!info] Input Actions
> Wir können in Godot beliebig viele `Input Actions` definieren. Eine könnten wir z.B. "Jump" und mit dem obengenannten Verfahren mit beliebigen Tasten kombinieren (z.B. Keyboard, Maus, Controller,...)
> Wenn wir später im Code "Jump" aufrufen, würde jede dieser Tasten gelesen werden.

## Szenenkomposition
Im Hauptfenster klicken wir links im Scene-Fenster auf "Node2D" und speichern die Datei sofort als "main.tscn" (beliebiger Name) ab. Das ist die Haupt-[[Scene]] in der wir arbeiten werden. Die Node2D können wir uns wie den Ursprung unserer Szene bzw. als die Wurzel unseres Level-Baums.

Als nächstes bauen wir unser Desktop-Pet langsam auf. Zuerst erstellen wir mit Rechtsclick und `Add New Node` ein neues Objekt namens `Area2D`. Wir können dieses auf "Pet" umbenennen und die Warnung rechts für's erste ignorieren.


## 💪 Übung: Modifikation
Versuche das Projekt zu modifizieren, indem du ein weiteres Feature hinzufügst oder etwas veränderst. Vorschläge findest du im Spoilerkasten unten.

> [!faq]- Vorschläge für Modifikationen
>* Eigenes Sprite Sheet + Sound erstellen und reinladen
>* Partikelsystem aktivieren (`ParticleSystemCPU`)
>* Sprite skalieren (`AnimationPlayer`)
>* Sprite spiegeln (horizontal/vertikal)


#### 👉 Weiter mit [03 💫 Animated Shapes!](03AnimatedShapes.md)