# Requisitos do Sistema

## Requisitos Funcionais  
1. RF‑01: O usuário pode se registrar com e‑mail e senha.  
2. RF‑02: O usuário pode criar um novo projeto e convidar membros da equipe.  
3. RF‑03: Dentro de um projeto, o usuário pode criar, atualizar e excluir tarefas.  
4. RF‑04: A tarefa possui título, descrição, autor, responsável, data de vencimento, estado.  
5. RF‑05: Usuário pode comentar em tarefas e anexar arquivos até 10 MB.  
6. RF‑06: O sistema envia notificação por e‑mail ou chat quando uma tarefa é atribuída ou alterada.  
7. RF‑07: O sistema fornece endpoint de API pública para consulta de tarefas com autenticação.  

## Requisitos Não‑Funcionais  
- RNF‑01: O sistema deve suportar 1000 usuários simultâneos.  
- RNF‑02: Tempo de resposta médio a requisição REST deve ser < 300ms 90% do tempo.  
- RNF‑03: Dados devem ser armazenados com criptografia em repouso.  
- RNF‑04: Logs de auditoria devem ser mantidos por 12 meses.  
- RNF‑05: Interface web deve funcionar em Chrome, Firefox, Safari (versões recentes).  

## Restrições e Dependências  
- RD‑01: Utilizar banco de dados PostgreSQL 14+  
- RD‑02: Hospedagem em nuvem (AWS ou equivalente)  
- RD‑03: Integração com sistema de chat via webhook (Slack ou Teams)  

## Critérios de Aceitação  
- Todas as funcionalidades RF listadas devem ter cobertura de teste automatizada > 80%.  
- Documentação técnica (esta) deverá estar revisada e aprovada antes do início de desenvolvimento.  

