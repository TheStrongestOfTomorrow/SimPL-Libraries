<div align="center">

# SimPL-Libraries

**The Community Package Registry for [SimPL](https://github.com/TheStrongestOfTomorrow/SimPL)**

*Publish. Install. Share.*

[![SimPL](https://img.shields.io/badge/SimPL-0.8.0-blue.svg)](https://github.com/TheStrongestOfTomorrow/SimPL)
[![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Packages](https://img.shields.io/badge/packages-community-orange.svg)](#-available-packages)

[Quick Start](#quick-start) · [Available Packages](#-available-packages) · [Publish a Package](#publishing-a-package) · [Install a Package](#installing-a-package) · [Guidelines](#package-guidelines)

</div>

---

SimPL-Libraries is the official community package registry for the SimPL programming language. Packages are hosted as **GitHub Issues** in this repository — no separate registry server, no authentication, no build step. Just open an Issue and your package is available to every SimPL user worldwide.

---

## Table of Contents

- [Quick Start](#quick-start)
- [How It Works](#how-it-works)
- [📦 Available Packages](#-available-packages)
- [Installing a Package](#installing-a-package)
- [Publishing a Package](#publishing-a-package)
- [Package Format](#package-format)
- [Package Guidelines](#package-guidelines)
- [FAQ](#faq)
- [License](#license)

---

## Quick Start

**Install and use a package in 30 seconds:**

```bash
# 1. Install a package
python simpl.py install super-math

# 2. Use it in your SimPL code
```

```simpl
import super-math

let result = super-math.add(10, 20)
print result  # 30
```

That's it! Browse all packages below or in the [Issues tab](https://github.com/TheStrongestOfTomorrow/SimPL-Libraries/issues?q=is%3Aissue+is%3Aopen).

> **Tip**: You can also install packages from the **TUI** — launch `python simpl.py` and use the built-in package menu to browse and install without leaving the interface.

---

## How It Works

The SimPL package manager reads GitHub Issues from this repository to find and install packages. Each Issue represents one package. The Issue body contains YAML metadata (name, version, dependencies) and the SimPL source code in a fenced code block.

When a user runs `simpl install <package-name>`, the package manager:

1. Searches this repo's Issues for an open Issue matching the package name
2. Reads the YAML frontmatter for metadata and dependencies
3. Extracts the SimPL code block
4. Saves the code locally to `./libs/<package-name>/<package-name>.simpl`
5. Recursively installs any declared dependencies
6. Updates `simpl.lock` with the installation record

There is no central server, no authentication, and no build pipeline. GitHub Issues *are* the registry.

---

## 📦 Available Packages

> **Note**: This section is manually updated. For the full, always-up-to-date list, check the [Issues tab](https://github.com/TheStrongestOfTomorrow/SimPL-Libraries/issues?q=is%3Aissue+is%3Aopen).

### Official Packages

| Package | Version | Description |
|---------|---------|-------------|
| `super-math` | 2.0.0 | Enhanced math functions: add, subtract, multiply, divide, power, max, min, abs, sqrt, floor, ceil, round, average, sum, median, clamp, lerp, factorial |
| `string-utils` | 2.0.0 | String utility functions: uppercase, lowercase, length, capitalize, reverse, contains, starts_with, ends_with, trim, replace, repeat, word_count |
| `io-utils` | 1.5.0 | File I/O utilities: read, write, append, read_lines, write_lines, copy, file_size |
| `list-tools` | 1.5.0 | Advanced list operations: reverse, sort, contains, index_of, unique, flatten, chunk, take, drop |
| `color-kit` | 1.0.0 | Terminal color output: red, green, yellow, blue, magenta, cyan, bold, underline, dim, rainbow |
| `http-client` | 1.0.0 | HTTP client utilities: get_json, post_json, is_success, status_ok, status_not_found |
| `json-tools` | 1.0.0 | JSON manipulation utilities: parse, stringify, compact, get_path, set_path, merge, save, load |

### Community Packages

Community packages are published by users like you! Browse them all in the [Issues tab](https://github.com/TheStrongestOfTomorrow/SimPL-Libraries/issues?q=is%3Aissue+is%3Aopen).

*Want to see your package listed here? Publish it and open a PR to update this table!*

---

## Installing a Package

### From the Command Line

From the SimPL project directory:

```bash
# Install a community package
python simpl.py install <package-name>

# Example
python simpl.py install super-math
```

Then use it in your SimPL code:

```simpl
import super-math

let result = super-math.add(10, 20)
print result  # 30
```

### From the TUI

Launch the SimPL TUI and use the built-in package menu to browse and install packages interactively — no need to remember package names or leave the interface:

```bash
python simpl.py
# Navigate to the package menu from the TUI home screen
```

### Managing Installations

```bash
python simpl.py list                       # List all installed packages
python simpl.py uninstall <package-name>   # Remove a package
```

### Offline / Mock Mode

If you don't have internet access, you can install packages using built-in mock data (available for select packages):

```bash
python simpl.py install super-math --mock
```

---

## Publishing a Package

Anyone can publish a package by opening a GitHub Issue in this repository. Here's how:

### Step 1: Write Your Package

Create your SimPL code. Follow the naming convention `<package-name>.<function-name>` for exported functions:

```simpl
# my-greeter package
function my-greeter.hello(name)
    return "Hello, " + name + "!"
end

function my-greeter.goodbye(name)
    return "Goodbye, " + name + "!"
end

let my-greeter.version = "1.0.0"
```

### Step 2: Create the Issue

1. Go to [Issues → New Issue](https://github.com/TheStrongestOfTomorrow/SimPL-Libraries/issues/new/choose) and select the **Package Submission** template
2. Set the **title** to your exact package name (e.g., `my-greeter`)
3. Add the YAML frontmatter and code block (see [Package Format](#package-format) below)
4. Submit the Issue

That's it! Your package is now installable by anyone.

### Step 3: Verify

Test that it works:

```bash
python simpl.py install my-greeter
```

Then create a test script:

```simpl
import my-greeter

print my-greeter.hello("World")
```

```bash
python simpl.py run test.simpl
```

---

## Package Format

Every package Issue must follow this format:

```markdown
---
name: package-name
version: 1.0.0
dependencies: []
author: YourName
description: A short description of what the package does
---

```simpl
# Your SimPL code here
function package-name.feature()
    return "Hello!"
end
```
```

### YAML Frontmatter Fields

| Field | Required | Description |
|-------|----------|-------------|
| `name` | Yes | The package name (must match the Issue title). Use lowercase with hyphens. |
| `version` | Yes | Semantic version (e.g., `1.0.0`, `0.2.1`). |
| `dependencies` | Yes | List of other SimPL packages this one needs. Use `[]` if none. |
| `author` | No | Your name or GitHub username. |
| `description` | No | Short description of the package. |

### Code Block

- Must be enclosed in triple backticks with the `simpl` language tag
- Can contain any valid SimPL code: functions, variables, constants
- Package code can use **any SimPL syntax flavor** (default, Python-style, Ruby-style, etc.) — choose whichever you prefer, but use it consistently within a single package
- Follow the `package-name.function-name` naming convention to avoid collisions

---

## Package Guidelines

### Naming Conventions

- **Package names**: lowercase with hyphens (e.g., `super-math`, `string-utils`, `http-client`)
- **Exported functions**: prefix with `package-name.` (e.g., `super-math.add`, `string-utils.uppercase`)
- **Version constants**: define `package-name.version` for version tracking

### Best Practices

1. **Keep it focused** — Each package should do one thing well. If your package has math utilities *and* string utilities, split them into `super-math` and `string-utils`.

2. **Declare dependencies** — If your package uses functions from another SimPL-Libraries package, list it in the `dependencies` field. The package manager will install them automatically.

3. **Document your API** — Add comments in your code explaining what each function does, its parameters, and return values. Users will read the Issue to understand how to use your package.

4. **Version your changes** — When updating a package, edit the Issue body and bump the `version` field. Users will get the latest version when they install.

5. **Test before publishing** — Run your package locally with `python simpl.py run test.simpl` before opening the Issue. Use `--mock` mode to test without network if needed.

6. **Pick one syntax flavor per package** — While package code can use any SimPL syntax flavor, choose one and use it consistently throughout your package for readability.

### What NOT to Publish

- **Single-function packages** — Unless the function is genuinely complex (e.g., a full JSON parser), consider grouping related functions into a larger package.
- **Packages that wrap `js_eval()` only** — If your package is just a thin wrapper around `js_eval("require('some-npm-package')")`, users can do that directly. Reserve SimPL-Libraries for native SimPL code.
- **Offensive or malicious code** — Packages containing harmful, offensive, or deliberately broken code will be closed and removed.

---

## FAQ

### How is this different from NPM or PyPI?

SimPL-Libraries uses GitHub Issues as the registry — there's no separate server, no CLI login, and no build pipeline. It's designed for simplicity and accessibility, matching SimPL's philosophy. For heavy-duty JavaScript packages, use the [NPM Bridge](https://github.com/TheStrongestOfTomorrow/SimPL#npm-bridge) instead.

### Can I install a specific version?

Currently, the package manager always installs the latest version (the current state of the Issue). Pinning to specific versions is on the roadmap.

### What if a package has a bug?

Open a comment on the package's Issue describing the bug. The package author can then edit the Issue body to fix the code.

### Can I delete my package?

Close the Issue. Closed Issues are not indexed by the package manager, so the package becomes unavailable. You can reopen it later if needed.

### Can I install packages from the TUI?

Yes! Launch `python simpl.py` and navigate to the package menu from the TUI home screen. You can browse available packages and install them directly without using the command line.

### What about NPM packages?

NPM packages are installed separately using the `npm:` prefix:

```bash
python simpl.py install npm:lodash
```

See the [main SimPL README](https://github.com/TheStrongestOfTomorrow/SimPL#npm-bridge) for details on the NPM Bridge.

---

## License

SimPL-Libraries is released under the [MIT License](LICENSE). A copy of the license is included in the repository. Individual packages may have their own licenses — check the package's Issue for details.

Copyright (c) 2024-2026 TheStrongestOfTomorrow
