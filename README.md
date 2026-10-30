# Laboratório de automação de processos de desenvolvimento

Laboratório concluído em 29/10/2026, baseado no material do [Prof. Marcelino Dias da Silva — UNINOVE](https://github.com/MarcelinoDiasU9/lab-cicd-actions).

**[Abrir site publicado](https://jayzin65.github.io/lab-cicd-actions/)** · **[Relatório em PDF](docs/relatorio-laboratorio-ci-cd.pdf)** · **[Modelagem TO-BE](docs/modelagem-to-be.png)**

## Resultado dos três cenários

| Versão | Commit | Verificação | Publicação | Evidência |
| --- | --- | --- | --- | --- |
| 1 | 56eb380 | Aprovada | Publicada | [Execução](https://github.com/JayZin65/lab-cicd-actions/actions/runs/40933187450) |
| 2 | 515e9fb | Reprovada na regra 3 | Bloqueada; Versão 1 preservada | [Execução](https://github.com/JayZin65/lab-cicd-actions/actions/runs/40933736298) |
| 3 | ece782a | Aprovada | Versão corrigida publicada | [Execução](https://github.com/JayZin65/lab-cicd-actions/actions/runs/40990078154) |

Resultado didático: **duas aprovações e uma falha esperada**. O histórico contém também a execução inicial do template, fora desses três cenários.

Site final observado: **Versão 3 — corrigida**, ator **JayZin65**, **29/10/2026 às 23:10** (America/Sao_Paulo), commit **ece782a**.

## AS-IS e TO-BE

No AS-IS, QA confere manualmente o arquivo, o título e a integridade do HTML; DevOps entrega e implanta o código.

No TO-BE, o push na main dispara GitHub Actions. O job verificar testa a existência de index.html e a presença de `<title>` e `</html>`. A dependência needs: verificar impede a publicação quando há falha. Com Pages habilitado e CI aprovada, o job publicar preenche os dados de rastreabilidade e publica o site.

![Processo TO-BE](docs/modelagem-to-be.png)

Cliente e PO mantêm a definição da demanda; DEV corrige falhas; QA mantém os critérios; DevOps acompanha a entrega. A validação funcional de CNPJ e o monitoramento contínuo não fazem parte deste workflow.

## Arquivos da entrega

- [Relatório completo — AS-IS, TO-BE, respostas e resultados](docs/relatorio-laboratorio-ci-cd.pdf)
- [Modelagem TO-BE em PDF](docs/modelagem-to-be.pdf)
- [Modelo BPMN editável](docs/modelagem-to-be.bpmn)
- [Relatório em texto editável](docs/relatorio-editavel.md)
- [Evidências das execuções e capturas](docs/)
- [Roteiro original do professor](ROTEIRO-ORIGINAL.md)

## Configuração e limites

GitHub Pages usa GitHub Actions como origem. O job publicar declara o ambiente github-pages. O workflow também permite disparo manual.

As regras fazem buscas simples no arquivo: não constituem validação completa de HTML nem teste funcional de CNPJ. O teste de fechamento procura `</html>` em qualquer posição. Não há rollback automático; na falha de CI o deploy nem começa.

Commits de documentação usam [skip ci] para preservar a publicação demonstrada. Os exemplos originais permanecem em arquivos-da-aula.

