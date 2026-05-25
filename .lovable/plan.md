## Objetivo
Tornar o login fictício temporariamente: qualquer email e qualquer senha entram no sistema, sem validar no Supabase.

## Mudanças

### `src/pages/Login.tsx`
- Remover a chamada `supabase.auth.signInWithPassword` no `handleSubmit`.
- Aceitar qualquer email/senha não vazios.
- Decidir o papel (empresa/fornecedor) com base no email para facilitar teste:
  - Se o email contiver `fornecedor` → redireciona para `/supplier-dashboard`.
  - Caso contrário → redireciona para `/dashboard`.
- Manter a animação do logo girando + modal de sucesso já existentes.
- Remover o `useEffect` que checa sessão existente (não precisamos mais redirecionar usuário já logado, já que não há login real).

### Observações
- Nada será alterado no Supabase, no `useAuth`, no Register, nem nas outras páginas.
- Isso é apenas para testes visuais de fluxo. As páginas internas que dependem de `useAuth`/dados reais do Supabase podem ficar vazias ou com erros de permissão — é esperado nesse modo fictício.
- Quando quiser voltar ao login real, basta reverter este arquivo.

## Pergunta rápida (opcional)
Quer que eu também faça um “bypass” no `useAuth` para simular um usuário logado (assim as páginas internas carregam sem erro), ou só o login visual já está bom por enquanto?