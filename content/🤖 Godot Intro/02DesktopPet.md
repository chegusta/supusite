---
title: 02 🐕 Desktop Pet
---

# 🎯 Was ist das Ziel?
Wir erstellen ein kleines interaktives Tierchen, das angeklickt werden kann. Sobald User:innen damit interagieren, werden ein Ton und eine Animation abgespielt.

## 📋 Übersicht der Schritte
* [[GodotGlossary#Area2D|Area2D]]erkennt gemeinsam mit `CollisionShape2D` Maus-Click
* [[GodotGlossary#AnimatedSprite2D|AnimatedSprite2D]] spielt Sprite Sheet-Animationen ab
* [[GodotGlossary#AudioStreamPlayer|AudioStreamPlayer]] spielt Sound ab
* **GDScript**: 
	* Signal des Maus-Clicks erkennen und Funktionen aktivieren (Animation & Audio abspielen)
	* `print`-Funktion nutzen, um uns beim Coden zu helfen

# 🔨 Implementierung

## 🔃 Assets ins Projekt laden
Für unser Projekt haben wir zwei Assets: Ein Sprite Sheet mit einer Katze und ein Sound-File. Wir können die beiden Dateien einfach von unserem Betriebssystem in das File System von Godot ziehen.

## 🛠️ Projekteinstellungen
Wir öffnen zuerst unter `Project > Project Settings` die Optionen für unser Projekt. Unter `Display > Window` lassen sich die Optionen für `Viewport Width` und `Viewport Height` finden. Wir können auch die Suchfunktion unter `Filter Settings` verwenden, um die Optionen schnell zu finden. Diese bestimmen die Größe unseres Programmfensters, also die größe des laufenden Spiels. Wir können z.B. 512 x 512 eingeben.

>[!tip] Editor-Sprache
> Sollte deine Godot-Version auf Deutsch sein, kannst du in den Editoreinstellungen die Sprache ändern. Ihr könnt ihr im Suchfeld nach "Sprache" suchen).

Da wir schon hier sind, können wir noch eine weitere Einstellung machen, die uns später helfen wird. Oben im Reiter `Input Map` > `Add New Action`: Name ist beliebig, aber wir verwenden einfach "Interact" > `Add`. Wir gehen dann zur neu erstellen Kategorie "LeftMouseClick" und clicken rechts auf das Plus-Symbol. Wir klicke danach auf `Listening for Input` und schon hat Godot unseren Mausclick registiert. Alternativ könnt ihr, wie im GIF unten zu sehen ist, eure Taste auswählen.

![[0101_project_settings.gif]]

> [!info] Input Actions
> Wir können in Godot beliebig viele `Input Actions` definieren. Eine könnten wir z.B. "Jump" und mit dem obengenannten Verfahren mit beliebigen Tasten kombinieren (z.B. Keyboard, Maus, Controller,...)
> Wenn wir später im Code "Jump" aufrufen, würde jede dieser Tasten gelesen werden.

## 🎨 Szenenkomposition
Im Hauptfenster klicken wir links im Scene-Fenster auf "Node2D" und speichern die Datei sofort als "main.tscn" (beliebiger Name) ab. Das ist die Haupt-[[Scene]] in der wir arbeiten werden. Die Node2D können wir uns wie den Ursprung unserer Szene bzw. als die Wurzel unseres Level-Baums.

Als nächstes bauen wir unser Desktop-Pet langsam auf. Zuerst erstellen wir mit Rechtsclick und `Add New Node` ein neues Objekt namens `Area2D`. Wir können dieses auf "Pet" umbenennen und die Warnung rechts für's Erste ignorieren. Danach klicken wir auf "Pet" und erstellen mit Rechtsclick (oder `CTRL + A`) eine weitere `Node` - diesmal ein `AnimatedSprite2D`. Diese Komponente wird dafür zuständig sein, dass unser Sprite Sheet animiert wird.

![[0102_area_animatedsprite.gif]]

Nun klicken wir auf `AnimatedSprite2D` und widmen uns dem Inspector rechts. Hier clicken wir auf `SpriteFrames <empty>` und wählen die Option `SpriteFrames` und klicken anschließend noch einmal darauf. Godot erstellt ein Umfeld, in dem wir unsere Sprite Sheets animieren können. Unten sollte sich nun ein Fenster geöffnet haben, das uns animieren lässt.

Wähle zuerst das Symbol, das wie ein kleines Gitter aussieht ("Add Frames from Sprite Sheet")

![[0104_add_anims.png]]

Es öffnet sich nun ein Fenster, dass die Sprite Frames unserer Katze anzeigt. Das Bild ist unterteilt in vier horizontale und vier vertikale Elemente. Wenn wir rechts diese Werte eingeben, wird das Bild in passende Zellen geteilt. Danach wählen wir oben "Select All" und unten "Add 12 Frames". Nun können wir die Animation abspielen, die FPS ändern, usw. Es macht Sinn, unserer Animation einen anderen Namen statt "default" zu geben. Nenne wir sie einfach "Cat". Danach deaktivieren wir das blaue Loop-Symbol bzw. clicken so lange auf jenes, bis es deaktiviert ist. Wir wollen nicht, dass sich die Animation wiederholt. Wird der Play Button aktiviert, spielt unsere Animation ein Mal ab.

Irgendwas wirkt komisch. Einerseits ist unsere Katze sehr klein. Andererseits wirkt sie verschwommen. Zuerst wählen wir unsere Pet-Node (`Area2D`) und verschieben sie in die Mitte. 

>[!warning] Achtung
> Wir verschieben die oberste Node, und alle anderen darunter gehen mit, auch unsere Animation.

Danach wählen wir unser `AnimatedSprite2D` und skalieren es: Wir drücken 'R' und machen es mit Shift und Mausclick + Ziehen so groß, wie wir wollen. Die Unschärfe lösen wir, indem wir im Inspector unter `Texture > Filter > Nearest` auswählen. Nun haben wir eine Pixelkatze!

## 📜 Unser erstes Script

# 💪 Übung: Modifikation
Versuche das Projekt zu modifizieren, indem du ein weiteres Feature hinzufügst oder etwas veränderst. Vorschläge findest du im Spoilerkasten unten.

> [!faq]- Vorschläge für Modifikationen
>* Eigenes Sprite Sheet + Sound erstellen und reinladen
>* Partikelsystem aktivieren (`ParticleSystemCPU`)
>* Sprite skalieren (`AnimationPlayer`)
>* Sprite spiegeln (horizontal/vertikal)


#### 👉 Weiter mit [03 💫 Animated Shapes!](03AnimatedShapes.md)