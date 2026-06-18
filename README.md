# Simple 2D Platformer Game Project

**Special thanks to "Pandemonium" for a fantastic course! [Youtube]([https://docs.unity3d.com](https://www.youtube.com/@PandemoniumGameDev))

A **real-time action game** developed in **Unity**, featuring interactive gameplay mechanics, physics-based movement, and efficient game state management. Built to demonstrate game design, scene architecture, and player interaction systems.

## Project Overview

This is an educational game project showcasing core game development concepts including player input handling, physics interactions, game state management, and scene transitions. The game provides an engaging gameplay loop with clear win/lose conditions and progressive difficulty.

---

## Game Features

### Gameplay Mechanics
- **Real-time Player Control:** Keyboard/input-based movement and actions
- **Physics-Based Interactions:** Gravity, collisions, and object dynamics via Unity Physics
- **Enemy AI:** Basic pathfinding and collision responses
- **Scoring System:** Points, lives, and game-over conditions
- **Scene Management:** Level transitions and UI state persistence
- **Audio Feedback:** Sound effects for actions and events (if included)

### Technical Highlights
- **Modular Architecture:** Separated player, enemy, and game manager scripts
- **State Machine:** Clean game state handling (playing, paused, game-over)
- **Asset Organization:** Structured folders for prefabs, sprites, and scenes
- **Efficient Rendering:** Optimized sprite rendering using Unity's 2D physics

---

## Technology Stack

| Component | Technology | Purpose |
|-----------|-----------|---------|
| **Engine** | Unity 2022.3+ | Game runtime and editor |
| **Scripting** | C# | Game logic, physics, and interactions |
| **Physics** | Unity 3D Physics / 2D Physics | Movement and collision detection |
| **Graphics** | Unity Sprite Renderer | 2D rendering and animations |
| **Build** | Unity Build Pipeline | Platform-specific deployment |

---

## Prerequisites

### Development
- **Unity Editor:** Version 2022.3 or later
- **Visual Studio / VS Code:** For C# scripting and debugging
- **.NET SDK:** 4.7.1+ (bundled with Unity)
- **Git:** For version control

### Runtime
- **Windows / macOS / Linux:** Standalone executable
- **WebGL / Mobile:** Optional deployment targets

---

## Installation & Setup

### 1. Clone the Repository
```bash
git clone https://github.com/VanThai42/A-simple-Java-game.git
cd A-simple-Java-game
```

### 2. Open in Unity

**Option A: Direct Open**
1. Launch **Unity Hub**
2. Click **Open Project**
3. Select the `A-simple-Java-game` folder
4. Wait for Unity to import assets and compile scripts (~1-2 minutes on first load)

**Option B: Unity Command Line**
```bash
unity -projectPath "$(pwd)" -username YOUR_UNITY_EMAIL -password YOUR_PASSWORD
```

### 3. Verify Setup
1. Open **Scenes/MainScene.unity** (or your entry scene)
2. Press **Play** (Ctrl+P) in the Editor
3. Verify game runs without compile errors in the Console

### 4. Build Standalone Executable

To create a playable build:

1. **File → Build Settings**
2. Select target platform (Windows PC, macOS, Linux)
3. Click **Build** and choose output directory
4. Run the generated `.exe` (Windows) or `.app` (macOS)

---

## Project Structure

```
A-simple-Java-game/
├── Assets/
│   ├── Scenes/
│   │   ├── MainScene.unity              # Primary gameplay scene
│   │   ├── MenuScene.unity              # Main menu (if included)
│   │   └── ...
│   ├── Scripts/
│   │   ├── Player/
│   │   │   ├── PlayerController.cs      # Player movement and input
│   │   │   ├── PlayerHealth.cs          # Health/lives system
│   │   │   └── PlayerAnimator.cs        # Animation state
│   │   ├── Enemy/
│   │   │   ├── EnemyController.cs       # Enemy AI and behavior
│   │   │   ├── EnemyPatrol.cs           # Pathfinding logic
│   │   │   └── EnemySpawner.cs          # Spawn management
│   │   ├── Game/
│   │   │   ├── GameManager.cs           # Game state and logic
│   │   │   ├── ScoreManager.cs          # Score tracking
│   │   │   ├── UIManager.cs             # HUD and menus
│   │   │   └── InputHandler.cs          # Centralized input
│   │   └── Utilities/
│   │       ├── Constants.cs             # Game-wide constants
│   │       └── ObjectPool.cs            # Reusable object pooling
│   ├── Prefabs/
│   │   ├── Player.prefab                # Player GameObject template
│   │   ├── Enemy.prefab                 # Enemy GameObject template
│   │   ├── Projectile.prefab            # Bullet/projectile prefab
│   │   └── ...
│   ├── Sprites/
│   │   ├── Player/                      # Character graphics
│   │   ├── Enemy/                       # Enemy graphics
│   │   ├── UI/                          # UI elements
│   │   └── Background/                  # Environment art
│   ├── Audio/
│   │   ├── SFX/                         # Sound effects
│   │   └── Music/                       # Background music
│   ├── Materials/
│   │   └── ...                          # Shaders and materials (if 3D)
│   └── ...
├── Packages/                            # Unity Package Manager dependencies
├── ProjectSettings/                     # Unity Editor settings
├── .gitattributes                       # Git LFS configuration for large files
├── .gitignore                           # Version control exclusions
└── README.md                            # This file
```

---

## Core Systems

### Player Controller
**File:** `Assets/Scripts/Player/PlayerController.cs`

Handles:
- Keyboard input (Arrow keys / WASD)
- Character movement and velocity
- Animation state transitions
- Ground detection for jumping

**Example Usage:**
```csharp
public class PlayerController : MonoBehaviour
{
    public float moveSpeed = 5f;
    public float jumpForce = 5f;
    
    void Update() => HandleInput();
    void FixedUpdate() => ApplyMovement();
}
```

### Game Manager
**File:** `Assets/Scripts/Game/GameManager.cs`

Manages:
- Game state (playing, paused, game-over)
- Score and lives tracking
- Level progression
- Scene transitions

**Example Usage:**
```csharp
public class GameManager : MonoBehaviour
{
    public static GameManager Instance { get; private set; }
    
    public void GameOver() { /* Handle game end */ }
    public void AddScore(int points) { /* Update score */ }
}
```

### Enemy AI
**File:** `Assets/Scripts/Enemy/EnemyController.cs`

Features:
- Simple state-based behavior (patrol, chase, attack)
- Collision response
- Death/despawn logic

---

## Gameplay Loop

1. **Initialize:** Load scene, spawn player, position enemies
2. **Player Input:** Read keyboard/gamepad input each frame
3. **Physics Update:** Calculate movement, apply forces, detect collisions
4. **Game Logic:** Check win/lose conditions, update score
5. **Render:** Draw sprites, UI, and camera updates
6. **Repeat** until game-over or level complete

---

## How to Play

### Controls
| Input | Action |
|-------|--------|
| **Arrow Keys / WASD** | Move left/right |
| **Space / W** | Jump |
| **Mouse / Ctrl** | Shoot / Interact |
| **ESC** | Pause / Menu |

### Objective
- **Goal:** [Describe primary objective - e.g., "Defeat all enemies" or "Reach the end of the level"]
- **Lives:** You have [X] lives; game ends when depleted
- **Scoring:** Earn points by [describe point mechanics]

---

## Development Guidelines

### Adding New Features

#### New Enemy Type
1. Create script: `Assets/Scripts/Enemy/NewEnemyType.cs`
2. Inherit from `EnemyController`
3. Override behavior methods: `Chase()`, `Attack()`, `Die()`
4. Create prefab in `Assets/Prefabs/`
5. Register in `EnemySpawner.cs`

#### New Weapon/Ability
1. Create script: `Assets/Scripts/Player/Abilities/NewAbility.cs`
2. Implement firing logic and cooldown
3. Wire to input handler: `InputHandler.cs`
4. Test in MainScene

### Code Standards
- **Naming:** PascalCase for classes, camelCase for variables
- **Comments:** Document complex logic and public APIs
- **Physics:** Use `Rigidbody` for physics objects; avoid direct `Transform` for physics entities
- **Prefabs:** Keep scripts parameterized (expose values in Inspector)

### Performance Optimization
- **Object Pooling:** Reuse bullets/enemies instead of Instantiate/Destroy
- **Update vs FixedUpdate:** Physics in FixedUpdate, input in Update
- **Culling:** Disable off-screen enemy scripts via frustum culling

---

## Known Limitations

- **Single-Player Only:** No multiplayer support
- **Basic AI:** Enemy pathfinding uses simple waypoint following, not advanced pathfinding
- **Limited Platforms:** Tested on Windows and macOS; mobile deployment requires UI scaling
- **No Save System:** Game progress is not persisted between sessions (if applicable)

---

## Future Enhancements

- [ ] **Advanced AI:** A* pathfinding for intelligent enemy movement
- [ ] **Level Design:** Multiple levels with progressive difficulty
- [ ] **Power-ups:** Health restore, temporary invincibility, weapon upgrades
- [ ] **Particle Effects:** Visual feedback for collisions and attacks
- [ ] **Sound Design:** Background music and dynamic sound effects
- [ ] **Leaderboard:** High score tracking and replay system
- [ ] **Mobile Support:** Touch controls and responsive UI for Android/iOS

---

## Troubleshooting

### "Import Error: Scripts fail to compile"
- **Fix:** Ensure Unity version 2022.3+ is installed
- Check Console for detailed C# compile errors
- Delete `Library/` folder and reimport: `Assets → Reimport All`

### "Game runs slowly or stutters"
- Check Profiler: **Window → Analysis → Profiler**
- Look for frame rate drops in CPU or GPU time
- Reduce enemy count or disable unnecessary updates

### "Physics behaves unexpectedly (clipping, excessive bouncing)"
- Verify Rigidbody settings: Body Type, Gravity Scale, Drag
- Check collision matrix: **Edit → Project Settings → Physics 2D**
- Increase Fixed Timestep precision if needed

### "Input not responding"
- Ensure `InputHandler` or `EventSystem` is in the scene
- Check Input settings: **Edit → Project Settings → Input Manager**
- Verify key bindings are not overridden

### "Game won't build"
- Delete `Library/`, `Temp/`, and `obj/` directories
- Rebuild Unity cache: **File → New Input System** (if applicable)
- Check for assembly definition (.asmdef) conflicts

---

## References & Learning Resources

- **Unity Manual:** [docs.unity3d.com](https://docs.unity3d.com)
- **Physics 2D Guide:** [Unity 2D Physics Reference](https://docs.unity3d.com/Manual/2D.html)
- **C# Scripting:** [C# Language Official Documentation](https://learn.microsoft.com/en-us/dotnet/csharp/)

---

## License

This project is developed for educational purposes as part of a university curriculum or personal portfolio.

---

## Contact

For questions or feedback about this game project:

**GitHub:** [VanThai42/A-simple-Java-game](https://github.com/VanThai42/A-simple-Java-game)

---

## Version History

| Version | Date | Notes |
|---------|------|-------|
| 1.0 | 2024 | Initial release |
