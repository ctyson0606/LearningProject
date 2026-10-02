# GOTCHAS

Version-bound traps. Every entry carries a date. Entries here may be deleted
without justification once the dependency they describe is gone.

Format:  ### <one-line trap>  `[YYYY-MM-DD]`

### Git Bash ignores `TZ=Europe/London` and prints UTC labelled GMT  `[2026-10-02]`

Git for Windows has no zoneinfo database, so an IANA zone name falls back to
UTC while `%Z` still says GMT: an hour off during BST, with nothing to show
it. The POSIX rule string `TZ='GMT0BST,M3.5.0/1,M10.5.0'` works there and on
macOS and Linux (checked across both 2026 switch-overs), and git honours it
for commit dates. Python zoneinfo worked on this machine but needs tzdata on
Windows, so the template does not rely on it.
