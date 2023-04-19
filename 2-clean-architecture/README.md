# 2 Clean Architecture

In this chapter, we'll learn, how to have a clean architecture that allows big teams to work together flawlessly.

## MVC Revisited
- Model: All the Data of your Game.
  - player stats
  - player level
  - enemy stats
  - items in the inventory
- View: Needs to react to changes of the Model (Observer Pattern).
  - when player health changes, health-bar needs to update itself
  - when the inventor contains a new item, the inventory ui needs to update itself.
  - when the player has a level-up, a cool effect needs to spawn.
- Controller: Needs to react to input and make changes to the model.
  - when the player walks into a spike, it needs to reduce player health.
  - when the players sells an item, it needs to remove the item and increase gold.

## The Common Ground: Data
As you can see:
- The View depends on the Model, so it can display its values on the Screen
- The Controller depends on the Model, so it can make changes to it

Not mentioned:
- The View and Controller also have some small inter-dependency:
  - When I click the Sell Item Button in the View, I want the Item to be sold through the Controller.
  - Either, the View has a dependency to the Controller `void onClick() {controller.SellItem(itemId);}`
  - Or better: You use a Broker (Publish/Subscribe Pattern) to send a Message to an unknown receiver.

Which leaves only the Model as the Main Dependency.

### The Model
The Model has a really big priority when working on the Game.
- It does not directly affect the Game and can't break anything.
  - Because it's like adding a new class `public class ItemData{string name; int damage;}`
  - It does not have any Behavior, only information.
- Therefore, it can usually be added early on and on the main branch.
  - To ensure that all Teams (Gameplay, Meta, UI) can work with it.
- Since everybody depends on it, changes on the Model can be
  - really difficult
  - affect many other scripts
- Therefore, it's best to put good planning into it.

### Configuration
Another thing that's part of the Model, but usually doesn't change during Runtime: Configuration files.
- Use Scriptable Objects, so they can be clearly treated as assets
  - e.g. `ItemData : ScriptableObject`
  - Instances: `BasicDagger`, `HeavyAxe`, `MachineGun`
- Make all Access Read-Only, i.e.
  - `[SerializeField] private int damage;`
  - `public int Damage => damage;`

## Namespaces
Use Namespaces and Folders to avoid conflicts regarding class namings.

## Replaceable: Dependencies
Whenever you have dependencies, try to make them abstract to become independent of their implementation.

### Abstraction
First, design an interface for the class that you depend on.
```cs
public interface IBackend {
    PlayerInfo Login();
    SaveGame DownloadSaveGame();
    void PostScore(int score);
}
```

### Dummy
Then, start off by providing a dummy implementation for the class:

```cs
public class DummyBackend : IBackend{
    PlayerInfo Login(){
        Debug.Log("DummyBackend Login successful.");
        return new PlayerInfo("Marc", 10, true);
    }

    /*...*/

    void PostScore(int score){
        Debug.Log($"DummyBackend Post Score: {score}");
    }
}
```

Now, you can assign the Dummy Backend somewhere:
```cs
public static class Singletons{
    public static IBackend Backend = new DummyBackend();
}
```

And continue working on your actual features:
```cs
public class Game : MonoBehaviour {
    void Update(){
        if(playerWon){
            Singletons.Backend.PostScore(collectedApples);
        }
    }
}
```

### Dependency Inversion
Above example fulfills the Dependency Inversion principle:
- instead of depending on low-level details like
  - specific backend technology, e.g. Firebase
  - specific databases, e.g. SQL
  - specific input mechanisms, e.g. Keyboard

You are supposed to create an interface and depend on that.
- `IBackend`
- `IDatabase`
- `IInput`

And then implement those interfaces building Wrapper-Classes for each technology:
- `class FirebaseBackend : IBackend`
- `class SQLDatabase : IDatabase`
- `class KeyboardInput : IInput`

The advantage: You can replace the implementation anytime without your game noticing:
- `IBackend backend = new PlayFabBackend();`
- `IDatabase database = new CouchDatabase();`
- `IInput input = new ControllerInput();`

## Branching
Branching will be the key from now on to ensure that you can collaborate with one part of the team without affecting the other part of the team too much.

```
branch from main -> feature/inventory-ui
commit: create prefabs for inventory ui and item ui
commit: add scrollable inventory
merge main -> feature/inventory-ui
commit: update inventory ui
commit: removed unused dependencies
merge main -> feature/inventory-ui
create pull request feature/inventory-ui -> main
test
complete pull request: merge & delete feature/inventory-ui
```

But make sure to have branches not run separate for more than half a week. If it does, ask yourself: what is necessary to make this version not break anything (even though it might not be fully done, yet), so you can merge a first iteration ASAP

## Mono-Repository
Having all your code in one repository is generally considered not so clean architecture.But it generally comes with advantages for smaller and short-term projects. Just keep in mind, that later, you might want to create separate repositories for:
- Unity Project
- Backend Project
- Pathfinding Library
- AI Library