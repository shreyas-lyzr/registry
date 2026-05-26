# SwiftUI Agent Skill

**Author:** [Paul Hudson (@twostraws)](https://github.com/twostraws)  
**Repository:** https://github.com/twostraws/SwiftUI-Agent-Skill  
**License:** MIT  
**Targets:** iOS 26+ · Swift 6.2+  

---

A comprehensive SwiftUI code-review agent skill for Claude Code, Codex, Gemini,
Cursor, and other AI coding assistants. Built on thousands of hours of real-world
SwiftUI experience, this skill directly targets the mistakes LLMs *actually* make
when writing SwiftUI code.

## What It Reviews

| Area | Examples |
|---|---|
| **Deprecated API** | `foregroundColor()` → `foregroundStyle()`, legacy `NavigationView` |
| **Views & Modifiers** | Redundant modifiers, animation API correctness |
| **Data Flow** | `@State`, `@Binding`, `@Observable`, `@StateObject` / `@ObservedObject` |
| **Navigation** | `NavigationStack` / `NavigationSplitView` patterns |
| **Design (HIG)** | Apple Human Interface Guidelines compliance |
| **Accessibility** | VoiceOver labels, Dynamic Type, Reduce Motion |
| **Performance** | Expensive view-body computations, `task(id:)` usage |
| **Swift** | Modern Concurrency, Swift 6.2+ idioms |
| **Hygiene** | One type per file, naming, clean compilation |

## Usage

**Claude Code:**
```
/swiftui-pro
/swiftui-pro Check for deprecated API
/swiftui-pro Focus on accessibility
```

**Codex:**
```
$swiftui-pro
$swiftui-pro Focus on performance
```

**Install via npx:**
```bash
npx skills add https://github.com/twostraws/swiftui-agent-skill --skill swiftui-pro
```

**Claude Code Marketplace:**
```
/plugin marketplace add twostraws/SwiftUI-Agent-Skill
/plugin install swiftui-pro@swiftui-agent-skill
```

## Output Format

Findings are organised by file. Each issue includes:
1. File name and relevant line(s)
2. The rule being violated
3. A before/after code fix

The review ends with a prioritised summary of the most impactful changes to make first.

## Related Skills

- [SwiftData Pro](https://github.com/twostraws/SwiftData-Agent-Skill)
- [Swift Concurrency Pro](https://github.com/twostraws/Swift-Concurrency-Agent-Skill)
- [Swift Testing Pro](https://github.com/twostraws/Swift-Testing-Agent-Skill)

---

*Part of the [Swift Agent Skills](https://github.com/twostraws/Swift-Agent-Skills) collection.*
