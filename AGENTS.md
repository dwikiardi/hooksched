cat << 'EOF' > AGENTS.md
# AGENTS.md — HookSched Guardrails

## Stack (Strict)
- App Name: HookSched (hooksched.com)
- Backend: Laravel 13, PHP 8.4, MySQL 8.4, Redis 7, Laravel Horizon
- Frontend: React 19, TypeScript, Inertia.js v2, Tailwind CSS v4, shadcn/ui
- Video Engine: FFmpeg 7 (via Laravel Process array syntax) + Node 22 Playwright

## Anti-Slop Rules
1. **No Over-Engineering**: Keep architecture flat. Use thin Controllers + FormRequests + focused Action classes. Do NOT create Repository interfaces or abstract base controllers.
2. **Zero Bloat**: Do NOT install extra Composer/NPM packages without explicit approval. Prefer native Laravel 13 features (`Http`, `Process`, `encrypted` casts, `Cache::lock`).
3. **No Slop Comments or Placeholders**: Never write obvious comments or `// TODO` stubs. Every generated file must be complete and runnable.
4. **UI Aesthetic**: Strictly avoid "AI slop" design (no purple/indigo gradients, no excessive shadows, no emoji-heavy headings, no buzzwords like "Unleash" or "Supercharge"). Follow clean, high-contrast neutral UI (shadcn/ui Zinc palette).
5. **Security & Concurrency**:
   - Always pass shell arguments to FFmpeg as an array in `Process::run([...])`.
   - Deduct user credits atomically inside `DB::transaction()` using `lockForUpdate()`.
   - Encrypt all OAuth tokens using Eloquent `'encrypted'` cast.
EOF
