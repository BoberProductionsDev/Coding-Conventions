# Conventions
This document will contain a list with conventions to follow while we are creating Within the Scraps

# General coding conventions
1. By default all methods, properties and fields should be private. Only if it is needed should you make it public. This will prevent our Unity Editor from filling up with useless information that we can access in better ways.
2. When writing a comment on a piece of code or method. Write about what it means in the context instead of what it does.
3. Check and remove unused imports.
4. Check and remove unused variables/fields/properties
    - With 3 and 4 we aim to have clean readable code that is made in as few lines as possible.
5. Think of how this code is supposed to interact with other objects. Don't just make it for it's own purpose. It needs to work with other objects if necessary and share informatino with each other.
    - Example: The save system needs to save and load data for certain objects which state can change. Take the guard as an example for this. The save system needs to save the position and rotation of the guard, but maybe also if it's alerted to the player. This data also needs to be loaded in and work on startup. Keep your data private but accessible if needed.
6. Fields should be ordered in the following way. Make sure to group private variables together to make the code more readable.
    - private
    - [SerializeField] private
    - public
7. Avoid using var when the type is not mentioned in the same line. 
    - Bad Example: var something = Component.GetObject();
    - Good Example: var something = new StringComponent();
    - Good Example: StringComponent something = new StringComponent();

# GitHub
1. Make sure to push everything to your own branch. Do not push to the main dev branch! (At current time of writing would be playground-main)
2. Give a proper message with the commit (This is going to help when you have to inevitably write documentation and don't know anymore what happened in certain commits). See https://www.conventionalcommits.org/en/v1.0.0/
    - Example commit "feat: created functional gravity boots" or "fix: resolved an issue with the screwdriver where it would get stuck".
3. Pull Requests to the main or dev-main branch should have at least one review before being accepted.

# Naming Conventions
1. Classes and method: PascalCase; this means you start with a capital letter and use another capital letter at the start of each new word in the name.
    - Example class name: public class ScrewdriverManager
    - Example method name: public string GetName()
2. File names: PascalCase or normal spacing
    - Example File Names: "GameplayImages" or "Interaction Team"
3. Field names: camelCase (private variable start with "_"); this means you start with lower case and then use a capital letter at the start of each new word in the name.
    - Field names examples: "private string _exampleString" or "public bool isActive"
4. Property names: PascalCase
    - Example property name: "public string ExampleString { get; set; }"
5. Interface naming: PascalCase but must start with the capital letter I.
    - Example interface: "public interface IDataPersistence"
6. Generic Types (I doubt we're going to use these): PascalCase but must start with the capital letter T.
    - Example of generic type: "T" or "TKey"
7. Method paramaters: camelCase
    - Example of method paramaters: "private void SetString(string exampleString)
8. Constant fields: ALL_CAPS; All capital letters with "_" in between the words
    - Example of constant field: "public const int MAX_COUNT = 100;"

# Unity Editor Conventions
1. Use proper names for objects
    - Bad example: first_pylon
    - Good example: Battery Container
    - Good example: GameManager
2. Group objects to get a clearer view on the project in the editor
    - Bad example:
```
        ├── GameManager
        ├── SceneManager
        ├── EnemyManager
        ├── Checkpoint 1
        ├── Checkpoint 2
        └── Checkpoint 3
```
    - Good example:
```
        Managers
        ├── GameManager
        ├── SceneManager
        └── EnemyManager
        Checkpoints
        ├── Checkpoint 1
        ├── Checkpoint 2
        └── Checkpoint 3
```
3. Order of objects
```
    ├── Cameras
    ├── Canvas (UI)
    ├── Level Design
    ├── Managers
    └── Other objects
```
