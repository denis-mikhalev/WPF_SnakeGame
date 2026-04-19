# 🐍 WPF Snake Game

![.NET Framework](https://img.shields.io/badge/.NET_Framework-4.x-512BD4?logo=dotnet&logoColor=white)
![C#](https://img.shields.io/badge/C%23-239120?logo=csharp&logoColor=white)
![WPF](https://img.shields.io/badge/WPF-0078D4?logo=windows&logoColor=white)
![Pattern](https://img.shields.io/badge/Pattern-MVVM-blueviolet)
![Platform](https://img.shields.io/badge/Platform-Windows-0078D4?logo=windows&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-yellow)

A classic Snake game built with **WPF** and the **MVVM** pattern. The snake moves on a timer, grows on eating food, and speeds up with every meal — all rendered via data-bound `ItemsControl` on a `Canvas`, with zero code in the code-behind.

---

## Demo

> **Add a GIF here to make this README stand out!**
>
> **How to record a GIF in 2 minutes:**
> 1. Download [ScreenToGif](https://www.screentogif.com/) (free, no install required)
> 2. Launch the app → click **Recorder** → resize the frame over the game window
> 3. Press **F7** to start recording, play the game, press **F8** to stop
> 4. Click **File → Save As** → choose **GIF** → save as `assets/demo.gif`
> 5. Replace this block with: `![Demo](assets/demo.gif)`

---

## Features

- 🟩 Snake grows and speeds up on every food eaten
- 🎨 Checkerboard grid rendered entirely via WPF data binding
- ⌨️ Arrow key controls bound via `KeyBinding` commands
- ⚡ `DispatcherTimer`-driven game loop (UI-thread safe, no cross-thread issues)
- 🏗️ Clean MVVM — code-behind contains only `DataContext = new GameViewModel()`

---

## Architecture

The project follows the **MVVM** pattern:

| Layer | File(s) | Responsibility |
|---|---|---|
| **View** | `MainWindow.xaml` | `ItemsControl` + `Canvas` renders all game objects via `DataTemplate` |
| **ViewModel** | `GameViewModel.cs` | Game state, timer, movement logic, commands |
| **Commands** | `RelayCommand.cs` | Lightweight `ICommand` wrapper |
| **Model** | `Figure`, `SnakePart`, `Food`, `RectField` | Data entities with `INotifyPropertyChanged` |

All game objects (background tiles, snake parts, food) live in a single `ObservableCollection<Figure>` — WPF's binding engine handles rendering automatically.

---

## Tech Stack

- **C#** / **.NET Framework 4.x**
- **WPF** — `Canvas`, `ItemsControl`, `DataTemplate`, `KeyBinding`
- **MVVM** — `INotifyPropertyChanged`, `ICommand`, `ObservableCollection`
- **DispatcherTimer** — game loop on the UI thread

---

## Getting Started

```bash
git clone https://github.com/<your-username>/WPF_SnakeGame.git
```

1. Open `WpfSnake/WpfSnake.sln` in **Visual Studio 2019+**
2. Press **F5** to build and run
3. Use **arrow keys** to steer the snake

---

## Project Structure

```
WpfSnake/
├── Model/
│   ├── Figure.cs          # Base class: position, color, size
│   ├── SnakePart.cs       # Extends Figure — marks the head
│   ├── Food.cs            # Extends Figure — red tile
│   └── RectField.cs       # Extends Figure — background grid tile
├── ViewModel/
│   ├── GameViewModel.cs   # Game loop, state, commands
│   └── RelayCommand.cs    # ICommand implementation
├── MainWindow.xaml        # View — Canvas + ItemsControl
└── MainWindow.xaml.cs     # DataContext assignment only
```

---

## License

[MIT](LICENSE) © 2026 Denis Mikhalev
