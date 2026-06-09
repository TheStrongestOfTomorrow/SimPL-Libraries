---
Task ID: 1
Agent: Main
Task: Fix GitHub username case sensitivity, update all references, bump version, push to GitHub

Work Log:
- Fixed package_manager.py: changed default repo_owner from "thestrongestoftomorrow" to "TheStrongestOfTomorrow"
- Added PAT authentication support via SIMPL_GITHUB_PAT environment variable in _curl_get()
- Updated User-Agent from 0.6.0 to 0.7.0 in package_manager.py
- Fixed core/tui.py: updated all GitHub URLs (check_for_updates, get_update_instructions, action_about) to use TheStrongestOfTomorrow
- Fixed install.sh: updated git clone URL and usage comment
- Fixed install.ps1: updated git clone URL and usage comment
- Fixed README.md: bulk replaced all thestrongestoftomorrow references, updated version badge to 0.7.0, added HTTP/JSON examples section, updated built-in function table with HTTP/JSON/Dict entries
- Updated real_world.simpl example with correct version 0.7.0
- Updated simpl.py VERSION from "0.6.0" to "0.7.0"
- Verified HTTP get(), post(), response.json(), parse_json(), to_json(), has_key(), remove() all work correctly
- Committed and pushed all changes to GitHub

Stage Summary:
- Critical 422 API bug fixed by correcting GitHub username case
- PAT auth support added for increased API rate limits
- All 7 modified files pushed to https://github.com/TheStrongestOfTomorrow/SimPL
- Version bumped to 0.7.0
