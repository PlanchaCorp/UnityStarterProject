# Unity Starter project

## Using Visual Code

Please install the editorconfig plugin, so we use the same settings   

## Configure Unity for Git

*[Instructions taken from here](https://thoughtbot.com/blog/how-to-git-with-unity)*  
* Make the .meta files visible to avoid broken object references:
  * Go to *Edit > Project Settings > Editor*
  * In *Version Control*, select *Mode: "Visible Meta Files"*
* Use plain text serialization to avoid unresolvable merge conflicts
  * In *Asset Serialization*, select *Mode: "Force Text"*
Save your changes using *File > Save Project*  

## File structure

- Separate the Assets file depending on what they are.  
- File naming practices:  # Try to not use underscores (_), whitespaces, hyphens (-) unless it belongs to the word  
  - Capitalize the folder names and use plural when possible.  
  - For all Unity files and scripts, use UpperCamelCase / PascalCase (ex: *LevelGenerator.cs*, *MyAwesomeScene.unity*, *Player.prefab*)  
  - For raw resources that are not scripts (and not Unity related), please use lowerCamelCase (ex: *playerRunning.png*, *deathRequiem.mp3*, *pillStats.json*)  

Example with a standard tree structure (this is but an example, though the comments are useful):  
```
- Scenes
  - Levels
    - Level01.unity
  - MainMenu.unity
  - Tests # Please put scenes that should not be shipped at the end within a **Tests** folder
    - Greg.unity
    - TestWithUsefulName.unity
- Scripts
  - Player
    - Movement.cs
  - UI
    - HealthBar.cs
- Sprites
  - Entities
    - slime.png
    - player.png
  - Items
    - projectile.png
- Sounds # Let's try to put music AND sound effects within one folder; we can separate them into subfolders
  - Music
    - frozenMemories.mp3
  - Effects
    - willhelmScream.mp3
- Prefabs
- Tiles
```

