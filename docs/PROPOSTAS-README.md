# Propostas de documentação dos projetos

[Auditoria](AUDITORIA.md) · [Catálogo](../CATALOGO.md)

**Estado: propostas para aprovação. Nenhum arquivo dos seis projetos originais foi modificado.** As descrições e instruções existentes foram aproveitadas no catálogo local; esta página delimita possíveis alterações futuras, sem incluir mudanças de código de aplicação.

## estacao-climatica-csharp

**Mudança proposta:** criar `README.md` na raiz como entrada curta e manter `docs/README.md` como guia detalhado.

Conteúdo sugerido: objetivo e funcionalidades da API, stack .NET 8/ASP.NET Core/Firebase, estrutura dos quatro projetos, requisitos, configuração com exemplos sem credenciais e links para o contrato de consultas. Reaproveitar os comandos já documentados de restore, execução e teste, sem declarar nova aprovação da suíte. Indicar testes xUnit/Playwright e condição da paridade ao vivo. Explicitar ausência de enforcement App Check e necessidade de definir o acesso Firebase na implantação.

**Justificativa:** o recrutador chega pela raiz; a documentação técnica atual já existe e pode ser preservada sem duplicação extensa. Não publicar a demonstração web como se fosse a implantação .NET.

## anvmano.github.io

**Mudança proposta:** criar `README.md` na raiz com objetivo, modo público/interno, demonstração existente, stack, estrutura resumida e acesso a `docs/README.md`.

Reaproveitar a instrução de servidor estático e os scripts existentes em `package.json`; distinguir bibliotecas de runtime/CDN das ferramentas de desenvolvimento. Reservar espaço para capturas apenas quando forem obtidas e sanitizadas. Documentar que autorização no cliente depende das regras Firebase. Propor separadamente um `.gitignore` para `node_modules` e artefatos locais.

**Justificativa:** dar acesso imediato ao aplicativo e às instruções sem obrigar o visitante a descobrir a pasta `docs/`.

## Oracle-Database

**Mudança proposta:** intervenção pequena no README: acrescentar no início um percurso de três links — roteiro por sintoma, catálogo SQL e cenário de laboratório. Manter o índice completo, a licença e todos os limites de versão/execução existentes.

**Justificativa:** o README já é abrangente; uma reescrita geral acrescentaria manutenção sem melhorar o acesso. Não remover a distinção entre revisão documental, simulações e validação em Oracle real.

## estacao-climatica

**Mudança proposta:** preservar o README completo. Se for útil, adicionar um resumo inicial que separe estação local, consultas de visitantes e consumidores do histórico. Vincular diagramas/pinagem ou fotos somente quando existirem.

**Justificativa:** instalação, dependências, comandos Telegram, credenciais de exemplo, fila e limitações já estão detalhados. Preservar o registro histórico de compilação como histórico, sem apresentá-lo como novo teste.

## SensorsController

**Mudança proposta:** manter a documentação atual e facilitar o acesso inicial às seções de sensores, formato dos registros e recuperação da fila. Acrescentar uma montagem elétrica apenas após conferência dos componentes reais.

**Justificativa:** o README já descreve inclusive os riscos de recuperação. Não substituir essas ressalvas por “fila sem perda de dados” nem por promessas de precisão dos sensores.

## LightingController

**Mudança proposta:** nenhuma reescrita necessária. Opcionalmente, acrescentar uma foto da montagem e uma pequena amostra visual da curva de brilho, identificadas como ilustração do algoritmo e somente após conferir o hardware.

**Justificativa:** documentação proporcional ao projeto, com comportamento, payload, instalação e limites. Preservar a dependência de horários solares externos e a informação sobre TLS.

## Limites das propostas

Não incluem novos endpoints, resultados de teste, imagens fictícias, novas licenças, alteração de configuração, refatoração ou correções de aplicação. Antes de editar qualquer um desses repositórios, o escopo correspondente deve ser aprovado pelo mantenedor, como solicitado na missão.
