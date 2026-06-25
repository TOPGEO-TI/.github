# Guia de Contribuição - TOPGEO TI

Bem-vindo(a) à equipa de engenharia e desenvolvimento da **TOPGEO CONSULTORIA LTDA**!

Este documento serve como a "fonte única de verdade" para o nosso fluxo de trabalho no GitHub. O objetivo destas diretrizes é garantir que o nosso código seja seguro, organizado, de fácil manutenção e que a nossa pequena equipa consiga produzir software com o máximo de agilidade e o mínimo de fricção.

Todos os membros da equipa devem ler, compreender e seguir este processo no seu dia a dia.

---

## 1. Fluxo de Trabalho Geral (Git Flow Simplificado)

A nossa branch principal é a `main`. Ela representa o código estável e pronto (ou em vias de ir) para produção. **Ninguém deve fazer commits diretamente na `main`.**

O fluxo padrão para qualquer entrega segue estes passos:

1. Escolher uma tarefa (**Issue**) priorizada no quadro Kanban.
2. Criar uma branch local para trabalhar nessa tarefa.
3. Desenvolver a solução e fazer os commits seguindo as regras da equipa.
4. Enviar a branch para o GitHub e abrir um **Pull Request (PR)**.
5. Obter a revisão e aprovação de, pelo menos, um colega de equipa.
6. Realizar o *Merge* na `main` (a branch de trabalho será eliminada automaticamente).

---

## 2. Gestão de Tarefas (Issues e Kanban)

O nosso ponto de encontro diário é o **GitHub Project (Quadro Kanban)** da TOPGEO TI. O fluxo dos cartões funciona da seguinte forma:

- **Backlog:** Onde as ideias, novas funcionalidades solicitadas e bugs reportados são registados. Os programadores não devem puxar tarefas daqui sem validação prévia.
- **Pronto para Dev (Next Up):** Tarefas que já foram refinadas, especificadas e estão prontas para serem iniciadas. Estão ordenadas por prioridade (de cima para baixo).
- **In Progress:** Quando iniciares uma tarefa, deves:
  1. Atribuir a Issue a ti mesmo (*Assignee*).
  2. Mover manualmente o cartão da coluna *Pronto para Dev* para *In Progress*.
  3. **Regra de Ouro:** Foca-te numa tarefa de cada vez. Evita ter múltiplos cartões em progresso em simultâneo.
- **In Review:** O código foi concluído e o Pull Request foi aberto. O cartão move-se automaticamente para aqui.
- **Done:** O Pull Request foi aprovado e integrado na `main`. A Issue fecha-se e o cartão move-se automaticamente para aqui.

---

## 3. Padrão de Commits (Conventional Commits)

Para mantermos o histórico do repositório legível e fácil de rastrear, adotamos o padrão mundial de **Conventional Commits**. Todas as mensagens de commit (e idealmente os títulos dos Pull Requests) devem seguir a estrutura:

```text
tipo(escopo-opcional): descrição curta em letras minúsculas
```

### Tipos Permitidos e Quando Usar

- **`feat`** — Quando adicionas uma nova funcionalidade ao sistema.
  - Exemplo: `feat(mapas): adiciona botão para exportar coordenadas em PDF`
- **`fix`** — Quando corriges um bug ou comportamento incorreto.
  - Exemplo: `fix(autenticação): corrige erro 500 ao redefinir palavra-passe`
- **`docs`** — Quando alteras apenas documentação (README, manuais, comentários de arquitetura).
  - Exemplo: `docs: atualiza instruções de configuração do ambiente docker`
- **`style`** — Alterações visuais ou de formatação que não mudam o comportamento do código (espaçamentos, organização de imports, linting).
  - Exemplo: `style: formata o alinhamento dos botões na dashboard`
- **`refactor`** — Uma alteração no código que melhora a sua estrutura ou performance, mas não corrige um bug nem adiciona uma funcionalidade.
  - Exemplo: `refactor: otimiza a query SQL de carregamento de dados geográficos`
- **`test`** — Quando adicionas ou modificas testes automatizados.
  - Exemplo: `test: adiciona testes unitários para a validação de NIF`
- **`chore`** — Tarefas de manutenção geral, atualização de bibliotecas, configurações de build ou CI/CD.
  - Exemplo: `chore: atualiza a versão da biblioteca Axios para a v1.7.0`

---

## 4. Nomeação de Branches

As branches devem ser criadas a partir da `main` atualizada e nomeadas com base no tipo de tarefa e no número da Issue correspondente. Use o formato `tipo/issue-numero-breve-descricao`:

- Para funcionalidades: `feature/issue-42-cadastro-clientes`
- Para correções de erros: `bugfix/issue-57-erro-exportacao`
- Para tarefas gerais: `chore/issue-12-configurar-env`

---

## 5. Criação e Vínculo de Pull Requests (PRs)

Ao concluir o desenvolvimento na tua branch, envia-a para o GitHub (`git push origin nome-da-branch`) e abre um Pull Request.

### Ligação Automática com a Issue

Para garantir o bom funcionamento do nosso Kanban automatizado, é obrigatório associar o PR à Issue que estás a resolver. Para o fazer, adiciona na descrição do teu PR uma das palavras-chave de fecho do GitHub seguida do número da Issue:

> "Este Pull Request implementa a interface de relatórios. Closes #42"

Palavras-chave aceites: `Closes #X`, `Fixes #X`, `Resolves #X`.

*(Isto garante que, quando o PR for aprovado e mesclado, o GitHub fechará a Issue e moverá o cartão para "Done" de forma automática.)*

### Regras do PR

- O título do PR deve ser claro e preferencialmente seguir o padrão dos commits (ex: `feat(relatorios): cria exportação shapefile`).
- Preenche o template de descrição explicando sucintamente o que foi feito e como testar.
- Solicita a revisão de, pelo menos, um colega de equipa.

---

## 6. Cultura de Code Review (Revisão de Código)

A revisão de código é uma responsabilidade partilhada de toda a equipa e tem a mesma importância que escrever código novo. PRs não devem ficar abertos e esquecidos.

### Como Revisor

- Sê construtivo, respeitoso e foca-te no código, nunca na pessoa.
- Procura por falhas de lógica, problemas de performance potenciais, vulnerabilidades de segurança e conformidade com o padrão de commits.
- Se estiver tudo correto, clica em **Approve**. Se precisares de alterações obrigatórias, usa o **Request Changes** explicando o motivo.

### Como Autor

- Vê o feedback como uma oportunidade de melhoria e aprendizagem de equipa.
- Responde aos comentários e, se necessário, faz novos commits na mesma branch para corrigir o que foi solicitado. O PR atualizar-se-á sozinho.

---

## 7. Definição de Concluído (Definition of Done - DoD)

Uma tarefa só é considerada verdadeiramente **Concluída (Done)** quando cumpre os seguintes critérios:

- [ ] O código foi escrito e resolve o problema descrito na Issue.
- [ ] O código foi testado localmente e não quebra outras funcionalidades.
- [ ] Nenhum segredo, password ou chave de API foi exposto nos ficheiros de código (o nosso sistema de Rulesets bloqueará o push caso detete algo).
- [ ] O Pull Request foi aberto e obteve pelo menos 1 aprovação de outro programador.
- [ ] O Merge foi realizado com sucesso na branch `main`.

---

Obrigado por nos ajudares a construir a engenharia da TOPGEO com excelência! Se tiveres sugestões de melhoria para este fluxo, abre uma Issue para podermos discutir em equipa.
