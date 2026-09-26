# C++ Architecture Journey — 6 Month Mentorship Log

> Goal: Go from "I know C++ syntax" to "I can design systems that survive
> a team, a deadline, and six months of feature creep."
>
> Format: 4 hrs/day, ~5 days/week, 6 months (~130 sessions)
> Mentor philosophy: concept → real-world reasoning → code → project → review

## How This Repo Works
- Each day gets a folder: `/days/dayNN-topic/`
- Each day: notes.md (what I learned) + code (what I built) + at least one
  "why" question answered in my own words.
- Evlery Friday: retro.md — what broke, what I'd do differenty.
- Every project lives in `/projects/`.

## Tools (Set up Day 0)
- [ ] GCC 12+ or Clang 15+
- [ ] CMake 3.25+
- [ ] Git
- [ ] VS Code + clangd, or Qt Creator
- [ ] vcpkg (installed, not necessarily used yet)
- [ ] Catch2 or GoogleTest
- [ ] Qt 6.x (needed from Month 3 onward)

---

## MONTH 1 — Modern C++ Foundations & Ownership
**Mission:** Understand *who owns what and for how long*. This is the #1
root cause of real-world C++ bugs and bad architecture.

### Week 1 — RAII & Move Semantics Mental Model
- [ ] Day 1: Course kickoff. Stack vs heap mental model. Why "ownership" is the central question in C++.
- [ ] Day 2: RAII deep dive — file handles, mutexes, sockets. Build a RAII FileGuard.
- [ ] Day 3: Lvalues, rvalues, and why they exist. Copy vs move — the cost story.
- [ ] Day 4: Move constructors/assignment, `std::move`, Rule of 0/3/5.
- [ ] Day 5: Practice + mini quiz. Build a move-aware `Buffer` class.

### Week 2 — Smart Pointers & Ownership Models
- [ ] Day 6: `unique_ptr` — exclusive ownership, custom deleters.
- [ ] Day 7: `shared_ptr`/`weak_ptr` — ref counting, breaking cycles.
- [ ] Day 8: Raw pointers & references — non-owning access, when smart pointers are *wrong*.
- [ ] Day 9: Design exercise — model a "Library" with Book/Member ownership graph.
- [ ] Day 10: Review + refactor exercise + quiz.

### Week 3 — Modern Utility Types
- [ ] Day 11: `std::optional` — nullable returns without null pointers.
- [ ] Day 12: `std::variant` + `std::visit` — type-safe unions.
- [ ] Day 13: `std::span` — safe views over arrays/vectors.
- [ ] Day 14: `constexpr` and compile-time computation.
- [ ] Day 15: C++20 concepts — constraining templates meaningfully.

### Week 4 — Memory & Performance Mental Model
- [ ] Day 16: Stack vs heap layout, cache lines, memory locality basics.
- [ ] Day 17: Why `vector` beats `list` — benchmark it yourself.
- [ ] Day 18: Small object/string optimization (SSO).
- [ ] Day 19: Virtual dispatch cost — vtables, when to avoid on hot paths.
- [ ] Day 20: Week review — benchmarking mini-project (vector vs list vs deque).

---

## MONTH 2 — Professional Tooling & CLI Project
**Mission:** Learn to build like a professional, not a student — proper structure,
build system, tests from day one.

### Week 5 — Project Scaffolding
- [ ] Day 21: Header/source structure, include guards vs `#pragma once`.
- [ ] Day 22: CMake basics — executables, libraries, targets.
- [ ] Day 23: CMake PUBLIC/PRIVATE/INTERFACE (intro pass).
- [ ] Day 24: `.clang-format`, clang-tidy static analysis.
- [ ] Day 25: Catch2/GoogleTest setup — first real unit tests.

### Weeks 6–8 — PROJECT 1: CLI Task Manager
- [ ] Day 26: Requirements + architecture sketch (domain model: Task, TaskManager).
- [ ] Day 27: `Task` class — RAII-correct design + tests.
- [ ] Day 28: `TaskManager` (add/remove/list) + tests.
- [ ] Day 29: Persistence interface design (future-proofing for swap).
- [ ] Day 30: JSON serialization via `nlohmann/json` (CMake FetchContent).
- [ ] Day 31: CLI argument parsing.
- [ ] Day 32: Error handling strategy doc — exceptions vs `optional`/`expected`.
- [ ] Day 33: Search/filter features + tests.
- [ ] Day 34: Refactor pass with clang-tidy.
- [ ] Day 35: Docs + ship v1.
- [ ] Day 36–40: Buffer/catch-up + write an ADR (Architecture Decision Record) for this project.

---

## MONTH 3 — Design Principles, Applied
**Mission:** Patterns as tools, not trivia.

### Week 9 — SOLID
- [ ] Day 41: SRP with a real refactor.
- [ ] Day 42: OCP via Strategy pattern.
- [ ] Day 43: LSP — inheritance pitfalls.
- [ ] Day 44: ISP.
- [ ] Day 45: DIP — the most important one for testability.

### Week 10 — GoF Patterns That Matter
- [ ] Day 46: Factory (simple + abstract).
- [ ] Day 47: Strategy (deeper).
- [ ] Day 48: Observer (foundation for Qt signals/slots).
- [ ] Day 49: Pimpl — ABI stability & compile firewalls.
- [ ] Day 50: Adapter & Command.

### Week 11 — Dependency Injection & Testability
- [ ] Day 51: Constructor injection deep dive.
- [ ] Day 52: Interfaces via abstract base classes — designing seams.
- [ ] Day 53: GoogleMock intro.
- [ ] Day 54: Refactor exercise for testability.
- [ ] Day 55: Review + design discussion.

### Week 12 — PROJECT 1 Rebuild: Layered Architecture
- [ ] Day 56–60: Rebuild Task Manager — core lib (zero I/O deps), Repository interface,
  app shell, DI wiring, full mock-based test suite.

---

## MONTH 4 — Qt/QML Architecture

### Week 13 — Qt Fundamentals
- [ ] Day 61: Qt install, Widgets vs QML, meta-object system & moc.
- [ ] Day 62: QObject — parent/child ownership model.
- [ ] Day 63: Signals & slots basics.
- [ ] Day 64: Queued vs direct connections, thread affinity.
- [ ] Day 65: First QML app.

### Week 14 — MVVM
- [ ] Day 66: MVVM theory — why separate layers.
- [ ] Day 67: `Q_PROPERTY`/`Q_INVOKABLE` deep dive.
- [ ] Day 68: qmlRegisterType vs context properties vs singletons.
- [ ] Day 69: `QAbstractListModel` for lists.
- [ ] Day 70: Mini MVVM demo (counter/todo).

### Weeks 15–16 — PROJECT 2: Notes/Dashboard App
- [ ] Day 71–80: Architecture design → domain (Note, NoteRepository interface) →
  SQLite via Qt SQL → ViewModel layer → QML UI → list model → CRUD → tests → polish.

---

## MONTH 5 — Real-World Engineering

### Week 17 — Build Systems Deep Dive
- [ ] Day 81: PUBLIC/PRIVATE/INTERFACE mastery.
- [ ] Day 82: vcpkg/Conan.
- [ ] Day 83: Out-of-source builds, build types.
- [ ] Day 84: Cross-compilation basics.
- [ ] Day 85: CPack packaging intro.

### Week 18 — ABI & Threading
- [ ] Day 86: ABI stability, Pimpl revisited.
- [ ] Day 87: Qt threading rules.
- [ ] Day 88: QThread vs QtConcurrent.
- [ ] Day 89: Cause and fix a real race condition.
- [ ] Day 90: Thread-safe Qt design patterns.

### Week 19 — Debugging & Tooling
- [ ] Day 91: gdb/lldb.
- [ ] Day 92: Valgrind/ASan.
- [ ] Day 93: Profiling (perf, Qt Creator profiler).
- [ ] Day 94: Core dumps.
- [ ] Day 95: Fix an intentionally broken program.

### Week 20 — Testing at Scale & Refactoring
- [ ] Day 96: Unit vs integration strategy.
- [ ] Day 97: GoogleMock deep dive.
- [ ] Day 98: Test doubles for Qt objects.
- [ ] Day 99: Refactor a messy codebase into layers.
- [ ] Day 100: Retro on months 1–5.

---

## MONTH 6 — Capstone & Breadth

### Weeks 21–24 — PROJECT 3 (Capstone)
Pick one: Media Library Manager / Personal Finance Tracker / Habit Tracker with sync.
- [ ] Day 101–105: Architecture doc, module boundaries.
- [ ] Day 106–115: Core domain + business logic (TDD).
- [ ] Day 116–120: QML UI + ViewModels.
- [ ] Day 121–125: Persistence + background threading.
- [ ] Day 126–130: Tests, CI (GitHub Actions, 2 platforms), CPack packaging.

### Weeks 25–26 — Breadth
- [ ] Study a real Qt/KDE open-source codebase — trace module structure.
- [ ] Practice design discussions: "How would you structure a media player?"
  "How would you add plugin support?"
- [ ] Final retro + plan next 6 months.

---

## The Two Habits That Matter Most
> Most architectural damage comes from **unclear ownership** (who deletes what,
> and when) and **leaky abstractions** (UI reaching into business logic).
> Keep core logic framework-free. Keep ownership explicit. Always.
