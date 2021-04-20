# Unity Starter project

## Using Visual Code

Please install the editorconfig plugin, so we use the same settings   

## File structure

- Separate the Assets file into folders, depending on what they are  
- File naming practices:  # Try to not use underscores (_), whitespaces, hyphens (-) unless it belongs to the word  
  - Capitalize the folder names and use plural when possible.  
  - For all Unity files and scripts, use UpperCamelCase / PascalCase (ex: *LevelGenerator.cs*, *MyAwesomeScene.unity*, *Player.prefab*)  
  - For raw resources that are not scripts (and not Unity related), please use lowerCamelCase (ex: *playerRunning.png*, *deathRequiem.mp3*, *pillStats.json*)  
  - For scripts and ScriptableObject: **always** name your file with the class name. You *will* get a bug if you name a "thingObject.cs" file for a "ThingObject" class.  

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

## Coding patterns

Our code tends to become messy. We should try to use some robust patterns to avoid bugs  

### State

Our code easily become convoluted because we don't do states (or not enough).  

#### The problem

We want to avoid using "if" conditions for complex objects behavior changes; example with a character that has to jump:  
```
void Player::handleInput(Input input) {
  if (input == PRESS_B) {
    if (!isJumping) {
      isJumping = true
      ...
    }
  }
}
```  
We want to avoid the above code. It looks fine as it is, but it will become messy once we need to:  
- implement a double jump
- implement a crouch system
- use animations
- have attacks that can be triggered on the ground or in the air
- ...
Instead we will use states!  

#### The switch state

The basic way to avoid this is to use a state with switch case.  
```
enum State {
  STANDING,
  JUMPING
}

void Player::handleInput(Input input) {
  switch (state) {
    case State.STANDING:
      if (input === PRESS_B) {
        state = State.JUMPING
        ...
      }
      break;
    case State.JUMPING:
      break;
  }
}

void Player::update(float deltaTime) {
  switch (state) {
    case State.JUMPING:
      jumpTime += deltaTime
      ...
      break;
  }
}
  
```
No "if hell" using this. Doesn't matter if you use switch or if for the state, but prefer switch if you have many states.  

*[Source](https://www.gameprogrammingpatterns.com/state.html)*

## Configure Unity for Git

* Make the .meta files visible to avoid broken object references:
  * Go to *Edit > Project Settings > Editor*
  * In *Version Control*, select *Mode: "Visible Meta Files"*
* Use plain text serialization to avoid unresolvable merge conflicts
  * In *Asset Serialization*, select *Mode: "Force Text"*
Save your changes using *File > Save Project*  

*[Source](https://thoughtbot.com/blog/how-to-git-with-unity)*  

