# SKILL — Review PR DIGIY

## Checklist de review

### Doctrine Façade
- [ ] Aucun terme technique visible côté user (slug, rail, module...)
- [ ] Wording humain et actionnable partout

### Sécurité
- [ ] Pas de service_role key exposée côté client
- [ ] RLS actif sur les tables concernées
- [ ] guard.js présent et correct sur les pages PRO

### Auth Rail
- [ ] Pattern canonique respecté : window.DIGIY_LOGIN_URL → visibility hidden → guard.js → Supabase CDN → app scripts
- [ ] Clé sessionStorage : `digiy_guard_session:MODULE`
- [ ] Expiry 8h respecté

### Backend
- [ ] RPC = `digiy_verify_pin` avec params `{p_phone, p_module, p_pin}`
- [ ] Noms de tables réels (pas inventés)

### Mobile Terrain
- [ ] CTA visible above the fold
- [ ] Pas de flash blanc au chargement

## Format de sortie
1. Verdict global (✅ MERGE / ⚠️ RÉSERVES / ❌ BLOQUER)
2. Points bloquants
3. Réserves non bloquantes
4. Ce qui est bien fait
