---
Task ID: 1
Agent: Main Agent
Task: Build the NPM Bridge feature for SimPL - update package_manager.py, create core/js_bridge.py, update core/parser.py, create examples/test_npm.simpl, and update simpl.py CLI

Work Log:
- Cloned the SimPL repository from github.com/thestrongestoftomorrow/SimPL
- Explored the existing codebase structure: simpl.py, package_manager.py, core/{lexer,parser,helper,__init__}.py, examples/
- Updated package_manager.py with full NPM Bridge support (npm: prefix detection, _fetch_npm_metadata, _download_and_extract_tarball, _generate_simpl_wrapper, install_npm_package, updated uninstall_package for npm: keys)
- Created core/js_bridge.py with js_eval function (Node.js subprocess execution, output parsing, error handling)
- Updated core/parser.py with FunctionCallNode AST node, function call parsing, and built-in functions (js_eval, str, int, float, len, type, abs, min, max, round)
- Created examples/test_npm.simpl demonstrating the NPM Bridge feature
- Updated simpl.py to wire up npm: installs (removed "not yet implemented" placeholder), added npm: import support in resolve_imports, updated version to 0.3.0
- Updated core/__init__.py to export js_bridge module
- Fixed a bug in extract_code_block (re.DALL -> re.DOTALL)
- Ran comprehensive smoke tests: all imports work, js_eval works with Node.js v24.16.0, built-in functions work, NPM package install/uninstall works, error handling works for 404s and empty npm: prefix

Stage Summary:
- All 4 requested features implemented and tested:
  1. NPM Bridge in package_manager.py: fetches metadata, downloads tarball, extracts main JS file, saves to libs/npm_<name>/, generates SimPL wrapper, updates simpl.lock
  2. JS execution in core/js_bridge.py: js_eval() runs JS via Node.js subprocess, parses stdout back to Python types, friendly error if Node.js not installed
  3. examples/test_npm.simpl: demo script with 5 test cases
  4. Error handling: 404 from NPM registry caught with friendly message, Node.js not installed caught with helpful tip
- Bumped version from 0.2.0 to 0.3.0
- Added 9 built-in functions to the Interpreter (js_eval, str, int, float, len, type, abs, min, max, round)
- Added FunctionCallNode AST node and function call parsing in parse_primary and parse_assignment_or_call
