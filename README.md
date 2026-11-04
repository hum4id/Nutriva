# Nutriva

Web pendamping gizi & tumbuh kembang balita (React 19 + Vite + Supabase) dengan layanan AI terpisah (`ai-service/`, FastAPI).

## Menjalankan frontend

```bash
npm install
cp .env.example .env      # isi VITE_SUPABASE_URL, VITE_SUPABASE_ANON_KEY, VITE_AI_API_URL
npm run dev
npm run lint && npm run build && npm run test:who
```

## Database

Jalankan `supabase_schema.sql`, lalu migrasi di `supabase/migrations/` secara berurutan, lalu `supabase/seed/nutrition_seed.sql` (1.063 bahan makanan berbasis TKPI 2017 + 30 resep balita Kemenkes; sumber dan QA di `ai-service/nutrition_data/README.md`). `supabase_seed.sql` lama berisi data dummy dan sudah deprecated.

## AI

- Backend AI, deploy ke Hugging Face Spaces, keamanan: `ai-service/README.md`
- Model card: `ai-service/docs/MODEL_CARD.md`

Semua API key LLM hanya disimpan di server AI. Jangan menaruh secret apa pun di variabel `VITE_*`, karena nilainya ikut ter-bundle ke browser.
