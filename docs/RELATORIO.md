# Relatório de entrega

[Abrir o portfólio](../README.md) · [Catálogo](../CATALOGO.md) · [Como publicar](PUBLICACAO.md)

**Referência:** 20/10/2026. Implementação local no repositório destinado ao portfólio, após auditoria do currículo, perfil e seis projetos.

## Arquivos entregues

| Arquivo | Operação e finalidade |
| --- | --- |
| [README.md](../README.md) | Modificado: apresentação backend, competências, três destaques, catálogo e contato. |
| [CATALOGO.md](../CATALOGO.md) | Criado: seis projetos, categorias, funcionalidades, estado, complexidade, execução, limites e evidências. |
| [perfil/README.md](../perfil/README.md) | Criado: conteúdo pronto para o README do perfil. |
| [EXPERIENCIA.md](EXPERIENCIA.md) | Criado: trajetória, formação e distinção das fontes. |
| [AUDITORIA.md](AUDITORIA.md) | Criado: diagnóstico, inventário, competências, plano e commits examinados. |
| [SEGURANCA.md](SEGURANCA.md) | Criado: achados de TLS, filas e acesso Firebase, sem credenciais. |
| [PROPOSTAS-README.md](PROPOSTAS-README.md) | Criado: escopo de melhorias nos seis projetos, aguardando autorização específica. |
| [PUBLICACAO.md](PUBLICACAO.md) | Criado: revisão, commit/push pelo mantenedor, ativação do perfil e manutenção. |
| [RELATORIO.md](RELATORIO.md) | Criado: registro desta entrega. |

Total: **um arquivo modificado e oito criados**. A imagem preexistente `DS.jpg` foi preservada; o histórico Git continua no clone. Nenhum arquivo de licença foi criado, alterado ou removido. O badge de licença do README antigo não foi mantido como declaração de licença do novo conteúdo.

## Projetos e hierarquia

- **Destaque principal:** `estacao-climatica-csharp`, pela evidência direta de backend C#/.NET, integrações, organização e testes.
- **Destaques:** `Oracle-Database`, pela profundidade em dados e documentação operacional; `anvmano.github.io`, pela interface demonstrável e contexto da evolução para .NET.
- **Complementares:** `estacao-climatica` e `SensorsController`, pela aquisição de dados e integração com dispositivos/serviços.
- **Demais projetos:** `LightingController`, automação de escopo específico, acessível no catálogo.

Todos os seis projetos fornecidos estão representados. `Meu-portfolio` é o destino editorial, sem ser contado como um sétimo projeto técnico analisado.

## Melhorias implementadas

A apresentação foi reposicionada de estudante de Data Science para desenvolvedor backend C#/.NET, com base no currículo atual. Os conteúdos longos foram organizados fora da página inicial; cada projeto recebeu descrição técnica e evidências no snapshot analisado. Tecnologias profissionais e públicas foram diferenciadas, sem atribuir senioridade, cobertura ou homologação não demonstradas.

O conteúdo usa Markdown nativo e links descritivos, sem dependências de badges ou serviços de estatísticas. Telefone, localização pessoal, PDF do currículo e configurações de serviços não foram publicados. O README de perfil usa links absolutos para poder ser copiado para o destino próprio.

## Validação

Verificações executadas nos arquivos da entrega:

- **Cobertura:** os seis projetos estão no catálogo e acessíveis pela página principal.
- **Markdown:** nove documentos analisados, com título, blocos de código fechados, codificação UTF-8 e ausência de caracteres inválidos ou espaços ao final das linhas; `git diff --check` sem erros.
- **Navegação:** 64 links locais conferidos, incluindo destinos e âncoras; todos os links do README de perfil são absolutos.
- **Rastreabilidade:** 50 ocorrências de links de código/documentação conferidas contra os arquivos/diretórios dos clones e suas revisões.
- **Destinos externos:** na conferência para publicação, 56 URLs únicas foram consultadas; 55 responderam HTTP 200. O LinkedIn retornou HTTP 999, bloqueando a validação automática. Foi mantido o endereço fornecido no currículo e já presente no README original; seu conteúdo não foi confirmado automaticamente.
- **Dados pessoais:** verificação dos nove documentos sem telefone, localização pessoal, caminhos de usuário, assinaturas comuns de chaves/tokens ou outros e-mails além do canal profissional fornecido. Isso não constitui uma busca exaustiva de segredos no histórico dos projetos.
- **Apresentação:** Markdown renderizado localmente com parser GFM e prévia CSS aproximada do GitHub; 36 verificações em nove documentos, larguras de 390 e 1440 px, temas claro e escuro. Um título principal por documento, links com texto e ausência de rolagem horizontal da página; tabelas/blocos extensos podem usar rolagem própria. Inspeção visual da apresentação, perfil e entrada do catálogo.
- **Preservação:** conferência da imagem existente e ausência de alterações nas cópias dos projetos originais. Nenhum comportamento de aplicação foi alterado.

A prévia não substitui a conferência final na renderização real do GitHub após a publicação. Nenhum resultado histórico de testes das aplicações foi reapresentado como teste executado nesta entrega.

## Limitações e próximos passos

Não foram executadas suítes dos projetos originais, compilação dos firmwares, testes físicos, procedimentos Oracle, autenticação Google real ou consultas a bancos privados. Os links das fontes preservam a revisão analisada; mudanças futuras podem exigir nova análise. A demonstração web foi identificada e consultada por HTTP, sem homologação funcional completa.

Os READMEs originais não foram editados; as [propostas](PROPOSTAS-README.md) dependem de aprovação. Os achados de [segurança e confiabilidade](SEGURANCA.md) permanecem nos projetos originais. Como evolução, priorizar acesso Firebase/TLS e recuperação da fila, depois evidências sanitizadas de execução e testes reproduzíveis.

## Publicação autorizada

O mantenedor autorizou a publicação em 20/10/2026. Destinos desta etapa: [Meu-portfolio](https://github.com/anvmano/Meu-portfolio) e [anvmano/anvmano](https://github.com/anvmano/anvmano).

O repositório público de perfil foi criado e seu README foi conferido contra `perfil/README.md`. A descrição de `Meu-portfolio` foi atualizada para backend C#/.NET, bancos de dados e integrações com ESP32. O portfólio usa o histórico existente, sem force push. O [guia](PUBLICACAO.md) registra como manter ambos os destinos.

A publicação não inclui mudanças nos seis projetos originais, na bio da conta ou nos itens fixados. As propostas de documentação continuam dependentes de autorização específica.
