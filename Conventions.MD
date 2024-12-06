# Conventions
This document will contain a list of conventions to follow while we are creating Within the Scraps.

# General coding conventions
1. By default all methods, properties and fields should be private. Only if it is needed should you make it public. This will prevent our Unity Editor from filling up with useless information that we can access in better ways.
2. When writing a comment on a piece of code or method. Write about what it means in the context instead of what it does.
    - Comments must be written in English!
3. Check and remove unused imports.
4. Check and remove unused variables/fields/properties
    - With 3 and 4 we aim to have clean readable code that is made in as few lines as possible.
5. Think of how this code is supposed to interact with other objects. Don't just make it for it's own purpose. It needs to work with other objects if necessary and share informatino with each other.
    - Example: 
    ```
    The save system needs to save and load data for certain objects which state can change. Take the guard as an example for this. The save system needs to save the position and rotation of the guard, but maybe also if it's alerted to the player. This data also needs to be loaded in and work on startup. Keep your data private but accessible if needed.
    ```
6. Fields should be ordered in the following way. Make sure to group private variables together to make the code more readable.
    - Example:
    ```cs
    private string _id;
    private int _count;
    [SerializeField] private string name;
    [SerializeField] private string publicId;
    public GameObject prefab; 
    ```

7. Avoid using var when the type is not mentioned in the same line. 
    - Bad
    ```cs
    // Does not show the class type we are getting. The variable name does not count.
    var stringComponent = Component.GetObject();
    ```
    - Good
    ```cs
    // Shows the class type is StringComponent;
    var stringComponent = new StringComponent();
    ```
    ```cs
    // Shows the class type with the variable type
    StringComponent stringComponent = Component.GetObject();
    ```
    
# GitHub
1. Make sure to push everything to your own branch. Do not push to the main dev branch! (At current time of writing would be playground-main)
2. Give a proper message with the commit (This is going to help when you have to inevitably write documentation and don't know anymore what happened in certain commits). See https://www.conventionalcommits.org/en/v1.0.0/
    - Example commit "feat: created functional gravity boots" or "fix: resolved an issue with the screwdriver where it would get stuck".
3. Pull Requests to the main or dev-main branch should have at least one review before being accepted.

# Naming Conventions
1. Classes and method: PascalCase; this means you start with a capital letter and use another capital letter at the start of each new word in the name.
    - Bad: 
    ```cs
    public class Screwdriver_Manager
    ```
    ```cs
    public string getName() {}
    ```
    - Good: 
    ```cs
    public class ScrewdriverManager
    ```
    ```cs
    public string GetName() {}
    ```

2. File/Directory names: PascalCase or normal spacing
    - Bad:
    ```
    Assets/interaction_team/
    ```
    ```
    gameplay_images.meta
    ```
    - Good:
    ```
    Assets/Interaction Team/
    ```
    ```
    Gameplay Images or GameplayImages
    ```
    
3. Field names: camelCase (private variable start with "_"); this means you start with lower case and then use a capital letter at the start of each new word in the name.
    - Bad:
    ```cs
    private string exampleString;
    ```
    ```cs
    [SerializedField]
    public bool IsActive;
    ```
    - Good:
    ```cs
    private string _exampleString;
    ```
    ```cs
    [SerializedField]
    public bool isActive;
    ```
    
4. Property names: PascalCase
    - Bad:
    ```cs
    public string exampleString { get; set; }
    ```
    - Good:
    ```cs
    public string ExampleString { get; set; }
    ```
5. Interface naming: PascalCase but must start with the capital letter I.
    - Bad:
    ```cs
    public interface DataPersistence {}
    ```
    - Good:
    ```cs
    public interface IDataPersistence {}
    ```
6. Generic Types (I doubt we're going to use these): PascalCase but must start with the capital letter T.
    - Bad:
    ```cs
    public class Example<Bike> {}
    ```
    ```cs
    public class Dictionary<Value, ValueTwo> {}
    ```
    - Good:
    ```cs
    public class Example<T> {}
    ```
    ```cs
    public class Dictionary<TKey, TValue> {}
    ```
7. Method paramaters: camelCase
    - Bad
    ```cs
    private void SetString(string ExampleString) {}
    ```
    ```cs
    private void SetString(string _exampleString) {}
    ```
    - Good:
    ```cs
    private void SetString(string exampleString) {}
    ```
8. Constant fields: ALL_CAPS; All capital letters with "_" in between the words
    - Bad:
    ```cs
    public const int maxCount = 100;
    ```
    - Good:
    ```cs
    public const int MAX_COUNT = 100;
    ```

# Unity Editor Conventions
1. Use proper names for objects
    - Bad:
    ```
    => first_pylon
    ```
    - Good
    ```
    => Battery Container
    => GameManager
    ```

2. Group objects to get a clearer view on the project in the editor
    - Bad:
        ```
        ├── GameManager
        ├── SceneManager
        ├── EnemyManager
        ├── Checkpoint 1
        ├── Checkpoint 2
        └── Checkpoint 3
        ```
    - Good:

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
