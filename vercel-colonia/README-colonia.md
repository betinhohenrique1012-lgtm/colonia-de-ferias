# Colônia de Férias — Coordenação

Site estático (index.html) hospedado na Vercel, com dados sincronizados no Supabase.

- Configuração central: `CFG.SYNC_URL` no topo do bloco de sincronização em index.html (URL da Edge Function `colonia-sync`). Nenhuma chave secreta fica no site.
- Dados: tabela `public.colonia_state` (RLS ligada, sem acesso direto). Só a Edge Function, com a senha da Coordenação, lê e grava.
- Atualizar o site NÃO apaga dados: o banco fica separado do código, e o site faz merge dos dados locais com os da nuvem (cópia de segurança local em `colonia_v1_bkp`).
- Backup: Admin > Exportar backup JSON.
