# Política de Segurança — Emma Honkai

**Versão:** 1.0 — 5 de novembro de 2026

## Escopo
Controles mínimos para frontend GitHub Pages, Supabase Auth/Postgres/Edge Functions, repositório privado de dados e contas administrativas. Esta política não representa certificação nem garantia de ausência de vulnerabilidades.

## Credenciais
- Nunca inserir PAT, chave service_role, senha ou segredo em JavaScript público, HTML, issues, logs ou repositórios.
- Usar Fine-grained tokens limitados ao repositório e permissões mínimas, com expiração.
- Guardar tokens somente em Supabase Edge Function Secrets/cofre equivalente.
- Revogar imediatamente credenciais expostas e revisar histórico Git.
- No frontend, usar somente chave publicável/anon com RLS.

## Autenticação
- Senhas gerenciadas pelo Supabase Auth; nunca registrar senha em texto puro.
- Exigir senhas longas e exclusivas (mínimo operacional 12 caracteres) e estimar força localmente.
- Aplicar rate limits e monitorar tentativas.
- Habilitar proteção contra senhas vazadas quando disponível no plano.
- Exigir MFA para administradores e manter recuperação segura.
- Não confiar em role, user metadata ou identificadores enviados pelo navegador para autorizar ações.

## Banco e autorização
- RLS habilitada em todas as tabelas expostas.
- Políticas devem validar propriedade/participação; authenticated isoladamente não é autorização.
- Alterações privilegiadas (cargo, moedas, banimentos, missões, assinaturas) validadas no servidor.
- Revisar views, RPCs, triggers, funções SECURITY DEFINER, Storage e grants.
- Impedir autoelevação de privilégios.
- Registrar ator, alvo, ação, horário e resultado de ações administrativas.

## Aplicação web
- Escapar conteúdo não confiável em HTML e atributos; preferir textContent e APIs DOM seguras.
- Validar URLs de imagens/uploads e rejeitar esquemas perigosos.
- Implementar CSP compatível com GitHub Pages; não presumir que o frontend define cabeçalhos HTTP.
- Limitar tamanho/frequência de mensagens, denúncias e uploads.
- Não expor mensagens privadas em páginas, logs ou erros.

## Privacidade e incidentes
- Chats acessíveis apenas a participantes autorizados e administradores com necessidade legítima.
- Acesso administrativo a conversas limitado e auditável.
- Em incidente: conter, revogar credenciais/sessões, preservar evidências mínimas, avaliar impacto, corrigir e comunicar quando exigido.
- Backups protegidos, acesso restrito e testes de restauração.
- Evitar coletar conteúdo de mensagens e segredos em logs.

## Estado verificado em 05/11/2026
- RLS habilitada nas tabelas públicas consultadas.
- Advisor Supabase reportou Leaked Password Protection Disabled; depende de plano/configuração Auth.
- A policy profiles_read_authenticated permite SELECT amplo a usuários autenticados. Isso pode expor campos de perfil além do necessário. Refatorar carregamento para view pública mínima e restringir tabela base a dono/admin antes de alterar policy.
- app_settings_read_authenticated permite leitura de todas as configurações por autenticados; separar configurações públicas e privadas.
- emma-api contém caminho server-side de GitHub usando variável GITHUB_TOKEN; confirmar segredo e testar gravação sem revelar valor.
- Frontend usa innerHTML em várias áreas. Mensagens são escapadas no render principal, mas revisar templates e atributos dinâmicos.

## Plano prioritário
1. Rotacionar credenciais expostas e verificar histórico público.
2. Restringir profiles e separar perfil público mínimo de campos privados.
3. Separar configurações públicas/privadas.
4. Adicionar MFA administrativo e encerramento/revogação de sessões.
5. Testar RLS com usuário A, usuário B e admin.
6. Implementar auditoria administrativa e retenção.
7. Adicionar CSP compatível e revisar XSS.
8. Implementar exclusão de conta/dados e backup com restauração testada.

## Relato de vulnerabilidade
Não publique credenciais ou dados pessoais em reports públicos. Envie ao mantenedor descrição, impacto, passos mínimos, evidência sanitizada e horário aproximado.
