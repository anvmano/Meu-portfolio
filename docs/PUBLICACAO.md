# Publicação e manutenção

[Apresentação](../README.md) · [README de perfil preparado](../perfil/README.md) · [Relatório](RELATORIO.md)

O mantenedor autorizou a publicação em 20/10/2026. Os destinos são o [portfólio](https://github.com/anvmano/Meu-portfolio) e o [repositório de perfil](https://github.com/anvmano/anvmano), criado com o README profissional preparado nesta entrega. Os comandos abaixo documentam o fluxo de publicação e futuras atualizações.

## Publicar o portfólio

1. Abra um terminal na pasta deste repositório. Confira destino, branch e mudanças:

```powershell
git remote get-url origin
git branch --show-current
git status --short
git diff -- README.md
git diff --check
```

O destino esperado é `https://github.com/anvmano/Meu-portfolio.git`, branch `main`. Revise também os arquivos novos no editor, pois `git diff` sem staging não mostra seu conteúdo.

2. Confira a identidade que será usada, sem inventar nome ou e-mail:

```powershell
git config --get user.name
git config --get user.email
```

3. Após revisar, prepare somente os arquivos da entrega e crie o commit local:

```powershell
git add README.md CATALOGO.md perfil/README.md docs/EXPERIENCIA.md docs/AUDITORIA.md docs/SEGURANCA.md docs/PROPOSTAS-README.md docs/PUBLICACAO.md docs/RELATORIO.md
git diff --cached --check
git diff --cached --stat
git commit -m 'Organiza portfolio backend C# e .NET com catalogo de projetos'
```

4. Com autorização para publicação, envie:

```powershell
git push origin main
```

Se o remoto tiver mudado, inspecione e integre o histórico antes de reenviar. Não use force push. Abra o [repositório do portfólio](https://github.com/anvmano/Meu-portfolio) após a publicação e confira README, catálogo e navegação na renderização real do GitHub.

## Ativar a apresentação no perfil

O conteúdo de `perfil/README.md` foi publicado no `README.md` da raiz do repositório público `anvmano/anvmano`. A pasta `perfil/` dentro de `Meu-portfolio` mantém a cópia editorial; sozinha, ela não ativa a apresentação no perfil.

Para atualizar a apresentação, revise `perfil/README.md` e publique o mesmo conteúdo no README de `anvmano/anvmano`, preservando o histórico dos dois repositórios. Eles não se sincronizam automaticamente. Não é necessário recriar o repositório ou alterar sua visibilidade.

O GitHub exige repositório público com o mesmo nome do usuário e README não vazio na raiz. [Orientação oficial sobre README de perfil](https://docs.github.com/en/account-and-profile/how-tos/profile-customization/managing-your-profile-readme).

O README preparado usa links absolutos aos repositórios existentes, por isso pode ser copiado sem depender da estrutura local de pastas. Os textos sobre o novo catálogo passam a corresponder ao conteúdo remoto depois do push de `Meu-portfolio`.

## Organização sugerida do perfil

- Bio sugerida: **Desenvolvedor Backend C#/.NET | ASP.NET MVC, SQL e testes automatizados | Experiência em Oracle**.
- Descrição aplicada a `Meu-portfolio`: **Portfólio de desenvolvimento backend C#/.NET, bancos de dados e integrações com ESP32.**
- Fixar primeiro `estacao-climatica-csharp`, depois `Oracle-Database`, `anvmano.github.io` e `Meu-portfolio`. Se desejar preencher os outros espaços, priorizar `estacao-climatica` e `SensorsController`; LightingController continua acessível pelo catálogo.

A bio e os itens fixados continuam como sugestões; não foram alterados nesta publicação. O GitHub permite até seis itens fixados; use a opção de personalizar os itens fixados no perfil. [Orientação oficial](https://docs.github.com/en/account-and-profile/how-tos/profile-customization/pinning-items-to-your-profile).

## Manter o conteúdo verificável

Ao adicionar ou alterar um projeto, atualize sua seção no catálogo com código-fonte e limitações, depois avalie se merece destaque na página principal. Mantenha nome, objetivo, tecnologias, funcionalidades, estado e instruções coerentes com a versão publicada.

Atualize experiência/formação apenas com informações confirmadas. Revise os contatos e os links ao publicar. Ao renovar uma auditoria, registre o novo commit e atualize conjuntamente descrição e evidências; não troque somente o hash de uma análise antiga.

Não é necessário ativar GitHub Pages para este portfólio em Markdown. A URL `anvmano.github.io` já demonstra o dashboard climático e não deve ser substituída por este conteúdo sem uma nova decisão do mantenedor.
