# 📦 SimPL-Libraries

> The official, zero-infrastructure package registry for the SimPL programming language.

## What is SimPL-Libraries?

SimPL-Libraries is a revolutionary approach to package management that eliminates the need for expensive servers, complex infrastructure, and centralized databases. Instead, we leverage **GitHub Issues** as our package registry.

### Why GitHub Issues?

- **💰 Zero Server Costs**: No hosting fees, no database bills, no maintenance overhead.
- **📜 Built-in Version History**: Every issue edit is tracked by Git. Full audit trail, forever.
- **💬 Community Discussion**: Users can comment on issues to report bugs, request features, or ask questions.
- **🔍 Powerful Search**: GitHub's search engine helps users discover libraries by name, tags, or content.
- **✅ Automated Validation**: Our YAML template enforces strict formatting so our Python package manager can parse submissions flawlessly.

This is package management, simplified. No bloat, no complexity—just pure community-driven code sharing.

---

## How to Publish a Library

Publishing your SimPL library takes less than 5 minutes:

### Step 1: Write Your Code

Create your `.simpl` library file following the [Library Standards](#library-standards--rules). Make sure it's well-documented and tested.

### Step 2: Click "New Issue"

Navigate to the [Issues tab](../../issues) of this repository and click **"New Issue"**.

### Step 3: Select the Template

Choose **"📦 Library Submission"** from the template list. This will load our strict validation form.

### Step 4: Fill Out the Form

Complete all required fields:

| Field | Description |
|-------|-------------|
| **Package Name** | Lowercase, hyphens allowed (e.g., `super-math`) |
| **Version** | Semantic versioning (e.g., `1.0.0`) |
| **Author** | Your GitHub username |
| **License** | MIT, Apache-2.0, GPL-3.0, or Unlicense |
| **Description** | Brief summary (max 150 chars) |
| **Dependencies** | Other SimPL packages you depend on |
| **Tags** | Keywords for discoverability |
| **Code** | Your complete SimPL source code |
| **Documentation** | Installation, Usage, and API Reference |
| **Changelog** | What's new in this version |

### Step 5: Submit

Check all the boxes in the Submission Checklist and click **"Submit new issue"**.

Your library will be reviewed by maintainers and added to the registry!

---

## Library Standards & Rules

To maintain quality and safety in the SimPL ecosystem, all submissions must follow these rules:

### ✅ Required Standards

1. **Pure SimPL Only**
   - All code must be written in standard SimPL syntax.
   - No FFI, no external binaries, no polyglot hacks.

2. **No Malicious Code**
   - Absolutely no system calls that could harm users.
   - No network requests without explicit user consent.
   - No file system manipulation beyond what's documented.

3. **Beginner-Friendly**
   - Code should be readable and well-commented.
   - Avoid overly clever or obfuscated solutions.
   - Follow SimPL style conventions.

4. **Complete Documentation**
   - Every public function must have a docstring.
   - Include usage examples in your submission.
   - Document all parameters and return values.

5. **Proper Licensing**
   - Choose from: MIT, Apache-2.0, GPL-3.0, or Unlicense.
   - Include a license header in your source file.
   - Respect third-party licenses if using ideas from other projects.

### ❌ Prohibited Content

- Cryptocurrency miners or blockchain code
- Malware, viruses, or exploit tools
- Hate speech, harassment, or discriminatory content
- Plagiarized or copyright-infringing code
- Spam or duplicate submissions

Violations will result in immediate issue closure and potential ban from the registry.

---

## How to Install

Once a library is published, installing it is as simple as:

```bash
simpl install <package_name>
```

### Examples

```bash
# Install the latest version
simpl install super-math

# Install a specific version
simpl install super-math@1.0.0

# Install multiple packages at once
simpl install super-math http-client json-utils
```

The `simpl` CLI will:
1. Fetch the library metadata from the GitHub Issue
2. Download the source code from the issue body
3. Resolve and install any dependencies
4. Add the package to your `simpl.json` manifest

---

## 📚 Example Libraries

Check out our [`examples/`](./examples/) directory for gold-standard library implementations:

- [`examples/gold_standard/super-math.simpl`](./examples/gold_standard/super-math.simpl) - A complete mathematical utilities library

---

## 🔧 For Package Manager Developers

If you're building a tool to parse SimPL-Libraries submissions, here's what you need to know:

### Issue Format

Each library submission follows a strict structure:

```markdown
### Package Name
<value>

### Version
<value>

### Author
<value>

...
```

### Parsing Tips

1. Use GitHub's GraphQL API to fetch issues with the `library-submission` label.
2. Parse the form fields from the issue body—they follow a predictable `### Field Name` pattern.
3. Extract the code block marked with ```simpl syntax highlighting.
4. Validate the semantic version before caching.

---

## 🤝 Contributing

Found a bug in a library? Comment on its issue!

Want to suggest improvements to this registry? Open an issue with the **"meta"** label.

---

## 📄 License

This registry infrastructure is licensed under the **MIT License**.

Individual libraries are licensed by their respective authors—check each library's issue for details.

---

**Happy coding in SimPL! 🚀**
