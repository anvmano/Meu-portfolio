# Auditoria e estratégia do portfólio

[Apresentação](../README.md) · [Inventário detalhado](../CATALOGO.md) · [Relatório de entrega](RELATORIO.md)

**Referência:** 20/10/2026, America/Sao_Paulo. Auditoria realizada antes da edição do conteúdo do portfólio.

## Fontes e método

- Currículo PDF fornecido: uma página, com leitura do texto e inspeção visual da página renderizada. Usado para experiência, formação e canais profissionais; o PDF original não foi copiado para este repositório.
- [Perfil público](https://github.com/anvmano) e API pública do GitHub: sete repositórios públicos, sendo seis projetos fornecidos e o destino `Meu-portfolio`. Nome público confirmado; bio e site não preenchidos na consulta.
- Cópias locais de leitura dos seis projetos, com árvore de arquivos, documentação disponível, configurações, dependências e trechos relevantes de implementação/testes examinados. A análise não corresponde à revisão linha a linha de todo o acervo ou à auditoria de todo o histórico Git.
- Clone completo de `Meu-portfolio`, preservando histórico e arquivos. Base: `2e7a679c20eb4e37fb3dc3277659c5a03ca1457e`.
- Consulta HTTP à demonstração web e leitura das orientações oficiais de README de perfil e fixação de repositórios.

Não houve repositório de projeto inacessível. A busca pública por `anvmano/anvmano` retornou 404; isso indica ausência de um repositório público acessível, sem permitir concluir sobre repositórios privados.

## Diagnóstico profissional

O posicionamento sustentado pelas fontes é **desenvolvedor backend C#/.NET com experiência anterior em administração Oracle**. O currículo descreve desenvolvimento corporativo de janeiro/2022 a junho/2026 e atuação DBA de julho/2017 a julho/2019. O projeto .NET oferece evidências públicas diretamente relacionadas ao objetivo profissional.

Os pontos fortes são regras de negócio e manutenção de sistemas, integração de dados, testes, conhecimento SQL e capacidade de conectar software a dispositivos. A formação em Ciência de Dados permanece como contexto acadêmico. Não foram encontrados projetos de Machine Learning entre os seis fornecidos que justifiquem esse foco na apresentação principal.

**Senioridade:** o currículo sustenta experiência profissional de vários anos; os projetos mostram separação de responsabilidades, integrações e testes. As fontes não bastam para atribuir um cargo “sênior”, liderança, escala de produção ou responsabilidade por arquitetura empresarial. O portfólio usa “Desenvolvedor Backend”, sem nível presumido.

## Inventário resumido

| Projeto | Evidência principal | Papel |
| --- | --- | --- |
| [estacao-climatica-csharp](../CATALOGO.md#estacao-climatica-csharp) | Backend .NET 8, controllers, serviços, Firebase REST e xUnit/Playwright. | Destaque principal, alinhado a backend. |
| [Oracle-Database](../CATALOGO.md#oracle-database) | Biblioteca SQL/PLSQL, guias e verificadores documentais. | Destaque, profundidade em dados. |
| [anvmano.github.io](../CATALOGO.md#anvmano-github-io) | Dashboard estático, integrações, relatórios e cenários de acessibilidade. | Destaque, interface demonstrável e origem da migração .NET. |
| [estacao-climatica](../CATALOGO.md#estacao-climatica) | DHT22, RTC, Telegram, Firebase e fila LittleFS. | Complementar, integração de ponta a ponta. |
| [SensorsController](../CATALOGO.md#sensorscontroller) | Sensores do ar/água, processamento e fila REST. | Complementar, aquisição de dados. |
| [LightingController](../CATALOGO.md#lightingcontroller) | Curva de brilho, FastLED, relé e horários solares. | Demais projetos, automação de finalidade específica. |

O [catálogo](../CATALOGO.md) registra, para cada projeto, objetivo, tecnologias, funcionalidades, arquitetura/estrutura, integrações, testes, execução, estado, complexidade estimada, documentação, imagens, diferenciais e melhorias.

## Matriz de competências

| Competência | Fonte e alcance |
| --- | --- |
| C#/.NET Framework, ASP.NET MVC, NHibernate e SQL Server | Experiência declarada no currículo. Não atribuídos ao projeto .NET público quando não constam do código. |
| .NET 8 e ASP.NET Core | `.csproj`, `Program.cs`, controllers e serviços no projeto C#. |
| HTTP, JSON, repositório e injeção de dependências | Abstrações em Application, implementação em Infrastructure e composição em Web. |
| Testes | NUnit/Playwright no currículo; xUnit/Playwright no projeto .NET; scripts Node/Playwright/axe no web; verificadores Python no Oracle. Existência não equivale a aprovação nesta auditoria. |
| SQL/PLSQL e administração Oracle | Experiência no currículo; scripts e documentação públicos como evidência técnica complementar. |
| JavaScript, HTML/CSS e visualização | Dashboards e Chart.js; TypeScript/Telerik apenas como experiência declarada no currículo. |
| C++/Arduino, ESP32, sensores e atuadores | Includes, sketches, processamento, filas e configuração dos três firmwares. Precisão/calibração física não verificada. |
| Ferramentas e ambiente | Git nos repositórios; SVN/Redmine e Linux/Windows no currículo; Oracle Linux/OCI nos guias. |

Não foram acrescentados certificados, microserviços, Docker, Kubernetes, Entity Framework, cloud deployment ou cobertura percentual de testes sem evidência. A [trajetória completa](EXPERIENCIA.md) separa formação e experiência de código examinável.

## Problemas identificados

1. O README de `Meu-portfolio` ainda se apresentava como estudante de Data Science, trazia um texto interrompido, um link de imagem para outro caminho e apenas o projeto Oracle. A instituição de graduação foi atualizada conforme o currículo atual.
2. Os dashboards web e .NET não têm README na raiz dos commits analisados, embora disponham de guias extensos em `docs/README.md`.
3. Não havia entrada pública de perfil identificada. Também faltava uma visão conjunta dos seis projetos e uma hierarquia orientada a backend.
4. Rótulos de tecnologia poderiam confundir recrutadores: Python no Oracle refere-se principalmente aos verificadores; xUnit no projeto .NET não é NUnit; MVC do currículo não substitui a identificação precisa de ASP.NET Core Controllers no projeto.
5. Não há workflows de CI nos seis snapshots. Os três firmwares não incluem suíte automatizada; os resultados históricos de compilação não foram repetidos.
6. Não foram encontradas capturas funcionais versionadas dos dashboards ou fotos/esquemas completos dos firmwares. Ícones e imagem decorativa não substituem evidências de execução.
7. TLS dos firmwares, recuperação da fila de sensores e configuração de acesso Firebase têm limites relevantes, registrados em [Segurança e confiabilidade](SEGURANCA.md).

## Plano de apresentação adotado

**Navegação em dois níveis:** apresentação curta no README e catálogo detalhado separado. Isso permite identificar especialidade e destaques rapidamente, com acesso ao inventário completo para uma análise técnica.

**Hierarquia:** .NET primeiro pela aderência às vagas; Oracle pela experiência em dados e documentação operacional; web pela demonstração acessível e contexto da evolução para .NET. Estação e SensorsController complementam a integração; LightingController permanece visível como automação de escopo concentrado. A ordem não usa data de criação ou volume de commits.

**Identidade visual:** títulos, listas curtas, links descritivos e tabelas de poucas colunas em Markdown nativo. A renderização do GitHub fornece tipografia, tema claro/escuro e adaptação de largura. Sem badges externos, animações ou fontes customizadas. A imagem `DS.jpg` permanece preservada, sem ocupar a abertura do portfólio.

**Estrutura:**

```text
README.md                  Apresentação profissional e destaques
CATALOGO.md                Inventário completo e evidências
perfil/README.md           Conteúdo pronto para o repositório de perfil
docs/EXPERIENCIA.md        Trajetória e formação por fonte
docs/AUDITORIA.md          Diagnóstico e plano adotado
docs/SEGURANCA.md          Limites encontrados e ações recomendadas
docs/PROPOSTAS-README.md   Propostas para os projetos originais
docs/PUBLICACAO.md        Publicação e manutenção
docs/RELATORIO.md         Entrega, validação e próximos passos
DS.jpg                    Imagem existente preservada
```

As melhorias propostas nos READMEs originais são proporcionais ao projeto e dependem da aprovação do mantenedor. Somente os arquivos locais do portfólio foram editados.

## Versões das evidências

| Repositório | Commit analisado |
| --- | --- |
| anvmano.github.io | `c4d5b5e624f0f5fe7c82742e788f3ddcde0da4e0` |
| estacao-climatica-csharp | `2dd5fe9a43c697f680ad8463a67d4ffb4bd8f52a` |
| estacao-climatica | `cc28a94828c8837fd1f625945856872f0f046324` |
| LightingController | `26fff2f1972567e9cf4dec678ce463311d51cfeb` |
| SensorsController | `f6840dbf34d2e15f90c4a4ff4429f6863aa5cdd5` |
| Oracle-Database | `93d72004e68216b00bc67afe6e2c977b3a701f6a` |

Cada seção do catálogo contém links para arquivos/diretórios dessas revisões. Novas versões podem mudar os achados.
