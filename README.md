# Política de Segurança — Emma Honkai

**Última atualização: 6 de novembro de 2026**

## 1. Objetivo e abrangência

Esta política estabelece regras para proteger contas, personagens, conversas, banco de dados, repositórios, serviços e usuários do Emma Honkai. Aplica-se ao mantenedor, administradores, colaboradores e qualquer pessoa autorizada a modificar ou operar a plataforma.

## 2. Senhas, tokens e segredos

Senhas, tokens pessoais, chaves de API, chaves privadas, credenciais de banco, segredos de funções e códigos administrativos são informações confidenciais. É proibido incluí-los no frontend, em arquivos públicos, commits, issues, comentários, capturas de tela, mensagens de suporte ou exemplos.

Segredos devem ficar somente no gerenciador de segredos do serviço que precisa deles, com as menores permissões possíveis. Tokens devem ter escopo limitado e validade curta sempre que possível. Se um segredo for publicado, compartilhado ou suspeito de exposição, deve ser revogado ou rotacionado imediatamente. Apagar o texto de um arquivo não remove necessariamente o segredo do histórico Git; também é preciso avaliar o histórico e os registros de acesso.

## 3. Separação entre site e servidor

O frontend público deve conter somente código e configurações que possam ser vistos por qualquer visitante. Operações privilegiadas, validações de autorização e acesso a credenciais devem ocorrer no backend. Chaves privilegiadas do Supabase e tokens de escrita do GitHub nunca podem ser enviados ao navegador.

O servidor deve validar cada solicitação, verificar a sessão e confirmar a permissão do usuário. Não se deve confiar apenas em verificações feitas pelo JavaScript do navegador, pois essas verificações podem ser modificadas pelo próprio usuário.

## 4. Contas e autenticação

Cada pessoa deve utilizar sua própria conta e manter sua senha em sigilo. É proibido tentar acessar, adivinhar, reutilizar ou redefinir a senha de outra pessoa sem autorização. Senhas não podem ser armazenadas em texto puro, logs, arquivos JSON ou repositórios.

A criação e promoção de administradores devem ocorrer por procedimento controlado no backend. Um cadastro comum não pode ganhar privilégios administrativos apenas por enviar um campo especial pelo navegador. Cada ação administrativa deve ser autorizada no servidor.

## 5. Permissões e isolamento de dados

O banco de dados deve aplicar controles de acesso no servidor, incluindo políticas de Row Level Security (RLS) quando disponíveis. Cada usuário só pode consultar ou alterar informações que suas permissões autorizem. Chats privados, mensagens, perfis, personagens privados, denúncias e configurações administrativas precisam de regras específicas.

Personagens públicos podem ser exibidos conforme a finalidade do produto, mas isso não torna públicos os dados privados de seus criadores. Não amplie permissões para resolver um erro de interface sem identificar a causa. Mudanças em políticas, privilégios, funções ou tabelas devem ser revisadas e testadas com contas de diferentes níveis de acesso.

## 6. Repositórios e código

O repositório do frontend pode ser público; portanto, todo arquivo nele deve ser considerado visível a qualquer pessoa. Repositórios que armazenam dados operacionais devem permanecer privados. Nenhum repositório deve conter senhas, tokens, dados reais de usuários, históricos privados de conversa ou cópias desnecessárias do banco.

Alterações devem preservar o código existente e ser revisadas antes de serem publicadas. Antes de migrações, exclusões em massa ou mudanças de alto impacto, deve existir backup e plano de recuperação. Não apague contas, mensagens ou dados de produção sem autorização explícita e confirmação do alvo.

## 7. APIs, entradas e prevenção de abuso

Toda informação recebida do navegador deve ser considerada não confiável. O backend deve validar tipos, tamanhos, formatos, identificadores e limites de frequência. Deve impedir acesso a recursos de terceiros por troca de IDs, elevação de privilégios, falsificação de remetente, abuso de convites, spam e chamadas administrativas não autorizadas.

Arquivos importados devem ser tratados como conteúdo não confiável. O usuário deve ter autorização para compartilhar o material importado. Mensagens e importações devem respeitar os limites definidos pelo serviço. Erros exibidos ao usuário não devem revelar tokens, consultas SQL sensíveis, caminhos internos ou detalhes que facilitem ataques.

## 8. Moderação, denúncias e banimentos

Denúncias devem ser acessíveis somente às pessoas que precisam analisá-las. A equipe deve preservar a confidencialidade dos relatos e evitar expor denunciantes. Banimentos e outras medidas administrativas devem ser aplicados no backend e registrados de forma adequada, não apenas escondidos na interface.

É proibido usar ferramentas administrativas para perseguir usuários, divulgar conversas privadas, alterar dados por vingança ou conceder vantagens indevidas. Ações administrativas devem ser proporcionais e respeitar as regras do serviço.

## 9. Logs, monitoramento e backups

Logs devem conter apenas as informações necessárias para investigar falhas e abusos. Não devem incluir senhas, tokens, chaves ou conteúdo privado desnecessário. O acesso aos logs deve ser limitado. Antes de compartilhar registros para diagnóstico, remova nomes, IDs, mensagens e outros dados identificáveis sempre que não forem necessários.

Backups devem ser protegidos, ter acesso restrito e ser testados periodicamente. Cópias antigas também são dados sensíveis e devem seguir controles de acesso e prazos de retenção. Antes de operações importantes, verifique se há uma cópia recuperável.

## 10. Dependências e atualizações

Bibliotecas, funções do backend, políticas do banco e integrações devem ser mantidas atualizadas. Dependências desconhecidas ou desnecessárias não devem ser adicionadas sem justificativa. Mudanças relevantes devem ser avaliadas quanto a riscos e compatibilidade.

## 11. Comunicação responsável de vulnerabilidades

Quem encontrar uma falha deve comunicá-la ao mantenedor por canal privado e oficial, informando o problema e passos mínimos para reproduzi-lo. Não publique a falha, dados de usuários ou provas que permitam exploração antes de dar oportunidade razoável para correção. Não tente acessar dados de terceiros, apagar informações, interromper o serviço ou ampliar o acesso para provar uma vulnerabilidade.

A equipe deve avaliar o risco, corrigir ou reduzir o impacto e informar o resultado quando possível. Se houver exposição de credenciais, a prioridade é revogar ou rotacionar o segredo e revisar os acessos.

## 12. Resposta a incidentes

Diante de suspeita de invasão, vazamento ou alteração indevida, a equipe deve conter o acesso afetado, revogar credenciais comprometidas, preservar evidências sem divulgar dados pessoais, revisar logs e permissões, corrigir a causa e avaliar comunicações a usuários ou autoridades conforme a legislação aplicável.

## 13. Limites

Esta política define práticas de segurança, mas não representa certificação, auditoria independente ou promessa de que o sistema esteja livre de vulnerabilidades. A segurança depende também da configuração real dos serviços, dos fornecedores, das atualizações e das ações de administradores e usuários.

---

## Resumo simples

- Nunca coloque senha, token ou chave secreta no código do site ou em repositório público.
- O site público não pode guardar poderes de administrador. Essas ações ficam no servidor.
- Cada pessoa só pode acessar contas, chats e personagens que tem permissão para ver.
- Repositórios com dados devem continuar privados.
- Não compartilhe conversas, denúncias ou dados reais de usuários.
- Antes de apagar ou alterar muitos dados, faça backup e confirme o que será afetado.
- Se um token vazar, revogue-o e crie outro. Apagar o texto não basta.
- Se encontrar uma falha, avise o mantenedor em particular. Não use a falha para invadir ou prejudicar alguém.
- Administradores também precisam seguir as regras.
- Nenhum sistema é 100% seguro; é preciso revisar, atualizar e testar.

**Em poucas palavras:** segredos ficam secretos, cada pessoa acessa somente o que pode, e problemas de segurança devem ser tratados rapidamente sem expor os usuários.