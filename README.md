# AI.TM

AI.TM is a modular, AI-powered desktop operating environment designed for productivity, idea synthesis, document summarization, and lightweight data analysis — all powered by local large language models. This WPF-based application leverages **Ollama** for AI, **ArangoDB** for graph-aware storage, and a plugin architecture for extensibility.

---

## ✨ Features

- 💬 **Command Console**: Interact with local LLMs via natural language.
- ✅ **Task Manager**: Manage tasks synthesized from documents or input.
- 🔌 **Plugin Manager**: Extend functionality via custom plugins (e.g., email summarization).
- ⚙️ **Settings Panel**: Configure models, database endpoints, themes, and more.

---

## 🧱 Project Structure

```bash
AIOperatingSystem/
├── AIOperatingSystem.UI        # WPF frontend (MVVM)
├── AIOperatingSystem.Core      # Business logic (AI, DB, Plugin services)
├── AIOperatingSystem.Plugins   # Plugin interface and default plugins
├── AIOperatingSystem.Tests     # Unit and integration tests
```

---

## 🚀 Getting Started

### Prerequisites

- [.NET 9.0 SDK](https://dotnet.microsoft.com/)
- [Ollama](https://ollama.com/) (for local LLMs like LLaMA3)
- [ArangoDB](https://www.arangodb.com/) (run locally or in Docker)

### Setup

1. **Clone the repo**
   ```bash
   git clone https://github.com/your-org/AIOperatingSystem.git
   cd AIOperatingSystem
   ```

2. **Install Ollama and load model**
   ```bash
   ollama run llama3
   ```

3. **Start ArangoDB locally**
   ```bash
   docker run -e ARANGO_ROOT_PASSWORD=root -p 8529:8529 arangodb
   ```

4. **Launch the app**
   Open `AIOperatingSystem.sln` in Visual Studio and run the `AIOperatingSystem.UI` project.

---

## 🧠 Plugin System

Create a plugin by implementing the `IPlugin` interface:

```csharp
public interface IPlugin
{
    string Name { get; }
    string Version { get; }
    string Description { get; }
    Task<PluginResult> ExecuteAsync(object input);
}
```

Drop your plugin DLL in the `/Plugins` folder. The app will load and execute it dynamically.

---

## 🧪 Testing

- Run tests with your preferred test runner (`dotnet test`).
- Integration tests connect to local Ollama and ArangoDB.
- Use Testcontainers if needed for full isolation.

---

## 📦 Roadmap

- [x] Ollama + ArangoDB integration
- [x] Modular plugin system
- [x] Local-only privacy-first design
- [ ] Natural language task planning
- [ ] Graph-based data visualization
- [ ] Plugin marketplace (WIP)

---

## 📄 License

MIT License — see `LICENSE` for details.

---

## 🤝 Contributing

Pull requests and ideas are welcome! If you're interested in building plugins or core features, please open an issue or draft a PR.
