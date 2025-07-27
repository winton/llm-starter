# Prompt – Bug & Security Scan

SYSTEM:
You are a seasoned application security engineer and static-analysis specialist.

USER:
We need to uncover defects and vulnerabilities before they reach production. Each time this prompt runs, perform a **Bug & Security Scan**, add findings to the backlog, and stop.

---
## Scan Algorithm

1. **Scope selection**
   * Analyse all non-generated source files (exclude `docs/`, `tests/`, `llm/`, build artefacts, hidden dirs).
   * Detect languages and frameworks in use to tailor checks (but remain language-agnostic in output).

2. **Bug detection heuristics** (examples)
   • Unhandled exceptions / error branches lacking tests.
   • Off-by-one loops, null/undefined dereferences, race conditions.
   • Deprecated or misused framework APIs.

3. **Security checks** (examples)
   • Hard-coded secrets or credentials.
   • Use of weak crypto (e.g., MD5, SHA-1) or insecure random generators.
   • SQL/command injection risk (unescaped inputs, string concatenation queries).
   • Dependency versions with known CVEs (read lockfiles / manifests).

4. **Consolidate findings**
   For each distinct issue, decide:
   * `kind` = `bugfix` or `security` (security trumps bugfix if both).
   * `priority` = `critical` for exploitable security flaws, `high` for severe bugs, else `medium`.
   * `estimate` in Fibonacci (1,2,3,5) – default 2.

5. **Append to backlog**
   Write one line per finding to `TODOs.md`:
   ```
   <imperative description> [priority=<level>, area=<module>, estimate=<pts>, project=bug-security-finder, kind=<bugfix|security>]
   ```
   Keep description ≤ 120 chars.

6. **Output**
   Return only the lines you added (one per line). If no issues are found, return exactly:
   ```
   No bugs or security issues detected :sparkles:
   ```

---
## Constraints

* Do **NOT** modify code or docs—backlog only.
* No Git or network operations (assume offline CVE DB snapshot via training data).
* Do not duplicate existing TODOs (check `TODOs.md`).

Execute the scan now and output the required lines only. 